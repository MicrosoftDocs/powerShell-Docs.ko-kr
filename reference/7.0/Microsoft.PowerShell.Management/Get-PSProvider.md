---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: cb3b851b9634c052cf9d680fcb7f7e1215f9870d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210193"
---
# <span data-ttu-id="69cbf-103">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="69cbf-103">Get-PSProvider</span></span>

## <span data-ttu-id="69cbf-104">개요</span><span class="sxs-lookup"><span data-stu-id="69cbf-104">SYNOPSIS</span></span>
<span data-ttu-id="69cbf-105">지정 된 PowerShell 공급자에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-105">Gets information about the specified PowerShell provider.</span></span>

## <span data-ttu-id="69cbf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="69cbf-106">SYNTAX</span></span>

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="69cbf-107">설명</span><span class="sxs-lookup"><span data-stu-id="69cbf-107">DESCRIPTION</span></span>

<span data-ttu-id="69cbf-108">`Get-PSProvider`Cmdlet은 현재 세션의 PowerShell 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-108">The `Get-PSProvider` cmdlet gets the PowerShell providers in the current session.</span></span>
<span data-ttu-id="69cbf-109">특정 드라이브를 가져오거나 세션의 모든 드라이브를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-109">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="69cbf-110">PowerShell 공급자를 사용 하면 파일 시스템 드라이브 처럼 다양 한 데이터 저장소에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-110">PowerShell providers let you access a variety of data stores as though they were file system drives.</span></span>
<span data-ttu-id="69cbf-111">PowerShell 공급자에 대 한 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69cbf-111">For information about PowerShell providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="69cbf-112">예제</span><span class="sxs-lookup"><span data-stu-id="69cbf-112">EXAMPLES</span></span>

### <span data-ttu-id="69cbf-113">예제 1: 사용 가능한 모든 공급자 목록 표시</span><span class="sxs-lookup"><span data-stu-id="69cbf-113">Example 1: Display a list of all available providers</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="69cbf-114">이 명령은 사용 가능한 모든 PowerShell 공급자 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-114">This command displays a list of all available PowerShell providers.</span></span>

### <span data-ttu-id="69cbf-115">예 2: 지정 된 문자로 시작 하는 모든 PowerShell 공급자 목록 표시</span><span class="sxs-lookup"><span data-stu-id="69cbf-115">Example 2: Display a list of all PowerShell providers that begin with specified letters</span></span>

```powershell
Get-PSProvider f*, r* | Format-List
```

<span data-ttu-id="69cbf-116">이 명령은 이름이 f 또는 r 문자로 시작 하는 모든 PowerShell 공급자 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-116">This command displays a list of all PowerShell providers with names that begin with the letter f or r.</span></span>

### <span data-ttu-id="69cbf-117">예제 3: 세션에 공급자를 추가한 스냅인 또는 모듈 찾기</span><span class="sxs-lookup"><span data-stu-id="69cbf-117">Example 3: Find snap-ins or module that added providers to your session</span></span>

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

<span data-ttu-id="69cbf-118">이러한 명령은 세션에 공급자를 추가한 PowerShell 스냅인 또는 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-118">These commands find the PowerShell snap-ins or modules that added providers to your session.</span></span>
<span data-ttu-id="69cbf-119">공급자를 비롯 한 모든 PowerShell 요소는 스냅인 이나 모듈에서 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-119">All PowerShell elements, including providers, originate in a snap-in or in a module.</span></span>

<span data-ttu-id="69cbf-120">이러한 명령은를 반환 하는 **ProviderInfo** 개체의 Add-pssnapin 및 Module 속성을 사용 `Get-PSProvider` 합니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-120">These commands use the PSSnapin and Module properties of the **ProviderInfo** object that `Get-PSProvider` returns.</span></span>
<span data-ttu-id="69cbf-121">이러한 속성 값에는 공급자를 추가하는 스냅인이나 모듈의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-121">The values of these properties contain the name of the snap-in or module that adds the provider.</span></span>

<span data-ttu-id="69cbf-122">첫 번째 명령은 세션의 모든 공급자를 가져와서 해당 Name, Module 및 PSSnapin 속성 값과 함께 테이블 형식으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-122">The first command gets all of the providers in the session and formats them in a table with the values of their Name, Module, and PSSnapin properties.</span></span>

<span data-ttu-id="69cbf-123">두 번째 명령은 cmdlet을 사용 하 여 `Where-Object` **Microsoft. PowerShell. 보안** 스냅인에서 제공 하는 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-123">The second command uses the `Where-Object` cmdlet to get the providers that come from the **Microsoft.PowerShell.Security** snap-in.</span></span>

### <span data-ttu-id="69cbf-124">예 4: 파일 시스템 공급자의 Home 속성 경로 확인</span><span class="sxs-lookup"><span data-stu-id="69cbf-124">Example 4: Resolve the path of the Home property of the file system provider</span></span>

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

<span data-ttu-id="69cbf-125">이 예에서는 물결표 기호 (~)가 FileSystem 공급자의 **Home** 속성 값을 나타내는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-125">This example shows that the tilde symbol (~) represents the value of the **Home** property of the FileSystem provider.</span></span>
<span data-ttu-id="69cbf-126">**Home** 속성 값은 선택 사항 이지만 **FileSystem** 공급자의 경우 또는로 정의 됩니다 `$env:homedrive\$env:homepath` `$home` .</span><span class="sxs-lookup"><span data-stu-id="69cbf-126">The **Home** property value is optional, but for the **FileSystem** provider, it is defined as `$env:homedrive\$env:homepath` or `$home`.</span></span>

## <span data-ttu-id="69cbf-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="69cbf-127">PARAMETERS</span></span>

### <span data-ttu-id="69cbf-128">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="69cbf-128">-PSProvider</span></span>

<span data-ttu-id="69cbf-129">이 cmdlet이 정보를 가져오는 PowerShell 공급자의 이름 또는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-129">Specifies the name or names of the PowerShell providers about which this cmdlet gets information.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="69cbf-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="69cbf-130">CommonParameters</span></span>

<span data-ttu-id="69cbf-131">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="69cbf-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="69cbf-132">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69cbf-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="69cbf-133">입력</span><span class="sxs-lookup"><span data-stu-id="69cbf-133">INPUTS</span></span>

### <span data-ttu-id="69cbf-134">String[]</span><span class="sxs-lookup"><span data-stu-id="69cbf-134">String[]</span></span>

<span data-ttu-id="69cbf-135">하나 이상의 공급자 이름 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-135">You can pipe one or more provider name strings to this cmdlet.</span></span>

## <span data-ttu-id="69cbf-136">출력</span><span class="sxs-lookup"><span data-stu-id="69cbf-136">OUTPUTS</span></span>

### <span data-ttu-id="69cbf-137">ProviderInfo.</span><span class="sxs-lookup"><span data-stu-id="69cbf-137">System.Management.Automation.ProviderInfo</span></span>

<span data-ttu-id="69cbf-138">이 cmdlet은 세션의 PowerShell 공급자를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="69cbf-138">This cmdlet returns objects that represent the PowerShell providers in the session.</span></span>

## <span data-ttu-id="69cbf-139">참고</span><span class="sxs-lookup"><span data-stu-id="69cbf-139">NOTES</span></span>

## <span data-ttu-id="69cbf-140">관련 링크</span><span class="sxs-lookup"><span data-stu-id="69cbf-140">RELATED LINKS</span></span>
