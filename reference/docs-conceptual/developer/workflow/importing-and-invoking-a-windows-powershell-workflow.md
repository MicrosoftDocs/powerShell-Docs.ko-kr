---
title: Windows PowerShell 워크플로 가져오기 및 호출 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366042"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Windows PowerShell 워크플로 가져오기 및 호출

Windows PowerShell 3을 사용 하면 Windows PowerShell 모듈로 패키지 된 워크플로를 가져오고 호출할 수 있습니다. Windows PowerShell 모듈에 대 한 자세한 내용은 [Windows Powershell 모듈 작성](../module/writing-a-windows-powershell-module.md)을 참조 하세요.

[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)클래스는 서버의 워크플로 개체에 대 한 클라이언트 쪽 프록시로 사용 됩니다. 다음 절차에서는 [Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)개체를 사용 하 여 워크플로를 호출 하는 방법을 설명 합니다.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>원격 서버에서 워크플로 명령을 실행할 PSJobProxy 개체를 만듭니다.

1. [Runspace Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)개체를 만들어 원격 runspace에 대 한 연결을 만듭니다.

2. [Runspace Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) 개체의 [runspace](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)속성을 `Microsoft.PowerShell.Workflow`로 설정 하 여 Windows PowerShell 끝점을 지정 합니다 (Windows PowerShell 끝점을 지정).

3. 이전 단계를 완료 하 여 만든 연결을 사용 하는 runspace를 만듭니다.

4. [System.object](/dotnet/api/System.Management.Automation.PowerShell)를 만들고 해당 개체의 [시스템](/dotnet/api/System.Management.Automation.PowerShell.Runspace) 을 이전 단계에서 만든 runspace로 설정 합니다 .이를 위해.

5. 워크플로 모듈 및 해당 명령을 [system.object](/dotnet/api/System.Management.Automation.PowerShell)로 가져옵니다.

6. [Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) 개체를 만들고이 개체를 사용 하 여 원격 서버에서 워크플로 명령을 실행 합니다.

## <a name="example"></a>예제

다음 코드 예제에서는 Windows PowerShell을 사용 하 여 워크플로를 호출 하는 방법을 보여 줍니다.

이 예에서는 Windows PowerShell 3이 필요 합니다.

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