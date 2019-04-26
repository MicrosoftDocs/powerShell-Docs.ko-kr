---
title: Windows PowerShell Cmdlet 개념 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067078"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="74ecb-102">Windows PowerShell Cmdlet 개념</span><span class="sxs-lookup"><span data-stu-id="74ecb-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="74ecb-103">이 섹션에서는 cmdlet이 작동 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="74ecb-104">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="74ecb-104">In This Section</span></span>

<span data-ttu-id="74ecb-105">이 섹션에는 다음 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-105">This section includes the following topics.</span></span>

<span data-ttu-id="74ecb-106">[Cmdlet 개발 지침](./cmdlet-development-guidelines.md) 이 항목에서는 잘 구성 된 cmdlet을 생성 하기 위해 사용할 수 있는 개발 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="74ecb-107">[Cmdlet 클래스 선언](./cmdlet-class-declaration.md) cmdlet 클래스 선언에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="74ecb-108">[Windows PowerShell 명령에 대 한 동사를 승인](./approved-verbs-for-windows-powershell-commands.md) 이 항목에서는 cmdlet 클래스를 선언 하는 경우 사용할 수 있는 미리 정의 된 cmdlet 동사를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="74ecb-109">[Cmdlet 입력 처리 메서드](./cmdlet-input-processing-methods.md) 이 항목에서는 전처리 작업을 수행 하 고 처리 작업, 입력 처리 작업을 게시 하는 cmdlet를 허용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="74ecb-110">[Cmdlet 매개 변수](./cmdlet-parameters.md) 이 섹션에서는 다양 한 cmdlet에 추가할 수 있는 매개 변수를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="74ecb-111">[Cmdlet 특성](./cmdlet-attributes.md) 이 섹션에서는 필드 cmdlet 매개 변수를 선언 하 고 매개 변수에 대 한 입력된 유효성 검사 규칙을 선언 하려면 cmdlet으로.NET Framework 클래스를 선언 하는 데 사용 되는 특성을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="74ecb-112">[Cmdlet 별칭](./cmdlet-aliases.md) cmdlet 별칭에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="74ecb-113">[Cmdlet 출력](./cmdlet-output.md) cmdlet 반환할 수 있는 출력 유형과 정의 cmdlet에서 반환 되는 개체를 표시 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="74ecb-114">[Cmdlet을 등록](./modules-and-snap-ins.md) 이 섹션에서는 cmdlet 모듈 및 스냅인을 사용 하 여 등록 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="74ecb-115">[확인을 요청](./requesting-confirmation-from-cmdlets.md) 전에 시스템 변경 하려면 해당 cmdlet에서 확인에서 사용자에 요청 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="74ecb-116">[Windows PowerShell 오류 보고](./error-reporting-concepts.md) cmdlet 종료 오류 및 종료 되지 않는 오류를 보고 하는 방법을 설명 및 오류 레코드를 해석 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="74ecb-117">[백그라운드 작업](./background-jobs.md) cmdlet 작업은 현재 세션에서 실행 하는 명령을 사용 하 여 방해 하지 않는 백그라운드 작업 내에서 해당 작업을 수행할 수 있습니다 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="74ecb-118">[Cmdlet과는 Cmdlet 내에서 스크립트를 호출](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) 이 항목에서는 어떻게 cmdlet를 호출할 수 있습니다 다른 cmdlet 및 스크립트 내에서 해당 입력 처리 메서드를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="74ecb-119">[Cmdlet은 설정](./cmdlet-sets.md) 이 항목에서는 기본 클래스를 사용 하 여 cmdlet 집합을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="74ecb-120">[Windows PowerShell 세션 상태](./windows-powershell-session-state.md) 이 항목에서는 Windows PowerShell 세션의 상태를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ecb-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
