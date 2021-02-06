---
description: PowerShell은 엔진, 공급자 및 cmdlet의 내부 작업을 Windows 이벤트 로그에 기록 합니다.
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: d6ae50b50911417da8dd306cad69e3fc7129fedc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599938"
---
# <a name="about-logging-windows"></a><span data-ttu-id="1b9fd-103">Windows 로깅 정보</span><span class="sxs-lookup"><span data-stu-id="1b9fd-103">About Logging Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="1b9fd-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="1b9fd-104">Short description</span></span>
<span data-ttu-id="1b9fd-105">PowerShell은 엔진, 공급자 및 cmdlet의 내부 작업을 Windows 이벤트 로그에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-105">PowerShell logs internal operations from the engine, providers, and cmdlets to the Windows event log.</span></span>

## <a name="long-description"></a><span data-ttu-id="1b9fd-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-106">Long description</span></span>

<span data-ttu-id="1b9fd-107">Powershell은 엔진 및 공급자 시작 및 중지, PowerShell 명령 실행과 같은 PowerShell 작업에 대 한 세부 정보를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-107">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="1b9fd-108">Windows PowerShell 버전 3.0, 4.0, 5.0 및 5.1에는 Windows 이벤트 로그에 대 한 **EventLog** cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-108">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="1b9fd-109">이러한 버전에서 **EventLog** cmdlet의 목록을 표시 하려면:를 입력 `Get-Command -Noun EventLog` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-109">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="1b9fd-110">자세한 내용은 Windows PowerShell 버전에 대 한 cmdlet 설명서 및 about_EventLogs을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-110">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="1b9fd-111">Windows에서 PowerShell 이벤트 로그 항목 보기</span><span class="sxs-lookup"><span data-stu-id="1b9fd-111">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="1b9fd-112">PowerShell 로그는 Windows 이벤트 뷰어를 사용 하 여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-112">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="1b9fd-113">이벤트 로그는 응용 프로그램 및 서비스 로그 그룹에 있으며 이름이로 지정 됩니다 `PowerShellCore` .</span><span class="sxs-lookup"><span data-stu-id="1b9fd-113">The event log is located in the Application and Services Logs group and is named `PowerShellCore`.</span></span> <span data-ttu-id="1b9fd-114">연결 된 ETW 공급자 `GUID` 는 `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` 입니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-114">The associated ETW provider `GUID` is `{f90714a8-5509-434a-bf6d-b1624c8a19a2}`.</span></span>

<span data-ttu-id="1b9fd-115">스크립트 블록 로깅을 사용 하는 경우 PowerShell은 다음 이벤트를 로그에 기록 합니다 `PowerShellCore/Operational` .</span><span class="sxs-lookup"><span data-stu-id="1b9fd-115">When Script Block Logging is enabled, PowerShell logs the following events to the `PowerShellCore/Operational` log:</span></span>

|  <span data-ttu-id="1b9fd-116">필드</span><span class="sxs-lookup"><span data-stu-id="1b9fd-116">Field</span></span>  |       <span data-ttu-id="1b9fd-117">값</span><span class="sxs-lookup"><span data-stu-id="1b9fd-117">Value</span></span>       |
| ------- | ----------------- |
| <span data-ttu-id="1b9fd-118">EventId</span><span class="sxs-lookup"><span data-stu-id="1b9fd-118">EventId</span></span> | `4104` / `0x1008` |
| <span data-ttu-id="1b9fd-119">채널</span><span class="sxs-lookup"><span data-stu-id="1b9fd-119">Channel</span></span> | `Operational`     |
| <span data-ttu-id="1b9fd-120">Level</span><span class="sxs-lookup"><span data-stu-id="1b9fd-120">Level</span></span>   | `Verbose`         |
| <span data-ttu-id="1b9fd-121">Opcode</span><span class="sxs-lookup"><span data-stu-id="1b9fd-121">Opcode</span></span>  | `Create`          |
| <span data-ttu-id="1b9fd-122">Task</span><span class="sxs-lookup"><span data-stu-id="1b9fd-122">Task</span></span>    | `CommandStart`    |
| <span data-ttu-id="1b9fd-123">키워드</span><span class="sxs-lookup"><span data-stu-id="1b9fd-123">Keyword</span></span> | `Runspace`        |

