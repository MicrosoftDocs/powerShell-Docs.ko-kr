---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC 그룹 리소스
ms.openlocfilehash: 695a914683c6daff44dd2a6c94b6353acf881030
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954660"
---
# <a name="dsc-group-resource"></a>DSC 그룹 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x

Windows PowerShell DSC(필요한 상태 구성)의 **그룹** 리소스에서는 대상 노드에 있는 로컬 그룹을 관리하는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |설명 |
|---|---|
|GroupName |상태를 확인하려는 그룹의 이름입니다. |
|자격 증명 |원격 리소스에 액세스하는 데 필요한 자격 증명입니다. 이 계정에는 로컬이 아닌 모든 계정을 그룹에 추가할 수 있는 Active Directory 사용 권한이 있어야 합니다. 그렇지 않으면 구성이 대상 노드에서 실행될 때 오류가 발생합니다.
|설명 |그룹에 대한 설명입니다. |
|구성원 |현재 그룹 구성원 자격을 지정된 구성원으로 바꾸려면 이 속성을 사용합니다. 이 속성의 값은 `Domain\UserName` 형식의 문자열 배열입니다. 구성에서 이 속성을 설정하는 경우 **MembersToExclude** 또는 **MembersToInclude** 속성을 사용하지 마세요. 사용할 경우 오류가 발생합니다. |
|MembersToExclude |그룹의 기존 구성원 자격에서 구성원을 제거하려면 이 속성을 사용합니다. 이 속성의 값은 `Domain\UserName` 형식의 문자열 배열입니다. 구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요. 사용할 경우 오류가 발생합니다. |
|MembersToInclude |그룹의 기존 구성원 자격에 구성원을 추가하려면 이 속성을 사용합니다. 이 속성의 값은 `Domain\UserName` 형식의 문자열 배열입니다. 구성에서 이 속성을 설정하는 경우 **Members** 속성을 사용하지 마세요. 사용할 경우 오류가 발생합니다. |

## <a name="common-properties"></a>공용 속성

|속성 |설명 |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |그룹이 존재하는지 여부를 나타냅니다. 그룹이 존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다. 그룹이 존재하도록 하려면 이 속성을 **Present**로 설정합니다. 기본값은 **Present**입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.

## <a name="example-1-ensure-group-is-not-present"></a>예제 1: 그룹이 존재하지 않는지 확인합니다.

다음 예제에서는 “TestGroup”이라는 그룹이 없음을 확인하는 방법을 보여 줍니다.

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a>예제 2: 로컬 그룹에 도메인 사용자 추가

다음 예제에서는 Active Directory 사용자를 로컬 관리자 그룹에 다중 머신 랩 빌드의 일부로 추가하는 방법을 보여줍니다. 여기에서 사용자는 이미 로컬 관리자 계정에 대해 PSCredential을 사용하고 있습니다. 이것은 또한 도메인 승급 후 도메인 관리자 계정에도 사용되므로, 기존 PSCredential을 도메인 자격 증명으로 변환해야 합니다. 그런 다음 구성원 서버에서 도메인 사용자를 로컬 관리자 그룹에 추가할 수 있습니다.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a>예제 3

다음 예제에서는 TigerTeamSource.Contoso.Com 서버의 로컬 그룹 TigerTeamAdmins에 특정 도메인 계정 Contoso\JerryG가 포함되지 않도록 하는 방법을 보여 줍니다.

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```