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
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a><span data-ttu-id="a835b-102">Windows PowerShell 워크플로 가져오기 및 호출</span><span class="sxs-lookup"><span data-stu-id="a835b-102">Importing and Invoking a Windows PowerShell Workflow</span></span>

<span data-ttu-id="a835b-103">Windows PowerShell 3을 사용 하면 Windows PowerShell 모듈로 패키지 된 워크플로를 가져오고 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a835b-103">Windows PowerShell 3, allows you to import and invoke a workflow that is packaged as a Windows PowerShell module.</span></span> <span data-ttu-id="a835b-104">Windows PowerShell 모듈에 대 한 자세한 내용은 [Windows Powershell 모듈 작성](../module/writing-a-windows-powershell-module.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a835b-104">For information about Windows PowerShell modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

<span data-ttu-id="a835b-105">[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)클래스는 서버의 워크플로 개체에 대 한 클라이언트 쪽 프록시로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a835b-105">The [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)class is used as a client side proxy for workflow objects on the server.</span></span> <span data-ttu-id="a835b-106">다음 절차에서는 [Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)개체를 사용 하 여 워크플로를 호출 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a835b-106">The following procedure explains how to use a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)object to invoke a workflow.</span></span>

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a><span data-ttu-id="a835b-107">원격 서버에서 워크플로 명령을 실행할 PSJobProxy 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a835b-107">Creating a PSJobProxy object to execute workflow commands on a remote server.</span></span>

1. <span data-ttu-id="a835b-108">[Runspace Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)개체를 만들어 원격 runspace에 대 한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a835b-108">Create an [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to create a connection to a remote runspace.</span></span>

2. <span data-ttu-id="a835b-109">[Runspace Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) 개체의 [runspace](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)속성을 `Microsoft.PowerShell.Workflow`로 설정 하 여 Windows PowerShell 끝점을 지정 합니다 (Windows PowerShell 끝점을 지정).</span><span class="sxs-lookup"><span data-stu-id="a835b-109">Set the [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) property of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to `Microsoft.PowerShell.Workflow` to specify a Windows PowerShell endpoint.</span></span>

3. <span data-ttu-id="a835b-110">이전 단계를 완료 하 여 만든 연결을 사용 하는 runspace를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a835b-110">Create a runspace that uses the connection created by completing the previous steps.</span></span>

4. <span data-ttu-id="a835b-111">[System.object](/dotnet/api/System.Management.Automation.PowerShell)를 만들고 해당 개체의 [시스템](/dotnet/api/System.Management.Automation.PowerShell.Runspace) 을 이전 단계에서 만든 runspace로 설정 합니다 .이를 위해.</span><span class="sxs-lookup"><span data-stu-id="a835b-111">Create a [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)object and set its [System.Management.Automation.Powershell.Runspace\*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) property to the runspace created in the previous step.</span></span>

5. <span data-ttu-id="a835b-112">워크플로 모듈 및 해당 명령을 [system.object](/dotnet/api/System.Management.Automation.PowerShell)로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a835b-112">Import the workflow module and its commands into the [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).</span></span>

6. <span data-ttu-id="a835b-113">[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) 개체를 만들고이 개체를 사용 하 여 원격 서버에서 워크플로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a835b-113">Create a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) object and use it to execute workflow commands on the remote server.</span></span>

## <a name="example"></a><span data-ttu-id="a835b-114">예제</span><span class="sxs-lookup"><span data-stu-id="a835b-114">Example</span></span>

<span data-ttu-id="a835b-115">다음 코드 예제에서는 Windows PowerShell을 사용 하 여 워크플로를 호출 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a835b-115">The following code example demonstrates how to invoke a workflow by using Windows PowerShell.</span></span>

<span data-ttu-id="a835b-116">이 예에서는 Windows PowerShell 3이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a835b-116">This example requires Windows PowerShell 3.</span></span>

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