### <a name="registering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="1b9fd-124">Windows에서 PowerShell 이벤트 공급자 등록</span><span class="sxs-lookup"><span data-stu-id="1b9fd-124">Registering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="1b9fd-125">Linux 또는 macOS와 달리 Windows에서는 이벤트 로그에 이벤트를 기록 하기 전에 이벤트 공급자를 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-125">Unlike Linux or macOS, Windows requires the event provider to be registered before events can be written to the event log.</span></span> <span data-ttu-id="1b9fd-126">PowerShell 이벤트 공급자를 사용 하도록 설정 하려면 관리자 권한 PowerShell 프롬프트에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-126">To enable the PowerShell event provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="1b9fd-127">Windows에서 PowerShell 이벤트 공급자 등록 취소</span><span class="sxs-lookup"><span data-stu-id="1b9fd-127">Unregistering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="1b9fd-128">이벤트 공급자를 등록 하면 이벤트를 디코딩하는 데 사용 되는 이진 라이브러리에 잠금이 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-128">Registering the event provider places a lock in the binary library used to decode events.</span></span> <span data-ttu-id="1b9fd-129">이 라이브러리를 업데이트 하려면이 잠금을 해제 하기 위해 공급자를 등록 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-129">To update this library, the provider must be unregistered to release this lock.</span></span>

<span data-ttu-id="1b9fd-130">PowerShell 공급자의 등록을 취소 하려면 관리자 권한 PowerShell 프롬프트에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-130">To unregister the PowerShell provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

<span data-ttu-id="1b9fd-131">PowerShell을 업데이트 한 후를 실행 `$PSHOME\RegisterManifest.ps1` 하 여 업데이트 된 이벤트 공급자를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-131">After updating PowerShell, run `$PSHOME\RegisterManifest.ps1` to register the updated event provider.</span></span>

## <a name="enabling-script-block-logging"></a><span data-ttu-id="1b9fd-132">스크립트 블록 로깅 사용</span><span class="sxs-lookup"><span data-stu-id="1b9fd-132">Enabling Script Block Logging</span></span>

<span data-ttu-id="1b9fd-133">스크립트 블록 로깅을 사용 하는 경우 PowerShell은 처리 하는 모든 스크립트 블록의 콘텐츠를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-133">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="1b9fd-134">사용 하도록 설정 되 면 모든 새 PowerShell 세션에서이 정보를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-134">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="1b9fd-135">진단이 아닌 다른 항목에 대해 스크립트 블록 로깅을 사용 하는 경우 아래에 설명 된 대로 보호 된 이벤트 로깅을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-135">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="1b9fd-136">스크립트 블록 로깅은 그룹 정책 또는 레지스트리 설정을 통해 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-136">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="1b9fd-137">그룹 정책을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="1b9fd-137">Using Group Policy</span></span>

