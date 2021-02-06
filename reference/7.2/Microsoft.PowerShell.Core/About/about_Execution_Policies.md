---
description: PowerShell 실행 정책에 대해 설명 하 고 관리 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 1a2b8458b39233f96d47a52e3fea21b31e9b3c42
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603303"
---
# <a name="about-execution-policies"></a>실행 정책 정보

## <a name="short-description"></a>간단한 설명
PowerShell 실행 정책에 대해 설명 하 고 관리 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell의 실행 정책은 PowerShell에서 구성 파일을 로드 하 고 스크립트를 실행 하는 조건을 제어 하는 안전 기능입니다. 이 기능은 악의적인 스크립트의 실행을 방지 하는 데 도움이 됩니다.

Windows 컴퓨터에서 로컬 컴퓨터, 현재 사용자 또는 특정 세션에 대 한 실행 정책을 설정할 수 있습니다. 그룹 정책 설정을 사용 하 여 컴퓨터 및 사용자에 대 한 실행 정책을 설정할 수도 있습니다.

로컬 컴퓨터 및 현재 사용자에 대 한 실행 정책이 레지스트리에 저장 됩니다. PowerShell 프로필에서 실행 정책을 설정할 필요가 없습니다.
특정 세션에 대 한 실행 정책은 메모리에만 저장 되며 세션을 닫으면 손실 됩니다.

실행 정책은 사용자 작업을 제한 하는 보안 시스템이 아닙니다. 예를 들어 사용자는 스크립트를 실행할 수 없는 경우 명령줄에서 스크립트 내용을 입력 하 여 정책을 쉽게 우회할 수 있습니다. 대신, 실행 정책은 사용자가 기본 규칙을 설정 하 고 실수로 위반 하지 않도록 방지 하는 데 도움이 됩니다.

비 Windows 컴퓨터의 기본 실행 정책은 **무제한** 이며 변경할 수 없습니다. `Set-ExecutionPolicy`Cmdlet을 사용할 수 있지만 PowerShell에서 지원 되지 않는 콘솔 메시지를 표시 합니다. 는 `Get-ExecutionPolicy` windows가 아닌 플랫폼에서 **무제한** 을 반환 하지만, 이러한 플랫폼은 windows 보안 영역을 구현 하지 않기 때문에이 동작은 **무시** 와 매우 일치 합니다.

## <a name="powershell-execution-policies"></a>PowerShell 실행 정책

이러한 정책을 적용 하는 것은 Windows 플랫폼 에서만 수행 됩니다. PowerShell 실행 정책은 다음과 같습니다.

### <a name="allsigned"></a>AllSigned

- 스크립트를 실행할 수 있습니다.
- 로컬 컴퓨터에서 작성하는 스크립트를 포함하여 모든 스크립트와 구성 파일에 신뢰할 수 있는 판매자의 서명이 있어야 합니다.
- 아직 신뢰할 수 있거나 신뢰할 수 없는 것으로 분류 하지 않은 게시자의 스크립트를 실행 하기 전에 메시지를 표시 합니다.
- 서명 되었지만 악의적인 스크립트를 실행 하는 위험

### <a name="bypass"></a>바이패스

- 아무것도 차단되지 않으며 경고 또는 프롬프트가 없습니다.
- 이 실행 정책은 powershell 스크립트가 대규모 응용 프로그램에 기본 제공 되는 구성 또는 PowerShell이 자체 보안 모델을 포함 하는 프로그램의 기반이 되는 구성에 맞게 설계 되었습니다.

### <a name="default"></a>기본값

- 기본 실행 정책을 설정 합니다.
- Windows 클라이언트에 대해 **제한** 됩니다.
- Windows 서버에 대 한 **RemoteSigned** .

### <a name="remotesigned"></a>RemoteSigned

- Windows server 컴퓨터에 대 한 기본 실행 정책입니다.
- 스크립트를 실행할 수 있습니다.
- 전자 메일 및 인스턴트 메시징 프로그램을 포함 하는 인터넷에서 다운로드 한 스크립트 및 구성 파일에 신뢰할 수 있는 게시자의 디지털 서명이 필요 합니다.
- 로컬 컴퓨터에 작성 되 고 인터넷에서 다운로드 되지 않은 스크립트에 디지털 서명이 필요 하지 않습니다.
- Cmdlet을 사용 하는 등의 방법으로 스크립트가 차단 해제 된 경우 인터넷에서 다운로드 되 고 서명 되지 않은 스크립트를 실행 합니다 `Unblock-File` .
- 인터넷 및 서명 된 스크립트 이외의 원본에서 서명 되지 않은 스크립트를 실행 하는 위험 (악성이 될 수 있음)

