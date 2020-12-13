---
ms.date: 09/13/2016
ms.topic: reference
title: 매개 변수 집합을 선언하는 방법
description: 매개 변수 집합을 선언하는 방법
ms.openlocfilehash: bd4d504a9fe6c7f7626901c49bc08851244f0995
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667065"
---
# <a name="how-to-declare-parameter-sets"></a>매개 변수 집합을 선언하는 방법

이 예에서는 cmdlet에 대 한 매개 변수를 선언할 때 두 개의 매개 변수 집합을 정의 하는 방법을 보여 줍니다. 각 매개 변수 집합에는 고유한 매개 변수 및 두 매개 변수 집합에서 사용 하는 공유 매개 변수가 모두 있습니다. 기본 매개 변수 집합을 지정 하는 방법을 비롯 하 여 매개 변수 집합에 대 한 자세한 내용은 [Cmdlet 매개 변수 집합](./cmdlet-parameter-sets.md)을 참조 하세요.

> [!IMPORTANT]
> 가능 하면 매개 변수 집합의 unique 매개 변수를 필수 매개 변수로 정의 합니다. 그러나 매개 변수를 지정 하지 않고 cmdlet을 실행 하려는 경우에는 unique 매개 변수를 선택적 매개 변수로 사용할 수 있습니다. 예를 들어 cmdlet의 unique 매개 변수는 `Get-Command` 선택 사항입니다.

## <a name="how-to-define-two-parameter-sets"></a>두 매개 변수 집합을 정의 하는 방법

1. `ParameterSet`첫 번째 매개 변수 집합의 고유 매개 변수에 대 한 매개 변수 특성에 키워드를 추가 합니다.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. `ParameterSet`두 번째 매개 변수 집합의 고유 매개 변수에 대 한 매개 변수 특성에 키워드를 추가 합니다.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. 두 매개 변수 집합에 속하는 매개 변수의 경우 각 매개 변수 집합에 대 한 매개 변수 특성을 추가한 다음 `ParameterSet` 각 집합에 키워드를 추가 합니다. 각 매개 변수 특성에서 매개 변수를 정의 하는 방법을 지정할 수 있습니다. 매개 변수는 한 집합에서 선택 사항이 며 다른 집합에서 필수 매개 변수가 될 수 있습니다.

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>참고 항목

[Cmdlet 매개 변수 집합](./cmdlet-parameter-sets.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
