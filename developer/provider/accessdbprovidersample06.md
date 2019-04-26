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
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080988"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

이 샘플에 대 한 호출을 지원 하기 위해 콘텐츠 메서드를 덮어쓰는 방법을 보여 줍니다 합니다 `Clear-Content`, `Get-Content`, 및 `Set-Content` cmdlet. 이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스에서 파생 되는 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스에 구현 된 [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스입니다.

## <a name="demonstrates"></a>데모

> [!IMPORTANT]
> 공급자 클래스는 대부분 다음 클래스 중 하나에서 파생 되며 다른 공급자 인터페이스를 구현할 수 있습니다.
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class. 참조 [AccessDBProviderSample03](./accessdbprovidersample03.md)합니다.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class. 참조 [AccessDBProviderSample04](./accessdbprovidersample04.md)합니다.
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.
>
> 자세한 내용은 공급자 기능에 따라에서 파생 되는 공급자 클래스를 선택 하는 방법에 대 한 [Your Windows PowerShell 공급자 디자인](./provider-types.md)합니다.

이 샘플에는 다음 방법을 보여 줍니다.

- 선언 된 `CmdletProvider` 특성입니다.

- 파생 되는 공급자 클래스를 정의 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 선언 클래스를 사용 하 여 [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스입니다.

- 덮어쓰기 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 의 동작을 변경 하는 방법의 `Clear-Content` cmdlet, 사용자가 항목에서 콘텐츠를 제거할 수 있도록 합니다. (이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Clear-Content` cmdlet입니다.)

- 덮어쓰기 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 의 동작을 변경 하는 방법의 `Get-Content` cmdlet, 사용자가 항목의 콘텐츠를 검색할 수 있도록 합니다. (이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Get-Content` cmdlet입니다.).

- 덮어쓰기 합니다 [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) 의 동작을 변경 하는 방법의 `Set-Content` cmdlet, 사용자가 항목의 콘텐츠를 업데이트할 수. (이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `Set-Content` cmdlet입니다.)

## <a name="example"></a>예제

이 샘플의 선택을 취소 하 고, 가져오기 및 기본 Microsoft Access 데이터에서 항목의 콘텐츠를 설정 하는 데 필요한 메서드를 덮어쓰는 방법을 보여 줍니다.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell 공급자를 디자인합니다.](./provider-types.md)