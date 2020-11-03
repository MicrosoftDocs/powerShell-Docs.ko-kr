---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: ce5dd31170bc47edaa04ca3c31deab62dc4ec354
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224994"
---
# <span data-ttu-id="c5d55-103">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="c5d55-103">Import-BinaryMiLog</span></span>

## <span data-ttu-id="c5d55-104">개요</span><span class="sxs-lookup"><span data-stu-id="c5d55-104">SYNOPSIS</span></span>
<span data-ttu-id="c5d55-105">내보내기 파일의 내용에 따라 저장 된 개체를 다시 만드는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5d55-105">Used to re-create the saved objects based on the contents of an export file.</span></span>

## <span data-ttu-id="c5d55-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c5d55-106">SYNTAX</span></span>

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="c5d55-107">설명</span><span class="sxs-lookup"><span data-stu-id="c5d55-107">DESCRIPTION</span></span>

<span data-ttu-id="c5d55-108">이 cmdlet을 사용 하 여에서 만든 내보내기 파일의 내용에 따라 저장 된 개체를 다시 만들 수 `Export-BinaryMILog` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5d55-108">Use this cmdlet to re-create saved objects based on the contents of an export file created by `Export-BinaryMILog`.</span></span> <span data-ttu-id="c5d55-109">이 cmdlet은 `Import-Clixml` `Export-BinaryMILog` 결과 개체를 이진 인코딩 파일에 저장 한다는 점을 제외 하 고와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="c5d55-109">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="c5d55-110">예제</span><span class="sxs-lookup"><span data-stu-id="c5d55-110">EXAMPLES</span></span>

### <span data-ttu-id="c5d55-111">예제 1-파일로 내보낸 개체 복원</span><span class="sxs-lookup"><span data-stu-id="c5d55-111">Example 1 - Restore objects exported to a file</span></span>

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## <span data-ttu-id="c5d55-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c5d55-112">PARAMETERS</span></span>

### <span data-ttu-id="c5d55-113">-Path</span><span class="sxs-lookup"><span data-stu-id="c5d55-113">-Path</span></span>

<span data-ttu-id="c5d55-114">개체의 이진 표현을 저장할 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5d55-114">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="c5d55-115">**Path** 매개 변수는 와일드 카드 및 상대 경로를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5d55-115">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="c5d55-116">이 cmdlet은 경로가 둘 이상의 파일로 확인 될 경우 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5d55-116">This cmdlet generates an error if the path resolves to more than one file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c5d55-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c5d55-117">CommonParameters</span></span>
<span data-ttu-id="c5d55-118">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c5d55-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c5d55-119">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c5d55-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c5d55-120">입력</span><span class="sxs-lookup"><span data-stu-id="c5d55-120">INPUTS</span></span>

### <span data-ttu-id="c5d55-121">없음</span><span class="sxs-lookup"><span data-stu-id="c5d55-121">None</span></span>

## <span data-ttu-id="c5d55-122">출력</span><span class="sxs-lookup"><span data-stu-id="c5d55-122">OUTPUTS</span></span>

### <span data-ttu-id="c5d55-123">System.Object</span><span class="sxs-lookup"><span data-stu-id="c5d55-123">System.Object</span></span>

## <span data-ttu-id="c5d55-124">참고</span><span class="sxs-lookup"><span data-stu-id="c5d55-124">NOTES</span></span>

## <span data-ttu-id="c5d55-125">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c5d55-125">RELATED LINKS</span></span>
