---
title: 공급자 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366302"
---
# <a name="provider-samples"></a>공급자 샘플

이 섹션에는 Microsoft Access 데이터베이스에 액세스 하는 공급자의 샘플이 포함 되어 있습니다. 이러한 샘플에는 모든 기본 공급자 클래스에서 파생 되는 공급자 클래스가 포함 됩니다.

## <a name="in-this-section"></a>섹션 내용

이 섹션에서는 다음 항목을 다룹니다.

[AccessDBProviderSample01 샘플](./accessdbprovidersample01.md) 이 샘플에서는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 클래스에서 직접 파생 되는 공급자 클래스를 선언 하는 방법을 보여 줍니다. 여기서는 참조용으로만 설명합니다.

[AccessDBProviderSample02](./accessdbprovidersample02.md) 이 샘플에서는 `New-PSDrive` 및 `Remove-PSDrive` cmdlet에 대 한 호출을 지원 하기 위해 [Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 및 [Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 덮어쓰는 방법을 보여 줍니다 (예를 들어,이 샘플은. 이 샘플의 공급자 클래스는 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 에서 파생 된 공급자 클래스에서 파생 됩니다.

[AccessDBProviderSample03](./accessdbprovidersample03.md) 이 샘플에서는 `Get-Item` 및 `Set-Item` cmdlet에 대 한 호출을 지원 하기 위해 [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 및 [Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 덮어쓰는 방법을 보여 줍니다 (예를 들면). 이 샘플의 공급자 클래스는 [system.web. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스에서 파생 됩니다.

[AccessDBProviderSample04](./accessdbprovidersample04.md) 이 샘플에서는 `Copy-Item`, `Get-ChildItem`, `New-Item`및 `Remove-Item` cmdlet에 대 한 호출을 지원 하도록 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다. 이러한 메서드는 데이터 저장소에 컨테이너 항목이 포함될 때 구현해야 합니다. 컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다. 이 샘플의 공급자 클래스는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스에서 파생 됩니다.

[AccessDBProviderSample05](./accessdbprovidersample05.md) 이 샘플에서는 `Move-Item` 및 `Join-Path` cmdlet에 대 한 호출을 지원 하도록 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다. 이러한 메서드는 사용자가 컨테이너 내의 항목을 이동해야 하고 데이터 저장소에 중첩된 컨테이너가 포함되는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스는 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 에서 파생 된 공급자 클래스에서 파생 됩니다.

[AccessDBProviderSample06](./accessdbprovidersample06.md) 이 샘플에서는 `Clear-Content`, `Get-Content`및 `Set-Content` cmdlet에 대 한 호출을 지원 하도록 콘텐츠 메서드를 덮어쓰는 방법을 보여 줍니다. 이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 구현 하는 클래스에서 파생 되며, [이 클래스는](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) system.object를 구현 합니다.

## <a name="see-also"></a>관련 항목

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)