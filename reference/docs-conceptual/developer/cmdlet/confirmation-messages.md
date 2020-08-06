---
title: 확인 메시지 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8f8192f6ed96b1eeb22e3b28ce1366eee8e7c16a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782194"
---
# <a name="confirmation-messages"></a>확인 메시지

다음은 호출 되는 [시스템](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 의 변형에 따라 표시 될 수 있는 다양 한 확인 메시지입니다 .이 메시지 [는를 호출](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 합니다.

> [!IMPORTANT]
> 확인을 요청 하는 방법을 보여 주는 샘플 코드는 확인 [을 요청 하는 방법](./how-to-request-confirmations.md)을 참조 하세요.

## <a name="specifying-the-resource"></a>리소스 지정

변경할 리소스를 지정할 수 있습니다 .이 [작업은 %2 a?를 호출 하 여 변경할 수 있습니다. Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) 메서드. 이 경우 메서드의 매개 변수를 사용 하 여 리소스를 제공 합니다 `target` .이 작업은 Windows PowerShell을 통해 추가 됩니다. 다음 메시지에서 "MyResource" 텍스트는 사용 되는 리소스 이며 작업은 호출을 수행 하는 명령 이름입니다.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

사용자가 다음 예제와 같이 확인 요청에 대해 모두 **예** 또는 예를 선택 **하** 는 경우에는 두 번째 확인 메시지가 표시 되는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하 게 됩니다.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>작업 및 리소스 지정

변경할 리소스와 해당 명령이 수행할 작업 (... n a m a. %2?)을 지정할 수 있습니다. [ Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) 메서드. 이 경우 매개 변수를 사용 하 여 리소스를 제공 하 `target` 고 매개 변수를 사용 하 여 작업을 수행 합니다 `target` . 다음 메시지에서 "MyResource" 라는 텍스트는 수행 되는 리소스 이며 "Myresource"은 수행 되는 작업입니다.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

사용자가 이전 메시지에 대해 **모두** **예** 또는 예를 선택 하는 경우에는 두 번째 확인 메시지가 표시 되는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 합니다.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
