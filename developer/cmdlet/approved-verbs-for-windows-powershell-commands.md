---
title: PowerShell 명령에 대 한 승인 된 동사 | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: 4475b3f5e15826efbe8bab867011985cd7e2e1ae
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59293353"
---
# <a name="approved-verbs-for-powershell-commands"></a>PowerShell 명령에 대 한 승인 된 동사

PowerShell은 cmdlet의 이름 및 해당 파생된 Microsoft.NET Framework 클래스에 대 한 동사-명사 쌍을 사용합니다.
예를 들어를 `Get-Command` PowerShell에 등록 된 모든 명령을 검색 하려면 PowerShell에서 제공 하는 cmdlet을 사용 합니다.
이름의 동사 부분 cmdlet에서 수행 하는 작업을 식별 합니다.
작업을 수행 하는 엔터티를 식별 하는 이름의 명사 부분입니다.

> [!NOTE]
> 라는 용어를 사용 하는 PowerShell *동사* 해당 단어가 표준 동사는 영어로 작성에서 된 경우에 작업을 의미 하는 단어를 설명 합니다.
> 예를 들어 용어 *새로 만들기* 유효한 이름이 PowerShell 동사는 영어에서 동사가 되지 않더라도는 작업을 의미 하기 때문입니다.

## <a name="verb-naming-rules"></a>동사 명명 규칙

다음은 cmdlet 이름에 대 한 동사를 선택할 때 고려해 야 할 지침을 제공 합니다.

* 동사를 지정 하는 경우 PowerShell에서 제공 하는 미리 정의 된 동사 이름 중 하나를 사용 하는 것이 좋습니다 (다음 테이블에서 이러한 미리 정의 된 동사에 대 한 별칭이 포함 됨).
  미리 정의 된 동사를 사용 하면 사용자가 만든 cmdlet, PowerShell에서 제공 하는 cmdlet 및 다른 사용자가 설계 된 cmdlet 간에 일관성을 확인 합니다.

* 미리 정의 된 동사를 사용 하 여 작업의 일반 범위를 설명 하 고 cmdlet의 작업을 더 구체화 하려면 매개 변수를 사용 합니다.

* Cmdlet 간에 일관성을 적용 하려면 승인된 된 동사의 동의어를 사용 하지 마십시오.

* 이 항목에 나열 된 각 동사 형태의 사용 합니다.
  예를 들어, "Get"을 사용 하지만 "가져오기" 또는 "가져오는" 사용 하지 마십시오.

* 파스칼을 사용 하 여 대/소문자를 구분 하 여 동사에 대 한 합니다.
  파스칼식에서 각 단어의 첫 글자를 대/소문자는 대문자로 시작 "ForEach" 등입니다.

* 다음 예약 된 동사 또는 별칭을 사용 하지 마세요.
  이러한 동사는 PowerShell 언어에서 또는 PowerShell에서 제공 하는 특별 한 경우 cmdlet에서 사용 됩니다.
  - ForEach (foreach)
  - 형식 (f)
  - 그룹 (gp)
  - 정렬 (sr)
  - Tee (te)
  - 여기서 (wh)

## <a name="similar-verbs-for-different-actions"></a>다양 한 작업에 대 한 유사한 동사

다음 유사한 동사 다른 동작을 나타냅니다.

### <a name="new-vs-set"></a>새 vs입니다. Set(영문)
`New` 동사는 새 리소스를 만드는 데 사용 됩니다.
합니다 `Set` 동사는 없는와 같은 경우 필요에 따라 리소스를 만들기, 기존 리소스를 수정 하는 데는 `Set-Variable` cmdlet.

### <a name="find-vs-search"></a>Vs를 찾습니다. 검색
`Find` 동사 개체를 찾는 데 사용 됩니다.
`Search` 동사 컨테이너의 리소스에 대 한 참조를 만드는 데 사용 됩니다.

