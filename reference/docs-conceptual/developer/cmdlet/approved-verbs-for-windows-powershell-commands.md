---
ms.date: 09/07/2018
ms.topic: reference
title: PowerShell 명령에 승인된 동사
description: PowerShell 명령에 승인된 동사
ms.openlocfilehash: fc1ff989ae86862e0f9cc24d8bcba2ff02ef68cc
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355105"
---
# <a name="approved-verbs-for-powershell-commands"></a>PowerShell 명령에 승인된 동사

PowerShell은 cmdlet 이름 및 파생된 .NET 클래스에 동사-명사 쌍을 사용합니다.
이름의 동사 부분은 cmdlet이 수행하는 작업을 식별합니다. 이름의 명사 부분은 작업을 수행하는 엔터티를 식별합니다. 예를 들어 `Get-Command` cmdlet은 PowerShell에 등록된 모든 명령을 검색합니다.

> [!NOTE]
> PowerShell은 영어의 표준 동사가 아닌 경우에도 작업을 의미하는 단어를 설명하기 위해 _동사_ 라는 용어를 사용합니다. 예를 들어 _New_ 라는 용어는 영어의 동사가 아니지만 작업을 암시하므로 유효한 PowerShell 동사 이름입니다.

승인된 각 동사에는 해당하는 _별칭 접두사_ 가 정의되어 있습니다. 이 별칭 접두사는 해당 동사를 사용하는 명령의 별칭으로 사용됩니다. 예를 들어 `Import`의 별칭 접두사는 `ip`이며, 따라서 `Import-Module`의 별칭 접두사는 `ipmo`입니다. 이는 권장 사항이지 규칙은 아닙니다. 특히 다른 환경에서 잘 알려진 명령을 모방하는 명령 별칭에는 이 권장 사항을 사용할 필요가 없습니다.

## <a name="verb-naming-recommendations"></a>동사 명명 권장 사항

다음 권장 사항은 자신이 만드는 cmdlet, PowerShell에서 제공하는 cmdlet, 다른 사용자가 디자인하는 cmdlet 간의 일관성을 보장하기 위해 cmdlet에서 적절한 동사를 선택하는 데 도움이 됩니다.

- PowerShell에서 제공하는 미리 정의된 동사 이름 중 하나를 사용합니다.
- 동사를 사용하여 작업의 일반 범위를 설명하고, 매개 변수를 사용하여 cmdlet의 작업을 추가로 구체화합니다.
- 승인된 동사의 동의어를 사용하지 않습니다. 예를 들어 항상 `Remove`를 사용하되, `Delete` 또는 `Eliminate`를 사용하지 않습니다.
- 이 항목에 나열된 각 동사의 형식만 사용합니다. 예를 들어 `Get`을 사용하되, `Getting` 또는 `Gets`를 사용하지 않습니다.
- 다음과 같은 예약된 동사 또는 별칭을 사용하지 않습니다. PowerShell 언어 또는 드물지만 이 cmdlet 중 일부는 예외적인 상황에서 이러한 동사를 사용합니다.
  - ForEach(foreach)
  - [Format](/dotnet/api/System.Management.Automation.VerbsCommon.Format)(f): 지정된 양식 또는 레이아웃의 개체를 정렬합니다.
  - [Group](/dotnet/api/System.Management.Automation.VerbsData.Group)(gp): 하나 이상의 리소스를 정렬하거나 연결합니다.
  - [Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping)(pi)
  - Sort(sr)
  - Tee(te)
  - Where(wh)

동사의 전체 목록을 보려면 `Get-Verb` cmdlet을 사용할 수 있습니다.

## <a name="similar-verbs-for-different-actions"></a>서로 다른 작업을 나타내는 유사한 동사

다음의 유사한 동사는 서로 다른 작업을 나타냅니다.

### <a name="new-vs-set"></a>New와 설정

새 리소스를 만들려면 `New` 동사를 사용합니다. 기존 리소스를 수정하려면 `Set` 동사를 사용합니다. 리소스가 존재하지 않는 경우 필요에 따라 만들 수 있습니다(예: `Set-Variable` cmdlet).

### <a name="find-vs-search"></a>Find와 검색

개체를 찾으려면 `Find` 동사를 사용합니다. 컨테이너의 리소스에 대한 참조를 만들려면 `Search` 동사를 사용합니다.

