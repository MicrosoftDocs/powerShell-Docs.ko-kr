---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: 713a25bd09b7abc63a0f4974eb905a88c1d4c0e1
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2020
ms.locfileid: "93219065"
---
# Start-Process

## 개요
로컬 컴퓨터에서 하나 이상의 프로세스를 시작합니다.

## SYNTAX

### Default (기본값)

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### UseShellExecute

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`Start-Process`Cmdlet은 로컬 컴퓨터에서 하나 이상의 프로세스를 시작 합니다. 기본적으로는 `Start-Process` 현재 프로세스에 정의 된 모든 환경 변수를 상속 하는 새 프로세스를 만듭니다.

프로세스에서 실행되는 프로그램을 지정하려면 실행 파일 또는 스크립트 파일을 입력하거나 컴퓨터의 프로그램을 사용하여 열 수 있는 파일을 입력합니다. 실행 파일이 아닌 파일을 지정 하는 경우는 `Start-Process` cmdlet과 유사 하 게 파일과 연결 된 프로그램을 시작 합니다 `Invoke-Item` .

의 매개 변수를 사용 `Start-Process` 하 여 사용자 프로필을 로드 하거나 새 창에서 프로세스를 시작 하거나 대체 자격 증명을 사용 하는 등의 옵션을 지정할 수 있습니다.

## 예제

### 예제 1: 기본값을 사용 하는 프로세스 시작

이 예에서는 현재 폴더에 있는 파일을 사용 하는 프로세스를 시작 `Sort.exe` 합니다. 이 명령은 기본 창 스타일, 작업 폴더 및 자격 증명을 비롯 한 모든 기본값을 사용 합니다.

```powershell
Start-Process -FilePath "sort.exe"
```

### 예제 2: 텍스트 파일 인쇄

이 예제에서는 파일을 인쇄 하는 프로세스를 시작 `C:\PS-Test\MyFile.txt` 합니다.

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### 예 3: 새 파일에 항목을 정렬 하는 프로세스 시작

이 예제에서는 파일의 항목을 정렬 하 `Testsort.txt` 고 정렬 된 항목을 파일에 반환 하는 프로세스를 시작 `Sorted.txt` 합니다. 모든 오류는 파일에 기록 됩니다 `SortError.txt` .

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

**UseNewEnvironment** 매개 변수는 프로세스가 고유한 환경 변수를 사용 하 여 실행 되도록 지정 합니다.

### 예제 4: 최대화 된 창에서 프로세스 시작

이 예제에서는 프로세스를 시작 `Notepad.exe` 합니다. 창을 최대화하고 프로세스가 완료될 때까지 창을 유지합니다.

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### 예 5: 관리자 권한으로 PowerShell 시작

이 예에서는 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### 예제 6: 다른 동사를 사용 하 여 프로세스 시작

이 예제에서는 프로세스를 시작할 때 사용할 수 있는 동사를 찾는 방법을 보여 줍니다. 사용 가능한 동사는 프로세스에서 실행 되는 파일의 파일 이름 확장명에 따라 결정 됩니다.

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

이 예에서는 `New-Object` 를 사용 하 여 PowerShell 프로세스에서 실행 되는 **PowerShell.exe** 에 대 한 **ProcessStartInfo** 개체를 만듭니다. **ProcessStartInfo** 개체의 **Verbs** 속성은에서 **Open** 및 **RunAs** 동사를 사용 `PowerShell.exe` 하거나 파일을 실행 하는 모든 프로세스를 사용할 수 있음을 보여 줍니다 `.exe` .

### 예 7: 프로세스에 인수 지정

두 명령은 모두 `dir` 폴더에 대해 명령을 실행 하 여 Windows 명령 인터프리터를 시작 합니다 `Program Files` . 이 foldername에 공백이 포함 되어 있으므로 값은 이스케이프 된 따옴표로 묶여 있어야 합니다.
첫 번째 명령은 문자열을 **Argumentlist** 로 지정 합니다. 두 번째 명령은 문자열 배열입니다.

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

## PARAMETERS

### -ArgumentList

이 cmdlet이 프로세스를 시작할 때 사용할 매개 변수 또는 매개 변수 값을 지정 합니다. 인수를 공백으로 구분 하는 단일 문자열이 나 쉼표로 구분 된 문자열 배열로 사용할 수 있습니다.

매개 변수 또는 매개 변수 값에 공백이 있는 경우 이스케이프 된 큰따옴표로 묶어야 합니다. 자세한 내용은 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)를 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. 기본적으로 이 cmdlet은 현재 사용자의 자격 증명을 사용합니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Default
Aliases: RunAs

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

프로세스에서 실행 되는 프로그램의 선택적 경로와 파일 이름을 지정 합니다. 컴퓨터의 프로그램과 연결 된 실행 파일 또는 문서 (예: 또는 파일)의 이름을 입력 합니다 `.txt` `.doc` . 이 매개 변수는 필수적 요소입니다.

파일 이름만 지정 하는 경우 **WorkingDirectory** 매개 변수를 사용 하 여 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Processmodel.loaduserprofile

이 cmdlet은 `HKEY_USERS` 현재 사용자의 레지스트리 키에 저장 된 Windows 사용자 프로필을 로드 함을 나타냅니다. Windows 이외의 시스템에는이 매개 변수가 적용 되지 않습니다.

이 매개 변수는 PowerShell 프로필에 영향을 주지 않습니다. 자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: Lup

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewWindow

