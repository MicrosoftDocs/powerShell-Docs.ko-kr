---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: cmdlet 문제 해결
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328304"
---
# <a name="troubleshooting-cmdlets"></a>cmdlet 문제 해결

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>"경고: '패키지 이름' 패키지를 다운로드하지 못했습니다." 문제를 해결하는 방법

`Install-Module` 또는 `Update-Module`이 일부 컴퓨터에서 실패하는 경우가 있다는 신고를 받았습니다.
조사 결과에 따르면 이 문제는 네트워킹 연결과 관련이 있습니다.
최근에 패키지를 안정적으로 다운로드할 수 있도록 NuGet 공급자를 업데이트했습니다.
아래 지침에 따라 NuGet 공급자의 최신 빌드를 설치한 다음 모듈을 설치 또는 업데이트할 수 있습니다.
아래에서는 'Azure' 모듈을 예로 사용합니다.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
