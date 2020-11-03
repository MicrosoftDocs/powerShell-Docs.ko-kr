---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-DscConfiguration
ms.openlocfilehash: 25c8bc61976ce3940e0b9bd949fa3ee60728450d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213577"
---
# <span data-ttu-id="4af65-103">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4af65-103">Test-DscConfiguration</span></span>

## <span data-ttu-id="4af65-104">개요</span><span class="sxs-lookup"><span data-stu-id="4af65-104">SYNOPSIS</span></span>
<span data-ttu-id="4af65-105">노드의 실제 구성이 원하는 구성과 일치하는지 여부를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-105">Tests whether the actual configuration on the nodes matches the desired configuration.</span></span>

## <span data-ttu-id="4af65-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4af65-106">SYNTAX</span></span>

### <span data-ttu-id="4af65-107">ComputerNameSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="4af65-107">ComputerNameSet (Default)</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Detailed] [<CommonParameters>]
```

### <span data-ttu-id="4af65-108">ComputerNameAndPathSet</span><span class="sxs-lookup"><span data-stu-id="4af65-108">ComputerNameAndPathSet</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="4af65-109">ComputerNameAndReferenceConfigurationSet</span><span class="sxs-lookup"><span data-stu-id="4af65-109">ComputerNameAndReferenceConfigurationSet</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] -ReferenceConfiguration <String> [<CommonParameters>]
```

### <span data-ttu-id="4af65-110">CimSessionAndPathSet</span><span class="sxs-lookup"><span data-stu-id="4af65-110">CimSessionAndPathSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Path] <String>
 [<CommonParameters>]
```

### <span data-ttu-id="4af65-111">CimSessionAndReferenceConfigurationSet</span><span class="sxs-lookup"><span data-stu-id="4af65-111">CimSessionAndReferenceConfigurationSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob]
 -ReferenceConfiguration <String> [<CommonParameters>]
```

### <span data-ttu-id="4af65-112">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="4af65-112">CimSessionSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Detailed]
 [<CommonParameters>]
```

## <span data-ttu-id="4af65-113">설명</span><span class="sxs-lookup"><span data-stu-id="4af65-113">DESCRIPTION</span></span>
<span data-ttu-id="4af65-114">**Test-DscConfiguration** cmdlet은 노드의 실제 구성이 원하는 구성과 일치하는지 여부를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-114">The **Test-DscConfiguration** cmdlet tests whether the actual configuration on the nodes matches the desired configuration.</span></span>
<span data-ttu-id="4af65-115">컴퓨터 이름 또는 CIM(Common Information Model) (CIM) 세션을 사용 하 여 구성을 테스트 하려는 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-115">Specify which computers for which you want to test configurations by using computer names or Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="4af65-116">대상 컴퓨터를 지정하지 않으면 cmdlet이 로컬 컴퓨터의 구성을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-116">If you do not specify a target computer, the cmdlet tests configuration of the local computer.</span></span>

<span data-ttu-id="4af65-117">원하는 구성과 실제 구성이 일치 하면 cmdlet이 ' t r u e '의 문자열 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-117">If the desired and actual configurations match, the cmdlet returns a string value of 'True'.</span></span>
<span data-ttu-id="4af65-118">그렇지 않으면 ' f a l s e '의 문자열 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-118">Otherwise, it returns a string value of 'False'.</span></span>

## <span data-ttu-id="4af65-119">예제</span><span class="sxs-lookup"><span data-stu-id="4af65-119">EXAMPLES</span></span>

### <span data-ttu-id="4af65-120">예제 1: 로컬 컴퓨터에 대 한 테스트 구성</span><span class="sxs-lookup"><span data-stu-id="4af65-120">Example 1: Test configuration for the local computer</span></span>

```
PS C:\> Test-DscConfiguration
```

<span data-ttu-id="4af65-121">이 명령은 로컬 컴퓨터의 구성을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-121">This command tests configuration for the local computer.</span></span>

### <span data-ttu-id="4af65-122">예 2: 지정 된 컴퓨터에 대 한 구성 테스트</span><span class="sxs-lookup"><span data-stu-id="4af65-122">Example 2: Test configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Test-DscConfiguration -CimSession $Session
```

