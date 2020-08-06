---
title: Runspace 만들기 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0c27e2bf54e16a3bdc93c4b91629893bb1cc1e3e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779576"
---
# <a name="creating-runspaces"></a>runspace 만들기

Runspace는 호스트 응용 프로그램에서 호출 하는 명령에 대 한 운영 환경입니다. 이 환경에는 현재 존재 하는 명령 및 데이터와 현재 적용 되는 모든 언어 제한이 포함 됩니다.

 호스트 응용 프로그램은 사용 가능한 모든 핵심 명령을 포함 하는 Windows PowerShell에서 제공 하는 기본 runspace를 사용 하거나 사용 가능한 명령의 하위 집합만 포함 하는 사용자 지정 runspace를 만들 수 있습니다. 사용자 지정 runspace를 만들려면 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 만들고 runspace에 할당 합니다.

## <a name="runspace-tasks"></a>Runspace 작업

1. [InitialSessionState 만들기](./creating-an-initialsessionstate.md)

2. [제한된 runspace 만들기](./creating-a-constrained-runspace.md)

3. [여러 runspace 만들기](./creating-multiple-runspaces.md)

## <a name="see-also"></a>참고 항목
