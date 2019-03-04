---
title: Cmdlet 매개 변수 유형의 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: 59921a92661482b8d518b82f490c9879643543bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859869"
---
# <a name="types-of-cmdlet-parameters"></a>Cmdlet 매개 변수 형식

이 항목에서는 다양 한 cmdlet에서 선언할 수 있는 매개 변수를 설명 합니다. Cmdlet 매개 변수 스위치 매개 변수 또는 위치, 명명 된, 필수 (선택 사항)을 수 있습니다.

## <a name="positional-and-named-parameters"></a>위치 인수와 명명 된 매개 변수

모든 cmdlet 매개 변수는 이름이 나 위치 매개 변수입니다. 명명된 된 매개 변수는 cmdlet을 호출 하는 경우 매개 변수 이름 및 인수를 입력 해야 합니다. 위치 매개 변수는 상대 순서로 인수를 입력할만 필요 합니다. 그런 다음 시스템은 첫 번째 위치 매개 변수를 명명 되지 않은 첫 번째 인수를 매핑합니다. 시스템은 두 번째 명명 되지 않은 두 번째 인수를 매핑합니다 명명 되지 않은 매개 변수를 등에입니다. 기본적으로 모든 cmdlet 매개 변수는 명명 된 매개 변수입니다.

명명된 된 매개 변수를 정의 하려면 생략 합니다 `Position` 키워드를 **매개 변수** 특성 선언에 다음 매개 변수 선언에 표시 된 대로 합니다.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

위치 매개 변수를 정의 하려면 추가 `Position` 매개 변수에 키워드 특성 선언 하 고 위치를 지정 합니다. 다음 샘플에서는 `UserName` 매개 변수가 0의 위치를 사용 하 여 위치 매개 변수로 선언 됩니다. 즉, 호출의 첫 번째 인수는이 매개 변수를 자동으로 바인딩할 수 있습니다.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> 좋은 cmdlet 설계 위치 매개 변수로 사용자는 cmdlet를 실행할 때 매개 변수 이름을 입력 하지 않아도 되도록 가장 많이 사용 되는 매개 변수를 선언 하는 것이 좋습니다.

위치 인수와 명명 된 매개 변수는 단일 인수 또는 쉼표로 구분 된 여러 인수를 수락 합니다. 여러 인수는 매개 변수가 문자열 배열과 같은 컬렉션을 허용 하는 경우에 허용 됩니다. 동일한 cmdlet에서 위치 인수와 명명 된 매개 변수를 혼합할 수 있습니다. 시스템 명명 된 인수를 먼저 검색 하 고에 나머지 매핑하려고 명명 되지 않은 인수가 위치 매개 변수를이 예제의 경우.

다음 명령은 단일 및 여러 인수 매개 변수를 지정할 수 있는 다양 한 방법을 표시 합니다 `Get-Command` cmdlet. 마지막 두 샘플에서 있음을 **-이름** 때문에 지정할 필요가 없습니다를 `Name` 매개 변수를 위치 매개 변수로 정의 됩니다.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>필수 및 선택적 매개 변수

또한 필수 또는 선택적 매개 변수로 cmdlet 매개 변수를 정의할 수 있습니다. (필수 매개 변수는 Windows PowerShell 런타임에 cmdlet을 호출 하기 전에 지정 되어야 합니다.)  기본적으로 매개 변수를 선택적으로 정의 됩니다.

필수 매개 변수를 정의 하려면 다음을 추가 합니다 `Mandatory` 특성 선언 하 고 설정 하는 매개 변수에 키워드 `true`다음 매개 변수 선언에 나와 있는 것 처럼 합니다.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

선택적 매개 변수를 정의 하려면 생략 합니다 `Mandatory` 키워드를 **매개 변수** 특성 선언에 다음 매개 변수 선언에 표시 된 대로 합니다.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>스위치 매개 변수

Windows PowerShell은 제공 된 [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) 값을 갖는 매개 변수를 정의할 수 있는 형식으로 자동 설정 됩니다 `false` 경우 cmdlet 매개 변수를 지정 하지 않으면 호출 됩니다. 가능 하면 부울 매개 변수 대신 스위치 매개 변수를 사용 합니다.

다음 샘플을 고려해보세요. 기본적으로 몇 가지 Windows PowerShell cmdlet에 출력 개체를 파이프라인으로 전달 하지 마십시오. 그러나 이러한 cmdlet에는 `PassThru` 기본 동작을 재정의 하는 매개 변수를 전환 합니다. 경우는 `PassThru` 파이프라인에 출력 개체를 반환 하는 cmdlet, 이러한 cmdlet이 호출 될 때 매개 변수를 지정 합니다.

매개 변수가 기본 값을 가질 경우 `true` 호출에서 매개 변수를 지정 하지 않으면, 매개 변수의 의미를 반전 고려해 야 합니다. 샘플의 경우, 매개 변수 속성의 부울 값으로 설정 하는 대신 `true`를 속성으로 선언 된 [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) 형식과 매개변수의기본값을설정합니다`false`.

스위치 매개 변수를 정의 하려면 속성으로 선언 된 [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) 다음 샘플에 표시 된 것과 같이 입력 합니다.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

지정 된 경우에 매개 변수를 작업할 cmdlet 입력 처리 메서드 중 하나에서 다음 구조를 사용 합니다.

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
