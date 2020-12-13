---
ms.date: 09/13/2016
ms.topic: reference
title: Credential 증명 특성 선언
description: Credential 증명 특성 선언
ms.openlocfilehash: fb826d9a46cadc021fe0c667091bbc7a9251aaa8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648609"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="fe6b4-103">Credential 증명 특성 선언</span><span class="sxs-lookup"><span data-stu-id="fe6b4-103">Credential Attribute Declaration</span></span>

<span data-ttu-id="fe6b4-104">Credential 특성은 문자열을 매개 변수에 대 한 인수로 전달할 수도 있도록 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 형식의 자격 증명 매개 변수와 함께 사용할 수 있는 선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="fe6b4-104">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="fe6b4-105">이 특성을 매개 변수 선언에 추가 하면 Windows PowerShell에서 문자열 입력을 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe6b4-105">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="fe6b4-106">예를 들어, [Get Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet은이 특성을 사용 하 여 Windows PowerShell에서 cmdlet에 의해 반환 되는 [system.web. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) 개체를 생성 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe6b4-106">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="fe6b4-107">구문</span><span class="sxs-lookup"><span data-stu-id="fe6b4-107">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="fe6b4-108">설명</span><span class="sxs-lookup"><span data-stu-id="fe6b4-108">Remarks</span></span>

- <span data-ttu-id="fe6b4-109">일반적으로이 특성은 문자열을 매개 변수에 대 한 인수로 전달할 수도 있도록 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 형식의 매개 변수에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe6b4-109">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="fe6b4-110">[System.object](/dotnet/api/System.Management.Automation.PSCredential) 가 매개 변수에 전달 되 면 Windows PowerShell은 아무 작업도 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe6b4-110">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="fe6b4-111">Windows PowerShell은 현재 호스트를 사용 하 여 사용자에 게 적절 한 프롬프트를 표시 [합니다.](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="fe6b4-111">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="fe6b4-112">예를 들어이 특성을 사용 하는 경우 기본 호스트는 사용자 이름 및 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe6b4-112">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="fe6b4-113">그러나 다른 프롬프트를 정의 하는 사용자 지정 호스트를 사용 하는 경우에는 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe6b4-113">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="fe6b4-114">이 특성은 Parameter 특성과 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe6b4-114">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="fe6b4-115">해당 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fe6b4-115">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="fe6b4-116">Credential 특성은 [system.web. credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe6b4-116">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe6b4-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe6b4-117">See Also</span></span>

[<span data-ttu-id="fe6b4-118">매개 변수 별칭</span><span class="sxs-lookup"><span data-stu-id="fe6b4-118">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="fe6b4-119">Parameter 특성 선언</span><span class="sxs-lookup"><span data-stu-id="fe6b4-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

<span data-ttu-id="fe6b4-120">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="fe6b4-120">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
