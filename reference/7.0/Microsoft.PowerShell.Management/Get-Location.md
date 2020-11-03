---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 235c775e2da4188213f4eb35612c469947b5e2fc
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2020
ms.locfileid: "93219545"
---
# Get-Location

## 개요
현재 작업 위치 또는 위치 스택에 대한 정보를 가져옵니다.

## SYNTAX

### Location (기본값)

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [<CommonParameters>]
```

### 스택

```
Get-Location [-Stack] [-StackName <String[]>] [<CommonParameters>]
```

## 설명

`Get-Location`Cmdlet은 pwd (인쇄 작업 디렉터리) 명령과 매우 유사 하 게 현재 디렉터리를 나타내는 개체를 가져옵니다.

PowerShell 드라이브 간을 이동 하면 PowerShell에서 각 드라이브의 위치를 유지 합니다. 이 cmdlet을 사용 하 여 각 드라이브에서 위치를 찾을 수 있습니다.

이 cmdlet을 사용 하 여 런타임에 현재 디렉터리를 가져오고 PowerShell 프롬프트에서 현재 디렉터리를 표시 하는 함수 등의 함수 및 스크립트에서 사용할 수 있습니다.

이 cmdlet을 사용 하 여 위치 스택의 위치를 표시할 수도 있습니다. 자세한 내용은 **Stack** 및 **stackname** 매개 변수에 대 한 참고 및 설명을 참조 하세요.

## 예제

### 예제 1: 현재 드라이브 위치 표시

이 명령은 현재 PowerShell 드라이브의 위치를 표시 합니다.

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

예를 들어, `Windows` 드라이브의 디렉터리에 있는 경우 `C:` 해당 디렉터리에 대 한 경로를 표시 합니다.

### 예 2: 다른 드라이브에 대 한 현재 위치 표시

이 예제에서는를 사용 `Get-Location` 하 여 다른 PowerShell 드라이브에 현재 위치를 표시 하는 방법을 보여 줍니다. `Set-Location` 는 다른 PSDrives에서 여러 다른 경로로 위치를 변경 하는 데 사용 됩니다.

```powershell
PS C:\> Set-Location C:\Windows
PS C:\Windows> Set-Location HKLM:\Software\Microsoft
PS HKLM:\Software\Microsoft> Set-Location "HKCU:\Control Panel\Input Method"
PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive C

Path
----
C:\Windows

PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive HKLM

Path
----
HKLM:\Software\Microsoft

PS HKCU:\Control Panel\Input Method> Set-Location C:
PS C:\Windows> Get-Location -PSProvider Registry

Path
----
HKCU:\Control Panel\Input Method
```

### 예 3: 스택을 사용 하 여 위치 가져오기

이 예제에서는의 **Stack** 및 **stackname** 매개 변수를 사용 하 여 `Get-Location` 현재 위치 스택과 대체 위치 스택의 위치를 나열 하는 방법을 보여 줍니다.

`Push-Location`Cmdlet은 3 개의 다른 위치로 변경 하는 데 사용 됩니다. 세 번째 푸시는 다른 스택 이름을 사용 합니다. 의 **stack** 매개 변수는 `Get-Location` 기본 스택의 내용을 표시 합니다. 의 **Stackname** 매개 변수는 `Get-Location` 라는 스택의 내용을 표시 합니다 `Stack2` .

```powershell
PS C:\> Push-Location C:\Windows
PS C:\Windows>Push-Location System32
PS C:\Windows\System32>Push-Location WindowsPowerShell -StackName Stack2
C:\Windows\System32\WindowsPowerShell>Get-Location -Stack

Path
----
C:\Windows
C:\

C:\Windows\System32\WindowsPowerShell>Get-Location -StackName Stack2