### <a name="get-vs-read"></a>Get과 읽기

리소스(예: 파일)에 대한 정보를 얻거나 나중에 리소스에 액세스하는 데 사용할 개체를 가져오려면 `Get` 동사를 사용합니다. 리소스를 열고 내부에 포함된 정보를 추출하려면 `Read` 동사를 사용합니다.

### <a name="invoke-vs-start"></a>Invoke와 시작

명령을 실행하고 종료를 기다리는 등의 동기 작업을 수행하려면 `Invoke` 동사를 사용합니다. 자율 프로세스 시작과 같은 비동기 작업을 시작하려면 `Start` 동사를 사용합니다.

### <a name="ping-vs-test"></a>Ping과 테스트

`Test` 동사를 사용합니다.

## <a name="common-verbs"></a>일반 동사

PowerShell은 [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) 열거형 클래스를 사용하여 거의 모든 cmdlet에 적용할 수 있는 일반 작업을 정의합니다. 다음 표에는 정의된 대부분의 동사가 나열되어 있습니다.

|동사(별칭)|작업|피해야 할 동의어|
|--------------------|------------|--------------|
|[Add](/dotnet/api/System.Management.Automation.VerbsCommon.Add)(a)|컨테이너에 리소스를 추가하거나 한 항목을 다른 항목에 연결합니다. 예를 들어 `Add-Content` cmdlet은 파일에 콘텐츠를 추가합니다. 이 동사는 `Remove`와 쌍을 이룹니다.|Append, Attach, Concatenate, Insert|
|[Clear](/dotnet/api/System.Management.Automation.VerbsCommon.Clear)(cl)|컨테이너에서 모든 리소스를 제거하지만 컨테이너는 삭제하지 않습니다. 예를 들어 `Clear-Content` cmdlet은 파일의 내용을 제거하지만 파일은 삭제하지 않습니다.|Flush, Erase, Release, Unmark, Unset, Nullify|
|[Close](/dotnet/api/System.Management.Automation.VerbsCommon.Close)(cs)|액세스할 수 없거나 사용할 수 없도록 리소스의 상태를 변경합니다. 이 동사는 `Open.`과 쌍을 이룹니다.||
|[Copy](/dotnet/api/System.Management.Automation.VerbsCommon.Copy)(cp)|다른 이름이나 다른 컨테이너로 리소스를 복사합니다. 예를 들어 `Copy-Item` cmdlet은 데이터 저장소의 한 위치에서 다른 위치로 항목(예: 파일)을 복사합니다.|Duplicate, Clone, Replicate, Sync|
|[Enter](/dotnet/api/System.Management.Automation.VerbsCommon.Enter)(et)|사용자가 리소스로 이동하도록 허용하는 작업을 지정합니다. 예를 들어 `Enter-PSSession` cmdlet은 사용자를 대화형 세션으로 이동합니다. 이 동사는 `Exit`와 쌍을 이룹니다.|Push, Into|
|[Exit](/dotnet/api/System.Management.Automation.VerbsCommon.Exit)(ex)|현재 환경 또는 컨텍스트를 가장 최근에 사용한 컨텍스트로 설정합니다. 예를 들어 `Exit-PSSession` cmdlet은 사용자를 대화형 세션을 시작하는 데 사용된 세션으로 이동합니다. 이 동사는 `Enter`와 쌍을 이룹니다.|Pop, Out|
|[Find](/dotnet/api/System.Management.Automation.VerbsCommon.Find)(fd)|알 수 없거나, 암시적이거나, 선택적이거나, 지정된 개체를 컨테이너에서 찾습니다.|검색|
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get)(g)|리소스를 검색하는 작업을 지정합니다. 이 동사는 `Set`와 쌍을 이룹니다.|Read, Open, Cat, Type, Dir, Obtain, Dump, Acquire, Examine, Find, Search|
|[Hide](/dotnet/api/System.Management.Automation.VerbsCommon.Hide)(h)|리소스를 감지할 수 없게 만듭니다. 예를 들어 이름에 Hide 동사가 포함된 cmdlet은 사용자에게 서비스를 숨길 수 있습니다. 이 동사는 `Show`와 쌍을 이룹니다.|차단|
|[Join](/dotnet/api/System.Management.Automation.VerbsCommon.Join)(j)|여러 리소스를 하나의 리소스로 결합합니다. 예를 들어 `Join-Path` cmdlet은 경로를 자식 경로 중 하나와 결합하여 단일 경로를 만듭니다. 이 동사는 `Split`와 쌍을 이룹니다.|Combine, Unite, Connect, Associate|
|[Lock](/dotnet/api/System.Management.Automation.VerbsCommon.Lock)(lk)|리소스를 보호합니다. 이 동사는 `Unlock`과 쌍을 이룹니다.|Restrict, Secure|
|[Move](/dotnet/api/System.Management.Automation.VerbsCommon.Move)(m)|리소스를 한 위치에서 다른 위치로 이동합니다. 예를 들어 `Move-Item` cmdlet은 데이터 저장소의 한 위치에서 다른 위치로 항목을 이동합니다.|Transfer, Name, Migrate|
|[New](/dotnet/api/System.Management.Automation.VerbsCommon.New)(n)|리소스를 만듭니다. `Set-Variable` cmdlet과 같이 데이터를 포함하는 리소스를 만들 때에도 `Set` 동사를 사용할 수 있습니다.|Create, Generate, Build, Make, Allocate|
|[Open](/dotnet/api/System.Management.Automation.VerbsCommon.Open)(op)|액세스할 수 있거나 사용할 수 있도록 리소스의 상태를 변경합니다. 이 동사는 `Close`와 쌍을 이룹니다.||
|[Optimize](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize)(om)|리소스의 효과를 높입니다.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop)(pop)|스택의 맨 위에서 항목을 제거합니다. 예를 들어 `Pop-Location` cmdlet은 현재 위치를 가장 최근에 스택에 푸시한 위치로 변경합니다.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push)(pu)|스택의 맨 위에 항목을 추가합니다. 예를 들어 `Push-Location` cmdlet은 현재 위치를 스택에 푸시합니다.||
|[Redo](/dotnet/api/System.Management.Automation.VerbsCommon.Redo)(re)|리소스를 실행 취소된 상태로 다시 설정합니다.||
|[Remove](/dotnet/api/System.Management.Automation.VerbsCommon.Remove)(r)|컨테이너에서 리소스를 삭제합니다. 예를 들어 `Remove-Variable` cmdlet은 변수와 해당 값을 삭제합니다. 이 동사는 `Add`와 쌍을 이룹니다.|Clear, Cut, Dispose, Discard, Erase|
|[Rename](/dotnet/api/System.Management.Automation.VerbsCommon.Rename)(rn)|리소스의 이름을 변경합니다. 예를 들어 저장된 데이터에 액세스하는 데 사용되는 `Rename-Item` cmdlet은 데이터 저장소에 있는 항목의 이름을 변경합니다.|변경|
|[Reset](/dotnet/api/System.Management.Automation.VerbsCommon.Reset)(rs)|리소스를 다시 원래 상태로 설정합니다.||
|[Resize](/dotnet/api/System.Management.Automation.VerbsCommon.Resize)(rz)|리소스의 크기를 변경합니다.||
|[Search](/dotnet/api/System.Management.Automation.VerbsCommon.Search)(sr)|컨테이너의 리소스에 대한 참조를 만듭니다.|Find, Locate|
|[Select](/dotnet/api/System.Management.Automation.VerbsCommon.Select)(sc)|컨테이너에서 리소스를 찾습니다. 예를 들어 `Select-String` cmdlet은 문자열 및 파일에서 텍스트를 찾습니다.|Find, Locate|
|[Set](/dotnet/api/System.Management.Automation.VerbsCommon.Set)(s)|기존 리소스의 데이터를 대체하거나 일부 데이터를 포함하는 리소스를 만듭니다. 예를 들어 `Set-Date` cmdlet은 로컬 컴퓨터의 시스템 시간을 변경합니다. (`New` 동사를 사용하여 리소스를 만들 수도 있습니다.) 이 동사는 `Get`과 쌍을 이룹니다.|Write, Reset, Assign, Configure|
|[Show](/dotnet/api/System.Management.Automation.VerbsCommon.Show)(sh)|사용자에게 리소스를 표시합니다. 이 동사는 `Hide`와 쌍을 이룹니다.|Display, Produce|
|[Skip](/dotnet/api/System.Management.Automation.VerbsCommon.Skip)(sk)|시퀀스에서 하나 이상의 리소스나 포인트를 바이패스합니다.|Bypass, Jump|
|[Split](/dotnet/api/System.Management.Automation.VerbsCommon.Split)(sl)|리소스의 일부를 분리합니다. 예를 들어 `Split-Path` cmdlet은 경로의 다른 부분을 반환합니다. 이 동사는 `Join`과 쌍을 이룹니다.|별도|
|[Step](/dotnet/api/System.Management.Automation.VerbsCommon.Step)(st)|시퀀스의 다음 포인트 또는 리소스로 이동합니다.||
|[Switch](/dotnet/api/System.Management.Automation.VerbsCommon.Switch)(sw)|두 개의 위치, 책임 또는 상태 간에 변경하는 등 두 리소스 간에 대체되는 작업을 지정합니다.||
|[Undo](/dotnet/api/System.Management.Automation.VerbsCommon.Undo)(un)|리소스를 이전 상태로 설정합니다.||
|[Unlock](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock)(uk)|잠긴 리소스를 해제합니다. 이 동사는 `Lock`과 쌍을 이룹니다.|Release, Unrestrict, Unsecure|
|[Watch](/dotnet/api/System.Management.Automation.VerbsCommon.Watch)(wc)|지속적으로 리소스를 검사하거나 변경을 모니터링합니다.||

