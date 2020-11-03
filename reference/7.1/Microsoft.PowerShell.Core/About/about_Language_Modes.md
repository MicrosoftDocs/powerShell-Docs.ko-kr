---
description: 언어 모드 및 PowerShell 세션에 미치는 영향을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 0b94125574bc65359b264225bb6c64231c1052d7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220441"
---
# <a name="about-language-modes"></a>언어 모드 정보

## <a name="short-description"></a>간단한 설명
언어 모드 및 PowerShell 세션에 미치는 영향을 설명 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell 세션의 언어 모드에서는 세션에서 사용할 수 있는 PowerShell 언어 요소를 부분적으로 결정 합니다.

PowerShell은 다음과 같은 언어 모드를 지원 합니다.

- FullLanguage
- ConstrainedLanguage (PowerShell 3.0에 도입 됨)
- RestrictedLanguage
- NoLanguage

### <a name="what-is-a-language-mode"></a>언어 모드는 무엇입니까?

언어 모드는 세션에서 허용 되는 언어 요소를 결정 합니다.

언어 모드는 실제로 세션을 만드는 데 사용 되는 세션 구성 (또는 "끝점")의 속성입니다. 특정 세션 구성을 사용 하는 모든 세션에는 세션 구성의 언어 모드가 있습니다.

모든 PowerShell 세션에는 cmdlet을 사용 하 여 만든 pssession `New-PSSession` , ComputerName 매개 변수를 사용 하는 임시 세션, powershell을 시작할 때 표시 되는 기본 세션 등의 언어 모드가 있습니다.

원격 세션은 원격 컴퓨터의 세션 구성을 사용 하 여 만듭니다. 세션 구성에 설정 된 언어 모드는 세션의 언어 모드를 결정 합니다. PSSession의 세션 구성을 지정 하려면 세션을 만드는 cmdlet의 ConfigurationName 매개 변수를 사용 합니다.

### <a name="language-modes"></a>언어 모드

이 섹션에서는 PowerShell 세션의 언어 모드에 대해 설명 합니다.

#### <a name="full-language-fulllanguage"></a>전체 언어 (FullLanguage)

FullLanguage 모드는 세션의 모든 언어 요소를 허용 합니다.
FullLanguage는 Windows RT를 제외한 모든 Windows 버전에서 기본 세션의 기본 언어 모드입니다.

#### <a name="restricted-language-restrictedlanguage"></a>제한 된 언어 (RestrictedLanguage)

RestrictedLanguage 모드에서 사용자는 명령 (cmdlet, 함수, CIM 명령 및 워크플로)을 실행할 수 있지만 스크립트 블록을 사용할 수는 없습니다.

기본적으로 RestrictedLanguage 모드에서는 다음 변수만 사용할 수 있습니다.

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

RestrictedLanguage 모드를 사용 하는 모듈 매니페스트는 다음과 같은 추가 변수도 허용 합니다.

- `$PSScriptRoot`
- `$PSEdition` (PowerShell Core에서)
- `$EnabledExperimentalFeatures` (PowerShell Core에서)

다음 비교 연산자만 사용할 수 있습니다.

- `-eq` 다릅니다
- `-gt` (보다 큼)
- `-lt` (보다 작음)

대입문, 속성 참조 및 메서드 호출은 허용되지 않습니다.

#### <a name="no-language-nolanguage"></a>언어 없음 (NoLanguage)

NoLanguage 모드는 API를 통해서만 사용할 수 있습니다. NoLanguage 모드는 모든 형식의 스크립트 텍스트가 허용 되지 않음을 의미 합니다. 이를 통해 구문 분석 되 고 실행 되는 PowerShell 스크립트의 조각을 보내는 **Addscript ()** 메서드를 사용할 수 없습니다. 파서를 통과 하지 않는 **Addcommand ()** 및 **addcommand ()** 만 사용할 수 있습니다.

#### <a name="constrained-language-constrained-language"></a>제약이 있는 언어 (제한 언어)

ConstrainedLanguage 모드는 모든 cmdlet 및 모든 PowerShell 언어 요소를 허용 하지만 허용 된 형식을 제한 합니다.

ConstrainedLanguage 모드는 Windows RT에서 UMCI (사용자 모드 코드 무결성)를 지원 하도록 설계 되었습니다. 이 모드는 Windows RT에서 유일 하 게 지원 되는 언어 모드 이지만 지원 되는 모든 시스템에서 사용할 수 있습니다.

UMCI는 Windows RT 기반 장치에 Microsoft 서명 및 Microsoft 인증 앱만 설치 하도록 허용 하 여 ARM 장치를 보호 합니다.
ConstrainedLanguage 모드를 사용 하면 사용자가 PowerShell을 사용 하 여 UMCI를 우회 하거나 위반할 수 없습니다.

ConstrainedLanguage 모드의 기능은 다음과 같습니다.

- Windows 모듈의 모든 cmdlet 및 기타 UMCI 승인 된 cmdlet은 완전히 작동 하며, 명시 된 경우를 제외 하 고 시스템 리소스에 대 한 완전 한 액세스 권한을 가집니다.

- PowerShell 스크립트 언어의 모든 요소를 사용할 수 있습니다.

- Windows에 포함 된 모든 모듈을 가져올 수 있으며, 모듈 내보내기가 세션에서 실행 하는 모든 명령을 가져올 수 있습니다.

