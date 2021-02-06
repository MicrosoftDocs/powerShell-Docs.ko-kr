---
description: PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSReadLine 정보
ms.openlocfilehash: 4836abfec465ba7cdfb6800c1e60104fba19ce08
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "99600623"
---
# <a name="psreadline"></a>PSReadLine

## <a name="about_psreadline"></a>about_PSReadLine

## <a name="short-description"></a>간단한 설명

PSReadLine은 PowerShell 콘솔에서 향상 된 명령줄 편집 환경을 제공 합니다.

## <a name="long-description"></a>자세한 설명

PSReadLine 2.2은 PowerShell 콘솔에 대 한 강력한 명령줄 편집 환경을 제공 합니다. 이 콘솔은 다음과 같은 기능을 제공합니다.

- 명령줄의 구문 색 지정
- 구문 오류를 시각적으로 표시 합니다.
- 더 나은 여러 줄 환경 (편집 및 기록 모두)
- 사용자 지정 가능한 키 바인딩
- Cmd 및 Emacs 모드
- 많은 구성 옵션
- Bash 스타일 완성 (Cmd 모드에서는 선택 사항, Emacs 모드에서는 기본값)
- Emacs yank/kill
- PowerShell 토큰 기반 "word" 이동 및 중지
- 예측 IntelliSense

PSReadLine 2.2.0는 두 가지 새로운 예측 IntelliSense 기능을 추가 했습니다.

- 새를 선택할 수 있도록 **PredictionViewStyle** 매개 변수를 추가 했습니다 `ListView` .
- PSReadLine을 `CommandPrediction` PS 7.1에 도입 된 api에 연결 하 여 사용자가 사용자 지정 원본에서 제안을 렌더링할 수 있는 예측 모듈을 가져올 수 있도록 합니다.

PSReadLine에는 PowerShell 3.0 이상이 필요 합니다. PSReadLine은 기본 콘솔 호스트, Visual Studio Code 및 창 터미널에서 작동 합니다. PowerShell ISE에서는 작동 하지 않습니다.

PSReadLine 2.2.0는 PowerShell 7.2과 함께 제공 되며, 지원 되는 모든 버전의 PowerShell에서 지원 됩니다. PowerShell 갤러리에서 설치할 수 있습니다.
지원 되는 버전의 PowerShell에서 PSReadLine 2.2.0을 설치 하려면 다음 명령을 실행 합니다.

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> PowerShell 7.0부터 PowerShell은 화면 판독기 프로그램이 검색 된 경우 Windows에서 PSReadLine 자동 로드를 건너뜁니다. 현재 PSReadLine은 화면 판독기에서 제대로 작동 하지 않습니다. Windows에서 PowerShell 7.0의 기본 렌더링 및 형식이 제대로 작동 합니다. 필요한 경우 모듈을 수동으로 로드할 수 있습니다.

## <a name="predictive-intellisense"></a>예측 IntelliSense

예측 IntelliSense는 사용자가 명령을 성공적으로 완료 하는 데 도움이 되는 탭 완성 이라는 개념에 추가 됩니다. 사용자가 사용자 기록과 추가 도메인 특정 플러그인의 일치 하는 예측에 따라 전체 명령을 검색, 편집 및 실행할 수 있습니다.

### <a name="enable-predictive-intellisense"></a>예측 IntelliSense 사용

예측 IntelliSense는 기본적으로 사용 되지 않습니다. 예측을 사용 하도록 설정 하려면 다음 명령을 실행 하기만 하면 됩니다.

```powershell
Set-PSReadLineOption -PredictionSource History
```

**PredictionSource** 매개 변수는 도메인 특정 요구 사항 및 사용자 지정 요구 사항에 대 한 플러그 인도 허용할 수 있습니다.

예측 IntelliSense를 사용 하지 않도록 설정 하려면 다음을 실행 합니다.

```powershell
Set-PSReadLineOption -PredictionSource None
```

다음 함수는 **[PSConsoleReadLine]** 클래스에서 사용할 수 있습니다.

## <a name="basic-editing-functions"></a>기본 편집 함수

### <a name="abort"></a>중단

현재 작업을 중단 합니다 (예: 증분 기록 검색).

- Emacs `<Ctrl+g>`

### <a name="acceptandgetnext"></a>AcceptAndGetNext

현재 입력을 실행 하려고 합니다. 실행 될 수 있는 경우 (예: AcceptLine) 다음에 ReadLine이 호출 될 때 기록에서 다음 항목을 회수 합니다.

- Emacs `<Ctrl+o>`

### <a name="acceptline"></a>AcceptLine

현재 입력을 실행 하려고 합니다. 누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.

- 입력 `<Enter>`
- Emacs `<Enter>`
- Vi 삽입 모드: `<Enter>`

### <a name="addline"></a>AddLine

연속 프롬프트가 다음 줄에 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다. 이는 한 줄이 자체적으로 전체 입력 인 경우에도 여러 줄 입력을 단일 명령으로 입력 하는 데 유용 합니다.

- 입력 `<Shift+Enter>`
- Emacs `<Shift+Enter>`
- Vi 삽입 모드: `<Shift+Enter>`
- Vi 명령 모드: `<Shift+Enter>`

### <a name="backwarddeletechar"></a>BackwardDeleteChar

커서 앞에 있는 문자를 삭제 합니다.

- Cmd: `<Backspace>` , `<Ctrl+h>`
- Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`
- Vi 삽입 모드: `<Backspace>`
- Vi 명령 모드: `<X>` , `<d,h>`

### <a name="backwarddeleteline"></a>BackwardDeleteLine

Like BackwardKillLine-점에서 줄의 시작 부분으로 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.

- 입력 `<Ctrl+Home>`
- Vi 삽입 모드: `<Ctrl+u>` , `<Ctrl+Home>`
- Vi 명령 모드: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`

### <a name="backwarddeleteword"></a>BackwardDeleteWord

이전 단어를 삭제 합니다.

- Vi 명령 모드: `<Ctrl+w>` , `<d,b>`

### <a name="backwardkillline"></a>BackwardKillLine

커서에 대 한 입력의 시작 부분에서 입력을 지웁니다. 지워진 텍스트는 kill 링에 배치 됩니다.

- Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`

### <a name="backwardkillword"></a>BackwardKillWord

커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다. 커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다. 지워진 텍스트는 kill 링에 배치 됩니다.

- Cmd: `<Ctrl+Backspace>` , `<Ctrl+w>`
- Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`
- Vi 삽입 모드: `<Ctrl+Backspace>`
- Vi 명령 모드: `<Ctrl+Backspace>`

