---
ms.date: 06/12/2017
title: 항목 만들기 및 게시
description: 이 문서에서는 스크립트 또는 모듈을 준비하여 PowerShell 갤러리에 게시하는 방법과 중요한 단계에 대해 설명합니다.
ms.openlocfilehash: be846799aff71d38bdd0c98b3f43eaee5aef7798
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662515"
---
# <a name="creating-and-publishing-an-item"></a>항목 만들기 및 게시

PowerShell 갤러리에서는 안정적인 PowerShell 모듈, 스크립트 및 DSC(Desired State Configuration) 리소스를 게시하여 광범위한 PowerShell 사용자 커뮤니티와 공유할 수 있습니다.

이 문서에서는 스크립트나 모듈을 준비하고 PowerShell 갤러리에 게시하는 방법과 중요한 단계에 대해 설명합니다. [게시 지침](../../concepts/publishing-guidelines.md)을 검토하여 게시하는 항목을 보다 많은 PowerShell 갤러리 사용자들이 활용할 수 있도록 하는 방법을 파악하는 것이 좋습니다.

PowerShell 갤러리에 항목을 게시하기 위한 최소 요구 사항은 다음과 같습니다.

- PowerShell 갤러리 계정 및 계정에 연결된 API 키가 있어야 합니다.
- 항목에 필수 메타데이터가 포함되어 있어야 합니다.
- 사전 유효성 검사 도구를 사용하여 항목을 게시할 준비가 되었는지를 확인해야 합니다.
- Publish-Module 및 Publish-Script 명령을 사용하여 PowerShell 갤러리에 항목을 게시해야 합니다.
- 항목에 대한 문의 사항이나 문제 제기에 응답해야 합니다.

PowerShell 갤러리에서는 PowerShell 모듈 및 PowerShell 스크립트를 게시할 수 있습니다. 여기서 스크립트란 대규모 모듈의 일부분이 아니라 단일 파일인 PowerShell 스크립트를 의미합니다.

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell 갤러리 계정 및 API 키

PowerShell 갤러리 계정을 설정하는 방법은 [PowerShell 갤러리 계정 만들기](creating-an-account.md)를 참조하세요.

계정을 만들면 항목을 게시하는 데 필요한 API 키를 받을 수 있습니다. 계정으로 로그인하고 나면 PowerShell 갤러리 페이지 위쪽에 "등록"이 아닌 사용자 이름이 표시됩니다. 사용자 이름을 클릭하면 내 계정 페이지로 이동하게 되며, 이 페이지에서 API 키를 확인할 수 있습니다.

> [!IMPORTANT]
> 참고: API 키는 로그인 및 암호와 마찬가지로 안전하게 취급해야 합니다. 이 키를 사용하면 사용자를 비롯하여 누구나 PowerShell 갤러리에서 소유한 항목을 업데이트할 수 있습니다. 따라서 키를 정기적으로 업데이트하는 것이 좋습니다. 내 계정 페이지에서 키 다시 설정을 사용하여 키를 업데이트할 수 있습니다.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>PowerShell 갤러리에 게시하는 항목의 필수 메타데이터

PowerShell 갤러리에서는 스크립트 또는 모듈 매니페스트에 포함된 메타데이터 필드에서 가져온 정보를 갤러리 사용자에게 제공합니다. 따라서 PowerShell 갤러리에 게시할 항목을 만들거나 수정할 때는 항목 매니페스트에서 제공되는 정보에 대한 몇 가지 요구 사항을 충족해야 합니다. [게시 지침](../../concepts/publishing-guidelines.md)의 항목 메타데이터 섹션을 검토하여 항목 사용자에게 가장 적절한 정보를 제공하는 방법을 파악하는 것이 좋습니다.

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest) 및 [New-ScriptFileInfo](/powershell/module/PowerShellGet/New-ScriptFileInfo) cmdlet이 매니페스트 템플릿을 자동으로 생성하며, 모든 매니페스트 요소는 자리 표시자로 지정됩니다.