### <a name="restricted"></a>제한

- Windows 클라이언트 컴퓨터에 대 한 기본 실행 정책입니다.
- 는 개별 명령을 허용 하지만 스크립트를 허용 하지 않습니다.
- 서식 지정 및 구성 파일 ( `.ps1xml` ), 모듈 스크립트 파일 ( `.psm1` ) 및 PowerShell 프로필 ()을 비롯 한 모든 스크립트 파일의 실행을 방지 `.ps1` 합니다.

### <a name="undefined"></a>정의되지 않음

- 현재 범위에 설정 된 실행 정책이 없습니다.
- 모든 범위의 실행 정책이 **정의 되지 않은** 경우에는 windows 클라이언트와 windows Server의 **RemoteSigned** 에 대 한 유효 실행 정책이 **제한** 됩니다.

### <a name="unrestricted"></a>제한 없음

- 비 Windows 컴퓨터에 대 한 기본 실행 정책은 변경할 수 없습니다.
- 서명 되지 않은 스크립트를 실행할 수 있습니다. 악의적인 스크립트를 실행할 위험이 있습니다.
- 로컬 인트라넷 영역에서 가져오지 않은 스크립트 및 구성 파일을 실행 하기 전에 사용자에 게 경고 합니다.

> [!NOTE]
> Unc (범용 명명 규칙) 경로를 인터넷 경로에서 구분 하지 않는 시스템에서는 UNC 경로에 의해 식별 되는 스크립트를 **RemoteSigned** 실행 정책으로 실행 하도록 허용 하지 않을 수 있습니다.

## <a name="execution-policy-scope"></a>실행 정책 범위

특정 범위에만 적용 되는 실행 정책을 설정할 수 있습니다.

**범위** 에 대 한 유효한 값은 **MachinePolicy**, **userpolicy**, **Process**, **CurrentUser** 및 **LocalMachine** 입니다. 실행 정책을 설정할 때 기본값은 **LocalMachine** 입니다.

**범위** 값은 우선 순위에 따라 나열 됩니다. 더 제한적인 정책이 더 낮은 우선 순위로 설정 된 경우에도 우선 순위가 높은 정책은 현재 세션에서 적용 됩니다.

자세한 내용은 [set-executionpolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)를 참조 하세요.

### <a name="machinepolicy"></a>MachinePolicy

컴퓨터의 모든 사용자에 대해 그룹 정책 설정 합니다.

### <a name="userpolicy"></a>UserPolicy

컴퓨터의 현재 사용자에 대 한 그룹 정책 설정 합니다.

### <a name="process"></a>프로세스

**프로세스** 범위는 현재 PowerShell 세션에만 영향을 줍니다. 실행 정책은 레지스트리가 아닌 환경 변수에 저장 됩니다 `$env:PSExecutionPolicyPreference` . PowerShell 세션이 닫히면 변수와 값이 삭제 됩니다.

### <a name="currentuser"></a>CurrentUser

실행 정책이 현재 사용자에게만 영향을 줍니다. **HKEY_CURRENT_USER** 레지스트리 하위 키에 저장 됩니다.

### <a name="localmachine"></a>LocalMachine

실행 정책은 현재 컴퓨터의 모든 사용자에 게 영향을 줍니다. **HKEY_LOCAL_MACHINE** 레지스트리 하위 키에 저장 됩니다.

## <a name="managing-the-execution-policy-with-powershell"></a>PowerShell을 사용 하 여 실행 정책 관리

현재 PowerShell 세션의 유효 실행 정책을 가져오려면 cmdlet을 사용 합니다 `Get-ExecutionPolicy` .

다음 명령은 유효한 실행 정책을 가져옵니다.

```powershell
Get-ExecutionPolicy
```

현재 세션에 영향을 주는 모든 실행 정책을 가져오고 우선 순위에 따라 표시 합니다.

```powershell
Get-ExecutionPolicy -List
```

결과는 다음 예제 출력과 유사 하 게 표시 됩니다.

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

이 경우 현재 사용자에 대 한 실행 정책이 로컬 컴퓨터에 설정 된 실행 정책 보다 우선적으로 적용 되기 때문에 유효한 실행 정책이 **RemoteSigned** 됩니다.

특정 범위에 대 한 실행 정책을 설정 하려면의 **scope** 매개 변수를 사용 `Get-ExecutionPolicy` 합니다.

