---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample05
description: AccessDBProviderSample05
ms.openlocfilehash: ad273720ded0b200530f4f81482d01a8fbb82aa3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92656904"
---
# <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

이 샘플에서는 및 cmdlet에 대 한 호출을 지원 하도록 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 `Move-Item` `Join-Path` . 이러한 메서드는 사용자가 컨테이너 내의 항목을 이동해야 하고 데이터 저장소에 중첩된 컨테이너가 포함되는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스는 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 에서 파생 된 공급자 클래스에서 파생 됩니다.

## <a name="demonstrates"></a>데모

> [!IMPORTANT]
> 공급자 클래스는 다음 클래스 중 하나에서 파생 되 고 다른 공급자 인터페이스를 구현할 수 있습니다.
>
> - [System.object. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다. [AccessDBProviderSample03](./accessdbprovidersample03.md)를 참조 하세요.
> - [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스를 제공 합니다. [AccessDBProviderSample04](./accessdbprovidersample04.md)를 참조 하세요.
> - [System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스를 제공 합니다.
>
> 공급자 기능을 기반으로 파생 시킬 공급자 클래스를 선택 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 공급자 디자인](./provider-types.md)을 참조 하세요.

이 샘플은 다음을 보여 줍니다.

- 특성 선언 `CmdletProvider`

- [System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스에서 파생 되는 공급자 클래스를 정의 합니다.

- [Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 덮어써서 cmdlet의 동작을 변경 하 여 `Move-Item` 사용자가 한 위치에서 다른 위치로 항목을 이동할 수 있도록 합니다. 이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Move-Item` .

- Cmdlet의 동작을 변경 하는 메서드를 덮어쓰는 중입니다 [. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드를 덮어씁니다. `Join-Path`

- System.object를 덮어씁니다. [Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드를 덮어씁니다.

- System.object를 덮어씁니다. [Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드를 덮어씁니다.

- System.object를 덮어씁니다. [Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드를 덮어씁니다.

- System.object를 덮어씁니다. [Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 메서드를 덮어씁니다.

## <a name="example"></a>예제

이 샘플에서는 Microsoft Access 데이터 베이스에서 항목을 이동 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="11-1960":::

## <a name="see-also"></a>참고 항목

[System.object.. i n g.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[Containercmdletprovider입니다.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.object.. i n.](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell 공급자 설계](./provider-types.md)
