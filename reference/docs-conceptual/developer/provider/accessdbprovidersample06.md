---
title: AccessDBProviderSample06 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 893eb80574c7f142f92906961588e22b1ced0052
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786835"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

이 샘플에서는 `Clear-Content` , 및 cmdlet에 대 한 호출을 지원 하도록 콘텐츠 메서드를 덮어쓰는 방법을 보여 줍니다 `Get-Content` `Set-Content` . 이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 구현 하는 클래스에서 파생 되며, [이 클래스는](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) system.object를 구현 합니다.

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
- [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 선언 하 고 system.object 클래스에서 파생 되는 [공급자 클래스를](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 정의 하는 것입니다 (.
- 사용자가 항목에서 콘텐츠를 제거할 수 있도록 cmdlet의 동작을 변경 하기 위해 [Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 덮어씁니다. `Clear-Content` 이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Clear-Content` .
- Cmdlet의 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 동작을 변경 하 여 `Get-Content` 사용자가 항목의 콘텐츠를 검색할 수 있도록 하는 Icontentcmdletprovider을 덮어쓰는 경우. 이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Get-Content` .
- Cmdlet의 동작을 변경 하 여 사용자가 항목의 내용을 업데이트할 수 있도록 하는 Filesystemprovider. [Getcontentwriter *](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) 메서드를 덮어씁니다. `Set-Content` 이 샘플에서는 cmdlet에 동적 매개 변수를 추가 하는 방법을 보여 주지 않습니다 `Set-Content` .

## <a name="example"></a>예제

이 샘플에서는 Microsoft Access 데이터 베이스에서 항목의 내용을 지우고 가져오고 설정 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a>참고 항목

[System.object.. i n g.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[Containercmdletprovider입니다.](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.object.. i n.](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell 공급자 설계](./provider-types.md)
