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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861409"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="63266-102">개체에 대한 기본 메서드 정의</span><span class="sxs-lookup"><span data-stu-id="63266-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="63266-103">.NET Framework 개체를 확장 하는 경우 코드 메서드 및 스크립트 메서드를 개체에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63266-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="63266-104">이러한 메서드를 정의 하는 데 사용 되는 XML은 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63266-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="63266-105">다음 섹션의 예는 Windows PowerShell 설치 디렉터리에서 Types.ps1xml 형식 파일에서 (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="63266-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="63266-106">코드 메서드</span><span class="sxs-lookup"><span data-stu-id="63266-106">Code Methods</span></span>

<span data-ttu-id="63266-107">코드 메서드는.NET Framework 개체의 정적 메서드를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="63266-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="63266-108">다음 예제에서는 **ConvertLargeIntegerToInt64** 메서드가 추가 되는 [System.Xml.Xmlnode? Displayproperty =](/dotnet/api/System.Xml.XmlNode) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="63266-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="63266-109">합니다 [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) 요소 코드 메서드로 확장된 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="63266-109">The [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element defines the extended method as a code method.</span></span> <span data-ttu-id="63266-110">합니다 [이름을](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) 요소 확장 메서드의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63266-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="63266-111">그 뿐만 아니라 [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) 요소는 정적 메서드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63266-111">And, the [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element specifies the static method.</span></span> <span data-ttu-id="63266-112">(추가할 수도 있습니다는 [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) 의 멤버에는 요소는 [구성원 집합](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="63266-112">(You can also add the [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="63266-113">스크립트 메서드</span><span class="sxs-lookup"><span data-stu-id="63266-113">Script Methods</span></span>

<span data-ttu-id="63266-114">스크립트 메서드 값을 스크립트의 출력 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="63266-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="63266-115">다음 예제에서는 **ConvertToDateTime** 메서드가 추가 되는 [System.Management.Managementobject? Displayproperty =](/dotnet/api/System.Management.ManagementObject) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="63266-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="63266-116">합니다 [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) 요소 스크립트 메서드로 확장된 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="63266-116">The [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element defines the extended method as a script method.</span></span> <span data-ttu-id="63266-117">합니다 [이름을](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) 요소 확장 메서드의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63266-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="63266-118">그 뿐만 아니라 [스크립트](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) 요소 메서드 값을 생성 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63266-118">And, the [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element specifies the script that generates the method value.</span></span> <span data-ttu-id="63266-119">(추가할 수도 있습니다는 [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) 의 멤버에는 요소는 [구성원 집합](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) 요소입니다.)</span><span class="sxs-lookup"><span data-stu-id="63266-119">(You can also add the [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="63266-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63266-120">See Also</span></span>

<span data-ttu-id="63266-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="63266-121">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>