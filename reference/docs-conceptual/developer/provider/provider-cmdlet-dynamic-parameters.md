---
title: Provider cmdlet 동적 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: 9e70fbeaef61d04e66f16d06519742ff2f679df6
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564243"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>공급자 cmdlet 동적 매개 변수

공급자는 사용자가 cmdlet의 정적 매개 변수 중 하나에 대해 특정 값을 지정할 때 공급자 cmdlet에 추가 되는 동적 매개 변수를 정의할 수 있습니다. 예를 들어 공급자는 `Get-Item` 또는 공급자 cmdlet을 호출할 때 사용자가 지정 하는 경로에 따라 다른 동적 매개 변수를 추가할 수 있습니다 `Set-Item` .

## <a name="dynamic-parameter-methods"></a>동적 매개 변수 메서드

동적 매개 변수는 동적 매개 변수 메서드 중 하나를 구현 하 여 정의 됩니다. 여기에는 System.object [와 같은](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)동적 매개 변수 메서드 (예: [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) )를 구현 하는 것입니다. 이러한 메서드는 독립 실행형 cmdlet의 특성과 비슷한 특성으로 데코레이팅된 public 속성이 있는 개체를 반환 합니다. 다음은 인증서 공급자에서 가져온. n a m a. m i n g. m a n [g](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

공급자 cmdlet의 정적 매개 변수와 달리 매개 변수는 독립 실행형 cmdlet에 정의 된 것과 동일한 방식으로 이러한 매개 변수의 특성을 지정할 수 있습니다. 인증서 공급자에서 가져온 동적 매개 변수 클래스의 예는 다음과 같습니다.

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>동적 매개 변수

동적 매개 변수를 추가 하는 데 사용할 수 있는 정적 매개 변수 목록은 다음과 같습니다.

`Clear-Content`cmdlet `Path` [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 을 구현 하 여 clear cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 (메서드를 구현 합니다.

`Clear-Item`cmdlet을 `Path` `Clear-Item` 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 있습니다.-. a m g.

`Clear-ItemProperty`cmdlet을 구현 하 여 cmdlet의 매개 변수로 트리거되는 동적 매개 변수를 정의할 수 있습니다. `Path` `Clear-ItemProperty` [Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 메서드.

`Copy-Item`cmdlet `Path` `Destination` `Recurse` `Copy-Item` [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 을 구현 하 여 cmdlet의, 및 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 (예를 들어,

Containercmdletprovider cmdlet을 구현 하 여 cmdlet의 및 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다. `Path` `Recurse` `Get-ChildItem` [Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 및 [Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 메서드를 구현 합니다.

`Get-Content`cmdlet `Path` `Get-Content` [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 을 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 (메서드를 구현 합니다.

`Get-Item`cmdlet을 `Path` `Get-Item` 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 있습니다... x m g.

`Get-ItemProperty`cmdlet을 구현 하 여 cmdlet의 및 매개 변수로 트리거되는 동적 매개 변수를 정의할 수 있습니다. `Path` `Name` `Get-ItemProperty` [getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 메서드.

`Invoke-Item`cmdlet `Path` `Invoke-Item` [Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 메서드를 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

`Move-Item`cmdlet을 구현 하 여 cmdlet의 및 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다. `Path` `Destination` `Move-Item` [system.webserver cmdletdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) 메서드.

`New-Item`cmdlet `Path` `ItemType` `Value` `New-Item` [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 을 구현 하 여 cmdlet의, 및 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 (예를 들어,

`New-ItemProperty`cmdlet `Path` `Name` `PropertyType` `Value` `New-ItemProperty` [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) 을 구현 하 여 cmdlet의,, 및 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

`New-PSDrive`cmdlet [PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 개체에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 .이 매개 변수는 cmdlet에서 반환 하는 `New-PSDrive` [Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 메서드를 구현 합니다.

`Remove-Item`Cmdlet의 및 매개 변수를 통해 트리거되는 동적 매개 변수는 `Path` `Recurse` `Remove-Item` [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 를 구현 하 여 정의할 수 있습니다.

`Remove-ItemProperty`Cmdlet의 및 매개 변수를 통해 트리거되는 동적 매개 변수는 `Path` `Name` `Remove-ItemProperty` [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) 를 구현 하 여 정의할 수 있습니다.

`Rename-Item`cmdlet `Path` `NewName` `Rename-Item` [Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 메서드를 구현 하 여 cmdlet의 및 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

`Rename-ItemProperty``Path` `Name` `NewName` `Rename-ItemProperty` [Idynamicpropertycmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) 메서드를 구현 하 여 cmdlet의, 및 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

`Set-Content`cmdlet `Path` `Set-Content` [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 을 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 (메서드를 구현 합니다.

`Set-Item`cmdlet은 `Path` cmdlet의 및 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 .이는 `Value` `Set-Item` [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 를 구현 하는 방법입니다.

`Set-ItemProperty`cmdlet을 `Path` `Value` `Set-Item` 구현 하 여 cmdlet [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) 의 및 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다....

`Test-Path`cmdlet `Path` `Test-Path` [Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 메서드를 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)
