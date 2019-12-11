---
ms.date: 03/27/2018
contributor: JKeithB
keywords: gallery,powershell,psgallery,GDPR
title: PowerShell 갤러리 GDPR 준수
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328324"
---
# <a name="powershell-gallery-gdpr-compliance"></a>PowerShell 갤러리 GDPR 준수

## <a name="overview"></a>개요

2018년 5월부터 유럽 개인 정보 보호법인 GDPR(General Data Protection Regulation)이 시행되었습니다.
GDPR은 기업, 정부 기관, 비영리 단체, 그리고 EU(유럽 연합)의 사람들에게 물품과 서비스를 제공하거나 EU 거주자와 관련된 데이터를 수집하고 분석하는 기타 조직에 새로운 규칙을 적용합니다.
GDPR은 귀하가 어디에 있든 관계없이 적용됩니다.

> [!NOTE]
> 이 문서는 PowerShell 갤러리에서 개인 데이터를 삭제하는 방법에 대한 단계를 제공하며 GDPR 하에서 의무를 이행하는 데 사용할 수 있습니다. GDPR에 대한 일반적인 정보는 [서비스 신뢰 포털의 GDPR 섹션](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted)을 참조하세요.

## <a name="personally-identifiable-data"></a>개인 식별 데이터

PowerShell 갤러리에는 개인 정보가 포함되어 있고 사용자가 제공할 수 있는 다음 정보가 저장됩니다.

- PowerShell 갤러리 계정
- PowerShell 갤러리에 게시된 패키지
- PowerShell 갤러리 팀과 이메일 서신

대부분의 사용자는 PowerShell 갤러리 계정을 만들지 않습니다
PowerShell 갤러리에서 패키지를 게시하거나 "소유자에게 문의"기능을 사용하지 않는 한 계정이 필요하지 않습니다.
PowerShell 갤러리는 사용자가 시작한 이메일 서신을 제외하고 계정을 만들지 않은 사용자의 개인 식별 데이터를 저장하지 않습니다.

PowerShell 갤러리 계정을 만든 사용자는 PowerShell 갤러리에 패키지를 게시할 수 있습니다.
이러한 패키지는 PowerShell 코드이며, 추가로 개인 정보를 비롯한 기타 정보가 포함될 수 있습니다.
아래에서는 PowerShell 갤러리에 게시한 모든 패키지를 가져오는 방법을 설명합니다.

## <a name="dsr-export-of-powershell-gallery-data"></a>PowerShell 갤러리 데이터의 DSR 내보내기

다음 절에서는 PowerShell 갤러리가 데이터 주체 요청(DSR)을 지원하는 방법과 PowerShell 갤러리에 저장된 정보를 내보내는 방법, 그리고 이 정보를 삭제하는 방법을 설명합니다.

### <a name="email"></a>메일

이메일 서신에는 다음 중 하나가 포함될 수 있습니다.

- 코드 분석 검색에서 PowerShell 갤러리에 게시한 패키지와 관련된 문제가 감지된 경우 PowerShell 갤러리 패키지 소유자에게 발송되는 메일
- "문의처" 페이지([cgadmin@microsoft.com](mailto:cgadmin@microsoft.com))에서 이메일 주소를 사용하여 누군가가 PowerShell 갤러리 팀에 보낸 이메일
- PowerShell 갤러리에서 "소유자에게 문의" 기능을 사용하여 PowerShell 갤러리의 패키지 소유자에게 메일을 보내는 등록된 사용자

PowerShell 갤러리에서 보내거나 PowerShell 갤러리로 보낸 이메일에는 PowerShell 갤러리에서 악성 코드 발견 시 보안 조사를 수행하기 위해 90일 보존 정책이 있습니다.
이메일은 90일 후에 정책에 의해 삭제됩니다.

지난 90일 이내에 자신의 이메일 주소와 PowerShell 갤러리에서 보내거나 받은 모든 이메일의 사본을 요청할 수 있습니다.
이 서신을 요청하려면 [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)으로 “이 계정과 관련된 메일에 대한 DSR 요청”이라는 제목으로 메일을 보내세요.
메시지 본문에 요청하려는 정보를 기재하세요(예: 이 메일 주소와 주고 받은 모든 메일을 보내주세요). 요청 후 90일 이내에 이메일 주소와 관련된 모든 이메일은 영업일 기준 7일 이내에 발송됩니다.

### <a name="powershell-gallery-account-information"></a>PowerShell 갤러리 계정 정보

PowerShell 갤러리 계정을 만든 경우 다음 단계를 수행하여 PowerShell 갤러리에 저장된 모든 개인 정보를 찾을 수 있습니다.

1. PowerShell 갤러리에 로그인한 후 사용자 이름을 클릭
2. 표시된 다음 페이지는 PowerShell 갤러리 계정에 사용된 이메일 주소를 보여주는 계정 페이지임

PowerShell 갤러리에서 둘 이상의 계정을 만든 경우 각 계정에 대해 이 단계를 반복해야 합니다.

### <a name="packages-in-the-powershell-gallery"></a>PowerShell 갤러리에 있는 패키지

PowerShell 갤러리에 게시된 패키지를 쉽게 내보낼 수 있도록 "GetPSGalleryItemsForAuthor" 스크립트를 PowerShell 갤러리에 게시했습니다.
이 스크립트는 패키지에 저장된 작성자 정보를 기반으로 PowerShell 갤러리에 있는 모든 패키지의 모든 버전의 복사본을 내보냅니다.

> [!NOTE]
> 작성자는 패키지를 게시할 때 패키지 매니페스트에 저장됩니다.
> 작성자가 PowerShell 갤러리에서 사용하는 계정과 동일한 ID라는 보장은 없습니다.
> 작성자 필드에서 다른 값을 사용하는 경우 이 스크립트를 사용할 때 해당 값을 제공해야 합니다.

다음 PowerShell 명령을 사용하여 스크립트를 다운로드할 수 있습니다.

```powershell
Save-Script Get-repository psgallery
```

다음 PowerShell 명령을 실행하여 스크립트를 직접 실행할 수 있습니다.

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

패키지를 저장하려는 시스템에 작성자와 폴더를 입력하라는 메시지가 나타납니다.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>PowerShell 갤러리에서 개인 데이터 삭제

PowerShell 갤러리 계정이나 PowerShell 갤러리에서 소유하고 있는 패키지를 삭제하려면 cgadmin@microsoft.com으로 "이 계정과 관련된 항목에 대한 GDPR 요청"이라는 제목으로 메일을 보내세요.
메시지 본문에는 삭제할 정보가 표시됩니다. 예:

- 내 패키지의 "패키지 이름"에서 버전 x.y.z를 삭제하세요.
- 내 패키지의 "패키지 이름"에서 버전을 모두 삭제하세요.
- PowerShell 갤러리 계정을 삭제하세요.

PowerShell 갤러리 관리자는 영업일 기준 7일 이내에 회신합니다.
지정된 패키지는 요청이 전송된 후 30일 이내에 삭제됩니다.
