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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860499"
---
# <a name="modules-and-snap-ins"></a>모듈 및 스냅인

Cmdlet (Windows PowerShell 2.0에서 도입 됨) 하는 모듈이 나 스냅인을 사용 하 여 세션에 추가할 수 있습니다. Cmdlet은 호스트 응용 프로그램 또는 명령줄에서 대화형으로 프로그래밍 방식으로 실행할 수 있습니다 세션에 추가 됩니다.

다음과 같은 이유로 세션에 cmdlet을 추가 하는 것에 대 한 배달 방법으로 모듈을 사용 하는 것이 좋습니다.

- 모듈의 cmdlet가 정의 되어 있는 어셈블리를 로드 하 여 cmdlet을 추가 할 수 있습니다. 스냅인 클래스를 구현할 필요가 없습니다 있습니다.

- 모듈을 사용 하면 변수, 함수, 스크립트, 형식 및 서식 파일 등과 같은 기타 리소스를 추가할 수 있습니다.

- 스냅인만 세션에 cmdlet 및 공급자를 추가 하려면 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
