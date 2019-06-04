---
title: Windows PowerShell 워크플로 호출 하는 가져오기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080342"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Windows PowerShell 워크플로 가져오기 및 호출

Windows PowerShell 3을 가져오고 Windows PowerShell 모듈로 서 패키지 된 워크플로 호출할 수 있습니다. Windows PowerShell 모듈에 대 한 정보를 참조 하세요 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)합니다.

합니다 [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)클래스는 워크플로 개체는 서버에 대 한 클라이언트 쪽 프록시를으로 사용 됩니다. 다음 절차를 사용 하는 방법에 설명 된 [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)워크플로 호출 하는 개체입니다.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>원격 서버에서 워크플로 명령을 실행 하는 PSJobProxy 개체를 만드는 중입니다.

1. 만들기는 [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)원격 runspace에 대 한 연결을 만들 개체입니다.

2. 설정 합니다 [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) 의 속성을 [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)개체를 `Microsoft.PowerShell.Workflow` 를 Windows PowerShell 끝점을 지정 합니다.

3. 이전 단계를 완료 하 여 만든 연결을 사용 하는 runspace를 만듭니다.

4. 만들기는 [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)개체 및 설정 해당 [System.Management.Automation.Powershell.Runspace*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) 이전 단계에서 만든 runspace에 대 한 속성입니다.

5. 가져오기 워크플로 모듈 및 해당 명령에는 [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)합니다.

6. 만들기는 [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) 개체를 원격 서버에서 워크플로 명령을 실행 하는 데 사용 합니다.

## <a name="example"></a>예제

다음 코드 예제에서는 Windows PowerShell을 사용 하 여 워크플로 호출 하는 방법에 설명 합니다.

이 예제에서는 Windows PowerShell 3이 필요 합니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace WorkflowHostTest
{

class Program
    {
        static void Main(string[] args)
        {
            if (args.Length == 0)
            {
                Console.WriteLine("Specify path to Workflow module");
                return;
            }

            string moduleFile = args[0];

            Console.Write("Creating Remote runspace connection...");
            WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

            //Set the shellURI to workflow endpoint Microsoft.PowerShell.Workflow
            connectionInfo.ShellUri = "Microsoft.PowerShell.Workflow";

            //Create and open a runspace.
            Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo);
            runspace.Open();
            Console.WriteLine("done");

            PowerShell powershell = PowerShell.Create();
            powershell.Runspace = runspace;
            Console.Write("Setting $VerbosePreference=\"Continue\"...");
            powershell.AddScript("$VerbosePreference=\"Continue\"");
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Importing Workflow module...");
            powershell.Commands.Clear();

            //Import the module in to the PowerShell runspace. A XAML file could also be imported directly by using Import-Module.
            powershell.AddCommand("Import-Module").AddArgument(moduleFile);
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Creating job proxy...");
            powershell.Commands.Clear();
            powershell.AddCommand("Get-Proc").AddArgument("*");
            PSJobProxy job = powershell.AsJobProxy();
            Console.WriteLine("done");

                Console.WriteLine();
                Console.WriteLine("Using job proxy and performing operations...");
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine("Starting job...");
                job.StartJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());

                // use blocking enumerator to wait for objects until job finishes
                job.Output.BlockingEnumerator = true;
                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                // wait for a random time before attempting to stop job
                Random random = new Random();
                int time = random.Next(1, 10);
                Console.Write("Sleeping for {0} seconds when job is running on another thread...", time);
                System.Threading.Thread.Sleep(time * 1000);
                Console.WriteLine("done");
                Console.WriteLine("Stopping job...");
                job.StopJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine();
                job.Finished.WaitOne();
                Console.WriteLine("Output from job");
                Console.WriteLine("---------------");

                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                Console.WriteLine();
                Console.WriteLine("Verbose messages from job");
                Console.WriteLine("-------------------------");
                foreach (VerboseRecord v in job.Verbose)
                {
                    Console.WriteLine(v.Message);
                }

            runspace.Close();
        }
    }
}

```