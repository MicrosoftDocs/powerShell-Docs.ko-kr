---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: abc40f3ae388a915c9df42d0c2df24f848e45e73
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/06/2020
ms.locfileid: "93219185"
---
# Push-Location

## 개요
현재 위치를 위치 스택의 맨 위에 추가합니다.

## SYNTAX

### Path (기본값)

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

## 설명

`Push-Location`Cmdlet은 현재 위치를 위치 스택에 추가 ("푸시") 합니다. 경로를 지정 하는 경우는 현재 위치를 `Push-Location` 위치 스택에 푸시한 다음 현재 위치를 경로에 지정 된 위치로 변경 합니다. Cmdlet을 사용 `Pop-Location` 하 여 위치 스택에서 위치를 가져올 수 있습니다.

기본적으로이 cmdlet은 현재 위치를 `Push-Location` 현재 위치 스택에 푸시한 다음 **stackname** 매개 변수를 사용 하 여 대체 위치 스택을 지정할 수 있습니다. 스택이 없으면에서 `Push-Location` 해당 스택을 만듭니다.

위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)

## 예제

### 예 1

이 예제에서는 현재 위치를 기본 위치 스택에 푸시한 다음 위치를로 변경 합니다 `C:\Windows` .

```
PS C:\> Push-Location C:\Windows
```

### 예제 2

이 예제에서는 현재 위치를 RegFunction 스택에 푸시하고 현재 위치를 `HKLM:\Software\Policies` 위치로 변경 합니다.

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

모든 PowerShell 드라이브 (PSDrive)에서 Location cmdlet을 사용할 수 있습니다.

### 예제 3

이 명령은 현재 위치를 기본 스택에 밀어 넣지만 위치를 변경하지는 않습니다.

```
PS C:\> Push-Location
```

### 예제 4-명명 된 스택 만들기 및 사용

이 명령은 명명된 위치 스택을 만들고 사용하는 방법을 보여 줍니다.

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

첫 번째 명령은 현재 위치를 Stack2 라는 새 스택으로 푸시하고, 현재 위치를 물결표 기호 ()로 표시 되는 홈 디렉터리로 변경 합니다 .이는 FileSystem 기호 ()로 표시 `~` 됩니다 .이는 FileSystem 기호 ()를 사용 하는 경우와 동일 합니다 `$HOME` `$env:USERPROFILE` .

Stack2가 세션에 아직 없는 경우에서 `Push-Location` 만듭니다. 두 번째 명령은 cmdlet을 사용 하 여 `Pop-Location` Stack2 stack에서 원래 위치 ()를 팝 합니다 `C:\` . **Stackname** 매개 변수를 사용 하지 않으면는 `Pop-Location` 명명 되지 않은 기본 스택의 위치를 팝 합니다.

위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)

## PARAMETERS

### -LiteralPath

새 위치의 경로를 지정합니다. **Path** 매개 변수와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

위치를 나타내는 개체를 파이프라인으로 전달합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -Path

현재 위치를 스택의 맨 위에 추가한(밀어 넣은) 다음 사용자 위치를 이 경로에서 지정하는 위치로 변경합니다. 이 cmdlet을 지원하는 공급자의 위치 경로를 입력합니다. 와일드카드가 지원됩니다. 매개 변수 이름은 선택 사항입니다.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -StackName

현재 위치가 추가되는 위치 스택을 지정합니다. 위치 스택 이름을 입력합니다.
스택이 없으면에서 `Push-Location` 해당 스택을 만듭니다.

이 매개 변수를 사용 하지 않으면 `Push-Location` 현재 위치 스택에 위치를 추가 합니다. 기본적으로 현재 위치 스택은 PowerShell에서 만드는 이름 없는 기본 위치 스택입니다.
위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Set-Location` . 위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)

> [!NOTE]
> `Push-Location` 현재 위치 스택이 아닌 경우 이름 없는 기본 스택에 위치를 추가할 수 없습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default stack
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseTransaction

