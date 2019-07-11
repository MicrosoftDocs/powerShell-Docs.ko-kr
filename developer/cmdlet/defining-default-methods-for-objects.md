---
title: 개체에 대 한 기본 메서드를 정의 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733987"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="6c93b-102">개체에 대한 기본 메서드 정의</span><span class="sxs-lookup"><span data-stu-id="6c93b-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="6c93b-103">.NET Framework 개체를 확장 하는 경우 코드 메서드 및 스크립트 메서드를 개체에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="6c93b-104">이러한 메서드를 정의 하는 데 사용 되는 XML은 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="6c93b-105">다음 섹션의 예는 Windows PowerShell 설치 디렉터리에서 Types.ps1xml 형식 파일에서 (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="6c93b-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="6c93b-106">코드 메서드</span><span class="sxs-lookup"><span data-stu-id="6c93b-106">Code Methods</span></span>

<span data-ttu-id="6c93b-107">코드 메서드는.NET Framework 개체의 정적 메서드를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="6c93b-108">다음 예제에서는 **ConvertLargeIntegerToInt64** 메서드가 추가 되는 [System.Xml.Xmlnode? Displayproperty =](/dotnet/api/System.Xml.XmlNode) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="6c93b-109">합니다 [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) 요소 코드 메서드로 확장된 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="6c93b-110">합니다 [이름을](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) 요소 확장 메서드의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="6c93b-111">그 뿐만 아니라 [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) 요소는 정적 메서드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="6c93b-112">(추가할 수도 있습니다는 [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) 의 멤버에는 요소는 [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="6c93b-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="6c93b-113">스크립트 메서드</span><span class="sxs-lookup"><span data-stu-id="6c93b-113">Script Methods</span></span>

<span data-ttu-id="6c93b-114">스크립트 메서드 값을 스크립트의 출력 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="6c93b-115">다음 예제에서는 **ConvertToDateTime** 메서드가 추가 되는 [System.Management.Managementobject? Displayproperty =](/dotnet/api/System.Management.ManagementObject) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="6c93b-116">합니다 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) 요소 스크립트 메서드로 확장된 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="6c93b-117">합니다 [이름을](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) 요소 확장 메서드의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="6c93b-118">그 뿐만 아니라 [스크립트](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) 요소 메서드 값을 생성 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c93b-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="6c93b-119">(추가할 수도 있습니다는 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) 의 멤버에는 요소는 [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="6c93b-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="6c93b-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c93b-120">See Also</span></span>

<span data-ttu-id="6c93b-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="6c93b-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
