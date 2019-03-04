---
title: Runspace04 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6a04f15-b5d8-475b-ac9c-e75c58ec8933
caps.latest.revision: 8
ms.openlocfilehash: 9e8123e9b1068e0fd6efec8508eacf594ff22301
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854749"
---
# <a name="runspace04-sample"></a><span data-ttu-id="b6aed-102">Runspace04 샘플</span><span class="sxs-lookup"><span data-stu-id="b6aed-102">Runspace04 Sample</span></span>

<span data-ttu-id="b6aed-103">이 샘플에 사용 하는 방법을 보여 줍니다 합니다 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 명령을 실행 하는 클래스 및 명령을 실행 하는 경우 throw 되는 종료 오류를 catch 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span> <span data-ttu-id="b6aed-104">두 개의 명령이 실행되는데, 마지막 명령은 유효하지 않은 매개 변수 인수를 전달받습니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-104">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span> <span data-ttu-id="b6aed-105">따라서 개체가 반환되지 않고 종료 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-105">As a result, no objects are returned and a terminating error is thrown.</span></span>

## <a name="requirements"></a><span data-ttu-id="b6aed-106">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b6aed-106">Requirements</span></span>

<span data-ttu-id="b6aed-107">이 샘플 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b6aed-108">시연</span><span class="sxs-lookup"><span data-stu-id="b6aed-108">Demonstrates</span></span>

<span data-ttu-id="b6aed-109">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="b6aed-110">만들기는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="b6aed-111">파이프라인에 명령을 추가 합니다 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-111">Adding commands to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="b6aed-112">파이프라인에 매개 변수 인수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-112">Adding parameter arguments to the pipeline.</span></span>

- <span data-ttu-id="b6aed-113">명령은 동기적으로 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-113">Invoking the commands synchronously.</span></span>

- <span data-ttu-id="b6aed-114">사용 하 여 [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) 개체를 추출 하 고 명령을 사용 하 여 반환 된 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-114">Using [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the commands.</span></span>

- <span data-ttu-id="b6aed-115">검색 하 고 명령을 실행 하는 동안 생성 된 오류 레코드를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-115">Retrieving and displaying error records that were generated during the running of the commands.</span></span>

- <span data-ttu-id="b6aed-116">Catch 및 명령을 사용 하 여 발생 한 종료 예외를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-116">Catching and displaying terminating exceptions thrown by the commands.</span></span>

## <a name="example"></a><span data-ttu-id="b6aed-117">예제</span><span class="sxs-lookup"><span data-stu-id="b6aed-117">Example</span></span>

<span data-ttu-id="b6aed-118">이 샘플은 동기적으로 Windows PowerShell에서 제공 하는 기본 runspace에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-118">This sample runs commands synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="b6aed-119">마지막 명령은 명령에 잘못 된 매개 변수 인수를 전달 되기 때문에 종료 되는 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-119">The last command throws a terminating error because a parameter argument that is not valid is passed to the command.</span></span> <span data-ttu-id="b6aed-120">종료 오류 트래핑 되어 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6aed-120">The terminating error is trapped and displayed.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace04
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands.
    /// The commands generate a terminating exception that the caller
    /// should catch and process.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run commands.
    /// 2. Adding commands to the pipeline of  the PowerShell object.
    /// 3. Passing input objects to the commands from the calling program.
    /// 4. Using PSObject objects to extract and display properties from the
    ///    objects returned by the commands.
    /// 5. Retrieving and displaying error records that were generated
    ///    while running the commands.
    /// 6. Catching and displaying terminating exceptions generated
    ///    while running the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object.
      using (PowerShell powershell = PowerShell.Create())
      {
        // Add the commands to the PowerShell object.
        powershell.AddCommand("Get-ChildItem").AddCommand("Select-String").AddArgument("*");

        // Run the commands synchronously. Because of the bad regular expression,
        // no objects will be returned. Instead, an exception will be thrown.
        try
        {
          foreach (PSObject result in powershell.Invoke())
          {
            Console.WriteLine("'{0}'", result.ToString());
          }

          // Process any error records that were generated while running the commands.
          Console.WriteLine("\nThe following non-terminating errors occurred:\n");
          PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
          if (errors != null && errors.Count > 0)
          {
            foreach (ErrorRecord err in errors)
            {
              System.Console.WriteLine("    error: {0}", err.ToString());
            }
          }
        }
        catch (RuntimeException runtimeException)
        {
          // Trap any exception generated by the commands. These exceptions
          // will all be derived from the RuntimeException exception.
          System.Console.WriteLine(
                        "Runtime exception: {0}: {1}\n{2}",
                        runtimeException.ErrorRecord.InvocationInfo.InvocationName,
                        runtimeException.Message,
                        runtimeException.ErrorRecord.InvocationInfo.PositionMessage);
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="b6aed-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6aed-121">See Also</span></span>

[<span data-ttu-id="b6aed-122">Windows PowerShell 호스트 응용 프로그램 작성</span><span class="sxs-lookup"><span data-stu-id="b6aed-122">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)