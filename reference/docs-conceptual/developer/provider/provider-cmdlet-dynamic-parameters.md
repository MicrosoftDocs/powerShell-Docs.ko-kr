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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359952"
---
# <a name="provider-cmdlet-dynamic-parameters"></a><span data-ttu-id="4821e-102">공급자 cmdlet 동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4821e-102">Provider cmdlet dynamic parameters</span></span>

<span data-ttu-id="4821e-103">공급자는 사용자가 cmdlet의 정적 매개 변수 중 하나에 대해 특정 값을 지정할 때 공급자 cmdlet에 추가 되는 동적 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-103">Providers can define dynamic parameters that are added to a provider cmdlet when the user specifies a certain value for one of the static parameters of the cmdlet.</span></span> <span data-ttu-id="4821e-104">예를 들어 공급자는 `Get-Item` 또는 `Set-Item` 공급자 cmdlet을 호출할 때 사용자가 지정 하는 경로에 따라 다른 동적 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-104">For example, a provider can add different dynamic parameters based on what path the user specifies when they call the `Get-Item` or `Set-Item` provider cmdlets.</span></span>

## <a name="dynamic-parameter-methods"></a><span data-ttu-id="4821e-105">동적 매개 변수 메서드</span><span class="sxs-lookup"><span data-stu-id="4821e-105">Dynamic Parameter Methods</span></span>

<span data-ttu-id="4821e-106">동적 매개 변수는 동적 매개 변수 메서드 (예: [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) [) 중 하나를 구현 하 여 정의 됩니다. System.web](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters). s t a t. s t a t.</span><span class="sxs-lookup"><span data-stu-id="4821e-106">Dynamic parameters are defined by implementing one of the dynamic parameter methods, such as the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s methods.</span></span> <span data-ttu-id="4821e-107">이러한 메서드는 독립 실행형 cmdlet의 특성과 비슷한 특성으로 데코레이팅된 public 속성이 있는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-107">These methods return an object that has public properties that are decorated with attributes similar to those of stand-alone cmdlets.</span></span> <span data-ttu-id="4821e-108">다음은 인증서 공급자에서 가져온. n a m a. m i n g. m a n [g](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="4821e-108">Here is an example of an implementation of the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method taken from the Certificate provider:</span></span>

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

<span data-ttu-id="4821e-109">공급자 cmdlet의 정적 매개 변수와 달리 매개 변수는 독립 실행형 cmdlet에 정의 된 것과 동일한 방식으로 이러한 매개 변수의 특성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-109">Unlike the static parameters of provider cmdlets, you can specify the characteristics of these parameters in the same way that parameters are defined in stand-alone cmdlets.</span></span> <span data-ttu-id="4821e-110">인증서 공급자에서 가져온 동적 매개 변수 클래스의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-110">Here is an example of a dynamic parameter class taken from the Certificate provider:</span></span>

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

## <a name="dynamic-parameters"></a><span data-ttu-id="4821e-111">동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4821e-111">Dynamic Parameters</span></span>

<span data-ttu-id="4821e-112">동적 매개 변수를 추가 하는 데 사용할 수 있는 정적 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-112">Here is a list of the static parameters that can be used to add dynamic parameters.</span></span>

