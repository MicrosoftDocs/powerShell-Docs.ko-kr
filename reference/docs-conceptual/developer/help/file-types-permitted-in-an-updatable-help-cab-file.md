---
ms.date: 03/22/2012
ms.topic: reference
title: 업데이트 가능한 도움말 CAB 파일 이름에 허용되는 파일 형식
description: 업데이트 가능한 도움말 CAB 파일 이름에 허용되는 파일 형식
ms.openlocfilehash: bb69b8b89a9a3a5c8c00059ec404a4d41a5db9a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654743"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>업데이트 가능한 도움말 CAB 파일 이름에 허용되는 파일 형식

압축 되지 않은 CAB 파일 콘텐츠는 기본적으로 1gb로 제한 됩니다. 이 제한을 무시 하려면 사용자가 [update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [저장-도움말](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet의 **Force** 매개 변수를 사용 해야 합니다.

인터넷에서 다운로드 되는 도움말 파일의 보안을 보장 하기 위해 업데이트할 수 있는 도움말 CAB 파일에는 아래 나열 된 파일 유형만 포함 될 수 있습니다. [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet은 도움말 항목 스키마에 대 한 모든 파일의 유효성을 검사 합니다. Cmdlet이 `Update-Help` 잘못 되었거나 허용 되는 형식이 아닌 파일을 발견 하는 경우 잘못 된 파일을 설치 하지 않고 사용자 컴퓨터의 CAB 파일 설치를 중지 합니다.

- Cmdlet에 대 한 XML 기반 도움말 항목입니다.
- 스크립트 및 함수에 대 한 XML 기반 도움말 항목입니다.
- PowerShell 공급자에 대 한 XML 기반 도움말 항목입니다.
- 텍스트 기반 도움말 항목 (예: 정보 항목)

[업데이트-도움말](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 은 cab 파일의 압축을 풀고 cab 콘텐츠를 확인 합니다. `Update-Help`에서 업데이트할 수 있는 도움말 CAB 파일에 비규격 파일 형식을 찾으면 종료 오류를 생성 하 고 작업을 중지 합니다. 호환 되는 파일 형식의 경우에도 CAB에서 도움말 파일을 설치 하지는 않습니다.
