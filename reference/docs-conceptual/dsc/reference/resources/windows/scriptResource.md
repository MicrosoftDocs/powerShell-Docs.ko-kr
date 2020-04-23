---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC 스크립트 리소스
ms.openlocfilehash: e09e86011fa7dbb2a4d7f28b5032b4328b6f6ec2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953070"
---
# <a name="dsc-script-resource"></a>DSC 스크립트 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x

Windows PowerShell DSC(필요한 상태 구성)의 **스크립트** 리소스에서는 대상 노드에서 Windows PowerShell 스크립트 블록을 실행하는 메커니즘을 제공합니다. **스크립트** 리소스는 사용자가 정의하는 스크립트 블록이 포함되는 **GetScript**, **SetScript** 및 **TestScript** 속성을 사용하여 해당 DSC 상태 작업을 수행합니다.

## <a name="syntax"></a>구문

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> **GetScript**, **TestScript** 및 **SetScript** 블록은 문자열로 저장됩니다.

## <a name="properties"></a>속성

|속성 |Description |
|---|---|
|GetScript |노드의 현재 상태를 반환하는 스크립트 블록입니다. |
|SetScript |노드가 원하는 상태가 아닐 때 DSC가 준수 적용을 위해 사용하는 스크립트 블록입니다. |
|TestScript |노드가 원하는 상태인지를 확인하는 스크립트 블록입니다. |
|자격 증명 |자격 증명이 필요한 경우 이 스크립트를 실행하는 데 사용할 자격 증명을 나타냅니다. |

## <a name="common-properties"></a>공용 속성

|속성 |Description |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.

### <a name="additional-information"></a>추가 정보

#### <a name="getscript"></a>GetScript

DSC에서는 **GetScript**의 출력을 사용하지 않습니다. [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet은 **GetScript**를 실행하여 노드의 현재 상태를 검색합니다. **GetScript**의 반환 값은 필요하지 않습니다. 반환 값을 지정하는 경우 해당 값이 문자열인 **Result** 키가 포함된 해시 테이블이어야 합니다.

#### <a name="testscript"></a>TestScript

**TestScript**는 **SetScript**를 실행해야 하는지 여부를 확인하기 위해 DSC에 의해 실행됩니다. **TestScript**가 `$false`를 반환하는 경우 DSC는 **SetScript**를 실행하여 노드를 원하는 상태로 다시 전환합니다. 부울 값을 반환해야 합니다. `$true`의 결과는 노드가 규정을 준수하며 **SetScript**를 실행하지 않아야 함을 나타냅니다.

[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet은 **TestScript**를 실행하여 **스크립트** 리소스에 대한 노드 준수 상태를 검색합니다.
그러나 이 경우에는 **TestScript** 블록이 반환하는 결과에 관계없이 **SetScript**는 실행되지 않습니다.

> [!NOTE]
> **TestScript** 모든 출력은 해당 반환 값의 일부입니다. PowerShell은 표시되는 출력을 0이 아닌 것으로 해석합니다. 즉, **TestScript**는 노드 상태에 관계없이 `$true`를 반환합니다. 이로 인해 예상치 못한 결과, 가양성이 발생하고, 문제를 해결하기 어렵습니다.

#### <a name="setscript"></a>SetScript

**SetScript**는 노드를 수정하여 원하는 상태를 적용합니다. **TestScript**가 `$false`를 반환하는 경우 DSC에 의해 호출됩니다. **SetScript**에는 반환 값이 없어야 합니다.

## <a name="examples"></a>예

### <a name="example-1-write-sample-text-using-a-script-resource"></a>예제 1: 스크립트 리소스를 사용하여 샘플 텍스트 쓰기

이 예제에서는 각 노드에서 `C:\TempFolder\TestFile.txt`의 존재 여부를 테스트합니다. 존재하지 않는 경우 `SetScript`를 사용하여 만듭니다. `GetScript`는 파일의 내용을 반환하고, 해당 반환 값은 사용되지 않습니다.

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>예제 2: 스크립트 리소스를 사용하여 버전 정보 비교

이 예제에서는 작성 컴퓨터의 텍스트 파일에서 *규격* 버전 정보를 검색한 후 `$version` 변수에 저장합니다. 노드의 MOF 파일을 생성할 때 DSC는 각 스크립트 블록의 `$using:version` 변수를 `$version` 변수의 값으로 바꿉니다.
실행 동안 *규격* 버전은 각 노드의 텍스트 파일에 저장되고, 후속 실행에서 비교 및 업데이트됩니다.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```