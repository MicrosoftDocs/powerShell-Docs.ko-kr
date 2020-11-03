---
description: 세션 구성 ("끝점"이 라고도 함)에서 세션 구성을 사용 하는 세션 환경을 정의 하는 데 사용 되는 세션 구성 파일에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configuration_Files
ms.openlocfilehash: 198a0aeb667c3c947bc7e202bc3c0d9832195b91
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222529"
---
# <a name="about-session-configuration-files"></a>세션 구성 파일 정보

## <a name="short-description"></a>간단한 설명

세션 구성 ("끝점"이 라고도 함)에서 세션 구성을 사용 하는 세션 환경을 정의 하는 데 사용 되는 세션 구성 파일에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

"세션 구성 파일"은 세션 구성 속성 및 값의 해시 테이블을 포함 하는 .psc 파일 이름 확장명을 포함 하는 텍스트 파일입니다. 세션 구성 파일을 사용 하 여 세션 구성의 속성을 설정할 수 있습니다. 이렇게 하면 해당 세션 구성을 사용 하는 Windows PowerShell 세션의 환경이 정의 됩니다.

세션 구성 파일을 사용 하면 복잡 한 c # 어셈블리나 스크립트를 사용 하지 않고 사용자 지정 세션 구성을 쉽게 만들 수 있습니다.

"세션 구성" 또는 "엔드포인트"는 사용자가 컴퓨터에서 세션을 만들 수 있는 작업을 결정 하는 로컬 컴퓨터 설정의 컬렉션입니다. 사용자가 해당 세션에서 실행할 수 있는 명령 세션을 권한 있는 가상 계정으로 실행할지 여부를 지정 합니다. 세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](about_Session_Configurations.md)를 참조 하세요.

세션 구성은 Windows PowerShell 2.0에서 도입 되었으며 세션 구성 파일은 Windows PowerShell 3.0에서 도입 되었습니다. 세션 구성에 세션 구성 파일을 포함 하려면 Windows PowerShell 3.0을 사용 해야 합니다. 그러나 Windows PowerShell 2.0 (이상)의 사용자는 세션 구성의 설정에 영향을 받습니다.

## <a name="creating-custom-sessions"></a>사용자 지정 세션 만들기

세션 구성에서 세션 속성을 지정 하 여 Windows PowerShell 세션의 여러 기능을 사용자 지정할 수 있습니다. 사용자 지정 runspace를 정의 하는 c # 프로그램을 작성 하 여 세션을 사용자 지정 하거나 세션 구성 파일을 사용 하 여 세션 구성을 사용 하 여 만든 세션의 속성을 정의할 수 있습니다. 일반적으로 c # 프로그램을 작성 하는 것 보다 세션 구성 파일을 사용 하는 것이 더 쉽습니다.

세션 구성 파일을 사용 하 여 신뢰할 수 있는 사용자에 대해 완전히 작동 하는 세션과 같은 항목을 만들 수 있습니다. 최소한의 액세스를 허용 하는 잠긴 세션 특별히 설계 되었으며 해당 작업에 필요한 모듈만 포함 하는 세션 권한 없는 사용자가 권한 있는 계정으로 특정 명령만 실행할 수 있는 세션입니다.

그 외에도 세션의 사용자가 스크립트 블록 등의 Windows PowerShell 언어 요소를 사용할 수 있는지 여부 또는 명령을 실행할 수 있는지 여부를 관리할 수 있습니다. 사용자가 세션에서 실행할 수 있는 Windows PowerShell 버전을 관리할 수 있습니다. 세션으로 가져올 모듈을 관리 합니다. 그리고 사용자가 실행할 수 있는 cmdlet, 함수 및 별칭 세션을 관리 합니다. RoleDefinitions 필드를 사용 하는 경우 그룹 멤버 자격을 기반으로 세션에서 사용자에 게 다른 기능을 제공할 수 있습니다.

RoleDefinitions이 값을 정의 하는 방법에 대 한 자세한 내용은 New-PSRoleCapabilityFile Cmdlet에 대 한 도움말 항목을 참조 하세요.

## <a name="creating-a-session-configuration-file"></a>세션 구성 파일 만들기

세션 구성 파일을 만드는 가장 쉬운 방법은 New-PSSessionConfigurationFile cmdlet을 사용 하는 것입니다. 이 cmdlet은 올바른 구문과 형식을 사용 하며 많은 구성 파일 속성 값을 자동으로 확인 하는 파일을 생성 합니다.

세션 구성 파일에서 설정할 수 있는 속성에 대 한 자세한 설명은 New-PSSessionConfigurationFile cmdlet에 대 한 도움말 항목을 참조 하세요.

다음 명령은 기본값을 사용 하는 세션 구성 파일을 만듭니다. 파일 경로를 지정 하는 경로 매개 변수 이외의 매개 변수가 포함 되어 있지 않기 때문에 결과 구성 파일은 기본값을 사용 합니다.

