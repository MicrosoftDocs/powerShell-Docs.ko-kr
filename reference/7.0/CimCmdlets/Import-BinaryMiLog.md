---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: 800cd9ea24bad09f532db26c5091735cd987eef0
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195056"
---
# <span data-ttu-id="6eeee-102">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="6eeee-102">Import-BinaryMiLog</span></span>

## <span data-ttu-id="6eeee-103">개요</span><span class="sxs-lookup"><span data-stu-id="6eeee-103">SYNOPSIS</span></span>
<span data-ttu-id="6eeee-104">내보내기 파일의 내용에 따라 저장 된 개체를 다시 만드는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6eeee-104">Used to re-create the saved objects based on the contents of an export file.</span></span>

## <span data-ttu-id="6eeee-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6eeee-105">SYNTAX</span></span>

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="6eeee-106">설명</span><span class="sxs-lookup"><span data-stu-id="6eeee-106">DESCRIPTION</span></span>

<span data-ttu-id="6eeee-107">이 cmdlet을 사용 하 여에서 만든 내보내기 파일의 내용에 따라 저장 된 개체를 다시 만들 수 `Export-BinaryMILog` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6eeee-107">Use this cmdlet to re-create saved objects based on the contents of an export file created by `Export-BinaryMILog`.</span></span> <span data-ttu-id="6eeee-108">이 cmdlet은 `Import-Clixml` `Export-BinaryMILog` 결과 개체를 이진 인코딩 파일에 저장 한다는 점을 제외 하 고와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="6eeee-108">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="6eeee-109">예제</span><span class="sxs-lookup"><span data-stu-id="6eeee-109">EXAMPLES</span></span>

### <span data-ttu-id="6eeee-110">예제 1-파일로 내보낸 개체 복원</span><span class="sxs-lookup"><span data-stu-id="6eeee-110">Example 1 - Restore objects exported to a file</span></span>

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## <span data-ttu-id="6eeee-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6eeee-111">PARAMETERS</span></span>

### <span data-ttu-id="6eeee-112">-Path</span><span class="sxs-lookup"><span data-stu-id="6eeee-112">-Path</span></span>

<span data-ttu-id="6eeee-113">개체의 이진 표현을 저장할 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6eeee-113">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="6eeee-114">**Path** 매개 변수는 와일드 카드 및 상대 경로를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="6eeee-114">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="6eeee-115">이 cmdlet은 경로가 둘 이상의 파일로 확인 될 경우 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="6eeee-115">This cmdlet generates an error if the path resolves to more than one file.</span></span>

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

### <span data-ttu-id="6eeee-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6eeee-116">CommonParameters</span></span>
<span data-ttu-id="6eeee-117">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6eeee-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6eeee-118">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6eeee-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6eeee-119">입력</span><span class="sxs-lookup"><span data-stu-id="6eeee-119">INPUTS</span></span>

### <span data-ttu-id="6eeee-120">None</span><span class="sxs-lookup"><span data-stu-id="6eeee-120">None</span></span>

## <span data-ttu-id="6eeee-121">출력</span><span class="sxs-lookup"><span data-stu-id="6eeee-121">OUTPUTS</span></span>

### <span data-ttu-id="6eeee-122">System.Object</span><span class="sxs-lookup"><span data-stu-id="6eeee-122">System.Object</span></span>

## <span data-ttu-id="6eeee-123">참고</span><span class="sxs-lookup"><span data-stu-id="6eeee-123">NOTES</span></span>

## <span data-ttu-id="6eeee-124">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6eeee-124">RELATED LINKS</span></span>
