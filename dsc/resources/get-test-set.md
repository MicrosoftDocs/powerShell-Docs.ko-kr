---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 가져오기-테스트-설정
ms.openlocfilehash: 6d059518a49926bc5fb56e37e7d3d4d2c66bddec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682203"
---
# <a name="get-test-set"></a>가져오기-테스트-설정

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

![가져오기, 테스트 및 설정](/media/get-test-set.png)

PowerShell Desired State Configuration 주위에 생성 된 **가져오기**, **테스트**, 및 **설정** 프로세스. DSC [리소스](resources.md) 각각 이러한 각 작업을 완료 하는 메서드를 포함 합니다. 에 [구성](../configurations/configurations.md), 리소스 블록을 리소스에 대 한 매개 변수는 키 입력을 정의한 **가져오기**를 **테스트**, 및 **설정** 메서드입니다.

에 대 한 구문은이 **서비스** 리소스 블록. 합니다 **서비스** 리소스는 Windows 서비스를 구성 합니다.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

**가져오기**, **테스트**, 및 **설정** 메서드를 **서비스** 리소스 이러한 값을 허용 하는 매개 변수 블록을 갖습니다.

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> 언어 및 리소스를 정의 하는 데 사용 되는 메서드를 결정 하는 방법을 **가져옵니다**, **테스트**, 및 **설정** 메서드 정의 됩니다.

때문에 합니다 **서비스** 리소스에만 필수 키에 (`Name`), **서비스** 블록 리소스는이 처럼 간단할 수 있습니다.

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

위의 구성을 컴파일하는 경우 키에 대 한 지정 된 값이 생성 되는 ".mof" 파일에 저장 됩니다. 자세한 내용은 [MOF](/windows/desktop/wmisdk/managed-object-format--mof-)합니다.

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

적용 하는 경우는 [로컬 구성 관리자](../managing-nodes/metaConfig.md) "Spooler" 값 ".mof" 파일에서 읽고에 전달 합니다 `-Name` 의 매개 변수를 **가져오기**, **테스트**, 및 **설정할** "MyService" 인스턴스에 대 한 메서드는 **서비스** 리소스입니다.

## <a name="get"></a>get

합니다 **가져올** 메서드는 리소스의 대상 노드에 구성 된 대로 리소스의 상태를 검색 합니다. 이 상태로 반환 되는 [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables). 키를 **hashtable** 됩니다 구성 가능한 값 또는 매개 변수는 리소스를 허용 합니다.

**가져오기** 메서드를 직접 매핑합니다 합니다 [Get-dscconfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet. 호출 하는 경우 `Get-DSCConfiguration`, LCM 실행 합니다 **가져올** 현재 적용된 된 구성의 각 리소스는 메서드. LCM는 각 해당 리소스 인스턴스에 대 한 매개 변수로 ".mof" 파일에 저장 된 키 값을 사용 합니다.

샘플 출력은이 **서비스** "Spooler" 서비스를 구성 하는 리소스입니다.

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

출력의 현재 값 속성을 구성할 수 있습니다 표시 합니다 **서비스** 리소스입니다.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a>테스트

합니다 **테스트** 메서드는 리소스의 대상 노드 리소스의 현재 호환 되는 경우 결정 *필요한 상태*합니다. 합니다 **테스트** 메서드가 반환 `$True` 또는 `$False` 노드 규격 인지 여부를 나타낼 때만 합니다.
호출 하는 경우 [Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), LCM 호출 합니다 **테스트** 현재 적용된 된 구성의 각 리소스는 메서드. LCM는 각 해당 리소스 인스턴스에 대 한 매개 변수로 ".mof" 파일에 저장 된 키 값을 사용 합니다.

경우 모든 개별 리소스의 결과인 **테스트** 는 `$False`, `Test-DSCConfiguration` 반환 `$False` 노드 규격 임을 나타내는입니다. 경우 모든 리소스 **테스트** 메서드는 반환 `$True`, `Test-DSCConfiguration` 반환 `$True` 노드 규격 임을 나타냅니다.

```powershell
Test-DSCConfiguration
```

```output
True
```

PowerShell 5.0부터는 `-Detailed` 매개 변수 추가 되었습니다. 지정 `-Detailed` 하면 `Test-DSCConfiguration` 호환 및 호환 되지 않는 리소스에 대 한 결과의 컬렉션을 포함 하는 개체를 반환 합니다.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

자세한 내용은 참조 하세요. [Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Set(영문)

합니다 **설정** 메서드는 리소스의 노드 리소스의 준수를 강제로 시도할지 *필요한 상태*합니다. 합니다 **설정** 메서드를 사용할 계획이 **idempotent**, 즉 **설정** 여러 번 실행 하 고 항상 오류 없이 같은 결과 얻을 수 있습니다.  실행할 때 [Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), 각 리소스에 현재 적용된 된 구성 LCM 순환 합니다. LCM ".mof" 파일에서 현재 리소스 인스턴스에 대 한 키 값을 검색 하 고 매개 변수로 사용 하 여 **테스트** 메서드. 경우는 **테스트** 메서드가 반환 `$True`, 노드는 현재 리소스, 호환 및 **설정** 메서드를 건너뜁니다. 경우는 **테스트** 반환 `$False`, 노드인 비준수입니다.  LCM은 리소스 인스턴스의 키 값 매개 변수로 전달 리소스의 **설정** 메서드를 준수 하려면 노드를 복원 합니다.

지정 하 여 합니다 `-Verbose` 하 고 `-Wait` 매개 변수에서의 진행률을 확인할 수 있습니다는 `Start-DSCConfiguration` cmdlet. 이 예제에서는 노드 준수 이미 있습니다. 합니다 `Verbose` 나타내는 출력을 **설정** 메서드 작업을 건너뛰었습니다.

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a>참고 항목

- [Azure Automation DSC 개요](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Setting up an SMB pull server(SMB 끌어오기 서버 설정)](../pull-server/pullServerSMB.md)
- [Configuring a pull client(끌어오기 클라이언트 구성)](../pull-server/pullClientConfigID.md)
