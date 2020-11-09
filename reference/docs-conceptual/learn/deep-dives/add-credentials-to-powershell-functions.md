---
title: PowerShell 함수에 자격 증명 지원 추가
description: PowerShell 스크립트, 함수, cmdlet에 자격 증명 매개 변수를 추가하는 방법입니다.
ms.date: 10/29/2020
ms.custom: contributor-JoshDuffney
ms.openlocfilehash: 3e4a3f41ccbca1cf97f2e96fd60f22d89be7bc5a
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354629"
---
# <a name="add-credential-support-to-powershell-functions"></a>PowerShell 함수에 자격 증명 지원 추가

> [!NOTE]
> 이 문서의 [원래 버전][]은 [@joshduffney][]가 작성한 블로그에 나옵니다. 이 문서는 이 사이트에 포함할 수 있도록 편집되었습니다. PowerShell 팀은 이 콘텐츠를 공유해 준 Josh에게 감사의 말을 전합니다. [duffney.io][]에서 Josh의 블로그를 확인하세요.

이 문서에서는 PowerShell 함수에 자격 증명 매개 변수를 추가하는 방법과 추가해야 하는 이유를 보여 줍니다. 자격 증명 매개 변수는 함수 또는 cmdlet을 다른 사용자로 실행할 수 있도록 하기 위한 것입니다. 가장 일반적인 용도는 함수 또는 cmdlet을 관리자 계정으로 실행하는 것입니다.

예를 들어 cmdlet `New-ADUser`에는 도메인에 계정을 만들기 위해 도메인 관리자 자격 증명을 제공할 수 있는 **Credential** 매개 변수가 있습니다. PowerShell 세션을 실행하는 일반 계정에 아직 이 액세스 권한이 없는 것으로 가정합니다.

## <a name="creating-credential-object"></a>자격 증명 개체 만들기

[PSCredential][] 개체는 사용자 이름 및 암호와 같은 보안 자격 증명 집합을 나타냅니다. 이 개체는 해당 자격 증명 개체의 사용자 계정으로 실행되는 함수에 매개 변수로 전달될 수 있습니다. 자격 증명 개체를 만드는 몇 가지 방법이 있습니다. 자격 증명 개체를 만드는 첫 번째 방법은 PowerShell cmdlet `Get-Credential`을 사용하는 것입니다. 매개 변수 없이 실행하는 경우 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다. 또는 몇 가지 선택적 매개 변수를 사용하여 cmdlet을 호출할 수 있습니다.

도메인 이름과 사용자 이름을 미리 지정하려면 **Credential** 또는 **UserNaem** 매개 변수를 사용할 수 있습니다. **UserName** 매개 변수를 사용하는 경우 **Message** 값도 제공해야 합니다. 아래 코드는 cmdlet 사용을 보여 줍니다. 자격 증명을 여러 번 사용할 수 있도록 자격 증명 개체를 변수에 저장할 수도 있습니다. 아래 예제에서 자격 증명 개체는 `$Cred` 변수에 저장됩니다.

```powershell
$Cred = Get-Credential
$Cred = Get-Credential -Credential domain\user
$Cred = Get-Credential -UserName domain\user -Message 'Enter Password'
```

이전 예제에 나온 자격 증명 개체를 만드는 대화형 메서드를 사용할 수 없는 경우가 있습니다. 대부분의 자동화 도구에는 비대화형 메서드가 필요합니다. 사용자 상호 작용 없이 자격 증명을 만들려면 암호를 포함하는 보안 문자열을 만드세요. 그런 다음 보안 문자열과 사용자 이름을 `System.Management.Automation.PSCredential()` 메서드에 전달합니다.

다음 명령을 사용하여 암호를 포함하는 보안 문자열을 만듭니다.

```powershell
ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
```

