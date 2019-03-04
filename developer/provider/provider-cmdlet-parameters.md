---
title: 공급자 cmdlet 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: d0fb81ee1ca1f80e216c021e1bd64771b8de4dc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860119"
---
# <a name="provider-cmdlet-parameters"></a>공급자 cmdlet 매개 변수

공급자 cmdlet은 cmdlet을 지 원하는 모든 공급자를 사용할 수 있는 정적 매개 변수, 사용자는 특정 공급자 cmdlet의 특정 정적 매개 변수 값을 지정 하는 경우 추가 되는 동적으로 매개 변수 집합이 함께 제공 됩니다.

## <a name="provider-cmdlet-static-parameters"></a>공급자 Cmdlet 정적 매개 변수

정적 매개 변수는 Windows PowerShell에서 정의 됩니다. 다양 한 이러한 매개 변수는 모든 공급자 간에 일관성을 제공 하 고 간단한 개발 환경을 제공 하기 위해 Windows PowerShell에서 구현 됩니다. 이러한 매개 변수의 예로 `literalPath`, `exclude`, 및 `include` 의 매개 변수는 `Get-Item` cmdlet. 공급자와 관련 된 작업을 제공 하도록이 매개 변수 중 더 작은 집합을 덮어쓸 수 있습니다. 이러한 매개 변수의 예로 `Path` 하 고 `Value` 의 매개 변수는 `Set-Item` cmdlet. 다음은 공급자 cmdlet에 대 한 덮어쓸 수 있는 매개 변수의 목록입니다.

`Clear-Content` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Clear-Content` 구현 하 여 cmdlet는 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)메서드.

`Clear-Item` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Clear-Item` 구현 하 여 cmdlet의 [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) 메서드입니다.

`Clear-ItemProperty` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다는 `Path` 하 고 `Name` 의 매개 변수를 `Clear-ItemProperty` 구현 하 여 cmdlet를 [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 메서드.

`Copy-Item` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다 합니다 `Path`, `Destination`, 및 `Recurse` 의 매개 변수를 `Copy-Item` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 메서드.

Get-ChildItems cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다는 `Path` 및 `Recures` 의 매개 변수를 `Get-ChildItem` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 하 고 [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 메서드.

`Get-Content` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Get-Content` 구현 하 여 cmdlet는 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 메서드.

`Get-Item` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Get-Item` 구현 하 여 cmdlet는 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드.

`Get-ItemProperty` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다는 `Path` 하 고 `Name` 의 매개 변수를 `Get-ItemProperty` 구현 하 여 cmdlet를 [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 메서드.

`Invoke-Item` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Invoke-Item` 구현 하 여 cmdlet는 [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)메서드.

`Move-Item` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다는 `Path` 하 고 `Destination` 의 매개 변수를 `Move-Item` 구현 하 여 cmdlet를 [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드.

`New-Item` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다 합니다 `Path`, `ItemType`, 및 `Value` 의 매개 변수를 `New-Item` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드.

`New-ItemProperty` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다 합니다 `Path`, `Name`, `PropertyType`, 및 `Value` 의 매개 변수는 `New-ItemProperty` 구현 하 여 cmdlet는 [ Microsoft.Powershell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) 메서드.

`Remove-Item` 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다는 `Path` 하 고 `Recurse` 의 매개 변수를 `Remove-Item` 구현 하 여 cmdlet를 [System.Management.Automation.Provider.Containercmdletprovider.Removeitem* ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드.

`Remove-ItemProperty` 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다는 `Path` 하 고 `Name` 의 매개 변수를 `Remove-ItemProperty` 구현 하 여 cmdlet를 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) 메서드.

`Rename-Item` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다는 `Path` 하 고 `NewName` 의 매개 변수를 `Rename-Item` 구현 하 여 cmdlet를 [ System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드.

`Rename-ItemProperty` 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다 합니다 `Path`, `NewName`, 및 `Name` 의 매개 변수를 `Rename-ItemProperty` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) 메서드.

`Set-Content` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Set-Content` 구현 하 여 cmdlet는 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 메서드.

`Set-Item` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다는 `Path` 하 고 `Value` 의 매개 변수를 `Set-Item` 구현 하 여 cmdlet를 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem* ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드.

`Set-ItemProperty` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다는 `Path` 하 고 `Value` 의 매개 변수를 `Set-Item` 구현 하 여 cmdlet를 [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 메서드.

`Test-Path` cmdlet 공급자에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Test-Path` 구현 하 여 cmdlet는 [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)메서드.

또한 특성은 선택적 또는 필요 등 이러한 매개 변수를 지정할 수 없습니다 나 수 있습니다 이러한 매개 변수는 별칭을 지정 또는 유효성 검사 특성 중 하나를 지정 합니다. 와 같은 특성을 사용 하 여 독립 실행형 cmdlet에 매개 변수 특징을 지정할 수는 반대로 `Parameters` 특성입니다.

## <a name="provider-cmdlet-dynamic-parameters"></a>공급자 cmdlet은 동적 매개 변수

Cmdlet 공급자에 대 한 동적 매개 변수는 독립 실행형 cmdlet에 대 한 동적 공급자와 비슷합니다. 두 경우 모두 매개 변수는 cmdlet에 추가 사용자와 같은 기본 매개 변수 중 하나에 대 한 특정 값을 지정 하는 경우는 `path` 매개 변수입니다. 그러나 정적 매개 변수 중 일부만 사용할 수 동적 매개 변수 추가 트리거할 수 있습니다. 동적 매개 변수에 대 한 자세한 내용은 참조 하십시오 [공급자 Cmdlet 동적 매개 변수](./provider-cmdlet-dynamic-parameters.md)합니다.

## <a name="see-also"></a>참고 항목

[공급자 cmdlet은 동적 매개 변수](./provider-cmdlet-dynamic-parameters.md)

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)