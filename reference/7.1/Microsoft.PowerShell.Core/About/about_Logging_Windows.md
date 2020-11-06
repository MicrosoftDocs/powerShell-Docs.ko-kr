---
description: PowerShell은 엔진, 공급자 및 cmdlet의 내부 작업을 Windows 이벤트 로그에 기록 합니다.
keywords: PowerShell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: 960394838097e4bfad1af5f4f0af7a813a50e761
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355020"
---
# <a name="about-logging-windows"></a><span data-ttu-id="e2033-104">Windows 로깅 정보</span><span class="sxs-lookup"><span data-stu-id="e2033-104">About Logging Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="e2033-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="e2033-105">Short description</span></span>
<span data-ttu-id="e2033-106">PowerShell은 엔진, 공급자 및 cmdlet의 내부 작업을 Windows 이벤트 로그에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-106">PowerShell logs internal operations from the engine, providers, and cmdlets to the Windows event log.</span></span>

## <a name="long-description"></a><span data-ttu-id="e2033-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-107">Long description</span></span>

<span data-ttu-id="e2033-108">Powershell은 엔진 및 공급자 시작 및 중지, PowerShell 명령 실행과 같은 PowerShell 작업에 대 한 세부 정보를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-108">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="e2033-109">Windows PowerShell 버전 3.0, 4.0, 5.0 및 5.1에는 Windows 이벤트 로그에 대 한 **EventLog** cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-109">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="e2033-110">이러한 버전에서 **EventLog** cmdlet의 목록을 표시 하려면:를 입력 `Get-Command -Noun EventLog` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-110">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="e2033-111">자세한 내용은 Windows PowerShell 버전에 대 한 cmdlet 설명서 및 about_EventLogs을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e2033-111">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="e2033-112">Windows에서 PowerShell 이벤트 로그 항목 보기</span><span class="sxs-lookup"><span data-stu-id="e2033-112">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="e2033-113">PowerShell 로그는 Windows 이벤트 뷰어를 사용 하 여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-113">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="e2033-114">이벤트 로그는 응용 프로그램 및 서비스 로그 그룹에 있으며 이름이로 지정 됩니다 `PowerShellCore` .</span><span class="sxs-lookup"><span data-stu-id="e2033-114">The event log is located in the Application and Services Logs group and is named `PowerShellCore`.</span></span> <span data-ttu-id="e2033-115">연결 된 ETW 공급자 `GUID` 는 `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` 입니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-115">The associated ETW provider `GUID` is `{f90714a8-5509-434a-bf6d-b1624c8a19a2}`.</span></span>

<span data-ttu-id="e2033-116">스크립트 블록 로깅을 사용 하는 경우 PowerShell은 다음 이벤트를 로그에 기록 합니다 `PowerShellCore/Operational` .</span><span class="sxs-lookup"><span data-stu-id="e2033-116">When Script Block Logging is enabled, PowerShell logs the following events to the `PowerShellCore/Operational` log:</span></span>

|  <span data-ttu-id="e2033-117">필드</span><span class="sxs-lookup"><span data-stu-id="e2033-117">Field</span></span>  |       <span data-ttu-id="e2033-118">값</span><span class="sxs-lookup"><span data-stu-id="e2033-118">Value</span></span>       |
| ------- | ----------------- |
| <span data-ttu-id="e2033-119">EventId</span><span class="sxs-lookup"><span data-stu-id="e2033-119">EventId</span></span> | `4104` / `0x1008` |
| <span data-ttu-id="e2033-120">채널</span><span class="sxs-lookup"><span data-stu-id="e2033-120">Channel</span></span> | `Operational`     |
| <span data-ttu-id="e2033-121">Level</span><span class="sxs-lookup"><span data-stu-id="e2033-121">Level</span></span>   | `Verbose`         |
| <span data-ttu-id="e2033-122">Opcode</span><span class="sxs-lookup"><span data-stu-id="e2033-122">Opcode</span></span>  | `Create`          |
| <span data-ttu-id="e2033-123">Task</span><span class="sxs-lookup"><span data-stu-id="e2033-123">Task</span></span>    | `CommandStart`    |
| <span data-ttu-id="e2033-124">키워드</span><span class="sxs-lookup"><span data-stu-id="e2033-124">Keyword</span></span> | `Runspace`        |

