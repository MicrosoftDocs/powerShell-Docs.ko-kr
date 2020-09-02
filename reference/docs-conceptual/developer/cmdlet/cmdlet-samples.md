---
title: Cmdlet 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7a4fb91cb316bf4231df0bb4446b9a7cd54cf647
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89235985"
---
# <a name="cmdlet-samples"></a>Cmdlet 샘플

이 섹션에서는 Windows PowerShell 2.0 SDK에서 제공되는 샘플 코드에 대해 설명합니다. 이 섹션의 항목에서 코드를 복사하거나 SDK를 사용하여 설치된 소스 파일을 열 수 있습니다. [Windows PowerShell 2.0 SDK(소프트웨어 개발 키트)](https://www.microsoft.com/download/details.aspx?id=2560)에서는 각 샘플에 대한 추가 정보 파일, 소스 파일 및 Visual Studio 프로젝트 파일을 제공합니다. SDK가 설치되면 `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` 폴더에서 샘플을 찾을 수 있습니다.

## <a name="in-this-section"></a>섹션 내용

[GetProcessSample01 샘플](./getprocesssample01-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색하는 cmdlet을 작성하는 방법을 보여 줍니다.

[GetProcessSample02 샘플](./getprocesssample02-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색하는 cmdlet을 작성하는 방법을 보여 줍니다. 검색할 프로세스를 지정하는 데 사용할 수 있는 Name 매개 변수를 제공합니다.

[GetProcessSample03 샘플](./getprocesssample03-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색하는 cmdlet을 작성하는 방법을 보여 줍니다. 파이프라인의 개체 또는 속성 이름이 매개 변수 이름과 동일한 개체의 속성 값을 사용할 수 있는 Name 매개 변수를 제공합니다.

[GetProcessSample04 샘플](./getprocesssample04-sample.md) 이 샘플에서는 로컬 컴퓨터의 프로세스를 검색하는 cmdlet을 작성하는 방법을 보여 줍니다. 프로세스를 검색하는 동안 오류가 발생하면 종료되지 않는 오류를 생성합니다.

[GetProcessSample05 샘플](./getprocesssample05-sample.md) 이 샘플은 Get-Proc cmdlet의 전체 버전을 보여 줍니다.

[StopProcessSample01 샘플](./stopprocesssample01-sample.md) 이 샘플에서는 프로세스 중지 전 사용자에게 피드백을 요청하는 cmdlet을 작성하는 방법과 사용자가 cmdlet이 개체를 반환하도록 하기 위해 사용하는 `PassThru` 매개 변수를 구현하는 방법을 보여 줍니다.

[StopProcessSample02 샘플](./stopprocesssample02-sample.md) 이 샘플에서는 로컬 컴퓨터에서 프로세스를 중지하는 동안 디버그, 자세한 정보 및 경고 메시지를 기록하는 cmdlet을 작성하는 방법을 보여 줍니다.

[StopProcessSample03 샘플](./stopprocesssample03-sample.md) 이 샘플에서는 매개 변수가 별칭을 포함하며 와일드카드 문자를 지원하는 cmdlet을 작성하는 방법을 보여 줍니다.

[StopProcessSample04 샘플](./stopprocesssample04-sample.md) 이 샘플에서는 매개 변수 집합을 선언하고 기본 매개 변수 집합을 지정하며 입력 개체를 허용할 수 있는 cmdlet을 작성하는 방법을 보여 줍니다.

[Events01 샘플](./events01-sample.md) 이 샘플에서는 사용자가 [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)에 의해 발생한 이벤트를 등록할 수 있도록 하는 cmdlet을 만드는 방법을 보여 줍니다. 예를 들어 이 cmdlet을 사용하면 특정 디렉터리에서 파일을 만들 때 실행할 작업을 등록할 수 있습니다. 이 샘플은 [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 기본 클래스에서 파생됩니다.

## <a name="see-also"></a>관련 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