### <a name="cancelline"></a>CancelLine

화면에 입력을 그대로 두고 현재 입력을 취소 합니다. 그러나 프롬프트가 다시 계산 되도록 다시 호스트로 돌아갑니다.

- Vi 삽입 모드: `<Ctrl+c>`
- Vi 명령 모드: `<Ctrl+c>`

### <a name="copy"></a>복사

선택한 영역을 시스템 클립보드에 복사 합니다. 선택 된 지역이 없으면 전체 줄을 복사 합니다.

- 입력 `<Ctrl+C>`

### <a name="copyorcancelline"></a>CopyOrCancelLine

텍스트를 선택한 경우 클립보드로 복사 하 고, 그렇지 않으면 줄을 취소 합니다.

- 입력 `<Ctrl+c>`
- Emacs `<Ctrl+c>`

### <a name="cut"></a>잘라내기

삭제 된 텍스트를 시스템 클립보드에 배치 하는 선택한 영역을 삭제 합니다.

- 입력 `<Ctrl+x>`

### <a name="deletechar"></a>DeleteChar

커서 아래의 문자를 삭제 합니다.

- 입력 `<Delete>`
- Emacs `<Delete>`
- Vi 삽입 모드: `<Delete>`
- Vi 명령 모드: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`

### <a name="deletecharorexit"></a>DeleteCharOrExit

커서 아래의 문자를 삭제 하거나, 줄이 비어 있으면 프로세스를 종료 합니다.

- Emacs `<Ctrl+d>`

### <a name="deleteendofbuffer"></a>DeleteEndOfBuffer

여러 줄 버퍼의 끝까지 삭제 합니다.

- Vi 명령 모드: `<d,G>`

### <a name="deleteendofword"></a>DeleteEndOfWord

단어의 끝까지 삭제 합니다.

- Vi 명령 모드: `<d,e>`

### <a name="deleteline"></a>Deleteline.invoke

여러 줄 버퍼의 현재 논리 줄을 삭제 하 고 실행 취소를 사용 하도록 설정 합니다.

- Vi 명령 모드: `<d,d>` , `<d,_>`

### <a name="deletepreviouslines"></a>DeletePreviousLines

여러 줄 버퍼에서 요청 된 이전 논리 줄과 현재 논리 줄을 삭제 합니다.

- Vi 명령 모드: `<d,k>`

### <a name="deleterelativelines"></a>DeleteRelativeLines

버퍼의 시작 부분에서 여러 줄 버퍼의 현재 논리 줄까지 삭제 합니다.

대부분의 Vi 명령으로 `<d,g,g>` 명령 앞에는 절대 줄 번호를 지정 하는 숫자 인수를 추가할 수 있습니다 .이 숫자는 현재 줄 번호와 함께 삭제 될 줄의 범위를 구성 합니다.
지정 하지 않으면 숫자 인수는 기본적으로 1로 설정 되며이는 여러 줄 버퍼의 첫 번째 논리 줄을 참조 합니다.

여러 줄에서 삭제 되는 실제 줄 수는 현재 논리 줄 번호와 지정 된 숫자 인수 간의 차이로 계산 되므로 음수가 될 수 있습니다. 따라서 메서드 이름의 _상대_ 부분입니다.

- Vi 명령 모드: `<d,g,g>`

### <a name="deletenextlines"></a>DeleteNextLines

여러 줄 버퍼에서 현재 논리 줄 및 요청 된 다음 논리 줄을 삭제 합니다.

- Vi 명령 모드: `<d,j>`

### <a name="deletelinetofirstchar"></a>DeleteLineToFirstChar

여러 줄 버퍼에서 현재 논리 줄의 비어 있지 않은 첫 번째 문자에서 삭제 합니다.

- Vi 명령 모드: `<d,^>`

### <a name="deletetoend"></a>DeleteToEnd

줄의 끝까지 삭제 합니다.

- Vi 명령 모드: `<D>` , `<d,$>`

### <a name="deleteword"></a>DeleteWord

다음 단어를 삭제 합니다.

- Vi 명령 모드: `<d,w>`

### <a name="forwarddeleteline"></a>ForwardDeleteLine

Like ForwardKillLine-포인트에서 줄 끝 까지의 텍스트를 삭제 하지만 삭제 된 텍스트는 kill 링에 삽입 하지 않습니다.

- 입력 `<Ctrl+End>`
- Vi 삽입 모드: `<Ctrl+End>`
- Vi 명령 모드: `<Ctrl+End>`

### <a name="insertlineabove"></a>InsertLineAbove

현재 줄에 커서가 있는 위치에 관계 없이 새 빈 줄이 현재 줄 위에 생성 됩니다. 커서가 새 줄의 시작 부분으로 이동 합니다.

- 입력 `<Ctrl+Enter>`

### <a name="insertlinebelow"></a>Insertlinenea

커서가 현재 줄에 있는지 여부에 관계 없이 현재 줄 아래에 빈 줄이 새로 만들어집니다. 커서가 새 줄의 시작 부분으로 이동 합니다.

- 입력 `<Shift+Ctrl+Enter>`

### <a name="invertcase"></a>InvertCase

현재 문자의 대/소문자를 반전 하 고 다음으로 이동 합니다.

- Vi 명령 모드: `<~>`

### <a name="killline"></a>KillLine

입력의 끝 부분까지 커서에서 입력을 지웁니다. 지워진 텍스트는 kill 링에 배치 됩니다.

- Emacs `<Ctrl+k>`

### <a name="killregion"></a>KillRegion

커서와 표시 사이에 있는 텍스트를 종료 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="killword"></a>KillWord

커서에서 현재 단어의 끝까지 입력을 지웁니다. 커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다. 지워진 텍스트는 kill 링에 배치 됩니다.

- Cmd: `<Alt+d>` , `<Ctrl+Delete>`
- Emacs: `<Alt+d>` , `<Escape,d>`
- Vi 삽입 모드: `<Ctrl+Delete>`
- Vi 명령 모드: `<Ctrl+Delete>`

### <a name="paste"></a>붙여넣기

시스템 클립보드에서 텍스트를 붙여넣습니다.

- Cmd: `<Ctrl+v>` , `<Shift+Insert>`
- Vi 삽입 모드: `<Ctrl+v>`
- Vi 명령 모드: `<Ctrl+v>`

> [!IMPORTANT]
> **Paste** 함수를 사용 하는 경우 클립보드 버퍼의 전체 내용이 psreadline의 입력 버퍼에 붙여넣어집니다. 그런 다음 입력 버퍼가 PowerShell 파서로 전달 됩니다. 콘솔 응용 프로그램의 **마우스 오른쪽 단추 클릭** 붙여넣기 메서드를 사용 하 여 붙여넣은 입력은 입력 버퍼에 한 번에 한 문자씩 복사 됩니다. 입력 버퍼는 줄 바꿈 문자가 복사 될 때 파서에 전달 됩니다. 따라서 입력은 한 번에 한 줄씩 구문 분석 됩니다. 붙여넣기 메서드 간의 차이점으로 인해 실행 동작이 달라 집니다.

### <a name="pasteafter"></a>PasteAfter

커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 뒤에 붙여 넣습니다.

- Vi 명령 모드: `<p>`

### <a name="pastebefore"></a>PasteBefore

커서를 붙여넣은 텍스트의 끝으로 이동 하 여 클립보드를 커서 앞에 붙여 넣습니다.

- Vi 명령 모드: `<P>`

### <a name="prependandaccept"></a>PrependAndAccept

' # ' 앞에를 추가 하 고 줄을 적용 합니다.

- Vi 명령 모드: `<#>`

