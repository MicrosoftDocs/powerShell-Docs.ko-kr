---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: d3ff6fe599873edafdda04b3fe17ae01d88c049d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213673"
---
# Show-Command

## 개요
그래픽 창에 PowerShell 명령 정보를 표시 합니다.

## SYNTAX

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## 설명

`Show-Command`Cmdlet을 사용 하 여 명령 창에서 PowerShell 명령을 만들 수 있습니다. 명령 창의 기능을 사용하여 명령을 실행하거나 해당 명령이 반환되도록 설정할 수 있습니다.

`Show-Command` 는 매우 유용한 교육 및 학습 도구입니다. `Show-Command` cmdlet, 함수, 워크플로 및 CIM 명령을 비롯 한 모든 명령 유형에 대해 작동 합니다.

매개 변수가 없으면 `Show-Command` 설치 된 모든 모듈에서 사용할 수 있는 모든 명령을 나열 하는 명령 창을 표시 합니다. 모듈의 명령을 찾으려면 모듈 드롭다운 목록에서 원하는 모듈을 선택합니다. 명령을 선택하려면 명령 이름을 클릭합니다.

명령 창을 사용 하려면 이름을 사용 하거나 **명령 목록에서** 명령 이름을 클릭 하 여 명령을 선택 합니다. 각 매개 변수 집합은 별도의 탭에 표시 됩니다. 별표는 필수 매개 변수를 표시 합니다. 매개 변수 값을 입력하려면 텍스트 상자에 값을 입력하거나 드롭다운 상자에서 값을 선택합니다. 스위치 매개 변수를 추가하려면 매개 변수를 확인란을 클릭하여 선택합니다.

준비되면 **Copy** 를 클릭하여 생성된 명령을 클립보드에 복사하거나 **Run** 을 클릭하여 명령을 실행합니다. **PassThru** 매개 변수를 사용 하 여 PowerShell 콘솔과 같은 호스트 프로그램에 명령을 반환할 수도 있습니다. 명령 선택을 취소 하 고 모든 명령을 표시 하는 뷰로 돌아가려면 Ctrl 키를 누르고 선택한 명령을 클릭 합니다.

PowerShell ISE (통합 스크립팅 환경)에서는 `Show-Command` 기본적으로 창의 변형이 표시 됩니다. 이 명령 창을 사용 하는 방법에 대 한 자세한 내용은 PowerShell ISE 도움말 항목을 참조 하세요.

이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.

이 cmdlet은 사용자 인터페이스를 필요로 하기 때문에 Windows Server Core 또는 Windows Nano Server에서는 작동 하지 않습니다. 이 cmdlet은 Windows 데스크톱을 지 원하는 Windows 시스템 에서만 사용할 수 있습니다.

## 예제

### 예제 1: 명령 창 열기

이 예에서는 창의 기본 뷰를 표시 합니다 `Show-Command` . **명령** 창에는 컴퓨터에 설치 된 모든 모듈의 모든 명령 목록이 표시 됩니다.

```powershell
Show-Command
```

### 예제 2: 명령 창에서 cmdlet 열기

이 예에서는 `Invoke-Command` **명령** 창에 cmdlet을 표시 합니다. 이 표시를 사용 하 여 명령을 실행할 수 있습니다 `Invoke-Command` .

```powershell
Show-Command -Name "Invoke-Command"
```

### 예제 3: 지정 된 매개 변수를 사용 하 여 cmdlet 열기

이 명령은 `Show-Command` cmdlet에 대 한 창을 엽니다 `Connect-PSSession` .

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

**Height** 및 **Width** 매개 변수는 명령 창의 차원을 지정 합니다. **Errorpopup** 매개 변수는 오류 명령 창을 표시 합니다.

**실행** 을 클릭 하면 명령줄 `Connect-PSSession` 에서 명령을 입력 하는 것과 마찬가지로 명령이 실행 됩니다 `Connect-PSSession` .

### 예제 4: cmdlet에 대 한 새로운 기본 매개 변수 값 지정

이 예에서는 `$PSDefaultParameterValues` 자동 변수를 사용 하 여 cmdlet의 **Height** , **Width** 및 **errorpopup** 매개 변수에 대 한 새 기본값을 설정 합니다 `Show-Command` .

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

이제 명령을 실행 하면 `Show-Command` 새 기본값이 자동으로 적용 됩니다. 모든 PowerShell 세션에서 이러한 기본값을 사용 하려면 `$PSDefaultParameterValues` powershell 프로필에 변수를 추가 합니다. 자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) 및 [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md)를 참조 하세요.

### 예 5: 표 뷰로 출력 보내기

이 명령은 및 cmdlet을 함께 사용 하는 방법을 보여 줍니다 `Show-Command` `Out-GridView` .

```powershell
Show-Command Get-ChildItem | Out-GridView
```

이 명령은 cmdlet을 사용 하 여 `Show-Command` cmdlet에 대 한 명령 창을 엽니다 `Get-ChildItem` .
**실행** 단추를 클릭 하면 `Get-ChildItem` 명령이 실행 되 고 출력이 생성 됩니다. 파이프라인 연산자 (|)가 `Get-ChildItem` cmdlet으로 명령의 출력을 보냅니다 `Out-GridView` .이 cmdlet은 `Get-ChildItem` 대화형 창에 출력을 표시 합니다.

