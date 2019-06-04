---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081073"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

이 샘플에서는를 덮어쓰는 방법을 보여 줍니다.는 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 하 고 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 호출을 지원 합니다 `Get-Item` 및 `Set-Item` cmdlet. 이 샘플의 공급자 클래스에서 파생 된 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.

## <a name="demonstrates"></a>데모

> [!IMPORTANT]
> 공급자 클래스는 대부분 다음 클래스 중 하나에서 파생 되며 다른 공급자 인터페이스를 구현할 수 있습니다.
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class. 참조 [AccessDBProviderSample04](./accessdbprovidersample04.md)합니다.
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class. 참조 [AccessDBProviderSample05](./accessdbprovidersample05.md)합니다.
>
> 자세한 내용은 공급자 기능에 따라에서 파생 되는 공급자 클래스를 선택 하는 방법에 대 한 [Your Windows PowerShell 공급자 디자인](./provider-types.md)합니다.

이 샘플에는 다음 방법을 보여 줍니다.

- 선언 된 `CmdletProvider` 특성입니다.

- 파생 되는 공급자 클래스를 정의 합니다 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.

- 덮어쓰지는 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 의 동작을 변경 하는 방법의 `New-PSDrive` cmdlet에 새 드라이브를 만들 수 있도록 허용 합니다. (이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `New-PSDrive` cmdlet입니다.)

- 덮어쓰기 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 지원 기존 드라이브를 제거 하는 방법입니다.

- 덮어쓰지는 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 의 동작을 변경 하는 방법의 `Get-Item` cmdlet, 사용자가 데이터 저장소에서 항목을 검색할 수 있도록 합니다. (이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Get-Item` cmdlet입니다.)

- 덮어쓰기 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 의 동작을 변경 하는 방법의 `Set-Item` cmdlet, 사용자가 데이터 저장소에서 항목을 업데이트할 수 있도록 합니다. (이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Get-Item` cmdlet입니다.)

- 덮어쓰기 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 의 동작을 변경 하는 방법의 `Test-Path` cmdlet. (이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Test-Path` cmdlet입니다.)

- 덮어쓰기 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 메서드를 제공 된 경로가 유효한 지 확인 합니다.

## <a name="example"></a>예제

이 예제를 가져오고 Microsoft Access 데이터에서 항목을 기본 설정 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell 공급자를 디자인합니다.](./provider-types.md)