```powershell
New-PSSessionConfigurationFile -Path .\Defaults.pssc
```

기본 텍스트 편집기에서 새 구성 파일을 보려면 다음 명령을 사용 합니다.

```powershell
Invoke-Item -Path .\Defaults.pssc
```

사용자가 명령을 실행할 수 있지만 Windows PowerShell 언어의 다른 요소를 사용 하지 않는 세션에 대 한 세션 구성을 만들려면 다음을 입력 합니다.

```powershell
New-PSSessionConfigurationFile -LanguageMode NoLanguage
-Path .\NoLanguage.pssc
```

이전 명령에서 LanguageMode 매개 변수를 NoLanguage로 설정 하면 사용자가 스크립트를 작성 하거나 실행 하거나 변수를 사용 하는 등의 작업을 수행할 수 없습니다.

사용자가 Get cmdlet만 사용할 수 있는 세션에 대 한 세션 구성을 만들려면 다음을 입력 합니다.

```powershell
New-PSSessionConfigurationFile -VisibleCmdlets Get-*
-Path .\GetSessions.pssc
```

앞의 예제에서 VisibleCmdlets 매개 변수를 Get-*로 설정 하면 이름이 문자열 값 "Get-"으로 시작 하는 cmdlet으로 제한 됩니다.

사용자의 자격 증명 대신 권한 있는 가상 계정으로 실행 되는 세션에 대 한 세션 구성을 만들려면 다음을 입력 합니다.

```powershell
New-PSSessionConfigurationFile -RunAsVirtualAccount
-Path .\VirtualAccount.pssc
```

사용자에 게 표시 되는 명령이 역할 기능 파일에 지정 된 세션에 대 한 세션 구성을 만들려면 다음을 입력 합니다.

```powershell
New-PSSessionConfigurationFile -RoleDefinitions
@{ 'CONTOSO\User' = @{ RoleCapabilities = 'Maintenance' }}
-Path .\Maintenance.pssc
```

### <a name="using-a-session-configuration-file"></a>세션 구성 파일 사용

세션 구성 파일을 포함할 수 있습니다. 세션 구성 파일을 추가 하거나 추가 하 여 나중에 세션 구성에 파일을 추가할 수 있습니다.

세션 구성을 만들 때 세션 구성 파일을 포함 하려면 Register-PSSessionConfiguration cmdlet의 Path 매개 변수를 사용 합니다.

예를 들어 다음 명령은 nolanguage. pssc 파일을 사용 하 여 NoLanguage 세션 구성을 만듭니다.

```powershell
Register-PSSessionConfiguration -Name NoLanguage
-Path .\NoLanguage.pssc
```

새 NoLanguage 세션이 시작 되 면 사용자는 Windows PowerShell 명령에만 액세스할 수 있습니다.

기존 세션 구성에 세션 구성 파일을 추가 하려면 Set-PSSessionConfiguration cmdlet 및 Path 매개 변수를 사용 합니다. 이는 지정 된 세션 구성을 사용 하 여 만든 모든 새 세션에 영향을 줍니다. Set-PSSessionConfiguration cmdlet은 세션 자체를 변경 하 고 세션 구성 파일을 수정 하지 않습니다.

예를 들어 다음 명령은 NoLanguage .pssc 파일을 LockedDown 세션 구성에 추가 합니다.

```powershell
Set-PSSessionConfiguration -Name LockedDown
-Path .\NoLanguage.pssc
```

사용자가 LockedDown 세션 구성을 사용 하 여 세션을 만드는 경우 cmdlet을 실행할 수는 있지만 변수를 만들거나 사용 하거나 값을 할당 하거나 다른 Windows PowerShell 언어 요소를 사용할 수 없습니다.

다음 명령은 New-PSSession cmdlet을 사용 하 여 LockedDown 세션 구성을 사용 하는 Srv01 컴퓨터에서 세션을 만들고 $s 변수에 세션에 대 한 개체 참조를 저장 합니다. 세션 구성의 ACL (액세스 제어 목록)은이를 사용 하 여 세션을 만들 수 있는 사용자를 결정 합니다.

```powershell
$s = New-PSSession -ComputerName Srv01
-ConfigurationName LockedDown
```

NoLanguage 제약 조건이 LockedDown 세션 구성에 추가 되었으므로 LockedDown 세션의 사용자는 Windows PowerShell 명령 및 cmdlet만 실행할 수 있습니다. 예를 들어 다음 두 명령은 Invoke-Command cmdlet을 사용 하 여 $s 변수에 참조 된 세션에서 명령을 실행 합니다. Get-UICulture cmdlet을 실행 하 고 변수를 사용 하지 않는 첫 번째 명령은 성공 합니다. $PSUICulture 변수의 값을 가져오는 두 번째 명령은 실패 합니다.

