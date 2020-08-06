---
title: Cmdlet 출력 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7697db01c8c4d1c831202c07256559bf638aeaef
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784438"
---
# <a name="cmdlet-output"></a><span data-ttu-id="fb72f-102">Cmdlet 출력</span><span class="sxs-lookup"><span data-stu-id="fb72f-102">Cmdlet Output</span></span>

<span data-ttu-id="fb72f-103">이 섹션에서는 cmdlet 출력 유형과 cmdlet이 오류 메시지 및 개체와 같은 출력을 생성 하기 위해 호출할 수 있는 메서드를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb72f-103">This section discusses the types of cmdlet output and the methods that cmdlets can call to generate output such as error messages and objects.</span></span> <span data-ttu-id="fb72f-104">이 섹션에서는 cmdlet에서 반환 되는 .NET Framework 형식 및 해당 개체를 표시 하는 방법을 정의 하는 방법에 대해서도 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb72f-104">This section also describes how to define the .NET Framework types that are returned by your cmdlets and how those objects are displayed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fb72f-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="fb72f-105">In This Section</span></span>

<span data-ttu-id="fb72f-106">[Cmdlet 출력의 유형](./types-of-cmdlet-output.md) Cmdlet에서 생성할 수 있는 형식과 출력 및 cmdlet이 출력을 생성 하기 위해 호출 하는 메서드를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb72f-106">[Types of Cmdlet Output](./types-of-cmdlet-output.md) Describes the types and output that cmdlets can generate and the methods that cmdlets call to generate the output.</span></span>

<span data-ttu-id="fb72f-107">[Cmdlet 오류 보고](./cmdlet-error-reporting.md) Cmdlet 출력의 하위 집합인 cmdlet 오류 보고에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb72f-107">[Cmdlet Error Reporting](./cmdlet-error-reporting.md) Discusses cmdlet error reporting, a subset of cmdlet output.</span></span>

<span data-ttu-id="fb72f-108">[출력 개체 확장](./extending-output-objects.md) 형식 파일 (. types.ps1xml)을 사용 하 여 cmdlet, 함수 및 스크립트에 의해 반환 되는 .NET Framework 개체를 확장 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb72f-108">[Extending Output Objects](./extending-output-objects.md) Discusses how to use the types files (.ps1xml) to extend the .NET Framework objects that are returned by cmdlets, functions, and scripts.</span></span>

<span data-ttu-id="fb72f-109">[PowerShell 서식 파일](../format/powershell-formatting-files.md) Windows PowerShell에서 .NET Framework 개체의 특정 집합에 대 한 기본 표시를 정의 하는 서식 파일 (.format.ps1xml) 파일에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb72f-109">[PowerShell Formatting Files](../format/powershell-formatting-files.md) Describes the formatting files (.format.ps1xml) files that define the default display for a specific set of .NET Framework objects in Windows PowerShell.</span></span>

<span data-ttu-id="fb72f-110">[사용자 지정 서식 파일](./custom-formatting-files.md) 사용자 고유의 사용자 지정 서식 파일을 만들어 기본 표시 형식을 덮어쓰거나 사용자의 명령으로 반환 되는 개체의 표시를 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb72f-110">[Custom Formatting Files](./custom-formatting-files.md) Describes how to create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb72f-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb72f-111">See Also</span></span>

[<span data-ttu-id="fb72f-112">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="fb72f-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
