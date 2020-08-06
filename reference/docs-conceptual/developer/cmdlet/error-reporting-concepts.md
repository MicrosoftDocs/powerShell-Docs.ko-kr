---
title: 오류 보고 개념 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.openlocfilehash: ff010bbe1a87daa351ec13ed249ffc899781a8c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774510"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="195f1-102">오류 보고 개념</span><span class="sxs-lookup"><span data-stu-id="195f1-102">Error Reporting Concepts</span></span>

<span data-ttu-id="195f1-103">Windows PowerShell은 오류를 보고 하는 두 가지 메커니즘인 오류를 *종료* 하는 메커니즘과 *종료 되지 않는 오류*에 대 한 다른 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="195f1-104">Cmdlet에서 오류를 올바르게 보고 하 여 cmdlet을 실행 하는 호스트 응용 프로그램이 적절 한 방식으로 반응할 수 있도록 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="195f1-105">Cmdlet이 해당 입력 개체를 계속 처리할 수 없는 오류가 발생 하는 경우 cmdlet은 [Throwterminatingerror \*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="195f1-106">Cmdlet은 입력 개체를 계속 처리할 수 있는 경우 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하 여 종료 되지 않는 오류를 보고 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="195f1-107">두 방법 모두 호스트 응용 프로그램에서 오류의 원인을 조사 하는 데 사용할 수 있는 오류 레코드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="195f1-108">다음 지침을 사용 하 여 오류가 종료 또는 종료 되지 않는 오류 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="195f1-109">오류는 cmdlet이 현재 개체를 계속 처리 하지 않거나 내용에 관계 없이 추가 입력 개체를 성공적으로 처리 하지 못하도록 하는 종료 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="195f1-110">오류는 cmdlet이 현재 개체 또는 추가 입력 개체의 내용에 관계 없이 계속 해 서 처리 하지 않으려는 경우 종료 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="195f1-111">개체를 허용 하거나 반환 하지 않는 cmdlet에서 발생 하거나 하나의 개체만 수락 하거나 반환 하는 cmdlet에서 발생 하는 경우에는 종료 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="195f1-112">Cmdlet이 현재 개체와 추가 입력 개체를 계속 해 서 처리 하 게 하려면 오류는 종료 되지 않는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="195f1-113">특정 입력 개체 또는 입력 개체의 하위 집합과 관련 된 경우에는 종료 되지 않는 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="195f1-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="195f1-114">See Also</span></span>

[<span data-ttu-id="195f1-115">Throwterminatingerror \*입니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="195f1-116">WriteError입니다.</span><span class="sxs-lookup"><span data-stu-id="195f1-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="195f1-117">Windows PowerShell 오류 레코드</span><span class="sxs-lookup"><span data-stu-id="195f1-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="195f1-118">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="195f1-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
