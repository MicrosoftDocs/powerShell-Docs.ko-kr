---
ms.date: 09/13/2016
ms.topic: reference
title: runspace 만들기
description: runspace 만들기
ms.openlocfilehash: c6b2c577e435ec88364b189a0c3d065f54f02525
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649343"
---
# <a name="creating-runspaces"></a>runspace 만들기

Runspace는 호스트 응용 프로그램에서 호출 하는 명령에 대 한 운영 환경입니다. 이 환경에는 현재 존재 하는 명령 및 데이터와 현재 적용 되는 모든 언어 제한이 포함 됩니다.

 호스트 응용 프로그램은 사용 가능한 모든 핵심 명령을 포함 하는 Windows PowerShell에서 제공 하는 기본 runspace를 사용 하거나 사용 가능한 명령의 하위 집합만 포함 하는 사용자 지정 runspace를 만들 수 있습니다. 사용자 지정 runspace를 만들려면 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 만들고 runspace에 할당 합니다.

## <a name="runspace-tasks"></a>Runspace 작업

1. [InitialSessionState 만들기](./creating-an-initialsessionstate.md)

2. [제한된 runspace 만들기](./creating-a-constrained-runspace.md)

3. [여러 runspace 만들기](./creating-multiple-runspaces.md)

## <a name="see-also"></a>참고 항목
