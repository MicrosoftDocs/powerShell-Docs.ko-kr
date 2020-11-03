---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Send-MailMessage
ms.openlocfilehash: 6f98c95e6c0144f76393e9d28454833097894512
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213721"
---
# <span data-ttu-id="8cc4b-103">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="8cc4b-103">Send-MailMessage</span></span>

## <span data-ttu-id="8cc4b-104">개요</span><span class="sxs-lookup"><span data-stu-id="8cc4b-104">SYNOPSIS</span></span>
<span data-ttu-id="8cc4b-105">이메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-105">Sends an email message.</span></span>

## <span data-ttu-id="8cc4b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8cc4b-106">SYNTAX</span></span>

### <span data-ttu-id="8cc4b-107">모두</span><span class="sxs-lookup"><span data-stu-id="8cc4b-107">All</span></span>

```
Send-MailMessage [-To] <string[]> [-Subject] <string> [[-Body] <string>] [[-SmtpServer] <string>]
 -From <string> [-Attachments <string[]>] [-Bcc <string[]>] [-BodyAsHtml] [-Encoding <Encoding>]
 [-Cc <string[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 [-Priority <MailPriority>] [-Credential <pscredential>] [-UseSsl] [-Port <int>]
 [<CommonParameters>]
```

## <span data-ttu-id="8cc4b-108">설명</span><span class="sxs-lookup"><span data-stu-id="8cc4b-108">DESCRIPTION</span></span>

<span data-ttu-id="8cc4b-109">`Send-MailMessage`Cmdlet은 PowerShell 내에서 전자 메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-109">The `Send-MailMessage` cmdlet sends an email message from within PowerShell.</span></span>

<span data-ttu-id="8cc4b-110">SMTP (Simple Mail Transfer Protocol) 서버를 지정 해야 합니다. 그렇지 `Send-MailMessage` 않으면 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-110">You must specify a Simple Mail Transfer Protocol (SMTP) server or the `Send-MailMessage` command fails.</span></span> <span data-ttu-id="8cc4b-111">**Smtp 서버** 매개 변수를 사용 하거나 `$PSEmailServer` 변수를 유효한 SMTP 서버로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-111">Use the **SmtpServer** parameter or set the `$PSEmailServer` variable to a valid SMTP server.</span></span>
<span data-ttu-id="8cc4b-112">에 할당 된 값은 `$PSEmailServer` PowerShell에 대 한 기본 SMTP 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-112">The value assigned to `$PSEmailServer` is the default SMTP setting for PowerShell.</span></span> <span data-ttu-id="8cc4b-113">자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-113">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

