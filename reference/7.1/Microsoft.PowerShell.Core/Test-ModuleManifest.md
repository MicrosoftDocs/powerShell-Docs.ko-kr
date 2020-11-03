---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: 36232f96f8d9e51b4151b971321b1b91a8a3fb00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216961"
---
# Test-ModuleManifest

## 개요
모듈 매니페스트 파일이 모듈의 내용을 정확하게 설명하는지 확인합니다.

## SYNTAX

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## 설명

**New-modulemanifest** cmdlet은 모듈 매니페스트 (. psd1) 파일에 나열 된 파일이 실제로 지정 된 경로에 있는지 확인 합니다.

이 cmdlet은 모듈 작성자가 매니페스트 파일을 테스트하는 데 도움을 주기 위해 설계되었습니다.
모듈 사용자는 스크립트와 명령에서이 cmdlet을 사용 하 여 모듈에 종속 된 스크립트를 실행 하기 전에 오류를 검색할 수도 있습니다.

**New-modulemanifest** 는 모듈을 나타내는 개체를 반환 합니다.
Get-Module 반환 하는 것과 동일한 형식의 개체입니다.
매니페스트에 지정된 위치에 파일이 없는 경우 이 cmdlet은 없는 각 파일에 대한 오류도 생성합니다.

## 예제

### 예제 1: 매니페스트 테스트

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

이 명령은 TestModule.psd1 모듈 매니페스트를 테스트합니다.

### 예제 2: 파이프라인을 사용 하 여 매니페스트 테스트

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

이 명령은 파이프라인 연산자 (|)를 사용 하 여 **new-modulemanifest** 에 경로 문자열을 보냅니다.

명령 출력에서는 매니페스트에 나열된 TestTypes.ps1xml 파일을 찾을 수 없어서 테스트가 실패했음을 보여 줍니다.

### 예제 3: 모듈 매니페스트를 테스트 하는 함수 작성

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

이 함수는 **new-modulemanifest** 와 유사 하지만 부울 값을 반환 합니다.
함수는 매니페스트가 테스트를 통과 한 경우 $True을 반환 하 고 그렇지 않으면 $False 합니다.

함수는 Get-ChildItem cmdlet, alias = dir을 사용 하 여 $path 변수로 지정 된 모듈 매니페스트를 가져옵니다.
이 명령은 파이프라인 연산자 (|)를 사용 하 여 파일 개체를 **new-modulemanifest** 에 전달 합니다.

**New-modulemanifest** 는 값이 SilentlyContinue 인 *erroraction* 일반 매개 변수를 사용 하 여 명령이 생성 하는 오류를 표시 하지 않습니다.
또한 **new-modulemanifest** 에서 반환 하는 **psmoduleinfo** 개체를 $a 변수에 저장 합니다.
따라서 개체는 표시 되지 않습니다.

그러면 별도의 명령에서 함수에 $?의 값이 표시 됩니다.
자동 변수입니다.
이전 명령에서 오류를 생성 하지 않으면 명령은 $True를 표시 하 고, 그렇지 않으면 $False 합니다.

**Import-module 명령이 나** 모듈을 사용 하는 명령 앞에 올 수 있는 조건문과 같은 조건문에서이 함수를 사용할 수 있습니다.

## PARAMETERS

### -Path

매니페스트 파일의 경로와 파일 이름을 지정 합니다.
Psd1 파일 이름 확장명을 가진 모듈 매니페스트 파일의 선택적 경로 및 이름을 입력 합니다.
기본 위치는 현재 디렉터리입니다.
와일드 카드 문자는 지원 되지만 단일 모듈 매니페스트 파일로 확인 되어야 합니다.
이 매개 변수는 필수적 요소입니다.
**New-modulemanifest** 에 대 한 경로를 파이프 할 수도 있습니다.

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

모듈 매니페스트에 대 한 경로를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### System.object..

이 cmdlet은 모듈을 나타내는 **Psmoduleinfo** 개체를 반환 합니다.
매니페스트에 오류가 있는 경우에도 이 개체를 반환합니다.

## 참고

## 관련 링크

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[모듈 가져오기](Import-Module.md)

[New-Module](New-Module.md)

[New-ModuleManifest](New-ModuleManifest.md)

[Remove-Module](Remove-Module.md)

[about_Modules](About/about_Modules.md)

