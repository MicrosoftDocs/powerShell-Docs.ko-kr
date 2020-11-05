---
ms.date: 06/09/2017
title: PowerShell 갤러리 UI에 영향을 주는 패키지 매니페스트 값
description: 이 문서에서는 PowerShell 갤러리에서 사용하는 모듈 매니페스트의 값에 대해 설명합니다.
ms.openlocfilehash: c59f65e72874a8a4ef946c954e1e8f12aad62b29
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664138"
---
# <a name="package-manifest-values-that-impact-the-powershell-gallery-ui"></a>PowerShell 갤러리 UI에 영향을 주는 패키지 매니페스트 값

이 항목에서는 PowerShellGet cmdlet의 기능과 PowerShell 갤러리 UI에 영향을 주는 PowerShell 갤러리 게시에 대한 매니페스트를 수정하는 방법에 관한 요약 정보를 게시자에게 제공합니다. 이 콘텐츠는 가운데 섹션에서 시작하여 왼쪽의 탐색 영역까지 변경 내용이 표시되는 위치별로 구성됩니다. 태그를 다루는 자세한 섹션이 있습니다. 이 섹션에서는 일반적으로 사용되는 태그와 중요한 태그를 확인합니다. 다음 두 항목에서 매니페스트 예를 제공합니다.

- 모듈의 경우 [모듈 매니페스트 업데이트](/powershell/module/powershellget/Update-ModuleManifest)를 참조하세요.
- 스크립트의 경우 [메타데이터를 사용하여 스크립트 파일 만들기](/powershell/module/powershellget/New-ScriptFileInfo)를 참조하세요.

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>매니페스트로 관리되는 PowerShell 갤러리 기능 요소

아래 표에는 게시자가 관리하는 PowerShell 갤러리 패키지 페이지 UI의 요소가 나와 있습니다. 각 항목은 모듈 매니페스트로 관리되는지, 스크립트 매니페스트로 관리되는지를 나타냅니다.

