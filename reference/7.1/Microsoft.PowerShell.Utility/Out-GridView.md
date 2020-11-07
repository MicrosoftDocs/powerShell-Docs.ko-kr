---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 840aa38ff17ceaf7dc65ca838da020c3d8c27952
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344391"
---
# Out-GridView

## 개요
별도의 창에 있는 대화형 테이블로 출력을 보냅니다.

## SYNTAX

### PassThru (기본값)

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### 연결 시도 간격

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### OutputMode

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## 설명

Cmdlet은 출력을 `Out-GridView` 대화형 테이블에 표시 하는 그리드 뷰 창에 명령의 출력을 보냅니다.

이 cmdlet은 사용자 인터페이스를 필요로 하기 때문에 Windows Server Core 또는 Windows Nano Server에서는 작동 하지 않습니다.

다음 테이블 기능을 사용하여 데이터를 조사할 수 있습니다.

- 열 숨기기, 표시 및 순서 바꾸기
- 행 정렬
- 빠른 필터
- 조건 필터 추가
- 복사 및 붙여넣기

전체 지침은이 문서의 [참고](#notes) 섹션을 참조 하세요.

> [!NOTE]
> 이 cmdlet은 PowerShell 7에서 다시 도입 되었습니다. 이 cmdlet은 Windows 데스크톱을 지 원하는 Windows 시스템 에서만 사용할 수 있습니다. 이 cmdlet의 플랫폼 간 버전은 PowerShell 갤러리 [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) 모듈을 참조 하세요.

## 예제

### 예제 1: 표 뷰로 출력 프로세스

이 예제에서는 로컬 컴퓨터에서 실행 중인 프로세스를 가져와 그리드 뷰 창으로 보냅니다.

```powershell
Get-Process | Out-GridView
```

### 예제 2: 변수를 사용 하 여 프로세스를 그리드 뷰로 출력

또한이 예제에서는 로컬 컴퓨터에서 실행 중인 프로세스를 가져와 그리드 뷰 창으로 보냅니다.

```powershell
$P = Get-Process
$P | Out-GridView
```

Cmdlet의 출력 `Get-Process` 은 변수에 저장 됩니다 `$P` . 그런 다음 `$P` 가로 파이프 됩니다 `Out-GridView` .

### 예제 3: 그리드 보기에서 선택한 속성 표시

이 예에서는 실행 중인 프로세스의 선택 된 속성을 그리드 보기에 표시 합니다.

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

의 출력은 `Get-Process` `Select-Object` **Name** , **WorkingSet** 및 **PeakWorkingSet** 속성을 선택 하기 위해로 파이프 됩니다. 다른 파이프라인 연산자는 필터링 된 개체를 cmdlet으로 보내 `Sort-Object` **WorkingSet** 속성의 값을 기준으로 내림차순으로 정렬 합니다.
그런 다음 정렬 된 결과를로 파이프 `Out-GridView` 합니다. 그런 다음에는 그리드 뷰의 기능을 사용하여 데이터를 검색, 정렬 및 필터링할 수 있습니다.

### 예 4: 출력을 변수에 저장 한 다음 그리드 보기 출력

이 예에서는 변수에 cmdlet 출력을 저장 한 다음로 보냅니다 `Out-GridView` .

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

`Get-ChildItem` 자동 변수를 사용 하 여 PowerShell 설치 디렉터리 및 해당 하위 디렉터리에 있는 모든 파일을 가져옵니다 `$PSHOME` . 명령의 괄호는 연산 순서를 설정합니다. 따라서 `Get-ChildItem` 명령의 출력이 `$A` 에 전송 되기 전에 변수에 저장 됩니다 `Out-GridView` .

### 예 5: 지정 된 컴퓨터에 대 한 프로세스를 그리드 뷰에 출력

이 예에서는 Server01 컴퓨터에서 실행 중인 프로세스를 그리드 뷰 창에 표시 합니다.

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

Examle는 `ogv` cmdlet에 대 한 별칭인를 사용 합니다 `Out-GridView` . **Title** 매개 변수는 창 제목을 지정 합니다.

### 예 6: 원격 컴퓨터의 데이터를 그리드 보기에 출력

이 예제에서는 원격 컴퓨터에서 수집 된 데이터를로 보내는 방법을 보여 줍니다 `Out-GridView` .

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

`Invoke-Command` 는 `Get-Culture` 세 대의 원격 컴퓨터에서 실행 됩니다. 결과 데이터는로 파이프 됩니다 `Out-GridView` . 원격 컴퓨터에서 실행 되는 스크립트 블록에는 명령이 포함 되지 않습니다 `Out-GridView` . 이 명령이 포함된 경우에는 명령이 각 원격 컴퓨터에서 그리드 뷰 창을 열려고 할 때 오류가 발생합니다.

### 예제 7:를 통해 여러 항목 전달 `Out-GridView`

이 예에서는 창에서 여러 프로세스를 선택할 수 있습니다 `Out-GridView` . 선택한 프로세스가 명령에 전달 되 `Export-Csv` 고 파일에 기록 됩니다 `ProcessLog.csv` .

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

의 **PassThru** 매개 변수를 `Out-GridView` 사용 하 여 파이프라인에서 여러 항목을 보낼 수 있습니다. **PassThru** 매개 변수는 **OutputMode** 매개 변수의 **Multiple** 값을 사용하는 경우와 동일한 결과를 제공합니다.

### 예 8: Windows 바로 가기를 만듭니다. `Out-GridView`

이 예에서는의 **Wait** 매개 변수를 사용 하 여 `Out-GridView` 창에 대 한 Windows 바로 가기를 만드는 방법을 보여 줍니다 `Out-GridView` .

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

이 명령줄은 Windows 바로 가기에서 사용할 수 있습니다. **Wait** 매개 변수가 없으면 창이 열리는 즉시 PowerShell이 종료 됩니다 `Out-GridView` `Out-GridView` . 그러면 창이 거의 즉시 종료 됩니다.

## PARAMETERS

### -InputObject

Cmdlet이에 대 한 입력으로 허용 하는 개체를 지정 합니다 `Out-GridView` .

**InputObject** 매개 변수를 사용 하 여 개체 컬렉션을로 보내는 경우 `Out-GridView` 는 `Out-GridView` 컬렉션을 하나의 컬렉션 개체로 처리 하 고 컬렉션을 나타내는 행 하나를 표시 합니다. 컬렉션의 각 개체를 표시 하려면 파이프라인 연산자 ()를 사용 `|` 하 여 개체를로 보냅니다 `Out-GridView` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OutputMode

대화형 창이 파이프라인을 다른 명령에 대 한 입력으로 전송 하는 항목을 지정 합니다.
기본적으로 이 cmdlet은 출력을 생성하지 않습니다. 대화형 창의 항목을 파이프라인으로 보내려면 항목을 클릭하여 선택한 다음 확인을 클릭합니다.

이 매개 변수 값이 파이프라인으로 보낼 수 있는 항목 수를 결정합니다.

- 없음  항목이 없습니다. 이것은 기본값입니다.
- 단일: 0개의 항목 또는 1개의 항목입니다. 다음 명령에서 입력 개체를 하나만 사용할 수 있는 경우 이 값을 사용합니다.
- 배수로. 0개, 1개 또는 많은 항목. 다음 명령에서 여러 개의 입력 개체를 사용할 수 있는 경우 이 값을 사용합니다. 이 값은 **Passthru** 매개 변수와 동일합니다.

```yaml
Type: Microsoft.PowerShell.Commands.OutputModeOption
Parameter Sets: OutputMode
Aliases:
Accepted values: None, Single, Multiple

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Cmdlet이 대화형 창의 항목을 다른 명령에 대 한 입력으로 파이프라인에서 보내도록 지정 합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다. 이 매개 변수는 **OutputMode** 매개 변수의 **Multiple** 값을 사용하는 경우와 동일한 결과를 제공합니다.

대화형 창의 항목을 파이프라인으로 보내려면 항목을 클릭하여 선택한 다음 확인을 클릭합니다. Shift 키나 Ctrl 키를 누른 상태에서 클릭할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PassThru
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Title

창의 제목 표시줄에 표시 되는 텍스트를 지정 합니다 `Out-GridView` . 기본적으로 제목 표시줄에는를 호출 하는 명령이 표시 됩니다 `Out-GridView` .

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

### -Wait

Cmdlet이 명령 프롬프트를 표시 하지 않고 창이 닫힐 때까지 Windows PowerShell을 닫지 않도록 지정 합니다 `Out-GridView` . 기본적으로 창이 열리면 명령 프롬프트가 반환 `Out-GridView` 됩니다.

이 기능을 사용 하면 `Out-GridView` Windows 바로 가기에서 cmdlet을 사용할 수 있습니다. `Out-GridView` **Wait** 매개 변수 없이 바로 가기에서를 사용 하면 `Out-GridView` PowerShell을 닫기 전에 창이 일시적 으로만 나타납니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Wait
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

이 cmdlet에 개체를 보낼 수 있습니다.

## 출력

### 없음

일반적으로는 `Out-GridView` 개체를 반환 하지 않습니다. **PassThru** 매개 변수를 사용 하는 경우 선택한 행을 나타내는 개체가 파이프라인으로 반환 됩니다.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

원격 명령을 사용하여 다른 컴퓨터에서 그리드 뷰 창을 열 수는 없습니다.

로 전송 하는 명령 출력은 `Out-GridView` `Format` cmdlet (예: 또는 cmdlet)을 사용 하 여 포맷할 수 없습니다 `Format-Table` `Format-Wide` . 속성을 선택 하려면 cmdlet을 사용 `Select-Object` 합니다.

원격 명령에서 역직렬화된 출력은 그리드 뷰 창에서 서식이 제대로 지정되지 않을 수 있습니다.

**바로 가기 키**`Out-GridView`

|              사용할 키:              |                                   수행할 작업:                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <kbd>탭</kbd>                          | 커서를 **필터** 상자에서 **조건 추가** 메뉴로 이동 하 여 다시 이동 합니다. |
| <kbd>서 위쪽 화살표</kbd>                      | 한 행 위로 이동 합니다. 첫 번째 데이터 행의 열 머리글로 이동 합니다.                             |
| <kbd>아래쪽 화살표</kbd>                    | 한 행 아래로 이동 합니다.                                                                           |
| <kbd>왼쪽 화살표</kbd>                    | 열 머리글 행에서 한 열 왼쪽으로 이동 합니다.                                                  |
| <kbd>오른쪽 화살표</kbd>                   | 열 머리글 행에서 한 열 오른쪽으로 이동 합니다.                                                 |
| <kbd>ContextMenuKey</kbd>               | 열 머리글 행에 열 선택 옵션을 표시 합니다.                                    |
| <kbd>Enter</kbd> 또는 <kbd>스페이스바</kbd> | 열 머리글 행에서 열 데이터를 정렬 합니다 (a-z, A-z).                                    |

**그리드 뷰 창 기능을 사용 하는 방법**

**열을 숨기거나 표시하려면:**

1. 열 머리글을 마우스 오른쪽 단추로 클릭 하 고 **열 선택** 을 클릭 합니다.
2. **열 선택** 대화 상자에서 화살표 키를 사용 하 여 선택한 열 사이에 있는 열을 사용 가능한 열 상자로 이동 합니다. **열 선택** 상자의 열만 그리드 뷰 창에 표시 됩니다.

**열의 순서를 바꾸려면:**

열을 원하는 위치로 끌어서 놓을 수 있습니다. 또는 다음 단계를 사용 합니다.

1. 열 머리글을 마우스 오른쪽 단추로 클릭 하 고 **열 선택** 을 클릭 합니다.
2. **열 선택** 대화 상자에서 **위로 이동** 및 **아래로 이동** 단추를 사용 하 여 열을 다시 정렬 합니다. 목록 맨 위에 있는 열은 그리드 뷰 창의 목록 맨 아래에 있는 열의 왼쪽에 나타납니다.

**테이블 데이터를 정렬하는 방법**

- 데이터를 정렬하려면 열 머리글을 클릭합니다.
- 정렬 순서를 변경 하려면 열 머리글을 다시 클릭 합니다. 같은 머리글을 클릭할 때마다 정렬 순서가 오름차순과 내림차순 간에 전환합니다. 현재 순서는 열 머리글의 삼각형으로 표시됩니다.

**테이블 데이터를 정렬하는 방법**

- 행을 선택 하려면 행을 선택 하거나 위쪽 또는 아래쪽 화살표를 사용 하 여 행으로 이동 합니다.
- 머리글 행을 제외 하 고 모든 행을 선택 하려면 <kbd>ctrl</kbd> + <kbd>A</kbd>를 누릅니다.
- 연속 된 행을 선택 하려면 <kbd>shift</kbd> 키를 누른 상태에서 행을 클릭 하거나 화살표 키를 사용 합니다.
- 비연속적인 행을 선택 하려면 Ctrl 키를 누른 <kbd>채</kbd> 클릭 하 여 선택 영역에 행을 추가 합니다.
- 열이나 전체 열 머리글 행은 선택할 수 없습니다.

**행을 복사하는 방법**

- 테이블에서 하나 이상의 행을 복사 하려면 행을 선택 하 고 CTRL + C를 누릅니다.

  복사한 데이터는 원하는 텍스트 또는 스프레드시트 프로그램에 붙여 넣을 수 있습니다. 열 또는 행의 일부나 열 머리글 행은 복사할 수 없습니다.

**테이블에서 검색 하는 방법 (빠른 필터)**

필터 상자를 사용 하 여 테이블에서 데이터를 검색 합니다. 상자에 입력하면 입력한 텍스트가 포함된 항목만 테이블에 표시됩니다.

- 텍스트를 검색 합니다. 테이블에서 텍스트를 검색 하려면 필터 상자에 찾을 텍스트를 입력 합니다.
- 여러 단어를 검색 합니다. 테이블에서 여러 단어를 검색하려면 단어를 공백으로 구분하여 입력합니다. `Out-GridView` 모든 단어 (논리적 AND)를 포함 하는 행을 표시 합니다.
- 리터럴 구를 검색 합니다. 공백이나 특수 문자가 포함된 구를 검색하려면 구를 따옴표로 묶어 입력합니다. `Out-GridView` 구와 정확히 일치 하는 항목을 포함 하는 행을 표시 합니다.
- 열에서 검색 합니다. 하나 이상의 열에서 텍스트를 검색하려면 다음 형식을 사용합니다.

  `<column>:<text> [<column>:<text>] ...`

  예를 들어 **DisplayName** 열에서 "Net"을 찾으려면 **필터** 상자에 다음을 입력 합니다.

  `displayname:net`

  **DisplayName** 및 **Name** 열에서 "Net"이 포함 된 행을 찾으려면 **필터** 상자에 다음을 입력 합니다.

  `displayname:net name:net`

- 검색을 해제 합니다. 전체 테이블을 다시 표시 하려면 **필터** 상자의 오른쪽 위 모서리에 있는 빨간색 X 단추를 클릭 하거나 **필터** 상자에서 텍스트를 삭제 합니다.

**조건을 사용하여 테이블 필터링**

규칙 또는 조건을 사용 하 여 테이블에 표시 되는 항목을 결정할 수 있습니다. 항목은 사용자가 설정한 모든 조건을 충족 하는 경우에만 표시 됩니다. 사용 가능한 조건은 그리드 뷰 창에 표시되는 개체의 속성 및 이러한 속성의 .NET Framework 유형에 따라 결정됩니다.

각 조건의 형식은 다음과 같습니다.

`<column> <operator> <value>`

다른 속성에 대 한 조건은 **및** 에서 연결 됩니다. 동일한 속성의 조건은 **또는** 로 연결 됩니다. 논리적 연결자는 변경할 수 없습니다.

조건은 표시에만 영향을 주고 테이블의 항목을 실제로 삭제하지는 않습니다.

**조건을 추가하는 방법**

1. **조건 추가** 메뉴 단추를 표시 하려면 창의 오른쪽 위 모서리에서 확장 화살표를 클릭 합니다.
2. **조건 추가** 메뉴 단추를 클릭 합니다.
3. 열(속성)을 클릭하여 선택합니다. 속성은 하나 이상 선택할 수 있습니다.
4. 속성 선택을 마쳤으면 **추가** 단추를 클릭 합니다.
5. 추가를 취소 하려면 **취소** 를 클릭 합니다.
6. 조건을 더 추가 하려면 **조건 추가** 단추를 다시 클릭 합니다.

**조건을 편집하는 방법**

- 연산자를 변경 하려면 파란색 연산자 값을 클릭 한 다음 드롭다운 목록에서 다른 연산자를 선택 합니다.
- 값을 입력 하거나 변경 하려면 값 상자에 값을 입력 합니다. 잘못된 값을 입력하면 원형 X 아이콘이 표시됩니다. 값을 제거하려면 변경하세요.
- **또는** 문을 만들려면 동일한 속성을 사용 하 여 조건을 추가 합니다.

**조건을 삭제하는 방법**

- 선택한 조건을 삭제 하려면 각 조건 옆에 있는 빨간색 X를 클릭 합니다.
- 모든 조건을 삭제 하려면 **모두 지우기** 단추를 클릭 합니다.

## 관련 링크

[Out-File](Out-File.md)

[Out-Printer](Out-Printer.md)

[Out-String](Out-String.md)

