---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 0a68c665e8a0b504cfef416134374c5598ba55a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602652"
---
# <span data-ttu-id="bf57f-102">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="bf57f-102">Send-MailMessage</span></span>

## <span data-ttu-id="bf57f-103">개요</span><span class="sxs-lookup"><span data-stu-id="bf57f-103">SYNOPSIS</span></span>
<span data-ttu-id="bf57f-104">이메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-104">Sends an email message.</span></span>

## <span data-ttu-id="bf57f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bf57f-105">SYNTAX</span></span>

### <span data-ttu-id="bf57f-106">모두</span><span class="sxs-lookup"><span data-stu-id="bf57f-106">All</span></span>

```
Send-MailMessage [-Attachments <String[]>] [-Bcc <String[]>] [[-Body] <String>] [-BodyAsHtml]
 [-Encoding <Encoding>] [-Cc <String[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 -From <String> [[-SmtpServer] <String>] [-Priority <MailPriority>] [-ReplyTo <String[]>]
 [[-Subject] <String>] [-To] <String[]> [-Credential <PSCredential>] [-UseSsl] [-Port <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="bf57f-107">설명</span><span class="sxs-lookup"><span data-stu-id="bf57f-107">DESCRIPTION</span></span>

<span data-ttu-id="bf57f-108">`Send-MailMessage`Cmdlet은 PowerShell 내에서 전자 메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-108">The `Send-MailMessage` cmdlet sends an email message from within PowerShell.</span></span>

<span data-ttu-id="bf57f-109">SMTP (Simple Mail Transfer Protocol) 서버를 지정 해야 합니다. 그렇지 `Send-MailMessage` 않으면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-109">You must specify a Simple Mail Transfer Protocol (SMTP) server or the `Send-MailMessage` command fails.</span></span> <span data-ttu-id="bf57f-110">**Smtp 서버** 매개 변수를 사용 하거나 `$PSEmailServer` 변수를 유효한 SMTP 서버로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-110">Use the **SmtpServer** parameter or set the `$PSEmailServer` variable to a valid SMTP server.</span></span>
<span data-ttu-id="bf57f-111">에 할당 된 값은 `$PSEmailServer` PowerShell에 대 한 기본 SMTP 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-111">The value assigned to `$PSEmailServer` is the default SMTP setting for PowerShell.</span></span> <span data-ttu-id="bf57f-112">자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf57f-112">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

> [!WARNING]
> <span data-ttu-id="bf57f-113">`Send-MailMessage`Cmdlet은 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-113">The `Send-MailMessage` cmdlet is obsolete.</span></span> <span data-ttu-id="bf57f-114">이 cmdlet은 SMTP 서버에 대 한 보안 연결을 보장 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-114">This cmdlet does not guarantee secure connections to SMTP servers.</span></span> <span data-ttu-id="bf57f-115">PowerShell에서 즉시 대체를 사용할 수 있는 것은 아니지만를 사용 하지 않는 것이 좋습니다 `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="bf57f-115">While there is no immediate replacement available in PowerShell, we recommend you do not use `Send-MailMessage`.</span></span> <span data-ttu-id="bf57f-116">자세한 내용은 [플랫폼 호환성 참고 DE0005](https://aka.ms/SendMailMessage)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf57f-116">For more information, see [Platform Compatibility note DE0005](https://aka.ms/SendMailMessage).</span></span>

## <span data-ttu-id="bf57f-117">예제</span><span class="sxs-lookup"><span data-stu-id="bf57f-117">EXAMPLES</span></span>

### <span data-ttu-id="bf57f-118">예제 1: 한 사용자에서 다른 사용자에 게 전자 메일 보내기</span><span class="sxs-lookup"><span data-stu-id="bf57f-118">Example 1: Send an email from one person to another person</span></span>

<span data-ttu-id="bf57f-119">이 예에서는 한 사람에서 다른 사람에 게 전자 메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-119">This example sends an email message from one person to another person.</span></span>

<span data-ttu-id="bf57f-120">**From**, **To** 및 **Subject** 매개 변수는에 필요 `Send-MailMessage` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-120">The **From**, **To**, and **Subject** parameters are required by `Send-MailMessage`.</span></span> <span data-ttu-id="bf57f-121">이 예에서는 `$PSEmailServer` SMTP 서버에 대 한 기본 변수를 사용 하므로 **smtp 서버** 매개 변수는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-121">This example uses the default `$PSEmailServer` variable for the SMTP server, so the **SmtpServer** parameter is not needed.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

<span data-ttu-id="bf57f-122">`Send-MailMessage`Cmdlet은 **From** 매개 변수를 사용 하 여 메시지의 보낸 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-122">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="bf57f-123">**To** 매개 변수는 메시지의 받는 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-123">The **To** parameter specifies the message's recipient.</span></span> <span data-ttu-id="bf57f-124">선택적 **본문** 매개 변수가 포함 되어 있지 않으므로 **Subject** 매개 변수는 텍스트 문자열 **테스트 메일** 을 메시지로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-124">The **Subject** parameter uses the text string **Test mail** as the message because the optional **Body** parameter is not included.</span></span>

### <span data-ttu-id="bf57f-125">예제 2: 첨부 파일 보내기</span><span class="sxs-lookup"><span data-stu-id="bf57f-125">Example 2: Send an attachment</span></span>

<span data-ttu-id="bf57f-126">이 예에서는 첨부 파일이 있는 전자 메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-126">This example sends an email message with an attachment.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

<span data-ttu-id="bf57f-127">`Send-MailMessage`Cmdlet은 **From** 매개 변수를 사용 하 여 메시지의 보낸 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-127">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="bf57f-128">**To** 매개 변수는 메시지의 받는 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-128">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="bf57f-129">**Subject** 매개 변수는 메시지의 내용을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-129">The **Subject** parameter describes the content of the message.</span></span> <span data-ttu-id="bf57f-130">**Body** 매개 변수는 메시지의 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-130">The **Body** parameter is the content of the message.</span></span>

<span data-ttu-id="bf57f-131">**첨부** 파일 매개 변수는 현재 디렉터리에서 전자 메일 메시지에 첨부 된 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-131">The **Attachments** parameter specifies the file in the current directory that is attached to the email message.</span></span> <span data-ttu-id="bf57f-132">**Priority** 매개 변수는 메시지를 **높은** 우선 순위로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-132">The **Priority** parameter sets the message to **High** priority.</span></span> <span data-ttu-id="bf57f-133">**-DeliveryNotificationOption** 매개 변수는 **Onsuccess** 및 **onsuccess** 의 두 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-133">The **-DeliveryNotificationOption** parameter specifies two values, **OnSuccess** and **OnFailure**.</span></span> <span data-ttu-id="bf57f-134">발신자는 메시지 배달의 성공 또는 실패를 확인 하는 전자 메일 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-134">The sender will receive email notifications to confirm the success or failure of the message delivery.</span></span>
<span data-ttu-id="bf57f-135">**Smtp 서버** 매개 변수는 SMTP 서버를 **smtp.fabrikam.com** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-135">The **SmtpServer** parameter sets the SMTP server to **smtp.fabrikam.com**.</span></span>

### <span data-ttu-id="bf57f-136">예 3: 메일 그룹에 전자 메일 보내기</span><span class="sxs-lookup"><span data-stu-id="bf57f-136">Example 3: Send email to a mailing list</span></span>

<span data-ttu-id="bf57f-137">이 예에서는 메일 그룹에 전자 메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-137">This example sends an email message to a mailing list.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

<span data-ttu-id="bf57f-138">`Send-MailMessage`Cmdlet은 **From** 매개 변수를 사용 하 여 메시지의 보낸 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-138">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="bf57f-139">**To** 매개 변수는 메시지의 받는 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-139">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="bf57f-140">**참조** 매개 변수는 지정 된 받는 사람에 게 메시지의 복사본을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-140">The **Cc** parameter sends a copy of the message to the specified recipient.</span></span> <span data-ttu-id="bf57f-141">**Bcc** 매개 변수는 메시지의 블라인드 복사본을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-141">The **Bcc** parameter sends a blind copy of the message.</span></span> <span data-ttu-id="bf57f-142">블라인드 복사는 다른 받는 사람에 게 서 숨겨진 전자 메일 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-142">A blind copy is an email address that is hidden from the other recipients.</span></span> <span data-ttu-id="bf57f-143">**Subject** 매개 변수는 선택적 **본문** 매개 변수가 포함 되지 않기 때문에 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-143">The **Subject** parameter is the message because the optional **Body** parameter is not included.</span></span>

<span data-ttu-id="bf57f-144">**Credential** 매개 변수는 도메인 관리자의 자격 증명을 사용 하 여 메시지를 전송 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-144">The **Credential** parameter specifies a domain administrator's credentials are used to send the message.</span></span> <span data-ttu-id="bf57f-145">**UseSsl** 매개 변수는 SSL (Secure Socket Layer)이 보안 연결을 생성 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-145">The **UseSsl** parameter specifies that Secure Socket Layer (SSL) creates a secure connection.</span></span>

## <span data-ttu-id="bf57f-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bf57f-146">PARAMETERS</span></span>

### <span data-ttu-id="bf57f-147">-첨부 파일</span><span class="sxs-lookup"><span data-stu-id="bf57f-147">-Attachments</span></span>

<span data-ttu-id="bf57f-148">메일 메시지에 첨부할 파일의 경로와 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-148">Specifies the path and file names of files to be attached to the email message.</span></span> <span data-ttu-id="bf57f-149">이 매개 변수를 사용 하거나 경로 및 파일 이름을로 파이프 할 수 있습니다 `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="bf57f-149">You can use this parameter or pipe the paths and file names to `Send-MailMessage`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-150">-Bcc</span><span class="sxs-lookup"><span data-stu-id="bf57f-150">-Bcc</span></span>

<span data-ttu-id="bf57f-151">메일의 복사본을 받는 전자 메일 주소를 지정 하지만 메시지의 받는 사람으로는 나열 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-151">Specifies the email addresses that receive a copy of the mail but are not listed as recipients of the message.</span></span> <span data-ttu-id="bf57f-152">이름 (선택 사항) 및 전자 메일 주소를 입력 합니다 (예:) `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="bf57f-152">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-153">-본문</span><span class="sxs-lookup"><span data-stu-id="bf57f-153">-Body</span></span>

<span data-ttu-id="bf57f-154">전자 메일 메시지의 내용을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-154">Specifies the content of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-155">-BodyAsHtml</span><span class="sxs-lookup"><span data-stu-id="bf57f-155">-BodyAsHtml</span></span>

<span data-ttu-id="bf57f-156">**Body** 매개 변수 값에 HTML이 포함 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-156">Specifies that the value of the **Body** parameter contains HTML.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-157">-Cc</span><span class="sxs-lookup"><span data-stu-id="bf57f-157">-Cc</span></span>

<span data-ttu-id="bf57f-158">전자 메일 메시지의 CC (참조)를 보낼 전자 메일 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-158">Specifies the email addresses to which a carbon copy (CC) of the email message is sent.</span></span> <span data-ttu-id="bf57f-159">이름 (선택 사항) 및 전자 메일 주소를 입력 합니다 (예:) `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="bf57f-159">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-160">-Credential</span><span class="sxs-lookup"><span data-stu-id="bf57f-160">-Credential</span></span>

<span data-ttu-id="bf57f-161">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-161">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="bf57f-162">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-162">The default is the current user.</span></span>

<span data-ttu-id="bf57f-163">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-163">Type a user name, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="bf57f-164">또는 예를 들어 cmdlet의 개체와 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="bf57f-164">Or, enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="bf57f-165">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-165">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="bf57f-166">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="bf57f-166">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-167">-DeliveryNotificationOption</span><span class="sxs-lookup"><span data-stu-id="bf57f-167">-DeliveryNotificationOption</span></span>

<span data-ttu-id="bf57f-168">전자 메일 메시지에 대 한 배달 알림 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-168">Specifies the delivery notification options for the email message.</span></span> <span data-ttu-id="bf57f-169">값을 여러 개 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-169">You can specify multiple values.</span></span>
<span data-ttu-id="bf57f-170">기본값은 없음입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-170">None is the default value.</span></span> <span data-ttu-id="bf57f-171">이 매개 변수에 대 한 별칭은 ' d ' **입니다.**</span><span class="sxs-lookup"><span data-stu-id="bf57f-171">The alias for this parameter is **DNO**.</span></span>

<span data-ttu-id="bf57f-172">배달 알림은 **From** 매개 변수의 주소로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-172">The delivery notifications are sent to the address in the **From** parameter.</span></span>

<span data-ttu-id="bf57f-173">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-173">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="bf57f-174">`None`: 알림이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-174">`None`: No notification.</span></span>
- <span data-ttu-id="bf57f-175">`OnSuccess`: 배달에 성공 하면 알립니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-175">`OnSuccess`: Notify if the delivery is successful.</span></span>
- <span data-ttu-id="bf57f-176">`OnFailure`: 배달이 실패 한 경우에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-176">`OnFailure`: Notify if the delivery is unsuccessful.</span></span>
- <span data-ttu-id="bf57f-177">`Delay`: 배달이 지연 되 면 알립니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-177">`Delay`: Notify if the delivery is delayed.</span></span>
- <span data-ttu-id="bf57f-178">`Never`: 알리지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-178">`Never`: Never notify.</span></span>

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-179">-Encoding</span><span class="sxs-lookup"><span data-stu-id="bf57f-179">-Encoding</span></span>

<span data-ttu-id="bf57f-180">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-180">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="bf57f-181">기본값은 `utf8NoBOM`입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-181">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="bf57f-182">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-182">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="bf57f-183">`ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-183">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="bf57f-184">`bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-184">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="bf57f-185">`bigendianutf32`: 빅 endian 바이트 순서를 사용 하 여 u t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-185">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="bf57f-186">`oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-186">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="bf57f-187">`unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-187">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="bf57f-188">`utf7`: UTF-7 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-188">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="bf57f-189">`utf8`: UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-189">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="bf57f-190">`utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-190">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="bf57f-191">`utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-191">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="bf57f-192">`utf32`: U t f-32 형식으로 인코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-192">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="bf57f-193">PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="bf57f-193">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="bf57f-194">자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf57f-194">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-195">-시작</span><span class="sxs-lookup"><span data-stu-id="bf57f-195">-From</span></span>

<span data-ttu-id="bf57f-196">**From** 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-196">The **From** parameter is required.</span></span> <span data-ttu-id="bf57f-197">이 매개 변수는 보낸 사람의 전자 메일 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-197">This parameter specifies the sender's email address.</span></span> <span data-ttu-id="bf57f-198">이름 (선택 사항) 및 전자 메일 주소 (예:)를 입력 `Name <someone@fabrikam.com>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-198">Enter a name (optional) and email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-199">-Port</span><span class="sxs-lookup"><span data-stu-id="bf57f-199">-Port</span></span>

<span data-ttu-id="bf57f-200">대체 SMTP 서버의 대체 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-200">Specifies an alternate port on the SMTP server.</span></span> <span data-ttu-id="bf57f-201">기본값은 SMTP 포트인 25입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-201">The default value is 25, which is the default SMTP port.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-202">-Priority</span><span class="sxs-lookup"><span data-stu-id="bf57f-202">-Priority</span></span>

<span data-ttu-id="bf57f-203">전자 메일 메시지의 우선 순위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-203">Specifies the priority of the email message.</span></span> <span data-ttu-id="bf57f-204">Normal이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-204">Normal is the default.</span></span> <span data-ttu-id="bf57f-205">이 매개 변수에 허용 되는 값은 Normal, High 및 Low입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-205">The acceptable values for this parameter are Normal, High, and Low.</span></span>

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-206">-ReplyTo</span><span class="sxs-lookup"><span data-stu-id="bf57f-206">-ReplyTo</span></span>

<span data-ttu-id="bf57f-207">이 메시지에 회신 하는 데 사용할 추가 전자 메일 주소 (보낸 사람 주소 제외)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-207">Specifies additional email addresses (other than the From address) to use to reply to this message.</span></span>
<span data-ttu-id="bf57f-208">이름 (선택 사항) 및 전자 메일 주소를 입력 합니다 (예:) `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="bf57f-208">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

<span data-ttu-id="bf57f-209">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-209">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-210">-Smtp 서버</span><span class="sxs-lookup"><span data-stu-id="bf57f-210">-SmtpServer</span></span>

<span data-ttu-id="bf57f-211">전자 메일 메시지를 보내는 SMTP 서버의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-211">Specifies the name of the SMTP server that sends the email message.</span></span>

<span data-ttu-id="bf57f-212">기본값은 기본 `$PSEmailServer` 설정 변수의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-212">The default value is the value of the `$PSEmailServer` preference variable.</span></span> <span data-ttu-id="bf57f-213">기본 설정 변수를 설정 하지 않은 경우이 매개 변수를 사용 하지 않으면 `Send-MailMessage` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-213">If the preference variable is not set and this parameter is not used, the `Send-MailMessage` command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-214">-주체</span><span class="sxs-lookup"><span data-stu-id="bf57f-214">-Subject</span></span>

<span data-ttu-id="bf57f-215">**Subject** 매개 변수는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-215">The **Subject** parameter isn't required.</span></span> <span data-ttu-id="bf57f-216">이 매개 변수는 전자 메일 메시지의 제목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-216">This parameter specifies the subject of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-217">-To</span><span class="sxs-lookup"><span data-stu-id="bf57f-217">-To</span></span>

<span data-ttu-id="bf57f-218">**To** 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-218">The **To** parameter is required.</span></span> <span data-ttu-id="bf57f-219">이 매개 변수는 받는 사람의 전자 메일 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-219">This parameter specifies the recipient's email address.</span></span> <span data-ttu-id="bf57f-220">받는 사람이 여러 개인 경우 해당 주소를 쉼표 ()로 구분 `,` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-220">If there are multiple recipients, separate their addresses with a comma (`,`).</span></span> <span data-ttu-id="bf57f-221">이름 (선택 사항) 및 전자 메일 주소를 입력 합니다 (예:) `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="bf57f-221">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-222">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="bf57f-222">-UseSsl</span></span>

<span data-ttu-id="bf57f-223">SSL (SSL(Secure Sockets Layer)) 프로토콜은 메일을 보내기 위해 원격 컴퓨터에 대 한 보안 연결을 설정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-223">The Secure Sockets Layer (SSL) protocol is used to establish a secure connection to the remote computer to send mail.</span></span> <span data-ttu-id="bf57f-224">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-224">By default, SSL is not used.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf57f-225">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bf57f-225">CommonParameters</span></span>

<span data-ttu-id="bf57f-226">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bf57f-226">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bf57f-227">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf57f-227">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bf57f-228">입력</span><span class="sxs-lookup"><span data-stu-id="bf57f-228">INPUTS</span></span>

### <span data-ttu-id="bf57f-229">System.String</span><span class="sxs-lookup"><span data-stu-id="bf57f-229">System.String</span></span>

<span data-ttu-id="bf57f-230">첨부 파일의 경로 및 파일 이름을로 파이프 할 수 있습니다 `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="bf57f-230">You can pipe the path and file names of attachments to `Send-MailMessage`.</span></span>

## <span data-ttu-id="bf57f-231">출력</span><span class="sxs-lookup"><span data-stu-id="bf57f-231">OUTPUTS</span></span>

### <span data-ttu-id="bf57f-232">없음</span><span class="sxs-lookup"><span data-stu-id="bf57f-232">None</span></span>

<span data-ttu-id="bf57f-233">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf57f-233">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="bf57f-234">참고</span><span class="sxs-lookup"><span data-stu-id="bf57f-234">NOTES</span></span>

## <span data-ttu-id="bf57f-235">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bf57f-235">RELATED LINKS</span></span>

[<span data-ttu-id="bf57f-236">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="bf57f-236">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="bf57f-237">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="bf57f-237">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)