- PowerShell 워크플로에서 스크립트 워크플로 (PowerShell 언어로 작성 된 워크플로)를 작성 하 고 실행할 수 있습니다. XAML 기반 워크플로는 지원 되지 않으므로를 사용 하는 등의 스크립트 워크플로에서는 XAML을 실행할 수 없습니다 `Invoke-Expression -Language XAML` . 또한 중첩 된 워크플로가 허용 되지만 워크플로는 다른 워크플로를 호출할 수 없습니다.

- `Add-Type`Cmdlet은 서명 된 어셈블리를 로드할 수 있지만 임의의 c # 코드 또는 Win32 api는 로드할 수 없습니다.

- 이 `New-Object` cmdlet은 허용 되는 형식 (아래 참조)에만 사용할 수 있습니다.

- PowerShell에서 허용 되는 유형 (아래에 나열 됨)만 사용할 수 있습니다. 다른 형식은 허용 되지 않습니다.

- 형식을 변환할 수 있지만 결과가 허용 되는 형식입니다.

- 문자열 입력을 형식으로 변환 하는 Cmdlet 매개 변수는 결과 형식이 허용 되는 형식인 경우에만 작동 합니다.

- **ToString ()** 메서드 및 허용 되는 형식 (아래 나열 됨)의 .net 메서드를 호출할 수 있습니다. 다른 메서드는 호출할 수 없습니다.

- 사용자는 허용 된 형식의 모든 속성을 가져올 수 있습니다. 사용자는 코어 유형에만 속성 값을 설정할 수 있습니다. 다음 COM 개체만 허용 됩니다.

  - **Scripting. 사전**
  - **Scripting.FileSystemObject**
  - **VBScript. RegExp**

ConstrainedLanguage 모드에서 허용 되는 형식은 다음과 같습니다. 사용자는 속성을 가져오고, 메서드를 호출 하 고, 개체를 이러한 형식으로 변환할 수 있습니다.

허용 되는 형식:

- AliasAttribute
- AllowEmptyCollectionAttribute
- AllowEmptyStringAttribute
- AllowNullAttribute
- 배열
- Bool
- byte
- char
- CmdletBindingAttribute
- DateTime
- decimal
- DirectoryEntry
- DirectorySearcher
- double
- float
- GUID
- Hashtable
- int
- Int16
- long
- ManagementClass
- ManagementObject
- ManagementObjectSearcher
- NullString
- OutputTypeAttribute
- ParameterAttribute
- PSCredential
- PSDefaultValueAttribute
- PSListModifier
- PSObject
- PSPrimitiveDictionary
- PSReference
- PSTypeNameAttribute
- Regex
- SByte
- 문자열
- SupportsWildcardsAttribute
- SwitchParameter
- System.object. CultureInfo
- 시스템 .Net. IPAddress
- 시스템 .Net. 메일 주소
- BigInteger
- System.Security.SecureString
- TimeSpan
- UInt16
- UInt32
- UInt64

### <a name="finding-the-language-mode-of-a-session-configuration"></a>세션 구성의 언어 모드 찾기

세션 구성 파일을 사용 하 여 세션 구성을 만드는 경우 세션 구성에는 LanguageMode 속성이 있습니다. LanguageMode 속성 값을 가져와서 언어 모드를 찾을 수 있습니다.

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

다른 세션 구성에서는 세션 구성을 사용 하 여 만든 세션의 언어 모드를 찾아 언어 모드를 간접적으로 찾을 수 있습니다.

### <a name="finding-the-language-mode-of-a-session"></a>세션의 언어 모드 찾기

세션 상태의 LanguageMode 속성 값을 가져와 FullLanguage 또는 ConstrainedLanguage 세션의 언어 모드를 찾을 수 있습니다.

다음은 그 예입니다. 

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

그러나 RestrictedLanguage 및 NoLanguage 모드를 사용 하는 세션에서는 점 메서드를 사용 하 여 속성 값을 가져올 수 없습니다. 대신 오류 메시지가 언어 모드를 표시 합니다.

`$ExecutionContext.SessionState.LanguageMode`RestrictedLanguage 세션에서 명령을 실행 하면 PowerShell에서 PropertyReferenceNotSupportedInDataSection 및 VariableReferenceNotSupportedInDataSection 오류 메시지를 반환 합니다.

- PropertyReferenceNotSupportedInDataSection: 제한 된 언어 모드 또는 데이터 섹션에는 속성 참조를 사용할 수 없습니다.
- 제한 된 언어 모드에서 참조할 수 없는 변수를 VariableReferenceNotSupportedInDataSection 하거나 데이터 섹션을 참조 하 고 있습니다.

`$ExecutionContext.SessionState.LanguageMode`NoLanguage 세션에서 명령을 실행 하면 PowerShell에서 ScriptsNotAllowed 오류 메시지를 반환 합니다.

- ScriptsNotAllowed:이 runspace에서 구문을 지원 하지 않습니다. 언어가 언어 모드에 있지 않기 때문일 수 있습니다.

## <a name="keywords"></a>어

- about_ConstrainedLanguage
- about_FullLanguage
- about_NoLanguage
- about_RestrictedLanguage

## <a name="see-also"></a>참고 항목

- [about_Session_Configuration_Files](about_Session_Configuration_Files.md)
- [about_Session_Configurations](about_Session_Configurations.md)

