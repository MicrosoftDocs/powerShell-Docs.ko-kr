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
# Send-MailMessage

## 개요
이메일 메시지를 보냅니다.

## SYNTAX

### 모두

```
Send-MailMessage [-To] <string[]> [-Subject] <string> [[-Body] <string>] [[-SmtpServer] <string>]
 -From <string> [-Attachments <string[]>] [-Bcc <string[]>] [-BodyAsHtml] [-Encoding <Encoding>]
 [-Cc <string[]>] [-DeliveryNotificationOption <DeliveryNotificationOptions>]
 [-Priority <MailPriority>] [-Credential <pscredential>] [-UseSsl] [-Port <int>]
 [<CommonParameters>]
```

## 설명

`Send-MailMessage`Cmdlet은 PowerShell 내에서 전자 메일 메시지를 보냅니다.

SMTP (Simple Mail Transfer Protocol) 서버를 지정 해야 합니다. 그렇지 `Send-MailMessage` 않으면 명령이 실패 합니다. **Smtp 서버** 매개 변수를 사용 하거나 `$PSEmailServer` 변수를 유효한 SMTP 서버로 설정 합니다.
에 할당 된 값은 `$PSEmailServer` PowerShell에 대 한 기본 SMTP 설정입니다. 자세한 내용은 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.

