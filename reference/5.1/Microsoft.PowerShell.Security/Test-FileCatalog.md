---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 8f5e11fca51bf92386c19a77fa9a66503b2d47a5
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343252"
---
# Test-FileCatalog

## 개요
`Test-FileCatalog` 카탈로그 파일 (.cat)에 포함 된 해시가 실제 파일의 해시와 일치 하는지 유효성을 검사 하기 위해 유효성을 검사 합니다.

이 cmdlet은 Windows 에서만 지원 됩니다.

## SYNTAX

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Test-FileCatalog` 카탈로그 파일 (.cat)의 파일 해시를 디스크에 있는 실제 파일의 해시와 비교 하 여 파일 신뢰성의 유효성을 검사 합니다. 불일치를 발견 하면 ValidationFailed로 상태를 반환 합니다. 사용자는 -Detailed 매개 변수를 사용하여 이 모든 정보를 검색할 수 있습니다. 또한이 `Get-AuthenticodeSignature` cmdlet은 카탈로그 파일에서 cmdlet을 호출 하는 것과 동일한 Signature 속성에 카탈로그의 서명 상태를 표시 합니다. 사용자는 -FilesToSkip 매개 변수를 사용하여 유효성 검사 시 파일을 건너뛸 수도 있습니다.

이 cmdlet은 Windows 에서만 지원 됩니다.

## 예제

### 예제 1: 파일 카탈로그 만들기 및 유효성 검사

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### 예제 2: 자세한 출력을 사용 하 여 파일 카탈로그 유효성 검사

```powershell
Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Status        : Valid
HashAlgorithm : SHA256
CatalogItems  : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
PathItems     : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
Signature     : System.Management.Automation.Signature
```

## PARAMETERS

### -CatalogFilePath

유효성 검사에 사용할 해시가 포함 된 카탈로그 파일 (.cat)의 경로입니다.

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

### -Detailed

추가 정보를 반환 합니다 `CatalogInformation` .이 개체에는 테스트 한 파일, 예상/실제 해시 및 서명 된 카탈로그 파일의 Authenticode 서명이 포함 되어 있습니다.

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

### -FilesToSkip

유효성 검사의 일부로 테스트 하면 안 되는 경로 배열입니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

카탈로그 파일에 대해 유효성을 검사 해야 하는 폴더 또는 파일의 배열입니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

### System.io.directoryinfo [], System.string []

파이프라인은 `DirectoryInfo` 유효성을 검사 해야 하는 파일의 경로를 나타내는 문자열 또는 개체의 배열을 허용 합니다.

## 출력

### CatalogValidationStatus.

또는의 값을 포함 하는 기본 반환 형식입니다 `Valid` `ValidationFailed` .

### CatalogInformation.

을 사용 하 여 `-Detailed` 유효성 검사를 통과 하거나 포함 하지 않을 수 있는 특정 파일을 분석 하는 데 사용할 수 있는 보다 자세한 개체를 사용 하는 경우, 필요한 해시 및 검색 된 알고리즘과 카탈로그에서 사용 되는 알고리즘입니다.

## 참고

## 관련 링크

[New-FileCatalog](New-FileCatalog.md)

[PowerShellGet](/powershell/module/PowerShellGet)
