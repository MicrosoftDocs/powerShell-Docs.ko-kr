---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f655cd7aa9b14bd38924d55c8f1246b55ef83756
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085856"
---
# <a name="enhanced-transcription-options"></a><span data-ttu-id="bfdbd-102">향상된 기록 옵션</span><span class="sxs-lookup"><span data-stu-id="bfdbd-102">Enhanced Transcription Options</span></span>

<span data-ttu-id="bfdbd-103">Windows PowerShell 기록이 단순한 콘솔 호스트(powershell.exe)가 아닌 모든 호스팅 애플리케이션(예: Windows PowerShell ISE)에 적용되도록 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bfdbd-103">Windows PowerShell transcription has been improved to apply to all hosting applications (such as Windows PowerShell ISE) rather than just the console host (powershell.exe).</span></span>

<span data-ttu-id="bfdbd-104">기록이 확장될 뿐만 아니라 기록의 임의 중첩, 결과 기록 헤더의 추가 메타데이터, 기록 출력 디렉터리 설정으로 중앙 집중화된 로그 컬렉션 지원 등을 지원하도록 기록 기능 자체가 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bfdbd-104">In addition to extending for transcripting, the transcripting functionality itself has been updated to support arbitrary nesting of transcripts, additional metadata in the resulting transcript header, and setting a transcription output directory (to support centralized log collection).</span></span>

<span data-ttu-id="bfdbd-105">시스템 차원의 기록 사용을 포함한 기록 옵션은 **PowerShell 기록 켜기** 그룹 정책 설정(관리 템플릿 -> Windows 구성 요소 -> Windows PowerShell)을 사용하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfdbd-105">Transcription options (including enabling a system-wide transcript) can be configured with the **Turn on PowerShell Transcription** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>
