---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 리소스 디자이너 도구 사용
ms.openlocfilehash: 9e7488e922bdca70bb152e7e976077e43cfad7af
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692187"
---
# <a name="using-the-resource-designer-tool"></a>리소스 디자이너 도구 사용

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

리소스 디자이너 도구는 Windows PowerShell DSC(필요한 상태 구성) 리소스를 만드는 작업을 더 쉽게 해주고 **xDscResourceDesigner** 모듈에 의해 노출된 cmdlet 집합입니다. 이 리소스의 cmdlet은 MOF 스키마, 스크립트 모듈 및 새 리소스에 대한 디렉터리 구조를 만드는 데 도움이 됩니다. DSC 리소스에 대한 자세한 내용은 [Build Custom Windows PowerShell Desired State Configuration Resources(사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드)](authoringResource.md)를 참조하세요. 이 항목에서는 Active Directory 사용자를 관리하는 DSC 리소스를 만듭니다. [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet을 사용하여 **xDscResourceDesigner** 모듈을 설치하세요.

## <a name="creating-resource-properties"></a>리소스 속성 만들기
가장 먼저 해야 할 일은 리소스가 노출할 속성에 대해 결정하는 것입니다. 이 예의 경우, 다음 속성으로 Active Directory 사용자를 정의하게 됩니다.

매개 변수 이름 설명

* **UserName**: 사용자를 고유하게 식별하는 주요 속성입니다.
* **Ensure**: 사용자 계정이 있음인지 또는 없음인지 여부를 지정합니다. 이 매개 변수는 두 개의 가능한 값만 갖습니다.
* **DomainCredential**: 사용자에 대한 도메인 암호입니다.
* **암호**: 필요한 경우 구성으로 사용자 암호를 변경할 수 있도록 해주는 사용자에 대한 원하는 암호입니다.

속성을 만들기 위해 우리는 **New-xDscResourceProperty** cmdlet을 사용합니다. 다음 PowerShell 명령을 사용하면 위에서 설명한 속성이 만들어집니다.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>리소스 만들기

이제 리소스 속성이 만들어졌으므로 **New-xDscResource** cmdlet을 호출하여 리소스를 만들 수 있습니다. **New-xDscResource** cmdlet에서는 속성 목록을 매개 변수로 사용합니다. 또한 모듈을 만들어야 하는 경로, 새 리소스의 이름 및 리소스가 들어 있는 모듈의 이름도 사용해야 합니다. 다음 PowerShell 명령은 리소스를 만듭니다.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

**New-xDscResource** cmdlet은 MOF 스키마, 뼈대 리소스 스크립트, 새 리소스에 대한 필수 디렉터리 구조와 새 리소스를 노출하는 모듈에 대한 매니페스트를 만듭니다.

MOF 스키마 파일은 **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**에 있으며 그 내용은 다음과 같습니다.

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

리소스 스크립트는 **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**에 있습니다.
이 스크립트는 리소스를 구현하는 실제 논리를 포함하지 않습니다. 실제 논리는 직접 추가해야 합니다. 뼈대 스크립트의 내용은 다음과 같습니다.

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}


function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $result = [System.Boolean]

  $result
  #>
}


Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a>리소스 업데이트

리소스의 매개 변수 목록을 추가하거나 수정해야 하는 경우 **Update-xDscResource** cmdlet을 호출할 수 있습니다. cmdlet은 새 매개 변수 목록으로 리소스를 업데이트합니다. 이미 리소스 스크립트에서 논리를 추가한 경우 그대로 유지됩니다.

예를 들어 리소스에서 사용자에 대한 마지막 로그인 시간을 포함하려고 한다고 가정할 경우, 리소스를 완전히 다시 작성하는 대신 **New-xDscResourceProperty**를 호출하여 새 속성을 만든 다음, **Update-xDscResource**를 호출하고 새 속성을 속성 목록에 추가할 수 있습니다.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>리소스 스키마 테스트

리소스 디자이너 도구는 수동으로 작성한 MOF 스키마의 유효성을 테스트하는 데 사용할 수 있는 cmdlet을 하나 더 노출합니다. **Test-xDscSchema** cmdlet을 호출하여 MOF 리소스 스키마의 경로를 매개 변수로 전달합니다. cmdlet이 스키마의 모든 오류를 출력합니다.

### <a name="see-also"></a>참고 항목

#### <a name="concepts"></a>개념
[사용자 지정 Windows PowerShell 필요한 상태 구성 리소스 빌드](authoringResource.md)

#### <a name="other-resources"></a>관련 자료
[xDscResourceDesigner 모듈](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
