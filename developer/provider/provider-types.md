---
title: 공급자 형식 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 37689571eb1650e5991af2e7002cd037ae99dd68
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080914"
---
# <a name="provider-types"></a>공급자 유형

공급자는 공급자 cmdlet (Windows PowerShell에서 제공 됨) 해당 작업을 수행 하는 방법을 변경 하 여 해당 기본 기능을 정의 합니다. 공급자의 기본 기능을 사용할 수는 예를 들어를 `Get-Item` cmdlet을 사용 하거나 해당 데이터 저장소에서 항목을 검색 하는 경우 해당 cmdlet의 작동 방식을 변경할 수 있습니다. 이 항목에 설명 된 공급자 기능이 특정 공급자 기본 클래스 및 인터페이스에서 메서드를 덮어쓰는 방법으로 정의 하는 기능이 포함 되어 있습니다.

> [!NOTE]
> Windows PowerShell에서 미리 정의 된 공급자 기능에 대 한 참조 [공급자 기능](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6)합니다.

## <a name="drive-enabled-providers"></a>공급자 드라이브 사용

사용자에 게 사용할 수 있는 기본 드라이브를 지정 하 고 사용자 추가 또는 드라이브를 제거 하도록 허용 하는 공급자 드라이브 사용. 대부분의 경우에서 공급자는 일부 기본 드라이브를 데이터 저장소에 액세스 해야 하므로 공급자 드라이브 사용 합니다. 있지만 고유한 공급자를 작성 하는 경우 수 있습니다 하거나 사용자가 만들고 드라이브를 제거 하도록 허용 하지 않을 수도 있습니다.

드라이브 설정 공급자를 만들려면 공급자 클래스에서 파생 되어야 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 클래스나 해당 클래스에서 파생 되는 다른 클래스입니다. 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 공급자의 기본 드라이브를 구현 하 고 지원 하기 위한 다음 메서드를 정의 하는 클래스는 `New-PSDrive` 고 `Remove-PSDrive` cmdlet. 대부분의 경우에는 공급자 cmdlet을 지원 하기 위해 덮어써야와 같은 cmdlet을 호출 하려면 Windows PowerShell 엔진을 호출 하는 메서드를 `NewDrive` 에 대 한 메서드는 `New-PSDrive` cmdlet을 필요에 따라 등의두번째메서드를덮어쓸수`NewDriveDynamicParameters`, 동적 매개 변수를 cmdlet에 추가 합니다.

- 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) 메서드는 공급자가 사용 될 때마다 사용자에 게 사용할 수 있는 기본 드라이브를 정의 합니다.

- 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 하 고 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 메서드 공급자에서 지 원하는 방법을 정의 합니다 `New-PSDrive` 공급자 cmdlet. 이 cmdlet에는 사용자가 데이터 저장소에 액세스 하는 드라이브를 만들 수 있도록 합니다.

