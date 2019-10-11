---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DependsOn을 사용하는 리소스 종속성
ms.openlocfilehash: 5ea08c76c203188f41513ad0cc1f4571579b4172
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954480"
---
# <a name="resource-dependencies-using-dependson"></a><span data-ttu-id="23c58-103">DependsOn을 사용하는 리소스 종속성</span><span class="sxs-lookup"><span data-stu-id="23c58-103">Resource dependencies using DependsOn</span></span>

<span data-ttu-id="23c58-104">[구성](configurations.md)을 작성하는 경우 [리소스 블록](../resources/resources.md)을 추가하여 대상 노드의 측면을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-104">When you write [Configurations](configurations.md), you add [Resource blocks](../resources/resources.md) to configure aspects of a target Node.</span></span> <span data-ttu-id="23c58-105">리소스 블록을 계속 추가하게 되면 구성을 관리하기에는 크고 불편할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-105">As you continue to add Resource blocks, your Configurations can grow quite large and cumbersome to manage.</span></span> <span data-ttu-id="23c58-106">이러한 문제 중 하나는 리소스 블록에 적용된 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-106">One such challenge is the applied order of your resource blocks.</span></span> <span data-ttu-id="23c58-107">일반적으로 리소스는 구성 내에서 정의된 순서대로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-107">Typically resources are applied in the order they are defined within the Configuration.</span></span> <span data-ttu-id="23c58-108">구성이 더 크고 복잡해지면 리소스가 다른 리소스에 종속되도록 지정하여 리소스의 적용된 순서를 변경하는 데 `DependsOn` 키를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-108">As your Configuration grows larger and more complex, you can use the `DependsOn` key to change the applied order of your resources by specifying that a resource depends on another resource.</span></span>

<span data-ttu-id="23c58-109">`DependsOn` 키는 리소스 블록에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-109">The `DependsOn` key can be used in any Resource block.</span></span> <span data-ttu-id="23c58-110">다른 리소스 키와 동일한 키/값 메커니즘을 사용하여 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-110">It is defined with the same key/value mechanism as other Resource keys.</span></span> <span data-ttu-id="23c58-111">`DependsOn` 키는 다음 구문을 포함한 문자열의 배열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-111">The `DependsOn` key expects an array of strings with the following syntax.</span></span>

```
DependsOn = '[<Resource Type>]<Resource Name>', '[<Resource Type>]<Resource Name'
```

<span data-ttu-id="23c58-112">다음 예제에서는 공개 프로필을 설정하고 구성한 후에 방화벽 규칙을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-112">The following example configures a firewall rule after enabling and configuring the public profile.</span></span>

```powershell
# Install the NetworkingDSC module to configure firewall rules and profiles.
Install-Module -Name NetworkingDSC

Configuration ConfigureFirewall
{
    Import-DSCResource -Name Firewall, FirewallProfile
    Node localhost
    {
        Firewall Firewall
        {
            Name                  = 'IIS-WebServerRole-HTTP-In-TCP'
            Ensure                = 'Present'
            Enabled               = 'True'
            DependsOn             = '[FirewallProfile]FirewallProfilePublic'
        }

        FirewallProfile FirewallProfilePublic
        {
            Name = 'Public'
            Enabled = 'True'
            DefaultInboundAction = 'Block'
            DefaultOutboundAction = 'Allow'
            AllowInboundRules = 'True'
            AllowLocalFirewallRules = 'False'
            AllowLocalIPsecRules = 'False'
            NotifyOnListen = 'True'
            LogFileName = '%systemroot%\system32\LogFiles\Firewall\pfirewall.log'
            LogMaxSizeKilobytes = 16384
            LogAllowed = 'False'
            LogBlocked = 'True'
            LogIgnored = 'NotConfigured'
        }
    }
}

ConfigureFirewall -OutputPath C:\Temp\
```

<span data-ttu-id="23c58-113">구성을 적용하는 경우 방화벽 프로필은 리소스 블록이 정의되는 순서에 관계 없이 항상 먼저 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-113">When you apply the Configuration, the firewall profile will always be configured first regardless of which order the Resource blocks are defined.</span></span> <span data-ttu-id="23c58-114">구성을 적용하면 원하는 경우 되돌릴 수 있도록 구성이 위치한 대상 노드를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-114">If you apply the Configuration, be sure to note your target Nodes existing Configuration so you can revert if desired.</span></span>

