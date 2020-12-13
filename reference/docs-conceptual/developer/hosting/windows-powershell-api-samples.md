---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell API 샘플
description: Windows PowerShell API 샘플
ms.openlocfilehash: b6336ae7a2abb98cbbaa69bf6c9455f893db2d94
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657536"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API 샘플

이 섹션에는 기능을 제한 하는 runspace를 만드는 방법 및 runspace 풀을 사용 하 여 runspace를 제공 하 여 비동기적으로 명령을 실행 하는 방법을 보여 주는 샘플 코드가 포함 되어 있습니다. Microsoft Visual Studio를 사용 하 여 콘솔 응용 프로그램을 만든 후이 섹션의 항목에서 호스트 응용 프로그램으로 코드를 복사할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용

[PowerShell01 샘플](./windows-powershell01-sample.md) 이 샘플에서는 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 사용 하 여 runspace의 기능을 제한 하는 방법을 보여 줍니다. 이 샘플의 출력에서는 runspace의 언어 모드를 제한 하는 방법, cmdlet을 비공개로 표시 하는 방법, cmdlet 및 공급자를 추가 및 제거 하는 방법, 프록시 명령을 추가 하는 방법 등을 보여 줍니다.

[PowerShell02 샘플](./windows-powershell02-sample.md) 이 샘플에서는 runspace 풀의 runspace을 사용 하 여 비동기적으로 명령을 실행 하는 방법을 보여 줍니다. 이 샘플에서는 명령 목록을 생성 한 다음, Windows PowerShell 엔진이 필요할 때 풀에서 runspace를 열 때 해당 명령을 실행 합니다.
