---
ms.date: 07/09/2019
keywords: dsc,gpo,powershell,configuration,setup
title: 빠른 시작 - 그룹 정책을 DSC로 변환
ms.openlocfilehash: a9ce9cecd71fe00d2908024a3ee474ec836af3ba
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808251"
---
# <a name="quickstart-convert-group-policy-into-dsc"></a>빠른 시작: 그룹 정책을 DSC로 변환

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

그룹 정책 또는 Azure Security Center 기준에서 DSC 구성을 생성할 수 있습니다. [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) 모듈에는 이 작업을 수행하기 위한 다음 명령이 포함되어 있습니다.

- `ConvertFrom-GPO` - 파일로 저장된 그룹 정책을 변환합니다. 하나의 구성으로 결합될 여러 정책을 포함하는 디렉터리를 지정할 수도 있습니다.
  - 환경에서 그룹 정책을 내보내려면 [GPO 백업](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet을 사용하거나 [파일로 GPO 내보내기](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file)의 지침을 따릅니다.
- `ConvertFrom-SCM` - `.xml` 파일로 저장된 Security Compliance Manager 기준선을 변환합니다.
- `ConvertFrom-ASC` - `.json` 파일로 저장된 Azure Security Center 기준선을 변환합니다.
- `Merge-GPOs` - 대상 컴퓨터에 적용된 그룹 정책을 변환합니다.

위에 나열된 cmdlet은 기준선을 DSC `.mof` 파일로 변환합니다. 편집하고 다시 컴파일할 수 있는 구성 스크립트(`.ps1`)를 출력하도록 선택할 수도 있습니다. cmdlet은 누락된 리소스 또는 중복된 리소스 블록에 대한 컴파일 오류를 검색합니다. 컴파일 오류를 발생시키는 리소스 블록은 주석 처리됩니다.

다음 예제에서는 [Microsoft Security 기준선](https://www.microsoft.com/en-us/download/details.aspx?id=55319)을 DSC 구성 스크립트(`.ps1`) 및 `.mof` 파일로 변환합니다.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

명령을 실행한 후 현재 경로 아래에 생성된 기본 "Output" 디렉터리에 두 개의 파일이 표시됩니다.

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

각 관리 노드에는 다음 두 모듈도 필요합니다.

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement**는 Microsoft가 아닌 프로젝트 유지 관리자로부터 커뮤니티 솔루션에 대한 지원을 DSC가 더 쉽게 검색할 수 있도록 커뮤니터에서 개발한 솔루션입니다. [GitHub](https://github.com/microsoft/BaselineManagement)의 **BaselineManagement**에 대한 새로운 이슈를 열 수 있습니다.

## <a name="next-steps"></a>다음 단계

- 구성 스크립트를 Azure Automation 상태 구성으로 업로드하려면 [시작하기](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation)를 참조하세요.
- **SecurityPolicyDSC** 및 **AuditPolicyDSC** 모듈을 [Automation 계정](/azure/automation/shared-resources/modules)에 추가합니다.
- [PowerShell 갤러리](https://www.powershellgallery.com/)에서는 DSC 구성 및 리소스를 찾을 수 있습니다.
