---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: a852a3016d7e63d17b86cf2efb3c928d2f7b901c
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194539"
---
# <span data-ttu-id="d602f-102">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d602f-102">Set-LogProperties</span></span>

## <span data-ttu-id="d602f-103">개요</span><span class="sxs-lookup"><span data-stu-id="d602f-103">SYNOPSIS</span></span>
<span data-ttu-id="d602f-104">Windows 이벤트 로그의 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d602f-104">Changes the properties of a Windows event log.</span></span>

## <span data-ttu-id="d602f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d602f-105">SYNTAX</span></span>

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="d602f-106">설명</span><span class="sxs-lookup"><span data-stu-id="d602f-106">DESCRIPTION</span></span>

<span data-ttu-id="d602f-107">이 cmdlet은 Windows 이벤트 로그의 구성 설정을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d602f-107">This cmdlet changes the configuration settings of a Windows event log.</span></span> <span data-ttu-id="d602f-108">이 cmdlet은 및 cmdlet에 사용 됩니다 `Enable-PSTrace` `Disable-PSTrace` .</span><span class="sxs-lookup"><span data-stu-id="d602f-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

<span data-ttu-id="d602f-109">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d602f-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d602f-110">예제</span><span class="sxs-lookup"><span data-stu-id="d602f-110">EXAMPLES</span></span>

### <span data-ttu-id="d602f-111">예 1: Windows PowerShell 이벤트 로그의 보존 설정 변경</span><span class="sxs-lookup"><span data-stu-id="d602f-111">Example 1: Change the retention setting of the Windows PowerShell event log</span></span>

```powershell
$logDetails = Get-LogProperties 'Windows PowerShell'
$logDetails.Retention = $True
Set-LogProperties -LogDetails $logDetails
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : True
AutoBackup : False
MaxLogSize : 15728640
```

## <span data-ttu-id="d602f-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d602f-112">PARAMETERS</span></span>

### <span data-ttu-id="d602f-113">-Force</span><span class="sxs-lookup"><span data-stu-id="d602f-113">-Force</span></span>

<span data-ttu-id="d602f-114">메시지를 표시 하지 않고 강제로 변경 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d602f-114">Used to force the change without prompting.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d602f-115">-LogDetails</span><span class="sxs-lookup"><span data-stu-id="d602f-115">-LogDetails</span></span>

<span data-ttu-id="d602f-116">이벤트 로그에 할당할 업데이트 된 구성 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="d602f-116">The updated configuration settings to be assigned to the event log.</span></span>

```yaml
Type: Microsoft.PowerShell.Diagnostics.LogDetails
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d602f-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d602f-117">CommonParameters</span></span>

<span data-ttu-id="d602f-118">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d602f-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d602f-119">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d602f-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d602f-120">입력</span><span class="sxs-lookup"><span data-stu-id="d602f-120">INPUTS</span></span>

### <span data-ttu-id="d602f-121">Microsoft. PowerShell. LogDetails</span><span class="sxs-lookup"><span data-stu-id="d602f-121">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="d602f-122">완전히 구성 된 **Logdetails** 개체를 cmdlet에 전달 해야 합니다 `Set-LogProperties` .</span><span class="sxs-lookup"><span data-stu-id="d602f-122">You must pass a fully configured **LogDetails** object to the `Set-LogProperties` cmdlet.</span></span>
<span data-ttu-id="d602f-123">따라서 하나의 설정을 변경 하려면를 사용 `Get-LogProperties` 하 여 현재 구성을 검색 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d602f-123">Therefore, to change one setting, you should use `Get-LogProperties` to retrieve the current configuration.</span></span>

## <span data-ttu-id="d602f-124">출력</span><span class="sxs-lookup"><span data-stu-id="d602f-124">OUTPUTS</span></span>

### <span data-ttu-id="d602f-125">System.Object</span><span class="sxs-lookup"><span data-stu-id="d602f-125">System.Object</span></span>

## <span data-ttu-id="d602f-126">참고</span><span class="sxs-lookup"><span data-stu-id="d602f-126">NOTES</span></span>

<span data-ttu-id="d602f-127">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d602f-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d602f-128">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d602f-128">RELATED LINKS</span></span>

[<span data-ttu-id="d602f-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="d602f-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="d602f-130">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d602f-130">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="d602f-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="d602f-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
