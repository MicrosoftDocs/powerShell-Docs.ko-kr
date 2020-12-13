---
ms.date: 09/13/2016
ms.topic: reference
title: 형식 지정 파일(.format.ps1xml)을 만드는 방법
description: 형식 지정 파일(.format.ps1xml)을 만드는 방법
ms.openlocfilehash: 5bbc1ba40bfccf13636abc0f0751938aa724b761
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652001"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>형식 지정 파일(.format.ps1xml)을 만드는 방법

이 항목에서는 서식 파일 (.format.ps1xml)을 만드는 방법에 대해 설명 합니다.

> [!NOTE]
> Windows PowerShell에서 제공 하는 파일 중 하나를 복사 하 여 서식 파일을 만들 수도 있습니다. 기존 파일의 복사본을 만드는 경우 기존 디지털 서명을 삭제 하 고 새 파일에 고유한 서명을 추가 합니다.

### <a name="to-create-a-formatps1xml-file"></a>.format.ps1xml 파일을 만듭니다.

1. 메모장과 같은 텍스트 편집기를 사용 하 여 텍스트 파일 (.txt)을 만듭니다.

2. 다음 줄을 서식 파일에 복사 합니다.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - `<Configuration></Configuration>`태그는 루트 노드를 정의 합니다 `Configuration` . 모든 추가 XML 태그는이 노드 내에 포함 됩니다.

   - `<ViewDefinitions></ViewDefinitions>`태그는 노드를 정의 합니다 `ViewDefinitions` . 모든 뷰는이 노드 내에 정의 됩니다.

3. Windows PowerShell 설치 폴더, 모듈 폴더 또는 모듈 폴더의 하위 폴더에 파일을 저장 합니다. 파일을 저장할 때 다음 이름 형식을 사용  `MyFile.format.ps1xml` 합니다.. 서식 파일은 확장명을 사용 해야 합니다 `.format.ps1xml` .

   이제 서식 파일에 뷰를 추가할 준비가 되었습니다. 서식 파일에서 정의할 수 있는 뷰 수에는 제한이 없습니다. 각 개체에 대해 단일 뷰를 추가 하거나, 동일한 개체에 대 한 여러 뷰를 추가 하거나, 여러 개체에서 사용 하는 단일 뷰를 추가할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 서식 지정 및 형식 파일 작성](./writing-a-powershell-formatting-file.md)
