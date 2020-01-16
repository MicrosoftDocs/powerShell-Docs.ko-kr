---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget,갤러리
title: PowerShell 갤러리
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327864"
---
# <a name="the-powershell-gallery"></a>PowerShell 갤러리

PowerShell 갤러리는 PowerShell 콘텐츠의 중앙 리포지토리입니다. PowerShell 갤러리에서 PowerShell 명령 및 DSC(필요한 상태 구성) 리소스가 포함된 유용한 PowerShell 모듈을 찾을 수 있습니다.
PowerShell 워크플로가 포함된 경우도 있으며 일련의 작업을 간략하게 설명하고 해당 작업 순서를 제공하는 PowerShell 스크립트를 찾을 수도 있습니다. 이러한 패키지 중 일부는 Microsoft에서 작성되었으며 다른 항목은 PowerShell 커뮤니티에서 작성되었습니다.

## <a name="powershellget-overview"></a>PowerShellGet 개요

PowerShellGet 모듈에는 [PowerShell 갤러리](https://www.PowerShellGallery.com) 및 다른 개인 리포지토리에서 모듈, DSC 리소스, 역할 기능 및 스크립트와 같은 아티팩트가 포함된 PowerShell 패키지를 검색, 설치, 업데이트 및 게시하기 위한 cmdlet이 포함되어 있습니다.

## <a name="getting-started-with-the-gallery"></a>갤러리 시작

갤러리에서 패키지를 설치하려면 최신 버전의 PowerShellGet 모듈이 필요합니다.
자세한 지침은 [PowerShellGet](installing-psget.md) 설치를 참조하세요.

갤러리와 함께 PowerShellGet 명령을 사용하는 방법에 대한 자세한 내용은 [시작](getting-started.md) 페이지를 참조하세요. *Update-Help -Module PowerShellGet*을 실행하여 이러한 명령에 대한 로컬 도움말을 설치할 수도 있습니다.

## <a name="supported-operating-systems"></a>지원되는 운영 체제

**PowerShellGet** 모듈을 사용하려면 **Windows PowerShell 3.0 이상** 또는 **PowerShell Core 6.0 이상**이 필요합니다.

적합한 **Windows PowerShell** 버전을 사용할 수 있는 운영 체제는 다음과 같습니다.

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet**을 사용하려면 .NET Framework 4.5 이상이 필요합니다. .NET Framework 4.5 이상은 [여기](https://msdn.microsoft.com/library/5a4x27ek.aspx)에서 설치할 수 있습니다.

**PowerShell Core**는 교차 플랫폼이므로 Windows, Linux 및 MacOS에서 작동하며, 그렇기 때문에 **PowerShellGet**을 이러한 시스템들에서 사용할 수 있습니다. **PowerShell Core**가 지원하는 전체 시스템 목록은 [PowerShell 설치](/powershell/scripting/setup/installing-powershell)를 참조하세요.

갤러리에 호스트된 많은 모듈은 각기 다른 OS를 지원하며 추가 요구 사항이 있습니다. 자세한 내용은 모듈 설명서를 참조하세요.

## <a name="got-a-question-have-feedback"></a>궁금한 점이 있나요? 피드백이 있습니까?

PowerShell 갤러리 및 PowerShellGet에 대한 자세한 내용은 [시작](getting-started.md) 페이지에서 확인할 수 있습니다. [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell)를 사용하여 피드백을 제공하고 문제를 신고하세요.
