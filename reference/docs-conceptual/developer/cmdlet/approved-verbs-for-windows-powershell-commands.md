---
title: PowerShell 명령에 대해 승인 된 동사 | Microsoft Docs
ms.date: 09/07/2018
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.openlocfilehash: f065610b6e54c9a6a927948bc6b2ffe5a1671e0c
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162480"
---
# <a name="approved-verbs-for-powershell-commands"></a>PowerShell 명령에 대해 승인 된 동사

PowerShell에서는 cmdlet 및 해당 파생 Microsoft .NET 프레임 워크 클래스에 대해 동사-명사 쌍을 사용 합니다. 예를 들어 powershell에서 제공 하는 `Get-Command` cmdlet은 powershell에 등록 된 모든 명령을 검색 하는 데 사용 됩니다. 이름의 verb 부분은 cmdlet이 수행 하는 작업을 식별 합니다. 이름의 명사 부분은 동작을 수행 하는 엔터티를 식별 합니다.

> [!NOTE]
> PowerShell은 용어 _동사_ 를 사용 하 여 단어가 영어의 표준 동사가 아닌 경우에도 동작을 의미 하는 단어를 설명 합니다. 예를 들어 _New_ 라는 용어는 영어의 동사가 아닌 경우에도 작업을 암시 하기 때문에 유효한 PowerShell 동사 이름입니다.

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->

승인 된 각 동사에는 해당 하는 _별칭 접두사가_ 정의 되어 있습니다.
이 별칭 접두사는 일반적으로 해당 동사를 사용 하는 명령에 대 한 별칭의 이름을 나타내는 데 사용 됩니다.
예를 들어의 별칭 접두사는 `Import` `ip` 이며, 그에 따라에 대 한 별칭은입니다 `Import-Module` `ipmo` .  이는 권장 사항 이지만 규칙은 아닙니다. 특히 다른 환경에서 잘 알려진 명령 모방 명령 별칭에는 적용 하지 않아도 됩니다.

## <a name="verb-naming-rules"></a>동사 명명 규칙

다음 목록에서는 cmdlet 이름에 대 한 동사를 선택할 때 고려해 야 할 지침을 제공 합니다.

- 동사를 지정 하는 경우 PowerShell에서 제공 하는 미리 정의 된 동사 이름 중 하나를 사용 하는 것이 좋습니다. 이러한 미리 정의 된 동사에 대 한 별칭은 다음 표에 포함 되어 있습니다. 미리 정의 된 동사를 사용 하는 경우 생성 하는 cmdlet, PowerShell에서 제공 하는 cmdlet 및 다른 사용자가 디자인 한 cmdlet 간에 일관성을 유지할 수 있습니다.

- 미리 정의 된 동사를 사용 하 여 동작의 일반 범위를 설명 하 고 매개 변수를 사용 하 여 cmdlet의 동작을 더 구체화 합니다.

- Cmdlet 간에 일관성을 유지 하려면 승인 된 동사의 동의어를 사용 하지 마십시오.

- 이 항목에 나열 된 각 동사의 형식만 사용 합니다. 예를 들어 "Get"을 사용 하 고 "Get" 또는 "Get"을 사용 하지 마십시오.

- 동사에 파스칼식 대/소문자를 사용 합니다. 파스칼식 대/소문자 구분에서 각 단어의 첫 글자는 대문자 (예: "ForEach")입니다.

- 다음 예약 된 동사 또는 별칭을 사용 하지 마십시오. 이러한 동사는 powershell 언어 또는 PowerShell에서 제공 하는 특별 한 사례 cmdlet에서 사용 됩니다.
  - ForEach (foreach)
  - Format (f)
  - 그룹 (gp)
  - 정렬 (sr)
  - 티 (te)
  - Where (호환성이)

Cmdlet을 사용 하 여 동사의 전체 목록을 표시할 수 있습니다 `Get-Verb` .

## <a name="similar-verbs-for-different-actions"></a>다른 동작에 대 한 유사한 동사

다음과 유사한 동사는 다른 작업을 나타냅니다.

### <a name="new-vs-set"></a>신규 및 Set

