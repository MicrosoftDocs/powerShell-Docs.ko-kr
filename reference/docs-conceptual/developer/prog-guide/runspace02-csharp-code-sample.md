---
title: Runspace02 (C#) 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: 047d14d70853399bc262ac3f1541da38184c3ff8
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977882"
---
# <a name="runspace02-c-code-sample"></a>Runspace02(C#) 코드 샘플

Runspace02 샘플에 C# 대 한 소스 코드는 다음과 같습니다. 이 샘플에서는 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하 여 `Get-Process` cmdlet을 동기적으로 실행 합니다. 그러면 Windows Forms 및 데이터 바인딩이 DataGridView 컨트롤에 결과를 표시 하는 데 사용 됩니다.

## <a name="code-sample"></a>코드 예제

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
