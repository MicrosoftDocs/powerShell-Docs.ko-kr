---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 916b0ca30240002949b947b857b257214ea9ca1a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216746"
---
# Export-Clixml

## 개요
개체의 XML 기반 표시를 만들고 이 표시를 파일에 저장합니다.

## SYNTAX

### ByPath (기본값)

```
Export-Clixml [-Path] <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Clixml -LiteralPath <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Export-Clixml`Cmdlet은 개체의 CLI (공용 언어 인프라) XML 기반 표현을 만들고이를 파일에 저장 합니다. 그런 다음 cmdlet을 사용 `Import-Clixml` 하 여 해당 파일의 내용을 기반으로 저장 된 개체를 다시 만들 수 있습니다.
CLI에 대 한 자세한 내용은 [언어 독립성](/dotnet/standard/language-independence)을 참조 하세요.

이 cmdlet은 `ConvertTo-Xml` `Export-Clixml` 결과 XML을 파일에 저장 한다는 점을 제외 하 고와 비슷합니다. `ConvertTo-XML` 는 XML을 반환 하므로 PowerShell에서 계속 처리할 수 있습니다.

Windows 컴퓨터에서의 중요 한 용도는 `Export-Clixml` 자격 증명과 보안 문자열을 XML로 안전 하 게 내보내는 것입니다. 예제를 보려면 예제 3을 참조 하세요.

## 예제

### 예제 1: 문자열을 XML 파일로 내보내기

이 예제에서는 현재 디렉터리에를 저장 하는 XML 파일을 만듭니다. **이는 테스트** 의 문자열 표현입니다.

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

이에 해당 하는 **테스트** 문자열은 파이프라인으로 전송 됩니다. `Export-Clixml`**Path** 매개 변수를 사용 하 여 현재 디렉터리에 라는 XML 파일을 만듭니다 `sample.xml` .

### 예제 2: XML 파일로 개체 내보내기

이 예제에서는 개체를 XML 파일로 내보낸 다음 파일에서 XML을 가져와 개체를 만드는 방법을 보여 줍니다.

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

`Get-Acl`Cmdlet은 파일의 보안 설명자를 가져옵니다 `Test.txt` . 보안 설명자를 전달할 파이프라인에서 개체를 보냅니다 `Export-Clixml` . 개체의 XML 기반 표현은 이라는 파일에 저장 됩니다 `FileACL.xml` .

`Import-Clixml`Cmdlet은 파일의 XML에서 개체를 만듭니다 `FileACL.xml` . 그런 다음 개체를 `$fileacl` 변수에 저장 합니다.

### 예제 3: Windows에서 내보낸 자격 증명 개체 암호화

이 예에서는 cmdlet을 실행 하 여 변수에 저장 한 자격 증명이 지정 된 경우 `$Credential` `Get-Credential` cmdlet을 실행 하 여 `Export-Clixml` 자격 증명을 디스크에 저장할 수 있습니다.

> [!IMPORTANT]
> `Export-Clixml` Windows에서 암호화 된 자격 증명만 내보냅니다. MacOS 및 Linux와 같은 Windows 이외의 운영 체제에서는 자격 증명을 유니코드 문자 배열로 저장 된 일반 텍스트로 내보냅니다. 이는 일부 난독 처리를 제공 하지만 암호화를 제공 하지 않습니다.

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

`Export-Clixml`Cmdlet은 Windows [데이터 보호 API](/previous-versions/windows/apps/hh464970(v=win.10))를 사용 하 여 자격 증명 개체를 암호화 합니다. 암호화를 사용 하면 해당 컴퓨터의 사용자 계정만 자격 증명 개체의 콘텐츠를 해독할 수 있습니다.
내보낸 `CLIXML` 파일은 다른 컴퓨터 또는 다른 사용자가 사용할 수 없습니다.

이 예에서 자격 증명이 저장 된 파일은로 표시 됩니다 `TestScript.ps1.credential` . **Testscript** 를 자격 증명을 로드 하는 스크립트의 이름으로 바꿉니다.

파이프라인의 자격 증명 개체를로 전송 하 `Export-Clixml` 고, `$Credxmlpath` 첫 번째 명령에서 지정한 경로에 저장 합니다.