### <a name="get-vs-read"></a>Vs를 가져옵니다. 읽기
`Get` 파일과 같은 리소스를 검색 하려면 동사가 사용 됩니다.
`Read` 동사와 파일을 같은 원본에서 정보를 가져오는 데 사용 됩니다.

### <a name="invoke-vs-start"></a>Vs를 호출 합니다. 관리자 권한으로
`Invoke` 동사는 일반적으로 명령을 실행 하는 등의 작업을 동기 작업을 수행 하는 사용 됩니다.
`Start` 동사는 프로세스를 시작 하는 등 비동기 작업은 일반적으로 작업을 시작 하는 합니다.

### <a name="ping-vs-test"></a>Ping vs입니다. 테스트
사용 된 `Test` 동사입니다.

## <a name="common-verbs"></a>일반 동사

PowerShell 사용 하는 [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) 열거형 클래스는 거의 모든 cmdlet에 적용할 수 있는 일반 동작을 정의할 수 있습니다.
다음 표에서 대부분의 정의 된 동사를 나열합니다.

|동사 (별칭)|작업|설명|
|--------------------|------------|--------------|
|[추가](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|리소스 컨테이너를 추가 하거나 다른 항목에 항목을 연결 합니다. 예를 들어를 `Add-Content` cmdlet은 파일 콘텐츠를 추가 합니다. 이 동사 이룹니다 `Remove`합니다.|이 작업에 대 한 추가, 연결, 연결 등의 동사를 사용 하지 않거나 삽입 합니다.|
|[지우기](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|컨테이너에서 모든 리소스를 제거 하지만 컨테이너를 삭제 하지 않습니다. 예를 들어를 `Clear-Content` cmdlet은 파일의 내용을 제거 하지만 파일을 삭제 하지 않습니다.|이 작업에 대 한 플러시, 지우기, Release, Unmark, 설정 해제, 무효화 등 동사를 사용 하지 마십시오.|
|[닫기](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|액세스할 수 없거나 사용할 수 있도록 하는 리소스의 상태를 변경 합니다. 이 동사는와 연결 됩니다. `Open.`||
|[복사](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|다른 컨테이너 또는 다른 이름으로 리소스를 복사합니다. 예를 들어를 `Copy-Item` cmdlet 저장 된 데이터에 액세스 하는 데 사용 되는 데이터 저장소의 한 위치에서 다른 위치로 항목을 복사 합니다.|이 작업에 대 한 중복, 복제본, 복제 또는 동기화와 같은 동사를 사용 하지 마십시오.|
|[입력](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|리소스를 이동할 수 있도록 하는 동작을 지정 합니다. 예를 들어를 `Enter-PSSession` cmdlet은 대화형 세션에 사용자를 배치 합니다. 이 동사 이룹니다 `Exit`합니다.|이 작업에 대 한 또는 푸시와 같은 동사를 사용 하지 마십시오.|
|[종료](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (예:)|가장 최근에 사용 된 컨텍스트에 현재 환경 또는 컨텍스트를 설정합니다. 예를 들어를 `Exit-PSSession` cmdlet는 대화형 세션을 시작 하는 데 사용 된 세션에서 사용자를 배치 합니다. 이 동사 이룹니다 `Enter`합니다.|이 작업에 대 한 Pop 같은 또는 Out 동사를 사용 하지 마십시오.|
|[찾을](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|알 수 없는 명시적, 묵시적, 선택적 또는 지정 된 컨테이너에서 개체를 찾습니다.||
|[형식](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|지정 된 폼 또는 레이아웃에 있는 개체를 정렬합니다.||
|[가져올](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|리소스를 검색 하는 동작을 지정 합니다. 이 동사 이룹니다 `Set`합니다.|이 작업에 대 한 읽기, 열기, Cat, 형식, Dir, 가져오기, 덤프, 획득, 검사, 찾기 또는 검색 등의 동사를 사용 하지 마십시오.|
|[숨기기](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|리소스를 검색할 수 있습니다. 예를 들어, 이름이 숨기기 동사를 포함 하는 cmdlet 사용자 로부터 서비스를 숨길 수 있습니다. 이 동사 이룹니다 `Show`합니다.|이 작업에 대 한 블록과 같은 동사를 사용 하지 마십시오.|
|[조인](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|하나의 리소스에 리소스를 결합합니다. 예를 들어를 `Join-Path` cmdlet 단일 경로 만들려면 해당 자식 경로 중 하나를 사용 하 여 경로 결합 합니다. 이 동사 이룹니다 `Split`합니다.|이 작업에 대 한 결합, Unite, 연결, 연결 등의 동사를 사용 하지 마십시오.|
|[잠금](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|리소스를 보호합니다. 이 동사 이룹니다 `Unlock`합니다.|이 작업에 대 한 제한 또는 보안 등의 동사를 사용 하지 마십시오.|
|[이동](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|다른 곳에서 리소스를 이동합니다. 예를 들어를 `Move-Item` cmdlet는 데이터 저장소의 한 위치에서 항목을 다른 위치로 이동 합니다.|이 작업에 대 한 전송, 이름 또는 마이그레이션 등의 동사를 사용 하지 마십시오.|
|[새](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|리소스를 만듭니다. (합니다 `Set` 와 같은 데이터를 포함 하는 리소스를 만들 때에 동사를 사용할 수는 `Set-Variable` cmdlet입니다.)|이 작업에 대 한 만들기 "," 생성 "," 빌드 "," Make "또는" 할당 등의 동사를 사용 하지 마십시오.|
|[열기](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|액세스할 수, 사용할 수 없거나 사용할 수 있도록 하는 리소스의 상태를 변경 합니다. 이 동사 이룹니다 `Close`합니다.||
|[최적화](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|리소스의 효율성이 증가합니다.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|스택의 맨 위에서 항목을 제거합니다. 예를 들어를 `Pop-Location` cmdlet은 현재 위치를 가장 최근에 스택에 푸시된 위치로 변경 합니다.||
|[푸시](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|스택의 맨 위에 항목을 추가합니다. 예를 들어를 `Push-Location` cmdlet은 현재 위치를 스택에 푸시합니다.||
|[다시 실행](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (다시)|취소 된 상태로 리소스를 다시 설정 합니다.||
|[제거](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|컨테이너에서 리소스를 삭제합니다. 예를 들어를 `Remove-Variable` cmdlet 변수와 해당 값을 삭제 합니다. 이 동사 이룹니다 `Add`합니다.|이 작업에 대 한 이러한 동사를 사용 하 여 일반, 잘라내기, 무시 항목을 삭제 하거나 마십시오 지웁니다.|
|[이름 바꾸기](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn 이라고 가정)|리소스의 이름을 변경합니다. 예를 들어를 `Rename-Item` cmdlet에 사용 되는 저장 된 데이터에 액세스 하는 데이터 저장소에 있는 항목의 이름을 변경 합니다.|이 작업에 대 한 변경과 같은 동사를 사용 하지 마십시오.|
|[재설정](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|리소스를 원래 상태로 다시 설정합니다.||
|[검색](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|컨테이너의 리소스에 대 한 참조를 만듭니다.|이 작업에 대 한 찾기 또는 찾기 등의 동사를 사용 하지 마십시오.|
|[선택](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|컨테이너의 리소스를 찾습니다. 예를 들어를 `Select-String` cmdlet 문자열 및 파일에서 텍스트를 찾습니다.|이 작업에 대 한 찾기 또는 찾기 등의 동사를 사용 하지 마십시오.|
|[설정](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|기존 리소스에서 데이터를 교체 하거나 일부 데이터를 포함 하는 리소스를 만듭니다. 예를 들어를 `Set-Date` cmdlet은 로컬 컴퓨터의 시스템 시간을 변경 합니다. (의 `New` 동사 리소스 만들기를 사용할 수도 있습니다.) 이 동사 이룹니다 `Get`합니다.|이 작업에 대 한 쓰기, Reset, 할당, 또는 구성 등의 동사를 사용 하지 마십시오.|
|[표시](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|사용자에 게 표시 되도록 리소스를 만듭니다. 이 동사 이룹니다 `Hide`합니다.|이 작업에 대 한 표시 또는 생성 등의 동사를 사용 하지 마십시오.|
|[Skip](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|하나 이상의 리소스 또는 시퀀스의 요소를 무시합니다.|이 작업에 대 한 바이패스 등 점프 동사를 사용 하지 마십시오.|
|[분할](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|리소스 부분을 구분합니다. 예를 들어를 `Split-Path` cmdlet은 다른 부분 경로 반환 합니다. 이 동사 이룹니다 `Join`합니다.|이 작업을 사용 하지 마십시오 동사의 이러한 별도 합니다.|
|[단계](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|다음 지점 또는 순서로 리소스 이동 합니다.||
|[스위치](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|두 위치, 역할 또는 상태를 전환 하려면와 같은 두 리소스 간에 대체 하는 동작을 지정 합니다.||
|[실행 취소](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (un)|이전 상태로 리소스를 설정합니다.||
|[잠금 해제](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (영국)|잠긴 리소스를 해제 합니다. 이 동사 이룹니다 `Lock`합니다.|이 작업에 대 한 릴리스, Unrestrict, 또는 Unsecure와 같은 동사를 사용 하지 마십시오.|
|[조사식](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|지속적으로 검사 하거나 변경 내용에 대 한 리소스를 모니터링 합니다.||

## <a name="communications-verbs"></a>통신 동사

PowerShell을 사용 합니다 [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) 통신에 적용 되는 동작을 정의 하는 클래스입니다.
다음 표에서 대부분의 정의 된 동사를 나열합니다.

|동사 (별칭)|작업|설명|
|--------------------|------------|--------------|
|[연결](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|원본과 대상 간의 링크를 만듭니다. 이 동사 이룹니다 `Disconnect`합니다.|이 작업에 대 한 조인 또는 텔넷 등의 동사를 사용 하지 마십시오.|
|[연결 끊기](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|원본과 대상 간에 연결을 끊습니다. 이 동사 이룹니다 `Connect`합니다.|이 작업에 대 한 중단 또는 로그 오프 하는 등의 동사를 사용 하지 마십시오.|
|[읽기](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|원본에서 정보를 가져옵니다. 이 동사 이룹니다 `Write`합니다.|이 작업에 대 한 프롬프트를 획득와 같은 동사를 사용 하지 않거나 가져옵니다.|
|[수신](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|원본에서 전송 되는 정보를 허용 합니다. 이 동사 이룹니다 `Send`합니다.|이 작업에 대 한 읽기, Accept와 같은 동사를 사용 하지 않거나 보기.|
|[보낼](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|대상 정보를 제공 합니다. 이 동사 이룹니다 `Receive`합니다.|이 작업에 대 한 Put, 브로드캐스트, 메일, 팩스 등 동사를 사용 하지 마십시오.|
|[쓰기](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (쓰기)|대상 정보를 추가합니다. 이 동사 이룹니다 `Read`합니다.|이 작업에 대 한 Put 또는 인쇄와 같은 동사를 사용 하지 마십시오.|

## <a name="data-verbs"></a>데이터 동사

PowerShell을 사용 합니다 [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) 데이터 처리에 적용 되는 동작을 정의 하는 클래스입니다.
다음 표에서 대부분의 정의 된 동사를 나열합니다.

|동사 이름 (별칭)|작업|설명|
|-------------------------|------------|--------------|
|[백업](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|복제 하 여 데이터를 저장 합니다.|이 작업에 대 한 저장, Burn, 복제 또는 동기화와 같은 동사를 사용 하지 마십시오.|
|[검사점](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|데이터 또는 해당 구성의 현재 상태의 스냅숏을 만듭니다.|이 작업에 대 한 차이 같은 동사를 사용 하지 마십시오|
|[비교](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|다른 리소스에서 데이터에 대해 하나의 리소스에서 데이터를 평가 합니다.|이 작업에 대 한 차이 같은 동사를 사용 하지 마십시오|
|[압축](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|리소스의 데이터를 압축합니다. 쌍 `Expand`합니다.|이 작업에 대 한 Compact와 같은 동사를 사용 하지 마십시오.|
|[변환](/dotnet/api/System.Management.Automation.VerbsData.Convert) (cv)|변경 데이터의 표현을 다른 cmdlet에서 양방향 변환을 지 원하는 경우 cmdlet은 여러 데이터 형식 간의 변환만 지원 됩니다.|이 작업에 대 한 변경, 크기 조정 등의 동사를 사용 하지 않거나 다시 샘플링 합니다.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|한 가지 기본 유형의 입력 (cmdlet 명사 입력을 나타냄) 하나 이상의 지원 되는 출력 형식으로 변환 합니다.|이 작업에 대 한 내보내기, 출력 또는 초과 같은 동사를 사용 하지 마십시오.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|하나 이상의 유형의 입력 (cmdlet 명사 출력 종류를 나타냄)을 기본 출력 형식에서 변환 합니다.|이 작업을 사용 하지 마십시오 가져오기 등의 동사 입력 또는 합니다.|
|[분리](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|위치에서 명명된 된 엔터티를 분리합니다. 이 동사 이룹니다 `Mount`합니다.|이 작업에 대 한 분리 또는 연결 끊기와 같은 동사를 사용 하지 마십시오.|
|[편집](/dotnet/api/System.Management.Automation.VerbsData.Edit) (교육)|추가 하거나 콘텐츠를 제거 하 여 기존 데이터를 수정 합니다.|이 작업에 대 한 변경, 업데이트 또는 수정 등의 동사를 사용 하지 마십시오.|
|[확장](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|압축 된 리소스의 데이터를 원래 상태로 복원 합니다. 이 동사 이룹니다 `Compress`합니다.|이 작업에 대 한 분해 등 압축 되지 않은 동사를 사용 하지 마십시오.|
|[내보내기](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|기본 입력 파일을 같은 영구 데이터 저장소에 또는 교환 형식으로 캡슐화합니다. 이 동사 이룹니다 `Import`합니다.|이 작업에 대 한 추출 또는 백업 등의 동사를 사용 하지 마십시오.|
|[그룹](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)|정렬 또는 하나 이상의 리소스를 연결 합니다.|이 작업에 대 한 집계, 정렬, 연결 등의 동사를 사용 하지 않거나 상관 관계를 지정 합니다.|
|[가져오기](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|(예: 파일)는 영구 데이터 저장소 또는 교환 형식으로 저장 된 데이터에서 리소스를 만듭니다. 예를 들어를 `Import-CSV` cmdlet은 다른 cmdlet에서 사용할 수 있는 개체에 쉼표로 구분 된 값 (CSV) 파일에서 데이터를 가져옵니다. 이 동사 이룹니다 `Export`합니다.|이 작업에 대 한 BulkLoad 또는 Load와 같은 동사를 사용 하지 마십시오.|
|[초기화](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|기본 상태로 설정 및 사용에 대 한 리소스를 준비 합니다.|이 작업에 대 한 지우기, Init, 갱신, 다시 작성, 다시 초기화, 또는 설치와 같은 동사를 사용 하지 마십시오.|
|[제한](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|리소스 제한이 적용 됩니다.|이 작업에 대 한 할당량와 같은 동사를 사용 하지 마십시오.|
|[병합](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|여러 리소스에서 단일 리소스를 만듭니다.|이 작업에 대 한 결합 또는 조인 등의 동사를 사용 하지 마십시오.|
|[탑재](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|위치에 있는 명명 된 엔터티를 연결합니다. 이 동사 이룹니다 `Dismount`합니다.|이 작업에 대 한 연결 된 동사를 사용 하지 마십시오.|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|환경에서 데이터를 보냅니다. 예를 들어를 `Out-Printer` cmdlet은 프린터에 데이터를 보냅니다.||
|[게시](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|다른 사용자에 게 사용 가능한 리소스를 만듭니다. 이 동사 이룹니다 `Unpublish`합니다.|이 작업에 대 한 릴리스를 배포와 같은 동사를 사용 하지 않거나 설치 합니다.|
|[복원](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|리소스 설정 된 상태와 같은 미리 정의 된 상태로 설정 `Checkpoint`합니다. 예를 들어를 `Restore-Computer` cmdlet은 로컬 컴퓨터에서 시스템 복원을 시작 합니다.|이 작업에 대 한 복구, Return, 실행 취소 또는 수정 등의 동사를 사용 하지 마십시오.|
|[저장](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|데이터 손실을 방지 하기 위해 유지 됩니다.||
|[동기화](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|두 개 이상의 리소스가 동일한 상태를 보장 합니다.|이 작업에 대 한 복제를 강제와 같은 동사를 사용 하지 않거나 일치 합니다.|
|[게시 취소](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|리소스를 하면 다른 사용자에 게 사용할 수 없게 합니다. 이 동사 이룹니다 `Publish`합니다.|이 작업에 대 한 제거, 되돌리기 등의 동사를 사용 하지 않거나 숨기기.|
|[업데이트](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|해당 상태, 정확도, 준수 또는 규정 준수를 유지 하기 위해 최신 리소스를 제공 합니다. 예를 들어를 `Update-FormatData` cmdlet 업데이트 하 고 현재 PowerShell 콘솔에 형식 지정 파일을 추가 합니다.|이 작업에 대 한 새로 고침, 갱신, 다시 계산 등의 동사를 사용 하지 않거나 인덱스를 다시 합니다.|

## <a name="diagnostic-verbs"></a>진단 동사

PowerShell을 사용 합니다 [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) 진단에 적용 되는 동작을 정의 하는 클래스입니다.
다음 표에서 대부분의 정의 된 동사를 나열합니다.

|동사 (별칭)|작업|설명|
|--------------------|------------|--------------|
|[디버그](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|운영 문제를 진단 하는 리소스를 검사 합니다.|이 작업에 대 한 진단 같은 동사를 사용 하지 마십시오.|
|[측정값](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|지정된 된 작업에서 사용 되는 리소스를 식별 하거나 리소스에 대 한 통계를 검색 합니다.|이 작업에 대 한 계산, 확인, 또는 분석 등의 동사를 사용 하지 마십시오.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|사용 된 `Test` 동사입니다.||
|[복구](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|사용 가능한 조건으로 리소스를 복원합니다.|이 작업에 대 한 수정 또는 Restore와 같은 동사를 사용 하지 마십시오.|
|[해결](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|리소스의 약식 표현을 더 완전 한 표현이 매핑됩니다.|이 작업에 대 한 확장 또는 확인 등의 동사를 사용 하지 마십시오.|
|[테스트](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|작업 또는 리소스의 일관성을 확인합니다.|이 작업에 대 한 진단, 분석, 복원 또는 확인 등의 동사를 사용 하지 마십시오.|
|[추적](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|리소스의 작업을 추적 합니다.|이 작업에 대 한 추적에서 다음을 검사와 같은 동사를 사용 하지 않거나 알아볼 차례입니다.|

## <a name="lifecycle-verbs"></a>수명 주기 동사

PowerShell을 사용 합니다 [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 리소스의 수명 주기에 적용 되는 작업을 정의 하는 클래스입니다.
다음 표에서 대부분의 정의 된 동사를 나열합니다.

|동사 (별칭)|작업|설명|
|--------------------|------------|--------------|
|[승인](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|확인 하거나 리소스 또는 프로세스의 상태에 동의 해야 합니다.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (로)|리소스의 상태를 수행 합니다.|이 작업에 대 한 Certify와 같은 동사를 사용 하지 마십시오.|
|[빌드](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|입력된 파일 (일반적으로 소스 코드 또는 선언적 문서)의 일부 집합에서 아티팩트 (일반적으로 이진 또는 문서)를 만듭니다.|이 동사 PowerShell v6에 추가 되었습니다.|
|[전체](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|작업을 완료 했습니다.||
|[확인](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|승인, 확인 또는 리소스 또는 프로세스의 상태를 검사 합니다.|이 작업에 대 한 승인, 동의 Certify, 유효성 검사, 또는 확인 등의 동사를 사용 하지 마십시오.|
|[거부](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|거부, 개체, 블록 또는 opposes 리소스 또는 프로세스의 상태입니다.|이 작업에 대 한 개체 블록 거부와 같은 동사를 사용 하지 않거나 거부 합니다.|
|[배포](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|이러한 방식으로 해당 솔루션의 소비자는 액세스할 수 있도록 해당 배포가 완료 된 후 원격 대상 [s]에 응용 프로그램, 웹 사이트 또는 솔루션을 보냅니다.|이 동사 PowerShell v6에 추가 되었습니다.|
|[사용 하지 않도록 설정](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|리소스를 사용할 수 없거나 비활성 상태를 구성합니다. 예를 들어를 `Disable-PSBreakpoint` cmdlet는 중단점을 비활성화 합니다. 이 동사 이룹니다 `Enable`합니다.|이 작업에 대 한 중단 또는 숨기기와 같은 동사를 사용 하지 마십시오.|
|[사용 하도록 설정](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|리소스를 사용할 수 없거나 활성 상태를 구성합니다. 예를 들어를 `Enable-PSBreakpoint` cmdlet은 중단점을 활성화 합니다. 이 동사 이룹니다 `Disable`합니다.|이 작업에 대 한 시작 또는 시작 등의 동사를 사용 하지 마십시오.|
|[설치](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (는)|리소스 위치에 배치 하 고 필요에 따라이 초기화 합니다. 이 동사 이룹니다 `Uninstall`합니다.|이 작업을 사용 하 여 동사를 설정과 같은 하지를 수행 합니다.|
|[호출](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|명령이 나 메서드를 실행 하는 등의 작업을 수행 합니다.|이 작업에 대 한 실행 또는 시작 등의 동사를 사용 하지 마십시오.|
|[등록](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|데이터베이스와 같은 리포지토리에서 리소스에 대 한 항목을 만듭니다. 이 동사 이룹니다 `Unregister`합니다.||
|[요청](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|리소스를 요청 하거나 권한을 요청 합니다.||
|[다시 시작](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|작업을 중지 하 고 다시 시작 합니다. 예를 들어를 `Restart-Service` cmdlet 중지 한 후 서비스를 시작 합니다.|이 작업에 대 한 재활용 같은 동사를 사용 하지 마십시오.|
|[다시 시작](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|일시 중단 된 작업을 시작 합니다. 예를 들어를 `Resume-Service` cmdlet은 일시 중단 된 서비스를 시작 합니다. 이 동사 이룹니다 `Suspend`합니다.||
|[시작](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|작업을 시작합니다. 예를 들어를 `Start-Service` cmdlet은 서비스를 시작 합니다. 이 동사 이룹니다 `Stop`합니다.|이 작업에 대 한 시작, 시작, 또는 부팅 등의 동사를 사용 하지 마십시오.|
|[중지](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|작업을 중단합니다. 이 동사 이룹니다 `Start`합니다.|이 작업에 대 한 끝, 중지, 종료와 같은 동사를 사용 하지 않거나 취소 합니다.|
|[제출](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|승인에 대 한 리소스를 제공합니다.|이 작업에 대 한 예: Post 동사를 사용 하지 마십시오.|
|[일시 중단](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|활동을 일시 중지합니다. 예를 들어를 `Suspend-Service` cmdlet는 서비스를 일시 중지 합니다. 이 동사 이룹니다 `Resume`합니다.|이 작업에 대 한 일시 중지와 같은 동사를 사용 하지 마십시오.|
|[제거](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|지정 된 위치에서 리소스를 제거합니다. 이 동사 이룹니다 `Install`합니다.||
|[등록을 취소](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (프로그램)|저장소에서 리소스에 대 한 항목을 제거합니다. 이 동사 이룹니다 `Register`합니다.|이 작업에 대 한 제거와 같은 동사를 사용 하지 마십시오.|
|[대기](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|지정된 된 이벤트가 발생할 때까지 작업을 일시 중지 합니다. 예를 들어를 `Wait-Job` cmdlet 하나까지 작업을 일시 중지 또는 이상의 백그라운드 작업을 완료 합니다.|이 작업에 대 한 중지 또는 일시 중지와 같은 동사를 사용 하지 마십시오.|

## <a name="security-verbs"></a>보안 동사

PowerShell을 사용 합니다 [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) 보안에 적용 되는 동작을 정의 하는 클래스입니다.
다음 표에서 대부분의 정의 된 동사를 나열합니다.

|동사 (별칭)|작업|설명|
|--------------------|------------|--------------|
|[블록](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|리소스에 대 한 액세스를 제한합니다. 이 동사 이룹니다 `Unblock`합니다.|이 작업에 대 한 사용 안 함, 제한 또는 거부와 같은 동사를 사용 하지 마십시오.|
|[권한 부여](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|리소스에 액세스할 수 있습니다. 이 동사 이룹니다 `Revoke`합니다.|이 작업에 대 한 허용 또는 같은 동사를 사용 하지 마십시오.|
|[보호](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|공격 또는 손실 로부터 리소스를 보호합니다. 이 동사 이룹니다 `Unprotect`합니다.|이 작업에 대 한 암호화, 보호, 또는 봉인와 같은 동사를 사용 하지 마십시오.|
|[Revoke](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (날짜별)|리소스에 대 한 액세스를 허용 하지 않는 동작을 지정 합니다. 이 동사 이룹니다 `Grant`합니다.|이 작업에 대 한 제거 하거나 사용 하지 않도록 설정 등의 동사를 사용 하지 마십시오.|
|[차단 해제](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|리소스에 대 한 제한을 제거합니다. 이 동사 이룹니다 `Block`합니다.|이 작업에 대 한 허용 또는 지우기와 같은 동사를 사용 하지 마십시오.|
|[보호를 해제할](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (최대)|공격 또는 손실을 방지 하기 위해 추가 된 리소스에서 보호를 제거 합니다. 이 동사 이룹니다 `Protect`합니다.|이 작업에 대 한 암호 해독 등 Unseal 동사를 사용 하지 마십시오.|

## <a name="other-verbs"></a>기타 동사

PowerShell을 사용 합니다 [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) 일반적인, 통신, 데이터, 수명 주기와 같은 특정 동사 이름 범주에 맞지 않는 정식 동사 이름 또는 보안 동사 이름 정의 하는 클래스 동사입니다.

|동사 (별칭)|작업|설명|
|--------------------|------------|--------------|
|[사용 하 여](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|사용 하거나 작업을 수행 하는 리소스를 포함 합니다.||

## <a name="see-also"></a>참고 항목

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Cmdlet은 선언](./cmdlet-class-declaration.md)

[Windows PowerShell 프로그래머 가이드](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
