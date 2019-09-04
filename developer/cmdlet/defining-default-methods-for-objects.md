---
title: 개체에 대 한 기본 메서드 정의 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215281"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="e4ba7-102">개체에 대한 기본 메서드 정의</span><span class="sxs-lookup"><span data-stu-id="e4ba7-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="e4ba7-103">.NET Framework 개체를 확장 하는 경우 개체에 코드 메서드 및 스크립트 메서드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="e4ba7-104">이러한 메서드를 정의 하는 데 사용 되는 XML은 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="e4ba7-105">다음 섹션의 예제는 Windows PowerShell 설치 디렉터리 `Types.ps1xml` (`$PSHOME`)의 형식 파일에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-105">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="e4ba7-106">자세한 내용은 [Types.ps1xml 정보](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="e4ba7-107">코드 메서드</span><span class="sxs-lookup"><span data-stu-id="e4ba7-107">Code methods</span></span>

<span data-ttu-id="e4ba7-108">코드 메서드가 .NET Framework 개체의 정적 메서드를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-108">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="e4ba7-109">다음 예제에서는 **ToString** 메서드를 [system.xml](/dotnet/api/System.Xml.XmlNode) 형식에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-109">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="e4ba7-110">[Pscodemethod](/dotnet/api/system.management.automation.pscodemethod) 요소는 확장 메서드를 코드 메서드로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-110">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="e4ba7-111">[Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) 요소는 확장 메서드의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="e4ba7-112">그리고 [Codereference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) 요소는 정적 메서드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-112">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="e4ba7-113">[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) 요소의 멤버에 [pscodemethod](/dotnet/api/system.management.automation.pscodemethod) 요소를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-113">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="e4ba7-114">스크립트 메서드</span><span class="sxs-lookup"><span data-stu-id="e4ba7-114">Script methods</span></span>

<span data-ttu-id="e4ba7-115">스크립트 메서드는 값이 스크립트의 출력을 포함 하는 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-115">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="e4ba7-116">다음 예제에서는 **ConvertToDateTime** 메서드를 [system.web 개체](/dotnet/api/System.Management.ManagementObject) 형식에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-116">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="e4ba7-117">[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) 요소는 확장 메서드를 스크립트 메서드로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-117">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="e4ba7-118">[Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) 요소는 확장 메서드의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="e4ba7-119">[스크립트](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) 요소는 메서드 값을 생성 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-119">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="e4ba7-120">[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) 요소의 멤버에 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) 요소를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba7-120">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e4ba7-121">참고자료</span><span class="sxs-lookup"><span data-stu-id="e4ba7-121">See also</span></span>

<span data-ttu-id="e4ba7-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="e4ba7-122">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