- 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Remove-PSDrive` 공급자 cmdlet. 이 cmdlet은 드라이브를 데이터 저장소에서 제거할 사용자를 수 있습니다.

## <a name="item-enabled-providers"></a>공급자 항목을 사용 하도록 설정

항목 사용할 공급자 가져오기, 설정, 데이터 저장소에 있는 항목의 선택을 취소 하는 사용자를 허용 합니다. "Item" 요소를 액세스 하거나 독립적으로 관리할 수 있는 데이터 저장소의 경우 항목이 활성화 공급자를 만들려면 공급자 클래스에서 파생 되어야 합니다는 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스나 해당 클래스에서 파생 되는 다른 클래스입니다.

합니다 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스는 특정 공급자 cmdlet을 구현 하기 위한 다음 메서드를 정의 합니다. 대부분의 경우에는 공급자 cmdlet을 지원 하기 위해 덮어써야와 같은 cmdlet을 호출 하려면 Windows PowerShell 엔진을 호출 하는 메서드를 `ClearItem` 에 대 한 메서드는 `Clear-Item` cmdlet을 필요에 따라 등의두번째메서드를덮어쓸수`ClearItemDynamicParameters`, 동적 매개 변수를 cmdlet에 추가 합니다.

- 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) 하 고 [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 메서드 공급자에서 지 원하는 방법을 정의 합니다 `Clear-Item` 공급자 cmdlet. 이 cmdlet에는 데이터 저장소에 있는 항목의 값을 제거 하려면 사용자 수 있습니다.

- 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 하 고 [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 메서드를 정의 하는 방법 공급자 지원에는 `Get-Item` 공급자 cmdlet. 이 cmdlet는 데이터 저장소에서 데이터를 검색할 수가 있도록 합니다.

- 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 하 고 [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 메서드를 정의 하는 방법 공급자 지원에는 `Set-Item` 공급자 cmdlet. 이 cmdlet은 사용자를 데이터 저장소에 있는 항목의 값을 업데이트할 수 있습니다.

- 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 하 고 [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 메서드 공급자에서 지 원하는 방법을 정의 합니다 `Invoke-Item` 공급자 cmdlet. 이 cmdlet을 사용 하면 항목으로 지정 된 기본 작업을 수행할 수 있습니다.

- 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 하 고 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) 메서드 공급자에서 지 원하는 방법을 정의 합니다 `Test-Path` 공급자 cmdlet. 이 cmdlet을 사용 하면 경로의 모든 요소가 있는지 확인 하려면 있습니다.

  공급자 cmdlet을 구현 하는 데 사용 하는 방법 이외에 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스도 다음 메서드를 정의 합니다.

- 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) 메서드 공급자 경로 지정할 때 와일드 카드를 사용할 수 있습니다.

- 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 구문 및 의미 체계가 잘못 된 공급자에 대 한 경로 인지 확인 하는 데 사용 됩니다.

## <a name="container-enabled-providers"></a>컨테이너 지원 공급자

컨테이너 지원 공급자에 컨테이너 항목을 관리 하는 사용자를 허용 합니다. 컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다. 컨테이너 기반 공급자를 만들려면 공급자 클래스에서 파생 되어야 합니다 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스나 해당 클래스에서 파생 되는 다른 클래스입니다.

> [!IMPORTANT]
> 컨테이너 지원 공급자에는 중첩 된 컨테이너를 포함 하는 데이터 저장소로 액세스할 수 없습니다. 컨테이너의 자식 항목을 다른 컨테이너 이면 탐색 지원 공급자를 구현 해야 합니다.

합니다 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스는 특정 공급자 cmdlet을 구현 하기 위한 다음 메서드를 정의 합니다. 대부분의 경우에는 공급자 cmdlet을 지원 하기 위해 덮어써야와 같은 cmdlet을 호출 하려면 Windows PowerShell 엔진을 호출 하는 메서드를 `CopyItem` 에 대 한 메서드는 `Copy-Item` cmdlet을 필요에 따라 등의두번째메서드를덮어쓸수`CopyItemDynamicParameters`, 동적 매개 변수를 cmdlet에 추가 합니다.

- 합니다 [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 하 고 [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Copy-Item` 공급자 cmdlet. 이 cmdlet을 사용 하면 다른 한 위치에서 항목을 복사할 수 있습니다.

- 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 고 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Get-ChildItem` 공급자 cmdlet. 이 cmdlet은 부모 항목의 자식 항목을 검색할 수가 있도록 합니다.

- 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 고 [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Get-ChildItem` 공급자 cmdlet 경우 해당 `Name` 매개 변수를 지정 합니다.