> [!WARNING]
> <span data-ttu-id="8cc4b-114">`Send-MailMessage`Cmdlet은 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-114">The `Send-MailMessage` cmdlet is obsolete.</span></span> <span data-ttu-id="8cc4b-115">이 cmdlet은 SMTP 서버에 대 한 보안 연결을 보장 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-115">This cmdlet does not guarantee secure connections to SMTP servers.</span></span> <span data-ttu-id="8cc4b-116">PowerShell에서 즉시 대체를 사용할 수 있는 것은 아니지만를 사용 하지 않는 것이 좋습니다 `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="8cc4b-116">While there is no immediate replacement available in PowerShell, we recommend you do not use `Send-MailMessage`.</span></span> <span data-ttu-id="8cc4b-117">자세한 내용은 [플랫폼 호환성 참고 DE0005](https://aka.ms/SendMailMessage)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-117">For more information, see [Platform Compatibility note DE0005](https://aka.ms/SendMailMessage).</span></span>

## <span data-ttu-id="8cc4b-118">예제</span><span class="sxs-lookup"><span data-stu-id="8cc4b-118">EXAMPLES</span></span>

### <span data-ttu-id="8cc4b-119">예제 1: 한 사용자에서 다른 사용자에 게 전자 메일 보내기</span><span class="sxs-lookup"><span data-stu-id="8cc4b-119">Example 1: Send an email from one person to another person</span></span>

<span data-ttu-id="8cc4b-120">이 예에서는 한 사람에서 다른 사람에 게 전자 메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-120">This example sends an email message from one person to another person.</span></span>

<span data-ttu-id="8cc4b-121">**From** , **To** 및 **Subject** 매개 변수는에 필요 `Send-MailMessage` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-121">The **From** , **To** , and **Subject** parameters are required by `Send-MailMessage`.</span></span> <span data-ttu-id="8cc4b-122">이 예에서는 `$PSEmailServer` SMTP 서버에 대 한 기본 변수를 사용 하므로 **smtp 서버** 매개 변수는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-122">This example uses the default `$PSEmailServer` variable for the SMTP server, so the **SmtpServer** parameter is not needed.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

<span data-ttu-id="8cc4b-123">`Send-MailMessage`Cmdlet은 **From** 매개 변수를 사용 하 여 메시지의 보낸 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-123">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="8cc4b-124">**To** 매개 변수는 메시지의 받는 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-124">The **To** parameter specifies the message's recipient.</span></span> <span data-ttu-id="8cc4b-125">선택적 **본문** 매개 변수가 포함 되어 있지 않으므로 **Subject** 매개 변수는 텍스트 문자열 **테스트 메일** 을 메시지로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-125">The **Subject** parameter uses the text string **Test mail** as the message because the optional **Body** parameter is not included.</span></span>

### <span data-ttu-id="8cc4b-126">예제 2: 첨부 파일 보내기</span><span class="sxs-lookup"><span data-stu-id="8cc4b-126">Example 2: Send an attachment</span></span>

<span data-ttu-id="8cc4b-127">이 예에서는 첨부 파일이 있는 전자 메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-127">This example sends an email message with an attachment.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

<span data-ttu-id="8cc4b-128">`Send-MailMessage`Cmdlet은 **From** 매개 변수를 사용 하 여 메시지의 보낸 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-128">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="8cc4b-129">**To** 매개 변수는 메시지의 받는 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-129">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="8cc4b-130">**Subject** 매개 변수는 메시지의 내용을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-130">The **Subject** parameter describes the content of the message.</span></span> <span data-ttu-id="8cc4b-131">**Body** 매개 변수는 메시지의 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-131">The **Body** parameter is the content of the message.</span></span>

<span data-ttu-id="8cc4b-132">**첨부** 파일 매개 변수는 현재 디렉터리에서 전자 메일 메시지에 첨부 된 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-132">The **Attachments** parameter specifies the file in the current directory that is attached to the email message.</span></span> <span data-ttu-id="8cc4b-133">**Priority** 매개 변수는 메시지를 **높은** 우선 순위로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-133">The **Priority** parameter sets the message to **High** priority.</span></span> <span data-ttu-id="8cc4b-134">**-DeliveryNotificationOption** 매개 변수는 **Onsuccess** 및 **onsuccess** 의 두 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-134">The **-DeliveryNotificationOption** parameter specifies two values, **OnSuccess** and **OnFailure** .</span></span> <span data-ttu-id="8cc4b-135">발신자는 메시지 배달의 성공 또는 실패를 확인 하는 전자 메일 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-135">The sender will receive email notifications to confirm the success or failure of the message delivery.</span></span>
<span data-ttu-id="8cc4b-136">**Smtp 서버** 매개 변수는 SMTP 서버를 **smtp.fabrikam.com** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-136">The **SmtpServer** parameter sets the SMTP server to **smtp.fabrikam.com** .</span></span>

### <span data-ttu-id="8cc4b-137">예 3: 메일 그룹에 전자 메일 보내기</span><span class="sxs-lookup"><span data-stu-id="8cc4b-137">Example 3: Send email to a mailing list</span></span>

<span data-ttu-id="8cc4b-138">이 예에서는 메일 그룹에 전자 메일 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-138">This example sends an email message to a mailing list.</span></span>

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

<span data-ttu-id="8cc4b-139">`Send-MailMessage`Cmdlet은 **From** 매개 변수를 사용 하 여 메시지의 보낸 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-139">The `Send-MailMessage` cmdlet uses the **From** parameter to specify the message's sender.</span></span> <span data-ttu-id="8cc4b-140">**To** 매개 변수는 메시지의 받는 사람을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-140">The **To** parameter specifies the message's recipients.</span></span> <span data-ttu-id="8cc4b-141">**참조** 매개 변수는 지정 된 받는 사람에 게 메시지의 복사본을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-141">The **Cc** parameter sends a copy of the message to the specified recipient.</span></span> <span data-ttu-id="8cc4b-142">**Bcc** 매개 변수는 메시지의 블라인드 복사본을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-142">The **Bcc** parameter sends a blind copy of the message.</span></span> <span data-ttu-id="8cc4b-143">블라인드 복사는 다른 받는 사람에 게 서 숨겨진 전자 메일 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-143">A blind copy is an email address that is hidden from the other recipients.</span></span> <span data-ttu-id="8cc4b-144">**Subject** 매개 변수는 선택적 **본문** 매개 변수가 포함 되지 않기 때문에 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-144">The **Subject** parameter is the message because the optional **Body** parameter is not included.</span></span>

<span data-ttu-id="8cc4b-145">**Credential** 매개 변수는 도메인 관리자의 자격 증명을 사용 하 여 메시지를 전송 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-145">The **Credential** parameter specifies a domain administrator's credentials are used to send the message.</span></span> <span data-ttu-id="8cc4b-146">**UseSsl** 매개 변수는 SSL (Secure Socket Layer)이 보안 연결을 생성 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-146">The **UseSsl** parameter specifies that Secure Socket Layer (SSL) creates a secure connection.</span></span>

## <span data-ttu-id="8cc4b-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8cc4b-147">PARAMETERS</span></span>

### <span data-ttu-id="8cc4b-148">-첨부 파일</span><span class="sxs-lookup"><span data-stu-id="8cc4b-148">-Attachments</span></span>

<span data-ttu-id="8cc4b-149">메일 메시지에 첨부할 파일의 경로와 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-149">Specifies the path and file names of files to be attached to the email message.</span></span> <span data-ttu-id="8cc4b-150">이 매개 변수를 사용 하거나 경로 및 파일 이름을로 파이프 할 수 있습니다 `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="8cc4b-150">You can use this parameter or pipe the paths and file names to `Send-MailMessage`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PsPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-151">-Bcc</span><span class="sxs-lookup"><span data-stu-id="8cc4b-151">-Bcc</span></span>

