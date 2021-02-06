---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: d280eba2e717ccfb0b896d62f42079390d1db848
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601444"
---
# <span data-ttu-id="d043e-102">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d043e-102">Remove-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="d043e-103">개요</span><span class="sxs-lookup"><span data-stu-id="d043e-103">SYNOPSIS</span></span>
<span data-ttu-id="d043e-104">키 바인딩을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="d043e-104">Removes a key binding.</span></span>

## <span data-ttu-id="d043e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d043e-105">SYNTAX</span></span>

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## <span data-ttu-id="d043e-106">설명</span><span class="sxs-lookup"><span data-stu-id="d043e-106">DESCRIPTION</span></span>

<span data-ttu-id="d043e-107">`Remove-PSReadLineKeyHandler`Cmdlet은 지정 된 키 바인딩을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="d043e-107">The `Remove-PSReadLineKeyHandler` cmdlet removes a specified key binding.</span></span>

## <span data-ttu-id="d043e-108">예제</span><span class="sxs-lookup"><span data-stu-id="d043e-108">EXAMPLES</span></span>

### <span data-ttu-id="d043e-109">예제 1: 바인딩 제거</span><span class="sxs-lookup"><span data-stu-id="d043e-109">Example 1: Remove a binding</span></span>

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

<span data-ttu-id="d043e-110">이 명령은 키 조합 또는 동시에서 바인딩을 제거 합니다 `Ctrl+B` .</span><span class="sxs-lookup"><span data-stu-id="d043e-110">This command removes the binding from the key combination, or chord, `Ctrl+B`.</span></span> <span data-ttu-id="d043e-111">`Ctrl+B`이 문서에는 현가 만들어집니다 `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="d043e-111">The `Ctrl+B` chord is created in the `Set-PSReadLineKeyHandler` article.</span></span>

## <span data-ttu-id="d043e-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d043e-112">PARAMETERS</span></span>

### <span data-ttu-id="d043e-113">-현</span><span class="sxs-lookup"><span data-stu-id="d043e-113">-Chord</span></span>

<span data-ttu-id="d043e-114">제거할 키의 배열이 나 시퀀스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d043e-114">Specifies an array of keys or sequences of keys to be removed.</span></span> <span data-ttu-id="d043e-115">단일 바인딩은 단일 문자열을 사용 하 여 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d043e-115">A single binding is specified by using a single string.</span></span> <span data-ttu-id="d043e-116">바인딩이 키 시퀀스 인 경우 다음 예제와 같이 키를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="d043e-116">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+x,Ctrl+l`

<span data-ttu-id="d043e-117">이 매개 변수는 문자열 배열을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d043e-117">This parameter accepts an array of strings.</span></span> <span data-ttu-id="d043e-118">각 문자열은 단일 바인딩의 키 시퀀스가 아닌 별도의 바인딩입니다.</span><span class="sxs-lookup"><span data-stu-id="d043e-118">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d043e-119">-ViMode</span><span class="sxs-lookup"><span data-stu-id="d043e-119">-ViMode</span></span>

<span data-ttu-id="d043e-120">바인딩이 적용 되는 vi 모드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d043e-120">Specify which vi mode the binding applies to.</span></span> <span data-ttu-id="d043e-121">가능한 값은 Insert, Command입니다.</span><span class="sxs-lookup"><span data-stu-id="d043e-121">Possible values are: Insert, Command.</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:
Accepted values: Insert, Command

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d043e-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d043e-122">CommonParameters</span></span>

<span data-ttu-id="d043e-123">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d043e-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d043e-124">자세한 내용은 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d043e-124">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d043e-125">입력</span><span class="sxs-lookup"><span data-stu-id="d043e-125">INPUTS</span></span>

### <span data-ttu-id="d043e-126">없음</span><span class="sxs-lookup"><span data-stu-id="d043e-126">None</span></span>

<span data-ttu-id="d043e-127">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d043e-127">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="d043e-128">출력</span><span class="sxs-lookup"><span data-stu-id="d043e-128">OUTPUTS</span></span>

### <span data-ttu-id="d043e-129">없음</span><span class="sxs-lookup"><span data-stu-id="d043e-129">None</span></span>

## <span data-ttu-id="d043e-130">참고</span><span class="sxs-lookup"><span data-stu-id="d043e-130">NOTES</span></span>

## <span data-ttu-id="d043e-131">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d043e-131">RELATED LINKS</span></span>

[<span data-ttu-id="d043e-132">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d043e-132">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="d043e-133">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d043e-133">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="d043e-134">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d043e-134">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="d043e-135">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d043e-135">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)