## <a name="communications-verbs"></a>통신 동사

PowerShell은 [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) 클래스를 사용하여 통신에 적용되는 작업을 정의합니다. 다음 표에는 정의된 대부분의 동사가 나열되어 있습니다.

|동사(별칭)|작업|피해야 할 동의어|
|--------------------|------------|--------------|
|[Connect](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect)(cc)|원본 및 대상 간에 링크를 만듭니다. 이 동사는 `Disconnect`와 쌍을 이룹니다.|Join, Telnet|
|[Disconnect](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect)(dc)|원본과 대상 간의 링크를 끊습니다. 이 동사는 `Connect`와 쌍을 이룹니다.|Break, Logoff|
|[Read](/dotnet/api/System.Management.Automation.VerbsCommunications.Read)(rd)|원본에서 정보를 가져옵니다. 이 동사는 `Write`와 쌍을 이룹니다.|Acquire, Prompt, Get|
|[Receive](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive)(rc)|원본에서 전송된 정보를 수락합니다. 이 동사는 `Send`와 쌍을 이룹니다.|Read, Accept, Peek|
|[Send](/dotnet/api/System.Management.Automation.VerbsCommunications.Send)(sd)|대상에 정보를 전달합니다. 이 동사는 `Receive`와 쌍을 이룹니다.|Put, Broadcast, Mail, Fax|
|[Write](/dotnet/api/System.Management.Automation.VerbsCommunications.Write)(wr)|대상에 정보를 추가합니다. 이 동사는 `Read`와 쌍을 이룹니다.|Put, Print|

