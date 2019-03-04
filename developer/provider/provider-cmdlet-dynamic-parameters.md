---
title: 공급자 cmdlet 동적 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: 803fe4ae24a4f8022639c5b6d6298100859177ce
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858359"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>공급자 cmdlet 동적 매개 변수

공급자는 cmdlet의 정적 매개 변수 중 하나에 대 한 특정 값을 지정할 때 공급자 cmdlet에 추가 되는 동적 매개 변수를 정의할 수 있습니다. 공급자를 기반으로 하는 다른 동적 매개 변수를 추가할 수는 예를 들어, 사용자는 경로에서 호출할 때을 지정 합니다 `Get-Item` 또는 `Set-Item` 공급자 cmdlet.

## <a name="dynamic-parameter-methods"></a>동적 매개 변수 메서드

와 같은 동적 매개 변수 방법 중 하나를 구현 하 여 정의 된 동적 매개 변수를 [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 고 [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)의메서드. 이러한 메서드는 독립 실행형 cmdlet의 유사 특성으로 데코레이팅된 공용 속성이 있는 개체를 반환 합니다. 다음은 구현의 예제는 [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 인증서 공급자에서 가져온 메서드:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

공급자 cmdlet의 정적 매개 변수와 달리 독립 실행형 cmdlet에 매개 변수 정의 동일한 방식으로 이러한 매개 변수의 특성을 지정할 수 있습니다. 인증서 공급자에서 수행 하는 동적 매개 변수 클래스의 예는 다음과 같습니다.

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

동적 매개 변수를 추가 하는 데 사용할 수 있는 정적 매개 변수 목록이 다음과 같습니다.

`Clear-Content` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path` 를 구현 하 여 일반 지우기 cmdlet의 매개 변수는 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 메서드.

`Clear-Item` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Clear-Item` 구현 하 여 cmdlet는 [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 메서드.

`Clear-ItemProperty` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Clear-ItemProperty` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 메서드.

`Copy-Item` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path`, `Destination`, 및 `Recurse` 의 매개 변수를 `Copy-Item` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 메서드.

Get-ChildItems cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다는 `Path` 및 `Recures` 의 매개 변수를 `Get-ChildItem` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 고 [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 메서드.

`Get-Content` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Get-Content` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 메서드.

`Get-Item` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Get-Item` 구현 하 여 cmdlet는 [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 메서드.

`Get-ItemProperty` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다는 `Path` 하 고 `Name` 의 매개 변수를 `Get-ItemProperty` 구현 하 여 cmdlet를 [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 메서드.

`Invoke-Item` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Invoke-Item` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 메서드.

`Move-Item` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다는 `Path` 하 고 `Destination` 의 매개 변수를 `Move-Item` 구현 하 여 cmdlet를 [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) 메서드.

`New-Item` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path`, `ItemType`, 및 `Value` 의 매개 변수를 `New-Item` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 메서드.

`New-ItemProperty` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path`, `Name`, `PropertyType`, 및 `Value` 의 매개 변수는 `New-ItemProperty` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) 메서드.

`New-PSDrive` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 에서 반환 된 개체를 `New-PSDrive` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 메서드.

`Remove-Item` 시작 되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path` 및 `Recurse` 의 매개 변수를 `Remove-Item` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 메서드.

`Remove-ItemProperty` 시작 되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path` 및 `Name` 의 매개 변수를 `Remove-ItemProperty` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) 메서드.

`Rename-Item` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다는 `Path` 하 고 `NewName` 의 매개 변수를 `Rename-Item` 구현 하 여 cmdlet를 [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 메서드.

`Rename-ItemProperty` 로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path`, `Name`, 및 `NewName` 의 매개 변수를 `Rename-ItemProperty` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) 메서드.

`Set-Content` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Set-Content` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 메서드.

`Set-Item` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다는 `Path` 하 고 `Value` 의 매개 변수를 `Set-Item` 구현 하 여 cmdlet를 [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 메서드.

`Set-ItemProperty` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다는 `Path` 하 고 `Value` 의 매개 변수를 `Set-Item` 구현 하 여 cmdlet를 [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) 메서드.

`Test-Path` cmdlet로 트리거되는 동적 매개 변수를 정의할 수 있습니다 합니다 `Path` 의 매개 변수를 `Test-Path` 구현 하 여 cmdlet는 [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 메서드.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)