---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: c0efd10680d3323b6c8d932604176c4425e7266a
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633365"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

이 샘플에서는 `Copy-Item` ,, `Get-ChildItem` `New-Item` 및 cmdlet에 대 한 호출을 지원 하도록 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 `Remove-Item` . 이러한 메서드는 데이터 저장소에 컨테이너 항목이 포함될 때 구현해야 합니다. 컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다. 이 샘플의 공급자 클래스는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스에서 파생 됩니다.

## <a name="demonstrates"></a>데모

> [!IMPORTANT]
> 공급자 클래스는 대부분 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 에서 파생 될 가능성이 높습니다.

이 샘플은 다음을 보여 줍니다.

- 특성 선언 `CmdletProvider`
- [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스에서 파생 되는 공급자 클래스를 정의 합니다.
- [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) `Copy-Item` 사용자가 한 위치에서 다른 위치로 항목을 복사할 수 있도록 하는 cmdlet의 동작을 변경 하는 ContainerCmdletProvider 메서드를 덮어씁니다. 이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Copy-Item` .
- [Containercmdletprovider Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 덮어써서 사용자가 부모 항목의 자식 항목을 검색할 수 있도록 하는 Get childitems cmdlet의 동작을 변경 합니다. (이 샘플은 동적 매개 변수를 Get ChildItems cmdlet에 추가 하는 방법을 보여 주지 않습니다.)
- Cmdlet의 매개 변수가 지정 된 경우 [Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 메서드를 덮어써서 Get childitems cmdlet의 동작을 변경 합니다 `Name` .
- 사용자가 데이터 저장소에 항목을 추가할 수 있도록 하는 cmdlet의 동작을 변경 하기 위해 [Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드를 덮어씁니다 `New-Item` . 이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `New-Item` .
- Cmdlet의 동작을 변경 하기 위해 [Containercmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드를 덮어씁니다. `Remove-Item` 이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Remove-Item` .

## <a name="example"></a>예제

이 샘플에서는 항목을 복사, 만들기 및 제거 하는 데 필요한 메서드 뿐만 아니라 부모 항목의 자식 항목을 가져오는 메서드를 덮어쓰는 방법을 보여 줍니다.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>참고 항목

[System.object.. i n g.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[Containercmdletprovider입니다.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.object.. i n.](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell 공급자 설계](./provider-types.md)