**AsPlainText** 및 **Force** 매개 변수가 모두 필요합니다. 이러한 매개 변수가 없으면 일반 텍스트를 보안 문자열로 전달하면 안 된다는 메시지 경고가 표시됩니다. PowerShell이 이 경고를 반환하는 이유는 일반 텍스트 암호가 다양한 로그에 기록되기 때문입니다. 보안 문자열을 만든 후 이를 `PSCredential()` 메서드로 전달하여 자격 증명 개체를 만들어야 합니다. 다음 예제에서 `$password` 변수는 자격 증명 개체를 포함하는 `$Cred` 보안 문자열을 포함합니다.

```powershell
$password = ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("username", $password)
```

자격 증명 개체를 만드는 방법을 배웠으므로 이제 PowerShell 함수에 자격 증명 매개 변수를 추가할 수 있습니다.

## <a name="adding-a-credential-parameter"></a>자격 증명 매개 변수 추가

다른 매개 변수와 마찬가지로 함수의 `param` 블록에 추가하여 시작합니다.
기존 PowerShell cmdlet에서 사용되므로 매개 변수 이름을 `$Credential`로 지정하는 것이 좋습니다. 매개 변수 형식은 `[System.Management.Automation.PSCredential]`이어야 합니다.

다음 예제는 `Get-Something`이라는 함수의 매개 변수 블록을 보여 줍니다. `$Name`과 `$Credential`이라는 두 개의 매개 변수가 있습니다.

```powershell
function Get-Something {
    param(
        $Name,
        [System.Management.Automation.PSCredential]$Credential
    )
```

이 예제의 코드도 작동하는 자격 증명 매개 변수를 갖기에 충분하지만 보다 강력한 기능을 위해 몇 가지를 추가할 수 있습니다.

- `[ValidateNotNull()]` 유효성 검사 특성을 추가하여 값이 **Credential** 에 전달되는지 확인합니다. 매개 변수 값이 null인 경우 이 특성을 사용하면 함수가 잘못된 자격 증명으로 실행되지 않습니다.

- `[System.Management.Automation.Credential()]`를 추가합니다. 이렇게 하면 사용자 이름을 문자열로 전달하고 암호를 묻는 대화형 프롬프트를 표시할 수 있습니다.

- `$Credential` 매개 변수의 기본값을 `[System.Management.Automation.PSCredential]::Empty`로 설정합니다. 함수는 이 `$Credential` 개체를 기존 PowerShell cmdlet에 전달할 수 있습니다. 함수 내에서 호출된 cmdlet에 null 값을 제공하면 오류가 발생합니다. 빈 자격 증명 개체를 제공하면 이 오류가 방지됩니다.

> [!TIP]
> 자격 증명 매개 변수를 허용하는 일부 cmdlet은 예상과 달리 `[System.Management.Automation.PSCredential]::Empty`를 지원하지 않습니다. 해결 방법은 [레거시 cmdlet 처리](#dealing-with-legacy-cmdlets) 섹션을 참조하세요.

## <a name="using-credential-parameters"></a>자격 증명 매개 변수 사용

다음 예제는 매개 변수를 사용하는 방법을 보여 줍니다. 이 예제는 [The Pester Book][]에서 가져온 `Set-RemoteRegistryValue`라는 함수를 보여 줍니다. 이 함수는 이전 섹션에 설명된 방법을 사용하여 자격 증명 매개 변수를 정의합니다. 이 함수는 함수가 만든 `$Credential` 변수를 사용하여 `Invoke-Command`를 호출합니다. 이렇게 하면 `Invoke-Command`를 실행하는 사용자를 변경할 수 있습니다. `$Credential`의 기본값이 빈 자격 증명이므로 자격 증명을 제공하지 않아도 함수를 실행할 수 있습니다.

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )
        $null = Invoke-Command -ComputerName $ComputerName -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } -Credential $Credential
}
```

다음 섹션에서는 `Set-RemoteRegistryValue`에 자격 증명을 제공하는 다양한 방법을 보여 줍니다.

### <a name="prompting-for-credentials"></a>자격 증명 입력 요구

런타임에 `()` 괄호 안에 `Get-Credential`을 사용하면 `Get-credential`이 먼저 실행됩니다. 사용자 이름과 암호를 묻는 메시지가 나타납니다. `Get-credential`의 **Credential** 또는 **UserName** 매개 변수를 사용하여 사용자 이름과 도메인을 미리 채울 수 있습니다. 다음 예제에서는 스플래팅이라는 방법을 사용하여 매개 변수를 `Set-RemoteRegistryValue` 함수에 전달합니다. 스플래팅에 대한 자세한 내용은 [about_Splatting][] 문서를 참조하세요.

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential (Get-Credential)
```

