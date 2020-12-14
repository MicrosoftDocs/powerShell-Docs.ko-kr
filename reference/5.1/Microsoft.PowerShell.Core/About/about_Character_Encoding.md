---
description: PowerShell에서 문자열 데이터의 입력 및 출력에 문자 인코딩을 사용 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 10/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Character_Encoding
ms.openlocfilehash: 48a33903bd44db68a3c581183f83ec23ea97161a
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96349809"
---
# <a name="about_character_encoding"></a>about_Character_Encoding

## <a name="short-description"></a>간단한 설명
PowerShell에서 문자열 데이터의 입력 및 출력에 문자 인코딩을 사용 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

유니코드는 전 세계 문자 인코딩 표준입니다. 시스템에서는 문자 및 문자열 조작을 위해 유니코드를 독점적으로 사용 합니다. 유니코드의 모든 측면에 대 한 자세한 내용은 [Unicode Standard](https://www.unicode.org/standard/standard.html)를 참조 하세요.

Windows는 유니코드 및 기존 문자 집합을 지원 합니다. Windows 코드 페이지와 같은 기존 문자 집합은 8 비트 값 또는 8 비트 값의 조합을 사용 하 여 특정 언어 또는 지리적 지역 설정에서 사용 되는 문자를 나타냅니다.

PowerShell은 기본적으로 유니코드 문자 집합을 사용 합니다. 그러나 여러 cmdlet에는 다른 문자 집합에 대 한 인코딩을 지정할 수 있는 **인코딩** 매개 변수가 있습니다. 이 매개 변수를 사용 하 여 다른 시스템 및 응용 프로그램과의 상호 운용성을 위해 필요한 특정 문자 인코딩을 선택할 수 있습니다.

다음 cmdlet에는 **Encoding** 매개 변수가 있습니다.

- Microsoft.PowerShell.Management
  - Add-Content
  - Get-Content
  - Set-Content
- Microsoft.PowerShell.Utility
  - Export-Clixml
  - Export-Csv
  - Export-PSSession
  - Format-Hex
  - Import-Csv
  - Out-File
  - Select-String
  - Send-MailMessage

## <a name="the-byte-order-mark"></a>바이트 순서 표시입니다.

BOM (바이트 순서 표시)은 파일 또는 텍스트 스트림의 처음 몇 바이트에 있는 _유니코드 서명_ 으로, 데이터에 사용 되는 유니코드 인코딩을 표시 합니다. 자세한 내용은 [바이트 순서 표시](/globalization/encoding/byte-order-mark) 설명서를 참조 하세요.

Windows PowerShell에서를 제외한 모든 유니코드 인코딩은 `UTF7` 항상 BOM을 만듭니다. PowerShell Core는 기본적으로 `utf8NoBOM` 모든 텍스트 출력에 대해로 설정 됩니다.

최상의 전반적인 호환성을 위해 u t f-8 파일에 Bom을 사용 하지 마십시오. Windows 플랫폼에도 사용 되는 unix 플랫폼 및 Unix heritage 유틸리티는 Bom을 지원 하지 않습니다.

마찬가지로 `UTF7` encoding을 피해 야 합니다. U t f-7은 표준 유니코드 인코딩이 아니므로 모든 버전의 PowerShell에서 BOM 없이 작성 됩니다.

Unix와 같은 플랫폼에서 PowerShell 스크립트를 만들거나 Visual Studio Code와 같이 Windows에서 플랫폼 간 편집기를 사용 하 여 파일을로 인코딩합니다 `UTF8NoBOM` . 이러한 파일은 PowerShell Core에서 잘 작동 하지만 파일에 비 Ascii 문자가 포함 된 경우 Windows PowerShell에서 중단 될 수 있습니다.

스크립트에서 Ascii가 아닌 문자를 사용 해야 하는 경우 BOM을 사용 하 여 u t f-8로 저장 합니다. BOM이 없으면 Windows PowerShell에서 스크립트를 레거시 "ANSI" 코드 페이지에서 misinterprets 합니다. 반대로 UTF-8 BOM이 있는 파일은 Unix와 비슷한 플랫폼에서 문제가 될 수 있습니다. `cat`, `sed` , 및와 같은 `awk` 일부 편집기는 BOM을 처리 하 `gedit` 는 방법을 알 수 없습니다.

## <a name="character-encoding-in-windows-powershell"></a>Windows PowerShell의 문자 인코딩

PowerShell 5.1에서 **Encoding** 매개 변수는 다음 값을 지원 합니다.

- `Ascii` Ascii (7 비트) 문자 집합을 사용 합니다.
- `BigEndianUnicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.
- `BigEndianUTF32` 는 빅 endian 바이트 순서를 사용 하 여 u t f-32을 사용 합니다.
- `Byte` 문자 집합을 바이트 시퀀스로 인코딩합니다.
- `Default` 시스템의 활성 코드 페이지에 해당 하는 인코딩을 사용 합니다 (일반적으로 ANSI).
- `Oem` 시스템의 현재 OEM 코드 페이지에 해당 하는 인코딩을 사용 합니다.
- `String`: `Unicode`과 동일합니다.
- `Unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.
- `Unknown`: `Unicode`과 동일합니다.
- `UTF32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.
- `UTF7` 는 u t f-7을 사용 합니다.
- `UTF8` 는 u t f-8 (BOM 포함)을 사용 합니다.

일반적으로 Windows PowerShell은 기본적으로 유니코드 [UTF-utf-16le](https://wikipedia.org/wiki/UTF-16) 인코딩을 사용 합니다. 그러나 Windows PowerShell에서 cmdlet에 사용 되는 기본 인코딩은 일치 하지 않습니다.

> [!NOTE]
> 를 제외 하 고 모든 유니코드 인코딩을 사용 하 여 `UTF7` 은 항상 BOM을 만듭니다.

파일에 출력을 기록 하는 cmdlet의 경우:

- `Out-File` 및와는 `>` `>>` 달리 utf-16le을 만듭니다 `Set-Content` `Add-Content` .

- `New-ModuleManifest``Export-CliXml`또한 utf-16le 파일을 만듭니다.

- 대상 파일이 비어 있거나 존재 하지 않는 경우 `Set-Content` 및 `Add-Content` `Default` 인코딩을 사용 합니다. `Default` 활성 시스템 로캘의 ANSI 레거시 코드 페이지에서 지정 하는 인코딩입니다.

- `Export-Csv``Ascii` **추가** 매개 변수를 사용할 때 파일을 만들지만 다른 인코딩을 사용 합니다 (아래 참조).

- `Export-PSSession` 기본적으로 BOM을 사용 하 여 UTF-8 파일을 만듭니다.

- `New-Item -Type File -Value` BOM less UTF-8 파일을 만듭니다.

- `Send-MailMessage` 에서는 `Default` 기본적으로 인코딩을 사용 합니다.

- `Start-Transcript``Utf8`BOM을 사용 하 여 파일을 만듭니다. **추가** 매개 변수를 사용 하는 경우 인코딩은 다를 수 있습니다 (아래 참조).

기존 파일에 추가 하는 명령:

- `Out-File -Append` 그리고 `>>` 리디렉션 연산자는 기존 대상 파일의 내용에 대 한 인코딩을 일치 시 키 지 않습니다. 대신 **encoding** 매개 변수를 사용 하지 않는 한 기본 인코딩을 사용 합니다. 콘텐츠를 추가할 때 원래 파일 인코딩을 사용 해야 합니다.

- 명시적 **인코딩** 매개 변수가 없는 경우는 `Add-Content` 기존 인코딩을 검색 하 고 새 내용에 자동으로 적용 합니다. 기존 콘텐츠에 BOM이 없으면 `Default` ANSI 인코딩이 사용 됩니다. 의 동작은 `Add-Content` 기본 인코딩이 인 경우를 제외 하 고 PowerShell Core (v6 이상)에서 동일 합니다 `Utf8` .

- `Export-Csv -Append` 대상 파일에 BOM이 포함 되어 있을 때 기존 인코딩과 일치 합니다. BOM이 없으면 `Utf8` 인코딩을 사용 합니다.

- `Start-Transcript -Append` BOM을 포함 하는 파일의 기존 인코딩과 일치 합니다. BOM이 없으면 기본값은 `Ascii` encoding입니다. 이 인코딩은 기록의 데이터에 멀티 바이트 문자가 포함 된 경우 데이터 손실 또는 문자 손상이 발생할 수 있습니다.

BOM이 없을 때 문자열 데이터를 읽는 cmdlet의 경우:

- `Get-Content` 및 `Import-PowerShellDataFile` 는 `Default` ANSI 인코딩을 사용 합니다. ANSI는 파일에서 소스 코드를 읽을 때 PowerShell 엔진에서 사용 하는 역할도 합니다.

- `Import-Csv`, `Import-CliXml` 및 `Select-String` `Utf8` 는 BOM이 없을 때를 가정 합니다.

## <a name="character-encoding-in-powershell-core"></a>PowerShell Core의 문자 인코딩

PowerShell Core (v6 이상)에서 **Encoding** 매개 변수는 다음 값을 지원 합니다.

- `ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.
- `bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.
- `unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `utf7`: UTF-7 형식으로 인코딩합니다.
- `utf8`: UTF-8 형식으로 인코딩합니다 (BOM 없음).
- `utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.
- `utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.
- `utf32`: U t f-32 형식으로 인코딩합니다.

PowerShell Core `utf8NoBOM` 는 모든 출력에 대해 기본적으로로 설정 됩니다.

PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ). 자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage)대 한 .net 설명서를 참조 하세요.

