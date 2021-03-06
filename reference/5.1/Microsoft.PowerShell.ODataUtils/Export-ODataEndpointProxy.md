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
# Export-ODataEndpointProxy

## 개요
OData 끝점을 관리 하는 cmdlet이 포함 된 모듈을 생성 합니다.

## SYNTAX

```
Export-ODataEndpointProxy [-Uri] <String> [-OutputModule] <String> [[-MetadataUri] <String>]
 [[-Credential] <PSCredential>] [[-CreateRequestMethod] <String>] [[-UpdateRequestMethod] <String>]
 [[-CmdletAdapter] <String>] [[-ResourceNameMapping] <Hashtable>] [-Force] [[-CustomData] <Hashtable>]
 [-AllowClobber] [-AllowUnsecureConnection] [[-Headers] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Export-ODataEndpointProxy`Cmdlet은 odata 끝점의 메타 데이터를 사용 하 여 odata 끝점을 관리 하는 데 사용할 수 있는 cmdlet이 포함 된 모듈을 생성 합니다. 모듈은 CDXML를 기반으로 합니다. 이 cmdlet은 모듈을 생성 한 후 해당 모듈을 **OutputModule** 매개 변수에 지정 된 경로 및 파일 이름에 저장 합니다.

`Export-ODataEndpointProxy` CRUD (만들기, 읽기, 업데이트 및 삭제) 작업, 비 CRUD 작업 및 연결 조작을 위한 cmdlet을 생성 합니다.

`Export-ODataEndpointProxy` 끝점 리소스 마다 하나의 CDXML 파일을 생성 합니다. 모듈이 생성 된 후 이러한 CDXML 파일을 편집할 수 있습니다. 예를 들어 Windows PowerShell cmdlet 명명 지침에 맞게 cmdlet의 명사 또는 verb 이름을 변경 하려는 경우 파일을 수정할 수 있습니다.

생성 된 모듈의 모든 cmdlet은 모듈에서 관리 하는 끝점에 연결 하기 위해 **Connectionuri** 매개 변수를 포함 해야 합니다.

## 예제

### 예제 1: 소매 웹 서비스 끝점을 관리 하는 모듈 생성

```powershell
PS C:\> Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -MetadataUri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc/$metadata' -AllowUnsecureConnection -OutputModule 'C:\Users\user\GeneratedScript.psm1' -ResourceNameMapping @{Products = 'Merchandise'}
```

이 명령은 소매 서비스 끝점을 관리 하는 모듈을 생성 합니다. 이 명령은 끝점의 URI와 끝점 메타 데이터의 URI를 지정 합니다. 또한이 명령은 **OutputModule** 매개 변수 값으로 출력 경로 및 스크립트 모듈 이름을 제공 합니다. **ResourceNameMapping** 매개 변수의 값에 대해 명령은 리소스 컬렉션 이름을 cmdlet 집합의 원하는 명사에 매핑하는 해시 테이블을 제공 합니다. 이 예에서 제품은 리소스 컬렉션 이름이 고 **상품** 은 명사입니다. HTTPS가 아닌 사이트에 대 한 연결을 허용 하려면 HTTPS가 아닌 HTTP, **AllowUnsecureConnection** 매개 변수를 추가 합니다.

## PARAMETERS

### -AllowClobber

이 cmdlet이 기존 모듈을 대체 함을 나타냅니다.

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

### -AllowUnsecureConnection

이 모듈이 SSL로 보호 되지 않는 Uri에 연결할 수 있음을 나타냅니다. 이 모듈은 HTTPS 사이트 외에 HTTP 사이트를 관리할 수 있습니다.

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

### -CmdletAdapter

Cmdlet 어댑터를 지정 합니다. 이 매개 변수에 허용 되는 값은 ODataAdapter 및 NetworkControllerAdapter입니다.

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

### -CreateRequestMethod

요청 메서드를 지정 합니다. 이 매개 변수에 허용 되는 값은 PUT, POST 및 PATCH입니다.

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

### -Credential

OData 끝점에 대 한 액세스 권한이 있는 사용자 계정을 지정 합니다. 기본값은 현재 사용자입니다. 원격 컴퓨터에서 windows Vista 또는 이후 버전의 Windows 운영 체제를 실행 하는 경우 cmdlet은 자격 증명을 묻는 메시지를 표시 합니다.

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

### -CustomData

사용자 지정 데이터의 해시 테이블을 지정 합니다.

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

### -Force

이 cmdlet이 기존 폴더에 있는 동일한 이름의 기존 생성 된 모듈을 덮어쓰도록 지정 `Modules` 합니다.

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

### -헤더

웹 요청의 헤더를 지정합니다. 해시 테이블 또는 사전을 입력합니다.

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

### -MetadataUri

끝점의 메타 데이터 URI를 지정 합니다.

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

### -OutputModule

이 cmdlet이 생성 된 프록시 명령 모듈을 저장 하는 경로 및 모듈 이름을 지정 합니다.

이 cmdlet은 이진 모듈, 모듈 매니페스트 및 서식 파일 (해당 하는 경우)을 지정 된 폴더에 복사 합니다. 모듈의 이름만 지정 하면에서 `Export-ODataEndpointProxy` 해당 모듈을 폴더에 저장 `$home\Documents\WindowsPowerShell\Modules` 합니다. 경로를 지정 하면 cmdlet이 해당 경로에 module 폴더를 만듭니다.

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

### -ResourceNameMapping

생성 된 cmdlet을 사용자 지정할 수 있는 매핑을 포함 하는 해시 테이블을 지정 합니다. 이 해시 테이블에서 리소스 컬렉션 이름은 키입니다. 원하는 cmdlet 명사는 값입니다.

예를 들어 해시 테이블에서 `@{Products = 'Merchandise'}` **Products** 는 키 역할을 하는 리소스 컬렉션 이름입니다. **상품** 은 결과 cmdlet 명사입니다. 생성 된 cmdlet 이름이 Windows PowerShell cmdlet 명명 지침에 맞지 않을 수 있습니다. 이 cmdlet이 모듈을 만든 후에 cmdlet 이름을 변경 하도록 리소스 CDXML 파일을 수정할 수 있습니다. 자세한 내용은 [강력한 개발 지침](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines)을 참조 하세요.

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

### -UpdateRequestMethod

업데이트 요청 메서드를 지정 합니다. 이 매개 변수에 허용 되는 값은 PUT, POST 및 PATCH입니다.

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

### -Uri

끝점의 URI를 지정 합니다.

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

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

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

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

## 참고

## 관련 링크

[OData 라이브러리](/previous-versions/dotnet/wcf-data-services/hh525392(v=vs.103))

[OData 프로토콜 이란?](https://www.odata.org/)

[Invoke-RestMethod](../Microsoft.PowerShell.Utility/Invoke-RestMethod.md)