## <a name="data-verbs"></a>데이터 동사

PowerShell은 [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) 클래스를 사용하여 데이터 처리에 적용되는 작업을 정의합니다. 다음 표에는 정의된 대부분의 동사가 나열되어 있습니다.

|동사 이름(별칭)|작업|피해야 할 동의어|
|-------------------------|------------|--------------|
|[Backup](/dotnet/api/System.Management.Automation.VerbsData.Backup)(ba)|데이터를 복제하여 저장합니다.|Save, Burn, Replicate, Sync|
|[Checkpoint](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint)(ch)|데이터 또는 해당 구성의 현재 상태에 대한 스냅샷을 만듭니다.|Diff|
|[Compare](/dotnet/api/System.Management.Automation.VerbsData.Compare)(cr)|한 리소스의 데이터를 다른 리소스의 데이터를 기준으로 평가합니다.|Diff|
|[Compress](/dotnet/api/System.Management.Automation.VerbsData.Compress)(cm)|리소스의 데이터를 압축합니다. `Expand`와 쌍을 이룹니다.|컴팩트|
|[Convert](/dotnet/api/System.Management.Automation.VerbsData.Convert)(cv)|cmdlet이 양방향 변환을 지원하거나 여러 데이터 형식 간의 변환을 지원하는 경우 데이터의 표현을 하나에서 다른 것으로 변경합니다.|Change, Resize, Resample|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom)(cf)|입력의 한 가지 기본 형식(cmdlet 명사는 입력을 나타냄)을 하나 이상의 지원되는 출력 형식으로 변환합니다.|Export, Output, Out|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo)(ct)|하나 이상의 입력 형식에서 기본 출력 형식(cmdlet 명사는 출력 형식을 나타냄)으로 변환합니다.|Import, Input, In|
|[Dismount](/dotnet/api/System.Management.Automation.VerbsData.Dismount)(dm)|명명된 엔터티를 위치에서 분리합니다. 이 동사는 `Mount`와 쌍을 이룹니다.|Unmount, Unlink|
|[Edit](/dotnet/api/System.Management.Automation.VerbsData.Edit)(ed)|콘텐츠를 추가 또는 제거하여 기존 데이터를 수정합니다.|Change, Update, Modify|
|[Expand](/dotnet/api/System.Management.Automation.VerbsData.Expand)(en)|압축된 리소스의 데이터를 원래 상태로 복원합니다. 이 동사는 `Compress`와 쌍을 이룹니다.|Explode, Uncompress|
|[Export](/dotnet/api/System.Management.Automation.VerbsData.Export)(ep)|기본 입력을 파일 등의 영구 데이터 저장소 또는 교환 형식으로 캡슐화합니다. 이 동사는 `Import`와 쌍을 이룹니다.|Extract, Backup|
|[Import](/dotnet/api/System.Management.Automation.VerbsData.Import)(ip)|영구 데이터 저장소(예: 파일) 또는 교환 형식에 저장된 데이터에서 리소스를 만듭니다. 예를 들어 `Import-CSV` cmdlet은 CSV(쉼표로 구분된 값) 파일의 데이터를 다른 cmdlet에서 사용할 수 있는 개체로 가져옵니다. 이 동사는 `Export`와 쌍을 이룹니다.|BulkLoad, Load|
|[Initialize](/dotnet/api/System.Management.Automation.VerbsData.Initialize)(in)|사용할 리소스를 준비하고 기본 상태로 설정합니다.|Erase, Init, Renew, Rebuild, Reinitialize, Setup|
|[Limit](/dotnet/api/System.Management.Automation.VerbsData.Limit)(l)|리소스에 제약 조건을 적용합니다.|할당량|
|[Merge](/dotnet/api/System.Management.Automation.VerbsData.Merge)(mg)|여러 리소스에서 단일 리소스를 만듭니다.|Combine, Join|
|[Mount](/dotnet/api/System.Management.Automation.VerbsData.Mount)(mt)|명명된 엔터티를 위치에 연결합니다. 이 동사는 `Dismount`와 쌍을 이룹니다.|연결|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out)(o)|환경에서 데이터를 보냅니다. 예를 들어 `Out-Printer` cmdlet은 프린터로 데이터를 보냅니다.||
|[Publish](/dotnet/api/System.Management.Automation.VerbsData.Publish)(pb)|리소스를 다른 사용자가 사용할 수 있게 만듭니다. 이 동사는 `Unpublish`와 쌍을 이룹니다.|Deploy, Release, Install|
|[Restore](/dotnet/api/System.Management.Automation.VerbsData.Restore)(rr)|`Checkpoint`에 의해 설정된 상태와 같이, 리소스를 미리 정의된 상태로 설정합니다. 예를 들어 `Restore-Computer` cmdlet은 로컬 컴퓨터에서 시스템 복원을 시작합니다.|Repair, Return, Undo, Fix|
|[Save](/dotnet/api/System.Management.Automation.VerbsData.Save)(sv)|데이터를 유지하여 손실을 방지합니다.||
|[Sync](/dotnet/api/System.Management.Automation.VerbsData.Sync)(sy)|두 개 이상의 리소스가 동일한 상태임을 보장합니다.|Replicate, Coerce, Match|
|[Unpublish](/dotnet/api/System.Management.Automation.VerbsData.Unpublish)(ub)|리소스를 다른 사용자가 사용할 수 없게 만듭니다. 이 동사는 `Publish`와 쌍을 이룹니다.|Uninstall, Revert, Hide|
|[Update](/dotnet/api/System.Management.Automation.VerbsData.Update)(ud)|리소스를 최신 상태로 유지하여 상태, 정확도, 규칙 또는 규정 준수를 유지 관리합니다. 예를 들어 `Update-FormatData` cmdlet은 서식 파일을 업데이트하고 현재 PowerShell 콘솔에 추가합니다.|Refresh, Renew, Recalculate, Re-index|

