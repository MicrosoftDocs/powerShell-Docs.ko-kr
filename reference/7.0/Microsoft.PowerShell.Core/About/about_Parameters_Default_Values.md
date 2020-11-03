---
description: Cmdlet 매개 변수 및 고급 기능에 대 한 사용자 지정 기본값을 설정 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 5/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: c2bc8c64b6b3c0d3627d9db61132dde58522555e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223121"
---
# <a name="about-parameters-default-values"></a>매개 변수 기본값 정보

## <a name="short-description"></a>간단한 설명

Cmdlet 매개 변수 및 고급 기능에 대 한 사용자 지정 기본값을 설정 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

`$PSDefaultParameterValues`기본 설정 변수를 사용 하 여 cmdlet 또는 고급 기능에 대 한 사용자 지정 기본값을 지정할 수 있습니다. Cmdlet 및 고급 함수는 명령에 다른 값을 지정 하지 않는 한 사용자 지정 기본값을 사용 합니다.

Cmdlet 및 고급 함수의 작성자는 해당 매개 변수에 대 한 표준 기본값을 설정 합니다. 일반적으로 표준 기본값은 유용 하지만 모든 환경에 적합 하지 않을 수 있습니다.

이 기능은 명령을 사용할 때마다 또는 전자 메일 서버 이름이 나 프로젝트 GUID와 같이 특정 매개 변수 값을 기억할 수 없는 경우 거의 동일한 대체 매개 변수 값을 지정 해야 하는 경우에 특히 유용 합니다.

원하는 기본값이 예측 가능 하면 다른 조건에서 매개 변수에 대해 다른 기본값을 제공 하는 스크립트 블록을 지정할 수 있습니다.

`$PSDefaultParameterValues` 는 PowerShell 3.0에서 도입 되었습니다.

## <a name="syntax"></a>구문

`$PSDefaultParameterValues`변수는 키 형식에 **대 한** 개체 형식의 유효성을 검사 하는 해시 테이블입니다. 해시 테이블에는 **키/값** 쌍이 포함 되어 있습니다. **키는** 형식입니다 `CmdletName:ParameterName` . **값** 은 키에 할당 된 **DefaultValue** 또는 **ScriptBlock** 입니다.

`$PSDefaultParameterValues`기본 설정 변수의 구문은 다음과 같습니다.

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

**CmdletName** 및 **ParameterName** 값에 와일드 카드 문자를 사용할 수 있습니다.

에서 특정 **키/값** 쌍을 설정, 변경, 추가 또는 제거 하려면 `$PSDefaultParameterValues` 메서드를 사용 하 여 표준 해시 테이블을 편집 합니다. 예를 들어 **Add** 및 **Remove** 메서드가 있습니다. 이러한 메서드는 해시 테이블의 다른 값을 덮어쓰지 않습니다.

기존 해시 테이블을 덮어쓰지 않는 또 다른 구문이 있습니다 `$PSDefaultParameterValues` . 특정 **키/값** 쌍을 추가 하거나 변경 하려면 다음 구문을 사용 합니다.

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

**CmdletName** 는 **cmdletbinding** 특성을 사용 하는 cmdlet의 이름 또는 고급 함수의 이름 이어야 합니다. `$PSDefaultParameterValues`를 사용 하 여 스크립트 또는 간단한 함수에 대 한 기본값을 지정할 수 없습니다.

**DefaultValue** 는 개체 또는 스크립트 블록일 수 있습니다. 값이 스크립트 블록인 경우 PowerShell은 스크립트 블록을 평가 하 고 결과를 매개 변수 값으로 사용 합니다. 지정 된 매개 변수가 스크립트 블록 값을 허용 하는 경우 다음과 같이 두 번째 중괄호 집합으로 스크립트 블록 값을 묶습니다.

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

자세한 내용은 다음 문서를 참조하세요.

- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Preference_Variables](about_Preference_Variables.md)

## <a name="examples"></a>예

### <a name="how-to-set-psdefaultparametervalues"></a>PSDefaultParameterValues 설정 방법 \$

`$PSDefaultParameterValues` 는 기본 설정 변수 이므로 설정 된 세션에만 존재 합니다. 기본값은 없습니다.

