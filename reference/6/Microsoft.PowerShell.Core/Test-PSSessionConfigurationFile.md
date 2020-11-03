---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: ea57ae0b3affcbe060b74c6cc21e6df6d50e50ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217153"
---
# Test-PSSessionConfigurationFile

## 개요
세션 구성 파일에서 키와 값을 확인합니다.

## SYNTAX

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## 설명

이 cmdlet은 세션 구성 파일에 유효한 키가 포함 되어 있고 값이 올바른 형식 인지 확인 합니다. 열거형 값의 경우 cmdlet은 지정한 값이 유효한지 확인합니다.

이 cmdlet은 `$True` 파일이 모든 테스트를 통과 하는 경우를 반환 하 고 `$False` 그렇지 않은 경우를 반환 합니다. 오류를 찾으려면 **Verbose** 매개 변수를 사용 합니다.

`Test-PSSessionConfigurationFile` cmdlet에서 만든 파일 등의 세션 구성 파일을 확인 합니다 `New-PSSessionConfigurationFile` . 세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요. 세션 구성 파일에 대 한 자세한 내용은 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조 하세요.

이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.

## 예제

### 예제 1: 세션 구성 파일 테스트

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### 예 2: 세션 구성의 세션 구성 파일 테스트

이 예제에서는 **제한** 된 세션 구성에 사용 되는 구성 파일을 테스트 합니다.
**Path** 매개 변수 값은 `Get-PSSessionConfiguration` **제한** 된 세션 구성을 가져오는 명령의 결과입니다. 세션 구성 파일의 경로는 세션 구성의 **Configfilepath** 속성 값에 저장 됩니다.

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### 예제 3: 모든 세션 구성 파일 테스트

이 예제의 함수는 로컬 컴퓨터의 모든 세션 구성 파일을 테스트 합니다. 함수는 cmdlet을 사용 하 여 `Get-PSSessionConfiguration` 모든 세션 구성을 가져옵니다. 루프 내의 코드는 `ForEach-Object` 파일 경로를 표시 하 고 각 세션 구성을 테스트 합니다.

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

세션 구성의 **Configfilepath** 속성에는 세션 구성에 사용 되는 세션 구성 파일의 경로 (있는 경우)가 포함 됩니다.

**ConfigFilePath** 속성 값이 채워져 있을 경우(true) 이 명령은 **ConfigFilePath** 속성 값을 가져옵니다(인쇄). 그런 다음 cmdlet을 사용 하 여 `Test-PSSessionConfigurationFile` **configfilepath** 값의 파일을 테스트 합니다. **Verbose** 매개 변수는 파일이 테스트에 실패할 경우 파일 오류를 반환합니다.

## PARAMETERS

### -Path

세션 구성 파일 (.psc)의 경로와 파일 이름을 지정 합니다. 경로를 생략할 경우 기본값은 현재 폴더입니다. 와일드 카드 문자는 지원 되지만 단일 파일로 확인 되어야 합니다. 세션 구성 파일 경로를로 파이프 할 수도 있습니다 `Test-PSSessionConfigurationFile` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

세션 구성 파일 경로를로 파이프 할 수 있습니다 `Test-PSSessionConfigurationFile` .

## 출력

### System.Boolean

## 참고

## 관련 링크

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 공급자](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
