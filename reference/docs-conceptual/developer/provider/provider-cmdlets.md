---
title: 공급자 cmdlet | Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: 24838eeec8e2d59ff3cc549c8659d5afb1c8f92f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771688"
---
# <a name="provider-cmdlets"></a>공급자 cmdlet

사용자가 데이터 저장소를 관리 하기 위해 실행할 수 있는 cmdlet을 공급자 cmdlet 이라고 합니다. 이러한 cmdlet을 지원 하려면 기본 공급자 클래스 및 인터페이스에 의해 정의 된 메서드 중 일부를 덮어써야 합니다.

## <a name="provider-cmdlets"></a>공급자 Cmdlet

사용자가 실행할 수 있는 공급자 cmdlet은 다음과 같습니다.

### <a name="psdrive-cmdlets"></a>PSDrive cmdlet

- `Get-PSDrive`:이 cmdlet은 현재 세션의 Windows PowerShell 드라이브를 반환 합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.

- `New-PSDrive`:이 cmdlet을 사용 하면 사용자가 Windows PowerShell 드라이브를 만들어 데이터 저장소에 액세스할 수 있습니다. 이 cmdlet을 지원 하려면 [Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 및 [Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 메서드를 덮어쓰십시오... d m d. n a m.. n a m.

- `Remove-PSDrive`:이 cmdlet을 사용 하면 사용자가 데이터 저장소에 액세스 하는 Windows PowerShell 드라이브를 제거할 수 있습니다. 이 cmdlet을 지원 하려면 System.object를 덮어씁니다. [Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 덮어씁니다.

### <a name="item-cmdlets"></a>항목 cmdlet

- `Clear-Item`:이 cmdlet을 사용 하면 사용자가 데이터 저장소에 있는 항목의 값을 제거할 수 있습니다. 이 cmdlet을 지원 하려면 [system.web](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) . m a n a m a. m a g. m a m a. m [a g.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)

- `Copy-Item`:이 cmdlet을 사용 하면 사용자가 한 위치에서 다른 위치로 항목을 복사할 수 있습니다. 이 cmdlet을 지원 하려면 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 및 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .. m a n a m e. m a n a m e.

- `Get-Item`:이 cmdlet을 사용 하면 사용자가 데이터 저장소에서 데이터를 검색할 수 있습니다. 이 cmdlet을 지원 하려면 [Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 및 [system.web](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) . n a m a. i n g. i n g. i n g.

- `Get-ChildItem`:이 cmdlet을 통해 사용자는 부모 항목의 자식 항목을 검색할 수 있습니다. 이 cmdlet을 지원 하려면 다음 메서드를 덮어씁니다.

  - [Containercmdletprovider입니다. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [Containercmdletprovider입니다. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [Containercmdletprovider입니다. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [Containercmdletprovider입니다. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`:이 cmdlet을 사용 하면 사용자가 항목에 지정 된 기본 작업을 수행할 수 있습니다. 이 cmdlet을 지원 하려면 [Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 및 Invokedefaultaction 메서드를 덮어쓰십시오.. n a m.. i n [g](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) . m a.

- `Move-Item`:이 cmdlet을 사용 하면 사용자가 한 위치에서 다른 위치로 항목을 이동할 수 있습니다. 이 cmdlet을 지원 하려면 [Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 및 system.webserver를 덮어씁니다. [Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s 메서드를 (를) 덮어씁니다 .이 경우.

- `New-ItemProperty`:이 cmdlet을 사용 하면 사용자가 데이터 저장소에 새 항목을 만들 수 있습니다.

- `Remove-Item`:이 cmdlet을 사용 하면 사용자가 데이터 저장소에서 항목을 제거할 수 있습니다. 이 cmdlet을 지원 하려면 Containercmdletprovider 및 Containercmdletprovider를 덮어씁니다. [Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 및 [. Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 메서드를 덮어씁니다.

- `Rename-Item`:이 cmdlet을 사용 하면 사용자가 데이터 저장소에 있는 항목의 이름을 바꿀 수 있습니다. 이 cmdlet을 지원 하려면 Renameitem 및 Containercmdletprovider 메서드를 덮어씁니다. [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) . [Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 메서드를 지원 합니다.

- `Set-Item`:이 cmdlet을 사용 하면 사용자가 데이터 저장소에 있는 항목의 값을 업데이트할 수 있습니다. 이 cmdlet을 지원 하려면 Setitem 및 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 및 [system.object (Setitemdynamicparameters. Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 메서드)를 덮어씁니다.

### <a name="item-content-cmdlets"></a>항목 콘텐츠 cmdlet

- `Add-Content`:이 cmdlet을 사용 하면 사용자가 항목에 콘텐츠를 추가할 수 있습니다.

- `Clear-Content`:이 cmdlet을 사용 하면 사용자가 항목을 삭제 하지 않고 항목에서 콘텐츠를 삭제할 수 있습니다. 이 cmdlet을 지원 하려면 Icontentcmdletprovider 및 Icontentcmdletprovider를 덮어씁니다. [Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 및 [. Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 메서드를 덮어씁니다.

- `Get-Content`:이 cmdlet을 사용 하면 사용자가 항목의 내용을 검색할 수 있습니다. 이 cmdlet을 지원 하려면 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 을 덮어씁니다. [Icontentcmdletprovider 및. Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 메서드 (영문)를 덮어씁니다. [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 메서드는 콘텐츠를 읽는 데 사용 되는 메서드를 정의 하는 [Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) 인터페이스를 반환 합니다 .이 인터페이스를 반환 합니다.

- `Set-Content`:이 cmdlet을 사용 하면 사용자가 항목의 내용을 업데이트할 수 있습니다. 이 cmdlet을 지원 하려면 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 을 덮어씁니다. [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) .. n a m a. n a m a. n a m a. [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 메서드는 콘텐츠를 쓰는 데 사용 되는 메서드를 정의 하는 [Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) 인터페이스를 반환 합니다 .이 인터페이스는 콘텐츠를 쓰는 데 사용 됩니다.

### <a name="item-property-cmdlets"></a>Item 속성 cmdlet

- `Clear-ItemProperty`:이 cmdlet을 사용 하면 사용자가 속성 값을 삭제할 수 있습니다. 이 cmdlet을 지원 하려면 System.object를 덮어씁니다. [Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 및 system.object를 덮어씁니다. [Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 메서드를 사용할 수 있는 경우.

- `Copy-ItemProperty`:이 cmdlet을 사용 하면 사용자가 한 위치에서 다른 위치로 속성 및 값을 복사할 수 있습니다. 이 cmdlet을 지원 하려면 [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) 및 [Idynamicpropertycmdletprovider와 dynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) 메서드를 덮어씁니다 .이 메서드를 지원 하지 않습니다.

- `Get-ItemProperty`:이 cmdlet은 항목의 속성을 검색 합니다. 이 cmdlet을 지원 하려면 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 를 덮어씁니다.. x m p. i n g. i n g. [i n](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) d o d.

- `Move-ItemProperty`:이 cmdlet을 통해 사용자는 속성 및 해당 값을 한 위치에서 다른 위치로 이동할 수 있습니다. 이 cmdlet을 지원 하려면 [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) 및 [Idynamicpropertycmdletprovider 및 매개 변수](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) 메서드를 덮어씁니다 .이 매개 변수를 지원 합니다.

- `New-ItemProperty`:이 cmdlet을 사용 하면 사용자가 새 속성을 만들고 해당 값을 설정할 수 있습니다. 이 cmdlet을 지원 하려면 [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) 및 Idynamicpropertycmdletprovider 및. n e t. n e t. [dynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) 메서드를 덮어씁니다.

- `Remove-ItemProperty`:이 cmdlet을 통해 사용자는 속성과 해당 값을 삭제할 수 있습니다. 이 cmdlet을 지원 하려면 [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) 및 [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) 및. m a p. i n p. n a m a.

- `Rename-ItemProperty`:이 cmdlet을 사용 하면 사용자가 속성의 이름을 변경할 수 있습니다. 이 cmdlet을 지원 하려면 Renameproperty 및 Idynamicpropertycmdletprovider 메서드를 덮어씁니다. [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) . [Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) 메서드를 지원 합니다.

- `Set-ItemProperty`:이 cmdlet을 사용 하면 사용자가 항목의 속성을 업데이트할 수 있습니다. 이 cmdlet을 지원 하려면 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 를 덮어씁니다.. d a t a. d a t a. d a t a. d a [t.](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)

### <a name="location-cmdlets"></a>위치 cmdlet

- `Get-Location`: 현재 작업 위치에 대 한 정보를 검색 합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.

- `Pop-Location`:이 cmdlet은 현재 위치를 가장 최근에 스택에 푸시한 위치로 변경 합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.

- `Push-Location`:이 cmdlet은 위치 목록 ("stack")의 맨 위에 현재 위치를 추가 합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.

- `Set-Location`:이 cmdlet은 현재 작업 위치를 지정 된 위치로 설정 합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.

### <a name="path-cmdlets"></a>경로 cmdlet

- `Join-Path`:이 cmdlet을 통해 사용자는 부모 및 자식 경로 세그먼트를 결합 하 여 공급자 내부 경로를 만들 수 있습니다. 이 cmdlet을 지원 하려면 [system.web](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .. n a m a.

- `Convert-Path`:이 cmdlet은 Windows PowerShell 경로에서 Windows PowerShell 공급자 경로로 경로를 변환 합니다.

- `Split-Path`: 경로의 지정 된 부분을 반환 합니다.

- `Resolve-Path`: 경로에서 와일드 카드 문자를 확인 하 고 경로 내용을 표시 합니다.

- `Test-Path`:이 cmdlet은 경로의 모든 요소가 있는지 여부를 확인 합니다. 이 cmdlet을 지원 하려면 [Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) 메서드를 덮어쓰십시오.. i n g. i [n g.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) m a n g.

### <a name="psprovider-cmdlets"></a>PSProvider cmdlet

- `Get-PSProvider`:이 cmdlet은 세션에서 사용할 수 있는 공급자에 대 한 정보를 반환 합니다. 이 cmdlet을 지원 하기 위해 메서드를 덮어쓸 필요가 없습니다.