| UI 요소 | Description | 모듈 | 스크립트 |
| --- | --- | --- | --- |
| **제목** | 갤러리에 게시되는 패키지의 이름입니다.  | 예 | 예 |
| **버전** | 표시되는 버전은 메타데이터의 버전 문자열이며, 버전이 지정된 경우 시험판입니다. 모듈 매니페스트에서 버전의 주 부분은 ModuleVersion입니다. 스크립트의 경우 .VERSION으로 식별됩니다. 시험판 버전 문자열이 지정되면 모듈의 경우 ModuleVersion에 추가되며, 스크립트의 경우 .VERSION의 일부로 지정됩니다. [모듈](module-prerelease-support.md) 및 [스크립트](script-prerelease-support.md)에 시험판 문자열 지정에 대한 설명서가 있습니다. | yes | yes |
| **설명** | 모듈 매니페스트의 설명이며, 스크립트 파일 매니페스트에서는 .DESCRIPTION입니다. | yes | yes |
| **라이선스 동의 필요** | 모듈은 모듈 매니페스트를 RequireLicenseAcceptance = $true로 수정하고, LicenseURI를 제공하고, 모듈 폴더의 루트에 license.txt 파일을 제공하여 사용자가 라이선스를 승인하도록 요구할 수 있습니다. [라이선스 동의 필요](../how-to/working-with-packages/packages-that-require-license-acceptance.md) 항목에서 추가 정보를 확인할 수 있습니다. | yes | 예 |
| **릴리스 정보** | 모듈의 경우 이 정보는 PSData\PrivateData 아래의 ReleaseNotes 섹션에서 가져옵니다. 스크립트 매니페스트에서는 .RELEASENOTES 요소입니다. | yes | yes |
| **소유자** | 소유자는 패키지를 업데이트할 수 있는 PowerShell 갤러리의 사용자 목록입니다. 소유자 목록은 패키지 매니페스트에 포함되지 않습니다. 추가 문서에 [항목 소유자 관리](../how-to/publishing-packages/managing-package-owners.md)방법이 설명되어 있습니다. | 예 | 예 |
| **작성자** | 모듈 매니페스트에 작성자로 포함되며, 스크립트 매니페스트에서는 .AUTHOR로 포함됩니다. 작성자 필드는 패키지와 연결된 회사 또는 조직을 지정하는 데 자주 사용됩니다. | yes | yes |
| **Copyright** | 모듈 매니페스트의 저작권 필드이며, 스크립트 매니페스트의 .COPYRIGHT입니다. | yes | yes |
| **FileList** | 파일 목록은 PowerShell 갤러리에 게시될 때 패키지에서 가져옵니다. 매니페스트 정보로 제어할 수 없습니다. 참고: PowerShell 갤러리에는 각 패키지와 함께 나열된 추가 .nuspec 파일이 있습니다. 이 파일은 시스템에 패키지를 설치한 후에는 존재하지 않습니다. 패키지에 대한 Nuget 패키지 매니페스트이며, 무시할 수 있습니다. | 예 | 예 |
| **태그** | 모듈의 경우 태그는 PSData\PrivateData 아래에 포함됩니다. 스크립트의 경우 섹션은 .TAGS로 레이블이 지정됩니다. 태그는 따옴표 안에 있는 경우에도 공백을 포함할 수 없습니다. 태그에는 추가 요구 사항과 의미가 있습니다. 추가 요구 사항과 의미는 이 항목의 뒷부분에 있는 태그 세부 정보 섹션에 설명되어 있습니다. | yes | yes |
| **Cmdlet** | CmdletsToExport를 사용하여 모듈 매니페스트에 제공됩니다. 가장 좋은 방법은 사용자의 load-module 성능을 개선하므로 와일드카드 “*”를 사용하는 대신 항목을 명시적으로 나열하는 것입니다. | yes | 예 |
| **함수** | FunctionsToExport를 사용하여 모듈 매니페스트에 제공됩니다. 가장 좋은 방법은 사용자의 load-module 성능을 개선하므로 와일드카드 “*”를 사용하는 대신 항목을 명시적으로 나열하는 것입니다. | yes | 예 |
| **DSC 리소스** | PowerShell 버전 5.0 이상에서 사용되는 모듈의 경우 DscResourcesToExport를 사용하여 매니페스트에 제공됩니다. 모듈이 PowerShell 4에서 사용되는 경우 DSCResourcesToExport는 지원되는 매니페스트 키가 아니므로 사용할 수 없습니다. (DSC는 PowerShell 4 이전에서는 사용할 수 없습니다.) | yes | 예 |
| **워크플로** | 워크플로는 PowerShell 갤러리에 스크립트로 게시되고 코드에서 워크플로로 식별됩니다([Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) 참조). 워크플로는 매니페스트에서 제어되지 않습니다. | 예 | 예 |
| **역할 기능** | PowerShell 갤러리에 게시되는 모듈에 JEA에서 사용되는 하나 이상의 역할 기능(.psrc) 파일이 있을 때 나열됩니다. [역할 기능](/powershell/scripting/learn/remoting/jea/role-capabilities)에 대한 자세한 내용은 JEA 문서를 참조하세요. | yes | 예 |
| **PowerShell 버전** | 스크립트 또는 모듈 매니페스트에 지정됩니다. PowerShell 5.0 이하에서 사용하도록 디자인된 모듈의 경우 태그를 사용하여 제어됩니다. Desktop의 경우 PSEdition_Desktop 태그를 사용하고, Core의 경우 PSEdition_Core를 사용합니다. PowerShell 5.1 이상에서만 사용할 모듈의 경우 주 매니페스트에 CompatiblePSEditions 키가 있습니다. 자세한 내용은 [PowerShell Get 설명서](module-psedition-support.md)에서 PS Edition 기능을 참조하세요. | yes | yes |
| **종속성** | 종속성은 모듈에서 RequiredModules로 선언되거나 스크립트 매니페스트에서 #Requires –Module (이름)로 선언되는 PowerShell 갤러리의 모듈입니다. | yes | yes |
| **최소 PowerShell 버전** | 모듈 매니페스트에서 PowerShellVersion으로 지정될 수 있습니다. | yes | 예 |
| **버전 기록** | 버전 기록은 PowerShell 갤러리의 모듈에 대한 업데이트를 반영합니다. 삭제 기능을 사용하여 패키지의 버전이 숨겨져 있으면 패키지 소유자에게만 표시되고 버전 기록에는 표시되지 않습니다. | 예 | 예 |
| **프로젝트 사이트** | 프로젝트 사이트는 ProjectURI를 지정하여 모듈 매니페스트의 Privatedata\PSData 섹션의 모듈에 대해 제공됩니다. 스크립트 매니페스트에서는 .PROJECTURI를 지정하여 제어됩니다. | yes | yes |
| **라이선스** | 라이선스 링크는 LicenseURI를 지정하여 모듈 매니페스트의 Privatedata\PSData 섹션의 모듈에 대해 제공됩니다. 스크립트 매니페스트에서는 .LICENSEURI를 지정하여 제어됩니다. 라이선스가 LicenseURI를 통해 제공되지 않거나 모듈 내에서 제공되지 않는 경우, PowerShell 갤러리에 대한 사용 약관에 패키지에 대한 사용 약관이 명시됩니다. 자세한 내용은 사용 약관을 참조하세요. | yes | yes |
| **아이콘** | 스크립트 매니페스트에서 또는 모듈 매니페스트의 Privatedata-PSData 섹션에서 IconURI 플래그를 제공하여 PowerShell 갤러리의 패키지에 대한 아이콘을 지정할 수 있습니다. IconURI는 배경이 투명한 85x85 이미지를 가리켜야 합니다. URI는 **반드시** 직접 이미지 URL이어야 하며, 이미지가 포함된 웹 페이지 또는 PowerShell 갤러리 패키지의 파일로 이동하면 **안 됩니다**. | yes | yes |

## <a name="editing-package-details"></a>패키지 세부 정보 편집

PowerShell 갤러리 편집 패키지 페이지에서는 게시자가 패키지에 대해 표시되는 여러 필드를 변경할 수 있습니다.

