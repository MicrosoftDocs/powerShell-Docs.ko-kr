---
title: Windows PowerShell Cmdlet 개념 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369122"
---
# <a name="windows-powershell-cmdlet-concepts"></a>Windows PowerShell Cmdlet 개념

이 섹션에서는 cmdlet의 작동 방식에 대해 설명 합니다.

## <a name="in-this-section"></a>이 섹션의 내용

이 섹션에는 다음 항목이 포함됩니다.

[Cmdlet 개발 지침](./cmdlet-development-guidelines.md) 이 항목에서는 올바른 형식의 cmdlet을 생성 하는 데 사용할 수 있는 개발 지침을 제공 합니다.

[Cmdlet 클래스 선언](./cmdlet-class-declaration.md) 이 항목에서는 cmdlet 클래스 선언에 대해 설명 합니다.

[Windows PowerShell 명령에 대해 승인 된 동사](./approved-verbs-for-windows-powershell-commands.md) 이 항목에서는 cmdlet 클래스를 선언할 때 사용할 수 있는 미리 정의 된 cmdlet 동사를 나열 합니다.

[Cmdlet 입력 처리 방법](./cmdlet-input-processing-methods.md) 이 항목에서는 cmdlet이 전처리 작업, 입력 처리 작업 및 사후 처리 작업을 수행할 수 있도록 하는 메서드에 대해 설명 합니다.

[Cmdlet 매개 변수](./cmdlet-parameters.md) 이 섹션에서는 cmdlet에 추가할 수 있는 다양 한 유형의 매개 변수를 설명 합니다.

[Cmdlet 특성](./cmdlet-attributes.md) 이 섹션에서는 .NET Framework 클래스를 cmdlet으로 선언 하 고, 필드를 cmdlet 매개 변수로 선언 하 고, 매개 변수에 대 한 입력 유효성 검사 규칙을 선언 하는 데 사용 되는 특성에 대해 설명 합니다.

[Cmdlet 별칭](./cmdlet-aliases.md) 이 항목에서는 cmdlet 별칭에 대해 설명 합니다.

[Cmdlet 출력](./cmdlet-output.md) 이 섹션에서는 cmdlet에서 반환할 수 있는 출력 유형과 cmdlet에서 반환 되는 개체를 정의 하 고 표시 하는 방법을 설명 합니다.

[Cmdlet 등록](./modules-and-snap-ins.md) 이 섹션에서는 모듈 및 스냅인을 사용 하 여 cmdlet을 등록 하는 방법에 대해 설명 합니다.

[확인 요청](./requesting-confirmation-from-cmdlets.md) 이 섹션에서는 사용자가 시스템을 변경 하기 전에 cmdlet에서 확인을 요청 하는 방법을 설명 합니다.

[Windows PowerShell 오류 보고](./error-reporting-concepts.md) 이 섹션에서는 cmdlet의 종료 오류 및 종료 되지 않는 오류를 보고 하는 방법에 대해 설명 하 고 오류 레코드를 해석 하는 방법을 설명 합니다.

[백그라운드 작업](./background-jobs.md) 이 항목에서는 cmdlet이 현재 세션에서 실행 되는 명령을 방해 하지 않는 백그라운드 작업 내에서 작업을 수행 하는 방법에 대해 설명 합니다.

[Cmdlet에서 cmdlet 및 스크립트 호출](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) 이 항목에서는 cmdlet이 입력 처리 메서드 내에서 다른 cmdlet 및 스크립트를 호출 하는 방법에 대해 설명 합니다.

[Cmdlet 집합](./cmdlet-sets.md) 이 항목에서는 기본 클래스를 사용 하 여 cmdlet 집합을 만드는 방법을 설명 합니다.

[Windows PowerShell 세션 상태](./windows-powershell-session-state.md) 이 항목에서는 Windows PowerShell 세션 상태에 대해 설명 합니다.
