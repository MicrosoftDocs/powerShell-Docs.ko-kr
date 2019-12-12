---
title: 자격 증명 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369892"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="c8683-102">Credential 증명 특성 선언</span><span class="sxs-lookup"><span data-stu-id="c8683-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="c8683-103">Credential 특성은 문자열을 매개 변수에 대 한 인수로 전달할 수도 있도록 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 형식의 자격 증명 매개 변수와 함께 사용할 수 있는 선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="c8683-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="c8683-104">이 특성을 매개 변수 선언에 추가 하면 Windows PowerShell에서 문자열 입력을 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8683-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="c8683-105">예를 들어, [Get Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet은이 특성을 사용 하 여 Windows PowerShell에서 cmdlet에 의해 반환 되는 [system.web. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) 개체를 생성 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8683-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="c8683-106">구문</span><span class="sxs-lookup"><span data-stu-id="c8683-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="c8683-107">설명</span><span class="sxs-lookup"><span data-stu-id="c8683-107">Remarks</span></span>

- <span data-ttu-id="c8683-108">일반적으로이 특성은 문자열을 매개 변수에 대 한 인수로 전달할 수도 있도록 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 형식의 매개 변수에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8683-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="c8683-109">[System.object](/dotnet/api/System.Management.Automation.PSCredential) 가 매개 변수에 전달 되 면 Windows PowerShell은 아무 작업도 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c8683-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="c8683-110">Windows PowerShell은 현재 호스트를 사용 하 여 사용자에 게 적절 한 프롬프트를 표시 [합니다.](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="c8683-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="c8683-111">예를 들어이 특성을 사용 하는 경우 기본 호스트는 사용자 이름 및 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8683-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="c8683-112">그러나 다른 프롬프트를 정의 하는 사용자 지정 호스트를 사용 하는 경우에는 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8683-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="c8683-113">이 특성은 Parameter 특성과 함께 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8683-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="c8683-114">해당 특성에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c8683-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="c8683-115">Credential 특성은 [system.web. credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) 클래스에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8683-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8683-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8683-116">See Also</span></span>

[<span data-ttu-id="c8683-117">매개 변수 별칭</span><span class="sxs-lookup"><span data-stu-id="c8683-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="c8683-118">매개 변수 특성 선언</span><span class="sxs-lookup"><span data-stu-id="c8683-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

<span data-ttu-id="c8683-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="c8683-119">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