- 제목
- Description
- 요약
- 아이콘 URL
- 프로젝트 홈페이지 URL
- Authors
- 저작권
- 태그들
- 릴리스 정보
- 라이선스 필요

모듈의 이전 버전에 대해 표시되는 내용을 정정하는 데 필요한 경우를 제외하고, 이 방식은 일반적으로 권장되지 않습니다. 모듈을 구입하는 사용자는 메타데이터가 PowerShell 갤러리에 표시되는 메타데이터와 일치하지 않음을 확인하고 패키지에 대해 우려하게 됩니다. 그러면 변경 내용을 확인하기 위해 패키지 소유자에게 문의하게 됩니다. 이러한 방식을 사용할 때마다 새 버전의 패키지를 동일한 변경 내용을 포함하여 게시해야 합니다.

## <a name="tag-details"></a>태그 세부 정보

태그는 소비자가 패키지를 찾기 위해 사용하는 간단한 문자열입니다. 태그는 동일한 주제와 관련된 여러 패키지에서 일관되게 사용되는 경우 가장 효과적입니다. 동일한 단어의 여러 특징을 사용하면(예를 들어 database와 databases, 또는 test와 testing) 일반적으로 효과적이지 않습니다. 태그는 대/소문자를 구분하지 않는 단일 단어 문자열이며 공백을 포함할 수 없습니다. 사용자가 검색할 것 같은 구문을 패키지 설명에 추가하면 검색 결과에 표시됩니다. 가독성을 향상하려면 파스칼식 대/소문자, 하이픈, 밑줄 또는 마침표를 사용하세요.
길고 복잡하고 특이한 태그는 철자가 틀리기 쉬우므로 주의하세요.

PowerShell 갤러리 및 PowerShellGet cmdlet이 고유하게 처리하는 태그가 있습니다. 구체적인 예로 PSEdition_Desktop과 PSEdition_Core가 있으며, 위에 설명되어 있습니다.

위에서 설명한 것처럼 태그는 구체적이고 여러 패키지에서 일관되게 사용되는 경우 가장 효과적입니다. 사용할 최상의 태그를 찾으려는 게시자로서 가장 쉬운 방법은 PowerShell 갤러리에서 태그를 검색하는 것입니다. 이상적으로는 많은 패키지가 반환될 것이며, 패키지 설명이 해당 키워드 사용과 함께 제공됩니다.

2017년 12월 14일 기준으로 가장 일반적으로 사용되는 태그는 다음과 같습니다. 경우에 따라 태그 옆에 비슷하지만 덜 적합한 옵션이 표시됩니다. 기본 태그를 사용하는 것이 가장 좋습니다. 노이즈가 적고 소비자에게 더 나은 검색 결과를 제공하기 때문입니다.

| 기본 태그 | 대체 및 메모 |
| --- | --- |
| Azure |  |
| DSC | DesiredStateConfiguration은 그다지 적합하지 않습니다. 너무 깁니다. |
| ResourceManager | ARM은 프로세서 그룹을 설명하는 데 사용되며, Azure Resource Manager에 대해 사용해서는 안 됩니다. |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| DSCResource |  |
| Automation |  |
| REST (영문) |  |
| ActiveDirectory | AD는 현재 단독으로 사용되지 않습니다.  |
| SQLServer |  |
| DBA |  |
| 보안 | Defense는 덜 정확합니다. |
| 데이터베이스 | Databases(복수)는 그다지 적합하지 않습니다. |
| DevOps |  |
| Windows |  |
| 빌드 |  |
| 배포 | Deploy는 자주 사용되지 않습니다. |
| 클라우드 |  |
| GIT |  |
| 테스트 | Testing은 그다지 적합하지 않습니다. |
| VersionControl | Version은 더 자주 사용되지만 덜 정확합니다.  |
| 로깅 | 동작인 경우 Logging을 사용하는 것이 좋습니다. |
| 로그 | 사물인 경우 Log를 사용하는 것이 좋습니다. |
| Backup |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| 스토리지 |  |
| GitHub |  |
| Json |  |
| Exchange |  |
| 네트워크 | Networking은 비슷하지만 자주 사용되지 않습니다. |
| SharePoint |  |
| 보고 | Reporting은 동작이고 Report는 사물입니다. |
| 보고서 | Report는 사물입니다. |
| WinRM |  |
| 모니터링 |  |
| VSTS |  |
| Excel |  |
| Google |  |
| 색 |  |
| DNS |  |
| Office365 | Office의 철자를 모두 쓰는 것이 좋습니다. O365는 짧지만 일반적으로 사용되지 않습니다. |
| Gitlab |  |
| Pester |  |
| AzureAD |  |
| HTML |  |
| Hyper-V | HyperV는 일반적으로 태그로 사용되지 않습니다. |
| 구성 |  |
| ChatOps |  |
| PackageManagement |  |
| WMI |  |
| 방화벽 |  |
| Docker |  |
| Appveyor |  |
| AzureRm | 주로 AzureRM 모듈에 대해 사용됩니다. |
| Zip |  |
| MSI |  |
| MacOS |  |
| PoshBot |  |