- 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 하 고 [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `New-Item` 공급자 cmdlet. 이 cmdlet에는 사용자가 데이터 저장소에 새 항목을 만들 수 있도록 합니다.

- 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 하 고 [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Remove-Item` 공급자 cmdlet. 이 cmdlet은 사용자를 데이터 저장소에서 항목을 제거할 수 있습니다.

- 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 하 고 [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Rename-Item` 공급자 cmdlet. 이 cmdlet을 사용 하면 데이터 저장소의 항목 이름을 바꾸려면 있습니다.

  공급자 cmdlet을 구현 하는 데 사용 하는 방법 이외에 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스도 다음 메서드를 정의 합니다.

- 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 메서드 수 공급자 클래스에 의해 항목에 자식 항목이 있는지 확인 합니다.

- 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) 메서드 수 공급자 클래스에 의해 지정된 된 경로에서 새 공급자 특정 경로 만듭니다.

## <a name="navigation-enabled-providers"></a>공급자 탐색 지원

탐색 지원 공급자 데이터 저장소에서 항목을 이동 하려면 사용자를 허용 합니다. 탐색 설정 공급자를 만들려면 공급자 클래스에서 파생 되어야 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스입니다.

합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스는 특정 공급자 cmdlet을 구현 하기 위한 다음 메서드를 정의 합니다. 대부분의 경우에는 공급자 cmdlet을 지원 하기 위해 덮어써야와 같은 cmdlet을 호출 하려면 Windows PowerShell 엔진을 호출 하는 메서드를 `MoveItem` 에 대 한 메서드는 `Move-Item` cmdlet을 필요에 따라 등의두번째메서드를덮어쓸수`MoveItemDynamicParameters`, 동적 매개 변수를 cmdlet에 추가 합니다.

- 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 하 고 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Move-Item` 공급자 cmdlet. 이 cmdlet는 저장소의 한 위치에서 다른 위치로 항목을 이동할 수가 있도록 합니다.

- 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Join-Path` 공급자 cmdlet. 이 cmdlet을 사용 하면 내부 공급자 경로를 만들 부모 및 자식 경로 세그먼트를 결합할 수 있습니다.

  공급자 cmdlet을 구현 하는 데 사용 하는 방법 이외에 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스도 다음 메서드를 정의 합니다.

- 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드 추출 경로의 자식 노드의 이름입니다.

- 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드 경로의 부모 부분을 추출 합니다.

- 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드 항목 컨테이너 인지 여부를 결정 합니다. 이 컨텍스트에서 컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다.

- 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 메서드는 지정 된 기본 경로 기준으로 하는 항목에는 경로 반환 합니다.

## <a name="content-enabled-providers"></a>공급자 콘텐츠 사용

콘텐츠 기반 공급자의 선택을 취소 가져오거나 데이터 저장소에서 항목의 콘텐츠를 설정 하려면 사용자를 허용 합니다. 예를 들어, 파일 시스템 공급자의 선택을 취소 하 고, 가져오기 및 파일 시스템에서 파일의 콘텐츠를 설정할 수 있습니다. 설정 된 콘텐츠 공급자를 만들려면 공급자 클래스의 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스입니다.

합니다 [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스 특정 공급자 cmdlet을 구현 하기 위한 다음 메서드를 정의 합니다. 대부분의 경우에는 공급자 cmdlet을 지원 하기 위해 덮어써야와 같은 cmdlet을 호출 하려면 Windows PowerShell 엔진을 호출 하는 메서드를 `ClearContent` 에 대 한 메서드는 `Clear-Content` cmdlet을 필요에 따라 등의두번째메서드를덮어쓸수`ClearContentDynamicParameters`, 동적 매개 변수를 cmdlet에 추가 합니다.

- 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 고 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Clear-Content` 공급자 cmdlet. 이 cmdlet은 항목을 삭제 하지 않고 항목의 콘텐츠를 삭제 하는 사용자를 수 있습니다.

- 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 고 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Get-Content` 공급자 cmdlet. 이 cmdlet에는 항목의 콘텐츠를 검색할 수가 있도록 합니다. 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 메서드가 반환 되는 [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) 정의 하는 인터페이스 콘텐츠를 읽기 위해 사용 되는 메서드.

- 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 고 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Set-Content` 공급자 cmdlet. 이 cmdlet 사용 하면 항목의 콘텐츠를 업데이트 합니다. 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 메서드가 반환 되는 [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) 정의 하는 인터페이스 콘텐츠를 쓰는 데 메서드입니다.

## <a name="property-enabled-providers"></a>공급자 속성을 사용 하도록 설정

공급자 속성 사용이 가능한 데이터 저장소에 있는 항목의 속성을 관리할 사용자를 허용 합니다. 속성을 사용 하도록 설정 공급자를 만들려면 공급자 클래스의 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 고 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) 인터페이스입니다. 대부분의 경우에는 공급자 cmdlet을 지원 하기 위해 덮어써야와 같은 cmdlet을 호출 하려면 Windows PowerShell 엔진을 호출 하는 메서드는 `ClearProperty` 일반-속성에 있는 cmdlet 및 필요에 따라 메서드 등의두번째메서드를덮어쓸수`ClearPropertyDynamicParameters`, 동적 매개 변수를 cmdlet에 추가 합니다.

합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 인터페이스 특정 공급자 cmdlet을 구현 하기 위한 다음 메서드를 정의 합니다.

- 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 고 [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Clear-ItemProperty` 공급자 cmdlet. 이 cmdlet은 사용자를 속성의 값을 삭제할 수 있습니다.

- 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 고 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Get-ItemProperty` 공급자 cmdlet. 이 cmdlet에는 항목의 속성을 검색할 수가 있도록 합니다.

- 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 고 [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Set-ItemProperty` 공급자 cmdlet. 이 cmdlet을 사용 하면 항목의 속성을 업데이트할 수 있습니다.

  합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) 인터페이스 특정 공급자 cmdlet을 구현 하기 위한 다음 메서드를 정의 합니다.

- 합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) 고 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Copy-ItemProperty` 공급자 cmdlet. 이 cmdlet은 사용자를 속성 및 해당 값을 한 위치에서 다른 위치로 복사할 수 있습니다.

- 합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) 고 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Move-ItemProperty` 공급자 cmdlet. 이 cmdlet에는 다른 위치로 속성 및 해당 값을 이동할 수가 있도록 합니다.

- 합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) 고 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `New-ItemProperty` 공급자 cmdlet. 이 cmdlet은 새 속성을 만들고 해당 값을 설정 하는 사용자를 수 있습니다.

- 합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) 고 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Remove-ItemProperty` cmdlet. 이 cmdlet은 속성 및 해당 값을 삭제할 수 있습니다.

- 합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) 고 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) 메서드는 공급자에서 지 원하는 방법을 정의 합니다 `Rename-ItemProperty` cmdlet. 이 cmdlet을 사용 하면 속성의 이름을 변경할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)