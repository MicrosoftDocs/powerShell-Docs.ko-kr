---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace03(VB.NET) 코드 샘플
description: RunSpace03(VB.NET) 코드 샘플
ms.openlocfilehash: 796e550d05de5c425dcabdb5ccf735acfb8f9ff0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647421"
---
# <a name="runspace03-vbnet-code-sample"></a><span data-ttu-id="f5adb-103">RunSpace03(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="f5adb-103">RunSpace03 (VB.NET) Code Sample</span></span>

<span data-ttu-id="f5adb-104">다음은 "지정 된 스크립트를 실행 하는 콘솔 응용 프로그램 만들기"에 설명 된 콘솔 응용 프로그램의 VB.NET 소스 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="f5adb-104">Here is the VB.NET source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="f5adb-105">이 샘플에서는 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하 여 스크립트에 전달 된 프로세스 이름 목록에 대 한 프로세스 정보를 검색 하는 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5adb-105">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information for the list of process names passed into the script.</span></span> <span data-ttu-id="f5adb-106">입력 개체를 스크립트에 전달 하는 방법 및 출력 개체 뿐만 아니라 오류 개체를 검색 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f5adb-106">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="f5adb-107">Windows Vista 용 Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 샘플에 대 한 VB.NET 원본 파일 (runspace03)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5adb-107">You can download the VB.NET source file (runspace03.vb) for this sample by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f5adb-108">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5adb-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="f5adb-109">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="f5adb-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f5adb-110">코드 예제</span><span class="sxs-lookup"><span data-stu-id="f5adb-110">Code Sample</span></span>

```vb
Imports System
Imports System.Collections
Imports System.Collections.Generic
Imports System.Collections.ObjectModel
Imports System.Text
Imports Microsoft.VisualBasic
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Class Runspace03

        ''' <summary>
        ''' This sample uses the RunspaceInvoke class to execute
        ''' a script that retrieves process information for the
        ''' list of process names passed into the script.
        ''' It shows how to pass input objects to a script and
        ''' how to retrieve error objects as well as the output objects.
        ''' </summary>
        ''' <param name="args">Unused</param>
        ''' <remarks>
        ''' This sample demonstrates the following:
        ''' 1. Creating an instance of the RunspaceInvoke class.
        ''' 2. Using this instance to execute a string as a PowerShell script.
        ''' 3. Passing input objects to the script from the calling program.
        ''' 4. Using PSObject to extract and display properties from the objects
        '''    returned by this command.
        ''' 5. Retrieving and displaying error records that were generated
        '''    during the execution of that script.
        ''' </remarks>
        Shared Sub Main(ByVal args() As String)
            ' Define a list of processes to look for
            Dim processNames() As String = {"lsass", "nosuchprocess", _
                "services", "nosuchprocess2"}

            ' The script to run to get these processes. Input passed
            ' to the script will be available in the $input variable.
            Dim script As String = "$input | get-process -name {$_}"

            ' Create an instance of the RunspaceInvoke class.
            Dim invoker As New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            Dim errors As System.Collections.IList = Nothing
            Dim result As PSObject
            For Each result In invoker.Invoke(script, processNames, errors)
                Console.WriteLine("{0,-20} {1}", _
                result.Members("ProcessName").Value, _
                result.Members("HandleCount").Value)
            Next result

            ' Now process any error records that were generated while
            ' running the script.
            Console.WriteLine(vbCrLf & _
                "The following non-terminating errors occurred:" & vbCrLf)
            If Not (errors Is Nothing) AndAlso errors.Count > 0 Then
                Dim err As PSObject
                For Each err In errors
                    System.Console.WriteLine("    error: {0}", err.ToString())
                Next err
            End If
            System.Console.WriteLine(vbCRLF & "Hit any key to exit...")
            System.Console.ReadKey()

        End Sub 'Main

    End Class 'Runspace03

End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace03.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace03.vb#L09-L83 "Runspace03.vb")] -->

## <a name="see-also"></a><span data-ttu-id="f5adb-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f5adb-111">See Also</span></span>

[<span data-ttu-id="f5adb-112">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="f5adb-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f5adb-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f5adb-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
