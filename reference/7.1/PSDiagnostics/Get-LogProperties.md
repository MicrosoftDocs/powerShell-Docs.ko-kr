---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
Locale: en-US
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 5b95fe3bc643c9e12a3d216523c086d9b0cdf901
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211705"
---
# <span data-ttu-id="aa36f-102">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="aa36f-102">Get-LogProperties</span></span>

## <span data-ttu-id="aa36f-103">개요</span><span class="sxs-lookup"><span data-stu-id="aa36f-103">SYNOPSIS</span></span>
<span data-ttu-id="aa36f-104">Windows 이벤트 로그의 속성을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa36f-104">Retrieves the properties of a Windows event log.</span></span>

## <span data-ttu-id="aa36f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aa36f-105">SYNTAX</span></span>

```
Get-LogProperties [-Name] <Object> [<CommonParameters>]
```

## <span data-ttu-id="aa36f-106">설명</span><span class="sxs-lookup"><span data-stu-id="aa36f-106">DESCRIPTION</span></span>

<span data-ttu-id="aa36f-107">이 cmdlet은 Windows 이벤트 로그의 구성 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aa36f-107">This cmdlet gets the configuration settings of a Windows event log.</span></span> <span data-ttu-id="aa36f-108">이 cmdlet은 및 cmdlet에 사용 됩니다 `Enable-PSTrace` `Disable-PSTrace` .</span><span class="sxs-lookup"><span data-stu-id="aa36f-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

## <span data-ttu-id="aa36f-109">예제</span><span class="sxs-lookup"><span data-stu-id="aa36f-109">EXAMPLES</span></span>

### <span data-ttu-id="aa36f-110">예 1: Windows PowerShell 이벤트 로그의 구성 설정 가져오기</span><span class="sxs-lookup"><span data-stu-id="aa36f-110">Example 1: Get the configuration settings of the Windows PowerShell event log</span></span>

```powershell
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : False
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="aa36f-111">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aa36f-111">PARAMETERS</span></span>

### <span data-ttu-id="aa36f-112">-Name</span><span class="sxs-lookup"><span data-stu-id="aa36f-112">-Name</span></span>

<span data-ttu-id="aa36f-113">이벤트 공급자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="aa36f-113">The name of the event provider.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="aa36f-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aa36f-114">CommonParameters</span></span>

<span data-ttu-id="aa36f-115">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aa36f-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aa36f-116">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa36f-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aa36f-117">입력</span><span class="sxs-lookup"><span data-stu-id="aa36f-117">INPUTS</span></span>

### <span data-ttu-id="aa36f-118">System.String</span><span class="sxs-lookup"><span data-stu-id="aa36f-118">System.String</span></span>

## <span data-ttu-id="aa36f-119">출력</span><span class="sxs-lookup"><span data-stu-id="aa36f-119">OUTPUTS</span></span>

### <span data-ttu-id="aa36f-120">Microsoft. PowerShell. LogDetails</span><span class="sxs-lookup"><span data-stu-id="aa36f-120">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="aa36f-121">**Psdiagnostics** 모듈은 네임 스페이스에 **logdetails** 클래스를 추가 합니다 `Microsoft.PowerShell.Diagnostics` .</span><span class="sxs-lookup"><span data-stu-id="aa36f-121">The **PSDiagnostics** module adds the **LogDetails** class to the `Microsoft.PowerShell.Diagnostics` namespace.</span></span>

## <span data-ttu-id="aa36f-122">참고</span><span class="sxs-lookup"><span data-stu-id="aa36f-122">NOTES</span></span>

## <span data-ttu-id="aa36f-123">관련 링크</span><span class="sxs-lookup"><span data-stu-id="aa36f-123">RELATED LINKS</span></span>

[<span data-ttu-id="aa36f-124">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="aa36f-124">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="aa36f-125">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="aa36f-125">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="aa36f-126">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="aa36f-126">Disable-PSTrace</span></span>](Disable-PSTrace.md)

