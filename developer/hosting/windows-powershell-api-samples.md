---
title: Windows PowerShell API 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082586"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API 샘플

이 섹션에서는 기능을 제한 하는 runspace를 만드는 방법과 비동기적으로 runspace를 제공 하는 runspace 풀을 사용 하 여 명령을 실행 하는 방법을 보여 주는 샘플 코드를 포함 합니다. 콘솔 응용 프로그램을 만들고 다음 호스트 응용 프로그램에이 섹션의 항목에서 코드를 복사 하려면 Microsoft Visual Studio를 사용할 수 있습니다.

## <a name="in-this-section"></a>이 섹션의 내용

[샘플 PowerShell01](./windows-powershell01-sample.md) 이 샘플에 사용 하는 방법을 보여 줍니다는 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) runspace의 기능을 제한 하는 개체입니다. 이 샘플의 출력에 runspace, 개인용으로 cmdlet을 표시 하는 방법, 추가 하는 방법 및 제거 cmdlet 및 공급자, 언어 모드를 제한 하는 방법을 보여 줍니다. 프록시 명령을 등을 추가 하는 방법입니다.

[PowerShell02 샘플](./windows-powershell02-sample.md) runspace 풀의 runspace를 사용 하 여 명령을 비동기적으로 실행 하는 방법을이 보여 줍니다. 샘플 명령의 목록을 생성 하 고 필요할 때 풀에서 runspace는 Windows PowerShell 엔진 열립니다 하는 동안 다음 해당 명령을 실행 합니다.