---
title: Cmdlet 이름 및 개요를 Cmdlet 도움말 항목에 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361192"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Cmdlet 도움말 항목에 Cmdlet 이름 및 개요를 추가하는 방법

이 섹션에서는 cmdlet 도움말의 NAME 및 개요 섹션에 표시 되는 콘텐츠를 추가 하는 방법에 대해 설명 합니다. 도움말 파일에서이 콘텐츠는 각 cmdlet에 대 한 명령 노드에 추가 됩니다.

> [!NOTE]
> 도움말 파일의 전체 보기를 보려면 Windows PowerShell 설치 디렉터리에 있는 dll-Help 파일 중 하나를 엽니다. 예를 들어 dll-Help 파일에는 몇 가지 Windows PowerShell cmdlet에 대 한 내용이 포함 되어 있습니다.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Cmdlet 이름 및 개요를 추가 하려면

- Cmdlet 도움말에는 cmdlet에 대 한 두 가지 설명이 표시 될 수 있습니다. 첫 번째 설명은 개요 이라고 하는 간단한 설명입니다. 두 번째 설명은 [Cmdlet 도움말 항목에](./how-to-add-a-cmdlet-description.md)대 한 자세한 설명을 추가 하는 방법에서 설명 하는 자세한 설명입니다. 두 설명을 모두 단일 단락으로 작성 해야 합니다.

- 개요 cmdlet 이름을 반복 하지 않습니다. 사용자에 게 Get Server cmdlet이 서버를 가져오지만 정보는 없다는 사실을 알려 줍니다. 대신 동의어를 사용 하 고 설명에 세부 정보를 추가 합니다.

  예: "로컬 또는 원격 컴퓨터를 나타내는 개체를 가져옵니다."

- 개요에서 "get", "create" 및 "change"와 같은 간단한 동사를 사용 합니다. "Set"는 모호 하 고 "modify"와 같은 고급 단어를 사용 하지 마십시오.

  예: "파일의 Authenticode 서명에 대 한 정보를 가져옵니다."

- 활성 음성으로 작성 합니다. 예: "TimeSpan 개체 사용 ..." "TimeSpan 개체를 사용할 수 있습니다." 보다 훨씬 더 명확 합니다.

- 개체를 가져오는 cmdlet을 설명할 때 동사 "display"를 사용 하지 않습니다. Windows PowerShell에서 cmdlet 데이터를 표시 하지만, 사용자에 게 데이터를 표시 하지 않을 수 있는 개체 .NET Framework cmdlet이 반환 한다는 개념을 소개 하는 것이 중요 합니다. 표시를 강조 표시 하는 경우 사용자는 cmdlet이 표시 되지 않는 다른 많은 유용한 속성 및 메서드를 반환 했을 수 있습니다.

## <a name="see-also"></a>참고 항목

 [Windows PowerShell SDK](../windows-powershell-reference.md)