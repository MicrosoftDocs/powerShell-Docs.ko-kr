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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083521"
---
# <a name="how-to-add-a-cmdlet-description"></a>Cmdlet 설명을 추가하는 방법

이 섹션에는 cmdlet 도움말의 설명 섹션에 표시 되는 콘텐츠를 추가 하는 방법을 설명 합니다. 도움말 파일에서이 콘텐츠는 각 cmdlet에 대 한 명령 노드로 추가 됩니다.

> [!NOTE]
> 에 대 한 도움말 파일의 열린 Windows PowerShell 설치 디렉터리에 있는 dll Help.xml 파일 중 하나는 전체 보기입니다. 예를 들어 Microsoft.PowerShell.Commands.Management.dll Help.xml 파일 다양 한 Windows PowerShell cmdlet에 대 한 콘텐츠를 포함합니다.

### <a name="to-add-a-description"></a>설명을 추가 하려면

- 자세히 cmdlet의 기본 기능을 설명 하 여 시작 합니다. 대부분의 경우 cmdlet 이름에 사용 된 용어를 설명 하 고 예제를 사용 하 여 알 수 없는 개념을 설명 수입니다. 예를 들어, cmdlet은 데이터 파일에 추가 하는 경우 기존 파일의 끝에 데이터를 추가 하는 설명 합니다.

- 모든 cmdlet의 기능을 찾으려면 매개 변수 목록을 검토 합니다. Cmdlet의 기본 기능을 설명 하 고 다른 함수 및 기능을 포함 합니다. 예를 들어, cmdlet의 주요 함수 하나의 속성을 변경 하는 cmdlet의 모든 속성을 변경할 수 있지만 경우 그렇게 말할 자세한 설명입니다. Cmdlet 매개 변수를 다른 방법으로 정보를 요청할 수에 대해 설명 합니다.

- 사용자가 분명 사용 하는 것 외에도 cmdlet을 사용할 수 있는 방법에 대 한 정보를 포함 합니다. 예를 들어 개체를 사용할 수 있습니다 하는 `Get-Host` cmdlet은 Windows PowerShell 명령 창에서 텍스트의 색을 변경 하는 검색 합니다.

  예:  "는 `Get-Acl` cmdlet은 파일 또는 리소스의 보안 설명자를 나타내는 개체를 가져옵니다. 보안 설명자에는 리소스의 ACL(액세스 제어 목록)이 포함되어 있습니다. ACL 지정 권한이 있는 사용자 및 사용자 그룹 리소스에 액세스할 수 있습니다. "

- 자세히 기술 한 cmdlet 설명 해야 하지만 cmdlet을 사용 하는 개념을 설명 하지 해야 합니다. 추가 정보에 개념 정의 배치 합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
