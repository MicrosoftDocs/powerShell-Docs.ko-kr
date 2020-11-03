---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 42a5c9c75c11a40b5bb842d86894688a354bed15
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/06/2020
ms.locfileid: "93219178"
---
# Pop-Location

## 개요
현재 위치를 가장 최근에 스택에 밀어 넣은 위치로 변경합니다.

## SYNTAX

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## 설명

`Pop-Location`Cmdlet은 cmdlet을 사용 하 여 현재 위치를 가장 최근에 스택에 푸시한 위치로 변경 합니다 `Push-Location` . 기본 스택 또는 명령을 사용 하 여 만든 스택에서 위치를 표시할 수 있습니다 `Push-Location` .

## 예제

### 예제 1: 최신 위치로 변경

```
PS C:\> Pop-Location
```

이 명령은 사용자 위치를 가장 최근에 현재 스택에 추가된 위치로 변경합니다.

### 예제 2: 명명 된 스택의 가장 최근 위치로 변경

```
PS C:\> Pop-Location -StackName "Stack2"
```

이 명령은 사용자 위치를 가장 최근에 Stack2 위치 스택에 추가된 위치로 변경합니다.

위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)

### 예 3: 다른 공급자의 위치 간 이동

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

이러한 명령은 `Push-Location` 및 cmdlet을 사용 `Pop-Location` 하 여 서로 다른 PowerShell 공급자가 지 원하는 위치 간에 이동 합니다. 이 명령은에 별칭을 사용 하 `pushd` `Push-Location` 고 `popd` 에 별칭을 사용 합니다 `Pop-Location` .

첫 번째 명령은 현재 파일 시스템 위치를 스택에 푸시하고 PowerShell 레지스트리 공급자가 지 원하는 HKLM 드라이브로 이동 합니다.

두 번째 명령은 레지스트리 위치를 스택에 푸시하고 PowerShell 인증서 공급자가 지 원하는 위치로 이동 합니다.

마지막 두 명령은 스택에서 해당 위치를 표시합니다. 첫 번째 `popd` 명령은 레지스트리 드라이브로를 반환 하 고, 두 번째 명령은 파일 시스템 드라이브로 돌아갑니다.

## PARAMETERS

### -PassThru

위치를 나타내는 개체를 파이프라인으로 전달 합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -StackName

위치가 표시되는 위치 스택을 지정합니다. 위치 스택 이름을 입력합니다.

이 매개 변수를 사용 하지 않으면는 `Pop-Location` 현재 위치 스택의 위치를 팝 합니다. 기본적으로 현재 위치 스택은 PowerShell에서 만드는 이름 없는 기본 위치 스택입니다. 위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Set-Location` . 위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)

`Pop-Location` 현재 위치 스택이 아닌 경우 이름 없는 기본 스택의 위치를 표시할 수 없습니다.

```yaml
Type: System.String
Parameter Sets: (All)
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

### None, System.web. PathInfo

이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 위치를 나타내는 **System.web. pathinfo** 개체를 생성 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

PowerShell은 프로세스 당 여러 runspace를 지원 합니다. 각 runspace에는 자체의 _현재 디렉터리가_ 있습니다.
와는 다릅니다 `[System.Environment]::CurrentDirectory` . 이 동작은 명시적 디렉터리 경로를 제공 하지 않고 .NET Api를 호출 하거나 네이티브 응용 프로그램을 실행할 때 문제가 될 수 있습니다.

Location cmdlet이 프로세스 차원의 현재 디렉터리를 설정 했더라도 다른 runspace가 언제 든 지 변경 될 수 있으므로이를 종속 시킬 수 없습니다. 현재 runspace와 관련 된 현재 작업 디렉터리를 사용 하 여 경로 기반 작업을 수행 하려면 location cmdlet을 사용 해야 합니다.

스택은 가장 최근에 추가한 항목만 액세스할 수 있는 마지막으로 시작 된 목록입니다. 사용하는 순서대로 스택에 항목을 추가한 다음 사용을 위해 역순으로 검색합니다. PowerShell을 사용 하 여 공급자 위치를 위치 스택에 저장할 수 있습니다.

PowerShell은 이름 없는 기본 위치 스택을 만들고 여러 개의 명명 된 위치 스택을 만들 수 있습니다. 스택 이름을 지정 하지 않으면 PowerShell은 현재 위치 스택을 사용 합니다. 기본적으로 이름 없는 기본 위치는 현재 위치 스택입니다. 하지만 cmdlet을 사용 `Set-Location` 하 여 현재 위치 스택을 변경할 수 있습니다.

위치 스택을 관리 하려면 다음과 `*-Location` 같이 PowerShell cmdlet을 사용 합니다.

- 위치 스택에 위치를 추가 하려면 cmdlet을 사용 `Push-Location` 합니다.

- 위치 스택에서 위치를 가져오려면 cmdlet을 사용 `Pop-Location` 합니다.

- 현재 위치 스택의 위치를 표시 하려면 cmdlet의 **stack** 매개 변수를 사용 합니다 `Get-Location` .

- 명명 된 위치 스택의 위치를 표시 하려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Get-Location` .

- 새 위치 스택을 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 `Push-Location` 합니다. 존재 하지 않는 스택을 지정 하면에서 `Push-Location` 스택을 만듭니다.

- 위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Set-Location` .

이름 없는 기본 위치 스택은 현재 위치 스택인 경우에만 완전히 액세스할 수 있습니다.
명명 된 위치 스택을 현재 위치 스택으로 만들면 `Push-Location` 또는 cmdlet을 사용 `Pop-Location` 하 여 기본 스택에서 항목을 추가 하거나 가져올 수 없으며 cmdlet을 사용 하 여 `Get-Location` 명명 되지 않은 스택의 위치를 표시할 수 없습니다. 명명 되지 않은 스택을 현재 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 `Set-Location` 값 `$Null` 이나 빈 문자열 ()로 사용 `""` 합니다.

의 기본 제공 별칭인를 참조할 수도 있습니다 `Pop-Location` `popd` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.

`Pop-Location` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Get-Location](Get-Location.md)

[Push-Location](Push-Location.md)

[Set-Location](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
