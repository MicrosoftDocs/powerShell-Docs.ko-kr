---
title: Provider cmdlet 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366312"
---
# <a name="provider-cmdlet-parameters"></a>공급자 cmdlet 매개 변수

공급자 cmdlet에는 cmdlet을 지 원하는 모든 공급자에서 사용할 수 있는 정적 매개 변수 집합 뿐만 아니라 사용자가 provider cmdlet의 특정 정적 매개 변수에 대 한 특정 값을 지정할 때 추가 되는 동적 매개 변수도 포함 됩니다.

## <a name="provider-cmdlet-static-parameters"></a>Provider Cmdlet 정적 매개 변수

정적 매개 변수는 Windows PowerShell에 의해 정의 됩니다. 이러한 매개 변수 집합은 Windows PowerShell에서 구현 하 여 모든 공급자에 일관성을 제공 하 고 개발 환경을 간단 하 게 제공 합니다. 이러한 매개 변수의 예로는 `Get-Item` cmdlet의 `literalPath`, `exclude` 및 `include` 매개 변수가 있습니다. 이러한 매개 변수 집합은 공급자와 관련 된 작업을 제공 하기 위해 덮어쓸 수 있습니다. 이러한 매개 변수의 예로는 `Set-Item` cmdlet의 `Path` 및 `Value` 매개 변수가 있습니다. 공급자 cmdlet에 대해 덮어쓸 수 있는 매개 변수 목록은 다음과 같습니다.

@no__t cmdlet [Icontentcmdletprovider Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 구현 하 여 공급자가 `Clear-Content` cmdlet의 `Path` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

@no__t cmdlet은 공급자가 `Clear-Item` cmdlet의 `Path` 매개 변수에 전달 되는 값을 사용 하는 방법을 정의할 수 있습니다. 여기서는 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) 를 구현 합니다.

@no__t cmdlet은 공급자가 `Clear-ItemProperty` cmdlet의 `Path` 및 `Name` 매개 변수에 전달 되는 값을 사용 하는 방법을 정의할 수 있습니다. 여기서는 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 를 구현 하 여.

@no__t cmdlet [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 을 구현 하 여 공급자가 `Copy-Item` cmdlet의 `Path`, `Destination` 및 `Recurse` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다. 방법이.

[Containercmdletprovider Cmdlet Getchilditems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 를 구현 하 여 공급자가 `Get-ChildItem` cmdlet의 `Path` 및 `Recurse` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다. 및 [Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 메서드를 제공 합니다.

@no__t cmdlet [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 을 구현 하 여 공급자가 `Get-Content` cmdlet의 `Path` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

@no__t cmdlet [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드를 구현 하 여 공급자가 `Get-Item` cmdlet의 `Path` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

@no__t cmdlet은 공급자가 `Get-ItemProperty` cmdlet의 `Path` 및 `Name` 매개 변수에 전달 되는 값을 사용 하는 방법을 정의할 수 있습니다. 여기서는 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 를 구현 합니다.

@no__t cmdlet [Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 메서드를 구현 하 여 공급자가 `Invoke-Item` cmdlet의 `Path` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

@no__t cmdlet [Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 구현 하 여 공급자가 `Move-Item` cmdlet의 `Path` 및 `Destination` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

@no__t cmdlet Newitem를 구현 하 여 공급자가 `New-Item` cmdlet의 `Path`, `ItemType` 및 `Value` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다. [Containercmdletprovider *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 방법이.

@no__t cmdlet [Registryprovider 속성](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) 을 구현 하 여 공급자가 @no__t cmdlet의 `Path`, `Name`, `PropertyType` 및 `Value` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다. 방법이.

`Remove-Item` [Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드를 구현 하 여 공급자가 `Remove-Item` cmdlet의 `Path` 및 `Recurse` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

`Remove-ItemProperty`은 공급자가 `Remove-ItemProperty` cmdlet의 `Path` 및 `Name` 매개 변수에 전달 되는 값을 사용 하는 방법을 정의할 수 있습니다. [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) 을 구현 합니다. 방법이.

@no__t cmdlet [Containercmdletprovider Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드를 구현 하 여 공급자가 `Rename-Item` cmdlet의 `Path` 및 `NewName` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

`Rename-ItemProperty` Renameproperty를 구현 하 여 공급자가 `Rename-ItemProperty` cmdlet의 `Path`, `NewName` 및 `Name` 매개 변수에 전달 되는 값을 사용 하는 방법을 정의할 수 있습니다. [Idynamicpropertycmdletprovider * ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)메서드.

@no__t cmdlet [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 을 구현 하 여 공급자가 `Set-Content` cmdlet의 `Path` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

@no__t cmdlet [Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 구현 하 여 공급자가 `Set-Item` cmdlet의 `Path` 및 `Value` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

@no__t cmdlet은 공급자가 `Set-Item` cmdlet의 `Path` 및 `Value` 매개 변수에 전달 되는 값을 사용 하는 방법을 정의할 수 있습니다. 여기서는 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 를 구현 합니다.

@no__t cmdlet [Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 메서드를 구현 하 여 공급자가 `Test-Path` cmdlet의 `Path` 매개 변수에 전달 된 값을 사용 하는 방법을 정의할 수 있습니다.

또한 이러한 매개 변수의 특성 (예: 선택 사항 또는 필수)을 지정할 수 없으며, 이러한 매개 변수를 별칭에 제공 하거나 유효성 검사 특성을 지정할 수도 없습니다. 반면에 `Parameters` 특성과 같은 특성을 사용 하 여 독립 실행형 cmdlet에 매개 변수 특성을 지정할 수 있습니다.

## <a name="provider-cmdlet-dynamic-parameters"></a>Provider Cmdlet 동적 매개 변수

Cmdlet 공급자의 동적 매개 변수는 독립 실행형 cmdlet에 대 한 동적 공급자와 유사 합니다. 두 경우 모두 사용자가 기본 매개 변수 중 하나에 대 한 특정 값 (예: `path` 매개 변수)을 지정할 때 매개 변수가 cmdlet에 추가 됩니다. 그러나 모든 정적 매개 변수를 사용 하 여 동적 매개 변수 추가를 트리거할 수 있는 것은 아닙니다. 동적 매개 변수에 대 한 자세한 내용은 [공급자 Cmdlet 동적 매개 변수](./provider-cmdlet-dynamic-parameters.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[Provider Cmdlet 동적 매개 변수](./provider-cmdlet-dynamic-parameters.md)

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)