`New`동사는 새 리소스를 만드는 데 사용 됩니다. `Set`동사는 기존 리소스를 수정 하는 데 사용 됩니다. 예를 들어 cmdlet과 같이 리소스가 없는 경우에는 리소스를 만들 수 `Set-Variable` 있습니다.

### <a name="find-vs-search"></a>찾기 및 검색

`Find`동사는 개체를 검색 하는 데 사용 됩니다. `Search`동사는 컨테이너의 리소스에 대 한 참조를 만드는 데 사용 됩니다.

### <a name="get-vs-read"></a>Get 및 Read

동사는 파일 등의 `Get` 리소스를 검색 하는 데 사용 됩니다. `Read`동사는 파일 등의 원본에서 정보를 가져오는 데 사용 됩니다.

### <a name="invoke-vs-start"></a>호출과 시작 비교

`Invoke`동사는 명령을 실행 하는 것과 같이 일반적으로 동기 작업 인 작업을 수행 하는 데 사용 됩니다. `Start`동사는 프로세스 시작과 같은 일반적으로 비동기 작업 인 작업을 시작 하는 데 사용 됩니다.

### <a name="ping-vs-test"></a>Ping 및 테스트 비교

동사를 사용 `Test` 합니다.

## <a name="common-verbs"></a>일반 동사

PowerShell은 [VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) 열거형 클래스를 사용 하 여 거의 모든 cmdlet에 적용 될 수 있는 제네릭 작업을 정의 합니다. 다음 표에서는 대부분의 정의 된 동사를 보여 줍니다.

