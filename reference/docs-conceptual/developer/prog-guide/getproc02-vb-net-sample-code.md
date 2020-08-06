---
title: GetProc02 (VB.NET) 샘플 코드 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 98261f2d6678e24bb8e8df6d2c8a405b25203364
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787175"
---
# <a name="getproc02-vbnet-sample-code"></a>GetProc02(VB.NET) 코드 샘플

다음 코드는 `Get-Process` 명령줄 입력을 허용 하는 cmdlet의 구현을 보여 줍니다. 이 구현에서는 `Name` 명령줄 입력을 허용 하는 매개 변수를 정의 하 고, 출력 개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 [WriteObject (system.object, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 메서드를 사용 합니다.

## <a name="code-sample"></a>코드 예제

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