예를 들어 다음 명령은 **CurrentUser** 범위에 대 한 실행 정책을 가져옵니다.

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a>실행 정책 변경

Windows 컴퓨터에서 PowerShell 실행 정책을 변경 하려면 cmdlet을 사용 합니다 `Set-ExecutionPolicy` . 변경 내용은 즉시 적용 됩니다. PowerShell을 다시 시작할 필요는 없습니다.

**LocalMachine** 또는 **CurrentUser** 범위에 대 한 실행 정책을 설정 하면 변경 내용이 레지스트리에 저장 되 고 다시 변경 될 때까지 유효 하 게 유지 됩니다.

**프로세스** 범위에 대 한 실행 정책을 설정 하면 레지스트리에 저장 되지 않습니다. 실행 정책은 현재 프로세스와 모든 자식 프로세스가 닫힐 때까지 유지 됩니다.

> [!NOTE]
> Windows Vista 이상 버전의 Windows에서 로컬 컴퓨터 **LocalMachine** 범위에 대 한 실행 정책을 변경 하는 명령을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.

실행 정책을 변경 하려면 다음을 수행 합니다.

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

다음은 그 예입니다. 

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

특정 범위에서 실행 정책을 설정 하려면 다음을 수행 합니다.

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

다음은 그 예입니다. 

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

실행 정책을 변경 하는 명령은 성공 하지만 유효 실행 정책을 변경 하지는 않습니다.

예를 들어 로컬 컴퓨터에 대 한 실행 정책을 설정 하는 명령은 성공 하지만 현재 사용자의 실행 정책에 의해 재정의 될 수 있습니다.

### <a name="remove-the-execution-policy"></a>실행 정책 제거

특정 범위에 대 한 실행 정책을 제거 하려면 실행 정책을 **Undefined** 로 설정 합니다.

예를 들어 로컬 컴퓨터의 모든 사용자에 대 한 실행 정책을 제거 하려면 다음을 수행 합니다.

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

**범위** 에 대 한 실행 정책을 제거 하려면 다음을 수행 합니다.

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

어떤 범위에도 실행 정책이 설정 되지 않은 경우 유효한 실행 정책이 Windows 클라이언트의 기본값인로 **제한** 됩니다.

### <a name="set-a-different-policy-for-one-session"></a>한 세션에 대해 다른 정책 설정

**pwsh.exe** 의 **set-executionpolicy** 매개 변수를 사용 하 여 새 PowerShell 세션의 실행 정책을 설정할 수 있습니다. 이 정책은 현재 세션 및 자식 세션에만 영향을 줍니다.

새 세션에 대 한 실행 정책을 설정 하려면 명령줄에서 **cmd.exe** 또는 powershell과 같은 powershell을 시작한 후 **pwsh.exe** 의 **set-executionpolicy** 매개 변수를 사용 하 여 실행 정책을 설정 합니다.

다음은 그 예입니다. 

```powershell
pwsh.exe -ExecutionPolicy AllSigned
```

설정 하는 실행 정책은 레지스트리에 저장 되지 않습니다. 대신, `$env:PSExecutionPolicyPreference` 환경 변수에 저장 됩니다. 정책이 설정 된 세션을 닫으면 변수가 삭제 됩니다. 변수 값을 편집 하 여 정책을 변경할 수는 없습니다.

세션 중에 세션에 대해 설정 된 실행 정책이 로컬 컴퓨터 또는 현재 사용자의 레지스트리에 설정 된 실행 정책 보다 우선 합니다. 그러나 그룹 정책를 사용 하 여 설정 된 실행 정책 보다 우선 적용 되지 않습니다.

## <a name="use-group-policy-to-manage-execution-policy"></a>그룹 정책를 사용 하 여 실행 정책 관리

그룹 정책 **스크립트 실행** 설정을 사용 하 여 엔터프라이즈의 컴퓨터에 대 한 실행 정책을 관리할 수 있습니다. 그룹 정책 설정은 모든 범위에서 PowerShell에 설정 된 실행 정책을 재정의 합니다.

**스크립트 실행** 설정 정책 설정은 다음과 같습니다.

- **스크립트 실행** 을 사용 하지 않도록 설정 하면 스크립트가 실행 되지 않습니다. 이는 **제한** 된 실행 정책과 동일 합니다.
- **스크립트 실행** 을 사용 하도록 설정 하는 경우 실행 정책을 선택할 수 있습니다. 그룹 정책 설정은 다음 실행 정책 설정과 동일 합니다.

  | 그룹 정책                                  | 실행 정책 |
  | --------------------------------------------- | ---------------- |
  | 모든 스크립트 허용                             | 제한 없음     |
  | 로컬 스크립트 및 원격 서명 된 스크립트 허용 | RemoteSigned     |
  | 서명 된 스크립트만 허용                     | AllSigned        |

