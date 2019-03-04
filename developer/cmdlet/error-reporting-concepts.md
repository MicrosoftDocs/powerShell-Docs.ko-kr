---
title: 오류 보고 개념 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: aac6b7b6ac8a0fad15194b6d3f92c434524fabdb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855079"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="f0df9-102">오류 보고 개념</span><span class="sxs-lookup"><span data-stu-id="f0df9-102">Error Reporting Concepts</span></span>

<span data-ttu-id="f0df9-103">오류를 보고 하는 두 가지 메커니즘을 제공 하는 Windows PowerShell: 메커니즘 중 하나 *종료* 및 다른 메커니즘 *비종료 오류*합니다.</span><span class="sxs-lookup"><span data-stu-id="f0df9-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="f0df9-104">반드시 오류를 보고 하려면 cmdlet에 대 한 올바르게 cmdlet을 실행 하는 호스트 응용 프로그램은 적절 한 방식으로 대응할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0df9-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="f0df9-105">Cmdlet을 호출 해야 합니다 [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드는 오류가 발생 하지 않습니다 또는 cmdlet이 해당 입력된 개체를 처리 하는 데 계속 하도록 허용 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0df9-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="f0df9-106">Cmdlet을 호출 해야 합니다 [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) cmdlet은 입력된 개체를 처리를 계속할 수 있으면 종료 되지 않는 오류를 보고 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f0df9-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="f0df9-107">두 메서드는 호스트 응용 프로그램 오류의 원인을 조사 하는 데 사용할 수 있는 오류 레코드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0df9-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="f0df9-108">오류 인지 종료 또는 종료 되지 않는 오류를 확인 하려면 다음 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="f0df9-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="f0df9-109">오류가 계속 현재 개체를 처리 또는 해당 내용에 관계 없이 모든 추가 입력된 개체를 성공적으로 처리에서 cmdlet을 방지 하는 경우 종료 오류를입니다.</span><span class="sxs-lookup"><span data-stu-id="f0df9-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="f0df9-110">오류가 발생 하지 않으려는 경우 cmdlet에 계속 해 서 현재 개체 또는 해당 내용에 관계 없이 모든 추가 입력된 개체를 처리 하는 경우 종료 오류를입니다.</span><span class="sxs-lookup"><span data-stu-id="f0df9-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="f0df9-111">오류가 되었거나 종료 오류를 허용 하지 않거나 개체를 반환 하는 cmdlet에서 발생 하는 경우 허용 하거나 개체를 하나만 반환 하는 cmdlet에서 발생 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="f0df9-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="f0df9-112">오류는 cmdlet에 계속 해 서 현재 개체와 모든 추가 입력된 개체를 처리 하려면 비종료 오류가입니다.</span><span class="sxs-lookup"><span data-stu-id="f0df9-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="f0df9-113">오류는 입력된 개체의 하위 집합 또는 특정 입력된 개체에 관련 된 경우 종료 되지 않는 오류가입니다.</span><span class="sxs-lookup"><span data-stu-id="f0df9-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0df9-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0df9-114">See Also</span></span>

[<span data-ttu-id="f0df9-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="f0df9-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="f0df9-116">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="f0df9-116">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="f0df9-117">Windows PowerShell 오류 레코드</span><span class="sxs-lookup"><span data-stu-id="f0df9-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

<span data-ttu-id="f0df9-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="f0df9-118">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
