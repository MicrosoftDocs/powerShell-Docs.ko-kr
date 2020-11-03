---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 2ff87c8d4b714be3b5be3bfe8f384b4c89c25272
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "93225234"
---
# Get-Credential

## 개요
사용자 이름 및 암호를 기반으로 자격 증명 개체를 가져옵니다.

## SYNTAX

### CredentialSet (기본값)

```
Get-Credential [[-Credential] <PSCredential>] [<CommonParameters>]
```

### MessageSet

```
Get-Credential [-Message <String>] [[-UserName] <String>] [-Title <String>] [<CommonParameters>]
```

## 설명

`Get-Credential`Cmdlet은 지정 된 사용자 이름 및 암호에 대 한 자격 증명 개체를 만듭니다. 보안 작업에서 자격 증명 개체를 사용할 수 있습니다.

Cmdlet은 사용자에 게 `Get-Credential` 암호나 사용자 이름 및 암호를 묻는 메시지를 표시 합니다. **Message** 매개 변수를 사용 하 여 명령줄 프롬프트에서 사용자 지정 메시지를 지정할 수 있습니다.

## 예제

### 예 1

```powershell
$c = Get-Credential
```

이 명령은 자격 증명 개체를 가져와서 `$c` 변수에 저장 합니다.

명령을 입력 하면 사용자 이름 및 암호를 입력 하 라는 메시지가 표시 됩니다. 요청 된 정보를 입력 하면 cmdlet이 사용자의 자격 증명을 나타내는 **PSCredential** 개체를 만들어 변수에 저장 합니다 `$c` .

사용자 인증을 요청하는 cmdlet(예: **Credential** 매개 변수를 사용하는 cmdlet)의 입력으로 이 개체를 사용할 수 있습니다. 그러나 PowerShell과 함께 설치 되는 일부 공급자는 **Credential** 매개 변수를 지원 하지 않습니다.

### 예제 2

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

이러한 명령은 `Get-Credential` WMI(Windows Management Instrumentation) (WMI)를 사용 하 여 컴퓨터를 관리할 수 있도록 cmdlet이 반환 하는 자격 증명 개체를 사용 하 여 원격 컴퓨터에서 사용자를 인증 합니다.

첫 번째 명령은 자격 증명 개체를 가져와서 변수에 저장 합니다 `$c` . 두 번째 명령은 명령에 credential 개체를 사용 합니다 `Get-CimInstance` . 이 명령은 Server01 컴퓨터의 디스크 드라이브 정보를 가져옵니다.

### 예제 3

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

이 명령은 명령에 명령을 포함 하는 방법을 보여 줍니다 `Get-Credential`  `Get-CimInstance` .

이 명령은 cmdlet을 사용 `Get-CimInstance` 하 여 Server01 컴퓨터의 BIOS에 대 한 정보를 가져옵니다. **Credential** 매개 변수를 사용 하 여 사용자, Domain01\User01 및 `Get-Credential` 명령을 **credential** 매개 변수 값으로 인증 합니다.

### 예제 4

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

이 예제에서는 도메인 이름이 없는 사용자 이름을 포함하는 자격 증명을 만들며,

첫 번째 명령은 사용자 이름 User01를 사용 하 여 자격 증명을 가져온 다음 변수에 저장 합니다 `$c` .
두 번째 명령은 생성된 자격 증명 개체의 **Username** 속성 값을 표시합니다.

### 예제 5

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

이 명령은 **PromptForCredential** 메서드를 사용하여 사용자에게 사용자 이름과 암호를 요청합니다. 이 명령은 결과 자격 증명을 변수에 저장 합니다 `$Credential` .

**PromptForCredential** 메서드를 사용 하는 대신 cmdlet을 사용할 수 `Get-Credential` 있습니다. **PromptForCredential** 를 사용 하는 경우 프롬프트에 표시 되는 캡션, 메시지 및 사용자 이름을 지정할 수 있습니다.

자세한 내용은 SDK의 [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) 설명서를 참조 하세요.

### 예제 6

이 예제에서는 `Get-Credential` 사용자에 게 메시지를 표시 하지 않고 반환 되는 개체와 동일한 자격 증명 개체를 만드는 방법을 보여 줍니다. 이 메서드에는 일반 텍스트 암호가 필요하며, 그에 따라 일부 기업의 보안 표준을 위반할 수 있습니다.

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

