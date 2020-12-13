---
ms.date: 09/13/2016
ms.topic: reference
title: 공급자 cmdlet 동적 매개 변수
description: 공급자 cmdlet 동적 매개 변수
ms.openlocfilehash: ac05a847afb0729c34d733fa4ba8da11f46746fe
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92662991"
---
# <a name="provider-cmdlet-dynamic-parameters"></a><span data-ttu-id="e4bcc-103">공급자 cmdlet 동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e4bcc-103">Provider cmdlet dynamic parameters</span></span>

<span data-ttu-id="e4bcc-104">공급자는 사용자가 cmdlet의 정적 매개 변수 중 하나에 대해 특정 값을 지정할 때 공급자 cmdlet에 추가 되는 동적 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-104">Providers can define dynamic parameters that are added to a provider cmdlet when the user specifies a certain value for one of the static parameters of the cmdlet.</span></span> <span data-ttu-id="e4bcc-105">예를 들어 공급자는 `Get-Item` 또는 공급자 cmdlet을 호출할 때 사용자가 지정 하는 경로에 따라 다른 동적 매개 변수를 추가할 수 있습니다 `Set-Item` .</span><span class="sxs-lookup"><span data-stu-id="e4bcc-105">For example, a provider can add different dynamic parameters based on what path the user specifies when they call the `Get-Item` or `Set-Item` provider cmdlets.</span></span>

## <a name="dynamic-parameter-methods"></a><span data-ttu-id="e4bcc-106">동적 매개 변수 메서드</span><span class="sxs-lookup"><span data-stu-id="e4bcc-106">Dynamic Parameter Methods</span></span>

