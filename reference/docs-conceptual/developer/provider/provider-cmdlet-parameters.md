---
ms.date: 09/13/2016
ms.topic: reference
title: 공급자 cmdlet 매개 변수
description: 공급자 cmdlet 매개 변수
ms.openlocfilehash: 6fd340f22202d984b7111c34806e3461a356c670
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92662777"
---
# <a name="provider-cmdlet-parameters"></a>공급자 cmdlet 매개 변수

공급자 cmdlet에는 cmdlet을 지 원하는 모든 공급자에서 사용할 수 있는 정적 매개 변수 집합 뿐만 아니라 사용자가 provider cmdlet의 특정 정적 매개 변수에 대 한 특정 값을 지정할 때 추가 되는 동적 매개 변수도 포함 됩니다.

## <a name="provider-cmdlet-static-parameters"></a>Provider Cmdlet 정적 매개 변수

정적 매개 변수는 Windows PowerShell에 의해 정의 됩니다. 이러한 매개 변수 집합은 Windows PowerShell에서 구현 하 여 모든 공급자에 일관성을 제공 하 고 개발 환경을 간단 하 게 제공 합니다. 이러한 매개 변수의 예로는 `literalPath` `exclude` cmdlet의, 및 `include` 매개 변수가 있습니다 `Get-Item` . 이러한 매개 변수 집합은 공급자와 관련 된 작업을 제공 하기 위해 덮어쓸 수 있습니다. 이러한 매개 변수의 예로는 `Path` `Value` cmdlet의 및 매개 변수가 `Set-Item` 있습니다. 공급자 cmdlet에 대해 덮어쓸 수 있는 매개 변수 목록은 다음과 같습니다.

`Clear-Content` cmdlet `Path` `Clear-Content` [Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 구현 하 여 공급자가 cmdlet의 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

`Clear-Item`cmdlet을 구현 하 여 공급자가 `Path` cmdlet의 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다. `Clear-Item` . [](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) .

`Clear-ItemProperty` cmdlet을 구현 하 여 공급자가 `Path` `Name` cmdlet의 및 매개 변수에 전달 되는 값을 사용 하는 방법을 정의할 수 `Clear-ItemProperty` [있습니다.](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) .

`Copy-Item`cmdlet `Path` `Destination` ContainerCmdletProvider 메서드를 구현 하 여 공급자가 cmdlet의, 및 `Recurse` 매개 변수에 `Copy-Item` [](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

Get-ChildItems cmdlet을 사용 하 여 공급자가 cmdlet의 및 매개 변수에 전달 되는 값을 사용 하는 방법을 정의할 수 있습니다. `Path` `Recurse` `Get-ChildItem` [Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 및 [Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 메서드를 구현 합니다.

`Get-Content`cmdlet Icontentcmdletprovider을 구현 하 여 공급자가 `Path` cmdlet의 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다. `Get-Content` [](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)

`Get-Item` cmdlet `Path` `Get-Item` [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드를 구현 하 여 공급자가 cmdlet의 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

`Get-ItemProperty`cmdlet을 구현 하 여 공급자가 `Path` `Name` cmdlet의 및 매개 변수에 전달 되 `Get-ItemProperty` [](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 는 값을 사용 하는 방법을 정의할 수 있습니다.

`Invoke-Item` cmdlet `Path` `Invoke-Item` [Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 메서드를 구현 하 여 공급자가 cmdlet의 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

`Move-Item` cmdlet `Path` `Destination` `Move-Item` [Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 구현 하 여 공급자가 cmdlet의 및 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

`New-Item` cmdlet `Path` `ItemType` `Value` `New-Item` [Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드를 구현 하 여 공급자가 cmdlet의, 및 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

`New-ItemProperty` cmdlet `Path` `Name` `PropertyType` `Value` `New-ItemProperty` [Registryprovider *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) 메서드를 구현 하 여 공급자가 cmdlet의,, 및 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

`Remove-Item` 공급자가 cmdlet의 및 매개 변수에 전달 되는 값을 사용 하는 방법을 정의할 수 있습니다. `Path` `Recurse` `Remove-Item` [Containercmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드를 구현 합니다.

`Remove-ItemProperty` 공급자가 cmdlet의 및 매개 변수에 전달 되는 값을 사용 하는 방법을 정의할 수 있습니다. `Path` `Name` `Remove-ItemProperty` [Idynamicpropertycmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) 메서드를 구현 합니다.

`Rename-Item` cmdlet `Path` `NewName` `Rename-Item` [Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드를 구현 하 여 공급자가 cmdlet의 및 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

`Rename-ItemProperty` 공급자가 `Path` `NewName` `Name` `Rename-ItemProperty` [Idynamicpropertycmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) 메서드를 구현 하 여 cmdlet의, 및 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

`Set-Content`cmdlet Icontentcmdletprovider을 구현 하 여 공급자가 `Path` cmdlet의 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다. `Set-Content` [](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)

`Set-Item` cmdlet `Path` `Value` `Set-Item` [Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 구현 하 여 공급자가 cmdlet의 및 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

`Set-ItemProperty`cmdlet을 구현 하 여 공급자가 `Path` `Value` cmdlet의 및 매개 변수에 전달 되 `Set-Item` [](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 는 값을 사용 하는 방법을 정의할 수 있습니다.

`Test-Path` cmdlet `Path` `Test-Path` [Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 메서드를 구현 하 여 공급자가 cmdlet의 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

또한 이러한 매개 변수의 특성 (예: 선택 사항 또는 필수)을 지정할 수 없으며, 이러한 매개 변수를 별칭에 제공 하거나 유효성 검사 특성을 지정할 수도 없습니다. 반면 특성과 같은 특성을 사용 하 여 독립 실행형 cmdlet에 매개 변수 특성을 지정할 수 있습니다 `Parameters` .

## <a name="provider-cmdlet-dynamic-parameters"></a>Provider Cmdlet 동적 매개 변수

Cmdlet 공급자의 동적 매개 변수는 독립 실행형 cmdlet에 대 한 동적 공급자와 유사 합니다. 두 경우 모두 사용자가 매개 변수 등의 기본 매개 변수 중 하나에 대해 특정 값을 지정 하면 cmdlet에 매개 변수가 추가 됩니다 `path` . 그러나 모든 정적 매개 변수를 사용 하 여 동적 매개 변수 추가를 트리거할 수 있는 것은 아닙니다. 동적 매개 변수에 대 한 자세한 내용은 [공급자 Cmdlet 동적 매개 변수](./provider-cmdlet-dynamic-parameters.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[Provider Cmdlet 동적 매개 변수](./provider-cmdlet-dynamic-parameters.md)

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)
