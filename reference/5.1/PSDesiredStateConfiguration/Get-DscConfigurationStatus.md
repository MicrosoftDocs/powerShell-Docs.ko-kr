---
external help file: Get-DscConfigurationStatus.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfigurationStatus
ms.openlocfilehash: 0d59ce58a70eab68441ea1fe6097bbdf7792a54f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215362"
---
# <span data-ttu-id="d1bf3-103">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="d1bf3-103">Get-DscConfigurationStatus</span></span>

## <span data-ttu-id="d1bf3-104">개요</span><span class="sxs-lookup"><span data-stu-id="d1bf3-104">SYNOPSIS</span></span>
<span data-ttu-id="d1bf3-105">완료 된 구성 실행에 대 한 데이터를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-105">Retrieves data about completed configuration runs.</span></span>

## <span data-ttu-id="d1bf3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d1bf3-106">SYNTAX</span></span>

```
Get-DscConfigurationStatus [-All] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## <span data-ttu-id="d1bf3-107">설명</span><span class="sxs-lookup"><span data-stu-id="d1bf3-107">DESCRIPTION</span></span>
<span data-ttu-id="d1bf3-108">**Get DscConfigurationStatus** cmdlet은 시스템에서 완료 된 구성 실행에 대 한 자세한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-108">The **Get-DscConfigurationStatus** cmdlet retrieves detailed information about completed configuration runs on the system.</span></span>
<span data-ttu-id="d1bf3-109">기본적으로 마지막 구성 실행에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-109">By default, it returns the information about the last configuration run.</span></span>
<span data-ttu-id="d1bf3-110">이 cmdlet은 구성이 실행 된 시간, 실행 상태, 구성의 리소스 수, 성공 또는 실패 한 리소스와 같은 구성 실행에 대 한 기록 정보를 찾는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-110">This cmdlet is useful for finding historical information about configuration runs, such as when the configurations were run, the status of the runs, the number of resources in the configurations, and which resources succeeded or failed.</span></span>

## <span data-ttu-id="d1bf3-111">예제</span><span class="sxs-lookup"><span data-stu-id="d1bf3-111">EXAMPLES</span></span>

### <span data-ttu-id="d1bf3-112">예제 1: 마지막 구성 실행에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="d1bf3-112">Example 1: Get information on the last configuration run</span></span>

```
PS C:\> Get-DscConfigurationStatus
```

<span data-ttu-id="d1bf3-113">이 명령은 마지막 구성 실행에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-113">This command gets information on the last configuration run.</span></span>

### <span data-ttu-id="d1bf3-114">예제 2: 모든 구성에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="d1bf3-114">Example 2: Get information on all configurations</span></span>

```
PS C:\> Get-DscConfigurationStatus -All
```

<span data-ttu-id="d1bf3-115">이 명령은 Windows PowerShell DSC (필요한 상태 구성) 일관성 확인을 포함 하 여 시스템에서 실행 된 모든 구성에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-115">This command gets information about all the configurations that were run on the system, including the Windows PowerShell Desired State Configuration (DSC) consistency check.</span></span>

### <span data-ttu-id="d1bf3-116">예 3: 원격 컴퓨터에서 구성 실행에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="d1bf3-116">Example 3: Get information on the configuration run on a remote computer</span></span>

```
PS C:\> Get-DscConfigurationStatus -CimSession "Server01"
```

<span data-ttu-id="d1bf3-117">이 명령은 Server01 라는 원격 컴퓨터의 구성 실행 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-117">This command gets the configuration run details of the remote computer named Server01.</span></span>
<span data-ttu-id="d1bf3-118">이 경우 WSMan 전송을 사용 하 여 원격 컴퓨터에 연결 하 고 연결 하는 사용자가 원격 컴퓨터의 관리자 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-118">This uses the WSMan transport to connect to the remote computer and requires that the connecting user be an administrator on the remote computer.</span></span>

## <span data-ttu-id="d1bf3-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d1bf3-119">PARAMETERS</span></span>

### <span data-ttu-id="d1bf3-120">-All</span><span class="sxs-lookup"><span data-stu-id="d1bf3-120">-All</span></span>
<span data-ttu-id="d1bf3-121">이 cmdlet은 구성 응용 프로그램 및 일관성 확인을 포함 하 여 컴퓨터에서 실행 되는 모든 구성에 대 한 정보를 검색 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-121">Indicates that this cmdlet retrieves information about all the configuration runs on the computer, including the configuration application and the consistency check.</span></span>

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

### <span data-ttu-id="d1bf3-122">-AsJob</span><span class="sxs-lookup"><span data-stu-id="d1bf3-122">-AsJob</span></span>
<span data-ttu-id="d1bf3-123">이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-123">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="d1bf3-124">-CimSession</span><span class="sxs-lookup"><span data-stu-id="d1bf3-124">-CimSession</span></span>
<span data-ttu-id="d1bf3-125">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-125">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="d1bf3-126">[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-126">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="d1bf3-127">기본값은 로컬 컴퓨터의 현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-127">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d1bf3-128">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="d1bf3-128">-ThrottleLimit</span></span>
<span data-ttu-id="d1bf3-129">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-129">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="d1bf3-130">이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-130">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="d1bf3-131">스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-131">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d1bf3-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d1bf3-132">CommonParameters</span></span>
<span data-ttu-id="d1bf3-133">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d1bf3-134">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d1bf3-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d1bf3-135">입력</span><span class="sxs-lookup"><span data-stu-id="d1bf3-135">INPUTS</span></span>

## <span data-ttu-id="d1bf3-136">출력</span><span class="sxs-lookup"><span data-stu-id="d1bf3-136">OUTPUTS</span></span>

## <span data-ttu-id="d1bf3-137">참고</span><span class="sxs-lookup"><span data-stu-id="d1bf3-137">NOTES</span></span>

## <span data-ttu-id="d1bf3-138">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d1bf3-138">RELATED LINKS</span></span>

[<span data-ttu-id="d1bf3-139">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="d1bf3-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="d1bf3-140">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1bf3-140">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="d1bf3-141">Get DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d1bf3-141">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

[<span data-ttu-id="d1bf3-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1bf3-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="d1bf3-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1bf3-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="d1bf3-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1bf3-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