<span data-ttu-id="8cc4b-152">메일의 복사본을 받는 전자 메일 주소를 지정 하지만 메시지의 받는 사람으로는 나열 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-152">Specifies the email addresses that receive a copy of the mail but are not listed as recipients of the message.</span></span> <span data-ttu-id="8cc4b-153">이름 (선택 사항) 및 전자 메일 주소를 입력 합니다 (예:) `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="8cc4b-153">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-154">-본문</span><span class="sxs-lookup"><span data-stu-id="8cc4b-154">-Body</span></span>

<span data-ttu-id="8cc4b-155">전자 메일 메시지의 내용을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-155">Specifies the content of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-156">-BodyAsHtml</span><span class="sxs-lookup"><span data-stu-id="8cc4b-156">-BodyAsHtml</span></span>

<span data-ttu-id="8cc4b-157">**Body** 매개 변수 값에 HTML이 포함 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-157">Specifies that the value of the **Body** parameter contains HTML.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: BAH

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-158">-Cc</span><span class="sxs-lookup"><span data-stu-id="8cc4b-158">-Cc</span></span>

<span data-ttu-id="8cc4b-159">전자 메일 메시지의 CC (참조)를 보낼 전자 메일 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-159">Specifies the email addresses to which a carbon copy (CC) of the email message is sent.</span></span> <span data-ttu-id="8cc4b-160">이름 (선택 사항) 및 전자 메일 주소를 입력 합니다 (예:) `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="8cc4b-160">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="8cc4b-161">-Credential</span></span>

<span data-ttu-id="8cc4b-162">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-162">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="8cc4b-163">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-163">The default is the current user.</span></span>

<span data-ttu-id="8cc4b-164">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-164">Type a user name, such as **User01** or **Domain01\User01** .</span></span> <span data-ttu-id="8cc4b-165">또는 예를 들어 cmdlet의 개체와 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="8cc4b-165">Or, enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="8cc4b-166">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-166">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="8cc4b-167">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="8cc4b-167">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-168">-DeliveryNotificationOption</span><span class="sxs-lookup"><span data-stu-id="8cc4b-168">-DeliveryNotificationOption</span></span>

