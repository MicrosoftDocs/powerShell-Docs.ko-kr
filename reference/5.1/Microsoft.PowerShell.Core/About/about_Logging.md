---
description: PowerShell은 엔진, 공급자 및 cmdlet에서 내부 작업을 기록 합니다.
keywords: PowerShell
Locale: en-US
ms.date: 12/14/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging
ms.openlocfilehash: 5d061b38b5b0fa45cf0a86c2f5b7e0efcb8d1f7b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222705"
---
# <a name="about-logging"></a><span data-ttu-id="5864f-104">로깅 정보</span><span class="sxs-lookup"><span data-stu-id="5864f-104">About Logging</span></span>

## <a name="short-description"></a><span data-ttu-id="5864f-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="5864f-105">Short description</span></span>

<span data-ttu-id="5864f-106">PowerShell은 엔진, 공급자 및 cmdlet에서 내부 작업을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-106">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="5864f-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-107">Long description</span></span>

<span data-ttu-id="5864f-108">Powershell은 엔진 및 공급자 시작 및 중지, PowerShell 명령 실행과 같은 PowerShell 작업에 대 한 세부 정보를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-108">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="5864f-109">Windows PowerShell 버전 3.0, 4.0, 5.0 및 5.1에는 Windows 이벤트 로그에 대 한 **EventLog** cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-109">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="5864f-110">이러한 버전에서 **EventLog** cmdlet의 목록을 표시 하려면:를 입력 `Get-Command -Noun EventLog` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-110">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="5864f-111">자세한 내용은 Windows PowerShell 버전에 대 한 cmdlet 설명서 및 about_EventLogs을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5864f-111">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="5864f-112">Windows에서 PowerShell 이벤트 로그 항목 보기</span><span class="sxs-lookup"><span data-stu-id="5864f-112">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="5864f-113">PowerShell 로그는 Windows 이벤트 뷰어를 사용 하 여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-113">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="5864f-114">이벤트 로그는 응용 프로그램 및 서비스 로그 그룹에 있으며 이름이로 지정 됩니다 `Microsoft-Windows-PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="5864f-114">The event log is located in the Application and Services Logs group and is named `Microsoft-Windows-PowerShell`.</span></span> <span data-ttu-id="5864f-115">연결 된 ETW 공급자 `GUID` 는 `{A0C1853B-5C40-4B15-8766-3CF1C58F985A}` 입니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-115">The associated ETW provider `GUID` is `{A0C1853B-5C40-4B15-8766-3CF1C58F985A}`.</span></span>

<span data-ttu-id="5864f-116">스크립트 블록 로깅을 사용 하는 경우 PowerShell은 다음 이벤트를 로그에 기록 합니다 `Microsoft-Windows-PowerShell/Operational` .</span><span class="sxs-lookup"><span data-stu-id="5864f-116">When Script Block Logging is enabled, PowerShell logs the following events to the `Microsoft-Windows-PowerShell/Operational` log:</span></span>

|<span data-ttu-id="5864f-117">필드</span><span class="sxs-lookup"><span data-stu-id="5864f-117">Field</span></span>| <span data-ttu-id="5864f-118">값</span><span class="sxs-lookup"><span data-stu-id="5864f-118">Value</span></span>|
|-|-|
|<span data-ttu-id="5864f-119">EventId</span><span class="sxs-lookup"><span data-stu-id="5864f-119">EventId</span></span>|`4104` / `0x1008`|
|<span data-ttu-id="5864f-120">채널</span><span class="sxs-lookup"><span data-stu-id="5864f-120">Channel</span></span>|`Operational`|
|<span data-ttu-id="5864f-121">Level</span><span class="sxs-lookup"><span data-stu-id="5864f-121">Level</span></span>|`Verbose`|
|<span data-ttu-id="5864f-122">Opcode</span><span class="sxs-lookup"><span data-stu-id="5864f-122">Opcode</span></span>|`Create`|
|<span data-ttu-id="5864f-123">작업</span><span class="sxs-lookup"><span data-stu-id="5864f-123">Task</span></span>|`CommandStart`|
|<span data-ttu-id="5864f-124">키워드</span><span class="sxs-lookup"><span data-stu-id="5864f-124">Keyword</span></span>|`Runspace`|

## <a name="enabling-script-block-logging"></a><span data-ttu-id="5864f-125">스크립트 블록 로깅 사용</span><span class="sxs-lookup"><span data-stu-id="5864f-125">Enabling Script Block Logging</span></span>

<span data-ttu-id="5864f-126">스크립트 블록 로깅을 사용 하는 경우 PowerShell은 처리 하는 모든 스크립트 블록의 콘텐츠를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-126">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="5864f-127">사용 하도록 설정 되 면 모든 새 PowerShell 세션에서이 정보를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-127">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="5864f-128">진단이 아닌 다른 항목에 대해 스크립트 블록 로깅을 사용 하는 경우 아래에 설명 된 대로 보호 된 이벤트 로깅을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-128">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="5864f-129">스크립트 블록 로깅은 그룹 정책 또는 레지스트리 설정을 통해 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-129">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="5864f-130">그룹 정책을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="5864f-130">Using Group Policy</span></span>