<span data-ttu-id="4821e-113">`Clear-Content` cmdlet [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 을 구현 하 여 clear cmdlet의 `Path` 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다. 방법이.</span><span class="sxs-lookup"><span data-stu-id="4821e-113">`Clear-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the Clear-Clear cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-114">`Clear-Item` cmdlet을 구현 하 여 `Clear-Item` cmdlet의 `Path` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. [Clearitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 메서드.</span><span class="sxs-lookup"><span data-stu-id="4821e-114">`Clear-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-115">`Clear-ItemProperty` cmdlet을 구현 하 여 `Clear-ItemProperty` cmdlet의 `Path` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. [Clearpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 메서드 .</span><span class="sxs-lookup"><span data-stu-id="4821e-115">`Clear-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-116">`Copy-Item` cmdlet을 구현 [하 여 `Copy-Item` cmdlet의 `Path`, `Destination` 및 `Recurse` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. Containercmdletprovider. Copyitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-116">`Copy-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Destination`, and `Recurse` parameters of the `Copy-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-117">Get ChildItems cmdlet `Path`에 의해 트리거되는 동적 매개 변수를 정의할 수 있으며, `Get-ChildItem` cmdlet의 `Recurse` 매개 변수를 구현 [하 여 Containercmdletprovider \* 및 Getchilditemsdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 및 [Containercmdletprovider. Getchildnamesdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 메서드를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-117">Get-ChildItems cmdlet You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Get-ChildItem` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) and [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) methods.</span></span>

<span data-ttu-id="4821e-118">`Get-Content` cmdlet [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 을 구현 하 여 `Get-Content` cmdlet의 `Path` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. 방법이.</span><span class="sxs-lookup"><span data-stu-id="4821e-118">`Get-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-119">`Get-Item` [cmdlet을 구현](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 하 여 `Get-Item` cmdlet의 `Path` 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다...</span><span class="sxs-lookup"><span data-stu-id="4821e-119">`Get-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-120">`Get-ItemProperty` cmdlet은 `Path`에 의해 트리거되는 동적 매개 변수를 정의하고, [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)메서드를 구현하여 `Get-ItemProperty` cmdlet의 `Name` 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-120">`Get-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Get-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-121">`Invoke-Item` cmdlet [Invokedefaultactiondynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 을 구현 하 여 `Invoke-Item` cmdlet의 `Path` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. 방법이.</span><span class="sxs-lookup"><span data-stu-id="4821e-121">`Invoke-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Invoke-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-122">`Move-Item` cmdlet `Path`에 의해 트리거되는 동적 매개 변수를 정의 하 고, `Move-Item` cmdlet의 `Destination` 매개 변수를 정의 하 여 System.object를 구현할 수 있습니다. [Moveitemdynamicparameters \* ](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)메서드.</span><span class="sxs-lookup"><span data-stu-id="4821e-122">`Move-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Destination` parameters of the `Move-Item` cmdlet by implementing the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-123">`New-Item` cmdlet을 구현 [하 여 `New-Item` cmdlet의 `Path`, `ItemType` 및 `Value` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) . n e t parameters \* 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-123">`New-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `ItemType`, and `Value` parameters of the `New-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-124">`New-ItemProperty` cmdlet을 구현 [하 여 `Value` cmdlet의 `Path`, `Name`, `PropertyType` 및 `New-ItemProperty` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. Idynamicpropertycmdletprovider Propertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-124">`New-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Name`, `PropertyType`, and `Value` parameters of the `New-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-125">`New-PSDrive` cmdlet은 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 메서드를 구현하여 `New-PSDrive`cmdlet에서 반환하는 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 개채를 트리거하여 동적 매개변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-125">`New-PSDrive` cmdlet You can define dynamic parameters that are triggered by the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object returned by the `New-PSDrive` cmdlet by implementing the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-126">`Remove-Item`은 `Path`에 의해 트리거되는 동적 매개 변수를 정의하고, [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)메서드를 구현하여 `Remove-Item` cmdlet의 `Recurse` 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-126">`Remove-Item` You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Remove-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-127">`Remove-ItemProperty`를 구현 [하 여 `Path`에 의해 트리거되는 동적 매개 변수 및 `Remove-ItemProperty` cmdlet의 `Name` 매개 변수를 정의할 수 있습니다. Idynamicpropertycmdletprovider. Removepropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-127">`Remove-ItemProperty` You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Remove-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-128">`Rename-Item` cmdlet은 `Path`에 의해 트리거되는 동적 매개 변수를 정의하고, [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)메서드를 구현하여 `Rename-Item` cmdlet의 `NewName` 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-128">`Rename-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `NewName` parameters of the `Rename-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-129">`Rename-ItemProperty`를 구현 [하 여 `Rename-ItemProperty` cmdlet의 `Path`, `Name` 및 `NewName` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-129">`Rename-ItemProperty` You can define dynamic parameters that are triggered by the `Path`, `Name`, and `NewName` parameters of the `Rename-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-130">`Set-Content` cmdlet [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 을 구현 하 여 `Set-Content` cmdlet의 `Path` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. 방법이.</span><span class="sxs-lookup"><span data-stu-id="4821e-130">`Set-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Set-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-131">`Set-Item` cmdlet `Path`에 의해 트리거되는 동적 매개 변수를 정의 하 고, `Set-Item` cmdlet의 `Value` 매개 변수를 정의할 수 [있습니다.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 방법이.</span><span class="sxs-lookup"><span data-stu-id="4821e-131">`Set-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-132">`Set-ItemProperty` cmdlet은 `Path`에 의해 트리거되는 동적 매개 변수를 정의하고, [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)메서드를 구현하여 `Set-Item` cmdlet의 `Value` 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4821e-132">`Set-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="4821e-133">`Test-Path` cmdlet [Invokedefaultactiondynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 을 구현 하 여 `Test-Path` cmdlet의 `Path` 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. 방법이.</span><span class="sxs-lookup"><span data-stu-id="4821e-133">`Test-Path` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Test-Path` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

## <a name="see-also"></a><span data-ttu-id="4821e-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4821e-134">See Also</span></span>

[<span data-ttu-id="4821e-135">Windows PowerShell 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="4821e-135">Writing a Windows PowerShell Provider</span></span>](./writing-a-windows-powershell-provider.md)