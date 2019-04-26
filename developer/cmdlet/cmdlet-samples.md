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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068454"
---
# <a name="cmdlet-samples"></a>Cmdlet 샘플

이 섹션에서는 Windows PowerShell 2.0 SDK에 제공 되는 샘플 코드를 설명 합니다. 이 섹션의 항목에서 코드를 복사 하거나 SDK와 함께 설치 되는 원본 파일을 열 수 있습니다. 합니다 [Windows PowerShell 2.0 소프트웨어 개발 키트 (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) 추가 정보 파일, 원본 파일 및 각 샘플에 대 한 Visual Studio 프로젝트 파일을 제공 합니다. 설치 된 SDK와 함께 아래에 있는 샘플을 찾을 수 있습니다는 `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` 폴더입니다.

## <a name="in-this-section"></a>이 섹션의 내용

[GetProcessSample01 샘플](./getprocesssample01-sample.md) 이 샘플에는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 작성 하는 방법을 보여 줍니다.

[GetProcessSample02 샘플](./getprocesssample02-sample.md) 이 샘플에는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 작성 하는 방법을 보여 줍니다. 프로세스를 검색할 수를 지정 하는 Name 매개 변수를 제공 합니다.

[GetProcessSample03 샘플](./getprocesssample03-sample.md) 이 샘플에는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 작성 하는 방법을 보여 줍니다. 파이프라인에서 개체 또는 속성 이름이 매개 변수 이름이 동일 개체의 속성에서 값을 받아들일 수 있는 이름 매개 변수를 제공 합니다.

[GetProcessSample04 샘플](./getprocesssample04-sample.md) 이 샘플에는 로컬 컴퓨터의 프로세스를 검색 하는 cmdlet을 작성 하는 방법을 보여 줍니다. 프로세스를 검색 하는 동안 오류가 발생 하는 경우 종료 되지 않는 오류를 생성 합니다.

[GetProcessSample05 샘플](./getprocesssample05-sample.md) 이 샘플에서는 Get-proc cmdlet의 전체 버전을 보여 줍니다.

[StopProcessSample01 샘플](./stopprocesssample01-sample.md) 이 예제에서는 프로세스를 중지 하려고 시도 하기 전에 사용자 로부터 피드백을 요청 하는 cmdlet을 작성 하는 방법 및 구현 하는 방법을 보여 줍니다.는 `PassThru` 사용자가 cmdlet을 반환 하는 여부를 나타내는 매개 변수는 개체입니다.

[StopProcessSample02 샘플](./stopprocesssample02-sample.md) 이 샘플에는 로컬 컴퓨터의 프로세스를 중지 하는 동안 verbose, debug 및 경고 메시지를 기록 하는 cmdlet을 작성 하는 방법을 보여 줍니다.

[StopProcessSample03 샘플](./stopprocesssample03-sample.md) 이 샘플은 cmdlet 매개 변수를 가진 있고 별칭을 작성 하는 방법을 보여 줍니다. 와일드 카드 문자를 지원 합니다.

[StopProcessSample04 샘플](./stopprocesssample04-sample.md) 매개 변수 집합을 선언, 기본 매개 변수를 설정 하 고 입력된 개체를 받을 수를 지정 하는 cmdlet을 작성 하는 방법을이 보여 줍니다.

[샘플 Events01](./events01-sample.md) 에서 발생 한 이벤트에 대 한 사용자 등록을 허용 하는 cmdlet을 만드는 방법을이 보여 줍니다 [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)합니다. 이 cmdlet을 사용 하 여 사용자 예를 들어 특정 디렉터리에서 파일을 만들 때 실행할 동작을 등록할 수 있습니다. 이 샘플에서 파생 된 [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 기본 클래스입니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
