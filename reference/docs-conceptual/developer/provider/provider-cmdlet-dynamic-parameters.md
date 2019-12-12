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
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359952"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>공급자 cmdlet 동적 매개 변수

공급자는 사용자가 cmdlet의 정적 매개 변수 중 하나에 대해 특정 값을 지정할 때 공급자 cmdlet에 추가 되는 동적 매개 변수를 정의할 수 있습니다. 예를 들어 공급자는 `Get-Item` 또는 `Set-Item` 공급자 cmdlet을 호출할 때 사용자가 지정 하는 경로에 따라 다른 동적 매개 변수를 추가할 수 있습니다.

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

`Clear-Content` cmdlet [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 을 구현 하 여 Clear-clear cmdlet의 `Path` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

`Clear-Item` cmdlet을 구현 하 여 `Clear-Item` cmdlet의 `Path` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. [Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 메서드.

`Clear-ItemProperty` cmdlet을 구현 하 여 `Clear-ItemProperty` cmdlet의 `Path` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. [Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 메서드.

`Copy-Item` cmdlet [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 을 구현 하 여 `Copy-Item` cmdlet의 `Path`, `Destination`및 `Recurse` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

[Containercmdletprovider Cmdlet Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 및 Containercmdletprovider 메서드를 구현 하 여 `Path`에 의해 트리거되는 동적 매개 변수를 정의 하 고 `Get-ChildItem` cmdlet의 매개 변수를 `Recurse` 수 있습니다. [Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 메서드를 제공 합니다.

`Get-Content` cmdlet [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 을 구현 하 여 `Get-Content` cmdlet의 `Path` 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

`Get-Item` [cmdlet을 구현](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 하 여 `Get-Item` cmdlet의 `Path` 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다...

`Get-ItemProperty` cmdlet은 `Path`에 의해 트리거되는 동적 매개 변수를 정의하고, [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)메서드를 구현하여 `Get-ItemProperty` cmdlet의 `Name` 매개 변수를 정의할 수 있습니다.

`Invoke-Item` cmdlet [Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 메서드를 구현 하 여 `Invoke-Item` cmdlet의 `Path` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

`Move-Item` cmdlet `Path`에 의해 트리거되는 동적 매개 변수를 정의 하 고, `Move-Item` cmdlet의 `Destination` 매개 변수를 정의 하 여 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) 를 구현할 수 있습니다.

`New-Item` cmdlet [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 을 구현 하 여 `New-Item` cmdlet의 `Path`, `ItemType`및 `Value` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

`New-ItemProperty` cmdlet [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) 을 구현 하 여 `Value` cmdlet의 `Path`, `Name`, `PropertyType`및 `New-ItemProperty` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

`New-PSDrive` cmdlet은 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 메서드를 구현하여 `New-PSDrive`cmdlet에서 반환하는 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 개채를 트리거하여 동적 매개변수를 정의할 수 있습니다.

`Remove-Item`은 `Path`에 의해 트리거되는 동적 매개 변수를 정의하고, [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)메서드를 구현하여 `Remove-Item` cmdlet의 `Recurse` 매개 변수를 정의할 수 있습니다.

`Remove-ItemProperty` `Path`에 의해 트리거되는 동적 매개 변수를 정의할 수 있으며, `Remove-ItemProperty` cmdlet의 `Name` 매개 변수는 [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) 를 구현 하 여 정의할 수 있습니다.

`Rename-Item` cmdlet은 `Path`에 의해 트리거되는 동적 매개 변수를 정의하고, [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)메서드를 구현하여 `Rename-Item` cmdlet의 `NewName` 매개 변수를 정의할 수 있습니다.

`Rename-ItemProperty` [Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) 메서드를 구현 하 여 `Rename-ItemProperty` cmdlet의 `Path`, `Name`및 `NewName` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

`Set-Content` cmdlet [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 을 구현 하 여 `Set-Content` cmdlet의 `Path` 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

`Set-Item` cmdlet `Path`에 의해 트리거되는 동적 매개 변수를 정의 하 고, `Set-Item` cmdlet의 `Value` 매개 변수를 정의 하 여 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 를 구현할 수 있습니다.

`Set-ItemProperty` cmdlet은 `Path`에 의해 트리거되는 동적 매개 변수를 정의하고, [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)메서드를 구현하여 `Set-Item` cmdlet의 `Value` 매개 변수를 정의할 수 있습니다.

`Test-Path` cmdlet [Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 메서드를 구현 하 여 `Test-Path` cmdlet의 `Path` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)