<span data-ttu-id="8cc4b-169">전자 메일 메시지에 대 한 배달 알림 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-169">Specifies the delivery notification options for the email message.</span></span> <span data-ttu-id="8cc4b-170">값을 여러 개 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-170">You can specify multiple values.</span></span>
<span data-ttu-id="8cc4b-171">기본값은 없음입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-171">None is the default value.</span></span> <span data-ttu-id="8cc4b-172">이 매개 변수에 대 한 별칭은 ' d ' **입니다.**</span><span class="sxs-lookup"><span data-stu-id="8cc4b-172">The alias for this parameter is **DNO** .</span></span>

<span data-ttu-id="8cc4b-173">배달 알림은 **From** 매개 변수의 주소로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-173">The delivery notifications are sent to the address in the **From** parameter.</span></span>

<span data-ttu-id="8cc4b-174">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="8cc4b-175">`None`: 알림이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-175">`None`: No notification.</span></span>
- <span data-ttu-id="8cc4b-176">`OnSuccess`: 배달에 성공 하면 알립니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-176">`OnSuccess`: Notify if the delivery is successful.</span></span>
- <span data-ttu-id="8cc4b-177">`OnFailure`: 배달이 실패 한 경우에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-177">`OnFailure`: Notify if the delivery is unsuccessful.</span></span>
- <span data-ttu-id="8cc4b-178">`Delay`: 배달이 지연 되 면 알립니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-178">`Delay`: Notify if the delivery is delayed.</span></span>
- <span data-ttu-id="8cc4b-179">`Never`: 알리지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-179">`Never`: Never notify.</span></span>

```yaml
Type: System.Net.Mail.DeliveryNotificationOptions
Parameter Sets: (All)
Aliases: DNO
Accepted values: None, OnSuccess, OnFailure, Delay, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-180">-Encoding</span><span class="sxs-lookup"><span data-stu-id="8cc4b-180">-Encoding</span></span>

<span data-ttu-id="8cc4b-181">대상 파일의 인코딩 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-181">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="8cc4b-182">기본값은 `Default`입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-182">The default value is `Default`.</span></span>

<span data-ttu-id="8cc4b-183">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-183">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="8cc4b-184">`ASCII` ASCII (7 비트) 문자 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-184">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="8cc4b-185">`BigEndianUnicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-185">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="8cc4b-186">`Default` 시스템의 활성 코드 페이지에 해당 하는 인코딩을 사용 합니다 (일반적으로 ANSI).</span><span class="sxs-lookup"><span data-stu-id="8cc4b-186">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="8cc4b-187">`OEM` 시스템의 현재 OEM 코드 페이지에 해당 하는 인코딩을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-187">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="8cc4b-188">`Unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-188">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="8cc4b-189">`UTF7` 는 u t f-7을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-189">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="8cc4b-190">`UTF8` 는 u t f-8을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-190">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="8cc4b-191">`UTF32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-191">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases: BE
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-192">-시작</span><span class="sxs-lookup"><span data-stu-id="8cc4b-192">-From</span></span>

<span data-ttu-id="8cc4b-193">**From** 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-193">The **From** parameter is required.</span></span> <span data-ttu-id="8cc4b-194">이 매개 변수는 보낸 사람의 전자 메일 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-194">This parameter specifies the sender's email address.</span></span> <span data-ttu-id="8cc4b-195">이름 (선택 사항) 및 전자 메일 주소 (예:)를 입력 `Name <someone@fabrikam.com>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-195">Enter a name (optional) and email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-196">-Port</span><span class="sxs-lookup"><span data-stu-id="8cc4b-196">-Port</span></span>

<span data-ttu-id="8cc4b-197">대체 SMTP 서버의 대체 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-197">Specifies an alternate port on the SMTP server.</span></span> <span data-ttu-id="8cc4b-198">기본값은 SMTP 포트인 25입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-198">The default value is 25, which is the default SMTP port.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 25
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-199">-Priority</span><span class="sxs-lookup"><span data-stu-id="8cc4b-199">-Priority</span></span>

<span data-ttu-id="8cc4b-200">전자 메일 메시지의 우선 순위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-200">Specifies the priority of the email message.</span></span> <span data-ttu-id="8cc4b-201">Normal이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-201">Normal is the default.</span></span> <span data-ttu-id="8cc4b-202">이 매개 변수에 허용 되는 값은 Normal, High 및 Low입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-202">The acceptable values for this parameter are Normal, High, and Low.</span></span>