### <a name="redo"></a>다시 실행

실행 취소를 실행 취소 합니다.

- 입력 `<Ctrl+y>`
- Vi 삽입 모드: `<Ctrl+y>`
- Vi 명령 모드: `<Ctrl+y>`

### <a name="repeatlastcommand"></a>RepeatLastCommand

마지막 텍스트 수정 작업을 반복 합니다.

- Vi 명령 모드: `<.>`

### <a name="revertline"></a>RevertLine

모든 입력을 현재 입력으로 되돌립니다.

- 입력 `<Escape>`
- Emacs: `<Alt+r>` , `<Escape,r>`

### <a name="shellbackwardkillword"></a>ShellBackwardKillWord

커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다. 커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다. 지워진 텍스트는 kill 링에 배치 됩니다.

함수가 바인딩 해제 되었습니다.

### <a name="shellkillword"></a>ShellKillWord

커서에서 현재 단어의 끝까지 입력을 지웁니다. 커서가 단어 사이에 있는 경우 커서에서 다음 단어의 끝까지 입력이 지워집니다. 지워진 텍스트는 kill 링에 배치 됩니다.

함수가 바인딩 해제 되었습니다.

### <a name="swapcharacters"></a>SwapCharacters

현재 문자와 그 앞의 문자를 바꿉니다.

- Emacs `<Ctrl+t>`
- Vi 삽입 모드: `<Ctrl+t>`
- Vi 명령 모드: `<Ctrl+t>`

### <a name="undo"></a>실행 취소

이전 편집을 실행 취소 합니다.