두 매니페스트에는 PrivateData의 기본 키 데이터 및 PSData 영역을 게시하기 위해 중요한 두 개의 섹션이 포함됩니다. PowerShell 모듈 매니페스트의 기본 키 데이터는 PrivateData 섹션을 제외한 모든 항목입니다. 기본 키 집합은 사용 중인 PowerShell 버전과 연결되며, 정의되지 않은 키는 지원되지 않습니다. PrivateData의 경우에는 새 키를 추가할 수 있으므로 PowerShell 갤러리와 관련된 요소는 PSData에 포함됩니다.

PowerShell 갤러리에 게시하는 항목에 대해 입력해야 하는 가장 중요한 매니페스트 요소는 다음과 같습니다.

- 스크립트 또는 모듈 이름 - 스크립트의 경우 .PS1, 모듈의 경우 .PSD1의 이름에서 가져옵니다.
- 버전 - 필수 기본 키이며 SemVer 지침의 형식을 따라야 합니다. 자세한 내용은 모범 사례를 참조하세요.
- 작성자 - 필수 기본 키이며 항목과 연결할 이름을 포함합니다. 아래의 작성자 및 소유자를 참조하세요.
- 설명 - 항목이 수행하는 작업과 항목 사용을 위한 요구 사항을 간략하게 설명하는 데 사용되는 필수 기본 키입니다.
- ProjectURI - 항목 개발을 수행하는 Github 리포지토리 또는 유사한 위치의 링크를 제공하는 PSData의 URI 필드로, 포함하는 것이 좋습니다.
- 태그 - PSEdition 및 플랫폼과의 호환성에 따라 패키지에 태그를 지정하는 것이 좋습니다. 자세한 내용은 [게시 지침](../../concepts/publishing-guidelines.md#tag-your-package-with-the-compatible-pseditions-and-platforms)을 참조하세요.

PowerShell 갤러리 항목의 작성자와 소유자는 서로 관련된 개념이지만 항상 일치하는 것은 아닙니다. 항목 소유자는 항목 유지 관리 권한이 있는 PowerShell 갤러리 계정을 소유한 사용자입니다. 항목을 업데이트할 수 있는 소유자가 여러 명일 수도 있습니다. 소유자는 PowerShell 갤러리에서만 사용 가능하며 시스템 간에 항목을 복사하면 손실됩니다. 작성자는 매니페스트 데이터에서 기본적으로 제공되는 문자열이므로 항상 항목의 일부분입니다. Microsoft 제품의 항목에 대한 권장 사항은 다음과 같습니다.

- 소유자를 여러 명 지정하고 한 명 이상의 이름을 항목을 제작하는 팀 이름으로 지정합니다.
- 작성자는 Azure SDK 팀 등 잘 알려진 팀 이름이나 Microsoft Corporation으로 지정합니다.

## <a name="pre-validate-your-item"></a>항목 사전 유효성 검사

항목을 PowerShell 갤러리에 게시하기 전에 코드에 대해 아래의 몇 가지 도구를 실행해야 합니다.

- [PowerShell 스크립트 분석기](https://www.powershellgallery.com/packages/PSScriptAnalyzer/)(PowerShell 갤러리에 있음)
- 모듈의 경우 Test-ModuleManifest(PowerShell의 일부분)
- 스크립트의 경우 Test-ScriptFileInfo(PowerShellGet과 함께 제공됨)

[PowerShell 스크립트 분석기](https://www.powershellgallery.com/packages/PSScriptAnalyzer/)는 코드를 검사하여 기본적인 PowerShell 코딩 지침을 충족하는지를 확인하는 정적 코드 분석 도구입니다. 이 도구는 코드에서 흔히 발생하는 중요한 문제를 파악하므로 개발 중에 정기적으로 실행하여 항목이 게시할 수 있는 상태인지를 확인해야 합니다. PowerShell 스크립트 분석기는 오류, 경고 및 정보로 식별된 문제 목록을 제공합니다. 모든 오류는 항목을 PowerShell 갤러리에 게시하기 전에 해결해야 합니다. 경고는 검토해야 하며 대다수는 해결해야 합니다. PowerShell 갤러리에서 항목을 게시하거나 업데이트할 때마다 PowerShell 스크립트 분석기가 실행됩니다. 그런 후에 갤러리 운영 팀이 확인된 오류 해결을 위해 항목 소유자에게 연락을 합니다.

항목의 매니페스트 정보를 PowerShell 갤러리 인프라에서 읽을 수 없는 경우에는 항목을 게시할 수 없습니다.
[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest)는 설치 시 모듈을 사용할 수 없게 만드는 일반적인 문제를 찾아냅니다. 모든 모듈을 PowerShell 갤러리에 게시하기 전에 이 cmdlet을 실행해야 합니다.

마찬가지로 [Test-ScriptFileInfo](/powershell/module/PowerShellGet/test-scriptfileinfo)는 스크립트의 메타데이터 유효성을 검사합니다. 모듈과 별도로 게시하는 모든 스크립트를 PowerShell 갤러리에 게시하기 전에 이 cmdlet을 실행해야 합니다.

## <a name="publishing-items"></a>항목 게시

PowerShell 갤러리에 항목을 게시하려면 [Publish-Script](/powershell/module/PowerShellGet/publish-script) 또는 [Publish-Module](/powershell/module/PowerShellGet/publish-module)을 사용해야 합니다. 이 두 명령에는 다음 항목이 필요합니다.

- 게시할 항목의 경로. 모듈의 경우 모듈 이름이 지정된 폴더를 사용합니다. 같은 모듈의 여러 버전이 포함된 폴더를 지정하는 경우에는 RequiredVersion을 지정해야 합니다.
- Nuget API 키. PowerShell 갤러리의 내 계정 페이지에서 확인할 수 있는 API 키입니다.

명령줄에 포함된 대부분의 기타 옵션은 게시하는 항목의 매니페스트 데이터에 포함되어 있으므로 명령에서는 지정하지 않아도 됩니다.

오류를 방지하려면 게시 전에 -WhatIf -Verbose를 사용하여 명령을 실행해 보는 것이 좋습니다. PowerShell 갤러리에 항목을 게시할 때마다 항목의 매니페스트 섹션에서 버전 번호를 업데이트해야 하므로, 이렇게 하면 시간을 크게 절약할 수 있습니다.

예제는 다음과 같습니다.

* `Publish-Module -Path ".\MyModule" -NugetAPIKey "GUID" -WhatIf -Verbose`
* `Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -WhatIf -Verbose`

출력을 자세히 검토하고 오류나 경고가 없으면 -WhatIf 없이 명령을 다시 실행합니다.

PowerShell 갤러리에서는 게시하는 모든 항목에 대해 바이러스를 검사하며, PowerShell 스크립트 분석기를 사용하여 항목을 분석합니다. 이 시점에서 문제가 발생하면 해당 문제를 해결하도록 항목이 게시자에게 반송됩니다.

PowerShell 갤러리에 항목을 게시한 후에는 항목에 대한 피드백을 확인해야 합니다.

- 게시할 때 사용한 계정과 연결된 전자 메일 주소를 모니터링합니다. PowerShell 갤러리 운영 팀과 사용자들이 해당 계정을 통해 PSSA 또는 바이러스 백신 검사 시에 발생하는 문제를 비롯한 피드백을 제공합니다. 전자 메일 계정이 잘못되었거나 심각한 문제가 계정으로 보고되었는데 장기간 해결되지 않는 경우에는 항목 유지 관리가 중단된 것으로 간주되어 [사용 약관](https://www.powershellgallery.com/policies/Terms)의 설명에 따라 PowerShell 갤러리에서 제거됩니다.