활성 트랜잭션에 명령을 포함합니다. 이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다. 자세한 내용은 [about_Transactions](../Microsoft.PowerShell.Core/About/about_transactions.md)를 참조하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

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

경로 (리터럴 경로 아님)가 포함 된 문자열을로 파이프 할 수 있습니다 `Push-Location` .

## 출력

### 없음 또는 System.web. PathInfo

**PassThru** 매개 변수를 사용 하는 경우는 `Push-Location` 위치를 나타내는 **system.web. pathinfo** 개체를 생성 합니다. 그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.

## 참고

PowerShell은 프로세스 당 여러 runspace를 지원 합니다. 각 runspace에는 자체의 _현재 디렉터리가_ 있습니다.
와는 다릅니다 `[System.Environment]::CurrentDirectory` . 이 동작은 명시적 디렉터리 경로를 제공 하지 않고 .NET Api를 호출 하거나 네이티브 응용 프로그램을 실행할 때 문제가 될 수 있습니다.

Location cmdlet이 프로세스 차원의 현재 디렉터리를 설정 했더라도 다른 runspace가 언제 든 지 변경 될 수 있으므로이를 종속 시킬 수 없습니다. 현재 runspace와 관련 된 현재 작업 디렉터리를 사용 하 여 경로 기반 작업을 수행 하려면 location cmdlet을 사용 해야 합니다.

스택은 가장 최근에 추가 된 항목만 액세스할 수 있는 마지막으로 시작 된 목록입니다.
사용하는 순서대로 스택에 항목을 추가한 다음 사용을 위해 역순으로 검색합니다. PowerShell을 사용 하 여 공급자 위치를 위치 스택에 저장할 수 있습니다.

PowerShell은 이름 없는 기본 위치 스택을 만들고 여러 개의 명명 된 위치 스택을 만들 수 있습니다. 스택 이름을 지정 하지 않으면 PowerShell은 현재 위치 스택을 사용 합니다. 기본적으로 이름 없는 기본 위치는 현재 위치 스택입니다. 하지만 cmdlet을 사용 `Set-Location` 하 여 현재 위치 스택을 변경할 수 있습니다.

위치 스택을 관리 하려면 다음과 같이 PowerShell 위치 cmdlet을 사용 합니다.

- 위치 스택에 위치를 추가 하려면 cmdlet을 사용 `Push-Location` 합니다.

- 위치 스택에서 위치를 가져오려면 cmdlet을 사용 `Pop-Location` 합니다.

- 현재 위치 스택의 위치를 표시 하려면 cmdlet의 **stack** 매개 변수를 사용 합니다 `Get-Location` .

- 명명 된 위치 스택의 위치를 표시 하려면 cmdlet의 **Stackname** 매개 변수를 사용 합니다 `Get-Location` .

- 새 위치 스택을 만들려면 cmdlet의 StackName 매개 변수를 사용 `Push-Location` 합니다. 존재 하지 않는 스택을 지정 하면에서 `Push-Location` 스택을 만듭니다.

- 위치 스택을 현재 위치 스택으로 만들려면 cmdlet의 StackName 매개 변수를 사용 합니다 `Set-Location` .

이름 없는 기본 위치 스택은 현재 위치 스택인 경우에만 완전히 액세스할 수 있습니다.
명명 된 위치 스택을 현재 위치 스택으로 만들면 `Push-Location` 또는 cmdlet을 사용 `Pop-Location` 하 여 기본 스택에서 항목을 추가 하거나 가져올 수 없으며 cmdlet을 사용 하 여 `Get-Location` 명명 되지 않은 스택의 위치를 표시할 수 없습니다. 명명 되지 않은 스택을 현재 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 `Set-Location` 값 `$null` 이나 빈 문자열 ()로 사용 `""` 합니다.

의 기본 제공 별칭인를 참조할 수도 있습니다 `Push-Location` `pushd` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.

`Push-Location`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Get-Location](Get-Location.md)

[Pop-Location](Pop-Location.md)

[Set-Location](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