> [!WARNING]
> `Send-MailMessage`Cmdlet은 사용 되지 않습니다. 이 cmdlet은 SMTP 서버에 대 한 보안 연결을 보장 하지 않습니다. PowerShell에서 즉시 대체를 사용할 수 있는 것은 아니지만를 사용 하지 않는 것이 좋습니다 `Send-MailMessage` . 자세한 내용은 [플랫폼 호환성 참고 DE0005](https://aka.ms/SendMailMessage)를 참조 하세요.

## 예제

### 예제 1: 한 사용자에서 다른 사용자에 게 전자 메일 보내기

이 예에서는 한 사람에서 다른 사람에 게 전자 메일 메시지를 보냅니다.

**From** , **To** 및 **Subject** 매개 변수는에 필요 `Send-MailMessage` 합니다. 이 예에서는 `$PSEmailServer` SMTP 서버에 대 한 기본 변수를 사용 하므로 **smtp 서버** 매개 변수는 필요 하지 않습니다.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>' -Subject 'Test mail'
```

`Send-MailMessage`Cmdlet은 **From** 매개 변수를 사용 하 여 메시지의 보낸 사람을 지정 합니다. **To** 매개 변수는 메시지의 받는 사람을 지정 합니다. 선택적 **본문** 매개 변수가 포함 되어 있지 않으므로 **Subject** 매개 변수는 텍스트 문자열 **테스트 메일** 을 메시지로 사용 합니다.

### 예제 2: 첨부 파일 보내기

이 예에서는 첨부 파일이 있는 전자 메일 메시지를 보냅니다.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'User02 <user02@fabrikam.com>', 'User03 <user03@fabrikam.com>' -Subject 'Sending the Attachment' -Body "Forgot to send the attachment. Sending now." -Attachments .\data.csv -Priority High -DeliveryNotificationOption OnSuccess, OnFailure -SmtpServer 'smtp.fabrikam.com'
```

`Send-MailMessage`Cmdlet은 **From** 매개 변수를 사용 하 여 메시지의 보낸 사람을 지정 합니다. **To** 매개 변수는 메시지의 받는 사람을 지정 합니다. **Subject** 매개 변수는 메시지의 내용을 설명 합니다. **Body** 매개 변수는 메시지의 내용입니다.

**첨부** 파일 매개 변수는 현재 디렉터리에서 전자 메일 메시지에 첨부 된 파일을 지정 합니다. **Priority** 매개 변수는 메시지를 **높은** 우선 순위로 설정 합니다. **-DeliveryNotificationOption** 매개 변수는 **Onsuccess** 및 **onsuccess** 의 두 값을 지정 합니다. 발신자는 메시지 배달의 성공 또는 실패를 확인 하는 전자 메일 알림을 받습니다.
**Smtp 서버** 매개 변수는 SMTP 서버를 **smtp.fabrikam.com** 로 설정 합니다.

### 예 3: 메일 그룹에 전자 메일 보내기

이 예에서는 메일 그룹에 전자 메일 메시지를 보냅니다.

```powershell
Send-MailMessage -From 'User01 <user01@fabrikam.com>' -To 'ITGroup <itdept@fabrikam.com>' -Cc 'User02 <user02@fabrikam.com>' -Bcc 'ITMgr <itmgr@fabrikam.com>' -Subject "Don't forget today's meeting!" -Credential domain01\admin01 -UseSsl
```

`Send-MailMessage`Cmdlet은 **From** 매개 변수를 사용 하 여 메시지의 보낸 사람을 지정 합니다. **To** 매개 변수는 메시지의 받는 사람을 지정 합니다. **참조** 매개 변수는 지정 된 받는 사람에 게 메시지의 복사본을 보냅니다. **Bcc** 매개 변수는 메시지의 블라인드 복사본을 보냅니다. 블라인드 복사는 다른 받는 사람에 게 서 숨겨진 전자 메일 주소입니다. **Subject** 매개 변수는 선택적 **본문** 매개 변수가 포함 되지 않기 때문에 메시지입니다.

**Credential** 매개 변수는 도메인 관리자의 자격 증명을 사용 하 여 메시지를 전송 하도록 지정 합니다. **UseSsl** 매개 변수는 SSL (Secure Socket Layer)이 보안 연결을 생성 하도록 지정 합니다.

## PARAMETERS

### -첨부 파일

메일 메시지에 첨부할 파일의 경로와 파일 이름을 지정 합니다. 이 매개 변수를 사용 하거나 경로 및 파일 이름을로 파이프 할 수 있습니다 `Send-MailMessage` .

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

### -Bcc

메일의 복사본을 받는 전자 메일 주소를 지정 하지만 메시지의 받는 사람으로는 나열 되지 않습니다. 이름 (선택 사항) 및 전자 메일 주소를 입력 합니다 (예:) `Name <someone@fabrikam.com>` .

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

### -본문

전자 메일 메시지의 내용을 지정 합니다.

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

### -BodyAsHtml

**Body** 매개 변수 값에 HTML이 포함 되도록 지정 합니다.

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

### -Cc

전자 메일 메시지의 CC (참조)를 보낼 전자 메일 주소를 지정 합니다. 이름 (선택 사항) 및 전자 메일 주소를 입력 합니다 (예:) `Name <someone@fabrikam.com>` .

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

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 합니다. 또는 예를 들어 cmdlet의 개체와 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

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

### -DeliveryNotificationOption

전자 메일 메시지에 대 한 배달 알림 옵션을 지정 합니다. 값을 여러 개 지정할 수 있습니다.
기본값은 없음입니다. 이 매개 변수에 대 한 별칭은 ' d ' **입니다.**

배달 알림은 **From** 매개 변수의 주소로 보내집니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `None`: 알림이 없습니다.
- `OnSuccess`: 배달에 성공 하면 알립니다.
- `OnFailure`: 배달이 실패 한 경우에 알립니다.
- `Delay`: 배달이 지연 되 면 알립니다.
- `Never`: 알리지 않습니다.

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

### -Encoding

대상 파일의 인코딩 유형을 지정합니다. 기본값은 `Default`입니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `ASCII` ASCII (7 비트) 문자 집합을 사용 합니다.
- `BigEndianUnicode` 에서는 u t f-16을 빅 endian 바이트 순서로 사용 합니다.
- `Default` 시스템의 활성 코드 페이지에 해당 하는 인코딩을 사용 합니다 (일반적으로 ANSI).
- `OEM` 시스템의 현재 OEM 코드 페이지에 해당 하는 인코딩을 사용 합니다.
- `Unicode` 는 u t f-16을 약간 endian 바이트 순서로 사용 합니다.
- `UTF7` 는 u t f-7을 사용 합니다.
- `UTF8` 는 u t f-8을 사용 합니다.
- `UTF32` 는 u t f-32을 작은 endian 바이트 순서로 사용 합니다.

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

### -시작

**From** 매개 변수는 필수입니다. 이 매개 변수는 보낸 사람의 전자 메일 주소를 지정 합니다. 이름 (선택 사항) 및 전자 메일 주소 (예:)를 입력 `Name <someone@fabrikam.com>` 합니다.

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

### -Port

대체 SMTP 서버의 대체 포트를 지정합니다. 기본값은 SMTP 포트인 25입니다.

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

### -Priority

전자 메일 메시지의 우선 순위를 지정 합니다. Normal이 기본값입니다. 이 매개 변수에 허용 되는 값은 Normal, High 및 Low입니다.

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

### -Smtp 서버

전자 메일 메시지를 보내는 SMTP 서버의 이름을 지정 합니다.

기본값은 기본 `$PSEmailServer` 설정 변수의 값입니다. 기본 설정 변수를 설정 하지 않은 경우이 매개 변수를 사용 하지 않으면 `Send-MailMessage` 명령이 실패 합니다.

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

### -주체

**Subject** 매개 변수는 필수입니다. 이 매개 변수는 전자 메일 메시지의 제목을 지정 합니다.

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

### -To

**To** 매개 변수는 필수입니다. 이 매개 변수는 받는 사람의 전자 메일 주소를 지정 합니다. 받는 사람이 여러 개인 경우 해당 주소를 쉼표 ()로 구분 `,` 합니다. 이름 (선택 사항) 및 전자 메일 주소를 입력 합니다 (예:) `Name <someone@fabrikam.com>` .

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

### -UseSsl

SSL (SSL(Secure Sockets Layer)) 프로토콜은 메일을 보내기 위해 원격 컴퓨터에 대 한 보안 연결을 설정 하는 데 사용 됩니다. 기본적으로 SSL은 사용되지 않습니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

첨부 파일의 경로 및 파일 이름을로 파이프 할 수 있습니다 `Send-MailMessage` .

## 출력

### 없음

이 cmdlet은 어떠한 출력도 생성하지 않습니다.

## 참고

## 관련 링크

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)
