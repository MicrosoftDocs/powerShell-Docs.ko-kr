---
title: Runspace 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857909"
---
# <a name="creating-runspaces"></a>runspace 만들기

Runspace에는 호스트 응용 프로그램에서 호출 되는 명령에 대 한 운영 환경입니다. 이 환경에는 명령 및 현재 존재 하는 데이터 및 현재 적용 되는 언어 제한이 포함 됩니다.

 응용 프로그램을 호스트 명령도 사용 가능한 코어를 포함 하는 Windows PowerShell에서 제공 하는 기본 runspace를 사용 하거나 사용 가능한 명령의 하위 집합만 포함 하는 사용자 지정 runspace를 만들 수 있습니다. 만든 runspace를 만드는 사용자 지정에 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체에 runspace에 할당 합니다.

## <a name="runspace-tasks"></a>Runspace 작업

1. [InitialSessionState 만들기](./creating-an-initialsessionstate.md)

2. [제한 된 runspace 만들기](./creating-a-constrained-runspace.md)

3. [여러 runspace 만들기](./creating-multiple-runspaces.md)

## <a name="see-also"></a>참고 항목
