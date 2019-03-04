---
title: 도움말 CAB 파일을 업데이트할 수 있는에서 허용 하는 파일 형식 | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 931383858c0b83f0a9a66026c215e16481b89e9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862839"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>업데이트 가능한 도움말 CAB 파일 이름에 허용되는 파일 형식

이 항목 나열 하 고 업데이트할 수 있는 도움말 CAB 파일에 대 한 콘텐츠 요구 사항에 설명 합니다.

## <a name="updatable-help-cab-file-requirements"></a>업데이트 가능한 도움말 CAB 파일 요구 사항

압축 되지 않은 CAB 파일 콘텐츠는 기본적으로 1GB로 제한 됩니다. 이 한도 무시 하려면 사용자를 사용 해야 합니다 **Force** 의 매개 변수를 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet.
압축 되지 않은 CAB 파일 콘텐츠는 기본적으로 1GB로 제한 됩니다. 이 한도 무시 하려면 사용자를 사용 해야 합니다 **Force** 의 매개 변수를 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet.

인터넷에서 다운로드 하는 도움말 파일의 보안을 보장 하는 업데이트 가능한 도움말 CAB 파일 아래에 나열 된 파일 형식만 포함할 수 있습니다. 합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 도움말 항목에서는 스키마에 대해 모든 파일의 유효성을 검사 합니다. 경우는 `Update-Help` 는 유효 하지 않거나 허용 된 형식이 아닌 파일을 발견 하는 cmdlet, 잘못 된 파일을 설치 하지 않습니다 고에서 사용자의 컴퓨터에서 CAB 파일 설치를 중지 합니다.
인터넷에서 다운로드 하는 도움말 파일의 보안을 보장 하는 업데이트 가능한 도움말 CAB 파일 아래에 나열 된 파일 형식만 포함할 수 있습니다. 합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 도움말 항목에서는 스키마에 대해 모든 파일의 유효성을 검사 합니다. 경우는 `Update-Help` 는 유효 하지 않거나 허용 된 형식이 아닌 파일을 발견 하는 cmdlet, 잘못 된 파일을 설치 하지 않습니다 고에서 사용자의 컴퓨터에서 CAB 파일 설치를 중지 합니다.

- Cmdlet에 대 한 XML 기반 도움말 항목

- 스크립트 및 함수에 대 한 XML 기반 도움말 항목

- Windows PowerShell 공급자에 대 한 XML 기반 도움말 항목

- 텍스트 기반 항목을 같은 항목에 대 한 도움말입니다.

합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) CAB 압축을 풉니다 CAB 내용을 확인 합니다. 경우 `Update-Help` 업데이트할 수 있는 도움말 CAB 파일에 호환 되지 않는 파일 형식, 종료 오류를 생성 하 고 작업을 중지를 찾습니다. 규정을 준수 하는 파일 형식 이더라도 CAB에서 도움말 파일을 설치 하지 않습니다.
합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) CAB 압축을 풉니다 CAB 내용을 확인 합니다. 경우 `Update-Help` 업데이트할 수 있는 도움말 CAB 파일에 호환 되지 않는 파일 형식, 종료 오류를 생성 하 고 작업을 중지를 찾습니다. 규정을 준수 하는 파일 형식 이더라도 CAB에서 도움말 파일을 설치 하지 않습니다.