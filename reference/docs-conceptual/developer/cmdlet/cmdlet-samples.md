---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 샘플
description: Cmdlet 샘플
ms.openlocfilehash: 6ee149f611e5af5c45a62363e19e66bf200c0c0a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668255"
---
# <a name="cmdlet-samples"></a><span data-ttu-id="09fad-103">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="09fad-103">Cmdlet Samples</span></span>

<span data-ttu-id="09fad-104">이 섹션에서는 Windows PowerShell 2.0 SDK에서 제공되는 샘플 코드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-104">This section describes sample code that is provided in the Windows PowerShell 2.0 SDK.</span></span> <span data-ttu-id="09fad-105">이 섹션의 항목에서 코드를 복사하거나 SDK를 사용하여 설치된 소스 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-105">You can copy code from the topics in this section, or open the source files installed with the SDK.</span></span> <span data-ttu-id="09fad-106">[Windows PowerShell 2.0 SDK(소프트웨어 개발 키트)](https://www.microsoft.com/download/details.aspx?id=2560)에서는 각 샘플에 대한 추가 정보 파일, 소스 파일 및 Visual Studio 프로젝트 파일을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-106">The [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/download/details.aspx?id=2560) provides ReadMe files, source files, and Visual Studio project files for each sample.</span></span> <span data-ttu-id="09fad-107">SDK가 설치되면 `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` 폴더에서 샘플을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-107">With the SDK installed, you can find the samples under the `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` folder.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="09fad-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="09fad-108">In This Section</span></span>

<span data-ttu-id="09fad-109">[GetProcessSample01 샘플](./getprocesssample01-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색하는 cmdlet을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-109">[GetProcessSample01 Sample](./getprocesssample01-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span>

<span data-ttu-id="09fad-110">[GetProcessSample02 샘플](./getprocesssample02-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색하는 cmdlet을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-110">[GetProcessSample02 Sample](./getprocesssample02-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="09fad-111">검색할 프로세스를 지정하는 데 사용할 수 있는 Name 매개 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-111">It provides a Name parameter that can be used to specify the processes to be retrieved.</span></span>

<span data-ttu-id="09fad-112">[GetProcessSample03 샘플](./getprocesssample03-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색하는 cmdlet을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-112">[GetProcessSample03 Sample](./getprocesssample03-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="09fad-113">파이프라인의 개체 또는 속성 이름이 매개 변수 이름과 동일한 개체의 속성 값을 사용할 수 있는 Name 매개 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-113">It provides a Name parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span>

<span data-ttu-id="09fad-114">[GetProcessSample04 샘플](./getprocesssample04-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색하는 cmdlet을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-114">[GetProcessSample04 Sample](./getprocesssample04-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="09fad-115">프로세스를 검색하는 동안 오류가 발생하면 종료되지 않는 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-115">It generates a nonterminating error if an error occurs while retrieving a process.</span></span>

<span data-ttu-id="09fad-116">[GetProcessSample05 샘플](./getprocesssample05-sample.md) 이 샘플은 Get-Proc cmdlet의 전체 버전을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-116">[GetProcessSample05 Sample](./getprocesssample05-sample.md) This sample shows a complete version of the Get-Proc cmdlet.</span></span>

<span data-ttu-id="09fad-117">[StopProcessSample01 샘플](./stopprocesssample01-sample.md) 이 샘플에서는 프로세스 중지 전 사용자에게 피드백을 요청하는 cmdlet을 작성하는 방법과 사용자가 cmdlet이 개체를 반환하도록 하기 위해 사용하는 `PassThru` 매개 변수를 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-117">[StopProcessSample01 Sample](./stopprocesssample01-sample.md) This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object.</span></span>

<span data-ttu-id="09fad-118">[StopProcessSample02 샘플](./stopprocesssample02-sample.md) 이 샘플에서는 로컬 컴퓨터에서 프로세스를 중지하는 동안 디버그, 자세한 정보 및 경고 메시지를 기록하는 cmdlet을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-118">[StopProcessSample02 Sample](./stopprocesssample02-sample.md) This sample shows how to write a cmdlet that writes debug, verbose, and warning messages while stopping processes on the local computer.</span></span>

<span data-ttu-id="09fad-119">[StopProcessSample03 샘플](./stopprocesssample03-sample.md) 이 샘플에서는 매개 변수가 별칭을 포함하며 와일드카드 문자를 지원하는 cmdlet을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-119">[StopProcessSample03 Sample](./stopprocesssample03-sample.md) This sample shows how to write a cmdlet whose parameters have aliases and that support wildcard characters.</span></span>

<span data-ttu-id="09fad-120">[StopProcessSample04 샘플](./stopprocesssample04-sample.md) 이 샘플에서는 매개 변수 집합을 선언하고 기본 매개 변수 집합을 지정하며 입력 개체를 허용할 수 있는 cmdlet을 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-120">[StopProcessSample04 Sample](./stopprocesssample04-sample.md) This sample shows how to write a cmdlet that declares parameter sets, specifies the default parameter set, and can accept an input object.</span></span>

<span data-ttu-id="09fad-121">[Events01 샘플](./events01-sample.md) 이 샘플에서는 사용자가 [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)에 의해 발생한 이벤트를 등록할 수 있도록 하는 cmdlet을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-121">[Events01 Sample](./events01-sample.md) This sample shows how to create a cmdlet that allows the user to register for events raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="09fad-122">예를 들어 이 cmdlet을 사용하면 특정 디렉터리에서 파일을 만들 때 실행할 작업을 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-122">With this cmdlet users can, for example, register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="09fad-123">이 샘플은 [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 기본 클래스에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="09fad-123">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="09fad-124">관련 항목</span><span class="sxs-lookup"><span data-stu-id="09fad-124">See Also</span></span>

[<span data-ttu-id="09fad-125">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="09fad-125">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