## <a name="changing-the-default-encoding"></a>기본 인코딩 변경

PowerShell에는 기본 인코딩 동작을 변경 하는 데 사용할 수 있는 두 가지 기본 변수가 있습니다.

- `$PSDefaultParameterValues`
- `$OutputEncoding`

자세한 내용은 [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.

PowerShell 5.1부터 리디렉션 연산자 ( `>` 및 `>>` )가 cmdlet을 호출 합니다 `Out-File` . 따라서 `$PSDefaultParameterValues` 다음 예제와 같이 기본 설정 변수를 사용 하 여 기본 인코딩을 설정할 수 있습니다.

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

다음 문을 사용 하 여 **encoding** 매개 변수가 있는 모든 cmdlet에 대 한 기본 인코딩을 변경 합니다.

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> PowerShell 프로필에이 명령을 배치 하면 인코딩을 명시적으로 지정 하지 않는 모든 명령 및 스크립트에 영향을 주는 기본 설정이 세션 전역 설정으로 지정 됩니다.
>
> 마찬가지로 동일한 방식으로 동작 하려는 스크립트나 모듈에 이러한 명령을 포함 해야 합니다. 이러한 명령을 사용 하 여 다른 사용자, 다른 컴퓨터 또는 다른 PowerShell 버전에서 실행 하는 경우에도 cmdlet이 동일한 방식으로 동작 하도록 합니다.

자동 변수는 `$OutputEncoding` PowerShell이 외부 프로그램과 통신 하는 데 사용 하는 인코딩에 영향을 줍니다. 출력 리디렉션 연산자와 PowerShell cmdlet이 파일에 저장 하는 데 사용 하는 인코딩에는 영향을 주지 않습니다.

## <a name="see-also"></a>참조

- [.NET의 문자 인코딩 소개](/dotnet/standard/base-types/character-encoding-introduction)
- [코드 페이지-Win32 앱](/windows/win32/intl/code-pages)
- [유니코드 표준](https://www.unicode.org/standard/standard.html)
- [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage)
- [UTF-16LE](https://wikipedia.org/wiki/UTF-16)
- [바이트 순서 표시](https://wikipedia.org/wiki/Byte_order_mark)
- [about_Preference_Variables](about_Preference_Variables.md)