## <a name="diagnostic-verbs"></a>진단 동사

PowerShell은 [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) 클래스를 사용하여 진단에 적용되는 작업을 정의합니다. 다음 표에는 정의된 대부분의 동사가 나열되어 있습니다.

|동사(별칭)|작업|피해야 할 동의어|
|--------------------|------------|--------------|
|[Debug](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug)(db)|리소스를 검사하여 운영 문제를 진단합니다.|진단|
|[Measure](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure)(ms)|지정된 작업에서 사용하는 리소스를 식별하거나 리소스에 대한 통계를 검색합니다.|Calculate, Determine, Analyze|
|[Repair](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair)(rp)|리소스를 사용 가능한 상태로 복원합니다.|Fix, Restore|
|[Resolve](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve)(rv)|리소스의 약식 표현을 좀 더 완전한 표현에 매핑합니다.|Expand, Determine|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test)(t)|리소스의 작업 또는 일관성을 확인합니다.|Diagnose, Analyze, Salvage, Verify|
|[Trace](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace)(tr)|리소스의 활동을 추적합니다.|Track, Follow, Inspect, Dig|

## <a name="lifecycle-verbs"></a>수명 주기 동사

PowerShell은 [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 클래스를 사용하여 리소스의 수명 주기에 적용되는 작업을 정의합니다. 다음 표에는 정의된 대부분의 동사가 나열되어 있습니다.

|동사(별칭)|작업|피해야 할 동의어|
|--------------------|------------|--------------|
|[Approve](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve)(ap)|리소스 또는 프로세스의 상태를 확인하거나 동의합니다.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert)(as)|리소스의 상태를 확인합니다.|Certify|
|[Build](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build)(bd)|몇몇 입력 파일 집합(일반적으로 소스 코드 또는 선언적 문서)에서 하나의 아티팩트(일반적으로 이진 또는 문서)를 만듭니다. 이 동사는 PowerShell 6에서 추가되었습니다.||
|[Complete](/dotnet/api/system.management.automation.host.buffercelltype)(cp)|작업을 종결합니다.||
|[Confirm](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm)(cn)|리소스 또는 프로세스의 상태를 승인 또는 확인하거나 유효성을 검사합니다.|Acknowledge, Agree, Certify, Validate, Verify|
|[Deny](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny)(dn)|리소스 또는 프로세스의 상태를 거부, 반대 또는 차단합니다.|Block, Object, Refuse, Reject|
|[Deploy](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy)(dp)|배포가 완료된 후 해당 솔루션의 소비자가 액세스할 수 있는 방식으로 애플리케이션, 웹 사이트 또는 솔루션을 원격 대상으로 보냅니다. 이 동사는 PowerShell 6에서 추가되었습니다.||
|[Disable](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable)(d)|리소스를 사용할 수 없는 상태 또는 비활성 상태로 구성합니다. 예를 들어 `Disable-PSBreakpoint` cmdlet은 중단점을 비활성 상태로 만듭니다. 이 동사는 `Enable`과 쌍을 이룹니다.|Halt, Hide|
|[Enable](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable)(e)|리소스를 사용할 수 있는 상태 또는 활성 상태로 구성합니다. 예를 들어 `Enable-PSBreakpoint` cmdlet은 중단점을 활성화합니다. 이 동사는 `Disable`과 쌍을 이룹니다.|Start, Begin|
|[Install](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install)(is)|리소스를 위치에 배치하고 필요에 따라 초기화합니다. 이 동사는 `Uninstall`과 쌍을 이룹니다.|설정|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke)(i)|명령 또는 메서드 실행과 같은 작업을 수행합니다.|Run, Start|
|[Register](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register)(rg)|데이터베이스와 같은 리포지토리에 리소스에 대한 항목을 만듭니다. 이 동사는 `Unregister`와 쌍을 이룹니다.||
|[Request](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request)(rq)|리소스를 요청하거나 사용 권한을 요청합니다.||
|[Restart](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart)(rt)|작업을 중지한 다음에 다시 시작합니다. 예를 들어 `Restart-Service` cmdlet은 서비스를 중지한 다음에 시작합니다.|재순환|
|[Resume](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume)(ru)|일시 중단된 작업을 시작합니다. 예를 들어 `Resume-Service` cmdlet은 일시 중단된 서비스를 시작합니다. 이 동사는 `Suspend`와 쌍을 이룹니다.||
|[Start](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start)(sa)|작업을 시작합니다. 예를 들어 `Start-Service` cmdlet은 서비스를 시작합니다. 이 동사는 `Stop`과 쌍을 이룹니다.|Launch, Initiate, Boot|
|[Stop](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop)(sp)|활동을 중단합니다. 이 동사는 `Start`와 쌍을 이룹니다.|End, Kill, Terminate, Cancel|
|[Submit](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit)(sb)|승인을 위해 리소스를 제공합니다.|게시|
|[Suspend](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend)(ss)|활동을 일시 중지합니다. 예를 들어 `Suspend-Service` cmdlet은 서비스를 일시 중지합니다. 이 동사는 `Resume`과 쌍을 이룹니다.|일시 중지|
|[Uninstall](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall)(us)|표시된 위치에서 리소스를 제거합니다. 이 동사는 `Install`과 쌍을 이룹니다.||
|[Unregister](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister)(ur)|리포지토리에서 리소스에 대한 항목을 제거합니다. 이 동사는 `Register`와 쌍을 이룹니다.|제거|
|[Wait](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait)(w)|지정된 이벤트가 발생할 때까지 작업을 일시 중지합니다. 예를 들어 `Wait-Job` cmdlet은 하나 이상의 백그라운드 작업이 완료될 때까지 작업을 일시 중지합니다.|Sleep, Pause|

