---
title: 콘솔 셸을 만드는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853499"
---
# <a name="how-to-create-a-console-shell"></a>콘솔 셸을 만드는 방법

Windows PowerShell의 "확인-키트"는 확장할 수 있는 콘솔 셸을 만드는 데 사용 되는 라고도 확인 셸 도구를 제공 합니다. 이 새 도구를 사용 하 여 만든 셸에 Windows PowerShell 스냅인을 통해 나중에 확장할 수 없습니다.

## <a name="syntax"></a>구문

확인-파일 내에서 셸 확인을 실행 하는 데 구문은 다음과 같습니다.

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>매개 변수

간략 한 설명은 확인 셸의 매개 변수는 다음과 같습니다.

> [!CAUTION]
> 어셈블리에 대 한 UNC 경로 확인 Shell에서 지원 되지 않습니다.

|매개 변수|설명|
|---------------|-----------------|
|-out n.exe|필수 사항입니다. 생성 하도록 셸에의 이름입니다. 경로이 매개 변수의 일부로 지정 됩니다.<br /><br /> 확인 셸이 지정 되지 않은 경우이 값에 ".exe"가 추가 됩니다. **주의:**  참조 된.dll 파일과 같은 이름의 출력 파일을 만들지 마십시오. 이 경우 셸 확인 도구 cmdlet 소스 코드에는.cs 파일을 덮어쓰게 되는 동일한 이름을 가진.cs 파일을 만듭니다.|
|네임 스페이스 ns|필수 사항입니다. 파생에 사용할 네임 스페이스 [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) 클래스 확인 키트를 생성 하 고 컴파일합니다.|
|-lib libdirectory1[,libdirectory2,..]|.NET 어셈블리, 어셈블리를 비롯 한 Windows PowerShell에 의해 지정 된 어셈블리를 검색 하는 디렉터리를 `reference` 매개 변수, 다른 어셈블리에서 간접적으로 참조 되는 어셈블리 및.NET 시스템 어셈블리입니다.|
|-참조 ca1.dll[,ca2.dll,...]|셸에서 포함 어셈블리의 쉼표로 구분 된 목록입니다. 이러한 어셈블리는 모든 cmdlet 및 공급자 어셈블리 뿐만 아니라 로드 해야 하는 리소스 어셈블리를 포함 합니다. 이 매개 변수를 지정 하지 않으면 다음 셸을 생성 됩니다 핵심 cmdlet 및 Windows PowerShell에서 제공 하는 공급자를 포함 하는 합니다.<br /><br /> 전체 경로 사용 하 여 어셈블리를 지정할 수 있습니다, 지정 된 경로 사용 하 여에 대 한 검색할 수이 고, 그렇지는 `lib` 매개 변수입니다.|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|셸에서 포함할 형식 데이터의 쉼표로 구분 된 목록입니다. 이 매개 변수를 지정 하지 않으면 다음 셸을 생성 됩니다만 Windows PowerShell에서 제공 된 형식 데이터를 포함 하는 합니다.|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|셸에서 포함 하도록 데이터 형식의 쉼표로 구분 된 목록입니다. 이 매개 변수를 지정 하지 않으면 다음 셸을 생성 됩니다만 Windows PowerShell에서 제공 된 유형 데이터를 포함 하는 합니다.|
|-원본 c1.cs [, c2.cs,...]|셸을 빌드하는 데 필요한 소스 코드를 포함 하는 셸 개발자가 제공한 파일의 이름입니다.<br /><br /> 소스 코드 파일의 다음 소스 코드를 포함할 수 있습니다.<br /><br /> 기본 권한 부여 관리자를 재정의 하는-권한 부여 관리자 구현입니다. (이 수도 제공 어셈블리로 컴파일됩니다.)<br />어셈블리 정보 특성 선언: AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, 및 AssemblyTrademarkAttribute 합니다.|
|-권한 authorizationManagerType|권한 부여 관리자 구현을 포함 하는 형식입니다. 소스 코드에 정의 된 또는 어셈블리로 컴파일할 수 수 있습니다 (지정 된는 `reference` 매개 변수). 이 매개 변수를 지정 하지 않으면 기본 보안 관리자가 사용 됩니다. 값 전체 형식 이름, 네임 스페이스를 포함 해야 합니다.|
|-win32icon i.ico|셸에 대 한.exe 파일에 대 한 아이콘입니다. 지정 하지 않으면 셸에서 c# 컴파일러 (있는 경우)를 포함 하는 아이콘을 해야 다음 합니다.|
|-initscript p.ps1|셸에 대 한 시작 프로필입니다. 파일이 포함 되어 "으로-는"; 유효성을 확인 하지 않고 셸 확인 하면 됩니다.|
|-builtinscript s1.ps1[,s2.ps1,...]|목록 셸에 대 한 기본 제공 스크립트입니다. 스크립트 경로에 하기 전에 이러한 스크립트 검색 및 셸 빌드될 때 해당 콘텐츠를 변경할 수 없습니다.<br /><br /> 파일이 포함 된 "으로-는"; 유효성을 확인 하지 않고 셸 확인 하면 됩니다.|
|-리소스 resourcefile.txt|셸에 대 한 도움말 및 배너 리소스가 포함 된.txt 파일입니다. 첫 번째 리소스 ShellHelp, 이름이 고 셸을 사용 하 여 호출 하는 경우 표시 되는 텍스트를 포함 합니다 `help` 매개 변수입니다. 두 번째 리소스 이름이 ShellBanner를 하 고 텍스트 및 대화형 모드에서 셸이 시작 될 때 표시 되는 저작권 정보를 포함 합니다.<br /><br /> 이 매개 변수를 지정 하지 않은 경우 이러한 리소스에 표시 되지 않으면 일반 도움말 및 배너 사용 됩니다.|
|-cscflags cscFlags|에 전달 되어야 하는 플래그를 C# 컴파일러 (csc.exe). 이 변경 하지 않고 통과 합니다. 이 매개 변수 공간에 포함 된 경우 큰따옴표로 묶어야 합니다.|
|-?<br /><br /> -도움말|저작권 메시지 및 확인 셸 명령줄 옵션을 표시합니다.|
|-verbose|셸을 만드는 동안 자세한 정보를 표시 합니다.|

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)