---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 노드에서 구성 적용, 가져오기 및 테스트
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402948"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>노드에서 구성 적용, 가져오기 및 테스트

이 가이드에서는 대상 노드에 구성을 사용 하는 방법을 보여 줍니다. 이 가이드는 다음 단계를로 세분화 됩니다.

## <a name="apply-a-configuration"></a>구성 적용

적용 하 고 구성 관리를 위해 ".mof" 파일을 생성 해야 합니다. 다음 코드는이 가이드 전체에서 사용 되는 간단한 구성을 나타냅니다.

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

이 구성을 컴파일하면 ".mof" 파일을 두 개 생성 합니다.

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

구성을 적용 하려면 사용 합니다 [Start-dscconfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. `-Path` 매개 변수 ".mof" 파일이 있는 디렉터리를 지정 합니다. 없으면 `-Computername` 지정 된 `Start-DSCConfiguration` '.mof' 파일의 이름으로 지정 된 컴퓨터 이름에 각 구성을 적용 하려고 합니다 (\<computername\>.mof). 지정할 `-Verbose` 에 `Start-DSCConfiguration` 자세한 출력을 확인 합니다.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

경우 `-Wait` 지정 하지 않으면 만든 하나의 작업을 표시 합니다. 만든 작업 하나가 포함 됩니다 **ChildJob** 에서 각 ".mof" 파일에 대 한 처리 `Start-DSCConfiguration`합니다.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

구성에 오랜 시간이 소요 됩니다 하 고 중지 하려는 사용할 수 있습니다 [Stop-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) 로컬 노드에서 응용 프로그램을 중지 합니다.

```powershell
Stop-DSCConfiguration -Force
```

완료 되 면 반환 하는 작업 개체를 통해 작업의 상태를 볼 수 있습니다 [Get-job](/powershell/module/microsoft.powershell.core/get-job)합니다.

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

보려는 **Verbose** 출력을 보려면 다음 명령을 사용 합니다 **Verbose** 스트림 각각에 대 한 **ChildJob**합니다. PowerShell 작업에 대 한 자세한 내용은 참조 하세요 [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)합니다.

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

PowerShell 5.0에서 시작 합니다 `-UseExisting` 매개 변수를 추가한 `Start-DSCConfiguration`합니다. 지정 하 여 `-UseExisting`, cmdlet이 적용된 된 기존 구성에서 지정 하는 대신 사용 하도록 지시 합니다 `-Path` 매개 변수입니다.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>구성 테스트

사용 하 여 현재 적용 된 구성을 테스트할 수 있습니다 [Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)합니다. `Test-DSCConfiguration` 돌아갑니다 `True` 노드인 준수 하는 경우 및 `False` 없는 경우.

```powershell
Test-DSCConfiguration
```

PowerShell 5.0에서 시작 합니다 `-Detailed` 매개 변수 컬렉션을 사용 하 여 개체를 반환 하는 추가 되었습니다 **ResourcesInDesiredState** 고 **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

PowerShell 5.0에서부터 적용 하지 않고 구성을 테스트할 수 있습니다. `-ReferenceConfiguration` 매개 변수는 노드를 테스트 하려면 "mof" 파일의 경로 허용 합니다. 아니오 **설정** 노드에 대해 동작이 수행 됩니다. PowerShell 4.0에서 대안을 적용 하지 않고 구성을 테스트 하려면 있고 여기서 설명 하지 않은 합니다.

## <a name="get-configuration-values"></a>구성 값을 얻으려면

합니다 [Get-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet은 현재 적용된 된 구성에 구성 된 모든 리소스에 대 한 현재 값을 반환 합니다.

```powershell
Get-DSCConfiguration
```

샘플 구성에서에서 출력 성공적으로 적용 하는 경우 다음과 같이 보입니다.

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a>구성 상태를 가져옵니다.

PowerShell 5.0부터 합니다 [Get-dscconfigurationstatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet을 사용 하면 적용 된 노드 구성의 기록을 볼 수 있습니다. PowerShell DSC에 적용 하는 마지막 {{N}을 (를) 구성 하는 추적 **푸시** 하거나 **끌어오기** 모드입니다. 여기에 모든 *일관성* 검사에서 LCM에 의해 실행 됩니다. 기본적으로 `Get-DSCConfigurationStatus` 마지막 기록 항목에만 보여 줍니다.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

사용 된 `-All` 모든 구성 상태 기록을 보려면 매개 변수입니다.

> [!NOTE]
> 간단한 설명을 위해 출력이 잘립니다.

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a>구성 문서를 관리 합니다.

사용 하 여 노드 구성을 관리 하는 LCM **구성 문서**합니다. 이러한 ".mof" files "C:\Windows\System32\Configuration" 디렉터리에 있어야합니다.

PowerShell 5.0부터 합니다 [Remove-dscconfigurationdocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) 이후 일관성 검사를 중지 하거나 적용 하는 경우 오류를 가진 구성 제거 ".mof" 파일을 제거할 수 있습니다. `-Stage` 매개 변수를 사용 하면 제거 하려는 ".mof" 파일을 지정할 수 있습니다.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> PowerShell 4.0에서 제거할 수 있습니다 여전히 이러한 ".mof" 파일을 사용 하 여 직접 [Remove-item](/powershell/module/microsoft.powershell.management/remove-item)합니다.

## <a name="publish-configurations"></a>게시 구성

PowerShell 5.0에서 시작 합니다 [Publish-dscconfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet이 추가 되었습니다. 이 cmdlet을 사용 하면 원격 컴퓨터에 적용 하지 않고 ".mof" 파일을 게시할 수 있습니다.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>참고 항목

- [가져오기, 테스트 및 설정](../resources/get-test-set.md)
