---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5280ef5ff95679dc8721be8f5f81031a4ffe796f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085249"
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="1d4d2-102">FileInfo 개체에 대한 업데이트</span><span class="sxs-lookup"><span data-stu-id="1d4d2-102">Updates to FileInfo object</span></span>
<span data-ttu-id="1d4d2-103">파일 버전 정보는 잘못될 수 있습니다. 특히 파일이 패치된 경우는 더욱 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d2-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="1d4d2-104">이 WMF Production Preview 릴리스에서는 새로운 **FileVersionRaw** 및 **ProductVersionRaw** 스크립트 속성을 FileInfo 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d2-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="1d4d2-105">다음은 powershell.exe에 대해 표시되는 속성입니다($pid는 PowerShell 프로세스의 ID로 간주).</span><span class="sxs-lookup"><span data-stu-id="1d4d2-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