```
PS> Start-DSCConfiguration -Verbose -Wait -Path C:\Temp\ -ComputerName localhost

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-181338-0189125723-1543119021-1282804.
VERBOSE: [SERVER01]: LCM:  [ Start  Set      ]
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module C:\Program Files\WindowsPowerShell\Modules\NetworkingDsc\6.1.0.0\DscResources\MSFT_Firewall\MSFT_Firewall.psm1 in force mode.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module C:\Program Files\WindowsPowerShell\Modules\NetworkingDsc\6.1.0.0\DscResources\MSFT_FirewallProfile\MSFT_FirewallProfile.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[FirewallProfile]FirewallProfilePublic]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[FirewallProfile]FirewallProfilePublic]
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Importing the module MSFT_FirewallProfile in force mode.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Testing Firewall Public Profile.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "AllowInboundRules" is "NotConfigured" but should be "True". Change required.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "AllowLocalFirewallRules" is "NotConfigured" but should be "False". Change required.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "AllowLocalIPsecRules" is "NotConfigured" but should be "False". Change required.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "DefaultOutboundAction" is "NotConfigured" but should be "Allow". Change required.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "LogBlocked" is "False" but should be "True". Change required.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Test-TargetResource: Firewall Public Profile "LogMaxSizeKilobytes" is "4096" but should be "16384". Change required.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[FirewallProfile]FirewallProfilePublic]  in 1.6890 seconds.
VERBOSE: [SERVER01]: LCM:  [ Start  Set      ]  [[FirewallProfile]FirewallProfilePublic]
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Importing the module MSFT_FirewallProfile in force mode.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile.
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter AllowInboundRules to "AllowInboundRules".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter AllowLocalFirewallRules to "AllowLocalFirewallRules".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter AllowLocalIPsecRules to "AllowLocalIPsecRules".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter DefaultOutboundAction to "DefaultOutboundAction".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter LogBlocked to "LogBlocked".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile parameter LogMaxSizeKilobytes to "LogMaxSizeKilobytes".
VERBOSE: [SERVER01]:                            [[FirewallProfile]FirewallProfilePublic] Set-TargetResource: Setting Firewall Public Profile updated.
VERBOSE: [SERVER01]: LCM:  [ End    Set      ]  [[FirewallProfile]FirewallProfilePublic]  in 10.0360 seconds.
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[FirewallProfile]FirewallProfilePublic]
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Firewall]Firewall]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Firewall]Firewall]
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Importing the module MSFT_Firewall in force mode.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Test-TargetResource: Checking settings for firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Test-TargetResource: Find firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Get-FirewallRule: No Firewall Rule found with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Test-TargetResource: Firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP' does not exist.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Test-TargetResource: Check Firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP' returning False.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Firewall]Firewall]  in 1.1780 seconds.
VERBOSE: [SERVER01]: LCM:  [ Start  Set      ]  [[Firewall]Firewall]
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Importing the module MSFT_Firewall in force mode.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Set-TargetResource: Applying settings for firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Set-TargetResource: Find firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Get-FirewallRule: No Firewall Rule found with Name 'IIS-WebServerRole-HTTP-In-TCP'.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Set-TargetResource: We want the firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP' to exist since Ensure is set to Present.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] Set-TargetResource: We want the firewall rule with Name 'IIS-WebServerRole-HTTP-In-TCP' to exist, but it does not.
VERBOSE: [SERVER01]:                            [[Firewall]Firewall] New-NetFirewallRule DisplayName: IIS-WebServerRole-HTTP-In-TCP
VERBOSE: [SERVER01]: LCM:  [ End    Set      ]  [[Firewall]Firewall]  in 1.0850 seconds.
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Firewall]Firewall]
VERBOSE: [SERVER01]: LCM:  [ End    Set      ]
VERBOSE: [SERVER01]: LCM:  [ End    Set      ]    in  15.2880 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 15.385 seconds
```

<span data-ttu-id="23c58-115">그러면 **FirewallProfile** 리소스가 어떤 이유로 실패하는 경우 **방화벽** 블록이 먼저 정의되더라도 실행되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-115">This also ensures that if the **FirewallProfile** resource fails for any reason, the **Firewall** block will not execute even though it was defined first.</span></span> <span data-ttu-id="23c58-116">`DependsOn` 키를 사용하면 보다 유연하게 리소스 블록을 그룹화하고 리소스가 실행되기 전에 종속성을 해결했는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-116">The `DependsOn` key allows more flexibility in grouping resource blocks and ensuring that dependencies are resolved before a Resource executes.</span></span>

<span data-ttu-id="23c58-117">고급 구성에서 [노드 간 종속성](crossNodeDependencies.md)을 사용하여 훨씬 더 세부적으로 제어할 수도 있습니다(예: 클라이언트 도메인에 가입하기 전에 도메인 컨트롤러가 구성되었는지 확인).</span><span class="sxs-lookup"><span data-stu-id="23c58-117">In more advanced Configurations, you can also use [Cross Node Dependency](crossNodeDependencies.md) to allow even more granular control (For example, ensuring a domain controller is configured before joining a client to the domain).</span></span>

## <a name="cleaning-up"></a><span data-ttu-id="23c58-118">정리</span><span class="sxs-lookup"><span data-stu-id="23c58-118">Cleaning Up</span></span>

<span data-ttu-id="23c58-119">위의 구성을 적용한 경우 키를 되돌려서 모든 변경 내용을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-119">If you applied the Configuration above, you can reverse keys to undo any changes.</span></span> <span data-ttu-id="23c58-120">위의 예제에서 **사용됨** 키를 false로 설정하면 방화벽 규칙 및 프로필을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-120">In the above example, setting the **Enabled** key to false will disable the firewall rule and profile.</span></span> <span data-ttu-id="23c58-121">대상 노드가 이전 구성된 상태와 일치하도록 필요에 따라 예제를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23c58-121">You should modify the example as needed to match your target Node's previous configured state.</span></span>

```powershell
        Firewall Firewall
        {
            Name                  = 'IIS-WebServerRole-HTTP-In-TCP'
            Enabled               = 'False'
            DependsOn             = '[FirewallProfile]FirewallProfilePublic'
        }

        FirewallProfile FirewallProfilePublic
        {
            Name = 'Public'
            Enabled = 'False'
        }
```

## <a name="see-also"></a><span data-ttu-id="23c58-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23c58-122">See also</span></span>

- [<span data-ttu-id="23c58-123">노드 간 종속성 사용</span><span class="sxs-lookup"><span data-stu-id="23c58-123">Use Cross Node Dependencies</span></span>](./crossNodeDependencies.md)