설정 하려면 `$PSDefaultParameterValues` 변수 이름과 하나 이상의 **키/값** 쌍을 입력 합니다. 다른 명령을 실행 하 `$PSDefaultParameterValues` 는 경우 기존 해시 테이블을 덮어씁니다.

기존 해시 테이블 값을 덮어쓰지 않고 **키/값** 쌍을 변경 하는 방법에 대 한 예제는 [ \$ PSDefaultParameterValues에 값을 추가](#how-to-add-values-to-psdefaultparametervalues) 하는 방법 또는 [ \$ PSDefaultParameterValues에서 값을 변경](#how-to-change-values-in-psdefaultparametervalues)하는 방법을 참조 하세요.

`$PSDefaultParameterValues`이후 세션을 위해 저장 하려면 `$PSDefaultParameterValues` PowerShell 프로필에 명령을 추가 합니다. 자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.

#### <a name="set-a-custom-default-value"></a>사용자 지정 기본값 설정

**키/값** 쌍은 키를 `Send-MailMessage:SmtpServer` **Server123** 의 사용자 지정 기본값으로 설정 합니다.

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a>여러 매개 변수에 대 한 기본값 설정

여러 매개 변수에 대 한 기본값을 설정 하려면 각 **키/값** 쌍을 세미콜론 ()으로 구분 `;` 합니다. `Send-MailMessage:SmtpServer`및 `Get-WinEvent:LogName` 키는 사용자 지정 기본값으로 설정 됩니다.

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a>와일드 카드 및 스위치 매개 변수 사용

Cmdlet 및 매개 변수 이름에는 와일드 카드 문자를 사용할 수 있습니다. 및를 사용 `$True` `$False` 하 여 **자세한 정보** 표시와 같은 스위치 매개 변수에 대 한 값을 설정 합니다. 일반 매개 변수의 **Verbose** 매개 변수는 `$True` 모든 명령에 대해로 설정 됩니다.

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a>기본값에 배열을 사용 합니다.

매개 변수가 여러 값을 사용할 수 있는 경우 여러 값을 기본값으로 설정할 수 있습니다. 키의 기본값은 `Invoke-Command:ComputerName` **Server01** 및 **Server02** 의 배열 값으로 설정 됩니다.

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a>스크립트 블록 사용

스크립트 블록을 사용 하 여 다른 조건에서 매개 변수에 대해 다른 기본값을 지정할 수 있습니다. PowerShell은 스크립트 블록을 평가 하 고 그 결과를 기본 매개 변수 값으로 사용 합니다.

`Format-Table:AutoSize`키는 매개 변수를 기본값인 **True** 로 설정 합니다. 문에는가 `If` `$host.Name` PowerShell 콘솔 **ConsoleHost** 해야 하는 조건이 포함 되어 있습니다.

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

매개 변수가 스크립트 블록 값을 허용 하는 경우 스크립트 블록을 추가 중괄호 집합으로 묶습니다. PowerShell에서 외부 스크립트 블록을 평가할 때 결과는 내부 스크립트 블록이 고 기본 매개 변수 값으로 설정 됩니다.

`Invoke-Command:ScriptBlock`스크립트 블록이 두 번째 중괄호 집합으로 묶여 있으므로 키가 **시스템 이벤트 로그** 의 기본값으로 설정 됩니다. 스크립트 블록의 결과는 cmdlet으로 전달 됩니다 `Invoke-Command` .

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a>PSDefaultParameterValues를 가져오는 방법 \$

해시 테이블 값은 PowerShell 프롬프트에서를 입력 하 여 표시 됩니다 `$PSDefaultParameterValues` .

`$PSDefaultParameterValues`해시 테이블은 3 개의 **키/값** 쌍으로 설정 됩니다.
이 해시 테이블은의 값을 추가, 변경 및 제거 하는 방법을 설명 하는 다음 예제에서 사용 됩니다 `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
  "Get-*:Verbose"=$True
}

PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

특정 키의 값을 가져오려면 `CmdletName:ParameterName` 다음 구문을 사용 합니다.

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

예를 들어 키의 값을 가져올 수 `Send-MailMessage:SmtpServer` 있습니다.

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a>PSDefaultParameterValues에 값을 추가 하는 방법 \$

에 값을 추가 하려면 `$PSDefaultParameterValues` **add** 메서드를 사용 합니다. 값을 추가 해도 해시 테이블의 기존 값에는 영향을 주지 않습니다.

쉼표 ()를 사용 `,` 하 여 **값** 과 **키** 를 구분 합니다. 다음 구문에서는에 대해 **Add** 메서드를 사용 하는 방법을 보여 줍니다 `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

이전 예제에서 만든 해시 테이블은 새 **키/값** 쌍으로 업데이트 됩니다. **Add** 메서드는 키를 `Get-Process:Name` 값 **PowerShell** 로 설정 합니다.

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

다음 구문은 동일한 결과를 생성 합니다.

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

`$PSDefaultParameterValues`변수는 업데이트 된 해시 테이블을 표시 합니다. `Get-Process:Name`키를 추가 했습니다.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a>PSDefaultParameterValues에서 값을 제거 하는 방법 \$

에서 값을 제거 하려면 `$PSDefaultParameterValues` 해시 테이블의 **remove** 메서드를 사용 합니다. 값을 제거 해도 해시 테이블의 기존 값에는 영향을 주지 않습니다.

다음 구문에서는에서 **Remove** 메서드를 사용 하는 방법을 보여 줍니다 `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

이 예제에서는 이전 예제에서 만든 해시 테이블을 업데이트 하 여 **키/값** 쌍을 제거 합니다. **Remove** 메서드는 키를 제거 합니다 `Get-Process:Name` .

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

`$PSDefaultParameterValues`변수는 업데이트 된 해시 테이블을 표시 합니다. `Get-Process:Name`키가 제거 되었습니다.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a>PSDefaultParameterValues의 값을 변경 하는 방법 \$

특정 값에 대 한 변경 내용은 기존 해시 테이블 값에 영향을 주지 않습니다. 에서 특정 **키/값** 쌍을 변경 하려면 `$PSDefaultParameterValues` 다음 구문을 사용 합니다.

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

이 예제에서는 이전 예제에서 만든 해시 테이블을 업데이트 하 여 **키/값** 쌍을 변경 합니다. 다음 명령은 `Send-MailMessage:SmtpServer` 키를 새 값 **serverxyz** 로 변경 합니다.

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

`$PSDefaultParameterValues`변수는 업데이트 된 해시 테이블을 표시 합니다. `Send-MailMessage:SmtpServer`키가 새 값으로 변경 되었습니다.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a>PSDefaultParameterValues를 사용 하지 않도록 설정 하 고 다시 사용 하도록 설정 하는 방법 \$

일시적으로 사용 하지 않도록 설정한 다음 다시 사용 하도록 설정할 수 있습니다 `$PSDefaultParameterValues` .
비활성화 `$PSDefaultParameterValues` 는 다른 기본 매개 변수 값이 필요한 스크립트를 실행 하는 경우에 유용 합니다.

비활성화 하려면 `$PSDefaultParameterValues` 값이 True 인의 키를 추가 `Disabled` 합니다 **True**. 의 값은 `$PSDefaultParameterValues` 유지 되지만 유효 하지 않습니다.

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

다음 구문은 동일한 결과를 생성 합니다.

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

`$PSDefaultParameterValues`변수는 키 값을 사용 하 여 업데이트 된 해시 테이블을 표시 합니다 `Disabled` .

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

다시 사용 하도록 설정 하려면 `$PSDefaultParameterValues` **사용 하지 않도록** 설정 된 키를 제거 하거나 **사용 하지 않도록 설정** 된 키의 값을로 변경 `$False` 합니다. 의 이전 값은 `$PSDefaultParameterValues` 다시 적용 됩니다.

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

다음 구문은 동일한 결과를 생성 합니다.

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

`$PSDefaultParameterValues`변수는 업데이트 된 해시 테이블을 표시 합니다. **Remove** 메서드를 사용 하면 `Disabled` 출력에서 키가 제거 됩니다.
대체 구문을 사용 하도록 다시 설정 하는 경우 `$PSDefaultParameterValues` `Disabled` 키가 **False** 로 표시 됩니다.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a>참고 항목

[about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Script_Blocks](about_Script_Blocks.md)