## <a name="security-verbs"></a>보안 동사

PowerShell은 [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) 클래스를 사용하여 보안에 적용되는 작업을 정의합니다. 다음 표에는 정의된 대부분의 동사가 나열되어 있습니다.

|동사(별칭)|작업|피해야 할 동의어|
|--------------------|------------|--------------|
|[Block](/dotnet/api/System.Management.Automation.VerbsSecurity.Block)(bl)|리소스에 대한 액세스를 제한합니다. 이 동사는 `Unblock`과 쌍을 이룹니다.|Prevent, Limit, Deny|
|[Grant](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant)(gr)|리소스에 대한 액세스를 허용합니다. 이 동사는 `Revoke`와 쌍을 이룹니다.|Allow, Enable|
|[Protect](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect)(pt)|공격 또는 손실로부터 리소스를 보호합니다. 이 동사는 `Unprotect`와 쌍을 이룹니다.|Encrypt, Safeguard, Seal|
|[Revoke](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke)(rk)|리소스에 대한 액세스를 허용하지 않는 작업을 지정합니다. 이 동사는 `Grant`와 쌍을 이룹니다.|Remove, Disable|
|[Unblock](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock)(ul)|리소스에 대한 제한을 제거합니다. 이 동사는 `Block`과 쌍을 이룹니다.|Clear, Allow|
|[Unprotect](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect)(up)|공격 또는 손실을 방지하기 위해 추가된 리소스에서 보호 기능을 제거합니다. 이 동사는 `Protect`와 쌍을 이룹니다.|Decrypt, Unseal|

## <a name="other-verbs"></a>기타 동사

PowerShell은 [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) 클래스를 사용하여 일반 동사, 통신 동사, 데이터 동사, 수명 주기 동사 또는 보안 동사 등 특정 동사 이름 범주에 속하지 않는 정규 동사 이름을 정의합니다.

|동사(별칭)|작업|피해야 할 동의어|
|--------------------|------------|--------------|
|[Use](/dotnet/api/System.Management.Automation.VerbsOther.Use)(u)|어떤 작업을 하기 위해 리소스를 사용하거나 포함합니다.||

## <a name="see-also"></a>참고 항목

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)
- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)
- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)
- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)
- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)
- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)
- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)
- [cmdlet 선언](./cmdlet-class-declaration.md)
- [Windows PowerShell 프로그래머 가이드](../prog-guide/windows-powershell-programmer-s-guide.md)
- [Windows PowerShell Shell SDK](../windows-powershell-reference.md)
