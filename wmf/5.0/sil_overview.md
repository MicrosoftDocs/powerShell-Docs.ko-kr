---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7e87ed4bc9a86be52d4d06d3e87386a1111227c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085017"
---
# <a name="software-inventory-logging-sil"></a>소프트웨어 인벤토리 로깅(SIL)

**중요:** ‘SIL이 이미 실행되고 있는 Windows Server 2012 R2 서버에 WMF 5.0을 설치하는 경우 설치 프로세스에서 소프트웨어 인벤토리 로깅 기능을 잘못 중지하므로 WMF 설치 후 Start-SilLogging cmdlet을 한 번 실행해야 합니다.’

소프트웨어 인벤토리 로깅을 사용하면 서버에 로컬로 설치된 Microsoft 소프트웨어에 대한 정확한 정보를 가져오는 운영 비용을 줄일 수 있지만 특히 IT 환경(소프트웨어가 IT 환경에서 설치되어 실행되고 있는 것으로 가정)의 여러 서버에서 그렇습니다. 설정된 다음에는 이 데이터를 집계 서버로 전달하고 균일한 자동 프로세스를 사용하여 로그 데이터를 한 곳에 수집할 수 있습니다.

각 컴퓨터를 직접 쿼리하여 소프트웨어 인벤토리 데이터를 로깅할 수도 있지만 소프트웨어 인벤토리 로깅에서는 각 서버에서 시작되는 전달(네트워크를 통해) 아키텍처를 사용하여 많은 소프트웨어 인벤토리 및 자산 관리 시나리오에 일반적인 서버 검색 문제를 방지할 수 있습니다. 소프트웨어 인벤토리 로깅에서는 SSL을 사용하여 HTTPS를 통해 집계 서버로 전달되는 데이터를 보호합니다. 데이터를 한 곳에 저장하면 필요할 때 보다 쉽게 데이터를 분석, 조작 및 공유할 수 있습니다.

이러한 데이터는 이 기능의 일부로 Microsoft에 전송되지 않습니다. 소프트웨어 인벤토리 로깅 데이터 및 기능은 서버 소프트웨어의 라이선스 소유자 및 관리자만 사용할 수 있습니다.

소프트웨어 인벤토리 로깅 cmdlet에 대한 자세한 내용 및 설명서는 Windows Server 2012 R2 온라인 리소스(<http://technet.microsoft.com/library/dn383584.aspx>)를 참조하세요.
