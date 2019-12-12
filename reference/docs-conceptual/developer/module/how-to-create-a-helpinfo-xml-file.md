---
title: HelpInfo XML 파일을 만드는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367322"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>HelpInfo XML 파일을 만드는 방법

이 섹션의이 항목에서는 Windows PowerShell 업데이트할 수 있는 도움말 기능에 대 한 도움말 정보 파일 (일반적으로 "HelpInfo XML file" 이라고 함)을 만들고 채우는 방법을 설명 합니다.

## <a name="helpinfo-xml-file-overview"></a>HelpInfo XML 파일 개요

HelpInfo XML 파일은 모듈에 대 한 업데이트할 수 있는 도움말에 대 한 정보의 기본 출처입니다. 여기에는 모듈에 대 한 도움말 파일의 위치, 지원 되는 UI 문화권 및 사용자에 게 최신 도움말 파일이 있는지 여부를 확인 하는 데 사용할 수 있는 버전 번호가 포함 됩니다.

모듈에 여러 UI 문화권에 대 한 여러 도움말 파일이 포함 되어 있는 경우에도 각 모듈에는 HelpInfo XML 파일이 하나 뿐입니다. 모듈 작성자는 HelpInfo XML 파일을 만들고 모듈 매니페스트의 **HelpInfoUri** 키로 지정 된 인터넷 위치에 배치 합니다. 모듈 도움말 파일을 업데이트 및 업로드 하면 모듈 작성자가 HelpInfo XML 파일을 업데이트 하 고 원래 HelpInfo XML 파일을 새 버전으로 바꿉니다.

HelpInfo XML 파일을 신중 하 게 유지 관리 하는 것이 중요 합니다. 새 파일을 업로드 하 고 버전 번호를 늘리는 경우 업데이트할 수 있는 도움말은 사용자의 컴퓨터에 새 파일을 다운로드 하지 않습니다. 새 UI 문화권에 대 한 도움말 파일을 추가 하지만 HelpInfo XML 파일을 업데이트 하지 않거나 올바른 위치에 배치 하지 않으면 업데이트할 수 있는 도움말이 새 파일을 다운로드 하지 않습니다.

## <a name="in-this-section"></a>이 섹션의 내용

이 섹션에는 다음 항목이 포함됩니다.

- [HelpInfo XML 스키마](./helpinfo-xml-schema.md)

- [HelpInfo XML 샘플 파일](./helpinfo-xml-sample-file.md)

- [HelpInfo XML 파일의 이름을로 만드는 방법](./how-to-name-a-helpinfo-xml-file.md)

- [HelpInfo XML 버전 번호를 설정 하는 방법](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>참고 항목

[업데이트할 수 있는 도움말 지원](./supporting-updatable-help.md)