- 입력 `<Ctrl+z>`
- Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`
- Vi 삽입 모드: `<Ctrl+z>`
- Vi 명령 모드: `<Ctrl+z>` , `<u>`

### <a name="undoall"></a>모두를

줄의 모든 이전 편집을 실행 취소 합니다.

- Vi 명령 모드: `<U>`

### <a name="unixwordrubout"></a>UnixWordRubout

커서에 대 한 현재 단어의 시작 부분에서 입력을 지웁니다. 커서가 단어 사이에 있는 경우 이전 단어의 시작 부분에서 커서로 입력이 지워집니다. 지워진 텍스트는 kill 링에 배치 됩니다.

- Emacs `<Ctrl+w>`

### <a name="validateandacceptline"></a>ValidateAndAcceptLine

현재 입력을 실행 하려고 합니다. 누락 된 닫는 괄호, 대괄호 또는 따옴표가 있는 경우와 같이 현재 입력이 완전 하지 않은 경우에는 다음 줄에 연속 프롬프트가 표시 되 고 PSReadLine은 키가 현재 입력을 편집할 수 있도록 대기 합니다.

- Emacs `<Ctrl+m>`

### <a name="viacceptline"></a>ViAcceptLine

줄을 적용 하 고 삽입 모드로 전환 합니다.

- Vi 명령 모드: `<Enter>`

### <a name="viacceptlineorexit"></a>ViAcceptLineOrExit

Emacs 모드에서 DeleteCharOrExit와 비슷하지만 문자를 삭제 하는 대신 줄을 허용 합니다.

- Vi 삽입 모드: `<Ctrl+d>`
- Vi 명령 모드: `<Ctrl+d>`

### <a name="viappendline"></a>ViAppendLine

현재 줄 아래에 새 줄이 삽입 됩니다.

- Vi 명령 모드: `<o>`

### <a name="vibackwarddeleteglob"></a>ViBackwardDeleteGlob

공백을 단어 구분 기호로 사용 하 여 이전 단어를 삭제 합니다.

- Vi 명령 모드: `<d,B>`

### <a name="vibackwardglob"></a>ViBackwardGlob

공백을 구분 기호로 사용 하 여 커서를 이전 단어의 시작 부분으로 다시 이동 합니다.

- Vi 명령 모드: `<B>`

### <a name="videletebrace"></a>ViDeleteBrace

괄호를 포함 하 여 일치 하는 중괄호, 괄호 또는 대괄호를 찾아 내에서 모든 내용을 삭제 합니다.

- Vi 명령 모드: `<d,%>`

### <a name="videleteendofglob"></a>ViDeleteEndOfGlob

단어의 끝까지 삭제 합니다.

- Vi 명령 모드: `<d,E>`

### <a name="videleteglob"></a>Videletlob

다음 glob (공백으로 구분 된 단어)를 삭제 합니다.

- Vi 명령 모드: `<d,W>`

### <a name="videletetobeforechar"></a>ViDeleteToBeforeChar

지정 된 문자가 나타날 때까지 삭제 합니다.

- Vi 명령 모드: `<d,t>`

### <a name="videletetobeforecharbackward"></a>ViDeleteToBeforeCharBackward

지정 된 문자가 나타날 때까지 삭제 합니다.

- Vi 명령 모드: `<d,T>`

### <a name="videletetochar"></a>ViDeleteToChar

지정 된 문자가 나타날 때까지 삭제 합니다.

- Vi 명령 모드: `<d,f>`

### <a name="videletetocharbackward"></a>ViDeleteToCharBackward

지정 된 문자까지 뒤로 삭제 합니다.

- Vi 명령 모드: `<d,F>`

### <a name="viinsertatbegining"></a>ViInsertAtBegining

삽입 모드로 전환 하 고 줄의 시작 부분에 커서를 놓습니다.

- Vi 명령 모드: `<I>`

### <a name="viinsertatend"></a>ViInsertAtEnd

삽입 모드로 전환 하 고 줄의 끝에 커서를 놓습니다.

- Vi 명령 모드: `<A>`

### <a name="viinsertline"></a>ViInsertLine

현재 줄 위에 새 줄이 삽입 됩니다.

- Vi 명령 모드: `<O>`

### <a name="viinsertwithappend"></a>ViInsertWithAppend

현재 줄 위치에서 추가 합니다.

- Vi 명령 모드: `<a>`

### <a name="viinsertwithdelete"></a>ViInsertWithDelete

현재 문자를 삭제 하 고 삽입 모드로 전환 합니다.

- Vi 명령 모드: `<s>`

### <a name="vijoinlines"></a>ViJoinLines

현재 줄과 다음 줄을 조인 합니다.

- Vi 명령 모드: `<J>`

### <a name="vireplaceline"></a>ViReplaceLine

전체 명령줄을 지웁니다.

- Vi 명령 모드: `<S>` , `<c,c>`

### <a name="vireplacetobeforechar"></a>ViReplaceToBeforeChar

지정 된 문자가 될 때까지 바꿉니다.

- Vi 명령 모드: `<c,t>`

### <a name="vireplacetobeforecharbackward"></a>ViReplaceToBeforeCharBackward

지정 된 문자가 될 때까지 바꿉니다.

- Vi 명령 모드: `<c,T>`

### <a name="vireplacetochar"></a>ViReplaceToChar

지정 된 문자가 나타날 때까지 삭제 합니다.

- Vi 명령 모드: `<c,f>`

### <a name="vireplacetocharbackward"></a>ViReplaceToCharBackward

지정 된 문자가 될 때까지 바꿉니다.

- Vi 명령 모드: `<c,F>`

### <a name="viyankbeginningofline"></a>ViYankBeginningOfLine

버퍼의 시작 부분에서 커서로 Yank.

- Vi 명령 모드: `<y,0>`

### <a name="viyankendofglob"></a>ViYankEndOfGlob

커서에서 단어의 끝까지 Yank 합니다.

- Vi 명령 모드: `<y,E>`

### <a name="viyankendofword"></a>ViYankEndOfWord

커서에서 단어의 끝까지 Yank 합니다.

- Vi 명령 모드: `<y,e>`

### <a name="viyankleft"></a>ViYankLeft

커서의 왼쪽에 문자를 Yank 합니다.

- Vi 명령 모드: `<y,h>`

### <a name="viyankline"></a>ViYankLine

전체 버퍼를 Yank 합니다.

- Vi 명령 모드: `<y,y>`

### <a name="viyanknextglob"></a>ViYankNextGlob

커서에서 다음 단어의 시작 부분으로 Yank.

- Vi 명령 모드: `<y,W>`

### <a name="viyanknextword"></a>ViYankNextWord

커서 뒤의 단어를 Yank 합니다.

- Vi 명령 모드: `<y,w>`

### <a name="viyankpercent"></a>ViYankPercent

짝이 되는 중괄호에서 Yank 합니다.

- Vi 명령 모드: `<y,%>`

### <a name="viyankpreviousglob"></a>ViYankPreviousGlob

단어의 시작부터 커서까지 Yank 합니다.

- Vi 명령 모드: `<y,B>`

### <a name="viyankpreviousword"></a>ViYankPreviousWord

커서 앞에 단어를 Yank.

- Vi 명령 모드: `<y,b>`

### <a name="viyankright"></a>ViYankRight

커서 오른쪽의 및 아래에 Yank 문자를 적용 합니다.

- Vi 명령 모드: `<y,l>` , `<y,Spacebar>`

### <a name="viyanktoendofline"></a>ViYankToEndOfLine

커서에서 버퍼 끝까지 Yank.

- Vi 명령 모드: `<y,$>`

### <a name="viyanktofirstchar"></a>ViYankToFirstChar

공백이 아닌 첫 번째 문자에서 커서로 Yank.

- Vi 명령 모드: `<y,^>`

### <a name="yank"></a>Yank

가장 최근에 종료 된 텍스트를 입력에 추가 합니다.

- Emacs `<Ctrl+y>`

### <a name="yanklastarg"></a>YankLastArg

이전 기록 줄에서 마지막 인수를 Yank 합니다. 인수를 사용 하면 처음 호출 될 때 YankNthArg 처럼 동작 합니다. 여러 번 호출 된 경우에는 기록 및 인수에서 방향을 설정 합니다. (음수는 방향을 반대로 바꿉니다.)

- 입력 `<Alt+.>`
- Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`

### <a name="yankntharg"></a>YankNthArg

이전 기록 줄에서 첫 번째 인수 (명령 뒤)를 Yank 합니다.
인수를 사용 하는 경우 n 번째 인수 (0부터 시작)를 yank. 인수가 음수 이면 마지막 인수부터 시작 합니다.

- Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`

### <a name="yankpop"></a>YankPop

이전 작업이 Yank 또는 YankPop 인 경우 이전 빼낼 텍스트를 kill 링에서 다음에 종료 된 텍스트로 바꿉니다.

- Emacs: `<Alt+y>` , `<Escape,y>`

## <a name="cursor-movement-functions"></a>커서 이동 함수

### <a name="backwardchar"></a>BackwardChar

커서를 한 문자 왼쪽으로 이동 합니다. 이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.

- 입력 `<LeftArrow>`
- Emacs: `<LeftArrow>` , `<Ctrl+b>`

### <a name="backwardword"></a>BackwardWord

커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다. 단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.

- 입력 `<Ctrl+LeftArrow>`
- Emacs: `<Alt+b>` , `<Escape,b>`
- Vi 삽입 모드: `<Ctrl+LeftArrow>`
- Vi 명령 모드: `<Ctrl+LeftArrow>`

### <a name="beginningofline"></a>BeginningOfLine

입력에 여러 줄이 있는 경우 현재 줄의 시작 부분으로 이동 하거나 이미 줄의 시작 부분에 있는 경우 입력의 시작 부분으로 이동 합니다. 입력에 한 줄이 있으면 입력의 시작 부분으로 이동 합니다.

- 입력 `<Home>`
- Emacs: `<Home>` , `<Ctrl+a>`
- Vi 삽입 모드: `<Home>`
- Vi 명령 모드: `<Home>`

### <a name="endofline"></a>EndOfLine

입력에 여러 줄이 있는 경우 현재 줄의 끝으로 이동 하거나 줄의 끝에 있는 경우 입력의 끝 부분으로 이동 합니다. 입력에 한 줄이 있으면 입력의 끝 부분으로 이동 합니다.

- 입력 `<End>`
- Emacs: `<End>` , `<Ctrl+e>`
- Vi 삽입 모드: `<End>`

### <a name="forwardchar"></a>ForwardChar

커서를 한 문자 오른쪽으로 이동 합니다. 그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.

- 입력 `<RightArrow>`
- Emacs: `<RightArrow>` , `<Ctrl+f>`

### <a name="forwardword"></a>ForwardWord

커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다. 단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.

- Emacs: `<Alt+f>` , `<Escape,f>`

### <a name="gotobrace"></a>GotoBrace

짝이 되는 중괄호, 괄호 또는 대괄호로 이동 합니다.

- 입력 `<Ctrl+]>`
- Vi 삽입 모드: `<Ctrl+]>`
- Vi 명령 모드: `<Ctrl+]>`

### <a name="gotocolumn"></a>GotoColumn

Arg로 표시 된 열로 이동 합니다.

- Vi 명령 모드: `<|>`

### <a name="gotofirstnonblankofline"></a>GotoFirstNonBlankOfLine

줄에서 비어 있지 않은 첫 번째 문자로 커서를 이동 합니다.

- Vi 명령 모드: `<^>` , `<_>`

### <a name="movetoendofline"></a>MoveToEndOfLine

커서를 입력 끝으로 이동 합니다.

- Vi 명령 모드: `<End>` , `<$>`

### <a name="nextline"></a>NextLine

커서를 다음 줄로 이동 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="nextword"></a>NextWord

커서를 다음 단어의 시작 부분으로 이동 합니다. 단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.

- 입력 `<Ctrl+RightArrow>`
- Vi 삽입 모드: `<Ctrl+RightArrow>`
- Vi 명령 모드: `<Ctrl+RightArrow>`

### <a name="nextwordend"></a>NextWordEnd

커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다. 단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.

- Vi 명령 모드: `<e>`

### <a name="previousline"></a>PreviousLine

커서를 이전 줄로 이동 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="shellbackwardword"></a>ShellBackwardWord

커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다. 단어 경계는 PowerShell 토큰에 의해 정의 됩니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="shellforwardword"></a>ShellForwardWord

커서를 다음 단어의 시작 부분으로 이동 합니다. 단어 경계는 PowerShell 토큰에 의해 정의 됩니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="shellnextword"></a>ShellNextWord

커서를 현재 단어의 끝 부분으로 이동 하거나 단어 사이에 있는 경우 다음 단어의 끝 부분으로 이동 합니다. 단어 경계는 PowerShell 토큰에 의해 정의 됩니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="vibackwardchar"></a>ViBackwardChar

Vi 편집 모드에서 커서를 한 문자 왼쪽으로 이동 합니다. 이렇게 하면 커서가 여러 줄 입력의 이전 줄로 이동 될 수 있습니다.

- Vi 삽입 모드: `<LeftArrow>`
- Vi 명령 모드: `<LeftArrow>` , `<Backspace>` , `<h>`

### <a name="vibackwardword"></a>ViBackwardWord

커서를 현재 단어의 시작 부분으로 다시 이동 하거나 단어 사이에 있는 경우 이전 단어의 시작 부분으로 이동 합니다. 단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.

- Vi 명령 모드: `<b>`

### <a name="viforwardchar"></a>ViForwardChar

Vi 편집 모드에서 커서를 한 문자 오른쪽으로 이동 합니다. 그러면 커서가 여러 줄 입력의 다음 줄로 이동 될 수 있습니다.

- Vi 삽입 모드: `<RightArrow>`
- Vi 명령 모드: `<RightArrow>` , `<Spacebar>` , `<l>`

### <a name="viendofglob"></a>ViEndOfGlob

공백을 구분 기호로 사용 하 여 커서를 단어의 끝으로 이동 합니다.

- Vi 명령 모드: `<E>`

### <a name="viendofpreviousglob"></a>ViEndOfPreviousGlob

공백을 단어 구분 기호로 사용 하 여 이전 단어의 끝으로 이동 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="vigotobrace"></a>ViGotoBrace

GotoBrace와 비슷하지만 토큰 기반이 아니라 문자 기반입니다.

- Vi 명령 모드: `<%>`

### <a name="vinextglob"></a>ViNextGlob

공백을 단어 구분 기호로 사용 하 여 다음 단어로 이동 합니다.

- Vi 명령 모드: `<W>`

### <a name="vinextword"></a>ViNextWord

커서를 다음 단어의 시작 부분으로 이동 합니다. 단어 경계는 구성 가능한 문자 집합으로 정의 됩니다.

- Vi 명령 모드: `<w>`

## <a name="history-functions"></a>기록 함수

### <a name="beginningofhistory"></a>BeginningOfHistory

기록의 첫 번째 항목으로 이동 합니다.

- Emacs `<Alt+<>`

### <a name="clearhistory"></a>ClearHistory

PSReadLine에서 기록을 지웁니다. PowerShell 기록에는 영향을 주지 않습니다.

- 입력 `<Alt+F7>`

### <a name="endofhistory"></a>EndOfHistory

기록에서 마지막 항목 (현재 입력)으로 이동 합니다.

- Emacs `<Alt+>>`

### <a name="forwardsearchhistory"></a>ForwardSearchHistory

기록을 통해 증분 전달 검색을 수행 합니다.

- 입력 `<Ctrl+s>`
- Emacs `<Ctrl+s>`

### <a name="historysearchbackward"></a>HistorySearchBackward

현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.

- 입력 `<F8>`

### <a name="historysearchforward"></a>HistorySearchForward

현재 입력을 시작 및 입력과 커서 사이의 문자와 일치 하는 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.

- 입력 `<Shift+F8>`

### <a name="nexthistory"></a>NextHistory

현재 입력을 PSReadLine 기록의 ' 다음 ' 항목으로 바꿉니다.

- 입력 `<DownArrow>`
- Emacs: `<DownArrow>` , `<Ctrl+n>`
- Vi 삽입 모드: `<DownArrow>`
- Vi 명령 모드: `<DownArrow>` , `<j>` , `<+>`

### <a name="previoushistory"></a>PreviousHistory

현재 입력을 PSReadLine 기록의 ' 이전 ' 항목으로 바꿉니다.

- 입력 `<UpArrow>`
- Emacs: `<UpArrow>` , `<Ctrl+p>`
- Vi 삽입 모드: `<UpArrow>`
- Vi 명령 모드: `<UpArrow>` , `<k>` , `<->`

### <a name="reversesearchhistory"></a>ReverseSearchHistory

기록을 통해 증분 역방향 검색을 수행 합니다.

- 입력 `<Ctrl+r>`
- Emacs `<Ctrl+r>`

### <a name="visearchhistorybackward"></a>ViSearchHistoryBackward

검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.

- Vi 삽입 모드: `<Ctrl+r>`
- Vi 명령 모드: `</>` , `<Ctrl+r>`

## <a name="completion-functions"></a>완료 함수

### <a name="complete"></a>완료

커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다. 가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다. 가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.

- Emacs `<Tab>`

### <a name="menucomplete"></a>MenuComplete

커서를 둘러싼 텍스트에서 완료를 수행 하려고 합니다. 가능한 여러 가지 완료가 있는 경우 완료 하는 데 가장 긴 명확한 접두사가 사용 됩니다. 가장 긴 명확한 완료를 완료 하려고 하면 가능한 완성 목록이 표시 됩니다.

- Cmd: `<Ctrl+@>` , `<Ctrl+Spacebar>`
- Emacs `<Ctrl+Spacebar>`

### <a name="possiblecompletions"></a>PossibleCompletions

가능한 완료 목록을 표시 합니다.

- Emacs `<Alt+=>`
- Vi 삽입 모드: `<Ctrl+Spacebar>`
- Vi 명령 모드: `<Ctrl+Spacebar>`

### <a name="tabcompletenext"></a>TabCompleteNext

다음에 사용 가능한 완료로 커서를 둘러싼 텍스트를 완성 해 봅니다.

- 입력 `<Tab>`
- Vi 명령 모드: `<Tab>`

### <a name="tabcompleteprevious"></a>TabCompletePrevious

이전에 사용 가능한 완료를 사용 하 여 커서를 둘러싼 텍스트를 완료 하려고 합니다.

- 입력 `<Shift+Tab>`
- Vi 명령 모드: `<Shift+Tab>`

### <a name="vitabcompletenext"></a>ViTabCompleteNext

필요한 경우 현재 편집 그룹을 종료 하 고 TabCompleteNext를 호출 합니다.

- Vi 삽입 모드: `<Tab>`

### <a name="vitabcompleteprevious"></a>ViTabCompletePrevious

필요한 경우 현재 편집 그룹을 종료 하 고 TabCompletePrevious를 호출 합니다.

- Vi 삽입 모드: `<Shift+Tab>`

## <a name="miscellaneous-functions"></a>기타 함수

### <a name="acceptnextsuggestionword"></a>AcceptNextSuggestionWord

인라인 또는 선택한 제안의 다음 단어를 적용 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="acceptsuggestion"></a>AcceptSuggestion

현재 인라인 또는 선택한 제안에 동의 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="capturescreen"></a>CaptureScreen

대화형 화면 캡처 시작-위쪽/아래쪽 화살표 선 선택, 선택한 텍스트를 클립보드에 텍스트 및 html로 복사를 입력 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="clearscreen"></a>ClearScreen

화면을 지우고 화면 위쪽에 현재 줄을 그립니다.

- 입력 `<Ctrl+l>`
- Emacs `<Ctrl+l>`
- Vi 삽입 모드: `<Ctrl+l>`
- Vi 명령 모드: `<Ctrl+l>`

### <a name="digitargument"></a>DigitArgument

다른 함수에 전달할 새 숫자 인수를 시작 합니다.

- Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`
- Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,,,, `<Alt+9>` , `<Alt+->`
- Vi 명령 모드: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` `<7>` `<8>` ,,, `<9>`

### <a name="invokeprompt"></a>InvokePrompt

현재 프롬프트를 지우고 prompt 함수를 호출 하 여 프롬프트를 다시 표시 합니다. 상태를 변경 하는 사용자 지정 키 처리기 (예: 현재 디렉터리 변경)에 유용 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="scrolldisplaydown"></a>ScrollDisplayDown

한 화면 아래로 표시를 스크롤합니다.

- 입력 `<PageDown>`
- Emacs `<PageDown>`

### <a name="scrolldisplaydownline"></a>ScrollDisplayDownLine

표시를 한 줄 아래로 스크롤합니다.

- 입력 `<Ctrl+PageDown>`
- Emacs `<Ctrl+PageDown>`

### <a name="scrolldisplaytocursor"></a>ScrollDisplayToCursor

표시를 커서로 스크롤합니다.

- Emacs `<Ctrl+End>`

### <a name="scrolldisplaytop"></a>ScrollDisplayTop

표시를 맨 위로 스크롤합니다.

- Emacs `<Ctrl+Home>`

### <a name="scrolldisplayup"></a>ScrollDisplayUp

한 화면 위로 표시를 스크롤합니다.

- 입력 `<PageUp>`
- Emacs `<PageUp>`

### <a name="scrolldisplayupline"></a>ScrollDisplayUpLine

디스플레이를 한 줄 위로 스크롤합니다.

- 입력 `<Ctrl+PageUp>`
- Emacs `<Ctrl+PageUp>`

### <a name="selfinsert"></a>SelfInsert

키를 삽입 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="showkeybindings"></a>ShowKeyBindings 바인딩

모든 바인딩된 키를 표시 합니다.

- 입력 `<Ctrl+Alt+?>`
- Emacs `<Ctrl+Alt+?>`
- Vi 삽입 모드: `<Ctrl+Alt+?>`

### <a name="vicommandmode"></a>ViCommandMode

Vi-Insert에서 현재 운영 모드를 Vi 명령으로 전환 합니다.

- Vi 삽입 모드: `<Escape>`

### <a name="vidigitargumentinchord"></a>ViDigitArgumentInChord

Vi의 누르는 중 하나에서 다른 함수에 전달할 새 digit 인수를 시작 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="vieditvisually"></a>ViEditVisually

$Env: 편집기 또는 $env: 시각적 개체에 지정 된 텍스트 편집기에서 명령줄을 편집 합니다.

- Emacs `<Ctrl+x,Ctrl+e>`
- Vi 명령 모드: `<v>`

### <a name="viexit"></a>ViExit

셸을 종료 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="viinsertmode"></a>ViInsertMode

삽입 모드로 전환 합니다.

- Vi 명령 모드: `<i>`

### <a name="whatiskey"></a>WhatIsKey

키를 읽고 키가 바인딩된 정보를 알려 줍니다.

- 입력 `<Alt+?>`
- Emacs `<Alt+?>`

## <a name="selection-functions"></a>선택 함수

### <a name="exchangepointandmark"></a>ExchangePointAndMark

커서는 표시 위치에 배치 되 고 표시는 커서의 위치로 이동 합니다.

- Emacs `<Ctrl+x,Ctrl+x>`

### <a name="selectall"></a>SelectAll

전체 줄을 선택 합니다.

- 입력 `<Ctrl+a>`

### <a name="selectbackwardchar"></a>SelectBackwardChar

이전 문자를 포함 하도록 현재 선택 영역을 조정 합니다.

- 입력 `<Shift+LeftArrow>`
- Emacs `<Shift+LeftArrow>`

### <a name="selectbackwardsline"></a>SelectBackwardsLine

커서에서 줄의 시작 부분까지 포함 하도록 현재 선택 영역을 조정 합니다.

- 입력 `<Shift+Home>`
- Emacs `<Shift+Home>`

### <a name="selectbackwardword"></a>SelectBackwardWord

이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.

- 입력 `<Shift+Ctrl+LeftArrow>`
- Emacs `<Alt+B>`

### <a name="selectforwardchar"></a>SelectForwardChar

다음 문자를 포함 하도록 현재 선택 영역을 조정 합니다.

- 입력 `<Shift+RightArrow>`
- Emacs `<Shift+RightArrow>`

### <a name="selectforwardword"></a>SelectForwardWord

ForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.

- Emacs `<Alt+F>`

### <a name="selectline"></a>줄을 select

커서에서 줄의 끝까지 포함 하도록 현재 선택 영역을 조정 합니다.

- 입력 `<Shift+End>`
- Emacs `<Shift+End>`

### <a name="selectnextword"></a>SelectNextWord

다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.

- 입력 `<Shift+Ctrl+RightArrow>`

### <a name="selectshellbackwardword"></a>SelectShellBackwardWord

ShellBackwardWord를 사용 하 여 이전 단어를 포함 하도록 현재 선택 영역을 조정 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="selectshellforwardword"></a>SelectShellForwardWord

ShellForwardWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="selectshellnextword"></a>SelectShellNextWord

ShellNextWord를 사용 하 여 다음 단어를 포함 하도록 현재 선택 영역을 조정 합니다.

- 함수가 바인딩 해제 되었습니다.

### <a name="setmark"></a>SetMark

이후 편집 명령에 사용할 커서의 현재 위치를 표시 합니다.

- Emacs `<Ctrl+@>`

## <a name="predictive-intellisense-functions"></a>예측 IntelliSense 함수

> [!NOTE]
> 이러한 함수를 사용 하려면 예측 IntelliSense를 사용 하도록 설정 해야 합니다.

### <a name="acceptnextwordsuggestion"></a>AcceptNextWordSuggestion

예측 IntelliSense에서 인라인 제안의 다음 단어를 허용 합니다.
이 함수 <kbd></kbd> + 는 다음 명령을 실행 하 여 Ctrl<kbd>F</kbd> 를 사용 하 여 바인딩할 수 있습니다.

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a>AcceptSuggestion

커서가 현재 줄의 끝에 있을 때 <kbd>오른쪽 화살표</kbd> 를 눌러 예측 IntelliSense의 현재 인라인 제안을 허용 합니다.

## <a name="search-functions"></a>검색 함수

### <a name="charactersearch"></a>CharacterSearch

문자를 읽고 그 다음 번에 해당 문자를 검색 합니다.
인수를 지정 하는 경우 n 번째 발생에 대해 앞으로 (음수 이면 뒤로) 검색 합니다.

- 입력 `<F3>`
- Emacs `<Ctrl+]>`
- Vi 삽입 모드: `<F3>`
- Vi 명령 모드: `<F3>`

### <a name="charactersearchbackward"></a>CharacterSearchBackward

문자를 읽은 다음 해당 문자의 다음 항목을 뒤로 검색 합니다. 인수를 지정 하는 경우 n 번째 발생에 대해 뒤로 검색 하거나 음수 이면 전달 합니다.

- 입력 `<Shift+F3>`
- Emacs `<Ctrl+Alt+]>`
- Vi 삽입 모드: `<Shift+F3>`
- Vi 명령 모드: `<Shift+F3>`

### <a name="repeatlastcharsearch"></a>RepeatLastCharSearch

마지막으로 기록 된 문자 검색을 반복 합니다.

- Vi 명령 모드: `<;>`

### <a name="repeatlastcharsearchbackwards"></a>RepeatLastCharSearchBackwards

마지막으로 기록 된 문자 검색을 반대 방향으로 반복 합니다.

- Vi 명령 모드: `<,>`

### <a name="repeatsearch"></a>RepeatSearch

이전과 동일한 방향으로 마지막 검색을 반복 합니다.

- Vi 명령 모드: `<n>`

### <a name="repeatsearchbackward"></a>RepeatSearchBackward

이전과 동일한 방향으로 마지막 검색을 반복 합니다.

- Vi 명령 모드: `<N>`

### <a name="searchchar"></a>SearchChar

다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다. ' T '의 기능에 대 한 것입니다.

- Vi 명령 모드: `<f>`

### <a name="searchcharbackward"></a>SearchCharBackward

다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다. ' T '의 기능에 대 한 것입니다.

- Vi 명령 모드: `<F>`

### <a name="searchcharbackwardwithbackoff"></a>SearchCharBackwardWithBackoff

다음 문자를 읽은 다음 뒤로 이동 하 여 문자를 다시 찾습니다. ' T '의 기능에 대 한 것입니다.

- Vi 명령 모드: `<T>`

### <a name="searchcharwithbackoff"></a>SearchCharWithBackoff

다음 문자를 읽은 후 앞으로 이동 하 여 문자를 다시 찾습니다. ' T '의 기능에 대 한 것입니다.

- Vi 명령 모드: `<t>`

### <a name="searchforward"></a>SearchForward

검색 문자열을 묻는 메시지를 표시 하 고 AcceptLine에 대 한 검색을 시작 합니다.

- Vi 삽입 모드: `<Ctrl+s>`
- Vi 명령 모드: `<?>` , `<Ctrl+s>`

## <a name="custom-key-bindings"></a>사용자 지정 키 바인딩

PSReadLine은 cmdlet을 사용 하 여 사용자 지정 키 바인딩을 지원 `Set-PSReadLineKeyHandler` 합니다. 대부분의 사용자 지정 키 바인딩은 위의 함수 중 하나를 호출 합니다. 예를 들면

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

ScriptBlock을 키에 바인딩할 수 있습니다. ScriptBlock은 필요한 모든 작업을 수행할 수 있습니다. 몇 가지 유용한 예는 다음과 같습니다.

- 명령줄 편집
- 새 창 열기 (예: 도움말)
- 명령줄을 변경 하지 않고 디렉터리를 변경 합니다.

ScriptBlock은 두 개의 인수를 받습니다.

- `$key` -사용자 지정 바인딩을 트리거한 키 인 **[ConsoleKeyInfo]** 개체입니다. 동일한 ScriptBlock을 여러 키에 바인딩하고 키에 따라 다른 작업을 수행 해야 하는 경우 $key를 확인할 수 있습니다. 많은 사용자 지정 바인딩에서이 인수를 무시 합니다.

- `$arg` -임의의 인수입니다. 가장 자주 사용 되는 정수 인수는 사용자가 키 바인딩 DigitArgument에서 전달 하는 것입니다. 바인딩에서 인수를 허용 하지 않는 경우에는이 인수를 무시 하는 것이 합리적입니다.

실행 하지 않고 기록에 명령줄을 추가 하는 예제를 살펴보겠습니다. 이는 작업을 수행 하지 못했지만 이미 입력 한 명령줄을 다시 입력 하지 않으려는 경우에 유용 합니다.

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

PSReadLine 모듈 폴더에 설치 된 파일에서 더 많은 예제를 볼 수 있습니다 `SamplePSReadLineProfile.ps1` .

대부분의 키 바인딩은 일부 도우미 함수를 사용 하 여 명령줄을 편집 합니다.
이러한 Api는 다음 섹션에 설명 되어 있습니다.

## <a name="custom-key-binding-support-apis"></a>사용자 지정 키 바인딩 지원 Api

다음 함수는 PSConsoleReadLine에서 공용 이지만 키에 직접 바인딩할 수 없습니다. 대부분은 사용자 지정 키 바인딩에 유용 합니다.

```csharp
void AddToHistory(string command)
```

실행 하지 않고 기록에 명령줄을 추가 합니다.

```csharp
void ClearKillRing()
```

Kill 링을 지웁니다.  이는 주로 테스트에 사용 됩니다.

```csharp
void Delete(int start, int length)
```

시작에서 길이 문자를 삭제 합니다.  이 작업은 실행 취소/다시 실행을 지원 합니다.

```csharp
void Ding()
```

사용자 기본 설정에 따라 작업을 수행 합니다.

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

이러한 두 함수는 입력 버퍼의 현재 상태에 대 한 유용한 정보를 검색 합니다.  첫 번째는 간단한 경우에 보다 일반적으로 사용 됩니다.  두 번째는 바인딩에서 Ast를 사용 하 여 더 높은 작업을 수행 하는 경우에 사용 됩니다.

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

이러한 두 함수는에 사용 됩니다 `Get-PSReadLineKeyHandler` . 첫 번째는 모든 키 바인딩을 가져오는 데 사용 됩니다. 두 번째는 특정 키 바인딩을 가져오는 데 사용 됩니다.

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

이 함수는 Get-PSReadLineOption에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

명령줄에 선택 항목이 없으면-1이 시작 및 길이 둘 다에서 반환 됩니다. 명령줄에 선택 항목이 있는 경우 선택의 시작 및 길이가 반환 됩니다.

```csharp
void Insert(char c)
void Insert(string s)
```

커서에 문자 또는 문자열을 삽입 합니다.  이 작업은 실행 취소/다시 실행을 지원 합니다.

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

PSReadLine에 대 한 주 진입점입니다. 재귀를 지원 하지 않으므로 사용자 지정 키 바인딩에는 유용 하지 않습니다.

```csharp
void RemoveKeyHandler(string[] key)
```

이 함수는 Remove-PSReadLineKeyHandler에서 사용 되며 사용자 지정 키 바인딩에서 너무 유용 하지 않을 수 있습니다.

```csharp
void Replace(int start, int length, string replacement)
```

일부 입력을 바꿉니다. 이 작업은 실행 취소/다시 실행을 지원 합니다. 이는 실행 취소의 단일 작업으로 처리 되기 때문에 Delete 뒤에 Insert를 통해 선호 됩니다.

```csharp
void SetCursorPosition(int cursor)
```

커서를 지정 된 오프셋으로 이동 합니다. 실행 취소를 위해 커서 이동이 추적 되지 않습니다.

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

이 함수는 cmdlet Set-PSReadLineOption에서 사용 되는 도우미 메서드로, 설정을 일시적으로 변경 하려는 사용자 지정 키 바인딩에 유용할 수 있습니다.

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

이 도우미 메서드는 DigitArgument을 준수 하는 사용자 지정 바인딩에 사용 됩니다. 일반적인 호출은 다음과 같습니다.

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a>참고

### <a name="command-history"></a>명령 기록

PSReadLine은 명령줄에서 입력 한 모든 명령 및 데이터를 포함 하는 기록 파일을 유지 관리 합니다. 여기에는 암호를 비롯 한 중요 한 데이터가 포함 될 수 있습니다. 예를 들어 cmdlet을 사용 하는 경우 `ConvertTo-SecureString` 암호는 일반 텍스트로 기록 파일에 기록 됩니다. 기록 파일은 라는 파일입니다 `$($host.Name)_history.txt` . Windows 시스템에서 기록 파일은에 저장 됩니다 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` . Windows가 아닌 시스템에서 기록 파일은 또는에 저장 됩니다 `$env:XDG_DATA_HOME/powershell/PSReadLine` `$env:HOME/.local/share/powershell/PSReadLine` .

### <a name="feedback--contributing-to-psreadline"></a>PSReadLine에 영향을 주는 & 피드백

[GitHub의 PSReadLine](https://github.com/PowerShell/PSReadLine)

GitHub 페이지에서 끌어오기 요청을 제출 하거나 피드백을 제출할 수 있습니다.

## <a name="see-also"></a>참고 항목

PSReadLine은 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 라이브러리의 영향을 많이 받습니다.
