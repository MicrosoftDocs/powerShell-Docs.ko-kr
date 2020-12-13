---
ms.date: 09/13/2016
ms.topic: reference
title: 공급자 샘플
description: 공급자 샘플
ms.openlocfilehash: e6b1e8ce603092a3fd9dd44d7be428587544466b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651139"
---
# <a name="provider-samples"></a>공급자 샘플

이 섹션에는 Microsoft Access 데이터베이스에 액세스 하는 공급자의 샘플이 포함 되어 있습니다. 이러한 샘플에는 모든 기본 공급자 클래스에서 파생 되는 공급자 클래스가 포함 됩니다.

## <a name="in-this-section"></a>섹션 내용

이 단원에 포함된 항목은 다음과 같습니다.

[AccessDBProviderSample01 샘플](./accessdbprovidersample01.md) 이 샘플에서는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 클래스에서 직접 파생 되는 공급자 클래스를 선언 하는 방법을 보여 줍니다. 여기서는 참조용으로만 설명합니다.

[AccessDBProviderSample02](./accessdbprovidersample02.md) 이 샘플에서는 및 cmdlet에 대 한 호출을 지원 하기 위해 [Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 및 [Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 덮어쓰는 방법을 보여 줍니다 .이 샘플은 및 cmdlet에 대 한 호출을 지원 `New-PSDrive` `Remove-PSDrive` 합니다. 이 샘플의 공급자 클래스는 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 에서 파생 된 공급자 클래스에서 파생 됩니다.

[AccessDBProviderSample03](./accessdbprovidersample03.md) 이 샘플에서는 및 cmdlet에 대 한 호출을 지원 하기 위해 [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 및 [Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 덮어쓰는 방법을 보여 줍니다 .이 샘플은 `Get-Item` 및 cmdlet에 대 한 호출을 지원 합니다. `Set-Item` 이 샘플의 공급자 클래스는 [system.web. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스에서 파생 됩니다.

[AccessDBProviderSample04](./accessdbprovidersample04.md) 이 샘플에서는 `Copy-Item` ,, `Get-ChildItem` `New-Item` 및 cmdlet에 대 한 호출을 지원 하도록 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 `Remove-Item` . 이러한 메서드는 데이터 저장소에 컨테이너 항목이 포함될 때 구현해야 합니다. 컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다. 이 샘플의 공급자 클래스는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스에서 파생 됩니다.

[AccessDBProviderSample05](./accessdbprovidersample05.md) 이 샘플에서는 및 cmdlet에 대 한 호출을 지원 하도록 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 `Move-Item` `Join-Path` . 이러한 메서드는 사용자가 컨테이너 내의 항목을 이동해야 하고 데이터 저장소에 중첩된 컨테이너가 포함되는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스는 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 에서 파생 된 공급자 클래스에서 파생 됩니다.

[AccessDBProviderSample06](./accessdbprovidersample06.md) 이 샘플에서는 `Clear-Content` , 및 cmdlet에 대 한 호출을 지원 하도록 콘텐츠 메서드를 덮어쓰는 방법을 보여 줍니다 `Get-Content` `Set-Content` . 이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 구현 하는 클래스에서 파생 되며, [이 클래스는](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) system.object를 구현 합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)