```
Invoke-Command -Session $s {Get-UICulture}
en-US

Invoke-Command -Session $s {$PSUICulture}
The syntax is not supported by this runspace. This might be
because it is in no-language mode.
+ CategoryInfo          : ParserError: ($PSUICulture:String) [],
ParseException
+ FullyQualifiedErrorId : ScriptsNotAllowed
```

## <a name="editing-a-session-configuration-file"></a>세션 구성 파일 편집

RunAsVirtualAccount 및 RunAsVirtualAccountGroups를 제외한 세션 구성의 모든 설정은 세션 구성에서 사용 하는 세션 구성 파일을 편집 하 여 수정할 수 있습니다. 이렇게 하려면 먼저 세션 구성 파일의 활성 복사본을 찾습니다.

세션 구성에서 세션 구성 파일을 사용 하는 경우 Windows PowerShell은 세션 구성 파일의 활성 복사본을 만들고 \$ \\ 로컬 컴퓨터의 pshome sessionconfig 디렉터리에 저장 합니다.

세션 구성 파일의 활성 복사본 위치는 세션 구성 개체의 ConfigFilePath 속성에 저장 됩니다.

다음 명령은 NoLanguage 세션 구성에 대 한 세션 구성 파일의 위치를 가져옵니다.

```powershell
(Get-PSSessionConfiguration -Name NoLanguage).ConfigFilePath
```

이 명령은 다음과 비슷한 파일 경로를 반환 합니다.

```
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

텍스트 편집기에서 .psc 파일을 편집할 수 있습니다. 파일이 저장 되 면 세션 구성을 사용 하는 모든 새 세션에 사용 됩니다.

RunAsVirtualAccount 또는 RunAsVirtualAccountGroups 설정을 수정 해야 하는 경우 세션 구성의 등록을 취소 하 고 편집 된 값을 포함 하는 세션 구성 파일을 다시 등록 해야 합니다.

## <a name="testing-a-session-configuration-file"></a>세션 구성 파일 테스트

Test-PSSessionConfigurationFile cmdlet을 사용 하 여 수동으로 편집한 세션 구성 파일을 테스트 합니다. 이는 중요 합니다. 파일 구문 및 값이 유효 하지 않으면 사용자가 세션 구성을 사용 하 여 세션을 만들 수 없습니다.

예를 들어 다음 명령은 NoLanguage 세션 구성의 활성 세션 구성 파일을 테스트 합니다.

```powershell
Test-PSSessionConfigurationFile -Path C:\WINDOWS\System32\
WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

구성 파일의 구문과 값이 유효한 경우 Test-PSSessionConfigurationFile True를 반환 합니다. 구문과 값이 유효 하지 않은 경우에는 cmdlet이 False를 반환 합니다.

Test-PSSessionConfigurationFile를 사용 하 여 New-PSSessionConfiguration cmdlet이 만드는 파일을 비롯 한 모든 세션 구성 파일을 테스트할 수 있습니다. 자세한 내용은 Test-PSSessionConfigurationFile cmdlet에 대 한 도움말 항목을 참조 하세요.

## <a name="removing-a-session-configuration-file"></a>세션 구성 파일 제거

세션 구성에서 세션 구성 파일을 제거할 수 없습니다.
그러나 기본 설정을 사용 하는 새 파일로 파일을 바꿀 수 있습니다. 이렇게 하면 원래 구성 파일에 사용 되는 설정이 효율적으로 취소 됩니다.

세션 구성 파일을 바꾸려면 기본 설정을 사용 하는 새 세션 구성 파일을 만든 다음 Set-PSSessionConfiguration cmdlet을 사용 하 여 사용자 지정 세션 구성 파일을 새 파일로 바꿉니다.

예를 들어 다음 명령은 기본 세션 구성 파일을 만든 다음 NoLanguage 세션 구성에서 활성 세션 구성 파일을 바꿉니다.

```powershell
New-PSSessionConfigurationFile -Path .\Default.pssc
Set-PSSessionConfiguration -Name NoLanguage
-Path .\Default.pssc
```

이 명령이 완료 되 면 NoLanguage 세션 구성은 실제로 해당 세션 구성을 사용 하 여 만든 모든 세션에 대 한 완전 한 언어 지원 (기본 설정)을 제공 합니다.

세션 구성의 속성 보기 세션 구성 파일을 사용 하 여 세션 구성을 나타내는 세션 구성 개체에는 세션 구성을 쉽게 검색 하 고 분석할 수 있도록 하는 추가 속성이 있습니다. 아래에 표시 된 형식 이름에는 서식이 지정 된 뷰 정의가 포함 되어 있습니다. Get-PSSessionConfiguration cmdlet을 실행 하 고 반환 된 데이터를 Get-Member cmdlet에 파이프 하 여 속성을 볼 수 있습니다.