```yaml
Type: System.Net.Mail.MailPriority
Parameter Sets: (All)
Aliases:
Accepted values: Normal, High, Low

Required: False
Position: Named
Default value: Normal
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-203">-Smtp 서버</span><span class="sxs-lookup"><span data-stu-id="8cc4b-203">-SmtpServer</span></span>

<span data-ttu-id="8cc4b-204">전자 메일 메시지를 보내는 SMTP 서버의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-204">Specifies the name of the SMTP server that sends the email message.</span></span>

<span data-ttu-id="8cc4b-205">기본값은 기본 `$PSEmailServer` 설정 변수의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-205">The default value is the value of the `$PSEmailServer` preference variable.</span></span> <span data-ttu-id="8cc4b-206">기본 설정 변수를 설정 하지 않은 경우이 매개 변수를 사용 하지 않으면 `Send-MailMessage` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-206">If the preference variable is not set and this parameter is not used, the `Send-MailMessage` command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ComputerName

Required: False
Position: 3
Default value: $PSEmailServer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-207">-주체</span><span class="sxs-lookup"><span data-stu-id="8cc4b-207">-Subject</span></span>

<span data-ttu-id="8cc4b-208">**Subject** 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-208">The **Subject** parameter is required.</span></span> <span data-ttu-id="8cc4b-209">이 매개 변수는 전자 메일 메시지의 제목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-209">This parameter specifies the subject of the email message.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sub

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-210">-To</span><span class="sxs-lookup"><span data-stu-id="8cc4b-210">-To</span></span>

<span data-ttu-id="8cc4b-211">**To** 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-211">The **To** parameter is required.</span></span> <span data-ttu-id="8cc4b-212">이 매개 변수는 받는 사람의 전자 메일 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-212">This parameter specifies the recipient's email address.</span></span> <span data-ttu-id="8cc4b-213">받는 사람이 여러 개인 경우 해당 주소를 쉼표 ()로 구분 `,` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-213">If there are multiple recipients, separate their addresses with a comma (`,`).</span></span> <span data-ttu-id="8cc4b-214">이름 (선택 사항) 및 전자 메일 주소를 입력 합니다 (예:) `Name <someone@fabrikam.com>` .</span><span class="sxs-lookup"><span data-stu-id="8cc4b-214">Enter names (optional) and the email address, such as `Name <someone@fabrikam.com>`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-215">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="8cc4b-215">-UseSsl</span></span>

<span data-ttu-id="8cc4b-216">SSL (SSL(Secure Sockets Layer)) 프로토콜은 메일을 보내기 위해 원격 컴퓨터에 대 한 보안 연결을 설정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-216">The Secure Sockets Layer (SSL) protocol is used to establish a secure connection to the remote computer to send mail.</span></span> <span data-ttu-id="8cc4b-217">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-217">By default, SSL is not used.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8cc4b-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8cc4b-218">CommonParameters</span></span>

<span data-ttu-id="8cc4b-219">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8cc4b-220">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8cc4b-221">입력</span><span class="sxs-lookup"><span data-stu-id="8cc4b-221">INPUTS</span></span>

### <span data-ttu-id="8cc4b-222">System.String</span><span class="sxs-lookup"><span data-stu-id="8cc4b-222">System.String</span></span>

<span data-ttu-id="8cc4b-223">첨부 파일의 경로 및 파일 이름을로 파이프 할 수 있습니다 `Send-MailMessage` .</span><span class="sxs-lookup"><span data-stu-id="8cc4b-223">You can pipe the path and file names of attachments to `Send-MailMessage`.</span></span>

## <span data-ttu-id="8cc4b-224">출력</span><span class="sxs-lookup"><span data-stu-id="8cc4b-224">OUTPUTS</span></span>

### <span data-ttu-id="8cc4b-225">없음</span><span class="sxs-lookup"><span data-stu-id="8cc4b-225">None</span></span>

<span data-ttu-id="8cc4b-226">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc4b-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8cc4b-227">참고</span><span class="sxs-lookup"><span data-stu-id="8cc4b-227">NOTES</span></span>

## <span data-ttu-id="8cc4b-228">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8cc4b-228">RELATED LINKS</span></span>

[<span data-ttu-id="8cc4b-229">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="8cc4b-229">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="8cc4b-230">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="8cc4b-230">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)
