---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc02(VB.NET) 코드 샘플
description: GetProc02(VB.NET) 코드 샘플
ms.openlocfilehash: aefc3a4df5e0f29120916648ecdca41931a4c1c6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93354544"
---
# <a name="getproc02-vbnet-sample-code"></a>GetProc02(VB.NET) 코드 샘플

다음 코드는 `Get-Process` 명령줄 입력을 허용 하는 cmdlet의 구현을 보여 줍니다. 이 구현에서는 `Name` 명령줄 입력을 허용 하는 매개 변수를 정의 하 고, 출력 개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 [WriteObject (system.object, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 메서드를 사용 합니다.

## <a name="code-sample"></a>코드 예제

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
