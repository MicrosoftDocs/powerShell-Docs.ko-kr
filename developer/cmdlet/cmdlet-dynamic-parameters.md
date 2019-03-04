---
title: Cmdlet은 동적 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853809"
---
# <a name="cmdlet-dynamic-parameters"></a>Cmdlet 동적 매개 변수

Cmdlet는 경우와 같이 다른 매개 변수 인수의 특정 값을 특수 한 상황에서 사용자에 게 사용할 수 있는 매개 변수를 정의할 수 있습니다. 이러한 매개 변수는 런타임에 추가 되 고 이라고 *동적 매개 변수* 있으므로 필요할 때에 추가 됩니다. 예를 들어, 특정 스위치 매개 변수를 지정 하는 경우에 여러 매개 변수를 추가 하는 cmdlet를 디자인할 수 있습니다.

> [!NOTE]
> 공급자 및 Windows PowerShell 함수는 동적 매개 변수를 정의할 수도 있습니다.

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Windows PowerShell Cmdlet에서 동적 매개 변수

Windows PowerShell 공급자 cmdlet의 여러 동적 매개 변수를 사용합니다. 예를 들어, 합니다 `Get-Item` 및 `Get-ChildItem` cmdlet 추가 `CodeSigningCert` 런타임에 매개 변수 때를 `Path` cmdlet의 매개 변수는 인증서 공급자 경로 지정 합니다. 경우는 `Path` 다른 공급자에 대 한 경로 지정 하는 cmdlet의 매개 변수는 `CodeSigningCert` 매개 변수를 사용할 수 없습니다.

다음 예제에서는 표시 하는 방법을 `CodeSigningCert` 매개 변수는 런타임에 추가 됩니다 때를 `Get-Item` cmdlet을 실행 합니다.

첫 번째 예에서는 Windows PowerShell 런타임이 매개 변수를 추가 및 cmdlet은 성공 합니다.

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

두 번째 예제에서는 파일 시스템 드라이브를 지정 하 고 오류가 반환 됩니다. 오류 메시지를 표시 하는 `CodeSigningCert` 매개 변수를 찾을 수 없습니다.

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>동적 매개 변수에 대 한 지원

동적 매개 변수를 지원 하려면 cmdlet 코드는 다음과 같은 요소를 포함 해야 합니다.

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) 이 인터페이스는 동적 매개 변수를 검색 하는 메서드를 제공 합니다.

예:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) 이 메서드는 동적 매개 변수 정의 포함 하는 개체를 검색 합니다.

예:

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

동적 매개 변수 클래스가이 클래스에 추가할 매개 변수를 정의 합니다. 이 클래스는 각 매개 변수 및 cmdlet에 필요한 모든 선택적 별칭 및 유효성 검사 특성에 대 한 매개 변수 특성을 포함 해야 합니다.

예:

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

동적 매개 변수를 지 원하는 cmdlet의 전체 예제를 참조 하세요 [동적 매개 변수를 선언 하는 방법을](./how-to-declare-dynamic-parameters.md)합니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[동적 매개 변수를 선언 하는 방법](./how-to-declare-dynamic-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
