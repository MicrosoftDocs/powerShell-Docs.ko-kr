---
ms.date: 09/13/2016
ms.topic: reference
title: Host01 샘플
description: Host01 샘플
ms.openlocfilehash: b4f1a81044a51855ad7decc25e1f5b1215ab0d62
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355479"
---
# <a name="host01-sample"></a><span data-ttu-id="050cc-103">Host01 샘플</span><span class="sxs-lookup"><span data-stu-id="050cc-103">Host01 Sample</span></span>

<span data-ttu-id="050cc-104">이 샘플에서는 사용자 지정 호스트를 사용 하는 호스트 응용 프로그램을 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="050cc-104">This sample shows how to implement a host application that uses a custom host.</span></span> <span data-ttu-id="050cc-105">이 샘플에서는 사용자 지정 호스트를 사용 하는 runspace가 생성 된 다음 "종료"를 호출 하는 스크립트를 실행 하는 데 사용 [됩니다.](/dotnet/api/System.Management.Automation.PowerShell)</span><span class="sxs-lookup"><span data-stu-id="050cc-105">In this sample a runspace is created that uses the custom host, and then the [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell) API is used to run a script that calls "exit."</span></span> <span data-ttu-id="050cc-106">호스트 애플리케이션은 스크립트의 출력을 살펴보고 결과를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="050cc-106">The host application then looks at the output of the script and prints out the results.</span></span>

