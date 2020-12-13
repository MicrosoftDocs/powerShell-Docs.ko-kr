---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 동적 매개 변수
description: Cmdlet 동적 매개 변수
ms.openlocfilehash: b44dda2354e8b689e419c7bf4deefadfc4edcb07
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653428"
---
# <a name="cmdlet-dynamic-parameters"></a>Cmdlet 동적 매개 변수

Cmdlet은 다른 매개 변수의 인수가 특정 값인 경우와 같이 사용자가 특별 한 조건에서 사용할 수 있는 매개 변수를 정의할 수 있습니다. 이러한 매개 변수는 런타임에 추가 되며 필요한 경우에만 추가 되므로 동적 매개 변수 라고 합니다. 예를 들어 특정 스위치 매개 변수가 지정 된 경우에만 여러 매개 변수를 추가 하는 cmdlet을 디자인할 수 있습니다.

> [!NOTE]
> 공급자 및 PowerShell 함수는 동적 매개 변수를 정의할 수도 있습니다.

## <a name="dynamic-parameters-in-powershell-cmdlets"></a>PowerShell cmdlet의 동적 매개 변수

PowerShell은 여러 공급자 cmdlet에서 동적 매개 변수를 사용 합니다. 예를 들어, `Get-Item` 및 `Get-ChildItem` Cmdlet은 **path** 매개 변수에서 **인증서** 공급자 경로를 지정 하는 경우 런타임에 **codesigningcert** 매개 변수를 추가 합니다. **Path** 매개 변수가 다른 공급자의 경로를 지정 하는 경우 **Codesigningcert** 매개 변수를 사용할 수 없습니다.

다음 예에서는를 실행할 때 **Codesigningcert** 매개 변수를 런타임에 추가 하는 방법을 보여 줍니다 `Get-Item` .

이 예에서는 PowerShell 런타임에서 매개 변수를 추가 하 고 cmdlet이 성공 했습니다.

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

이 예제에서는 **파일 시스템** 드라이브를 지정 하 고 오류가 반환 됩니다. 오류 메시지는 **Codesigningcert** 매개 변수를 찾을 수 없음을 나타냅니다.

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>동적 매개 변수 지원

동적 매개 변수를 지원 하려면 다음 요소를 cmdlet 코드에 포함 해야 합니다.

### <a name="interface"></a>인터페이스

[IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters)입니다.
이 인터페이스는 동적 매개 변수를 검색 하는 메서드를 제공 합니다.

예를 들어:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a>메서드

[IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)
이 메서드는 동적 매개 변수 정의를 포함 하는 개체를 검색 합니다.

예를 들면 다음과 같습니다.

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

### <a name="class"></a>클래스

추가할 동적 매개 변수를 정의 하는 클래스입니다. 이 클래스에는 각 매개 변수에 대 한 **매개 변수** 특성과 cmdlet에 필요한 선택적 **별칭** 및 **유효성 검사** 특성이 포함 되어야 합니다.

예를 들어:

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

동적 매개 변수를 지 원하는 cmdlet의 전체 예제는 [동적 매개 변수를 선언 하는 방법](./how-to-declare-dynamic-parameters.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[IDynamicParameters.](/dotnet/api/System.Management.Automation.IDynamicParameters)

[IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[동적 매개 변수를 선언하는 방법](./how-to-declare-dynamic-parameters.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
