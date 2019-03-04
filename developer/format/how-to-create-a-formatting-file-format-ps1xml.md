---
title: 형식 지정 파일을 만드는 방법 (. format.ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862969"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>형식 지정 파일(.format.ps1xml)을 만드는 방법

이 항목에서는 서식 파일을 만드는 방법에 설명 합니다 (. format.ps1xml).

> [!NOTE]
> 또한 Windows PowerShell에서 제공 하는 파일 중 하나의 복사본을 만들어 형식 지정 파일을 만들 수 있습니다. 기존 파일의 복사본을 만들면 기존 디지털 서명을 삭제 하 고 새 파일에 고유한 서명을 추가 합니다.

### <a name="to-create-a-formatps1xml-file"></a>만들려는. format.ps1xml 파일입니다.

1. 메모장과 같은 편집기 텍스트를 사용 하 여 텍스트 파일 (.txt)을 만듭니다.

2. 서식 파일에 다음 줄을 복사 합니다.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - 합니다 \<구성 >\</Configuration > 태그 정의 루트 `Configuration` 노드. 추가 하는 모든 XML 태그는이 노드 내에 묶어야 합니다.

   - 합니다 <ViewDefinitions> </ViewDefinitions> 태그를 정의 합니다 `ViewDefinitions` 노드. 모든 뷰는이 노드 내에서 정의 됩니다.

3. Windows PowerShell 설치 폴더, 모듈 폴더를 사용 하 여 또는 모듈 폴더의 하위 폴더에 파일을 저장 합니다. 파일을 저장 하면 다음과 같은 이름 형식을 사용 하 여: `MyFile.format.ps1xml`합니다. 서식 파일 사용 해야 합니다는 `.format.ps1xml` 확장 합니다.

   서식 파일에 뷰를 추가할 준비가 되었습니다. 서식 파일에 정의 될 수 있는 뷰의 수 제한은 없습니다. 각 개체, 동일한 개체에 대 한 여러 뷰 또는 여러 개체에서 사용 되는 단일 보기에 대 한 단일 뷰를 추가할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 형식 지정을 작성 하 고 파일 형식](./writing-a-powershell-formatting-file.md)