### <a name="registering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="e2033-125">Windows에서 PowerShell 이벤트 공급자 등록</span><span class="sxs-lookup"><span data-stu-id="e2033-125">Registering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="e2033-126">Linux 또는 macOS와 달리 Windows에서는 이벤트 로그에 이벤트를 기록 하기 전에 이벤트 공급자를 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-126">Unlike Linux or macOS, Windows requires the event provider to be registered before events can be written to the event log.</span></span> <span data-ttu-id="e2033-127">PowerShell 이벤트 공급자를 사용 하도록 설정 하려면 관리자 권한 PowerShell 프롬프트에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-127">To enable the PowerShell event provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="e2033-128">Windows에서 PowerShell 이벤트 공급자 등록 취소</span><span class="sxs-lookup"><span data-stu-id="e2033-128">Unregistering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="e2033-129">이벤트 공급자를 등록 하면 이벤트를 디코딩하는 데 사용 되는 이진 라이브러리에 잠금이 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-129">Registering the event provider places a lock in the binary library used to decode events.</span></span> <span data-ttu-id="e2033-130">이 라이브러리를 업데이트 하려면이 잠금을 해제 하기 위해 공급자를 등록 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-130">To update this library, the provider must be unregistered to release this lock.</span></span>

<span data-ttu-id="e2033-131">PowerShell 공급자의 등록을 취소 하려면 관리자 권한 PowerShell 프롬프트에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-131">To unregister the PowerShell provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

<span data-ttu-id="e2033-132">PowerShell을 업데이트 한 후를 실행 `$PSHOME\RegisterManifest.ps1` 하 여 업데이트 된 이벤트 공급자를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-132">After updating PowerShell, run `$PSHOME\RegisterManifest.ps1` to register the updated event provider.</span></span>

## <a name="enabling-script-block-logging"></a><span data-ttu-id="e2033-133">스크립트 블록 로깅 사용</span><span class="sxs-lookup"><span data-stu-id="e2033-133">Enabling Script Block Logging</span></span>

<span data-ttu-id="e2033-134">스크립트 블록 로깅을 사용 하는 경우 PowerShell은 처리 하는 모든 스크립트 블록의 콘텐츠를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-134">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="e2033-135">사용 하도록 설정 되 면 모든 새 PowerShell 세션에서이 정보를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-135">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="e2033-136">진단이 아닌 다른 항목에 대해 스크립트 블록 로깅을 사용 하는 경우 아래에 설명 된 대로 보호 된 이벤트 로깅을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-136">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="e2033-137">스크립트 블록 로깅은 그룹 정책 또는 레지스트리 설정을 통해 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-137">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="e2033-138">그룹 정책을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="e2033-138">Using Group Policy</span></span>

