---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: 501c0482270a5a4919ed33844beb838e231f8636
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210641"
---
# <span data-ttu-id="17387-103">Out-Null</span><span class="sxs-lookup"><span data-stu-id="17387-103">Out-Null</span></span>

## <span data-ttu-id="17387-104">개요</span><span class="sxs-lookup"><span data-stu-id="17387-104">SYNOPSIS</span></span>
<span data-ttu-id="17387-105">파이프라인으로 보내거나 표시 하지 않고 출력을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="17387-105">Hides the output instead of sending it down the pipeline or displaying it.</span></span>

## <span data-ttu-id="17387-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="17387-106">SYNTAX</span></span>

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="17387-107">설명</span><span class="sxs-lookup"><span data-stu-id="17387-107">DESCRIPTION</span></span>

<span data-ttu-id="17387-108">**Out-null** cmdlet은 결과를 null로 보내 파이프라인에서 제거 하 고 출력이 화면에 표시 되는 것을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="17387-108">The **Out-Null** cmdlet sends its output to NULL, in effect, removing it from the pipeline and preventing the output to be displayed at the screen.</span></span>

## <span data-ttu-id="17387-109">예제</span><span class="sxs-lookup"><span data-stu-id="17387-109">EXAMPLES</span></span>

### <span data-ttu-id="17387-110">예제 1: 출력 삭제</span><span class="sxs-lookup"><span data-stu-id="17387-110">Example 1: Delete output</span></span>

```powershell
Get-ChildItem | Out-Null
```

<span data-ttu-id="17387-111">이 명령은 현재 위치/디렉터리에 있는 항목을 가져오지만 출력은 파이프라인을 통해 전달 되거나 명령줄에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17387-111">This command gets items in the current location/directory, but its output is not passed through the pipeline nor displayed at the command line.</span></span>
<span data-ttu-id="17387-112">이는 필요 하지 않은 출력을 숨기는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17387-112">This is useful for hiding output that you do not need.</span></span>

## <span data-ttu-id="17387-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="17387-113">PARAMETERS</span></span>

### <span data-ttu-id="17387-114">-InputObject</span><span class="sxs-lookup"><span data-stu-id="17387-114">-InputObject</span></span>

<span data-ttu-id="17387-115">NULL로 보낼 개체를 지정 합니다 (파이프라인에서 제거 됨).</span><span class="sxs-lookup"><span data-stu-id="17387-115">Specifies the object to be sent to NULL (removed from pipeline).</span></span>
<span data-ttu-id="17387-116">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="17387-116">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="17387-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="17387-117">CommonParameters</span></span>

<span data-ttu-id="17387-118">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="17387-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="17387-119">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17387-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="17387-120">입력</span><span class="sxs-lookup"><span data-stu-id="17387-120">INPUTS</span></span>

### <span data-ttu-id="17387-121">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="17387-121">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="17387-122">모든 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17387-122">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="17387-123">출력</span><span class="sxs-lookup"><span data-stu-id="17387-123">OUTPUTS</span></span>

### <span data-ttu-id="17387-124">없음</span><span class="sxs-lookup"><span data-stu-id="17387-124">None</span></span>

<span data-ttu-id="17387-125">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17387-125">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="17387-126">참고</span><span class="sxs-lookup"><span data-stu-id="17387-126">NOTES</span></span>

* <span data-ttu-id="17387-127">**Out** 동사를 포함 하는 Cmdlet ( **out** cmdlet)에는 이름이 나 파일 경로에 대 한 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17387-127">The cmdlets that contain the **Out** verb (the **Out** cmdlets) do not have parameters for names or file paths.</span></span> <span data-ttu-id="17387-128">**Out** cmdlet에 데이터를 보내려면 파이프라인 연산자 (|)를 사용 하 여 PowerShell 명령의 출력을 cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="17387-128">To send data to an **Out** cmdlet, use a pipeline operator (|) to send the output of a PowerShell command to the cmdlet.</span></span> <span data-ttu-id="17387-129">데이터를 변수에 저장하고 *InputObject* 매개 변수를 사용하여 데이터를 cmdlet으로 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17387-129">You can also store data in a variable and use the *InputObject* parameter to pass the data to the cmdlet.</span></span> <span data-ttu-id="17387-130">자세한 내용은 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17387-130">For more information, see the examples.</span></span>
* <span data-ttu-id="17387-131">**Out-Null** 은 출력 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17387-131">**Out-Null** does not return any output objects.</span></span> <span data-ttu-id="17387-132">**Out-Null** 출력을 Get-Member cmdlet에 파이프 하면 개체가 지정 되지 않은 것 **으로 보고 됩니다** .</span><span class="sxs-lookup"><span data-stu-id="17387-132">If you pipe the output of **Out-Null** to the Get-Member cmdlet, **Get-Member** reports that no objects have been specified.</span></span>

## <span data-ttu-id="17387-133">관련 링크</span><span class="sxs-lookup"><span data-stu-id="17387-133">RELATED LINKS</span></span>

[<span data-ttu-id="17387-134">Out-Default</span><span class="sxs-lookup"><span data-stu-id="17387-134">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="17387-135">Out-Host</span><span class="sxs-lookup"><span data-stu-id="17387-135">Out-Host</span></span>](Out-Host.md)