<span data-ttu-id="4af65-123">이 예제에서는 CIM 세션에 지정된 컴퓨터의 구성을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-123">This example test configuration from a computer specified by a CIM session.</span></span>
<span data-ttu-id="4af65-124">또한 cmdlet에 사용하기 위해 이름이 Server01인 컴퓨터에 대한 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-124">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="4af65-125">또는 지정한 여러 컴퓨터에 cmdlet을 적용하기 위해 CIM 세션 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-125">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="4af65-126">첫 번째 명령은 **New-CimSession** cmdlet을 사용하여 CIM 세션을 만든 다음 **CimSession** 개체를 $Session 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-126">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="4af65-127">또한 암호를 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-127">The command prompts you for a password.</span></span>
<span data-ttu-id="4af65-128">자세한 내용을 보려면 `Get-Help New-CimSession`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="4af65-128">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="4af65-129">두 번째 명령은 $Session 변수에 저장 된 **CimSession** 개체로 식별 된 컴퓨터 (이 경우 이름이 Server01 인 컴퓨터)의 구성을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-129">The second command tests configuration for the computers identified by the **CimSession** objects stored in the $Session variable, in this case, the computer named Server01.</span></span>

### <span data-ttu-id="4af65-130">예제 3: 자세한 결과를 포함 하는 테스트 구성</span><span class="sxs-lookup"><span data-stu-id="4af65-130">Example 3: Test configurations with detailed results</span></span>

```
PS C:\> Test-DscConfiguration -ComputerName "Server01", "Server02", "Server03" -Detailed
```

<span data-ttu-id="4af65-131">이 명령은 *ComputerName* 매개 변수로 지정 된 컴퓨터 집합에 대 한 구성을 테스트 하 고 전체 상태, 원하는 상태에 있는 리소스, 원하는 상태 및 컴퓨터 이름에 없는 리소스를 포함 하는 세부 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-131">This command tests configurations for a set of computers specified by the *ComputerName* parameter and returns detailed information that includes the overall state, resources that are in the desired state, resources that are not in the desired state and computer name.</span></span>

### <span data-ttu-id="4af65-132">예제 4: 폴더에 지정 된 테스트 구성</span><span class="sxs-lookup"><span data-stu-id="4af65-132">Example 4: Test configurations specified in a folder</span></span>

```
PS C:\> Test-DscConfiguration -Path "C:\Dsc\Configurations"
```

<span data-ttu-id="4af65-133">이 명령은 *Path* 매개 변수로 지정 된 폴더에 정의 된 구성을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-133">This command tests configurations that are defined in a folder specified by the *Path* parameter.</span></span>
<span data-ttu-id="4af65-134">구성은 구성 파일의 파일 이름으로 식별 되는 컴퓨터 집합에 대해 테스트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-134">The configurations are tested against a set of computers, each identified by the file name of the configuration file.</span></span>

### <span data-ttu-id="4af65-135">예 5: 파일에 지정 된 테스트 구성</span><span class="sxs-lookup"><span data-stu-id="4af65-135">Example 5: Test configurations specified in a file</span></span>

```
PS C:\> Test-DscConfiguration -ReferenceConfiguration "C:\Dsc\Configurations\WebServer.mof" -ComputerName "Server01", "Server02", "Server03"
```

<span data-ttu-id="4af65-136">이 명령은 *ComputerName* 매개 변수로 지정 된 컴퓨터 집합에 대해 파일에 정의 된 구성을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-136">This command tests a configuration defined in a file against a set of computers specified by the *ComputerName* parameter.</span></span>

## <span data-ttu-id="4af65-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4af65-137">PARAMETERS</span></span>

### <span data-ttu-id="4af65-138">-AsJob</span><span class="sxs-lookup"><span data-stu-id="4af65-138">-AsJob</span></span>
<span data-ttu-id="4af65-139">이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-139">Indicates that this cmdlet runs the command as a background job.</span></span>

