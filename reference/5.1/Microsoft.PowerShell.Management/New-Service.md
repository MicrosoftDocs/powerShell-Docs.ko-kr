---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 758b0a8ef9a5f65f0e7cfa7f3633086cf9f0445d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891771"
---
# New-Service

## 개요
새 Windows 서비스를 만듭니다.

## SYNTAX

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## 설명

`New-Service`Cmdlet은 레지스트리 및 서비스 데이터베이스에 Windows 서비스에 대 한 새 항목을 만듭니다. 새 서비스에는 서비스 중 실행 되는 실행 파일이 필요 합니다.

이 cmdlet의 매개 변수를 사용하면 서비스의 표시 이름, 설명, 시작 유형 및 종속성을 설정할 수 있습니다.

## 예제

### 예제 1: 서비스 만들기

```powershell
New-Service -Name "TestService" -BinaryPathName '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
```

이 명령은 TestService 라는 서비스를 만듭니다.

### 예제 2: 설명, 시작 유형 및 표시 이름을 포함 하는 서비스 만들기

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

이 명령은 TestService 라는 서비스를 만듭니다. 의 매개 변수를 사용 하 여 `New-Service` 새 서비스의 설명, 시작 유형 및 표시 이름을 지정 합니다.

### 예 3: 새 서비스 보기

```powershell
Get-CimInstance -ClassName Win32_Service -Filter "Name='testservice'"
```

```Output
ExitCode  : 0
Name      : testservice
ProcessId : 0
StartMode : Auto
State     : Stopped
Status    : OK
```

이 명령은 `Get-CimInstance` 를 사용 하 여 새 서비스에 대 한 **Win32_Service** 개체를 가져옵니다. 이 개체에는 시작 모드와 서비스 설명이 포함되어 있습니다.

### 예제 4: 서비스 삭제

```powershell
sc.exe delete TestService
# - or -
(Get-CimInstance -Class Win32_Service -Filter "name='TestService'").delete()
```

이 예제에서는 TestService 서비스를 삭제할 수 있는 두 가지 방법을 보여 줍니다. 첫 번째 명령은의 delete 옵션을 사용 합니다 `Sc.exe` . 두 번째 명령은에서 반환 하는 **Win32_Service** 개체의 **Delete** 메서드를 사용 합니다 `Get-CimInstance` .

## PARAMETERS

### -BinaryPathName

서비스의 실행 파일 경로를 지정 합니다. 이 매개 변수는 필수적 요소입니다.

서비스 이진 파일의 정규화 된 경로입니다. 경로에 공백이 있는 경우 올바르게 해석 되도록 따옴표로 묶어야 합니다. 예를 들어는 `d:\my share\myservice.exe` 로 지정 해야 합니다 `'"d:\my share\myservice.exe"'` .

경로에는 자동 시작 서비스의 인수도 포함 될 수도 있습니다. 예: `'"d:\myshare\myservice.exe arg1 arg2"'`. 이러한 인수는 서비스 진입점에 전달 됩니다.

자세한 내용은 [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API의 **lpBinaryPathName** 매개 변수를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

서비스에서 [서비스 로그온 계정](/windows/desktop/ad/about-service-logon-accounts)으로 사용 하는 계정을 지정 합니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DependsOn

새 서비스가 종속되는 다른 서비스의 이름을 지정합니다. 여러 서비스 이름을 입력하려면 쉼표를 사용하여 이름을 구분합니다.

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

### -Description

서비스에 대한 설명을 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

서비스의 표시 이름을 지정합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

서비스의 이름을 지정합니다. 이 매개 변수는 필수적 요소입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StartupType

서비스의 시작 유형을 설정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- **자동** -시스템이 시작 되거나 운영 체제에서 서비스를 시작 합니다.
  자동으로 시작된 서비스가 수동으로 시작된 서비스에 따라 달라지는 경우, 시스템 시작 시 수동으로 시작된 서비스도 자동으로 시작됩니다.
- **사용 안 함** -서비스를 사용할 수 없으며 사용자 또는 응용 프로그램에서 시작할 수 없습니다.
- **수동** -서비스 제어 관리자 또는 응용 프로그램을 사용 하 여 수동으로 또는 사용자가 서비스를 시작 합니다.
- **Boot** -서비스가 시스템 로더에서 시작한 장치 드라이버 임을 나타냅니다. 이 값은 디바이스 드라이버에만 유효합니다.
- **시스템** -서비스가 ' IOInitSystem () ' 함수에서 시작한 장치 드라이버 임을 나타냅니다. 이 값은 디바이스 드라이버에만 유효합니다.

 기본값은 **Automatic** 입니다.

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases:
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.ServiceProcess.ServiceController

이 cmdlet은 새 서비스를 나타내는 개체를 반환 합니다.

## 참고

이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

서비스를 삭제 하려면 Sc.exe를 사용 하거나 cmdlet을 사용 `Get-CimInstance` 하 여 서비스를 나타내는 **Win32_Service** 개체를 가져온 다음 **delete** 메서드를 사용 하 여 서비스를 삭제 합니다. 을 반환 하는 개체에는 `Get-Service` 삭제 메서드가 없습니다.

## 관련 링크

[Get-Service](Get-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