<span data-ttu-id="5864f-131">자동 기록을 사용 하도록 설정 하려면 그룹 정책에서 기능을 사용 하도록 설정 `Turn on PowerShell Script Block
Logging` `Administrative Templates -> Windows
Components -> Windows PowerShell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-131">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="5864f-132">레지스트리 사용</span><span class="sxs-lookup"><span data-stu-id="5864f-132">Using the Registry</span></span>

<span data-ttu-id="5864f-133">다음 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-133">Run the following function:</span></span>

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a><span data-ttu-id="5864f-134">보호 된 이벤트 로깅</span><span class="sxs-lookup"><span data-stu-id="5864f-134">Protected Event Logging</span></span>

<span data-ttu-id="5864f-135">시스템에 대 한 로깅 수준을 높이면 기록 된 콘텐츠에 중요 한 데이터가 포함 될 가능성이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-135">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="5864f-136">예를 들어 스크립트 로깅을 사용 하는 경우 스크립트에서 사용 하는 자격 증명 또는 기타 중요 한 데이터를 이벤트 로그에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-136">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="5864f-137">중요 한 데이터를 기록 하는 컴퓨터가 손상 된 경우 로그는 해당 연결을 확장 하는 데 필요한 정보를 공격자에 게 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-137">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="5864f-138">이 정보를 보호 하기 위해 Windows 10에서는 보호 된 이벤트 로깅을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-138">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="5864f-139">보호 된 이벤트 로깅을 사용 하면 참여 응용 프로그램에서 이벤트 로그에 기록 된 중요 한 데이터를 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-139">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="5864f-140">나중에 보다 안전 하 고 중앙 집중식 로그 수집기에서 이러한 로그를 해독 하 고 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-140">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="5864f-141">이벤트 로그 내용은 IETF CMS (암호화 메시지 구문) 표준을 사용 하 여 보호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-141">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="5864f-142">CMS는 공개 키 암호화를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-142">CMS uses public key cryptography.</span></span> <span data-ttu-id="5864f-143">콘텐츠를 암호화 하 고 암호를 해독 하는 데 사용 되는 키는 분리 된 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-143">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="5864f-144">공개 키는 광범위 하 게 공유할 수 있으며 중요 한 데이터가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-144">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="5864f-145">이 공개 키로 암호화 된 콘텐츠는 개인 키로만 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-145">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="5864f-146">공개 키 암호화에 대 한 자세한 내용은 [위키백과-공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5864f-146">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="5864f-147">보호 된 이벤트 로깅 정책을 사용 하도록 설정 하려면 보호할 이벤트 로그 데이터가 있는 모든 컴퓨터에 공개 키를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-147">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="5864f-148">해당 개인 키는 중앙 이벤트 로그 수집기 또는 [Siem][] 집계와 같은 보다 안전한 위치에서 이벤트 로그를 사후 처리 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-148">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="5864f-149">Azure에서 SIEM을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-149">You can set up SIEM in Azure.</span></span> <span data-ttu-id="5864f-150">자세한 내용은 [일반 SIEM 통합](/cloud-app-security/siem)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5864f-150">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="5864f-151">그룹 정책를 통해 보호 된 이벤트 로깅 사용</span><span class="sxs-lookup"><span data-stu-id="5864f-151">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="5864f-152">보호 된 이벤트 로깅을 사용 하도록 설정 하려면 `Enable Protected Event Logging` 그룹 정책에서로 기능을 사용 하도록 설정 `Administrative Templates -> Windows Components
-> Event Logging` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-152">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="5864f-153">이 설정에는 암호화 인증서가 필요 하며,이 인증서는 다음과 같은 여러 형식 중 하나로 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-153">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="5864f-154">Base-64로 인코딩된 x.509 인증서 (예: `Export` 인증서 관리자의 옵션에서 제공 하는)의 콘텐츠입니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-154">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="5864f-155">로컬 컴퓨터 인증서 저장소에서 찾을 수 있는 인증서의 지문입니다 (PKI 인프라로 배포할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="5864f-155">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="5864f-156">인증서에 대 한 전체 경로입니다 (로컬 또는 원격 공유 일 수 있음).</span><span class="sxs-lookup"><span data-stu-id="5864f-156">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="5864f-157">인증서 또는 인증서를 포함 하는 디렉터리의 경로 (로컬 또는 원격 공유 일 수 있음)입니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-157">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="5864f-158">로컬 컴퓨터 인증서 저장소에서 찾을 수 있는 인증서의 주체 이름입니다 (PKI 인프라로 배포할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="5864f-158">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="5864f-159">결과 인증서에 확장 된 `Document Encryption` 키 사용 ( `1.3.6.1.4.1.311.80.1` )이 있어야 하 고 `Data Encipherment` 또는 키 사용이 `Key
Encipherment` 사용 하도록 설정 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-159">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="5864f-160">개인 키는 컴퓨터 로깅 이벤트에 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-160">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="5864f-161">메시지를 암호 해독 하는 안전한 위치에 보관 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-161">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="5864f-162">보호 된 이벤트 로깅 메시지 암호 해독</span><span class="sxs-lookup"><span data-stu-id="5864f-162">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="5864f-163">다음 스크립트는 개인 키가 있는 것으로 가정 하 여를 검색 하 고 암호를 해독 합니다.</span><span class="sxs-lookup"><span data-stu-id="5864f-163">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="5864f-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5864f-164">See also</span></span>

[<span data-ttu-id="5864f-165">PowerShell 블루 팀</span><span class="sxs-lookup"><span data-stu-id="5864f-165">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="5864f-166">일반 SIEM 통합</span><span class="sxs-lookup"><span data-stu-id="5864f-166">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
