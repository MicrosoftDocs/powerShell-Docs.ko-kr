---
ms.date: 09/12/2016
ms.topic: reference
title: GetProc03(VB.NET) 코드 샘플
description: GetProc03(VB.NET) 코드 샘플
ms.openlocfilehash: fc70496178c85e101b380e68aacd64c8d1f350e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355564"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03(VB.NET) 코드 샘플

다음 코드는 `Get-Process` 파이프라인 입력을 수락할 수 있는 cmdlet의 구현을 보여 줍니다. 이 구현은 `Name` 파이프라인 입력을 허용 하 고, 제공 된 이름에 따라 로컬 컴퓨터에서 프로세스 정보를 검색 하 고, 개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 [WriteObject (system.string, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 메서드를 사용 하는 매개 변수를 정의 합니다.

## <a name="code-sample"></a>코드 예제

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
