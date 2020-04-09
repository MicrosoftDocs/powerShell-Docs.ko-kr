---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: 2fe5c82bc4516574c48fe7effb8bcc60ea6d0bbf
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977474"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

이 샘플에서는 `Clear-Content`, `Get-Content`및 `Set-Content` cmdlet에 대 한 호출을 지원 하도록 콘텐츠 메서드를 덮어쓰는 방법을 보여 줍니다. 이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 구현 하는 클래스에서 파생 되며, [이 클래스는](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) system.object를 구현 합니다.

## <a name="demonstrates"></a>데모

> [!IMPORTANT]
> 공급자 클래스는 다음 클래스 중 하나에서 파생 되 고 다른 공급자 인터페이스를 구현할 수 있습니다.
>
> -   [System.object. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다. [AccessDBProviderSample03](./accessdbprovidersample03.md)를 참조 하세요.
> -   [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스를 제공 합니다. [AccessDBProviderSample04](./accessdbprovidersample04.md)를 참조 하세요.
> -   [System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스를 제공 합니다.
>
> 공급자 기능을 기반으로 파생 시킬 공급자 클래스를 선택 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 공급자 디자인](./provider-types.md)을 참조 하세요.

이 샘플은 다음을 보여 줍니다.

- `CmdletProvider` 특성을 선언 합니다.
- [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 선언 하 고 system.object 클래스에서 파생 되는 [공급자 클래스를](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 정의 하는 것입니다 (.
- `Clear-Content` cmdlet의 동작을 변경 하 여 사용자가 항목에서 콘텐츠를 제거할 수 있도록 하는 [Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 덮어씁니다. (이 샘플은 `Clear-Content` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)
- `Get-Content` cmdlet의 동작을 변경 하 여 사용자가 항목의 콘텐츠를 검색할 수 있도록 하는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 메서드를 덮어씁니다. (이 샘플은 `Get-Content` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)
- `Set-Content` cmdlet의 동작을 변경 하 여 사용자가 항목의 내용을 업데이트할 수 있도록 하는 [Filesystemprovider](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) 메서드를 덮어씁니다. (이 샘플은 `Set-Content` cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다.)

## <a name="example"></a>예제

이 샘플에서는 Microsoft Access 데이터 베이스에서 항목의 내용을 지우고 가져오고 설정 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a>참고 항목

[System.object. i n g.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[Containercmdletprovider입니다.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.object. i n.](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell 공급자 디자인](./provider-types.md)
