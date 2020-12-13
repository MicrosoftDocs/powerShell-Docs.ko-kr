---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell Cmdlet 개념
description: Windows PowerShell Cmdlet 개념
ms.openlocfilehash: da34d3d229f6d57ee22d84fc024b31eb2ee27ba3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652536"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="4b8b3-103">Windows PowerShell Cmdlet 개념</span><span class="sxs-lookup"><span data-stu-id="4b8b3-103">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="4b8b3-104">이 섹션에서는 cmdlet의 작동 방식에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-104">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4b8b3-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="4b8b3-105">In This Section</span></span>

<span data-ttu-id="4b8b3-106">이 섹션에는 다음 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-106">This section includes the following topics.</span></span>

<span data-ttu-id="4b8b3-107">[Cmdlet 개발 지침](./cmdlet-development-guidelines.md) 이 항목에서는 올바른 형식의 cmdlet을 생성 하는 데 사용할 수 있는 개발 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-107">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="4b8b3-108">[Cmdlet 클래스 선언](./cmdlet-class-declaration.md) 이 항목에서는 cmdlet 클래스 선언에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-108">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="4b8b3-109">[Windows PowerShell 명령에 대해 승인 된 동사](./approved-verbs-for-windows-powershell-commands.md) 이 항목에서는 cmdlet 클래스를 선언할 때 사용할 수 있는 미리 정의 된 cmdlet 동사를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-109">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="4b8b3-110">[Cmdlet 입력 처리 방법](./cmdlet-input-processing-methods.md) 이 항목에서는 cmdlet이 전처리 작업, 입력 처리 작업 및 사후 처리 작업을 수행할 수 있도록 하는 메서드에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-110">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="4b8b3-111">[Cmdlet 매개 변수](./cmdlet-parameters.md) 이 섹션에서는 cmdlet에 추가할 수 있는 다양 한 유형의 매개 변수를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-111">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="4b8b3-112">[Cmdlet 특성](./cmdlet-attributes.md) 이 섹션에서는 .NET Framework 클래스를 cmdlet으로 선언 하 고, 필드를 cmdlet 매개 변수로 선언 하 고, 매개 변수에 대 한 입력 유효성 검사 규칙을 선언 하는 데 사용 되는 특성에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-112">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="4b8b3-113">[Cmdlet 별칭](./cmdlet-aliases.md) 이 항목에서는 cmdlet 별칭에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-113">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="4b8b3-114">[Cmdlet 출력](./cmdlet-output.md) 이 섹션에서는 cmdlet에서 반환할 수 있는 출력 유형과 cmdlet에서 반환 되는 개체를 정의 하 고 표시 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-114">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="4b8b3-115">[Cmdlet 등록](./modules-and-snap-ins.md) 이 섹션에서는 모듈 및 스냅인을 사용 하 여 cmdlet을 등록 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-115">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="4b8b3-116">[확인 요청](./requesting-confirmation-from-cmdlets.md) 이 섹션에서는 사용자가 시스템을 변경 하기 전에 cmdlet에서 확인을 요청 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-116">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="4b8b3-117">[Windows PowerShell 오류 보고](./error-reporting-concepts.md) 이 섹션에서는 cmdlet의 종료 오류 및 종료 되지 않는 오류를 보고 하는 방법에 대해 설명 하 고 오류 레코드를 해석 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-117">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="4b8b3-118">[백그라운드 작업](./background-jobs.md) 이 항목에서는 cmdlet이 현재 세션에서 실행 되는 명령을 방해 하지 않는 백그라운드 작업 내에서 작업을 수행 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-118">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="4b8b3-119">[Cmdlet에서 cmdlet 및 스크립트 호출](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) 이 항목에서는 cmdlet이 입력 처리 메서드 내에서 다른 cmdlet 및 스크립트를 호출 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-119">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="4b8b3-120">[Cmdlet 집합](./cmdlet-sets.md) 이 항목에서는 기본 클래스를 사용 하 여 cmdlet 집합을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-120">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="4b8b3-121">[Windows PowerShell 세션 상태](./windows-powershell-session-state.md) 이 항목에서는 Windows PowerShell 세션 상태에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b8b3-121">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
