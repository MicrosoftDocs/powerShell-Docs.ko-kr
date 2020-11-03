---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/unprotect-cmsmessage?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unprotect-CmsMessage
ms.openlocfilehash: 7d33d6b5ffe9a2a4807d864c6acb2021fff88e01
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2020
ms.locfileid: "93217961"
---
# Unprotect-CmsMessage

## 개요
암호화 메시지 구문 형식을 사용 하 여 암호화 된 콘텐츠를 해독 합니다.

## SYNTAX

### ByWinEvent (기본값)

```
Unprotect-CmsMessage [-EventLogRecord] <PSObject> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

### ByContent

```
Unprotect-CmsMessage [-Content] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### ByPath

```
Unprotect-CmsMessage [-Path] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### ByLiteralPath

```
Unprotect-CmsMessage [-LiteralPath] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

## 설명

`Unprotect-CmsMessage`Cmdlet은 CMS (암호화 메시지 구문) 형식을 사용 하 여 암호화 된 콘텐츠의 암호를 해독 합니다.

CMS cmdlet은 [RFC5652](https://tools.ietf.org/html/rfc5652)에 설명 된 대로 암호화 된 메시지를 보호 하기 위해 IETF 표준 형식을 사용 하 여 콘텐츠의 암호화 및 암호 해독을 지원 합니다.

CMS 암호화 표준은 공개 키 암호화를 사용 합니다. 여기서는 콘텐츠를 암호화 하는 데 사용 되는 키 (공개 키)와 콘텐츠를 암호 해독 하는 데 사용 되는 키 (개인 키)가 구분 됩니다. 공개 키는 광범위하게 공유할 수 있으며 중요한 데이터가 아닙니다. 콘텐츠가 이 퍼블릭 키로 암호화된 경우 프라이빗 키로만 암호 해독할 수 있습니다. 자세한 내용은 [공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조하세요.

`Unprotect-CmsMessage` CMS 형식으로 암호화 된 콘텐츠를 해독 합니다. 이 cmdlet을 실행 하 여 cmdlet을 실행 하 여 암호화 한 콘텐츠의 암호를 해독할 수 있습니다 `Protect-CmsMessage` . 암호화 된 내용에 대 한 경로를 통해 암호화 이벤트 로그 레코드 ID 번호를 기준으로 암호 해독 하려는 콘텐츠를 지정할 수 있습니다. `Unprotect-CmsMessage`Cmdlet은 암호 해독 된 콘텐츠를 반환 합니다.

> [!NOTE]
> 이 cmdlet은 Windows 에서만 사용할 수 있습니다.

## 예제

### 예제 1: 메시지 암호 해독

다음 예제에서는 리터럴 경로에 있는 콘텐츠의 암호를 해독 `C:\Users\Test\Documents\PowerShell` 합니다. 필수 **To** 매개 변수 값의 경우이 예제에서는 암호화를 수행 하는 데 사용 된 인증서의 지문을 사용 합니다. 해독 된 메시지 "새 중단 모두 실행 명령"이 결과에 해당 합니다.

```powershell
$parameters = @{
  LiteralPath = "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
  To = '0f 8j b1 ab e0 ce 35 1d 67 d2 f2 6f a2 d2 00 cl 22 z9 m9 85'
}
Unprotect-CmsMessage -LiteralPath @parameters
```

```Output
Try the new Break All command
```

## PARAMETERS

### -콘텐츠

암호화 된 문자열 또는 암호화 된 문자열을 포함 하는 변수를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -EventLogRecord

CMS 암호화 작업을 나타내는 이벤트 로그 레코드 ID를 지정 합니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByWinEvent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -IncludeContext

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

### -LiteralPath

해독 하려는 암호화 된 콘텐츠의 경로를 지정 합니다. **Path** 와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드 문자로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

해독 하려는 암호화 된 콘텐츠의 경로를 지정 합니다.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -To

다음 형식으로 식별 된 하나 이상의 CMS 메시지 받는 사람을 지정 합니다.

- 실제 인증서 (인증서 공급자에서 검색 됨)
- 인증서를 포함 하는 파일의 경로입니다.
- 인증서를 포함 하는 디렉터리의 경로입니다.
- 인증서의 지문 (인증서 저장소를 찾는 데 사용 됨)
- 인증서 저장소를 찾는 데 사용 되는 인증서의 주체 이름입니다.

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### EventLogRecord 또는 System.string이 있습니다.

암호화 된 콘텐츠를 포함 하는 개체를로 파이프 할 수 있습니다 `Unprotect-CmsMessage` .

## 출력

### System.String

암호화 되지 않은 메시지입니다.

## 참고

## 관련 링크

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-CmsMessage](Get-CmsMessage.md)

[Protect-CmsMessage](Protect-CmsMessage.md)
