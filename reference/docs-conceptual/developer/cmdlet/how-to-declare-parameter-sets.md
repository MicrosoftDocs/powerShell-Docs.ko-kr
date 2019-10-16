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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365612"
---
# <a name="how-to-declare-parameter-sets"></a>매개 변수 집합을 선언하는 방법

이 예에서는 cmdlet에 대 한 매개 변수를 선언할 때 두 개의 매개 변수 집합을 정의 하는 방법을 보여 줍니다. 각 매개 변수 집합에는 고유한 매개 변수 및 두 매개 변수 집합에서 사용 하는 공유 매개 변수가 모두 있습니다. 기본 매개 변수 집합을 지정 하는 방법을 비롯 하 여 매개 변수 집합에 대 한 자세한 내용은 [Cmdlet 매개 변수 집합](./cmdlet-parameter-sets.md)을 참조 하세요.

> [!IMPORTANT]
> 가능 하면 매개 변수 집합의 unique 매개 변수를 필수 매개 변수로 정의 합니다. 그러나 매개 변수를 지정 하지 않고 cmdlet을 실행 하려는 경우에는 unique 매개 변수를 선택적 매개 변수로 사용할 수 있습니다. 예를 들어 `Get-Command` cmdlet의 unique 매개 변수는 선택 사항입니다.

## <a name="how-to-define-two-parameter-sets"></a>두 매개 변수 집합을 정의 하는 방법

1. 첫 번째 매개 변수 집합의 unique 매개 변수에 대 한 매개 변수 특성에 `ParameterSet` 키워드를 추가 합니다.

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

2. 두 번째 매개 변수 집합의 고유 매개 변수에 대 한 매개 변수 특성에 `ParameterSet` 키워드를 추가 합니다.

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

3. 두 매개 변수 집합에 속하는 매개 변수의 경우 각 매개 변수 집합에 대 한 매개 변수 특성을 추가한 다음 각 집합에 `ParameterSet` 키워드를 추가 합니다. 각 매개 변수 특성에서 매개 변수를 정의 하는 방법을 지정할 수 있습니다. 매개 변수는 한 집합에서 선택 사항이 며 다른 집합에서 필수 매개 변수가 될 수 있습니다.

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