<span data-ttu-id="050cc-107">이 샘플에서는 Windows PowerShell에서 제공 하는 기본 UI 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="050cc-107">This sample uses the default UI features provided by Windows PowerShell.</span></span> <span data-ttu-id="050cc-108">사용자 지정 호스트의 UI 기능을 구현 하는 방법에 대 한 자세한 내용은 [Host02 샘플](./host02-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="050cc-108">For more information about implementing the UI features of a custom host, see [Host02 Sample](./host02-sample.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="050cc-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="050cc-109">Requirements</span></span>

<span data-ttu-id="050cc-110">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="050cc-110">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="050cc-111">데모</span><span class="sxs-lookup"><span data-stu-id="050cc-111">Demonstrates</span></span>

- <span data-ttu-id="050cc-112">[PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) 클래스에서 파생 되는 사용자 지정 호스트 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="050cc-112">Creating a custom host class that derives from the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span>

- <span data-ttu-id="050cc-113">사용자 지정 호스트 클래스를 사용 하는 runspace 만들기</span><span class="sxs-lookup"><span data-stu-id="050cc-113">Creating a runspace that uses the custom host class.</span></span>

- <span data-ttu-id="050cc-114">Exit를 호출 하는 스크립트를 실행 하는 [system.web. Powershell](/dotnet/api/System.Management.Automation.PowerShell) 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="050cc-114">Creating a [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell) object that runs a script that calls exit.</span></span>

- <span data-ttu-id="050cc-115">종료 프로세스에 올바른 종료 코드가 사용 되었는지 확인 하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="050cc-115">Verifying that the correct exit code was used in the exit process.</span></span>

## <a name="example-1"></a><span data-ttu-id="050cc-116">예 1</span><span class="sxs-lookup"><span data-stu-id="050cc-116">Example 1</span></span>

<span data-ttu-id="050cc-117">다음 코드에서는 간단한 사용자 지정 호스트 인터페이스를 사용 하는 호스트 응용 프로그램의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="050cc-117">The following code shows an implementation of a host application that uses a simple custom host interface.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Host
{

    using System;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using PowerShell = System.Management.Automation.PowerShell;

    /// <summary>
    /// This class contains the Main entry point for this host application.
    /// </summary>
    internal class Host01
    {

        /// <summary>
        /// Indicator to tell the host application that it should exit.
        /// </summary>
        private bool shouldExit;

        /// <summary>
        /// The exit code that the host application will use to exit.
        /// </summary>
        private int exitCode;

        /// <summary>
        /// Gets or sets a value indicating whether the
        /// host application should exit.
        /// </summary>
        public bool ShouldExit
        {
            get { return this.shouldExit; }
            set { this.shouldExit = value; }
        }

        /// <summary>
        /// Gets or sets the PSHost implementation that is
        /// used to tell the host application what code to use
        /// when exiting.
        /// </summary>
        public int ExitCode
        {
            get { return this.exitCode; }
            set { this.exitCode = value; }
        }

        /// <summary>
        /// This sample uses a PowerShell object to run
        /// a script that calls exit. The host application looks at
        /// this and prints out the result.
        /// </summary>
        /// <param name="args">Parameter not used.</param>
        private static void Main(string[] args)
        {
            // Create an instance of this host application class so that
            // the Windows PowerShell engine will have access to the
            // ShouldExit and ExitCode parameters.
            Host01 me = new Host01();

            // Create the host instance to use.
            MyHost myHost = new MyHost(me);

            // Create a runspace that uses the host object and run the
            // script using a PowerShell object.
            using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(myHost))
            {
                // Open the runspace.
                myRunSpace.Open();

                // Create a PowerShell object to run the script.
                using (PowerShell powershell = PowerShell.Create())
                {
                    powershell.Runspace = myRunSpace;

                    // Create the pipeline and run the script
                    // "exit (2+2)".
                    string script = "exit (2+2)";
                    powershell.AddScript(script);
                    powershell.Invoke(script);
                }

                // Check the flags and see if they were set propertly.
                Console.WriteLine(
                    "ShouldExit={0} (should be True); ExitCode={1} (should be 4)",
                    me.ShouldExit,
                    me.ExitCode);

                // close the runspace to free resources.
                myRunSpace.Close();
            }

            Console.WriteLine("Hit any key to exit...");
            Console.ReadKey();
        }
    }
}
```

## <a name="example-2"></a><span data-ttu-id="050cc-118">예제 2</span><span class="sxs-lookup"><span data-stu-id="050cc-118">Example 2</span></span>

<span data-ttu-id="050cc-119">다음 코드는이 호스트 응용 프로그램에서 사용 하는 [PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) 클래스의 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="050cc-119">The following code is the implementation of the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class that is used by this host application.</span></span> <span data-ttu-id="050cc-120">구현 되지 않은 요소는 예외를 throw 하거나 아무 것도 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="050cc-120">Those elements that are not implemented throw an exception or return nothing.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Host
{
    using System;
    using System.Globalization;
    using System.Management.Automation.Host;

    /// <summary>
    /// This is a sample implementation of the PSHost abstract class for
    /// console applications. Not all members are implemented. Those that
    /// are not implemented throw a NotImplementedException exception or
    /// return nothing.
    /// </summary>
    internal class MyHost : PSHost
    {
        /// <summary>
        /// A reference to the PSHost implementation.
        /// </summary>
        private Host01 program;

        /// <summary>
        /// The culture information of the thread that created
        /// this object.
        /// </summary>
        private CultureInfo originalCultureInfo =
            System.Threading.Thread.CurrentThread.CurrentCulture;

        /// <summary>
        /// The UI culture information of the thread that created
        /// this object.
        /// </summary>
        private CultureInfo originalUICultureInfo =
            System.Threading.Thread.CurrentThread.CurrentUICulture;

        /// <summary>
        /// The identifier of this PSHost implementation.
        /// </summary>
        private Guid myId = Guid.NewGuid();

        /// <summary>
        /// Initializes a new instance of the MyHost class. Keep
        /// a reference to the host application object so that it
        /// can be informed of when to exit.
        /// </summary>
        /// <param name="program">
        /// A reference to the host application object.
        /// </param>
        public MyHost(Host01 program)
        {
            this.program = program;
        }

        /// <summary>
        /// Return the culture information to use. This implementation
        /// returns a snapshot of the culture information of the thread
        /// that created this object.
        /// </summary>
        public override System.Globalization.CultureInfo CurrentCulture
        {
            get { return this.originalCultureInfo; }
        }

        /// <summary>
        /// Return the UI culture information to use. This implementation
        /// returns a snapshot of the UI culture information of the thread
        /// that created this object.
        /// </summary>
        public override System.Globalization.CultureInfo CurrentUICulture
        {
            get { return this.originalUICultureInfo; }
        }

        /// <summary>
        /// This implementation always returns the GUID allocated at
        /// instantiation time.
        /// </summary>
        public override Guid InstanceId
        {
            get { return this.myId; }
        }

        /// <summary>
        /// Return a string that contains the name of the host implementation.
        /// Keep in mind that this string may be used by script writers to
        /// identify when your host is being used.
        /// </summary>
        public override string Name
        {
            get { return "MySampleConsoleHostImplementation"; }
        }

        /// <summary>
        /// This sample does not implement a PSHostUserInterface component so
        /// this property simply returns null.
        /// </summary>
        public override PSHostUserInterface UI
        {
            get { return null; }
        }

        /// <summary>
        /// Return the version object for this application. Typically this
        /// should match the version resource in the application.
        /// </summary>
        public override Version Version
        {
            get { return new Version(1, 0, 0, 0); }
        }

        /// <summary>
        /// Not implemented by this example class. The call fails with
        /// a NotImplementedException exception.
        /// </summary>
        public override void EnterNestedPrompt()
        {
            throw new NotImplementedException(
                "The method or operation is not implemented.");
        }

        /// <summary>
        /// Not implemented by this example class. The call fails
        /// with a NotImplementedException exception.
        /// </summary>
        public override void ExitNestedPrompt()
        {
            throw new NotImplementedException(
                "The method or operation is not implemented.");
        }

        /// <summary>
        /// This API is called before an external application process is
        /// started. Typically it is used to save state so the parent can
        /// restore state that has been modified by a child process (after
        /// the child exits). In this example, this functionality is not
        /// needed so the method returns nothing.
        /// </summary>
        public override void NotifyBeginApplication()
        {
            return;
        }

        /// <summary>
        /// This API is called after an external application process finishes.
        /// Typically it is used to restore state that a child process may
        /// have altered. In this example, this functionality is not
        /// needed so the method returns nothing.
        /// </summary>
        public override void NotifyEndApplication()
        {
           return;
        }

        /// <summary>
        /// Indicate to the host application that exit has
        /// been requested. Pass the exit code that the host
        /// application should use when exiting the process.
        /// </summary>
        /// <param name="exitCode">The exit code to use.</param>
        public override void SetShouldExit(int exitCode)
        {
            this.program.ShouldExit = true;
            this.program.ExitCode = exitCode;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="050cc-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="050cc-121">See Also</span></span>
