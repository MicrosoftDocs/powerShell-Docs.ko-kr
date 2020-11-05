---
ms.date: 06/12/2017
title: cmdlet 문제 해결
description: 이 문서에서는 PowerShell 갤러리를 사용하여 오류를 해결하는 데 필요한 정보 및 단계를 제공합니다.
ms.openlocfilehash: db9e58c185c6f3bca26ff3639af85fa2dba48909
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661060"
---
# <a name="troubleshooting-cmdlets"></a>cmdlet 문제 해결

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>"경고: '패키지 이름' 패키지를 다운로드하지 못했습니다." 문제를 해결하는 방법

`Install-Module` 또는 `Update-Module`이 일부 컴퓨터에서 실패하는 경우가 있다는 신고를 받았습니다. 조사 결과에 따르면 이 문제는 네트워킹 연결과 관련이 있습니다. 최근에 패키지를 안정적으로 다운로드할 수 있도록 NuGet 공급자를 업데이트했습니다. 아래 지침에 따라 NuGet 공급자의 최신 빌드를 설치한 다음 모듈을 설치 또는 업데이트할 수 있습니다. 아래에서는 'Azure' 모듈을 예로 사용합니다.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a>필수 네트워크 엔드포인트

설치 및 업데이트 cmdlets에는 PowerShell 갤러리에서 사용하는 네트워크 엔드포인트로의 연결을 위해 인터넷 액세스가 필요합니다. 네트워크 액세스 정책에 따라 다음 엔드포인트로 연결할 수 있는지 확인하십시오.

- oneget.org
- go.microsoft.com
- az818661.vo.msecnd.net
- www.powershellgallery.com
- devopsgallerystorage.blob.core.windows.net
