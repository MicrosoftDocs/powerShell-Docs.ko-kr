---
title: 'Runspace02 (c #) 코드 샘플 | Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: 1e58f035f20baa7443d9031499062a45beae01b9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778446"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="e3afd-102">Runspace02(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="e3afd-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="e3afd-103">Runspace02 샘플에 대 한 c # 소스 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e3afd-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="e3afd-104">이 샘플에서는 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하 여 cmdlet을 동기적으로 실행 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3afd-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="e3afd-105">그러면 Windows Forms 및 데이터 바인딩이 DataGridView 컨트롤에 결과를 표시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3afd-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="e3afd-106">코드 예제</span><span class="sxs-lookup"><span data-stu-id="e3afd-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a><span data-ttu-id="e3afd-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3afd-107">See Also</span></span>

[<span data-ttu-id="e3afd-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e3afd-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
