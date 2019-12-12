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
ms.openlocfilehash: aa67bb605f90c1ea40323b4583766069ff1226fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359992"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

이 샘플에서는 `Get-Item` 및 `Set-Item` cmdlet에 대 한 호출을 지원 하기 위해 [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 및 [Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 덮어쓰는 방법을 보여 줍니다 (예를 들면). 이 샘플의 공급자 클래스는 [system.web. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스에서 파생 됩니다.

## <a name="demonstrates"></a>데모

> [!IMPORTANT]
> 공급자 클래스는 다음 클래스 중 하나에서 파생 되 고 다른 공급자 인터페이스를 구현할 수 있습니다.
>
> -   [System.object. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.
> -   [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스를 제공 합니다. [AccessDBProviderSample04](./accessdbprovidersample04.md)를 참조 하세요.
> -   [System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스를 제공 합니다. [AccessDBProviderSample05](./accessdbprovidersample05.md)를 참조 하세요.
>
> 공급자 기능을 기반으로 파생 시킬 공급자 클래스를 선택 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 공급자 디자인](./provider-types.md)을 참조 하세요.

이 샘플은 다음을 보여 줍니다.

- `CmdletProvider` 특성을 선언 합니다.

- [System.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스에서 파생 되는 공급자 클래스를 정의 합니다.

- `New-PSDrive` cmdlet의 동작을 변경 하 여 사용자가 새 드라이브를 만들 수 있도록 하는 [Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 메서드를 덮어씁니다. (이 샘플은 `New-PSDrive` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)

- 기존 드라이브 제거를 지원 하기 위해 [Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 덮어씁니다 (영문).

- `Get-Item` cmdlet의 동작을 변경 하 여 사용자가 데이터 저장소에서 항목을 검색할 수 있도록 하는 [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드를 덮어씁니다. (이 샘플은 `Get-Item` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)

- `Set-Item` cmdlet의 동작을 변경 하 여 사용자가 데이터 저장소의 항목을 업데이트할 수 있도록 하는 [Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 덮어씁니다. (이 샘플은 `Get-Item` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)

- `Test-Path` cmdlet의 동작을 변경 하는 메서드를 덮어쓰는 중. [Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 메서드를 덮어씁니다. (이 샘플은 `Test-Path` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)

- 제공 된 경로가 유효한 지 여부를 확인 하기 위해 [system.web. Itemcmdletprovider. Isvalid path *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 메서드를 덮어씁니다.

## <a name="example"></a>예제

이 샘플에서는 Microsoft Access 데이터 베이스에서 항목을 가져오고 설정 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>참고 항목

[System.object. i n g.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[Containercmdletprovider입니다.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.object. i n.](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell 공급자 디자인](./provider-types.md)
