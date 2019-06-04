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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080937"
---
# <a name="provider-samples"></a>공급자 샘플

이 섹션에는 Microsoft Access 데이터베이스에 액세스 하는 공급자의 샘플이 포함 됩니다. 이 이들은 모든 기본 공급자 클래스에서 파생 되는 공급자 클래스를 포함 합니다.

## <a name="in-this-section"></a>이 섹션의 내용

이 섹션에는 다음 항목이 포함됩니다.

[샘플 AccessDBProviderSample01](./accessdbprovidersample01.md) 에서 직접 파생 되는 공급자 클래스를 선언 하는 방법을이 보여 줍니다 합니다 [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 클래스입니다. 여기서는 참조용으로만 설명합니다.

[AccessDBProviderSample02](./accessdbprovidersample02.md) 이 샘플에서는를 덮어쓰는 방법을 보여 줍니다. 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 고 [ System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드 호출을 지원 하기는 `New-PSDrive` 고 `Remove-PSDrive` cmdlet. 이 샘플의 공급자 클래스에서 파생 된 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 클래스입니다.

[AccessDBProviderSample03](./accessdbprovidersample03.md) 이 샘플에서는를 덮어쓰는 방법을 보여 줍니다. 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 고 [ System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드 호출을 지원 하기는 `Get-Item` 고 `Set-Item` cmdlet. 이 샘플의 공급자 클래스에서 파생 된 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.

[AccessDBProviderSample04](./accessdbprovidersample04.md) 이 샘플에 대 한 호출을 지원 하기 위해 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 합니다 `Copy-Item`를 `Get-ChildItem`를 `New-Item`, 및 `Remove-Item` cmdlet. 이러한 메서드는 데이터 저장소에 컨테이너 항목이 포함될 때 구현해야 합니다. 컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다. 이 샘플의 공급자 클래스에서 파생 된 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스입니다.

[AccessDBProviderSample05](./accessdbprovidersample05.md) 이 샘플에 대 한 호출을 지원 하기 위해 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 합니다 `Move-Item` 고 `Join-Path` cmdlet. 이러한 메서드는 사용자가 컨테이너 내의 항목을 이동해야 하고 데이터 저장소에 중첩된 컨테이너가 포함되는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스에서 파생 된 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스입니다.

[AccessDBProviderSample06](./accessdbprovidersample06.md) 위해 콘텐츠 메서드 호출을 지원 하기를 덮어쓰는 방법을이 보여 줍니다 합니다 `Clear-Content`를 `Get-Content`, 및 `Set-Content` cmdlet. 이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스에서 파생 되는 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스에 구현 된 [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스입니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)