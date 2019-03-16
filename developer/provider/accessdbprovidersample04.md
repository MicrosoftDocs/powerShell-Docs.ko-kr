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
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057623"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

이 샘플에 대 한 호출을 지원 하기 위해 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 합니다 `Copy-Item`, `Get-ChildItem`를 `New-Item`, 및 `Remove-Item` cmdlet. 이러한 메서드는 데이터 저장소에 컨테이너 항목이 포함될 때 구현해야 합니다. 컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다. 이 샘플의 공급자 클래스에서 파생 된 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스입니다.

## <a name="demonstrates"></a>시연

> [!IMPORTANT]
> 공급자 클래스에서 파생 가능성이 됩니다는 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

이 샘플에는 다음 방법을 보여 줍니다.

- 선언 된 `CmdletProvider` 특성입니다.

- 파생 되는 공급자 클래스를 정의 합니다 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스입니다.

- 덮어쓰기 합니다 [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 의 동작을 변경 하는 방법의 `Copy-Item` 다른 한 위치에서 항목을 복사할 수 있는 cmdlet. (이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Copy-Item` cmdlet입니다.)

- 덮어쓰기 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 부모 항목의 자식 항목을 검색할 수 있는 Get ChildItems cmdlet의 동작을 변경 하는 방법 . (이 샘플 ChildItems Get cmdlet에 동적 매개 변수를 추가 하는 표시 되지 않습니다.)

- 덮어쓰기 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) ChildItems Get cmdlet의 동작을 변경 하는 방법 때는 `Name` cmdlet의 매개 변수를 지정 합니다.

- 덮어쓰지는 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 의 동작을 변경 하는 방법의 `New-Item` cmdlet는 데이터 저장소에 항목을 추가할 수 있습니다. (이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `New-Item` cmdlet입니다.)

- 덮어쓰기 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 의 동작을 변경 하는 방법의 `Remove-Item` cmdlet. (이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Remove-Item` cmdlet입니다.)

## <a name="example"></a>예제

이 예제를 복사, 생성 및 자식 부모 항목의 항목을 가져오기 위한 메서드에 뿐만 아니라 항목을 제거 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell 공급자를 디자인합니다.](./provider-types.md)