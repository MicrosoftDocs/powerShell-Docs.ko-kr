---
title: Cmdlet 이름 및 개요 Cmdlet 도움말 항목을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083340"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 Cmdlet 이름 및 개요를 추가하는 방법

이 섹션에는 cmdlet 도움말의 이름과 개요 섹션에 표시 되는 콘텐츠를 추가 하는 방법을 설명 합니다. 도움말 파일에서이 콘텐츠는 각 cmdlet에 대 한 명령 노드로 추가 됩니다.

> [!NOTE]
> 에 대 한 도움말 파일의 열린 Windows PowerShell 설치 디렉터리에 있는 dll Help.xml 파일 중 하나는 전체 보기입니다. 예를 들어 Microsoft.PowerShell.Commands.Management.dll Help.xml 파일 다양 한 Windows PowerShell cmdlet에 대 한 콘텐츠를 포함합니다.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Cmdlet 이름 및 개요를 추가 하려면

- Cmdlet 도움말에는 cmdlet에 대 한 두 설명을 표시할 수 있습니다. 첫 번째 설명에는 개요를 참조 하는 간단한 설명이입니다. 두 번째 설명에서 설명 하는 자세한 설명입니다 [Cmdlet 도움말 항목에 자세한 설명이 추가](./how-to-add-a-cmdlet-description.md)합니다. 이러한 설명은 모두 단일 단락으로 작성 되어야 합니다.

- 개요에 cmdlet 이름을 반복 하지 않습니다. 서버는 cmdlet을 사용자에 게 알리는 하는 것은 간단 하면서도 이지만 정보를 제공 하지 않습니다. 대신 동의어를 사용 하 고 설명에 대 한 세부 정보를 추가 합니다.

  예: "로컬 또는 원격 컴퓨터를 나타내는 개체를 가져옵니다."

- "Get", "만들기" 및 "변경"의 개요와 같은 간단한 동사를 사용 합니다. 모호한, 것 이므로 부르는 같은 "수정". "설정"을 사용 하지 마십시오

  예: "파일에서 Authenticode 서명 정보를 가져옵니다."

- 능동태를 작성 합니다. 예를 들어 "사용" TimeSpan 개체... "TimeSpan 개체 수..." 보다 훨씬 명확

- 개체를 가져오는 cmdlet을 설명 하는 경우 "표시" 동사를 방지 합니다. Windows PowerShell cmdlet은 데이터를 표시 하는 경우 이지만 사용자가 cmdlet은 해당 데이터가 표시 될 수 있습니다 하는.NET Framework 개체를 반환 하는 개념을 소개 하는 것이 중요 합니다. 표시를 강조 하는 경우 사용자가 다른 여러 유용한 속성 및 메서드 표시 되지 않는 cmdlet 반환 수 있습니다 모를 수도 있습니다.

## <a name="see-also"></a>참고 항목

 [Windows PowerShell SDK](../windows-powershell-reference.md)