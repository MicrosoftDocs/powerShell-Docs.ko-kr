---
title: Runspace02 (VB.NET) 코드 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 922d1e8568dad8c02f77e4b76342418bb3b54469
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771654"
---
# <a name="runspace02-vbnet-code-sample"></a><span data-ttu-id="0b291-102">Runspace02(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="0b291-102">Runspace02 (VB.NET) Code Sample</span></span>

<span data-ttu-id="0b291-103">Runspace02 샘플에 대 한 VB.NET 소스 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0b291-103">Here is the VB.NET source code for the Runspace02 sample.</span></span> <span data-ttu-id="0b291-104">이 샘플에서는 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하 여 cmdlet을 동기적으로 실행 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b291-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="0b291-105">그러면 Windows Forms 및 데이터 바인딩이 DataGridView 컨트롤에 결과를 표시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b291-105">Windows Forms and data binding are then used to display the results in a DataGridView control.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0b291-106">코드 예제</span><span class="sxs-lookup"><span data-stu-id="0b291-106">Code Sample</span></span>

```vb
Imports System
Imports System.Collections
Imports System.Collections.ObjectModel
Imports System.Windows.Forms
Imports System.Management.Automation.Runspaces
Imports System.Management.Automation

Namespace Microsoft.Samples.PowerShell.Runspaces

    Class Runspace02

        Shared Sub CreateForm()
            Dim form As New Form()
            Dim grid As New DataGridView()
            form.Controls.Add(grid)
            grid.Dock = DockStyle.Fill

            ' Create an instance of the RunspaceInvoke class.
            ' This takes care of all building all of the other
            ' data structures needed...
            Dim invoker As New RunspaceInvoke()

            Dim results As Collection(Of PSObject) = _
                invoker.Invoke("get-process | sort-object ID")

            ' The generic collection needs to be re-wrapped in an ArrayList
            ' for data-binding to work...
            Dim objects As New ArrayList()
            objects.AddRange(results)

            ' The DataGridView will use the PSObjectTypeDescriptor type
            ' to retrieve the properties.
            grid.DataSource = objects

            form.ShowDialog()

        End Sub 'CreateForm


        ''' <summary>
        ''' This sample uses the RunspaceInvoke class to execute
        ''' the get-process cmdlet synchronously. Windows Forms and data
        ''' binding are then used to display the results in a
        ''' DataGridView control.
        ''' </summary>
        ''' <param name="args">Unused</param>
        ''' <remarks>
        ''' This sample demonstrates the following:
        ''' 1. Creating an instance of the RunspaceInvoke class.
        ''' 2. Using this instance to invoke a PowerShell command.
        ''' 3. Using the output of RunspaceInvoke in a DataGridView
        '''    in a Windows Forms application
        ''' </remarks
        Shared Sub Main(ByVal args() As String)
            Runspace02.CreateForm()
        End Sub 'Main

    End Class 'Runspace02

End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace02.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace02/Runspace02.vb#L09-L68 "Runspace02.vb")] -->

## <a name="see-also"></a><span data-ttu-id="0b291-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b291-107">See Also</span></span>

[<span data-ttu-id="0b291-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0b291-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
