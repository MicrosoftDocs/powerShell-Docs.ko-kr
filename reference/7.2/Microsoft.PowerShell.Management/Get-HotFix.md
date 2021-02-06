---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 5b5b5939d4dcae8a99b1030b533fe6a85bcc601a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603061"
---
# Get-HotFix

## 개요
로컬 또는 원격 컴퓨터에 설치 된 핫픽스를 가져옵니다.

## SYNTAX

### Default (기본값)

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### 설명

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## 설명

`Get-Hotfix`Cmdlet은 로컬 컴퓨터 또는 지정 된 원격 컴퓨터에 설치 된 핫픽스 또는 업데이트를 가져옵니다. 업데이트는 Windows 업데이트, Microsoft 업데이트, Windows Server Update Services 또는 수동으로 설치 하 여 설치할 수 있습니다.

## 예제

### 예 1: 로컬 컴퓨터에서 모든 핫픽스 가져오기

`Get-Hotfix`Cmdlet은 로컬 컴퓨터에 설치 된 모든 핫픽스를 가져옵니다.

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### 예제 2: 문자열로 필터링 된 여러 컴퓨터에서 핫픽스 가져오기

이 `Get-Hotfix` 명령은 매개 변수를 사용 하 여 원격 컴퓨터에 설치 된 핫픽스를 가져옵니다. 결과는 지정 된 설명 문자열을 기준으로 필터링 됩니다.

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

`Get-Hotfix`**Description** 매개 변수 및 별표 () 와일드 카드를 포함 하는 문자열 **보안** 을 사용 하 여 출력을 필터링 합니다 `*` . **ComputerName** 매개 변수는 쉼표로 구분 된 원격 컴퓨터 이름 문자열을 포함 합니다. **Credential** 매개 변수는 원격 컴퓨터에 액세스할 수 있는 권한이 있는 사용자 계정을 지정 하 고 명령을 실행 합니다.

### 예 3: 업데이트가 설치 되어 있는지 확인 하 고 파일에 컴퓨터 이름을 기록 합니다.

이 예제의 명령은 특정 업데이트가 설치 되어 있는지 여부를 확인 합니다. 업데이트가 설치 되지 않은 경우 컴퓨터 이름이 텍스트 파일에 기록 됩니다.

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

`$A`변수에는 텍스트 파일에서 가져온 컴퓨터 이름이 포함 `Get-Content` 됩니다. 의 개체는 `$A` 파이프라인에서로 전송 됩니다 `ForEach-Object` . `if`문은 `Get-Hotfix` Cmdlet에 **id** 매개 변수와 각 컴퓨터 이름에 대 한 특정 id 번호를 사용 합니다. 컴퓨터에 지정 된 핫픽스 Id가 설치 되어 있지 않은 경우 `Add-Content` cmdlet은 파일에 컴퓨터 이름을 기록 합니다.

### 예 4: 로컬 컴퓨터에서 최신 핫픽스 가져오기

이 예제에서는 컴퓨터에 설치 된 최신 핫픽스를 가져옵니다.

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

`Get-Hotfix` 파이프라인의 개체를 cmdlet으로 보냅니다 `Sort-Object` . `Sort-Object` 개체를 오름차순으로 정렬 하 고 **Property** 매개 변수를 사용 하 여 각 **설치** 날짜를 평가 합니다. 배열 표기법은 `[-1]` 가장 최근에 설치 된 핫픽스를 선택 합니다.

## PARAMETERS

### -ComputerName

원격 컴퓨터를 지정합니다. 원격 컴퓨터의 NetBIOS 이름, IP (인터넷 프로토콜) 주소 또는 FQDN (정규화 된 도메인 이름)을 입력 합니다.

**ComputerName** 매개 변수를 지정 하지 않으면가 `Get-Hotfix` 로컬 컴퓨터에서 실행 됩니다.

**ComputerName** 매개 변수는 Windows PowerShell 원격을 사용 하지 않습니다. 컴퓨터가 원격 명령을 실행 하도록 구성 되지 않은 경우 **ComputerName** 매개 변수를 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

컴퓨터에 액세스할 수 있는 권한이 있는 사용자 계정을 지정 하 고 명령을 실행 합니다. 기본값은 현재 사용자입니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

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

### -Description

`Get-HotFix`**Description** 매개 변수를 사용 하 여 핫픽스 유형을 지정 합니다. 와일드카드가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Id

`Get-HotFix`특정 핫픽스 id의 결과를 필터링 합니다. 와일드 카드는 허용 되지 않습니다.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### String

하나 이상의 컴퓨터 이름을 Get-help로 파이프 할 수 있습니다.

## 출력

### Root\CIMV2\ 개체 # Win32_QuickFixEngineering

`Get-HotFix` 컴퓨터의 핫픽스를 나타내는 개체를 반환 합니다.

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

**Win32_QuickFixEngineering** [WMI 클래스](/windows/desktop/WmiSdk/retrieving-a-class) 는 현재 운영 체제에 적용 되는, 일반적으로 QFE (quick fix 공학적) 업데이트 라고 하는 작은 시스템 차원 업데이트를 나타냅니다. 이 클래스는 CBS (구성 요소 기반 서비스)에서 제공 하는 업데이트만 반환 합니다. 이러한 업데이트는 레지스트리에 나열 되지 않습니다. MSI (Microsoft Windows Installer) 또는 [Windows 업데이트](https://update.microsoft.com) 사이트에서 제공 하는 업데이트는 **Win32_QuickFixEngineering** 에서 반환 되지 않습니다. 자세한 내용은 [Win32_QuickFixEngineering 클래스](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)를 참조 하세요.

`Get-HotFix`출력은 운영 체제 마다 다를 수 있습니다.

## 관련 링크

[about_Arrays](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[Add-Content](Add-Content.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Win32_QuickFixEngineering 클래스](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