- **설정 스크립트 실행** 이 구성 되지 않은 경우에는 영향을 주지 않습니다. PowerShell에서 설정 된 실행 정책이 적용 됩니다.

PowerShellExecutionPolicy 및 PowerShellExecutionPolicy 파일은 다음 경로에 그룹 정책 편집기의 컴퓨터 구성 및 사용자 구성 노드에 대 한 **스크립트 실행 정책 설정** 정책을 추가 합니다.

Windows XP 및 Windows Server 2003:

관리 템플릿 \ PowerShell

Windows Vista 이상 버전의 경우:

관리 Templates\Classic 관리 템플릿 \
Windows s PowerShell

컴퓨터 구성 노드에서 설정 된 정책은 사용자 구성 노드에 설정 된 정책 보다 우선적으로 적용 됩니다.

자세한 내용은 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)를 참조하세요.

### <a name="execution-policy-precedence"></a>실행 정책 우선 순위

세션에 대 한 유효한 실행 정책을 결정할 때 PowerShell은 다음 우선 순위에 따라 실행 정책을 평가 합니다.

- 그룹 정책: MachinePolicy
- 그룹 정책: UserPolicy
- 실행 정책: Process (or `pwsh.exe -ExecutionPolicy` )
- 실행 정책: CurrentUser
- 실행 정책: LocalMachine

## <a name="manage-signed-and-unsigned-scripts"></a>서명 및 서명 되지 않은 스크립트 관리

Windows에서 Internet Explorer 및 Microsoft Edge와 같은 프로그램은 다운로드 된 파일에 대체 데이터 스트림을 추가 합니다. 이렇게 하면 파일이 "인터넷에서 제공"으로 표시 됩니다. PowerShell 실행 정책이 **RemoteSigned** 인 경우 powershell은 전자 메일 및 인스턴트 메시징 프로그램을 포함 하는 인터넷에서 다운로드 한 서명 되지 않은 스크립트를 실행 하지 않습니다.

스크립트에 서명 하거나 실행 정책을 변경 하지 않고 서명 되지 않은 스크립트를 실행 하도록 선택할 수 있습니다.

PowerShell 3.0부터 cmdlet의 **Stream** 매개 변수를 사용 하 여 `Get-Item` 차단 된 파일이 인터넷에서 다운로드 되어 해당 파일을 검색할 수 있습니다. Cmdlet을 사용 `Unblock-File` 하 여 PowerShell에서 실행할 수 있도록 스크립트를 차단 해제 합니다.

자세한 내용은 [about_Signing](about_Signing.md), [항목 가져오기](xref:Microsoft.PowerShell.Management.Get-Item)및 [파일 차단 해제](xref:Microsoft.PowerShell.Utility.Unblock-File)를 참조 하세요.

> [!NOTE]
> 파일을 다운로드 하는 다른 방법은 인터넷 영역에서 가져온 파일을 표시 하지 않을 수 있습니다. 일부 사례:
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a>Windows Server Core 및 Window Nano Server에 대 한 실행 정책

특정 조건에서 Windows Server Core 또는 Windows Nano Server에서 PowerShell 6을 실행 하면 다음 오류와 함께 실행 정책이 실패할 수 있습니다.

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

PowerShell은 Windows Desktop Shell ()의 Api를 사용 하 여 `explorer.exe` 스크립트 파일 영역의 유효성을 검사 합니다. Windows Shell은 windows Server Core 및 Windows Nano Server에서 사용할 수 없습니다.

Windows 데스크톱 셸을 사용할 수 없거나 응답 하지 않는 경우 Windows 시스템에서이 오류를 가져올 수도 있습니다. 예를 들어 로그온 하는 동안 Windows 데스크톱이 준비 되기 전에 PowerShell 로그온 스크립트가 실행을 시작할 수 있으며,이로 인해 오류가 발생 합니다.

**바이패스** 또는 **AllSigned** 실행 정책을 사용 하는 경우에는 문제를 방지 하는 영역 검사가 필요 하지 않습니다.

## <a name="see-also"></a>참고 항목

[about_Environment_Variables](about_Environment_Variables.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Signing](about_Signing.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)

[Pwsh 콘솔 도움말](about_pwsh.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File)

