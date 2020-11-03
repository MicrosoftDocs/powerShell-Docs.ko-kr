---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: d6ad6f8cc299351cc85d4ed7e7b9682a1d90307b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217081"
---
# <span data-ttu-id="7827a-102">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="7827a-102">Set-LogProperties</span></span>

## <span data-ttu-id="7827a-103">개요</span><span class="sxs-lookup"><span data-stu-id="7827a-103">SYNOPSIS</span></span>
<span data-ttu-id="7827a-104">Windows 이벤트 로그의 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7827a-104">Changes the properties of a Windows event log.</span></span>

## <span data-ttu-id="7827a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7827a-105">SYNTAX</span></span>

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="7827a-106">설명</span><span class="sxs-lookup"><span data-stu-id="7827a-106">DESCRIPTION</span></span>

<span data-ttu-id="7827a-107">이 cmdlet은 Windows 이벤트 로그의 구성 설정을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7827a-107">This cmdlet changes the configuration settings of a Windows event log.</span></span> <span data-ttu-id="7827a-108">이 cmdlet은 및 cmdlet에 사용 됩니다 `Enable-PSTrace` `Disable-PSTrace` .</span><span class="sxs-lookup"><span data-stu-id="7827a-108">This cmdlet is used by the `Enable-PSTrace` and `Disable-PSTrace` cmdlets.</span></span>

<span data-ttu-id="7827a-109">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7827a-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="7827a-110">예제</span><span class="sxs-lookup"><span data-stu-id="7827a-110">EXAMPLES</span></span>

### <span data-ttu-id="7827a-111">예 1: Windows PowerShell 이벤트 로그의 보존 설정 변경</span><span class="sxs-lookup"><span data-stu-id="7827a-111">Example 1: Change the retention setting of the Windows PowerShell event log</span></span>

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

## <span data-ttu-id="7827a-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7827a-112">PARAMETERS</span></span>

### <span data-ttu-id="7827a-113">-Force</span><span class="sxs-lookup"><span data-stu-id="7827a-113">-Force</span></span>

<span data-ttu-id="7827a-114">메시지를 표시 하지 않고 강제로 변경 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7827a-114">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="7827a-115">-LogDetails</span><span class="sxs-lookup"><span data-stu-id="7827a-115">-LogDetails</span></span>

<span data-ttu-id="7827a-116">이벤트 로그에 할당할 업데이트 된 구성 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="7827a-116">The updated configuration settings to be assigned to the event log.</span></span>

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

### <span data-ttu-id="7827a-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7827a-117">CommonParameters</span></span>

<span data-ttu-id="7827a-118">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7827a-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7827a-119">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7827a-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7827a-120">입력</span><span class="sxs-lookup"><span data-stu-id="7827a-120">INPUTS</span></span>

### <span data-ttu-id="7827a-121">Microsoft. PowerShell. LogDetails</span><span class="sxs-lookup"><span data-stu-id="7827a-121">Microsoft.PowerShell.Diagnostics.LogDetails</span></span>

<span data-ttu-id="7827a-122">완전히 구성 된 **Logdetails** 개체를 cmdlet에 전달 해야 합니다 `Set-LogProperties` .</span><span class="sxs-lookup"><span data-stu-id="7827a-122">You must pass a fully configured **LogDetails** object to the `Set-LogProperties` cmdlet.</span></span>
<span data-ttu-id="7827a-123">따라서 하나의 설정을 변경 하려면를 사용 `Get-LogProperties` 하 여 현재 구성을 검색 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7827a-123">Therefore, to change one setting, you should use `Get-LogProperties` to retrieve the current configuration.</span></span>

## <span data-ttu-id="7827a-124">출력</span><span class="sxs-lookup"><span data-stu-id="7827a-124">OUTPUTS</span></span>

### <span data-ttu-id="7827a-125">없음</span><span class="sxs-lookup"><span data-stu-id="7827a-125">None</span></span>

## <span data-ttu-id="7827a-126">참고</span><span class="sxs-lookup"><span data-stu-id="7827a-126">NOTES</span></span>

<span data-ttu-id="7827a-127">관리자 권한 PowerShell 세션에서이 cmdlet을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7827a-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="7827a-128">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7827a-128">RELATED LINKS</span></span>

[<span data-ttu-id="7827a-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="7827a-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="7827a-130">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="7827a-130">Enable-PSTrace</span></span>](Enable-PSTrace.md)

[<span data-ttu-id="7827a-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="7827a-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