첫 번째 명령은 사용자 계정 이름을 매개 변수에 저장 합니다 `$User` . 이 값은 "도메인\사용자" 또는 "컴퓨터이름\사용자" 형식이어야 합니다.

두 번째 명령은 cmdlet을 사용 하 여 `ConvertTo-SecureString` 일반 텍스트 암호에서 보안 문자열을 만듭니다. 이 명령은 **AsPlainText** 매개 변수를 사용하여 문자열이 일반 텍스트인 것을 나타내며 **Force** 매개 변수를 사용하여 일반 텍스트를 사용할 경우 발생할 수 있는 위험을 이해하고 있는지 확인합니다.

세 번째 명령은 cmdlet을 사용 하 여 `New-Object` 및 변수의 값에서 **PSCredential** 개체를 만듭니다 `$User` `$PWord` .

### 예제 7

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

이 명령은 cmdlet의 **메시지** 및 **사용자 이름** 매개 변수를 사용 합니다 `Get-Credential` . 이 명령 형식은 공유 스크립트와 함수를 사용하도록 설계되었습니다. 이런 경우, 메시지를 통해 자격 증명이 필요한 이유를 알려 주며 요청이 적합하다는 확신을 줍니다.

### 예제 8

```powershell
Invoke-Command -ComputerName Server01 {Get-Credential Domain01\User02}
```

```Output
PowerShell Credential Request : PowerShell Credential Request
Warning: This credential is being requested by a script or application on the SERVER01 remote computer. Enter your credentials only if you
 trust the remote computer and the application or script requesting it.

Enter your credentials.
Password for user Domain01\User02: ***************

PSComputerName     : Server01
RunspaceId         : 422bdf52-9886-4ada-ab2f-130497c6777f
PSShowComputerName : True
UserName           : Domain01\User01
Password           : System.Security.SecureString
```

이 명령은 Server01 원격 컴퓨터에서 자격 증명을 가져옵니다. 이 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Get-Credential` 원격 컴퓨터에서 명령을 실행 합니다. 출력에는 인증 프롬프트에가 포함 된 원격 보안 메시지가 표시 `Get-Credential` 됩니다.

## PARAMETERS

### -Credential

**User01** 또는 **Domain01\User01** 와 같은 자격 증명의 사용자 이름을 지정 합니다. 매개 변수 이름는 `-Credential` 선택 사항입니다.

명령을 제출 하 고 사용자 이름을 지정 하는 경우 암호를 입력 하 라는 메시지가 표시 됩니다. 이 매개 변수를 생략 하면 사용자 이름과 암호를 입력 하 라는 메시지가 표시 됩니다.

PowerShell 3.0부터 도메인 없이 사용자 이름을 입력 하는 경우는 `Get-Credential` 더 이상 이름 앞에 백슬래시를 삽입 하지 않습니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -메시지

인증 프롬프트에 표시되는 메시지를 지정합니다. 이 매개 변수는 함수나 스크립트에서 사용하도록 설계되었습니다. 메시지를 사용하여 자격 증명을 요청하는 이유와 사용자에게 설명하는 방법을 설명할 수 있습니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Title

콘솔의 인증 프롬프트에 대 한 제목 줄의 텍스트를 설정 합니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

사용자 이름을 지정합니다. 인증 프롬프트에서 사용자 이름에 대한 암호를 요청합니다. 기본적으로 사용자 이름이 비어 있으며 인증 프롬프트에서 사용자 이름과 암호를 모두 요청합니다.

이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: 1
Default value: None (blank)
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.object. PSCredential

`Get-Credential` 자격 증명 개체를 반환 합니다.

## 참고

Credential 매개 변수를 **PSCredential** 사용 하는 `Get-Credential` 것과 같이 사용자 인증을 요청 하는 Cmdlet에서 만드는 PSCredential **Credential** 개체를 사용할 수 있습니다.

**Credential** 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.
PowerShell 3.0부터 및 cmdlet과 같은 select cmdlet에서 지원 됩니다 `Get-Content` `New-PSDrive` .

## 관련 링크

[PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