<span data-ttu-id="1b9fd-138">자동 기록을 사용 하도록 설정 하려면 그룹 정책에서 기능을 사용 하도록 설정 `Turn on PowerShell Script Block
Logging` `Administrative Templates -> Windows
Components -> Windows PowerShell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-138">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="1b9fd-139">레지스트리 사용</span><span class="sxs-lookup"><span data-stu-id="1b9fd-139">Using the Registry</span></span>

<span data-ttu-id="1b9fd-140">다음 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-140">Run the following function:</span></span>

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

## <a name="protected-event-logging"></a><span data-ttu-id="1b9fd-141">보호 된 이벤트 로깅</span><span class="sxs-lookup"><span data-stu-id="1b9fd-141">Protected Event Logging</span></span>

<span data-ttu-id="1b9fd-142">시스템에 대 한 로깅 수준을 높이면 기록 된 콘텐츠에 중요 한 데이터가 포함 될 가능성이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-142">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="1b9fd-143">예를 들어 스크립트 로깅을 사용 하는 경우 스크립트에서 사용 하는 자격 증명 또는 기타 중요 한 데이터를 이벤트 로그에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-143">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="1b9fd-144">중요 한 데이터를 기록 하는 컴퓨터가 손상 된 경우 로그는 해당 연결을 확장 하는 데 필요한 정보를 공격자에 게 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-144">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="1b9fd-145">이 정보를 보호 하기 위해 Windows 10에서는 보호 된 이벤트 로깅을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-145">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="1b9fd-146">보호 된 이벤트 로깅을 사용 하면 참여 응용 프로그램에서 이벤트 로그에 기록 된 중요 한 데이터를 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-146">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="1b9fd-147">나중에 보다 안전 하 고 중앙 집중식 로그 수집기에서 이러한 로그를 해독 하 고 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-147">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="1b9fd-148">이벤트 로그 내용은 IETF CMS (암호화 메시지 구문) 표준을 사용 하 여 보호 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-148">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="1b9fd-149">CMS는 공개 키 암호화를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-149">CMS uses public key cryptography.</span></span> <span data-ttu-id="1b9fd-150">콘텐츠를 암호화 하 고 암호를 해독 하는 데 사용 되는 키는 분리 된 상태로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-150">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="1b9fd-151">공개 키는 광범위 하 게 공유할 수 있으며 중요 한 데이터가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-151">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="1b9fd-152">이 공개 키로 암호화 된 콘텐츠는 개인 키로만 해독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-152">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="1b9fd-153">공개 키 암호화에 대 한 자세한 내용은 [위키백과-공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-153">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="1b9fd-154">보호 된 이벤트 로깅 정책을 사용 하도록 설정 하려면 보호할 이벤트 로그 데이터가 있는 모든 컴퓨터에 공개 키를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-154">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="1b9fd-155">해당 개인 키는 중앙 이벤트 로그 수집기 또는 [Siem][] 집계와 같은 보다 안전한 위치에서 이벤트 로그를 사후 처리 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-155">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="1b9fd-156">Azure에서 SIEM을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-156">You can set up SIEM in Azure.</span></span> <span data-ttu-id="1b9fd-157">자세한 내용은 [일반 SIEM 통합](/cloud-app-security/siem)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-157">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="1b9fd-158">그룹 정책를 통해 보호 된 이벤트 로깅 사용</span><span class="sxs-lookup"><span data-stu-id="1b9fd-158">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="1b9fd-159">보호 된 이벤트 로깅을 사용 하도록 설정 하려면 `Enable Protected Event Logging` 그룹 정책에서로 기능을 사용 하도록 설정 `Administrative Templates -> Windows Components
-> Event Logging` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-159">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="1b9fd-160">이 설정에는 암호화 인증서가 필요 하며,이 인증서는 다음과 같은 여러 형식 중 하나로 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-160">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="1b9fd-161">Base-64로 인코딩된 x.509 인증서 (예: `Export` 인증서 관리자의 옵션에서 제공 하는)의 콘텐츠입니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-161">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="1b9fd-162">로컬 컴퓨터 인증서 저장소에서 찾을 수 있는 인증서의 지문입니다 (PKI 인프라로 배포할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="1b9fd-162">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="1b9fd-163">인증서에 대 한 전체 경로입니다 (로컬 또는 원격 공유 일 수 있음).</span><span class="sxs-lookup"><span data-stu-id="1b9fd-163">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="1b9fd-164">인증서 또는 인증서를 포함 하는 디렉터리의 경로 (로컬 또는 원격 공유 일 수 있음)입니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-164">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="1b9fd-165">로컬 컴퓨터 인증서 저장소에서 찾을 수 있는 인증서의 주체 이름입니다 (PKI 인프라로 배포할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="1b9fd-165">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="1b9fd-166">결과 인증서에 확장 된 `Document Encryption` 키 사용 ( `1.3.6.1.4.1.311.80.1` )이 있어야 하 고 `Data Encipherment` 또는 키 사용이 `Key
Encipherment` 사용 하도록 설정 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-166">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="1b9fd-167">개인 키는 컴퓨터 로깅 이벤트에 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-167">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="1b9fd-168">메시지를 암호 해독 하는 안전한 위치에 보관 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-168">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="1b9fd-169">보호 된 이벤트 로깅 메시지 암호 해독</span><span class="sxs-lookup"><span data-stu-id="1b9fd-169">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="1b9fd-170">다음 스크립트는 개인 키가 있는 것으로 가정 하 여를 검색 하 고 암호를 해독 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b9fd-170">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="1b9fd-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1b9fd-171">See also</span></span>

[<span data-ttu-id="1b9fd-172">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="1b9fd-172">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="1b9fd-173">PowerShell 블루 팀</span><span class="sxs-lookup"><span data-stu-id="1b9fd-173">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="1b9fd-174">일반 SIEM 통합</span><span class="sxs-lookup"><span data-stu-id="1b9fd-174">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
