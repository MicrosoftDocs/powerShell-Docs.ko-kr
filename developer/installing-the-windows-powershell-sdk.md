---
title: Windows PowerShell SDK 설치
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082484"
---
# <a name="installing-the-windows-powershell-sdk"></a>Windows PowerShell SDK 설치

적용 대상: Windows PowerShell 2.0, Windows PowerShell 3.0

다음 항목에서는 여러 버전의 Windows에 PowerShell SDK를 설치하는 방법을 설명합니다.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Windows 8 및 Windows Server 2012용 Windows PowerShell 3.0 SDK 설치

Windows PowerShell 3.0은 Windows 8 및 Windows Server 2012와 함께 자동으로 설치됩니다. 또한 Windows 8 SDK의 일부로써 Windows PowerShell 3.0의 참조 어셈블리를 다운로드하고 설치할 수 있습니다. 이러한 어셈블리를 사용하여 Windows PowerShell 3.0에 대한 cmdlet, 공급자 및 호스트 프로그램을 작성할 수 있습니다. Windows 8용 Windows SDK를 설치하면 Windows PowerShell 어셈블리가 참조 어셈블리 폴더(\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0)에 자동으로 설치됩니다. 자세한 내용은 Windows 8 SDK 다운로드 사이트를 참조 하세요. Windows PowerShell 코드 샘플은 개발자 센터에서도 제공됩니다.
자세한 내용은 개발자 센터 사이트에서 데스크톱 코드 샘플 페이지를 참조 하세요.

