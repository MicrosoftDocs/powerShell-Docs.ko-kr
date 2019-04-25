---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057930"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>DSC 리소스의 Side-By-Side 모듈 버전 관리 지원

DSC 리소스를 포함하는 모듈은 병렬로 설치할 수 있으며, DSC 구성에서는 시스템에 설치되어 있는 특정 버전의 리소스를 사용할 수 있습니다.

자세한 내용은 [여러 버전의 리소스 사용](https://msdn.microsoft.com/powershell/dsc/sxsresource)을 참조하세요.

## <a name="known-issues"></a>알려진 문제

이번 릴리스에서 병렬 설치에는 다음과 같은 알려진 문제가 있습니다.

-   동일한 구성 내에서 두 가지 다른 버전의 DSC 리소스를 사용할 수 없습니다.