|동사 (별칭)|작업|주석|
|--------------------|------------|--------------|
|(A) [추가](/dotnet/api/System.Management.Automation.VerbsCommon.Add)|컨테이너에 리소스를 추가 하거나 항목을 다른 항목에 연결 합니다. 예를 들어 `Add-Content` cmdlet은 파일에 콘텐츠를 추가 합니다. 이 동사는와 쌍을 이룹니다 `Remove` .|이 작업의 경우 Append, Attach, Attach 또는 Insert와 같은 동사를 사용 하지 마십시오.|
|[Clear](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|컨테이너에서 모든 리소스를 제거 하지만 컨테이너를 삭제 하지는 않습니다. 예를 들어 `Clear-Content` cmdlet은 파일의 내용을 제거 하지만 파일을 삭제 하지는 않습니다.|이 작업의 경우 Flush, Erase, Release, 표시 해제, 설정 해제 또는 무효화 같은 동사를 사용 하지 마십시오.|
|[닫기](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|리소스의 상태를 변경 하 여 액세스할 수 없거나 사용할 수 없게 되거나 사용할 수 없도록 설정 합니다. 이 동사는와 쌍을 이룹니다.`Open.`||
|[복사](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|리소스를 다른 이름이 나 다른 컨테이너에 복사 합니다. 예를 들어 `Copy-Item` 저장 된 데이터에 액세스 하는 데 사용 되는 cmdlet은 데이터 저장소의 한 위치에서 다른 위치로 항목을 복사 합니다.|이 작업의 경우 중복, 복제, 복제 또는 동기화와 같은 동사를 사용 하지 마십시오.|
|[Enter](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|사용자가 리소스로 이동할 수 있도록 하는 작업을 지정 합니다. 예를 들어 `Enter-PSSession` cmdlet은 사용자를 대화형 세션에 배치 합니다. 이 동사는와 쌍을 이룹니다 `Exit` .|이 작업의 경우 Push 또는 Into와 같은 동사를 사용 하지 마십시오.|
|[종료](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (예:)|현재 환경 또는 컨텍스트를 가장 최근에 사용한 컨텍스트로 설정 합니다. 예를 들어 `Exit-PSSession` cmdlet은 대화형 세션을 시작 하는 데 사용 된 세션에 사용자를 배치 합니다. 이 동사는와 쌍을 이룹니다 `Enter` .|이 작업의 경우 Pop 또는 Out과 같은 동사를 사용 하지 마십시오.|
|[찾기](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|컨테이너에서 알 수 없거나 암시 된, 선택적 또는 지정 된 개체를 찾습니다.||
|[Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|지정 된 폼 또는 레이아웃으로 개체를 정렬 합니다.||
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|리소스를 검색 하는 작업을 지정 합니다. 이 동사는와 쌍을 이룹니다 `Set` .|이 작업의 경우 읽기, 열기, Cat, 형식, 디렉터리, 가져오기, 덤프, 획득, 검사, 찾기 또는 검색과 같은 동사를 사용 하지 마십시오.|
|[숨기기](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|리소스를 감지할 수 없게 만듭니다. 예를 들어 이름이 Hide 동사를 포함 하는 cmdlet은 사용자의 서비스를 숨길 수 있습니다. 이 동사는와 쌍을 이룹니다 `Show` .|이 작업의 경우 Block과 같은 동사를 사용 하지 마십시오.|
|[조인](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|리소스를 하나의 리소스로 결합 합니다. 예를 들어 `Join-Path` cmdlet은 경로를 자식 경로 중 하나와 결합 하 여 단일 경로를 만듭니다. 이 동사는와 쌍을 이룹니다 `Split` .|이 작업의 경우 Combine, 자리, Connect 또는 Connect와 같은 동사를 사용 하지 마십시오.|
|[Lock](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|리소스를 보호 합니다. 이 동사는와 쌍을 이룹니다 `Unlock` .|이 작업의 경우 Restrict 또는 Secure와 같은 동사를 사용 하지 마십시오.|
|[이동](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|리소스를 한 위치에서 다른 위치로 이동 합니다. 예를 들어 `Move-Item` cmdlet은 데이터 저장소의 한 위치에서 다른 위치로 항목을 이동 합니다.|이 작업의 경우 전송, 이름 또는 마이그레이션 같은 동사를 사용 하지 마십시오.|
|[새](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|리소스를 만듭니다. `Set`Cmdlet과 같은 데이터를 포함 하는 리소스를 만들 때에도 동사를 사용할 수 있습니다 `Set-Variable` .|이 작업의 경우 만들기, 생성, 빌드, 만들기 또는 할당과 같은 동사를 사용 하지 마십시오.|
|[열기](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|리소스의 상태를 변경 하 여 액세스 가능, 사용 가능 또는 사용할 수 있도록 합니다. 이 동사는와 쌍을 이룹니다 `Close` .||
|[최적화](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|리소스의 효율성을 높입니다.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|스택의 맨 위에서 항목을 제거 합니다. 예를 들어 `Pop-Location` cmdlet은 현재 위치를 가장 최근에 스택에 푸시한 위치로 변경 합니다.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|스택의 맨 위에 항목을 추가 합니다. 예를 들어 `Push-Location` cmdlet은 현재 위치를 스택에 푸시합니다.||
|다시 [실행](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|리소스를 실행 취소 된 상태로 다시 설정 합니다.||
|[제거](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|컨테이너에서 리소스를 삭제 합니다. 예를 들어 `Remove-Variable` cmdlet은 변수와 그 값을 삭제 합니다. 이 동사는와 쌍을 이룹니다 `Add` .|이 작업의 경우 Clear, Cut, Dispose, Clear 또는 Erase와 같은 동사를 사용 하지 마십시오.|
|[이름 바꾸기](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) ()|리소스의 이름을 변경 합니다. 예를 들어 `Rename-Item` 저장 된 데이터에 액세스 하는 데 사용 되는 cmdlet은 데이터 저장소에 있는 항목의 이름을 변경 합니다.|이 작업의 경우 Change와 같은 동사를 사용 하지 마십시오.|
|[다시 설정](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|리소스를 원래 상태로 다시 설정 합니다.||
|[크기 조정](/dotnet/api/System.Management.Automation.VerbsCommon.Resize)(rz)|리소스의 크기를 변경 합니다.||
|[검색](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|컨테이너의 리소스에 대 한 참조를 만듭니다.|이 작업의 경우 찾기 또는 찾기와 같은 동사를 사용 하지 마십시오.|
|[선택](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|컨테이너에서 리소스를 찾습니다. 예를 들어 `Select-String` cmdlet은 문자열 및 파일에서 텍스트를 찾습니다.|이 작업의 경우 찾기 또는 찾기와 같은 동사를 사용 하지 마십시오.|
|[집합](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|기존 리소스의 데이터를 대체 하거나 일부 데이터를 포함 하는 리소스를 만듭니다. 예를 들어 `Set-Date` cmdlet은 로컬 컴퓨터의 시스템 시간을 변경 합니다. ( `New` 동사를 사용 하 여 리소스를 만들 수도 있습니다.) 이 동사는와 쌍을 이룹니다 `Get` .|이 작업의 경우 쓰기, 다시 설정, 할당, 구성 등의 동사를 사용 하지 마십시오.|
|[표시](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|사용자에 게 리소스를 표시 합니다. 이 동사는와 쌍을 이룹니다 `Hide` .|이 작업의 경우 표시 또는 생성과 같은 동사를 사용 하지 마십시오.|
|[건너뛰기](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (대만)|시퀀스에서 하나 이상의 리소스나 요소를 무시 합니다.|이 작업의 경우 바이패스 또는 점프와 같은 동사를 사용 하지 마십시오.|
|[분할](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|리소스의 일부를 구분 합니다. 예를 들어 `Split-Path` cmdlet은 경로의 다른 부분을 반환 합니다. 이 동사는와 쌍을 이룹니다 `Join` .|이 작업의 경우에는 별도의 동사를 사용 하지 마십시오.|
|[단계](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|시퀀스의 다음 점 또는 리소스로 이동 합니다.||
|[스위치](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|두 개의 위치, 책임 또는 상태 사이에서 변경 하는 등 두 리소스 사이에서 대체 되는 작업을 지정 합니다.||
|[실행 취소](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (취소)|리소스를 이전 상태로 설정 합니다.||
|[잠금 해제](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (영국)|잠긴 리소스를 해제 합니다. 이 동사는와 쌍을 이룹니다 `Lock` .|이 작업의 경우 릴리스, 제한 없음 또는 보안 해제와 같은 동사를 사용 하지 마십시오.|
|[Watch](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc.exe)|지속적으로 리소스를 검사 하거나 변경에 대 한 모니터링 합니다.||

## <a name="communications-verbs"></a>통신 동사

PowerShell은 [VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) 클래스를 사용 하 여 통신에 적용 되는 작업을 정의 합니다. 다음 표에서는 대부분의 정의 된 동사를 보여 줍니다.

|동사 (별칭)|작업|주석|
|--------------------|------------|--------------|
|[연결](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|원본 및 대상 간에 링크를 만듭니다. 이 동사는와 쌍을 이룹니다 `Disconnect` .|이 작업의 경우 Join 또는 Telnet과 같은 동사를 사용 하지 마십시오.|
|[연결 끊기](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|원본과 대상 간의 링크를 끊습니다. 이 동사는와 쌍을 이룹니다 `Connect` .|이 작업의 경우 중단 또는 로그 오프와 같은 동사를 사용 하지 마십시오.|
|[읽기](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|원본에서 정보를 가져옵니다. 이 동사는와 쌍을 이룹니다 `Write` .|이 작업의 경우 획득, 프롬프트 또는 Get과 같은 동사를 사용 하지 마십시오.|
|[수신](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|원본에서 전송 된 정보를 수락 합니다. 이 동사는와 쌍을 이룹니다 `Send` .|이 작업의 경우 읽기, 수락 또는 피킹 (Peeking)과 같은 동사를 사용 하지 마십시오.|
|[송신](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|대상에 정보를 전달 합니다. 이 동사는와 쌍을 이룹니다 `Receive` .|이 작업의 경우 Put, 브로드캐스트, 메일 또는 팩스와 같은 동사를 사용 하지 마십시오.|
|[쓰기](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (wr)|대상에 정보를 추가 합니다. 이 동사는와 쌍을 이룹니다 `Read` .|이 작업의 경우 Put 또는 Print와 같은 동사를 사용 하지 마십시오.|

## <a name="data-verbs"></a>데이터 동사

PowerShell은 [VerbsData](/dotnet/api/System.Management.Automation.VerbsData) 클래스를 사용 하 여 데이터 처리에 적용 되는 작업을 정의 합니다. 다음 표에서는 대부분의 정의 된 동사를 보여 줍니다.

|동사 이름 (별칭)|작업|주석|
|-------------------------|------------|--------------|
|[백업](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|는 복제 하 여 데이터를 저장 합니다.|이 작업의 경우 저장, 굽기, 복제 또는 동기화와 같은 동사를 사용 하지 마십시오.|
|[검사점](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|데이터 또는 해당 구성의 현재 상태에 대 한 스냅숏을 만듭니다.|이 작업의 경우 Diff와 같은 동사를 사용 하지 마십시오.|
|[비교](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|다른 리소스의 데이터에 대해 한 리소스의 데이터를 평가 합니다.|이 작업의 경우 Diff와 같은 동사를 사용 하지 마십시오.|
|[압축](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|리소스의 데이터를 압축 합니다. 과 쌍 `Expand` .|이 작업의 경우 Compact와 같은 동사를 사용 하지 마십시오.|
|[Convert](/dotnet/api/System.Management.Automation.VerbsData.Convert) (cv)|Cmdlet이 양방향 변환을 지원 하거나 cmdlet이 여러 데이터 형식 간의 변환을 지 원하는 경우 한 표현의 데이터를 다른 표현으로 변경 합니다.|이 작업의 경우 변경, 크기 조정 또는 다시 샘플링과 같은 동사를 사용 하지 마십시오.|
|[Convertfrom-csv](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|입력의 한 가지 기본 형식 (cmdlet 명사는 입력을 나타냄)을 하나 이상의 지원 되는 출력 형식으로 변환 합니다.|이 작업의 경우 내보내기, 출력 또는 출력 등의 동사를 사용 하지 마십시오.|
|[Convertto-html](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|하나 이상의 입력 형식에서 기본 출력 형식으로 변환 합니다 (cmdlet 명사는 출력 형식을 나타냄).|이 작업의 경우에는 가져오기, 입력 또는와 같은 동사를 사용 하지 마십시오.|
|[분리](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|위치에서 명명 된 엔터티를 분리 합니다. 이 동사는와 쌍을 이룹니다 `Mount` .|이 작업의 경우 분리 또는 연결 해제와 같은 동사를 사용 하지 마십시오.|
|[편집](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|콘텐츠를 추가 하거나 제거 하 여 기존 데이터를 수정 합니다.|이 작업의 경우 변경, 업데이트 또는 수정 등의 동사를 사용 하지 마십시오.|
|[확장](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|원래 상태로 압축 된 리소스의 데이터를 복원 합니다. 이 동사는와 쌍을 이룹니다 `Compress` .|이 작업의 경우에는 분해 또는 압축 풀기와 같은 동사를 사용 하지 마십시오.|
|[내보내기](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|기본 입력을 파일 등의 영구 데이터 저장소 또는 교환 형식으로 캡슐화 합니다. 이 동사는와 쌍을 이룹니다 `Import` .|이 작업의 경우 Extract 또는 Backup과 같은 동사를 사용 하지 마십시오.|
|[그룹](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)|하나 이상의 리소스를 정렬 하거나 연결 합니다.|이 동작의 경우 집계, 정렬, 연결 또는 상관 관계와 같은 동사를 사용 하지 마십시오.|
|[가져오기](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|영구 데이터 저장소 (예: 파일) 또는 교환 형식에 저장 된 데이터에서 리소스를 만듭니다. 예를 들어 `Import-CSV` cmdlet은 CSV (쉼표로 구분 된 값) 파일에서 다른 cmdlet에 사용할 수 있는 개체로 데이터를 가져옵니다. 이 동사는와 쌍을 이룹니다 `Export` .|이 작업의 경우 BulkLoad 또는 Load와 같은 동사를 사용 하지 마십시오.|
|[Initialize](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|사용할 리소스를 준비 하 고 기본 상태로 설정 합니다.|이 작업을 수행 하려면 지우기, Init, 갱신, 다시 빌드, 다시 초기화 또는 설치와 같은 동사를 사용 하지 마십시오.|
|[제한](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|리소스에 제약 조건을 적용 합니다.|이 작업의 경우 할당량과 같은 동사를 사용 하지 마십시오.|
|[Merge](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|여러 리소스에서 단일 리소스를 만듭니다.|이 작업의 경우 Combine 또는 Join과 같은 동사를 사용 하지 마십시오.|
|[탑재](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|명명 된 엔터티를 위치에 연결 합니다. 이 동사는와 쌍을 이룹니다 `Dismount` .|이 작업의 경우 동사 연결을 사용 하지 마십시오.|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|환경에서 데이터를 보냅니다. 예를 들어 `Out-Printer` cmdlet은 프린터로 데이터를 보냅니다.||
|[게시](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|다른 사용자가 리소스를 사용할 수 있도록 합니다. 이 동사는와 쌍을 이룹니다 `Unpublish` .|이 작업의 경우 배포, 릴리스 또는 설치와 같은 동사를 사용 하지 마십시오.|
|[복원](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|리소스를에 설정 된 상태와 같은 미리 정의 된 상태로 설정 `Checkpoint` 합니다. 예를 들어 `Restore-Computer` cmdlet은 로컬 컴퓨터에서 시스템 복원을 시작 합니다.|이 작업의 경우 복구, 반환, 실행 취소, 수정 등의 동사를 사용 하지 마십시오.|
|[저장](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|데이터를 유지 하 여 손실을 방지 합니다.||
|[동기화](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|두 개 이상의 리소스가 동일한 상태임을 보장 합니다.|이 작업의 경우 복제, 강제 또는 일치와 같은 동사를 사용 하지 마십시오.|
|[게시 취소](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|리소스를 다른 사용자가 사용할 수 없게 만듭니다. 이 동사는와 쌍을 이룹니다 `Publish` .|이 작업의 경우 제거, 되돌리기 또는 숨기기와 같은 동사를 사용 하지 마십시오.|
|[업데이트](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|리소스를 최신 상태로 유지 하 여 상태, 정확성, 규칙 또는 규정 준수를 유지 합니다. 예를 들어 `Update-FormatData` cmdlet은 형식 지정 파일을 업데이트 하 고 현재 PowerShell 콘솔에 추가 합니다.|이 작업의 경우 새로 고침, 갱신, 다시 계산 또는 인덱스 다시 만들기와 같은 동사를 사용 하지 마십시오.|

## <a name="diagnostic-verbs"></a>진단 동사

PowerShell은 [VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) 클래스를 사용 하 여 진단에 적용 되는 작업을 정의 합니다. 다음 표에서는 대부분의 정의 된 동사를 보여 줍니다.

|동사 (별칭)|작업|주석|
|--------------------|------------|--------------|
|[디버그](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|리소스를 검사 하 여 운영 문제를 진단 합니다.|이 작업의 경우 진단과 같은 동사를 사용 하지 마십시오.|
|[측정](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (밀리초)|지정 된 작업에서 사용 하는 리소스를 식별 하거나 리소스에 대 한 통계를 검색 합니다.|이 작업의 경우 Calculate, 결정 또는 분석과 같은 동사를 사용 하지 마십시오.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|동사를 사용 `Test` 합니다.||
|[복구](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|리소스를 사용 가능한 조건으로 복원 합니다.|이 작업의 경우 수정 이나 복원과 같은 동사를 사용 하지 마십시오.|
|[해결](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|리소스의 약식 표현을 보다 완전 한 표현으로 매핑합니다.|이 작업의 경우 확장 또는 확인과 같은 동사를 사용 하지 마십시오.|
|[테스트](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|리소스의 작업 또는 일관성을 확인 합니다.|이 작업의 경우 진단, 분석, Salvage 또는 Verify와 같은 동사를 사용 하지 마십시오.|
|[추적](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|리소스의 작업을 추적 합니다.|이 작업의 경우 추적, 따르기, 검사 또는 자세히와 같은 동사를 사용 하지 마십시오.|

## <a name="lifecycle-verbs"></a>수명 주기 동사

PowerShell은 [VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 클래스를 사용 하 여 리소스의 수명 주기에 적용 되는 작업을 정의 합니다. 다음 표에서는 대부분의 정의 된 동사를 보여 줍니다.

|동사 (별칭)|작업|주석|
|--------------------|------------|--------------|
|[승인](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|리소스 또는 프로세스의 상태를 확인 하거나 동의 합니다.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (as)|리소스의 상태를은 합니다.|이 작업의 경우 인증 등의 동사를 사용 하지 마십시오.|
|[빌드](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|일부 입력 파일 집합 (일반적으로 소스 코드 또는 선언적 문서)에서 아티팩트 (일반적으로 이진 또는 문서)를 만듭니다.|이 동사는 PowerShell v6에 추가 되었습니다.|
|[완료](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|작업을 마칩니다.||
|[확인](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|리소스 또는 프로세스의 상태를 승인, 확인 또는 유효성을 검사 합니다.|이 작업의 경우 승인, 동의, 인증, 유효성 검사 또는 확인과 같은 동사를 사용 하지 마십시오.|
|[거부](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|리소스 또는 프로세스의 상태를 거부, 개체, 블록 또는 opposes 합니다.|이 작업의 경우 블록, 개체, 거부 또는 거부와 같은 동사를 사용 하지 마십시오.|
|[배포](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|배포가 완료 된 후 해당 솔루션의 소비자가 액세스할 수 있는 방식으로 응용 프로그램, 웹 사이트 또는 솔루션을 원격 대상 [s]에 보냅니다.|이 동사는 PowerShell v6에 추가 되었습니다.|
|[사용 안 함](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|리소스를 사용할 수 없거나 비활성 상태로 구성 합니다. 예를 들어 `Disable-PSBreakpoint` cmdlet은 중단점을 비활성 상태로 만듭니다. 이 동사는와 쌍을 이룹니다 `Enable` .|이 작업의 경우 중지 또는 숨기기와 같은 동사를 사용 하지 마십시오.|
|[사용](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|리소스를 사용 가능 또는 활성 상태로 구성 합니다. 예를 들어 `Enable-PSBreakpoint` cmdlet을 사용 하면 중단점이 활성화 됩니다. 이 동사는와 쌍을 이룹니다 `Disable` .|이 작업의 경우 Start 또는 Begin과 같은 동사를 사용 하지 마십시오.|
|[설치](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (is)|리소스를 위치에 배치 하 고 필요에 따라 초기화 합니다. 이 동사는와 쌍을 이룹니다 `Uninstall` .|이 작업의 경우 설치와 같은 동사를 사용 하지 마십시오.|
|[호출](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|명령 또는 메서드 실행과 같은 작업을 수행 합니다.|이 작업의 경우 실행 또는 시작과 같은 동사를 사용 하지 마십시오.|
|[등록](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|데이터베이스와 같은 리포지토리의 리소스에 대 한 항목을 만듭니다. 이 동사는와 쌍을 이룹니다 `Unregister` .||
|[요청](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (sysrq)|리소스를 요청 하거나 사용 권한을 요청 합니다.||
|[다시 시작](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|작업을 중지 한 다음 다시 시작 합니다. 예를 들어 `Restart-Service` cmdlet은 서비스를 중지 한 다음 시작 합니다.|이 작업의 경우에는 재활용과 같은 동사를 사용 하지 마십시오.|
|[다시 시작](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (r)|일시 중단 된 작업을 시작 합니다. 예를 들어 `Resume-Service` cmdlet은 일시 중단 된 서비스를 시작 합니다. 이 동사는와 쌍을 이룹니다 `Suspend` .||
|[시작](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|작업을 시작 합니다. 예를 들어 `Start-Service` cmdlet은 서비스를 시작 합니다. 이 동사는와 쌍을 이룹니다 `Stop` .|이 작업의 경우 시작, 시작 또는 부팅 같은 동사를 사용 하지 마십시오.|
|[중지](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|활동을 중단 합니다. 이 동사는와 쌍을 이룹니다 `Start` .|이 작업의 경우 End, Kill, Terminate 또는 Cancel과 같은 동사를 사용 하지 마십시오.|
|[제출](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|승인을 위한 리소스를 제공 합니다.|이 작업의 경우 Post와 같은 동사를 사용 하지 마십시오.|
|[일시 중단](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|작업을 일시 중지 합니다. 예를 들어 `Suspend-Service` cmdlet은 서비스를 일시 중지 합니다. 이 동사는와 쌍을 이룹니다 `Resume` .|이 작업의 경우 Pause와 같은 동사를 사용 하지 마십시오.|
|[제거](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|표시 된 위치에서 리소스를 제거 합니다. 이 동사는와 쌍을 이룹니다 `Install` .||
|[등록 취소](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (사용자)|리포지토리에서 리소스에 대 한 항목을 제거 합니다. 이 동사는와 쌍을 이룹니다 `Register` .|이 작업의 경우 Remove와 같은 동사를 사용 하지 마십시오.|
|[대기](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|지정 된 이벤트가 발생할 때까지 작업을 일시 중지 합니다. 예를 들어 `Wait-Job` cmdlet은 하나 이상의 백그라운드 작업이 완료 될 때까지 작업을 일시 중지 합니다.|이 작업의 경우에는 중지 또는 일시 중지와 같은 동사를 사용 하지 마십시오.|

## <a name="security-verbs"></a>보안 동사

PowerShell은 [VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) 클래스를 사용 하 여 보안에 적용 되는 작업을 정의 합니다. 다음 표에서는 대부분의 정의 된 동사를 보여 줍니다.

|동사 (별칭)|작업|주석|
|--------------------|------------|--------------|
|[블록](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|리소스에 대 한 액세스를 제한 합니다. 이 동사는와 쌍을 이룹니다 `Unblock` .|이 작업의 경우 방지, 제한 또는 거부와 같은 동사를 사용 하지 마십시오.|
|[Grant](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|리소스에 대 한 액세스를 허용 합니다. 이 동사는와 쌍을 이룹니다 `Revoke` .|이 작업의 경우 허용 또는 사용과 같은 동사를 사용 하지 마십시오.|
|[보호](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|공격 또는 손실 으로부터 리소스를 보호 합니다. 이 동사는와 쌍을 이룹니다 `Unprotect` .|이 작업의 경우 Encrypt, 보호책 또는 밀봉과 같은 동사를 사용 하지 마십시오.|
|[Revoke](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (날짜별)|리소스에 대 한 액세스를 허용 하지 않는 작업을 지정 합니다. 이 동사는와 쌍을 이룹니다 `Grant` .|이 작업의 경우 제거 또는 사용 안 함과 같은 동사를 사용 하지 마십시오.|
|[차단 해제](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|리소스에 대 한 제한을 제거 합니다. 이 동사는와 쌍을 이룹니다 `Block` .|이 작업의 경우 Clear 또는 Allow와 같은 동사를 사용 하지 마십시오.|
|[보호 해제](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (up)|공격 또는 손실을 방지 하기 위해 추가 된 리소스에서 보호 기능을 제거 합니다. 이 동사는와 쌍을 이룹니다 `Protect` .|이 작업의 경우 암호 해독 또는 봉인와 같은 동사를 사용 하지 마십시오.|

## <a name="other-verbs"></a>기타 동사

PowerShell은 [VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) 클래스를 사용 하 여 공통, 통신, 데이터, 수명 주기 또는 보안 동사 이름 동사와 같은 특정 동사 이름 범주에 맞지 않는 정식 동사 이름을 정의 합니다.

|동사 (별칭)|작업|주석|
|--------------------|------------|--------------|
|(U) [사용](/dotnet/api/System.Management.Automation.VerbsOther.Use)|또는를 사용 하 여 작업을 수행 하는 리소스를 포함 합니다.||

## <a name="see-also"></a>참고 항목

[VerbsCommon.](/dotnet/api/System.Management.Automation.VerbsCommon)

[VerbsCommunications.](/dotnet/api/System.Management.Automation.VerbsCommunications)

[VerbsData.](/dotnet/api/System.Management.Automation.VerbsData)

[VerbsDiagnostic.](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[VerbsLifeCycle.](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[VerbsSecurity.](/dotnet/api/System.Management.Automation.VerbsSecurity)

[VerbsOther.](/dotnet/api/System.Management.Automation.VerbsOther)

[Cmdlet 선언](./cmdlet-class-declaration.md)

[Windows PowerShell 프로그래머 가이드](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