또한 Windows PowerShell 3.0은 다수의 코드 샘플이 포함된 이전 버전인 Windows PowerShell 2.0 SDK와 호환됩니다. Windows PowerShell 2.0 SDK를 다운로드하는 방법에 대한 자세한 내용은 다음을 참조하세요. (2.0 코드 샘플은 Windows 8 및 Windows PowerShell 3.0과 호환되지만 Windows 8 플랫폼에 Windows PowerShell 2.0을 설치할 수 없습니다.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Windows 7 및 Windows Server 2008 R2용 Windows PowerShell 3.0 SDK 설치

Windows 7 및 Windows Server 2008 R2는 PowerShell 2.0을 자동으로 설치합니다. 또한 이러한 시스템에 PowerShell 3.0을 설치할 수 있습니다. (자세한 내용은 참조 Windows PowerShell을 설치 합니다.). 위에서 설명한 대로, Windows 7 및 Windows Server 2008 R2에서도 Windows 8 SDK를 설치할 수 있습니다.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Windows 7, Vista, XP, Server 2003 및 Server 2008용 Windows PowerShell 2.0 SDK 설치

Windows PowerShell 2.0 SDK는 cmdlet, 공급자 및 호스팅 애플리케이션을 작성하는 데 필요한 참조 어셈블리를 제공하고 코드 작성을 시작할 때 시작 지점으로 사용할 수 있는 C# 샘플 코드를 제공합니다.

이 SDK를 설치 하려면 Windows PowerShell 2.0 SDK를 참조 하세요.

### <a name="reference-assemblies"></a>참조 어셈블리

참조 어셈블리는 기본적으로 다음 위치에 설치 됩니다: c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0 합니다.

> [!NOTE]
>
> Windows PowerShell 2.0 어셈블리에 대해 컴파일된 코드는 Windows PowerShell 1.0 설치에 로드할 수 없습니다. 그러나 Windows PowerShell 1.0 어셈블리에 대해 컴파일되는 코드는 Windows PowerShell 2.0 설치에 로드할 수 있습니다.


### <a name="samples"></a>샘플

코드 샘플은 기본적으로 다음 위치에 설치 됩니다. C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. 다음 섹션에서는 각 샘플의 용도에 대해 간략하게 설명합니다.

#### <a name="cmdlet-samples"></a>Cmdlet 샘플

- GetProcessSample01-로컬 컴퓨터의 모든 프로세스를 가져오는 간단한 cmdlet을 작성 하는 방법을 보여 줍니다.
- GetProcessSample02-cmdlet에 매개 변수를 추가 하는 방법을 보여 줍니다. cmdlet은 하나 이상의 프로세스 이름을 사용하고 일치하는 프로세스를 반환합니다.
- GetProcessSample03-파이프라인에서 입력을 허용 하는 매개 변수를 추가 하는 방법을 보여 줍니다.
- GetProcessSample04-종료 되지 않는 오류를 처리 하는 방법을 보여 줍니다.
- GetProcessSample05-지정 된 프로세스의 목록을 표시 하는 방법을 보여 줍니다.
- SelectObject-특정 개체만 선택 하는 필터를 작성 하는 방법을 보여 줍니다.
- SelectString-지정 된 패턴에 대 한 파일을 검색 하는 방법을 보여 줍니다.
- StopProcessSample01-PassThru 매개 변수를 구현 하는 방법 및 ShouldProcess 및 ShouldContinue 메서드를 호출 하 여 사용자에 게 피드백을 요청 하는 방법을 보여 줍니다. 사용자 개체를 반환 하는 cmdlet에서 강제로 하려는 경우 PassThru 매개 변수 지정
- StopProcessSample02-특정 프로세스를 중지 하는 방법을 보여 줍니다.
- StopProcessSample03-매개 변수에 대 한 별칭을 선언 하는 방법과 와일드 카드를 지원 하는 방법을 보여 줍니다.
- StopProcessSample04-매개 변수 집합을 선언 하는 방법을 보여 줍니다 cmdlet은 입력으로 사용 하도록 설정 하는 기본 매개 변수를 지정 하는 방법을 사용 하는 개체입니다.

#### <a name="remoting-samples"></a>원격 샘플

- RemoteRunspace01-원격 연결을 설정 하는 데 사용 되는 원격 runspace를 만드는 방법을 보여 줍니다.
- RemoteRunspacePool01-에 원격 runspace 풀을 생성 하는 방법 및이 풀을 사용 하 여 여러 명령을 동시에 실행 하는 방법을 보여 줍니다.
- Serialization01-기존.NET 클래스를 살펴보고이 클래스의 선택한 공용 속성에서 정보가 직렬화/역직렬화에서 유지 되는지 확인 하는 방법을 보여 줍니다.
- Serialization02-기존.NET 클래스를 살펴보고 정보 클래스의 공용 속성에 사용할 수 없을 때이 클래스 인스턴스의 정보가 직렬화/역직렬화에서 유지 되는지 확인 하는 방법을 보여 줍니다.
- Serialization03-기존.NET 클래스를 살펴보고이 클래스의 파생된 클래스의 인스턴스 (리하이드레이션) 라이브.NET 개체로 역직렬화 됩니다 있는지 확인 하는 방법을 보여 줍니다.

#### <a name="event-samples"></a>이벤트 샘플

- Event01-ObjectEventRegistrationBase에서 파생 하 여 이벤트 등록 용 cmdlet을 만드는 방법을 보여 줍니다.
- Event02-표시 방법을 원격 컴퓨터에서 생성 되는 Windows PowerShell 이벤트 알림을 수신 하는 방법을 보여줍니다. Runspace 클래스를 통해 노출 되는 PSEventReceived 이벤트를 사용 합니다.

#### <a name="hosting-application-samples"></a>호스팅 애플리케이션 샘플

- Runspace01-PowerShell 클래스를 사용 하 여 실행 하는 방법을 보여 줍니다는 `Get-Process` cmdlet 동기적으로 합니다.
`Get-Process` cmdlet은 로컬 컴퓨터에서 실행 중인 각 프로세스에 대 한 프로세스 개체를 반환 합니다.
- Runspace02-PowerShell 클래스를 사용 하 여 실행 하는 방법을 보여 줍니다 합니다 `Get-Process` 고 `Sort-Object` cmdlet 동기적으로 합니다. `Get-Process` 로컬 컴퓨터에서 실행 중인 각 프로세스에 대 한 프로세스 개체를 반환 하는 cmdlet 및 `Sort-Object` 해당 Id 속성을 기반으로 개체를 정렬 합니다. 이러한 명령의 결과 DataGridView 컨트롤을 사용 하 여 표시 됩니다.
- Runspace03-PowerShell 클래스를 사용 하 여 스크립트를 동기적으로 실행 하는 방법과 종료 되지 않는 오류를 처리 하는 방법을 보여 줍니다. 스크립트는 프로세스 이름 목록을 받은 다음 해당 프로세스를 검색합니다. 스크립트를 실행할 때 생성된 종료되지 않는 오류를 포함하여 스크립트의 결과가 콘솔 창에 표시됩니다.
- Runspace04-PowerShell 클래스를 사용 하 여 명령을 실행 하는 방법 및 catch 하는 방법을 보여 줍니다. 명령을 실행 하는 경우 throw 되는 오류를 종료 합니다. 두 개의 명령이 실행되는데, 마지막 명령은 유효하지 않은 매개 변수 인수를 전달받습니다. 따라서 개체가 반환되지 않고 종료 오류가 발생합니다.
- Runspace05-runspace를 열 때 스냅인의 cmdlet을 사용할 수 있도록 InitialSessionState 개체에 스냅인을 추가 하는 방법을 보여 줍니다. 스냅인을 PowerShell 개체를 사용 하 여 동기적으로 실행 되는 Get-proc cmdlet (GetProcessSample01 샘플에서 정의 됨)를 제공 합니다.
- Runspace06-runspace를 열 때 모듈이 로드 되도록 InitialSessionState 개체에 모듈을 추가 하는 방법을 보여 줍니다. 모듈이는 PowerShell 개체를 사용 하 여 동기적으로 실행 되는 Get-proc cmdlet (GetProcessSample02 샘플에서 정의 됨)를 제공 합니다.
- Runspace07-runspace를 만들고 해당 runspace를 사용 하 여 PowerShell 개체를 사용 하 여 두 개의 cmdlet을 동기적으로 실행 하는 방법을 보여 줍니다.
- Runspace08-PowerShell 개체의 파이프라인에 명령 및 인수를 추가 하는 방법과 동기적으로 명령을 실행 하는 방법을 보여 줍니다.
- Runspace09-스크립트는 PowerShell 개체의 파이프라인에 추가 하는 방법과 비동기적으로 스크립트를 실행 하는 방법을 보여 줍니다. 이벤트는 스크립트의 출력을 처리하는 데 사용됩니다.
- Runspace10-기본 초기 세션 상태를 만드는 방법, cmdlet를 InitialSessionState 추가 하는 방법, 초기 세션 상태를 사용 하는 runspace를 만드는 방법 및 PowerShell 개체를 사용 하 여 명령을 실행 하는 방법을 보여 줍니다.
- Runspace11-ProxyCommand 클래스를 사용 하 여 기존 cmdlet을 호출 하지만 사용 가능한 매개 변수 집합을 제한 하는 프록시 명령을 만드는 방법을 보여 줍니다. 프록시 명령은 제한된 runspace를 만드는 데 사용되는 초기 세션 상태에 추가됩니다. 따라서 사용자가 프록시 명령을 통해서만 cmdlet의 기능에 액세스할 수 있습니다.
- PowerShell01-InitialSessionState 개체를 사용 하 여 제한 된 runspace를 만드는 방법을 보여 줍니다.
- PowerShell02-을 runspace 풀을 사용 하 여 여러 명령을 동시에 실행 하는 방법을 보여 줍니다.

#### <a name="host-samples"></a>호스트 샘플

- Host01-사용자 지정 호스트를 사용 하는 호스트 응용 프로그램을 구현 하는 방법을 보여 줍니다. 사용자 지정 호스트를 사용 하는 runspace를 만든이 샘플에서 및 PowerShell API를 사용 합니다 "종료"를 호출 하는 스크립트를 실행 합니다. 호스트 애플리케이션은 스크립트의 출력을 살펴보고 결과를 출력합니다.
- Host02-사용자 지정 호스트 구현과 함께 Windows PowerShell 런타임을 사용 하는 호스트 응용 프로그램을 작성 하는 방법을 보여 줍니다. 독일어로 실행은 호스트 문화권을 설정 하는 호스트 응용 프로그램을 `Get-Process` cmdlet으로 결과 표시 하 고 보았을 독일어에서 pwrsh.exe, 및 현재 날짜와 시간을 다음 출력을 사용 하 여 합니다.
- Host03-명령줄에서 명령을 읽고 명령을 실행 하 고 다음 콘솔에 결과 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다.
- Host04-명령줄에서 명령을 읽고 명령을 실행 하 고 다음 콘솔에 결과 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다. 이 호스트 애플리케이션은 사용자가 여러 선택 항목을 지정할 수 있는 프롬프트 표시도 지원합니다.
- Host05-명령줄에서 명령을 읽고 명령을 실행 하 고 다음 콘솔에 결과 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다. 또한이 호스트 응용 프로그램 사용 하 여 원격 컴퓨터에 대 한 호출을 지원 합니다 `Enter-PsSession` 고 `Exit-PsSession` cmdlet.
- Host06-명령줄에서 명령을 읽고 명령을 실행 하 고 다음 콘솔에 결과 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다. 또한 이 샘플에서는 토크나이저 API를 사용하여 사용자가 입력하는 텍스트의 색을 지정합니다.

#### <a name="provider-samples"></a>공급자 샘플

- AccessDBProviderSample01-CmdletProvider 클래스에서 직접 파생 되는 공급자 클래스를 선언 하는 방법을 보여 줍니다. 여기서는 참조용으로만 설명합니다.

- AccessDBProviderSample02-호출을 지원 하기 NewDrive 및 RemoveDrive 메서드를 덮어쓰는 방법을 보여 줍니다 합니다 `New-PSDrive` 고 `Remove-PSDrive` cmdlet. 이 샘플의 공급자 클래스 DriveCmdletProvider 클래스에서 파생 됩니다.

- AccessDBProviderSample03-호출을 지원 하기 GetItem 및 SetItem 메서드를 덮어쓰는 방법을 보여 줍니다 합니다 `Get-Item` 고 `Set-Item` cmdlet. 이 샘플의 공급자 클래스 ItemCmdletProvider 클래스에서 파생 됩니다.

- AccessDBProviderSample04-에 대 한 호출을 지원 하기 위해 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 합니다 `Copy-Item`, `Get-ChildItem`를 `New-Item`, 및 `Remove-Item` cmdlet. 이러한 메서드는 데이터 저장소에 컨테이너 항목이 포함될 때 구현해야 합니다. 컨테이너는 공통 부모 항목 아래에 있는 자식 항목 그룹입니다. 이 샘플의 공급자 클래스 ItemCmdletProvider 클래스에서 파생 됩니다.

- AccessDBProviderSample05-에 대 한 호출을 지원 하기 위해 컨테이너 메서드를 덮어쓰는 방법을 보여 줍니다 합니다 `Move-Item` 고 `Join-Path` cmdlet. 이러한 메서드는 사용자가 컨테이너 내의 항목을 이동해야 하고 데이터 저장소에 중첩된 컨테이너가 포함되는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스 NavigationCmdletProvider 클래스에서 파생 됩니다.

- AccessDBProviderSample06-에 대 한 호출을 지원 하기 위해 콘텐츠 메서드를 덮어쓰는 방법을 보여 줍니다 합니다 `Clear-Content`, `Get-Content`, 및 `Set-Content` cmdlet. 이러한 메서드는 사용자가 데이터 저장소에 있는 항목의 콘텐츠를 관리해야 하는 경우에 구현해야 합니다. 이 샘플의 공급자 클래스 NavigationCmdletProvider 클래스에서 파생 하 고 IContentCmdletProvider 인터페이스를 구현 합니다.
