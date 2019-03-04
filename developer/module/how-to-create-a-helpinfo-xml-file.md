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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853269"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>HelpInfo XML 파일을 만드는 방법

이 섹션의이 항목에서는이 만들고 일반적으로 "HelpInfo XML 파일 이라는," Windows PowerShell 업데이트할 수 있는 도움말 기능에 대 한 도움말 정보 파일을 채우는 방법에 설명 합니다.

## <a name="helpinfo-xml-file-overview"></a>HelpInfo XML 파일 개요

HelpInfo XML 파일은 모듈에 대해 업데이트할 수 있는 도움말에 대 한 정보의 기본 소스. 모듈, 지원 되는 UI 문화권을 및 버전 번호는 사용자가 최신 도움말 파일을 확인 하는 업데이트 가능한 도움말에 대 한 도움말 파일의 위치를 포함 합니다.

각 모듈 모듈 여러 UI 문화권에 대 한 여러 도움말 파일을 포함 하는 경우에 하나의 HelpInfo XML 파일을 있습니다. 모듈 작성자 HelpInfo XML 파일을 생성 하 고 지정 된 인터넷 위치에 배치 합니다 **HelpInfoUri** 모듈 매니페스트 키입니다. 모듈 도움말 파일이 업데이트 되 고 업로드, 하는 경우 모듈 작성자 HelpInfo XML 파일을 업데이트 하 여 새 버전을 사용 하 여 원래 HelpInfo XML 파일을 바꿉니다.

반드시 HelpInfo XML 파일을 신중 하 게 유지 되도록 합니다. 새 파일을 업로드 해도 버전 번호를 증가 해야 하는 경우 업데이트할 수 있는 도움말 다운로드할 수 없습니다 새 파일을 사용자의 컴퓨터. 새 UI 문화권에 대 한 도움말 파일을 추가 하지만 하지 HelpInfo XML 파일을 업데이트 하거나 올바른 위치에 배치를 업데이트할 수 있는 도움말 다운로드할 수 없습니다 새 파일.

## <a name="in-this-section"></a>이 섹션의 내용

이 섹션에는 다음 항목이 포함됩니다.

- [HelpInfo XML 스키마](./helpinfo-xml-schema.md)

- [HelpInfo XML 샘플 파일](./helpinfo-xml-sample-file.md)

- [HelpInfo XML 파일의 이름을 지정 하는 방법](./how-to-name-a-helpinfo-xml-file.md)

- [HelpInfo XML 버전 번호를 설정 하는 방법](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>참고 항목

[업데이트 가능한 도움말 지원](./supporting-updatable-help.md)