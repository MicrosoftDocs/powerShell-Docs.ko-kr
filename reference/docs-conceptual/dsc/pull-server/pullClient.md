---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 끌어오기 클라이언트 설정
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955170"
---
# <a name="setting-up-a-dsc-pull-client"></a>DSC 끌어오기 클라이언트 설정

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> 끌어오기 서버(Windows 기능 *DSC-Service*)는 Windows Server의 지원되는 구성 요소이지만 새로운 기능을 제공할 계획은 없습니다. 관리되는 클라우드를 [Azure Automation DSC](/azure/automation/automation-dsc-getting-started)(Windows Server에 끌어오기 서버 이외의 기능 포함) 또는 [여기](pullserver.md#community-solutions-for-pull-service)에 나열된 커뮤니티 솔루션 중 하나로 전환하기 시작하는 것이 좋습니다.

각 대상 노드는 끌어오기 모드를 사용하도록 지시받고 끌어오기 서버에 연결하여 구성 및 리소스를 가져올 수 있는 URL 또는 파일 위치와 보고서 데이터를 보내야 하는 URL 또는 파일 위치를 받아야 합니다.

다음 항목에서는 끌어오기 클라이언트를 설정하는 방법에 대해 설명합니다.

* [구성 이름을 사용하여 끌어오기 클라이언트 설정](pullClientConfigNames.md)
* [구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID.md)

> [!NOTE]
> 이 토픽은 PowerShell 5.0에 적용됩니다. PowerShell 4.0에서 끌어오기 클라이언트를 설정하려면 [PowerShell 4.0에서 구성 ID를 사용하여 끌어오기 클라이언트 설정](pullClientConfigID4.md)을 참조합니다.