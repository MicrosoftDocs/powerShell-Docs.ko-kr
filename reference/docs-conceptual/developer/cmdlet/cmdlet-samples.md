---
title: Cmdlet 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365882"
---
# <a name="cmdlet-samples"></a><span data-ttu-id="0ee79-102">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="0ee79-102">Cmdlet Samples</span></span>

<span data-ttu-id="0ee79-103">이 섹션에서는 Windows PowerShell 2.0 SDK에서 제공 되는 샘플 코드에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-103">This section describes sample code that is provided in the Windows PowerShell 2.0 SDK.</span></span> <span data-ttu-id="0ee79-104">이 섹션의 항목에서 코드를 복사 하거나 SDK를 사용 하 여 설치 된 소스 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-104">You can copy code from the topics in this section, or open the source files installed with the SDK.</span></span> <span data-ttu-id="0ee79-105">[Windows PowerShell 2.0 SDK (소프트웨어 개발 키트)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) 는 각 샘플에 대 한 추가 정보 파일, 소스 파일 및 Visual Studio 프로젝트 파일을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-105">The [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) provides ReadMe files, source files, and Visual Studio project files for each sample.</span></span> <span data-ttu-id="0ee79-106">SDK가 설치 되 면 `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` 폴더 아래에 있는 샘플을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-106">With the SDK installed, you can find the samples under the `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` folder.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0ee79-107">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="0ee79-107">In This Section</span></span>

<span data-ttu-id="0ee79-108">[GetProcessSample01 샘플](./getprocesssample01-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-108">[GetProcessSample01 Sample](./getprocesssample01-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span>

<span data-ttu-id="0ee79-109">[GetProcessSample02 샘플](./getprocesssample02-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-109">[GetProcessSample02 Sample](./getprocesssample02-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="0ee79-110">검색할 프로세스를 지정 하는 데 사용할 수 있는 Name 매개 변수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-110">It provides a Name parameter that can be used to specify the processes to be retrieved.</span></span>

<span data-ttu-id="0ee79-111">[GetProcessSample03 샘플](./getprocesssample03-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-111">[GetProcessSample03 Sample](./getprocesssample03-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="0ee79-112">파이프라인의 개체 또는 속성 이름이 매개 변수 이름과 동일한 개체의 속성 값을 받아들일 수 있는 Name 매개 변수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-112">It provides a Name parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span>

<span data-ttu-id="0ee79-113">[GetProcessSample04 샘플](./getprocesssample04-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-113">[GetProcessSample04 Sample](./getprocesssample04-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="0ee79-114">프로세스를 검색 하는 동안 오류가 발생 하는 경우 종료 되지 않는 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-114">It generates a nonterminating error if an error occurs while retrieving a process.</span></span>

<span data-ttu-id="0ee79-115">[GetProcessSample05 샘플](./getprocesssample05-sample.md) 이 샘플은 전체 버전의 Get Proc cmdlet을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-115">[GetProcessSample05 Sample](./getprocesssample05-sample.md) This sample shows a complete version of the Get-Proc cmdlet.</span></span>

<span data-ttu-id="0ee79-116">[StopProcessSample01 샘플](./stopprocesssample01-sample.md) 이 샘플에서는 프로세스를 중지 하기 전에 사용자에 게 피드백을 요청 하는 cmdlet을 작성 하는 방법과 사용자가 cmdlet을 사용 하 여 개체를 반환 하도록 지정 하는 `PassThru` 매개 변수를 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-116">[StopProcessSample01 Sample](./stopprocesssample01-sample.md) This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object.</span></span>

<span data-ttu-id="0ee79-117">[StopProcessSample02 샘플](./stopprocesssample02-sample.md) 이 샘플에서는 로컬 컴퓨터에서 프로세스를 중지 하는 동안 디버그, 자세한 정보 및 경고 메시지를 기록 하는 cmdlet을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-117">[StopProcessSample02 Sample](./stopprocesssample02-sample.md) This sample shows how to write a cmdlet that writes debug, verbose, and warning messages while stopping processes on the local computer.</span></span>

<span data-ttu-id="0ee79-118">[StopProcessSample03 샘플](./stopprocesssample03-sample.md) 이 샘플에서는 매개 변수에서 별칭을 포함 하며 와일드 카드 문자를 지 원하는 cmdlet을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-118">[StopProcessSample03 Sample](./stopprocesssample03-sample.md) This sample shows how to write a cmdlet whose parameters have aliases and that support wildcard characters.</span></span>

<span data-ttu-id="0ee79-119">[StopProcessSample04 샘플](./stopprocesssample04-sample.md) 이 샘플에서는 매개 변수 집합을 선언 하 고, 기본 매개 변수 집합을 지정 하 고, 입력 개체를 허용할 수 있는 cmdlet을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-119">[StopProcessSample04 Sample](./stopprocesssample04-sample.md) This sample shows how to write a cmdlet that declares parameter sets, specifies the default parameter set, and can accept an input object.</span></span>

<span data-ttu-id="0ee79-120">[Events01 샘플](./events01-sample.md) 이 샘플에서는 사용자가 [system.web](/dotnet/api/System.IO.FileSystemWatcher)에서 발생 한 이벤트를 등록할 수 있도록 하는 cmdlet을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-120">[Events01 Sample](./events01-sample.md) This sample shows how to create a cmdlet that allows the user to register for events raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="0ee79-121">예를 들어이 cmdlet을 사용 하면 특정 디렉터리에서 파일을 만들 때 실행할 작업을 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-121">With this cmdlet users can, for example, register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="0ee79-122">이 샘플은 [Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 기본 클래스에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ee79-122">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ee79-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0ee79-123">See Also</span></span>

<span data-ttu-id="0ee79-124">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="0ee79-124">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