<span data-ttu-id="4af65-140">*AsJob* 매개 변수를 지정 하는 경우이 명령은 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-140">If you specify the *AsJob* parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span>
<span data-ttu-id="4af65-141">작업이 완료 될 때까지 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-141">You can continue to work in the session until the job finishes.</span></span>
<span data-ttu-id="4af65-142">AsJob 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-142">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="4af65-143">작업을 관리하려면 Job cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-143">To manage the job, use the Job cmdlets.</span></span>
<span data-ttu-id="4af65-144">작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="4af65-144">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="4af65-145">이 매개 변수를 사용 하려면 로컬 및 원격 컴퓨터를 원격으로 구성 하 고 Windows Vista 이상 버전의 Windows 운영 체제에서는 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-145">To use this parameter, the local and remote computers must be configured for remoting, and on Windows Vista and later versions of the Windows operating system, you must open Windows PowerShell with the Run as administrator option.</span></span>
<span data-ttu-id="4af65-146">자세한 내용은 [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4af65-146">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="4af65-147">Windows PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 및 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4af65-147">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="4af65-148">-CimSession</span><span class="sxs-lookup"><span data-stu-id="4af65-148">-CimSession</span></span>
<span data-ttu-id="4af65-149">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-149">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="4af65-150">[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-150">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="4af65-151">기본값은 로컬 컴퓨터의 현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-151">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndReferenceConfigurationSet, CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4af65-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4af65-152">-ComputerName</span></span>
<span data-ttu-id="4af65-153">이 cmdlet이 구성을 테스트 하는 컴퓨터 이름의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-153">Specifies an array of computer names on which this cmdlet tests the configuration.</span></span>
<span data-ttu-id="4af65-154">Cmdlet은 *Path* 매개 변수로 지정 된 위치에 있는 구성 문서를 이러한 컴퓨터에 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-154">The cmdlet tests the configuration document in the location specified by the *Path* parameter to these computers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4af65-155">-Credential</span><span class="sxs-lookup"><span data-stu-id="4af65-155">-Credential</span></span>
<span data-ttu-id="4af65-156">대상 컴퓨터에 대한 사용자 이름과 암호를 **PSCredential** 개체로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-156">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="4af65-157">**PSCredential** 개체를 가져오려면 Get-Credential cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-157">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="4af65-158">자세한 내용을 보려면 `Get-Help Get-Credential`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="4af65-158">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4af65-159">-Detailed</span><span class="sxs-lookup"><span data-stu-id="4af65-159">-Detailed</span></span>
<span data-ttu-id="4af65-160">이 cmdlet이 구성 문서를 노드의 원하는 상태와 비교한 결과를 자세히 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-160">Indicates that this cmdlet returns a detailed result of comparing the configuration document with the desired state of the nodes.</span></span>
<span data-ttu-id="4af65-161">결과에는 전체 상태, 원하는 상태에 있는 리소스, 원하는 상태가 아닌 리소스, 컴퓨터 이름 등의 정보가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-161">The result includes information such as overall state, resources that are in the desired state, resources that are not in desired state, and computer name.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameSet, CimSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4af65-162">-Path</span><span class="sxs-lookup"><span data-stu-id="4af65-162">-Path</span></span>
<span data-ttu-id="4af65-163">구성 문서 파일을 포함 하는 폴더의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-163">Specifies the path of a folder that contains configuration document files.</span></span>
<span data-ttu-id="4af65-164">Cmdlet은 *ComputerName* 또는 *CimSession* 매개 변수로 지정 된 컴퓨터의 원하는 상태에 대해 구성을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-164">The cmdlet tests the configuration against the desired state of computers specified by the *ComputerName* or *CimSession* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4af65-165">-ReferenceConfiguration</span><span class="sxs-lookup"><span data-stu-id="4af65-165">-ReferenceConfiguration</span></span>
<span data-ttu-id="4af65-166">구성 문서 파일의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-166">Specifies the path of the configuration document file.</span></span>
<span data-ttu-id="4af65-167">이 cmdlet은 *ComputerName* 또는 *CimSession* 매개 변수로 지정 된 컴퓨터의 실제 상태에 대 한 구성을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-167">This cmdlet tests the configuration against the actual state of computers specified by the *ComputerName* or *CimSession* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndReferenceConfigurationSet, CimSessionAndReferenceConfigurationSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4af65-168">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="4af65-168">-ThrottleLimit</span></span>
<span data-ttu-id="4af65-169">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-169">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="4af65-170">이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-170">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="4af65-171">스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4af65-171">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="4af65-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4af65-172">CommonParameters</span></span>
<span data-ttu-id="4af65-173">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4af65-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4af65-174">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4af65-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4af65-175">입력</span><span class="sxs-lookup"><span data-stu-id="4af65-175">INPUTS</span></span>

## <span data-ttu-id="4af65-176">출력</span><span class="sxs-lookup"><span data-stu-id="4af65-176">OUTPUTS</span></span>

## <span data-ttu-id="4af65-177">참고</span><span class="sxs-lookup"><span data-stu-id="4af65-177">NOTES</span></span>

## <span data-ttu-id="4af65-178">관련 링크</span><span class="sxs-lookup"><span data-stu-id="4af65-178">RELATED LINKS</span></span>

[<span data-ttu-id="4af65-179">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="4af65-179">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="4af65-180">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4af65-180">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="4af65-181">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="4af65-181">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="4af65-182">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4af65-182">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="4af65-183">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4af65-183">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)