```powershell
Get-PSSessionConfiguration NoLanguage | Get-Member
```

```output
TypeName: Microsoft.PowerShell.Commands.PSSessionConfigurationCommands
#PSSessionConfiguration

Name                          MemberType     Definition
----                          ----------     ----------
Equals                        Method         bool Equals(System.O...
GetHashCode                   Method         int GetHashCode()
GetType                       Method         type GetType()
ToString                      Method         string ToString()
Architecture                  NoteProperty   System.String Archit...
Author                        NoteProperty   System.String Author...
AutoRestart                   NoteProperty   System.String AutoRe...
Capability                    NoteProperty   System.Object[] Capa...
CompanyName                   NoteProperty   System.String Compan...
configfilepath                NoteProperty   System.String config...
Copyright                     NoteProperty   System.String Copyri...
Enabled                       NoteProperty   System.String Enable...
ExactMatch                    NoteProperty   System.String ExactM...
ExecutionPolicy               NoteProperty   System.String Execut...
Filename                      NoteProperty   System.String Filena...
GUID                          NoteProperty   System.String GUID=0...
ProcessIdleTimeoutSec         NoteProperty   System.String Proces...
IdleTimeoutms                 NoteProperty   System.String IdleTi...
lang                          NoteProperty   System.String lang=e...
LanguageMode                  NoteProperty   System.String Langua...
MaxConcurrentCommandsPerShell NoteProperty   System.String MaxCon...
MaxConcurrentUsers            NoteProperty   System.String MaxCon...
MaxIdleTimeoutms              NoteProperty   System.String MaxIdl...
MaxMemoryPerShellMB           NoteProperty   System.String MaxMem...
MaxProcessesPerShell          NoteProperty   System.String MaxPro...
MaxShells                     NoteProperty   System.String MaxShells
MaxShellsPerUser              NoteProperty   System.String MaxShe...
Name                          NoteProperty   System.String Name=N...
PSVersion                     NoteProperty   System.String PSVersion
ResourceUri                   NoteProperty   System.String Resour...
RunAsPassword                 NoteProperty   System.String RunAsP...
RunAsUser                     NoteProperty   System.String RunAsUser
SchemaVersion                 NoteProperty   System.String Schema...
SDKVersion                    NoteProperty   System.String SDKVer...
OutputBufferingMode           NoteProperty   System.String Output...
SessionType                   NoteProperty   System.String Sessio...
UseSharedProcess              NoteProperty   System.String UseSha...
SupportsOptions               NoteProperty   System.String Suppor...
xmlns                         NoteProperty   System.String xmlns=...
XmlRenderingType              NoteProperty   System.String XmlRen...
Permission                    ScriptProperty System.Object Permis...
```

이러한 속성을 통해 특정 세션 구성을 쉽게 검색할 수 있습니다.
예를 들어 Set-executionpolicy 속성을 사용 하 여 RemoteSigned 실행 정책을 통해 세션을 지 원하는 세션 구성을 찾을 수 있습니다.
Set-executionpolicy 속성은 세션 구성 파일을 사용 하는 세션에만 존재 하기 때문에 명령은 정규화 된 세션 구성을 모두 반환 하지 않을 수 있습니다.

```powershell
Get-PSSessionConfiguration |
where {$_.ExecutionPolicy -eq "RemoteSigned"}
```

다음 명령은 RunAsUser가 Exchange 관리자 인 세션 구성을 가져옵니다.

```powershell
 Get-PSSessionConfiguration |
where {$_.RunAsUser -eq "Exchange01\Admin01"}
```

구성과 관련 된 역할 정의에 대 한 정보를 보려면 Get-PSSessionCapability cmdlet을 사용 합니다. 이 cmdlet을 사용 하면 특정 끝점의 특정 사용자가 사용할 수 있는 명령 및 환경을 결정할 수 있습니다.

## <a name="notes"></a>참고

세션 구성은 "빈" 세션 이라는 유형의 세션도 지원 합니다. 빈 세션 유형을 사용 하면 선택한 명령을 사용 하 여 사용자 지정 세션을 만들 수 있습니다. 빈 세션에 모듈, 함수 또는 스크립트를 추가 하지 않으면 세션은 식으로 제한 되며 실용적으로 사용 되지 않을 수 있습니다. SessionType 속성은 빈 세션으로 작업 하 고 있는지 여부를 알려 줍니다.

## <a name="see-also"></a>참고 항목

[about_Session_Configurations](about_Session_Configurations.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Enable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Unregister-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

[Get-PSSessionCapability](xref:Microsoft.PowerShell.Core.Get-PSSessionCapability)

[New-PSRoleCapabilityFile](xref:Microsoft.PowerShell.Core.New-PSRoleCapabilityFile)
