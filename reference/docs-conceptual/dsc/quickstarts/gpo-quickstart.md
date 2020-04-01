---
ms.date: 07/09/2019
keywords: dsc,gpo,powershell,configuration,setup
title: 빠른 시작 - 그룹 정책을 DSC로 변환
ms.openlocfilehash: 5e6b86be5127332fe4fd400980c8e147b735247b
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500646"
---
> <span data-ttu-id="59881-103">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="59881-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="59881-104">빠른 시작: 그룹 정책을 DSC로 변환</span><span class="sxs-lookup"><span data-stu-id="59881-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="59881-105">그룹 정책 또는 Azure Security Center 기준에서 DSC 구성을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59881-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="59881-106">[BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) 모듈에는 이 작업을 수행하기 위한 다음 명령이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59881-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="59881-107">`ConvertFrom-GPO` - 파일로 저장된 그룹 정책을 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="59881-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="59881-108">하나의 구성으로 결합될 여러 정책을 포함하는 디렉터리를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59881-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="59881-109">환경에서 그룹 정책을 내보내려면 [GPO 백업](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet을 사용하거나 [파일로 GPO 내보내기](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="59881-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="59881-110">`ConvertFrom-SCM` - `.xml` 파일로 저장된 Security Compliance Manager 기준선을 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="59881-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="59881-111">`ConvertFrom-ASC` - `.json` 파일로 저장된 Azure Security Center 기준선을 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="59881-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="59881-112">`Merge-GPOs` - 대상 컴퓨터에 적용된 그룹 정책을 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="59881-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="59881-113">위에 나열된 cmdlet은 기준선을 DSC `.mof` 파일로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="59881-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="59881-114">편집하고 다시 컴파일할 수 있는 구성 스크립트(`.ps1`)를 출력하도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59881-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="59881-115">cmdlet은 누락된 리소스 또는 중복된 리소스 블록에 대한 컴파일 오류를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="59881-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="59881-116">컴파일 오류를 발생시키는 리소스 블록은 주석 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="59881-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="59881-117">다음 예제에서는 [Microsoft Security 기준선](https://www.microsoft.com/en-us/download/details.aspx?id=55319)을 DSC 구성 스크립트(`.ps1`) 및 `.mof` 파일로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="59881-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="59881-118">명령을 실행한 후 현재 경로 아래에 생성된 기본 "Output" 디렉터리에 두 개의 파일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="59881-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

<span data-ttu-id="59881-119">각 관리 노드에는 다음 두 모듈도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="59881-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="59881-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="59881-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="59881-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="59881-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="59881-122">**BaselineManagement**는 Microsoft가 아닌 프로젝트 유지 관리자로부터 커뮤니티 솔루션에 대한 지원을 DSC가 더 쉽게 검색할 수 있도록 커뮤니터에서 개발한 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="59881-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="59881-123">[GitHub](https://github.com/microsoft/BaselineManagement)의 **BaselineManagement**에 대한 새로운 이슈를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59881-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="59881-124">다음 단계</span><span class="sxs-lookup"><span data-stu-id="59881-124">Next steps</span></span>

- <span data-ttu-id="59881-125">구성 스크립트를 Azure Automation 상태 구성으로 업로드하려면 [시작하기](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59881-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="59881-126">**SecurityPolicyDSC** 및 **AuditPolicyDSC** 모듈을 [Automation 계정](/azure/automation/shared-resources/modules)에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="59881-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="59881-127">[PowerShell 갤러리](https://www.powershellgallery.com/)에서는 DSC 구성 및 리소스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59881-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
