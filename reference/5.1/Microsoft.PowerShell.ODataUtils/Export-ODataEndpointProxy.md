---
external help file: Microsoft.PowerShell.ODataUtils-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.ODataUtils
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.odatautils/export-odataendpointproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ODataEndpointProxy
ms.openlocfilehash: 846aca6974190863a073773fe5148f0c57d77dc3
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388198"
---
# <span data-ttu-id="9f730-103">Export-ODataEndpointProxy</span><span class="sxs-lookup"><span data-stu-id="9f730-103">Export-ODataEndpointProxy</span></span>

## <span data-ttu-id="9f730-104">개요</span><span class="sxs-lookup"><span data-stu-id="9f730-104">SYNOPSIS</span></span>
<span data-ttu-id="9f730-105">OData 끝점을 관리 하는 cmdlet이 포함 된 모듈을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-105">Generates a module that contains cmdlets to manage an OData endpoint.</span></span>

## <span data-ttu-id="9f730-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9f730-106">SYNTAX</span></span>

```
Export-ODataEndpointProxy [-Uri] <String> [-OutputModule] <String> [[-MetadataUri] <String>]
 [[-Credential] <PSCredential>] [[-CreateRequestMethod] <String>] [[-UpdateRequestMethod] <String>]
 [[-CmdletAdapter] <String>] [[-ResourceNameMapping] <Hashtable>] [-Force] [[-CustomData] <Hashtable>]
 [-AllowClobber] [-AllowUnsecureConnection] [[-Headers] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9f730-107">설명</span><span class="sxs-lookup"><span data-stu-id="9f730-107">DESCRIPTION</span></span>

<span data-ttu-id="9f730-108">`Export-ODataEndpointProxy`Cmdlet은 odata 끝점의 메타 데이터를 사용 하 여 odata 끝점을 관리 하는 데 사용할 수 있는 cmdlet이 포함 된 모듈을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-108">The `Export-ODataEndpointProxy` cmdlet uses the metadata of an OData endpoint to generate a module that contains cmdlets you can use to manage that OData endpoint.</span></span> <span data-ttu-id="9f730-109">모듈은 CDXML를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-109">The module is based on CDXML.</span></span> <span data-ttu-id="9f730-110">이 cmdlet은 모듈을 생성 한 후 해당 모듈을 **OutputModule** 매개 변수에 지정 된 경로 및 파일 이름에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-110">After this cmdlet generates the module, it saves that module to the path and file name specified by the **OutputModule** parameter.</span></span>

<span data-ttu-id="9f730-111">`Export-ODataEndpointProxy` CRUD (만들기, 읽기, 업데이트 및 삭제) 작업, 비 CRUD 작업 및 연결 조작을 위한 cmdlet을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-111">`Export-ODataEndpointProxy` generates cmdlets for create, read, update, and delete (CRUD) operations, non-CRUD actions, and association manipulation.</span></span>

<span data-ttu-id="9f730-112">`Export-ODataEndpointProxy` 끝점 리소스 마다 하나의 CDXML 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-112">`Export-ODataEndpointProxy` generates one CDXML file per endpoint resource.</span></span> <span data-ttu-id="9f730-113">모듈이 생성 된 후 이러한 CDXML 파일을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-113">You can edit these CDXML files after the module is generated.</span></span> <span data-ttu-id="9f730-114">예를 들어 Windows PowerShell cmdlet 명명 지침에 맞게 cmdlet의 명사 또는 verb 이름을 변경 하려는 경우 파일을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-114">For example, if you want to change the noun or verb names of the cmdlets to align with Windows PowerShell cmdlet naming guidelines, you can modify the file.</span></span>

<span data-ttu-id="9f730-115">생성 된 모듈의 모든 cmdlet은 모듈에서 관리 하는 끝점에 연결 하기 위해 **Connectionuri** 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-115">Every cmdlet in a generated module must include a **ConnectionURI** parameter in order to connect to the endpoint that the module manages.</span></span>

## <span data-ttu-id="9f730-116">예제</span><span class="sxs-lookup"><span data-stu-id="9f730-116">EXAMPLES</span></span>

### <span data-ttu-id="9f730-117">예제 1: 소매 웹 서비스 끝점을 관리 하는 모듈 생성</span><span class="sxs-lookup"><span data-stu-id="9f730-117">Example 1: Generate a module to manage a retail web service endpoint</span></span>

```powershell
PS C:\> Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -MetadataUri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc/$metadata' -AllowUnsecureConnection -OutputModule 'C:\Users\user\GeneratedScript.psm1' -ResourceNameMapping @{Products = 'Merchandise'}
```

<span data-ttu-id="9f730-118">이 명령은 소매 서비스 끝점을 관리 하는 모듈을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-118">This command generates a module to manage a retail service endpoint.</span></span> <span data-ttu-id="9f730-119">이 명령은 끝점의 URI와 끝점 메타 데이터의 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-119">The command specifies the URI of the endpoint and the URI of the endpoint metadata.</span></span> <span data-ttu-id="9f730-120">또한이 명령은 **OutputModule** 매개 변수 값으로 출력 경로 및 스크립트 모듈 이름을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-120">The command also provides an output path and script module name as the value of the **OutputModule** parameter.</span></span> <span data-ttu-id="9f730-121">**ResourceNameMapping** 매개 변수의 값에 대해 명령은 리소스 컬렉션 이름을 cmdlet 집합의 원하는 명사에 매핑하는 해시 테이블을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-121">For the value of the **ResourceNameMapping** parameter, the command provides a hashtable that maps the resource collection name to the desired noun for the cmdlet set.</span></span> <span data-ttu-id="9f730-122">이 예에서 제품은 리소스 컬렉션 이름이 고 **상품** 은 명사입니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-122">In this example, Products is the resource collection name and **Merchandise** is the noun.</span></span> <span data-ttu-id="9f730-123">HTTPS가 아닌 사이트에 대 한 연결을 허용 하려면 HTTPS가 아닌 HTTP, **AllowUnsecureConnection** 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-123">To allow connections to non-SSL sites, HTTP, as opposed to HTTPS, add the **AllowUnsecureConnection** parameter.</span></span>

## <span data-ttu-id="9f730-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9f730-124">PARAMETERS</span></span>

### <span data-ttu-id="9f730-125">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="9f730-125">-AllowClobber</span></span>

<span data-ttu-id="9f730-126">이 cmdlet이 기존 모듈을 대체 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-126">Indicates that this cmdlet replaces an existing module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 10
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-127">-AllowUnsecureConnection</span><span class="sxs-lookup"><span data-stu-id="9f730-127">-AllowUnsecureConnection</span></span>

<span data-ttu-id="9f730-128">이 모듈이 SSL로 보호 되지 않는 Uri에 연결할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-128">Indicates that this module can connect to URIs that are not SSL-secured.</span></span> <span data-ttu-id="9f730-129">이 모듈은 HTTPS 사이트 외에 HTTP 사이트를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-129">The module can manage HTTP sites in addition to HTTPS sites.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 11
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-130">-CmdletAdapter</span><span class="sxs-lookup"><span data-stu-id="9f730-130">-CmdletAdapter</span></span>

<span data-ttu-id="9f730-131">Cmdlet 어댑터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-131">Specifies the cmdlet adapter.</span></span> <span data-ttu-id="9f730-132">이 매개 변수에 허용 되는 값은 ODataAdapter 및 NetworkControllerAdapter입니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-132">The acceptable values for this parameter are: ODataAdapter and NetworkControllerAdapter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ODataAdapter, NetworkControllerAdapter, ODataV4Adapter

Required: False
Position: 6
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-133">-CreateRequestMethod</span><span class="sxs-lookup"><span data-stu-id="9f730-133">-CreateRequestMethod</span></span>

<span data-ttu-id="9f730-134">요청 메서드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-134">Specifies the request method.</span></span> <span data-ttu-id="9f730-135">이 매개 변수에 허용 되는 값은 PUT, POST 및 PATCH입니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-135">The acceptable values for this parameter are: PUT, POST, and PATCH.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 4
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-136">-Credential</span><span class="sxs-lookup"><span data-stu-id="9f730-136">-Credential</span></span>

<span data-ttu-id="9f730-137">OData 끝점에 대 한 액세스 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-137">Specifies a user account that has access to the OData endpoint.</span></span> <span data-ttu-id="9f730-138">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-138">The default value is the current user.</span></span> <span data-ttu-id="9f730-139">원격 컴퓨터에서 windows Vista 또는 이후 버전의 Windows 운영 체제를 실행 하는 경우 cmdlet은 자격 증명을 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-139">If a remote computer runs Windows Vista or a later release of the Windows operating system, the cmdlet prompts you for credentials.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-140">-CustomData</span><span class="sxs-lookup"><span data-stu-id="9f730-140">-CustomData</span></span>

<span data-ttu-id="9f730-141">사용자 지정 데이터의 해시 테이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-141">Specifies a hash table of custom data.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 9
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-142">-Force</span><span class="sxs-lookup"><span data-stu-id="9f730-142">-Force</span></span>

<span data-ttu-id="9f730-143">이 cmdlet이 기존 폴더에 있는 동일한 이름의 기존 생성 된 모듈을 덮어쓰도록 지정 `Modules` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-143">Indicates that this cmdlet overwrites an existing generated module of the same name in an existing `Modules` folder.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 8
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-144">-헤더</span><span class="sxs-lookup"><span data-stu-id="9f730-144">-Headers</span></span>

<span data-ttu-id="9f730-145">웹 요청의 헤더를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-145">Specifies the headers of the web request.</span></span> <span data-ttu-id="9f730-146">해시 테이블 또는 사전을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-146">Enter a hash table or dictionary.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 12
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-147">-MetadataUri</span><span class="sxs-lookup"><span data-stu-id="9f730-147">-MetadataUri</span></span>

<span data-ttu-id="9f730-148">끝점의 메타 데이터 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-148">Specifies the URI of the metadata of the endpoint.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-149">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="9f730-149">-OutputModule</span></span>

<span data-ttu-id="9f730-150">이 cmdlet이 생성 된 프록시 명령 모듈을 저장 하는 경로 및 모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-150">Specifies the path and module name to which this cmdlet saves the generated module of proxy commands.</span></span>

<span data-ttu-id="9f730-151">이 cmdlet은 이진 모듈, 모듈 매니페스트 및 서식 파일 (해당 하는 경우)을 지정 된 폴더에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-151">This cmdlet copies a binary module, module manifest, and formatting file, if applicable, to the specified folder.</span></span> <span data-ttu-id="9f730-152">모듈의 이름만 지정 하면에서 `Export-ODataEndpointProxy` 해당 모듈을 폴더에 저장 `$home\Documents\WindowsPowerShell\Modules` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-152">If you specify only the name of the module, `Export-ODataEndpointProxy` saves the module in the `$home\Documents\WindowsPowerShell\Modules` folder.</span></span> <span data-ttu-id="9f730-153">경로를 지정 하면 cmdlet이 해당 경로에 module 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-153">If you specify a path, the cmdlet creates the module folder in that path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-154">-ResourceNameMapping</span><span class="sxs-lookup"><span data-stu-id="9f730-154">-ResourceNameMapping</span></span>

<span data-ttu-id="9f730-155">생성 된 cmdlet을 사용자 지정할 수 있는 매핑을 포함 하는 해시 테이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-155">Specifies a hashtable that contains mappings that let you customize the generated cmdlets.</span></span> <span data-ttu-id="9f730-156">이 해시 테이블에서 리소스 컬렉션 이름은 키입니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-156">In this hashtable, the resource collection name is the key.</span></span> <span data-ttu-id="9f730-157">원하는 cmdlet 명사는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-157">The desired cmdlet noun is the value.</span></span>

<span data-ttu-id="9f730-158">예를 들어 해시 테이블에서 `@{Products = 'Merchandise'}` **Products** 는 키 역할을 하는 리소스 컬렉션 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-158">For example, in the hash table `@{Products = 'Merchandise'}`, **Products** is the resource collection name that serves as the key.</span></span> <span data-ttu-id="9f730-159">**상품** 은 결과 cmdlet 명사입니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-159">**Merchandise** is the resulting cmdlet noun.</span></span> <span data-ttu-id="9f730-160">생성 된 cmdlet 이름이 Windows PowerShell cmdlet 명명 지침에 맞지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-160">The generated cmdlet names might not align to Windows PowerShell cmdlet naming guidelines.</span></span> <span data-ttu-id="9f730-161">이 cmdlet이 모듈을 만든 후에 cmdlet 이름을 변경 하도록 리소스 CDXML 파일을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-161">You can modify the resource CDXML file to change the cmdlet names after this cmdlet creates the module.</span></span> <span data-ttu-id="9f730-162">자세한 내용은 [강력한 개발 지침](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9f730-162">For more information, see [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines).</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 7
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-163">-UpdateRequestMethod</span><span class="sxs-lookup"><span data-stu-id="9f730-163">-UpdateRequestMethod</span></span>

<span data-ttu-id="9f730-164">업데이트 요청 메서드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-164">Specifies the update request method.</span></span> <span data-ttu-id="9f730-165">이 매개 변수에 허용 되는 값은 PUT, POST 및 PATCH입니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-165">The acceptable values for this parameter are: PUT, POST, and PATCH.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 5
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-166">-Uri</span><span class="sxs-lookup"><span data-stu-id="9f730-166">-Uri</span></span>

<span data-ttu-id="9f730-167">끝점의 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-167">Specifies the URI of the endpoint.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9f730-168">-Confirm</span></span>

<span data-ttu-id="9f730-169">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-169">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9f730-170">-WhatIf</span></span>

<span data-ttu-id="9f730-171">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9f730-172">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9f730-172">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f730-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9f730-173">CommonParameters</span></span>

<span data-ttu-id="9f730-174">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9f730-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9f730-175">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9f730-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9f730-176">입력</span><span class="sxs-lookup"><span data-stu-id="9f730-176">INPUTS</span></span>

## <span data-ttu-id="9f730-177">출력</span><span class="sxs-lookup"><span data-stu-id="9f730-177">OUTPUTS</span></span>

## <span data-ttu-id="9f730-178">참고</span><span class="sxs-lookup"><span data-stu-id="9f730-178">NOTES</span></span>

## <span data-ttu-id="9f730-179">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9f730-179">RELATED LINKS</span></span>

<span data-ttu-id="9f730-180">[OData 라이브러리](/previous-versions/dotnet/wcf-data-services/hh525392(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="9f730-180">[OData Library](/previous-versions/dotnet/wcf-data-services/hh525392(v=vs.103))</span></span>

[<span data-ttu-id="9f730-181">OData 프로토콜 이란?</span><span class="sxs-lookup"><span data-stu-id="9f730-181">What is the OData Protocol?</span></span>](https://www.odata.org/)

[<span data-ttu-id="9f730-182">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="9f730-182">Invoke-RestMethod</span></span>](../Microsoft.PowerShell.Utility/Invoke-RestMethod.md)
