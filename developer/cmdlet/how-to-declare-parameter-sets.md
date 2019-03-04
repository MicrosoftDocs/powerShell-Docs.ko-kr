---
title: 매개 변수 집합을 선언 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859699"
---
# <a name="how-to-declare-parameter-sets"></a>매개 변수 집합을 선언하는 방법

이 예제에서는 cmdlet에 대 한 매개 변수를 선언 하는 경우 두 매개 변수 집합을 정의 하는 방법을 보여 줍니다. 각 매개 변수 집합에는 고유한 매개 변수 및 매개 변수 집합 모두에서 사용 되는 공유 매개 변수 모두에 있습니다. 매개 변수 집합을 기본 매개 변수 집합을 지정 하는 방법을 포함 하는 방법에 대 한 자세한 내용은 참조 [Cmdlet 매개 변수 설정](./cmdlet-parameter-sets.md)합니다.

> [!IMPORTANT]
> 가능 하면 필수 매개 변수로 설정할 매개 변수의 고유한 매개 변수를 정의 합니다. 그러나 매개 변수를 지정 하지 않고 실행 하려면 cmdlet을 사용 하도록 하려는 경우 고유한 매개 변수는 선택적 매개 변수를 수 있습니다. 예를 들어, 고유한 매개 변수는 `Get-Command` cmdlet은 선택 사항입니다.

## <a name="how-to-define-two-parameter-sets"></a>두 매개 변수 집합을 정의 하는 방법

1. 추가 된 `ParameterSet` 키워드를 첫 번째 매개 변수 집합의 고유한 매개 변수, 매개 변수 속성.

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

2. 추가 된 `ParameterSet` 키워드를 두 번째 매개 변수 집합의 고유한 매개 변수, 매개 변수 속성.

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

3. 두 매개 변수 집합에 속하는 매개 변수에 각 매개 변수 집합에 대 한 매개 변수 특성을 추가한 다음 추가 `ParameterSet` 각 집합에는 키워드입니다. 각 매개 변수 특성의 해당 매개 변수를 정의 하는 방법을 지정할 수 있습니다. 하나의 집합에는 선택 사항이 며 다른 필수 매개 변수 수 있습니다.

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
