---
description: 종료 오류를 생성하는 Throw 키워드에 대해 설명합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: caac7679e2c7ecd21b4fa9e43ab76681ee3faed5
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222482"
---
# <a name="about-throw"></a>Throw 정보

## <a name="short-description"></a>간단한 설명

종료 오류를 생성하는 Throw 키워드에 대해 설명합니다.

## <a name="long-description"></a>자세한 설명

Throw 키워드는 종료 오류를 발생 시킵니다. Throw 키워드를 사용 하 여 명령, 함수 또는 스크립트의 처리를 중지할 수 있습니다.

예를 들어 If 문의 스크립트 블록에서 Throw 키워드를 사용 하 여 조건문의 조건 또는 Catch 블록에 응답할 수 있습니다. 매개 변수 선언에서 Throw 키워드를 사용 하 여 함수 매개 변수를 필수로 만들 수도 있습니다.

Throw 키워드는 사용자 메시지 문자열 또는 오류를 발생 시킨 개체와 같은 모든 개체를 throw 할 수 있습니다.

## <a name="syntax"></a>SYNTAX

Throw 키워드의 구문은 다음과 같습니다.

```powershell
throw [<expression>]
```

Throw 구문의 식은 선택 사항입니다. Catch 블록에 Throw 문이 표시 되지 않고 식이 포함 되지 않은 경우에는 스크립트가 잘못 된 오류를 생성 합니다.

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

Throw 키워드가 식 없이 Catch 블록에서 사용 되는 경우 현재 RuntimeException을 다시 throw 합니다. 자세한 내용은 about_Try_Catch_Finally를 참조 하세요.

## <a name="throwing-a-string"></a>문자열 THROW

Throw 문의 선택적 식은 다음 예제에 표시 된 것 처럼 문자열일 수 있습니다.

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a>다른 개체 THROW

식은 다음 예제와 같이 PowerShell 프로세스를 나타내는 개체를 throw 하는 개체 일 수도 있습니다.

```powershell
C:\PS> throw (get-process PowerShell)

System.Diagnostics.Process (PowerShell)
At line:1 char:6
+ throw <<<<  (get-process PowerShell)
+ CategoryInfo          : OperationStopped: (System.Diagnostics.Process (Pow
erShell):Process) [],
RuntimeException
+ FullyQualifiedErrorId : System.Diagnostics.Process (PowerShell)
```

$Error 자동 변수에 ErrorRecord 개체의 TargetObject 속성을 사용 하 여 오류를 검사할 수 있습니다.

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

ErrorRecord 개체 또는 Microsoft .NET 프레임 워크 예외를 throw 할 수도 있습니다. 다음 예제에서는 Throw 키워드를 사용 하 여 FormatException 개체를 throw 합니다.

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

One of the identified items was in an invalid format.
At line:1 char:6
+ throw <<<<  $formatError
+ CategoryInfo          : OperationStopped: (:) [], FormatException
+ FullyQualifiedErrorId : One of the identified items was in an invalid
format.
```

## <a name="resulting-error"></a>결과 오류

Throw 키워드는 ErrorRecord 개체를 생성할 수 있습니다. ErrorRecord 개체의 Exception 속성에는 RuntimeException 개체가 포함 되어 있습니다. ErrorRecord 개체와 RuntimeException 개체의 나머지 부분은 Throw 키워드가 throw 하는 개체에 따라 달라 집니다.

RunTimeException 개체가 ErrorRecord 개체에 래핑되어 ErrorRecord 개체가 자동으로 $Error 자동으로 저장 됩니다.

## <a name="using-throw-to-create-a-mandatory-parameter"></a>THROW를 사용 하 여 필수 매개 변수 만들기

Throw 키워드를 사용 하 여 함수 매개 변수를 필수로 만들 수 있습니다.

매개 변수 키워드의 필수 매개 변수를 사용 하는 대신 사용할 수 있습니다. 필수 매개 변수를 사용 하는 경우 시스템은 사용자에 게 필요한 매개 변수 값을 묻는 메시지를 표시 합니다. Throw 키워드를 사용 하는 경우 명령에서 오류 레코드를 중지 하 고 표시 합니다.

예를 들어 매개 변수 하위 식의 Throw 키워드는 함수에서 Path 매개 변수를 필수 매개 변수로 만듭니다.

이 경우 Throw 키워드는 메시지 문자열을 throw 하지만 Path 매개 변수가 지정 되지 않은 경우에는 종료 오류를 생성 하는 Throw 키워드가 존재 합니다. Throw 뒤에 오는 식은 선택 사항입니다.

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a>참고 항목

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
