---
title: 공급자 cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080954"
---
# <a name="provider-cmdlets"></a>공급자 cmdlet

사용자 데이터 저장소를 관리 하기 위해 실행할 수 있는 cmdlet 공급자 cmdlet으로 참조 됩니다. 이러한 cmdlet을 지원 하려면 기본 공급자 클래스 및 인터페이스에서 정의 된 메서드 중 일부를 덮어쓸 수 해야 합니다.

## <a name="provider-cmdlets"></a>공급자 Cmdlet

사용자가 실행할 수 있는 공급자 cmdlet은 다음과 같습니다.

### <a name="psdrive-cmdlets"></a>PSDrive cmdlet

- `Get-PSDrive`: 이 cmdlet은 현재 세션의 Windows PowerShell 드라이브를 반환 합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.

- `New-PSDrive`: 이 cmdlet에는 사용자가 데이터 저장소에 액세스 하려면 Windows PowerShell 드라이브를 만들 수 있도록 합니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 고 [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 메서드.

- `Remove-PSDrive`: 이 cmdlet은 사용자를 데이터 저장소에 액세스 하는 Windows PowerShell 드라이브를 제거할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드.

### <a name="item-cmdlets"></a>Item cmdlet

- `Clear-Item`: 이 cmdlet은 사용자를 데이터 저장소에서 항목의 값을 제거할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) 고 [ System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 메서드.

- `Copy-Item`: 이 cmdlet을 사용 하면 다른 한 위치에서 항목을 복사할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 고 [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 메서드.

- `Get-Item`: 이 cmdlet는 데이터 저장소에서 데이터를 검색할 수가 있도록 합니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 고 [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 메서드.

- `Get-ChildItem`: 이 cmdlet은 부모 항목의 자식 항목을 검색할 수가 있도록 합니다. 이 cmdlet을 지원 하려면 다음 메서드를 덮어써서:

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: 이 cmdlet을 사용 하면 항목으로 지정 된 기본 작업을 수행할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 고 [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 메서드.

- `Move-Item`: 이 cmdlet에는 사용자 항목을 한 위치에서 다른 위치로 이동할 수 있도록 합니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 고 [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)의메서드.

- `New-ItemProperty`: 이 cmdlet에는 사용자가 데이터 저장소에 새 항목을 만들 수 있도록 합니다.

- `Remove-Item`: 이 cmdlet은 사용자를 데이터 저장소에서 항목을 제거할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 고 [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 메서드.

- `Rename-Item`: 이 cmdlet을 사용 하면 데이터 저장소의 항목 이름을 바꾸려면 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 고 [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 메서드.

- `Set-Item`: 이 cmdlet은 사용자를 데이터 저장소에 있는 항목의 값을 업데이트할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 고 [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 메서드.

### <a name="item-content-cmdlets"></a>Item 콘텐츠 cmdlet

- `Add-Content`: 이 cmdlet은 사용자를를 항목에 콘텐츠를 추가할 수 있습니다.

- `Clear-Content`: 이 cmdlet을 사용 하면 콘텐츠를 삭제 하려면 항목에서 항목을 삭제 하지 않고 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 고 [ System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 메서드.

- `Get-Content`: 이 cmdlet에는 항목의 콘텐츠를 검색할 수가 있도록 합니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 고 [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 메서드. 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 메서드가 반환 되는 [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) 정의 하는 인터페이스 콘텐츠를 읽기 위해 사용 되는 메서드.

- `Set-Content`: 이 cmdlet 사용 하면 항목의 콘텐츠를 업데이트 합니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 고 [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 메서드. 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 메서드가 반환 되는 [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) 정의 하는 인터페이스 콘텐츠를 쓰는 데 메서드입니다.

### <a name="item-property-cmdlets"></a>Item 속성 cmdlet

- `Clear-ItemProperty`: 이 cmdlet은 사용자를 속성의 값을 삭제할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 고 [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 메서드.

- `Copy-ItemProperty`: 이 cmdlet은 사용자를 속성 및 해당 값을 한 위치에서 다른 위치로 복사할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) 고 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) 메서드.

- `Get-ItemProperty`: 이 cmdlet은 항목의 속성을 가져옵니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 고 [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 메서드.

- `Move-ItemProperty`: 이 cmdlet에는 다른 위치로 속성 및 해당 값을 이동할 수가 있도록 합니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) 고 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) 메서드.

- `New-ItemProperty`: 이 cmdlet은 새 속성을 만들고 해당 값을 설정 하는 사용자를 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) 고 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) 메서드.

- `Remove-ItemProperty`: 이 cmdlet은 속성 및 해당 값을 삭제할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) 고 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) 메서드.

- `Rename-ItemProperty`: 이 cmdlet을 사용 하면 속성의 이름을 변경할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) 고 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) 메서드.

- `Set-ItemProperty`: 이 cmdlet을 사용 하면 항목의 속성을 업데이트할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 고 [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) 메서드.

### <a name="location-cmdlets"></a>Location cmdlet

- `Get-Location`: 현재 작업 위치에 대 한 정보를 검색합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.

- `Pop-Location`: 이 cmdlet은 가장 최근에 스택에 밀어 넣은 위치로 현재 위치를 변경 합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.

- `Push-Location`: 이 cmdlet의 위치 ("스택")의 목록 맨 위에 현재 위치를 추가합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.

- `Set-Location`: 이 cmdlet는 지정된 된 위치에 현재 작업 위치를 설정합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.

### <a name="path-cmdlets"></a>Path cmdlet

- `Join-Path`: 이 cmdlet을 사용 하면 내부 공급자 경로를 만들 부모 및 자식 경로 세그먼트를 결합할 수 있습니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드.

- `Convert-Path`: 이 cmdlet은 Windows PowerShell 경로에서 Windows PowerShell 공급자 경로로 경로 변환합니다.

- `Split-Path`: 경로의 지정된 일부를 반환합니다.

- `Resolve-Path`: 경로에서 와일드카드 문자를 확인하고 경로 내용을 표시합니다.

- `Test-Path`: 이 cmdlet은 경로의 모든 요소가 있는지 확인 합니다. 이 cmdlet을 지원 하려면 덮어쓰기 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 고 [ System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) 메서드.

### <a name="psprovider-cmdlets"></a>PSProvider cmdlet

- `Get-PSProvider`: 이 cmdlet은 세션에서 사용할 수 있는 공급자에 대 한 정보를 반환합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.