![런타임에 자격 증명 가져오기](./media/add-credentials-to-powershell-functions/GetCredAtRunTime.gif)

`(Get-Credential)` 사용은 번거로워 보입니다. 일반적으로 사용자 이름만으로 **Credential** 매개 변수를 사용하면 cmdlet은 자동으로 암호를 묻는 메시지를 표시합니다. `[System.Management.Automation.Credential()]` 특성은 이 동작을 사용하도록 설정합니다.

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential duffney
```

![자격 증명 확인](./media/add-credentials-to-powershell-functions/GetCredsPrompt.gif)

> [!NOTE]
> 표시되는 레지스트리 값을 설정하기 위해 이 예제에서는 Windows의 **웹 서버** 기능이 설치되어 있다고 가정합니다. 필요한 경우 `Install-WindowsFeature Web-Server`와 `Install-WindowsFeature web-mgmt-tools`를 실행하세요.

### <a name="provide-credentials-in-a-variable"></a>변수에서 자격 증명 제공

미리 자격 증명 변수를 채우고 `Set-RemoteRegistryValue` 함수의 **Credential** 매개 변수에 전달할 수도 있습니다. Jenkins, TeamCity, Octopus Deploy와 같은 CI/CD(연속 통합/지속적인 배포) 도구에 이 메서드를 사용하세요. Jenkins를 사용하는 예제는 Hodge의 블로그 [Automating with Jenkins and PowerShell on Windows - Part 2][] 게시물을 참조하세요.

이 예제는 .NET 메서드를 사용하여 암호에 전달할 보안 문자열과 자격 증명 개체를 만듭니다.

```powershell
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("duffney", $password)

$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential $Cred
```

이 예제에서는 일반 텍스트 암호를 사용하여 보안 문자열을 만듭니다. 앞에서 언급한 모든 CI/CD에는 런타임에 해당 암호를 제공하는 안전한 메서드가 있습니다. 이러한 도구를 사용하는 경우 사용하는 CI/CD 도구 내에서 정의된 변수로 일반 텍스트 암호를 바꾸세요.

### <a name="run-without-credentials"></a>자격 증명 없이 실행

`$Credential`은 빈 자격 증명 개체가 기본값이므로 다음 예제와 같이 자격 증명 없이 명령을 실행할 수 있습니다.

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams
```

## <a name="dealing-with-legacy-cmdlets"></a>레거시 cmdlet 처리

모든 cmdlet이 자격 증명 개체를 지원하거나 빈 자격 증명을 허용하지는 않습니다. 대신 cmdlet은 사용자 이름 및 암호 매개 변수가 문자열이기를 원합니다. 이 제한 사항을 해결하는 몇 가지 방법이 있습니다.

### <a name="using-if-else-to-handle-empty-credentials"></a>if-else를 사용하여 빈 자격 증명 처리