<span data-ttu-id="e4bcc-107">동적 매개 변수는 동적 매개 변수 메서드 중 하나를 구현 하 여 정의 됩니다. 여기에는 System.object [와 같은](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)동적 매개 변수 메서드 (예: [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) )를 구현 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-107">Dynamic parameters are defined by implementing one of the dynamic parameter methods, such as the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s methods.</span></span> <span data-ttu-id="e4bcc-108">이러한 메서드는 독립 실행형 cmdlet의 특성과 비슷한 특성으로 데코레이팅된 public 속성이 있는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-108">These methods return an object that has public properties that are decorated with attributes similar to those of stand-alone cmdlets.</span></span> <span data-ttu-id="e4bcc-109">다음은 인증서 공급자에서 가져온. n a m a. m i n g. m a n [g](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="e4bcc-109">Here is an example of an implementation of the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method taken from the Certificate provider:</span></span>

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

<span data-ttu-id="e4bcc-110">공급자 cmdlet의 정적 매개 변수와 달리 매개 변수는 독립 실행형 cmdlet에 정의 된 것과 동일한 방식으로 이러한 매개 변수의 특성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-110">Unlike the static parameters of provider cmdlets, you can specify the characteristics of these parameters in the same way that parameters are defined in stand-alone cmdlets.</span></span> <span data-ttu-id="e4bcc-111">인증서 공급자에서 가져온 동적 매개 변수 클래스의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-111">Here is an example of a dynamic parameter class taken from the Certificate provider:</span></span>

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

## <a name="dynamic-parameters"></a><span data-ttu-id="e4bcc-112">동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="e4bcc-112">Dynamic Parameters</span></span>

<span data-ttu-id="e4bcc-113">동적 매개 변수를 추가 하는 데 사용할 수 있는 정적 매개 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-113">Here is a list of the static parameters that can be used to add dynamic parameters.</span></span>

<span data-ttu-id="e4bcc-114">`Clear-Content`cmdlet Icontentcmdletprovider cmdlet Clear-Clear의 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다 .이 매개 변수는 `Path` [](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 를 구현 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-114">`Clear-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the Clear-Clear cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-115">`Clear-Item`cmdlet을 `Path` `Clear-Item` 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 [](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 있습니다.-. a m g.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-115">`Clear-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-116">`Clear-ItemProperty` cmdlet을 구현 하 여 cmdlet의 매개 변수로 트리거되는 동적 매개 변수를 정의할 수 있습니다. `Path` `Clear-ItemProperty` [Clearpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 메서드.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-116">`Clear-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-117">`Copy-Item` cmdlet `Path` `Destination` `Recurse` `Copy-Item` [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 을 구현 하 여 cmdlet의, 및 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 (예를 들어,</span><span class="sxs-lookup"><span data-stu-id="e4bcc-117">`Copy-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Destination`, and `Recurse` parameters of the `Copy-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-118">Get-ChildItems cmdlet `Path` `Recurse` `Get-ChildItem` [Containercmdletprovider \* 및 Getchilditemsdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 및 Containercmdletprovider 메서드를 구현 하 여 cmdlet의 및 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다. [Getchildnamesdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="e4bcc-118">Get-ChildItems cmdlet You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Get-ChildItem` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) and [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) methods.</span></span>

<span data-ttu-id="e4bcc-119">`Get-Content` cmdlet `Path` `Get-Content` [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 을 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 (메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-119">`Get-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-120">`Get-Item`cmdlet을 `Path` `Get-Item` 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 [](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 있습니다... x m g.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-120">`Get-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-121">`Get-ItemProperty` cmdlet을 구현 하 여 cmdlet의 및 매개 변수로 트리거되는 동적 매개 변수를 정의할 수 있습니다. `Path` `Name` `Get-ItemProperty` [getpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 메서드.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-121">`Get-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Get-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-122">`Invoke-Item` cmdlet `Path` `Invoke-Item` [Invokedefaultactiondynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 메서드를 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-122">`Invoke-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Invoke-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-123">`Move-Item` cmdlet을 구현 하 여 cmdlet의 및 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다. `Path` `Destination` `Move-Item` [system.webserver cmdletdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) 메서드.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-123">`Move-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Destination` parameters of the `Move-Item` cmdlet by implementing the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-124">`New-Item` cmdlet `Path` `ItemType` `Value` `New-Item` [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 을 구현 하 여 cmdlet의, 및 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 (예를 들어,</span><span class="sxs-lookup"><span data-stu-id="e4bcc-124">`New-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `ItemType`, and `Value` parameters of the `New-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-125">`New-ItemProperty` cmdlet `Path` `Name` `PropertyType` `Value` `New-ItemProperty` [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) 을 구현 하 여 cmdlet의,, 및 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-125">`New-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Name`, `PropertyType`, and `Value` parameters of the `New-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-126">`New-PSDrive`cmdlet [](/dotnet/api/System.Management.Automation.PSDriveInfo) `New-PSDrive` [Newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 메서드를 구현 하 여 cmdlet에서 반환 하는System.Management.Automation.PSDriveinfo 개체에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-126">`New-PSDrive` cmdlet You can define dynamic parameters that are triggered by the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object returned by the `New-PSDrive` cmdlet by implementing the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-127">`Remove-Item` Cmdlet의 및 매개 변수를 통해 트리거되는 동적 매개 변수는 `Path` `Recurse` `Remove-Item` [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 를 구현 하 여 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-127">`Remove-Item` You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Remove-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-128">`Remove-ItemProperty` Cmdlet의 및 매개 변수를 통해 트리거되는 동적 매개 변수는 `Path` `Name` `Remove-ItemProperty` [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) 를 구현 하 여 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-128">`Remove-ItemProperty` You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Remove-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-129">`Rename-Item` cmdlet `Path` `NewName` `Rename-Item` [Containercmdletprovider. Renameitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 메서드를 구현 하 여 cmdlet의 및 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-129">`Rename-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `NewName` parameters of the `Rename-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-130">`Rename-ItemProperty``Path` `Name` `NewName` `Rename-ItemProperty` [Idynamicpropertycmdletprovider. Renamepropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) 메서드를 구현 하 여 cmdlet의, 및 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-130">`Rename-ItemProperty` You can define dynamic parameters that are triggered by the `Path`, `Name`, and `NewName` parameters of the `Rename-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-131">`Set-Content` cmdlet `Path` `Set-Content` [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 을 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 (메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-131">`Set-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Set-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-132">`Set-Item` cmdlet은 `Path` cmdlet의 및 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다 .이는 `Value` `Set-Item` [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 를 구현 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-132">`Set-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-133">`Set-ItemProperty`cmdlet을 `Path` `Value` `Set-Item` 구현 하 여 cmdlet [](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) 의 및 매개 변수를 통해 트리거되는 동적 매개 변수를 정의할 수 있습니다....</span><span class="sxs-lookup"><span data-stu-id="e4bcc-133">`Set-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="e4bcc-134">`Test-Path` cmdlet `Path` `Test-Path` [Invokedefaultactiondynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 메서드를 구현 하 여 cmdlet의 매개 변수에 의해 트리거되는 동적 매개 변수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-134">`Test-Path` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Test-Path` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4bcc-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4bcc-135">See Also</span></span>

[<span data-ttu-id="e4bcc-136">Windows PowerShell 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="e4bcc-136">Writing a Windows PowerShell Provider</span></span>](./writing-a-windows-powershell-provider.md)
