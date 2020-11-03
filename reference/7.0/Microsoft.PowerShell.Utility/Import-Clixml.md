---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: 67dd525da0f1ee7b9f49e585588640030ede8c2b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211433"
---
# Import-Clixml

## 개요
EXPORT-CLIXML 파일을 가져오고 PowerShell에서 해당 개체를 만듭니다.

## SYNTAX

### ByPath (기본값)

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### ByLiteralPath

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## 설명

`Import-Clixml`Cmdlet은 Microsoft .NET Framework 개체를 나타내는 데이터가 포함 된 CLI (공용 언어 인프라) XML 파일을 가져오고 PowerShell 개체를 만듭니다. CLI에 대 한 자세한 내용은 [언어 독립성](/dotnet/standard/language-independence)을 참조 하세요.

Windows 컴퓨터에서의 중요 한 용도는를 `Import-Clixml` 사용 하 여 보안 XML로 내보낸 자격 증명 및 보안 문자열을 가져오는 것입니다 `Export-Clixml` . 예제는 예제 2를 참조 하세요.

`Import-Clixml` 는 BOM (바이트 순서 표시)을 사용 하 여 파일의 인코딩 형식을 검색 합니다. 파일에 BOM이 없으면 인코딩이 UTF8 이라고 가정 합니다.

## 예제

### 예제 1: serialize 된 파일 가져오기 및 개체 다시 만들기

이 예에서는 cmdlet을 사용 하 `Export-Clixml` 여에서 반환 된 프로세스 정보의 직렬화 된 복사본을 저장 `Get-Process` 합니다. `Import-Clixml` serialize 된 파일의 내용을 검색 하 고 변수에 저장 된 개체를 다시 만듭니다 `$Processes` .

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### 예제 2: 보안 자격 증명 개체 가져오기

이 예에서는 cmdlet을 실행 하 여 변수에 저장 한 자격 증명이 지정 된 경우 `$Credential` `Get-Credential` cmdlet을 실행 하 여 `Export-Clixml` 자격 증명을 디스크에 저장할 수 있습니다.

> [!IMPORTANT]
> `Export-Clixml` Windows에서 암호화 된 자격 증명만 내보냅니다. MacOS 및 Linux와 같은 Windows 이외의 운영 체제에서는 자격 증명을 일반 텍스트로 내보냅니다.

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

`Export-Clixml`Cmdlet은 Windows [데이터 보호 API](/previous-versions/windows/apps/hh464970(v=win.10))를 사용 하 여 자격 증명 개체를 암호화 합니다.
암호화를 사용 하면 사용자 계정만 자격 증명 개체의 콘텐츠를 해독할 수 있습니다. 내보낸 `CLIXML` 파일은 다른 컴퓨터 또는 다른 사용자가 사용할 수 없습니다.

이 예에서 자격 증명이 저장 된 파일은로 표시 됩니다 `TestScript.ps1.credential` . **Testscript** 를 자격 증명을 로드 하는 스크립트의 이름으로 바꿉니다.

파이프라인의 자격 증명 개체를로 전송 하 `Export-Clixml` 고, `$Credxmlpath` 첫 번째 명령에서 지정한 경로에 저장 합니다.

스크립트에 자격 증명을 자동으로 가져오려면 최종 두 개의 명령을 실행 합니다. `Import-Clixml`을 실행 하 여 보안 자격 증명 개체를 스크립트로 가져옵니다. 이 가져오기는 스크립트에서 일반 텍스트 암호를 노출 하는 위험을 제거 합니다.

## PARAMETERS

### -첫 번째

지정된 수의 개체만 가져옵니다. 가져올 개체 수를 입력합니다.

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeTotalCount

선택한 개체 다음에 오는 데이터 집합의 총 개체 수를 보고 합니다. Cmdlet이 총 개수를 확인할 수 없는 경우에는 **알 수 없는 총 개수** 를 표시 합니다. 정수에는 총 개수 값의 안정성을 나타내는 **정확도** 속성이 있습니다. **정확도** 범위 값은에서 `0.0` 로 지정 됩니다 `1.0` . 여기서은 `0.0` cmdlet이 개체를 계산할 수 없음을 의미 하 고,는 `1.0` 개수가 정확 함을 의미 하며,와 사이의 값은 점점 더 `0.0` `1.0` 안정적인 추정치를 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

XML 파일의 경로를 지정 합니다. **Path** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

XML 파일의 경로를 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Skip

지정된 개체 수를 무시하고 남은 개체를 가져옵니다. 건너뛸 개체 수를 입력합니다.

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

에 대 한 경로를 포함 하는 문자열을 파이프라인으로 만들 수 있습니다 `Import-Clixml` .

## 출력

### PSObject

`Import-Clixml` 저장 된 XML 파일에서 deserialize 된 개체를 반환 합니다.

## 참고

매개 변수에 여러 값을 지정할 때는 쉼표를 사용하여 값을 구분하세요. 예들 들어 `<parameter-name> <value1>, <value2>`입니다.

## 관련 링크

[Export-Clixml](Export-Clixml.md)

[XML serialization 소개](/dotnet/standard/serialization/introducing-xml-serialization)

[Join-Path](../Microsoft.PowerShell.Management/Join-Path.md)

[디스크에 자격 증명을 안전 하 게 저장](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[PowerShell을 사용 하 여 레거시 시스템에 자격 증명 전달](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)
