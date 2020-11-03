---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: d73d8d6a30e6b7c08b5a0b7988ea2327be34002a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215313"
---
# <span data-ttu-id="99273-103">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="99273-103">Invoke-DscResource</span></span>

## <span data-ttu-id="99273-104">개요</span><span class="sxs-lookup"><span data-stu-id="99273-104">SYNOPSIS</span></span>
<span data-ttu-id="99273-105">지정 된 DSC 리소스의 메서드를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-105">Runs a method of a specified DSC resource.</span></span>

## <span data-ttu-id="99273-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="99273-106">SYNTAX</span></span>

```
Invoke-DscResource [-Name] <String> [-Method] <String> -ModuleName <ModuleSpecification> -Property <Hashtable>
 [<CommonParameters>]
```

## <span data-ttu-id="99273-107">설명</span><span class="sxs-lookup"><span data-stu-id="99273-107">DESCRIPTION</span></span>
<span data-ttu-id="99273-108">**Get-dscresource** cmdlet은 지정 된 WINDOWS PowerShell DSC (필요한 상태 구성) 리소스의 메서드를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-108">The **Invoke-DscResource** cmdlet runs a method of a specified Windows PowerShell Desired State Configuration (DSC) resource.</span></span>
<span data-ttu-id="99273-109">이 cmdlet을 실행 하기 전에 로컬 Configuration Manager (LCM)의 새로 고침 모드를 사용 안 함으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-109">Before you run this cmdlet, set the refresh mode of the Local Configuration Manager (LCM) to Disabled.</span></span>

<span data-ttu-id="99273-110">이 cmdlet은 구성 문서를 만들지 않고 DSC 리소스를 직접 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-110">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span>
<span data-ttu-id="99273-111">이 cmdlet을 사용 하 여 구성 관리 제품은 DSC 리소스를 사용 하 여 windows를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99273-111">Using this cmdlet, configuration management products can manage windows by using DSC resources.</span></span>
<span data-ttu-id="99273-112">이 cmdlet을 사용 하면 디버깅을 사용 하도록 설정한 상태에서 DSC 엔진 또는 LCM이 실행 중일 때에도 리소스를 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99273-112">This cmdlet also enables debugging of resources when the DSC engine or LCM is running with debugging enabled.</span></span>

## <span data-ttu-id="99273-113">예제</span><span class="sxs-lookup"><span data-stu-id="99273-113">EXAMPLES</span></span>

### <span data-ttu-id="99273-114">예제 1: 필수 속성을 지정 하 여 리소스의 Set 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-114">Example 1: Invoke the Set method of a resource by specifying its mandatory properties</span></span>

```
PS C:\> Invoke-DscResource -Name Log -Method Set -Property @{Message = 'Hello World'} -ModuleName PSDesiredStateConfiguration
```

<span data-ttu-id="99273-115">이 명령은 Log 라는 리소스의 **Set** 메서드를 호출 하 고이에 대 한 **메시지** 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-115">This command invokes the **Set** method of a resource named Log and specifies a **Message** property for it.</span></span>

### <span data-ttu-id="99273-116">예제 2: 지정 된 모듈에 대 한 리소스의 테스트 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="99273-116">Example 2: Invoke the Test method of a resource for a specified module</span></span>

```
PS C:\> Invoke-DscResource -Name WindowsProcess -Method Test -Property @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''} -ModuleName PSDesiredStateConfiguration
```

<span data-ttu-id="99273-117">이 명령은 PSDesiredStateConfiguration 라는 모듈에 있는 WindowsProcess 라는 리소스의 **테스트** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-117">This command invokes the **Test** method of a resource named WindowsProcess, which is in the module named PSDesiredStateConfiguration.</span></span>

## <span data-ttu-id="99273-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="99273-118">PARAMETERS</span></span>

### <span data-ttu-id="99273-119">-메서드</span><span class="sxs-lookup"><span data-stu-id="99273-119">-Method</span></span>
<span data-ttu-id="99273-120">이 cmdlet이 호출 하는 리소스의 메서드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-120">Specifies the method of the resource that this cmdlet invokes.</span></span> <span data-ttu-id="99273-121">이 매개 변수에 허용 되는 값은 Get, Set 및 Test입니다.</span><span class="sxs-lookup"><span data-stu-id="99273-121">The acceptable values for this parameter are: Get, Set, and Test.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="99273-122">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="99273-122">-ModuleName</span></span>
<span data-ttu-id="99273-123">이 cmdlet이 지정 된 리소스를 호출 하는 모듈의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-123">Specifies the name of the module from which this cmdlet invokes the specified resource.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="99273-124">-Name</span><span class="sxs-lookup"><span data-stu-id="99273-124">-Name</span></span>
<span data-ttu-id="99273-125">시작할 DSC 리소스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-125">Specifies the name of the DSC resource to start.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="99273-126">-속성</span><span class="sxs-lookup"><span data-stu-id="99273-126">-Property</span></span>
<span data-ttu-id="99273-127">해시 테이블의 리소스 속성 이름 및 해당 값을 키와 값으로 각각 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-127">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="99273-128">**Get-DscResource** cmdlet을 사용하여 리소스 속성 및 해당 종류를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="99273-128">Use the **Get-DscResource** cmdlet to discover resource properties and their types.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="99273-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="99273-129">CommonParameters</span></span>
<span data-ttu-id="99273-130">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="99273-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="99273-131">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99273-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="99273-132">입력</span><span class="sxs-lookup"><span data-stu-id="99273-132">INPUTS</span></span>

## <span data-ttu-id="99273-133">출력</span><span class="sxs-lookup"><span data-stu-id="99273-133">OUTPUTS</span></span>

### <span data-ttu-id="99273-134">Ciminstance 개체로, System.web. 부울</span><span class="sxs-lookup"><span data-stu-id="99273-134">Microsoft.Management.Infrastructure.CimInstance, System.Boolean</span></span>

## <span data-ttu-id="99273-135">참고</span><span class="sxs-lookup"><span data-stu-id="99273-135">NOTES</span></span>

## <span data-ttu-id="99273-136">관련 링크</span><span class="sxs-lookup"><span data-stu-id="99273-136">RELATED LINKS</span></span>

[<span data-ttu-id="99273-137">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="99273-137">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="99273-138">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="99273-138">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="99273-139">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="99273-139">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="99273-140">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="99273-140">Get-DscResource</span></span>](Get-DscResource.md)

[<span data-ttu-id="99273-141">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="99273-141">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="99273-142">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="99273-142">Set-DscLocalConfigurationManager</span></span>](Set-DscLocalConfigurationManager.md)

[<span data-ttu-id="99273-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="99273-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="99273-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="99273-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