이 시나리오에서 실행할 cmdlet은 빈 자격 증명 개체를 허용하지 않습니다. 이 예제는 **Credential** 매개 변수가 비어 있지 않은 경우에만 `Invoke-Command`에 이를 추가합니다. 비어 있으면 **Credential** 매개 변수 없이 `Invoke-Command`를 실행합니다.

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

    if($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
        Invoke-Command -ComputerName:$ComputerName -Credential:$Credential  {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    } else {
        Invoke-Command -ComputerName:$ComputerName {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    }
}
```

### <a name="using-splatting-to-handle-empty-credentials"></a>스플래팅을 사용하여 빈 자격 증명 처리

이 예제는 매개 변수 스플래팅을 사용하여 레거시 cmdlet을 호출합니다. `$Credential` 개체는 조건부로 스플래팅 해시 테이블에 추가되며, `Invoke-Command` 스크립트 블록을 반복하지 않아도 됩니다. 함수 내에서의 스플래팅에 대한 자세한 내용은 [Splatting Parameters Inside Advanced Functions][] 블로그 게시물을 참조하세요.

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $Splat = @{
            ComputerName = $ComputerName
        }

        if ($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
            $Splat['Credential'] = $Credential
        }

        $null = Invoke-Command -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } @splat
}
```

### <a name="working-with-string-passwords"></a>문자열 암호 사용

`Invoke-Sqlcmd` cmdlet은 문자열을 암호로 허용하는 cmdlet의 예입니다.
`Invoke-Sqlcmd`를 사용하면 간단한 SQL insert, update, delete 문을 실행할 수 있습니다. `Invoke-Sqlcmd`에서는 더 안전한 자격 증명 개체보다는 일반 텍스트 사용자 이름 및 암호를 사용해야 합니다. 이 예제는 자격 증명 개체에서 사용자 이름 및 암호를 추출하는 방법을 보여 줍니다.

이 예제의 `Get-AllSQLDatabases` 함수는 `Invoke-Sqlcmd` cmdlet을 호출하여 SQL Server에서 모든 해당 데이터베이스를 쿼리합니다. 이 함수는 이전 예제에서 사용된 것과 동일한 특성을 사용하여 **Credential** 매개 변수를 정의합니다. 사용자 이름과 암호가 `$Credential` 변수 내에 있기 때문에 `Invoke-Sqlcmd`에 사용할 값을 추출할 수 있습니다.

사용자 이름은 `$Credential` 변수의 **UserName** 속성에서 사용할 수 있습니다. 암호를 가져오려면 `$Credential` 개체의 `GetNetworkCredential()` 메서드를 사용해야 합니다. 값은 `Invoke-Sqlcmd`에 대한 매개 변수 스플래팅에 사용되는 해시 테이블에 추가되는 변수로 추출됩니다.

```powershell
function Get-AllSQLDatabases {
    param(
        $SQLServer,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $UserName = $Credential.UserName
        $Password = $Credential.GetNetworkCredential().Password

        $splat = @{
            UserName = $UserName
            Password = $Password
            ServerInstance = 'SQLServer'
            Query = "Select * from Sys.Databases"
        }

        Invoke-Sqlcmd @splat
}

$credSplat = @{
    TypeName = 'System.Management.Automation.PSCredential'
    ArgumentList = 'duffney',('P@ssw0rd' | ConvertTo-SecureString -AsPlainText -Force)
}
$Credential= New-Object @credSplat
ConvertTo-SecureString -AsPlainText -Force)

Get-AllSQLDatabases -SQLServer SQL01 -Credential $Credential
```

## <a name="continued-learning-credential-management"></a>자격 증명 관리 학습 계속

자격 증명 개체를 안전하게 만들고 저장하는 것은 어려울 수 있습니다. 다음 리소스는 PowerShell 자격 증명을 유지하는 데 도움이 될 수 있습니다.

- [BetterCredentials][]
- [Azure Key Vault][]
- [Vault Project][]
- [SecretManagement 모듈][]

<!-- link references -->
[원래 버전]: https://duffney.io/addcredentialstopowershellfunctions/
[@joshduffney]: https://twitter.com/joshduffney
[duffney.io]: https://duffney.io/posts/
[BetterCredentials]: https://www.powershellgallery.com/packages/BetterCredentials/
[Azure Key Vault]: https://azure.microsoft.com/services/key-vault/
[Vault Project]: https://www.vaultproject.io/
[Splatting Parameters Inside Advanced Functions]: https://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[Automating with Jenkins and PowerShell on Windows - Part 2]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2
[PSCredential]: /dotnet/api/system.management.automation.pscredential
[The Pester Book]: https://leanpub.com/the-pester-book
[about_Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[SecretManagement 모듈]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