### 예제 6: 명령 창에서 만든 명령 표시

이 예에서는 창에서 만든 명령을 보여 줍니다 `Show-Command` . 이 명령은 **PassThru** 매개 변수를 사용 하 여 결과를 문자열로 반환 합니다 `Show-Command` .

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

예를 들어 `Show-Command` `Get-EventLog` Windows PowerShell 이벤트 로그에 있는 5 개의 최신 이벤트를 가져오는 명령을 만든 다음 **확인** 을 클릭 하면이 명령은 위에 표시 된 출력을 반환 합니다. 명령 문자열을 보면 PowerShell을 배우는 데 도움이 됩니다.

### 예 7: 변수에 명령 저장

이 예에서는 cmdlet의 **PassThru** 매개 변수를 사용할 때 가져오는 명령 문자열을 실행 하는 방법을 보여 줍니다 `Show-Command` . 이 전략을 사용하면 명령을 보고 사용할 수 있습니다.

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

첫 번째 명령은 cmdlet의 **PassThru** 매개 변수를 사용 하 여 `Show-Command` 명령 결과를 변수에 저장 합니다 `$C` . 이 경우 `Show-Command` `Get-EventLog` Windows PowerShell 이벤트 로그에 있는 5 개의 최신 이벤트를 가져오는 명령을 만드는 데 창을 사용 합니다. **확인** 을 클릭 하면에서 `Show-Command` 변수에 저장 되는 명령 문자열을 반환 `$C` 합니다.

### 예 8: 명령의 출력을 변수에 저장

이 예에서는 **Errorpopup** 매개 변수를 사용 하 여 명령의 출력을 변수에 저장 합니다.

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

창에서 오류를 표시할 수 있을 뿐 아니라 **ErrorPopup** 은 새 명령을 만들지 않고 명령 출력을 현재 명령에 반환합니다. 이 명령을 실행 하면 `Show-Command` 창이 열립니다. 창 기능을 사용하여 매개 변수 값을 설정할 수 있습니다. 명령을 실행 하려면 창에서 **실행** 단추를 클릭 합니다 `Show-Command` .

## PARAMETERS

### -ErrorPopup

Cmdlet이 명령줄에 표시 하는 것 외에도 팝업 창에 오류를 표시 함을 나타냅니다. 기본적으로 창에서 실행 되는 명령을 실행 하면 오류가 발생 하는 경우 `Show-Command` 명령줄 에서만 오류가 표시 됩니다.

또한 창에서 **실행** 단추를 사용 하 여 명령을 실행 하는 경우 `Show-Command` **errorpopup** 매개 변수는 명령을 실행 하 고 해당 출력을 새 명령으로 반환 하는 대신 명령 결과를 현재 명령으로 반환 합니다. 이 기능을 사용하여 명령 결과를 변수에 저장할 수 있습니다.

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

### -높이

`Show-Command`창의 높이 (픽셀)를 지정 합니다. 300과 화면 해상도의 픽셀 수 사이의 값을 입력합니다. 값이 너무 커서 화면에 명령 창을 표시할 수 없는 경우에서 오류를 `Show-Command` 생성 합니다. 기본 높이는 600픽셀입니다. `Show-Command` **Name** 매개 변수를 포함 하는 명령의 경우 기본 높이는 300 픽셀입니다.

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

지정된 명령에 대한 명령 창을 표시합니다. 한 명령의 이름 (예: cmdlet, 함수 또는 CIM 명령)을 입력 합니다. 이 매개 변수를 생략 하면는 `Show-Command` 컴퓨터에 설치 된 모든 모듈의 모든 PowerShell 명령을 나열 하는 명령 창을 표시 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoCommonParameter

이 cmdlet이 명령 표시의 일반 매개 변수 섹션을 생략 함을 나타냅니다. 기본적으로 일반 매개 변수는 명령 창의 맨 아래에 있는 확장 가능한 섹션에 나타납니다.

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

### -PassThru

작업 중인 항목을 나타내는 개체를 반환합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다. 명령 문자열을 실행 하려면 명령 프롬프트에서 해당 문자열을 복사 하 여 붙여넣고 변수에 저장 한 다음 cmdlet을 사용 `Invoke-Expression` 하 여 변수에 문자열을 실행 합니다.

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

### -너비

`Show-Command`창의 너비 (픽셀)를 지정 합니다. 300과 화면 해상도의 픽셀 수 사이의 값을 입력합니다. 값이 너무 커서 화면에 명령 창을 표시할 수 없는 경우에서 오류를 `Show-Command` 생성 합니다. 기본 높이는 300픽셀입니다.

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

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

입력을로 파이프 할 수 없습니다 `Show-Command` .

## 출력

### None, System.string, System.object

**PassThru** 매개 변수를 사용 하는 경우는 `Show-Command` 명령 문자열을 반환 합니다. **Errorpopup** 매개 변수를 사용 하는 경우 `Show-Command` 명령 출력 (모든 개체)을 반환 합니다. 그렇지 않으면에서 `Show-Command` 출력을 생성 하지 않습니다.

## 참고

`Show-Command` 는 원격 세션에서 작동 하지 않습니다.

## 관련 링크
