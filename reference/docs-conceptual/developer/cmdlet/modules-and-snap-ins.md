---
title: 모듈 및 스냅인 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365372"
---
# <a name="modules-and-snap-ins"></a>모듈 및 스냅인

Cmdlet은 모듈 (Windows PowerShell 2.0에서 도입) 또는 스냅인을 사용 하 여 세션에 추가할 수 있습니다. Cmdlet이 세션에 추가 되 면 호스트 응용 프로그램에서 프로그래밍 방식으로 실행 하거나 명령줄에서 대화형으로 실행할 수 있습니다.

다음 이유 때문에 cmdlet을 세션에 추가 하기 위한 배달 방법으로 모듈을 사용 하는 것이 좋습니다.

- 모듈을 사용 하 여 cmdlet이 정의 된 어셈블리를 로드 하 여 cmdlet을 추가할 수 있습니다. 스냅인 클래스를 구현할 필요는 없습니다.

- 모듈을 사용 하 여 변수, 함수, 스크립트, 형식 및 서식 파일 등의 다른 리소스를 추가할 수 있습니다.

- 스냅인은 cmdlet 및 공급자를 세션에 추가 하는 데만 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
