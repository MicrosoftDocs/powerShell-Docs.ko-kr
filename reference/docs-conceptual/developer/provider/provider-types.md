---
title: 공급자 유형 | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 0a9bfe5dd0978ffce66db1b18ef4d82be6c1a7f2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359962"
---
# <a name="provider-types"></a>공급자 유형

공급자는 PowerShell에서 제공 하는 공급자 cmdlet이 해당 작업을 수행 하는 방법을 변경 하 여 기본 기능을 정의 합니다. 예를 들어 공급자는 `Get-Item` cmdlet의 기본 기능을 사용할 수도 있고, 데이터 저장소에서 항목을 검색할 때이 cmdlet이 작동 하는 방식을 변경할 수도 있습니다. 이 문서에 설명 된 공급자 기능에는 특정 공급자 기본 클래스 및 인터페이스에서 메서드를 덮어쓰는 방법으로 정의 된 기능이 포함 되어 있습니다.

> [!NOTE]
> PowerShell에서 미리 정의 된 공급자 기능에 대해서는 [공급자 기능](/previous-versions//ee126189(v=vs.85))을 참조 하세요.

## <a name="drive-enabled-providers"></a>드라이브 사용 공급자

드라이브 사용 공급자는 사용자에 게 제공 되는 기본 드라이브를 지정 하 고 사용자가 드라이브를 추가 또는 제거할 수 있도록 허용 합니다. 대부분의 경우 공급자는 데이터 저장소에 액세스 하기 위해 기본 드라이브가 필요 하기 때문에 드라이브 사용이 가능한 공급자입니다. 그러나 사용자 고유의 공급자를 작성 하는 경우 사용자가 드라이브를 만들고 제거 하는 것을 허용 하거나 원하지 않을 수도 있습니다.

드라이브 사용 공급자를 만들려면 공급자 클래스가 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 에서 파생 되거나 해당 클래스에서 파생 되는 다른 클래스에서 파생 될 수 있어야 합니다. **System.object** 는 공급자의 기본 드라이브를 구현 하 고 `New-PSDrive` 및 @no__t cmdlet을 지 원하는 다음 메서드를 정의 합니다. 대부분의 경우 공급자 cmdlet을 지원 하려면 cmdlet을 호출 하기 위해 PowerShell 엔진이 호출 하는 메서드 (예: `New-PSDrive` cmdlet에 대 한 `NewDrive` 메서드)를 덮어써야 하 고 필요에 따라 동적 추가를 위해 `NewDriveDynamicParameters`와 같은 두 번째 메서드를 덮어쓸 수 있습니다. cmdlet에 대 한 매개 변수입니다.

- [System.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) 를 사용 하는 경우 사용자가 사용할 수 있는 기본 드라이브를 정의 하는 기본 드라이브를 정의 합니다.

- [NewDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 및 NewDriveDynamicParameters 메서드는 공급자가 `New-PSDrive`를 지 원하는 방법을 정의 합니다 [.](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) -2를 제공 하는 메서드는입니다. 공급자 cmdlet. 이 cmdlet을 사용 하면 사용자는 드라이브를 만들어 데이터 저장소에 액세스할 수 있습니다.

- [RemoveDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드는 공급자가 `Remove-PSDrive` 공급자 cmdlet을 지 원하는 방법을 정의 합니다. 이 cmdlet을 사용 하면 사용자가 데이터 저장소에서 드라이브를 제거할 수 있습니다.

## <a name="item-enabled-providers"></a>항목 사용 공급자

사용자는 항목 사용 공급자를 사용 하 여 데이터 저장소의 항목을 가져오거나 설정 하거나 지울 수 있습니다. "항목"은 사용자가 독립적으로 액세스 하거나 관리할 수 있는 데이터 저장소의 요소입니다. 항목 사용 공급자를 만들려면 공급자 클래스가 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 에서 파생 되거나 해당 클래스에서 파생 되는 다른 클래스에서 파생 되어야 합니다.

**System.object** 클래스는 특정 공급자 cmdlet을 구현 하기 위해 다음 메서드를 정의 합니다. 대부분의 경우 공급자 cmdlet을 지원 하려면 cmdlet을 호출 하기 위해 PowerShell 엔진이 호출 하는 메서드 (예: `Clear-Item` cmdlet에 대 한 `ClearItem` 메서드)를 덮어써야 하 고 필요에 따라 동적 추가를 위해 `ClearItemDynamicParameters`와 같은 두 번째 메서드를 덮어쓸 수 있습니다. cmdlet에 대 한 매개 변수입니다.

- The [System.Management.Automation.Provider.ItemCmdletProvider.ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) 및 [System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 메서드는 공급자가 다음을 `Clear-Item` 지원하는 방법을 정의합니다. 이 cmdlet을 사용 하면 사용자가 데이터 저장소에 있는 항목의 값을 제거할 수 있습니다.

- [GetItem 및](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 및 [System.object. GetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 메서드는 공급자가 `Get-Item` 공급자를 지 원하는 방법을 정의 하 고 있습니다. #a0. 이 cmdlet을 사용 하면 사용자가 데이터 저장소에서 데이터를 검색할 수 있습니다.

- [SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 및 [System.object. SetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 메서드는 공급자가 `Set-Item` 공급자를 지 원하는 방법을 정의 하는 방법에 대해 설명 합니다. #a0. 이 cmdlet을 사용 하면 사용자가 데이터 저장소에 있는 항목의 값을 업데이트할 수 있습니다.

- [InvokeDefaultAction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 및 [InvokeDefaultActionDynamicParameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters) 메서드는 공급자를 정의 하는 방법을 정의 하는 방법에 대해 설명 합니다. 는 `Invoke-Item` 공급자 cmdlet을 지원 합니다. 이 cmdlet을 사용 하면 사용자가 항목에 지정 된 기본 작업을 수행할 수 있습니다.

- The [System.Management.Automation.Provider.ItemCmdletProvider.ItemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) and [System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)메서드는 공급자가 다음을 `Test-Path` 지원하는 방법을 정의합니다. 이 cmdlet을 사용 하면 사용자가 경로의 모든 요소가 있는지 여부를 확인할 수 있습니다.

공급자 cmdlet을 구현 하는 데 사용 되는 메서드 외에도, **system.object** 는 다음과 같은 메서드를 정의 합니다.

- [ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) 메서드를 사용 하 여 공급자 경로를 지정 하는 경우 사용자가 와일드 카드를 사용할 수 있습니다.

- [System.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 를 사용 하 여 경로를 구문상 사용할 수 있는지 여부를 결정 하는 데 사용 됩니다.

## <a name="container-enabled-providers"></a>컨테이너 사용 공급자

컨테이너를 사용 하는 공급자를 통해 사용자는 컨테이너 항목을 관리할 수 있습니다. 컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다. 컨테이너를 사용 하는 공급자를 만들려면 공급자 클래스가 [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스 또는 해당 클래스에서 파생 되는 다른 클래스에서 파생 되어야 합니다.

> [!IMPORTANT]
> 컨테이너 사용 공급자는 중첩 된 컨테이너를 포함 하는 데이터 저장소에 액세스할 수 없습니다. 컨테이너의 자식 항목이 다른 컨테이너인 경우 탐색 지원 공급자를 구현 해야 합니다.

**ContainerCmdletProvider** 클래스는 특정 공급자 cmdlet을 구현 하기 위해 다음 메서드를 정의 합니다. 대부분의 경우 공급자 cmdlet을 지원 하려면 cmdlet을 호출 하기 위해 PowerShell 엔진이 호출 하는 메서드 (예: `Copy-Item` cmdlet에 대 한 `CopyItem` 메서드)를 덮어써야 하 고 필요에 따라 동적 추가를 위해 `CopyItemDynamicParameters`와 같은 두 번째 메서드를 덮어쓸 수 있습니다. cmdlet에 대 한 매개 변수입니다.

- [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 및 @no__ [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 및. m a n a m e. m a n a m e. m a p. t-2 공급자 cmdlet입니다. 이 cmdlet을 사용 하면 사용자가 한 위치에서 다른 위치로 항목을 복사할 수 있습니다.

- [ContainerCmdletProvider GetChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 및 [ContainerCmdletProvider. GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 메서드는 공급자를 정의 하는 방법을 정의 합니다. 는 `Get-ChildItem` 공급자 cmdlet을 지원 합니다. 이 cmdlet을 사용 하 여 사용자는 부모 항목의 자식 항목을 검색할 수 있습니다.

- [ContainerCmdletProvider GetChildNames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 및 [ContainerCmdletProvider. GetChildNamesDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 메서드는 공급자를 정의 하는 방법을 정의 합니다. 는 `Name` 매개 변수가 지정 된 경우 `Get-ChildItem` 공급자 cmdlet을 지원 합니다.

- [ContainerCmdletProvider NewItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 및 ContainerCmdletProvider. n a m e. n e t [parameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 메서드는 공급자가 @no__를 지 원하는 방법을 정의 합니다. t-2 공급자 cmdlet입니다. 이 cmdlet을 사용 하면 사용자가 데이터 저장소에 새 항목을 만들 수 있습니다.

- [ContainerCmdletProvider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 및 [ContainerCmdletProvider. RemoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 메서드는 공급자가 다음을 지 원하는 방법을 정의 합니다. `Remove-Item` 공급자 cmdlet입니다. 이 cmdlet을 사용 하면 사용자가 데이터 저장소에서 항목을 제거할 수 있습니다.

- ContainerCmdletProvider 및 RenameItemDynamicParameters 메서드는 공급자가 다음을 지 원하는 방법을 정의 합니다. [RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 및 [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) . `Rename-Item` 공급자 cmdlet입니다. 이 cmdlet을 사용 하면 사용자가 데이터 저장소에 있는 항목의 이름을 바꿀 수 있습니다.

공급자 cmdlet을 구현 하는 데 사용 되는 메서드 외에도 **ContainerCmdletProvider** 클래스는 다음 메서드를 정의 합니다.

- [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 메서드는 공급자 클래스에서 항목에 자식 항목이 있는지 여부를 확인 하는 데 사용할 수 있습니다.

- 공급자 클래스에서 [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) 메서드를 사용 하 여 지정 된 경로에서 새 공급자별 경로를 만들 수 있습니다.

## <a name="navigation-enabled-providers"></a>탐색 지원 공급자

탐색 사용 공급자를 사용 하면 사용자가 데이터 저장소에서 항목을 이동할 수 있습니다. 탐색 지원 공급자를 만들려면 공급자 클래스가 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 에서 파생 되어야 합니다. c d c.

**System.object** 클래스는 특정 공급자 cmdlet을 구현 하기 위해 다음 메서드를 정의 합니다. 대부분의 경우 공급자 cmdlet을 지원 하려면 cmdlet을 호출 하기 위해 PowerShell 엔진이 호출 하는 메서드 (예: `Move-Item` cmdlet에 대 한 `MoveItem` 메서드)를 덮어써야 하 고 필요에 따라 동적 추가를 위해 `MoveItemDynamicParameters`와 같은 두 번째 메서드를 덮어쓸 수 있습니다. cmdlet에 대 한 매개 변수입니다.

- [MoveItem 및](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 및. [MoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) 메서드는 공급자가를 지 원하는 방법을 정의 합니다 .이 메서드를 통해 @no __t-2 공급자 cmdlet. 이 cmdlet을 통해 사용자는 저장소의 한 위치에서 다른 위치로 항목을 이동할 수 있습니다.

- [System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 는 공급자가 `Join-Path` 공급자 cmdlet을 지 원하는 방법을 정의 하 고, 이 cmdlet을 통해 사용자는 부모 및 자식 경로 세그먼트를 결합 하 여 공급자 내부 경로를 만들 수 있습니다.

공급자 cmdlet을 구현 하는 데 사용 되는 메서드 외에도 다음과 같은 메서드를 정의 **합니다.**

- [GetChildName](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드는 경로에 대 한 자식 노드의 이름을 추출 하는 방법을 제공 합니다.

- [GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드는 경로의 부모 부분을 추출 합니다 .이 메서드는

- [IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드는 해당 항목이 컨테이너 항목 인지 여부를 확인 하 고, 이 컨텍스트에서 컨테이너는 공통 부모 항목 아래에 있는 자식 항목의 그룹입니다.

- [NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 메서드는 지정 된 기본 경로를 기준으로 하는 항목에 대 한 경로를 반환 합니다.

## <a name="content-enabled-providers"></a>콘텐츠 사용 공급자

콘텐츠 사용 공급자를 사용 하면 사용자가 데이터 저장소에 있는 항목의 내용을 지우거 나 가져오거나 설정할 수 있습니다.
예를 들어 파일 시스템 공급자를 사용 하 여 파일 시스템에서 파일의 내용을 지우고, 가져오고, 설정할 수 있습니다. 콘텐츠 사용 공급자를 만들려면 공급자 클래스가 [IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스의 메서드를 구현 해야 합니다.

**IContentCmdletProvider** 인터페이스는 특정 공급자 cmdlet을 구현 하기 위해 다음 메서드를 정의 합니다. 대부분의 경우 공급자 cmdlet을 지원 하려면 cmdlet을 호출 하기 위해 PowerShell 엔진이 호출 하는 메서드 (예: `Clear-Content` cmdlet에 대 한 `ClearContent` 메서드)를 덮어써야 하 고 필요에 따라 동적 추가를 위해 `ClearContentDynamicParameters`와 같은 두 번째 메서드를 덮어쓸 수 있습니다. cmdlet에 대 한 매개 변수입니다.

- The [System.Management.Automation.Provider.IContentCmdletProvider.ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) and [System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 메서드는 공급자가 다음을 `Clear-Content` 지원하는 방법을 정의합니다. 이 cmdlet을 사용 하면 사용자가 항목을 삭제 하지 않고 항목의 내용을 삭제할 수 있습니다.

- [IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 및 [IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) . n a m. n a m. n a m. n a m. 는 `Get-Content` 공급자 cmdlet을 지원 합니다. 이 cmdlet을 사용 하면 사용자가 항목의 내용을 검색할 수 있습니다. @No__t-0 메서드는 콘텐츠를 읽는 데 사용 되는 메서드를 정의 하는 [IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader) 인터페이스를 반환 합니다.

- [IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 및 [IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) . n a m a. n a m a. n a m a. 는 `Set-Content` 공급자 cmdlet을 지원 합니다. 이 cmdlet을 사용 하면 사용자가 항목의 내용을 업데이트할 수 있습니다. @No__t-0 메서드는 콘텐츠를 쓰는 데 사용 되는 메서드를 정의 하는 [IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) 인터페이스를 반환 합니다.

## <a name="property-enabled-providers"></a>속성 사용 공급자

속성 사용 공급자를 사용 하면 사용자가 데이터 저장소에 있는 항목의 속성을 관리할 수 있습니다.
속성 사용 공급자를 만들려면 공급자 클래스에서 [System.Management.Automation.Provider.IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) and [System.Management.Automation.Provider.IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) 메서드를 구현해야 합니다. 대부분의 경우 공급자 cmdlet을 지원 하려면 Clear 속성 cmdlet에 대 한 `ClearProperty` 메서드와 같이 PowerShell 엔진이 호출 하기 위해 호출 하는 메서드를 덮어써야 하 고 필요에 따라 `ClearPropertyDynamicParameters`과 같은 두 번째 메서드를 덮어써서 추가 하 여 추가할 수 있습니다. cmdlet에 대 한 동적 매개 변수입니다.

**System.object** 는 특정 공급자 cmdlet을 구현 하기 위해 다음 메서드를 정의 합니다.

- [System.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 를 지정 합니다. Clearpropertyimparameters 메서드는 공급자가 제공 하는 방법을 정의 합니다 [. clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 메서드 는 `Clear-ItemProperty` 공급자 cmdlet을 지원 합니다. 이 cmdlet을 사용 하면 사용자가 속성의 값을 삭제할 수 있습니다.

- [System.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) . n o d. i n d. x m p. [i](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) n d. n o d. `Get-ItemProperty` 공급자 cmdlet입니다. 이 cmdlet을 사용 하면 사용자가 항목의 속성을 검색할 수 있습니다.

- [System.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) . d a t. t a p [. i n](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) t. i n t. p a n t o. `Set-ItemProperty` 공급자 cmdlet입니다. 이 cmdlet을 사용 하면 사용자가 항목의 속성을 업데이트할 수 있습니다.

  **IDynamicPropertyCmdletProvider** 인터페이스는 특정 공급자 cmdlet을 구현 하기 위해 다음 메서드를 정의 합니다.

- [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) 및 [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) 및. m a p. m a. n a m e. 공급자는 `Copy-ItemProperty` 공급자 cmdlet을 지원 합니다. 이 cmdlet을 사용 하면 사용자가 한 위치에서 다른 위치로 속성 및 값을 복사할 수 있습니다.

- [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) 및 [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) 및. m a n a. m a. m a n a m. 공급자는 `Move-ItemProperty` 공급자 cmdlet을 지원 합니다. 이 cmdlet을 통해 사용자는 속성 및 해당 값을 한 위치에서 다른 위치로 이동할 수 있습니다.

- [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) 및 IDynamicPropertyCmdletProvider 및. n a m e. n e t [매개 변수](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) 메서드는 다음 방법을 정의 합니다. 공급자는 `New-ItemProperty` 공급자 cmdlet을 지원 합니다. 이 cmdlet을 사용 하면 사용자가 새 속성을 만들고 해당 값을 설정할 수 있습니다.

- [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) 및 [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) 및. m a p. m a. m a. m a p. 공급자는 `Remove-ItemProperty` cmdlet을 지원 합니다. 이 cmdlet을 통해 사용자는 속성과 해당 값을 삭제할 수 있습니다.

- IDynamicPropertyCmdletProvider 및 RenamePropertyDynamicParameters 메서드는 다음 방법을 정의 합니다. [RenameProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) 및 [IDynamicPropertyCmdletProvider.](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) 공급자는 `Rename-ItemProperty` cmdlet을 지원 합니다. 이 cmdlet을 사용 하면 사용자가 속성의 이름을 변경할 수 있습니다.

## <a name="see-also"></a>참고 항목

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)