스크립트에 자격 증명을 자동으로 가져오려면 최종 두 개의 명령을 실행 합니다. `Import-Clixml`을 실행 하 여 보안 자격 증명 개체를 스크립트로 가져옵니다. 이 가져오기는 스크립트에서 일반 텍스트 암호를 노출 하는 위험을 제거 합니다.

### 예제 4: Linux 또는 macOS에서 자격 증명 개체 내보내기

이 예제에서는 cmdlet을 사용 하 여 변수에 **PSCredential** 을 만듭니다 `$Credential` `Get-Credential` . 그런 다음 `Export-Clixml` 를 사용 하 여 디스크에 자격 증명을 저장 합니다.

> [!IMPORTANT]
> `Export-Clixml` Windows에서 암호화 된 자격 증명만 내보냅니다. MacOS 및 Linux와 같은 Windows 이외의 운영 체제에서는 자격 증명을 유니코드 문자 배열로 저장 된 일반 텍스트로 내보냅니다. 이는 일부 난독 처리를 제공 하지만 암호화를 제공 하지 않습니다.

```powershell
PS> $Credential = Get-Credential

PowerShell credential request
Enter your credentials.
User: User1
Password for user User1: ********

PS> $Credential | Export-Clixml ./cred2.xml
PS> Get-Content ./cred2.xml

...
    <Props>
      <S N="UserName">User1</S>
      <SS N="Password">700061007300730077006f0072006400</SS>
    </Props>
...

PS> 'password' | Format-Hex -Encoding unicode

                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
0000000000000000 70 00 61 00 73 00 73 00 77 00 6F 00 72 00 64 00 p a s s w o r d
```

`Get-Content`이 예제의 출력은 XML 파일의 자격 증명 정보에 초점을 맞추기 위해 잘립니다. 암호의 일반 텍스트 값은에 의해 검증 된 대로 XML 파일에 유니코드 문자 배열로 저장 됩니다 `Format-Hex` . 따라서 값은 인코딩되어 암호화 되지 않습니다.

## PARAMETERS

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

### -깊이

XML 표시에 포함되는 포함 개체 수준을 지정합니다. 기본값은 `2`입니다.

파일의 개체 형식에 대 한 기본값을 재정의할 수 있습니다 `Types.ps1xml` . 자세한 내용은 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)을 참조 하세요.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

대상 파일의 인코딩 유형을 지정합니다. 기본값은 `utf8NoBOM`입니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.
- `bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.
- `unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `utf7`: UTF-7 형식으로 인코딩합니다.
- `utf8`: UTF-8 형식으로 인코딩합니다.
- `utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.
- `utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.
- `utf32`: U t f-32 형식으로 인코딩합니다.

PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ). 자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

필요한 경우 Cmdlet을 사용하여 출력 파일의 읽기 전용 특성을 제거합니다. 명령이 완료되면 cmdlet이 읽기 전용 특성을 다시 설정하려고 합니다.

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

### -InputObject

변환할 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요. 개체를로 파이프 할 수도 있습니다 `Export-Clixml` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

개체의 XML 표시를 저장할 파일 경로를 지정합니다. **Path** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Cmdlet이 기존 파일의 내용을 덮어쓰지 않음을 나타냅니다. 기본적으로 지정 된 경로에 파일이 있으면는 `Export-Clixml` 경고 없이 파일을 덮어씁니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

개체의 XML 표시를 저장할 파일 경로를 지정합니다.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. Cmdlet이 실행 되지 않습니다.

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

### System.web. PSObject

모든 개체를로 파이프라인 할 수 있습니다 `Export-Clixml` .

## 출력

### System.object

`Export-Clixml` XML이 포함 된 파일을 만듭니다.

## 참고

## 관련 링크

[ConvertTo-Html](ConvertTo-Html.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

[Export-Csv](Export-Csv.md)

[Import-Clixml](Import-Clixml.md)

[Join-Path](../Microsoft.PowerShell.Management/Join-Path.md)

[디스크에 자격 증명을 안전 하 게 저장](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[PowerShell을 사용 하 여 레거시 시스템에 자격 증명 전달](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[Windows.Security.Cryptography.DataProtection](/uwp/api/windows.security.cryptography.dataprotection)
