---
title: Cmdlet 설명을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361282"
---
# <a name="how-to-add-a-cmdlet-description"></a>Cmdlet 설명을 추가하는 방법

이 섹션에서는 cmdlet 도움말의 설명 섹션에 표시 되는 콘텐츠를 추가 하는 방법에 대해 설명 합니다. 도움말 파일에서이 콘텐츠는 각 cmdlet에 대 한 명령 노드에 추가 됩니다.

> [!NOTE]
> 도움말 파일의 전체 보기를 보려면 Windows PowerShell 설치 디렉터리에 있는 dll-Help 파일 중 하나를 엽니다. 예를 들어 dll-Help 파일에는 몇 가지 Windows PowerShell cmdlet에 대 한 내용이 포함 되어 있습니다.

### <a name="to-add-a-description"></a>설명을 추가 하려면

- 먼저 cmdlet의 기본 기능에 대해 자세히 설명 합니다. 대부분의 경우 cmdlet 이름에 사용 되는 용어를 설명 하 고 예제를 사용 하 여 익숙하지 않은 개념을 설명할 수 있습니다. 예를 들어 cmdlet이 파일에 데이터를 추가 하는 경우 기존 파일의 끝에 데이터를 추가 함을 설명 합니다.

- Cmdlet의 모든 기능을 찾으려면 매개 변수 목록을 검토 합니다. Cmdlet의 기본 기능을 설명 하 고 다른 함수 및 기능을 포함 합니다. 예를 들어 cmdlet의 main 함수가 하나의 속성을 변경 하는 것 이지만이 cmdlet은 자세한 설명에서 모든 속성을 변경할 수 있습니다. Cmdlet 매개 변수를 사용 하 여 사용자가 다른 방법으로 정보를 요청 하는 경우 설명 합니다.

- 사용자가이 cmdlet을 사용할 수 있는 방법 뿐만 아니라 명확한 사용 방법에 대 한 정보를 포함 합니다. 예를 들어, `Get-Host` cmdlet이 검색 하는 개체를 사용 하 여 Windows PowerShell 명령 창의 텍스트 색을 변경할 수 있습니다.

  예: "`Get-Acl` cmdlet은 파일 또는 리소스의 보안 설명자를 나타내는 개체를 가져옵니다. 보안 설명자에는 리소스의 ACL(액세스 제어 목록)이 포함되어 있습니다. ACL은 사용자 및 사용자 그룹이 리소스에 액세스 해야 하는 권한을 지정 합니다. "

- 자세한 설명은 cmdlet에 대해 설명 하지만 cmdlet에서 사용 하는 개념을 설명 하지는 않습니다. 추가 참고 사항에 개념 정의를 입력 합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