<span data-ttu-id="e2033-139">자동 기록을 사용 하도록 설정 하려면 그룹 정책에서 기능을 사용 하도록 설정 `Turn on PowerShell Script Block
Logging` `Administrative Templates -> Windows
Components -> Windows PowerShell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-139">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="e2033-140">레지스트리 사용</span><span class="sxs-lookup"><span data-stu-id="e2033-140">Using the Registry</span></span>

<span data-ttu-id="e2033-141">다음 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-141">Run the following function:</span></span>

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

## <a name="protected-event-logging"></a><span data-ttu-id="e2033-142">보호 된 이벤트 로깅</span><span class="sxs-lookup"><span data-stu-id="e2033-142">Protected Event Logging</span></span>

<span data-ttu-id="e2033-143">시스템에 대 한 로깅 수준을 높이면 기록 된 콘텐츠에 중요 한 데이터가 포함 될 가능성이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-143">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="e2033-144">예를 들어 스크립트 로깅을 사용 하는 경우 스크립트에서 사용 하는 자격 증명 또는 기타 중요 한 데이터를 이벤트 로그에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-144">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="e2033-145">중요 한 데이터를 기록 하는 컴퓨터가 손상 된 경우 로그는 해당 연결을 확장 하는 데 필요한 정보를 공격자에 게 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-145">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="e2033-146">이 정보를 보호 하기 위해 Windows 10에서는 보호 된 이벤트 로깅을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-146">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="e2033-147">보호 된 이벤트 로깅을 사용 하면 참여 응용 프로그램에서 이벤트 로그에 기록 된 중요 한 데이터를 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-147">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="e2033-148">나중에 보다 안전 하 고 중앙 집중식 로그 수집기에서 이러한 로그를 해독 하 고 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-148">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="e2033-149">이벤트 로그 내용은 IETF CMS (암호화 메시지 구문) 표준을 사용 하 여 보호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-149">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="e2033-150">CMS는 공개 키 암호화를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-150">CMS uses public key cryptography.</span></span> <span data-ttu-id="e2033-151">콘텐츠를 암호화 하 고 암호를 해독 하는 데 사용 되는 키는 분리 된 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-151">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="e2033-152">공개 키는 광범위 하 게 공유할 수 있으며 중요 한 데이터가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-152">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="e2033-153">이 공개 키로 암호화 된 콘텐츠는 개인 키로만 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-153">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="e2033-154">공개 키 암호화에 대 한 자세한 내용은 [위키백과-공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e2033-154">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="e2033-155">보호 된 이벤트 로깅 정책을 사용 하도록 설정 하려면 보호할 이벤트 로그 데이터가 있는 모든 컴퓨터에 공개 키를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-155">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="e2033-156">해당 개인 키는 중앙 이벤트 로그 수집기 또는 [Siem][] 집계와 같은 보다 안전한 위치에서 이벤트 로그를 사후 처리 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-156">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="e2033-157">Azure에서 SIEM을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-157">You can set up SIEM in Azure.</span></span> <span data-ttu-id="e2033-158">자세한 내용은 [일반 SIEM 통합](/cloud-app-security/siem)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e2033-158">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="e2033-159">그룹 정책를 통해 보호 된 이벤트 로깅 사용</span><span class="sxs-lookup"><span data-stu-id="e2033-159">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="e2033-160">보호 된 이벤트 로깅을 사용 하도록 설정 하려면 `Enable Protected Event Logging` 그룹 정책에서로 기능을 사용 하도록 설정 `Administrative Templates -> Windows Components
-> Event Logging` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-160">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="e2033-161">이 설정에는 암호화 인증서가 필요 하며,이 인증서는 다음과 같은 여러 형식 중 하나로 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-161">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="e2033-162">Base-64로 인코딩된 x.509 인증서 (예: `Export` 인증서 관리자의 옵션에서 제공 하는)의 콘텐츠입니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-162">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="e2033-163">로컬 컴퓨터 인증서 저장소에서 찾을 수 있는 인증서의 지문입니다 (PKI 인프라로 배포할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="e2033-163">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="e2033-164">인증서에 대 한 전체 경로입니다 (로컬 또는 원격 공유 일 수 있음).</span><span class="sxs-lookup"><span data-stu-id="e2033-164">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="e2033-165">인증서 또는 인증서를 포함 하는 디렉터리의 경로 (로컬 또는 원격 공유 일 수 있음)입니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-165">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="e2033-166">로컬 컴퓨터 인증서 저장소에서 찾을 수 있는 인증서의 주체 이름입니다 (PKI 인프라로 배포할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="e2033-166">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="e2033-167">결과 인증서에 확장 된 `Document Encryption` 키 사용 ( `1.3.6.1.4.1.311.80.1` )이 있어야 하 고 `Data Encipherment` 또는 키 사용이 `Key
Encipherment` 사용 하도록 설정 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-167">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="e2033-168">개인 키는 컴퓨터 로깅 이벤트에 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-168">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="e2033-169">메시지를 암호 해독 하는 안전한 위치에 보관 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-169">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="e2033-170">보호 된 이벤트 로깅 메시지 암호 해독</span><span class="sxs-lookup"><span data-stu-id="e2033-170">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="e2033-171">다음 스크립트는 개인 키가 있는 것으로 가정 하 여를 검색 하 고 암호를 해독 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2033-171">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="e2033-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2033-172">See also</span></span>

[<span data-ttu-id="e2033-173">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="e2033-173">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="e2033-174">PowerShell 블루 팀</span><span class="sxs-lookup"><span data-stu-id="e2033-174">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="e2033-175">일반 SIEM 통합</span><span class="sxs-lookup"><span data-stu-id="e2033-175">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