Path
----
C:\Windows\System32
```

### 예제 4: PowerShell 프롬프트 사용자 지정

이 예제에서는 PowerShell 프롬프트를 사용자 지정 하는 방법을 보여 줍니다.

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

프롬프트를 정의 하는 함수에는 `Get-Location` 프롬프트를 콘솔에 표시할 때마다 실행 되는 명령이 포함 되어 있습니다.

기본 PowerShell 프롬프트의 형식은 라는 특수 함수에 의해 정의 됩니다 `prompt` . 이라는 새 함수를 만들어 콘솔의 프롬프트를 변경할 수 있습니다 `prompt` .

현재 프롬프트 함수를 보려면 다음 명령을 입력 합니다. `Get-Content Function:\prompt`

## PARAMETERS

### -PSDrive

지정 된 PowerShell 드라이브의 현재 위치를 가져옵니다.

예를 들어, 드라이브에 있는 경우 `Cert:` 이 매개 변수를 사용 하 여 드라이브에서 현재 위치를 찾을 수 있습니다 `C:` .

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

지정 된 PowerShell 공급자가 지 원하는 드라이브에서 현재 위치를 가져옵니다.
지정 된 공급자가 둘 이상의 드라이브를 지 원하는 경우이 cmdlet은 가장 최근에 액세스 한 드라이브의 위치를 반환 합니다.

예를 들어, 드라이브에 있는 경우 `C:` 이 매개 변수를 사용 하 여 PowerShell **레지스트리** 공급자의 드라이브에서 현재 위치를 찾을 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -스택

이 cmdlet이 현재 위치 스택에 추가 된 위치를 표시 함을 나타냅니다. Cmdlet을 사용 하 여 스택에 위치를 추가할 수 있습니다 `Push-Location` .

다른 위치 스택에 위치를 표시 하려면 **Stackname** 매개 변수를 사용 합니다. 위치 스택에 대 한 자세한 [내용은 참고를 참조 하세요.](#notes)

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StackName

을 문자열 배열로 명명 된 위치 스택으로 지정 합니다. 위치 스택 이름을 하나 이상 입력합니다.

현재 위치 스택의 위치를 표시 하려면 **stack** 매개 변수를 사용 합니다. 위치 스택을 현재 위치 스택으로 만들려면 cmdlet을 사용 `Set-Location` 합니다.

이 cmdlet은 현재 스택이 아닌 경우 이름 없는 기본 스택의 위치를 표시할 수 없습니다.

```yaml
Type: System.String[]
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.object 또는 System.web.. d m p. PathInfoStack

**Stack** 또는 **stackname** 매개 변수를 사용 하는 경우이 Cmdlet은 **pathinfostack** 개체를 반환 합니다. 그렇지 않으면 **Pathinfo** 개체를 반환 합니다.

## 참고

PowerShell은 프로세스 당 여러 runspace를 지원 합니다. 각 runspace에는 자체의 _현재 디렉터리가_ 있습니다.
와는 다릅니다 `[System.Environment]::CurrentDirectory` . 이 동작은 명시적 디렉터리 경로를 제공 하지 않고 .NET Api를 호출 하거나 네이티브 응용 프로그램을 실행할 때 문제가 될 수 있습니다.
`Get-Location`Cmdlet은 현재 PowerShell runspace의 현재 디렉터리를 반환 합니다.

이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션의 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

**Psprovider** , **PSDrive** , **Stack** 및 **stackname** 매개 변수가 상호 작용 하는 방법은 공급자에 따라 다릅니다. 드라이브와 해당 드라이브를 노출하지 않는 공급자를 둘 다 지정하는 경우 등 일부 조합에서는 오류가 발생합니다. 매개 변수를 지정 하지 않으면이 cmdlet은 현재 작업 위치를 포함 하는 공급자에 대 한 **Pathinfo** 개체를 반환 합니다.

스택은 가장 최근에 추가 된 항목만 액세스할 수 있는 마지막으로 시작 된 목록입니다. 사용하는 순서대로 스택에 항목을 추가한 다음 사용을 위해 역순으로 검색합니다. PowerShell을 사용 하 여 공급자 위치를 위치 스택에 저장할 수 있습니다. PowerShell은 이름 없는 기본 위치 스택을 만들고 여러 개의 명명 된 위치 스택을 만들 수 있습니다. 스택 이름을 지정 하지 않으면 PowerShell은 현재 위치 스택을 사용 합니다. 기본적으로 이름 없는 기본 위치는 현재 위치 스택입니다. 하지만 cmdlet을 사용 `Set-Location` 하 여 현재 위치 스택을 변경할 수 있습니다.

위치 스택을 관리 하려면 `*-Location` 다음과 같이 PowerShell cmdlet을 사용 합니다.

- 위치 스택에 위치를 추가 하려면 cmdlet을 사용 `Push-Location` 합니다.

- 위치 스택에서 위치를 가져오려면 cmdlet을 사용 `Pop-Location` 합니다.

- 현재 위치 스택의 위치를 표시 하려면 cmdlet의 **stack** 매개 변수를 사용 합니다 `Get-Location` . 명명 된 위치 스택의 위치를 표시 하려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Get-Location` .

- 새 위치 스택을 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 `Push-Location` 합니다.
  존재 하지 않는 스택을 지정 하면에서 `Push-Location` 스택을 만듭니다.

- 위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Set-Location` .

이름 없는 기본 위치 스택은 현재 위치 스택인 경우에만 완전히 액세스할 수 있습니다.
명명 된 위치 스택을 현재 위치 스택으로 만든 경우 더 이상 `Push-Location` 또는 cmdlet을 사용 `Pop-Location` 하 여 기본 스택에서 항목을 추가 하거나 가져올 수 없으며이 cmdlet을 사용 하 여 명명 되지 않은 스택의 위치를 표시할 수 있습니다. 명명 되지 않은 스택을 현재 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 `Set-Location` 값 `$null` 이나 빈 문자열 ()로 사용 `""` 합니다.

## 관련 링크

[Pop-Location](Pop-Location.md)

[Push-Location](Push-Location.md)

[Set-Location](Set-Location.md)