현재 콘솔 창에서 새 프로세스를 시작합니다. 기본적으로 Windows에서 PowerShell은 새 창을 엽니다. 비 Windows 시스템에서는 새 터미널 창이 표시 되지 않습니다.

동일한 명령에서 **Nonewwindow** 및 **system.windows.window.windowstyle** 매개 변수를 사용할 수 없습니다.

Windows 이외의 시스템에는이 매개 변수가 적용 되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: nnw

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

cmdlet이 시작한 각 프로세스에 대한 프로세스 개체를 반환합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -RedirectStandardError

파일을 지정 합니다. 이 cmdlet은 프로세스에서 생성 된 모든 오류를 지정한 파일로 보냅니다.
경로 및 파일 이름을 입력 합니다. 기본적으로 오류는 콘솔에 표시됩니다.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardInput

파일을 지정 합니다. 이 cmdlet은 지정 된 파일에서 입력을 읽습니다. 입력 파일의 경로와 파일 이름을 입력 합니다. 기본적으로 프로세스는 키보드에서 입력을 가져옵니다.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardOutput

파일을 지정 합니다. 이 cmdlet은 프로세스에서 생성 된 출력을 지정한 파일로 보냅니다.
경로 및 파일 이름을 입력 합니다. 기본적으로 출력은 콘솔에 표시됩니다.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseNewEnvironment

이 cmdlet이 프로세스에 대해 지정 된 새 환경 변수를 사용 함을 나타냅니다. 기본적으로 시작 된 프로세스는 부모 프로세스에서 상속 된 환경 변수를 사용 하 여 실행 됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -동사

이 cmdlet이 프로세스를 시작할 때 사용할 동사를 지정 합니다. 사용 가능한 동사는 프로세스에서 실행 되는 파일의 파일 이름 확장명에 따라 결정 됩니다.

다음 표에서는 몇 가지 일반적인 프로세스 파일 형식에 대한 동사를 보여 줍니다.

| 파일 형식 |                동사                |
| --------- | ----------------------------------- |
| .cmd      | 편집, 열기, 인쇄, 실행, RunAsUser |
| .exe      | Open, RunAs, RunAsUser              |
| .txt      | 열기, 인쇄, PrintTo                |
| .wav      | 열기, 재생                          |

프로세스에서 실행 되는 파일에 사용할 수 있는 동사를 찾으려면 cmdlet을 사용 `New-Object` 하 여 파일에 대 한 **ProcessStartInfo** 개체를 만듭니다. 사용 가능한 동사는 **ProcessStartInfo** 개체의 **verbs** 속성에 있습니다. 자세한 내용은 예제를 참조하세요.

Windows 이외의 시스템에는이 매개 변수가 적용 되지 않습니다.

```yaml
Type: System.String
Parameter Sets: UseShellExecute
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait

이 cmdlet은 지정 된 프로세스와 해당 하위 항목이 완료 될 때까지 대기한 후 추가 입력을 수락 함을 나타냅니다. 이 매개 변수는 프로세스가 완료 될 때까지 명령 프롬프트를 표시 하지 않거나 창을 유지 합니다.

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

### -WindowStyle

새 프로세스에 사용되는 창의 상태를 지정합니다. 이 매개 변수에 허용 되는 값은 **Normal** , **Hidden** , **최소화** 및 **최대화** 입니다. 기본값은 **Normal** 입니다.

동일한 명령에서 **system.windows.window.windowstyle** 및 **nonewwindow** 매개 변수를 사용할 수 없습니다.

Windows 이외의 시스템에는이 매개 변수가 적용 되지 않습니다.

```yaml
Type: System.Diagnostics.ProcessWindowStyle
Parameter Sets: (All)
Aliases:
Accepted values: Normal, Hidden, Minimized, Maximized

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkingDirectory

새 프로세스를 시작할 위치를 지정 합니다. 기본값은 시작 되는 실행 파일 또는 문서의 위치입니다. 제공 된 경로는 리터럴 경로로 처리 됩니다. 와일드카드는 지원되지 않습니다. `'`경로 이름에 와일드 카드로 해석 될 문자가 포함 된 경우 경로를 작은따옴표 ()로 묶어야 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### 없음, 시스템 진단 프로세스

이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 **system.object** 개체를 생성 합니다. 그러지 않으면 아무 출력도 반환하지 않습니다.

## 참고

- 이 cmdlet은 **system.web. Process** 클래스의 **Start** 메서드를 사용 하 여 구현 됩니다. 이 메서드에 대 한 자세한 내용은 [Process. Start 메서드](/dotnet/api/system.diagnostics.process.start#overloads)를 참조 하세요.

- Windows에서 **UseNewEnvironment** 를 사용 하는 경우 새 프로세스가 **컴퓨터** 범위에 대해 정의 된 기본 환경 변수만 포함 하는 것으로 시작 됩니다. 이를 통해 `$env:USERNAME` 가 **시스템** 으로 설정 된다는 측면에 영향을 줍니다. **사용자** 범위의 변수가 포함 되지 않습니다.

- Windows에서의 가장 일반적인 사용 사례는 `Start-Process` **Wait** 매개 변수를 사용 하 여 새 프로세스가 종료 될 때까지 진행을 차단 하는 것입니다. 비 Windows 시스템에서는 명령줄 응용 프로그램의 기본 동작이와 동일 하기 때문에이 작업이 거의 필요 하지 않습니다 `Start-Process -Wait` .

- `Start-Process`Windows 이외의 시스템에서를 사용 하는 경우 새 터미널 창이 표시 되지 않습니다.

## 관련 링크

[about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Service](Start-Service.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
