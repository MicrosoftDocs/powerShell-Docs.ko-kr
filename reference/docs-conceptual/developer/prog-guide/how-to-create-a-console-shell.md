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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360272"
---
# <a name="how-to-create-a-console-shell"></a>콘솔 셸을 만드는 방법

Windows PowerShell은 확장 가능 하지 않은 콘솔 셸을 만드는 데 사용 되는 셸 만들기 도구 ("키트" 라고도 함)를 제공 합니다. 이 새로운 도구를 사용 하 여 만든 셸을 나중에 Windows PowerShell 스냅인을 통해 확장할 수 없습니다.

## <a name="syntax"></a>구문

다음은 파일에서 만들기-셸을 실행 하는 데 사용 되는 구문입니다.

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

다음은 Shell의 매개 변수에 대 한 간단한 설명입니다.

> [!CAUTION]
> 어셈블리에 대 한 UNC 경로는 Shell에서 지원 되지 않습니다.

|매개 변수|설명|
|---------------|-----------------|
|-out n .exe|필수. 생성할 셸의 이름입니다. 이 매개 변수의 일부로 경로가 지정 됩니다.<br /><br /> 지정 하지 않으면 shell은이 값에 ".exe"를 추가 합니다. **주의:**  참조 된 .dll 파일과 동일한 이름의 출력 파일을 만들지 마십시오. 이 작업을 수행 하는 경우 셸 도구는 동일한 이름으로 .cs 파일을 만듭니다 .이 파일은 cmdlet 소스 코드가 포함 된 .cs 파일을 덮어씁니다.|
|-namespace ns|필수. Runspace가 생성 하 고 컴파일하는 파생 된 [Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) 클래스에 사용할 네임 스페이스입니다.|
|-lib libdirectory1 [, libdirectory2,..]|Windows PowerShell 어셈블리, `reference` 매개 변수로 지정 된 어셈블리, 다른 어셈블리에서 간접적으로 참조 하는 어셈블리 및 .NET 시스템 어셈블리를 포함 하 여 .NET 어셈블리를 검색 하는 디렉터리입니다.|
|-reference c a 1 [, ca2,...]|셸에 포함할 어셈블리를 쉼표로 구분한 목록입니다. 이러한 어셈블리에는 모든 cmdlet 및 공급자 어셈블리와 함께 로드 해야 하는 리소스 어셈블리가 포함 됩니다. 이 매개 변수를 지정 하지 않으면 Windows PowerShell에서 제공 하는 핵심 cmdlet 및 공급자만 포함 된 셸이 생성 됩니다.<br /><br /> 어셈블리는 전체 경로를 사용 하 여 지정할 수 있습니다. 그렇지 않으면 `lib` 매개 변수에 지정 된 경로를 사용 하 여 검색 됩니다.|
|-formatdata f. types.ps1xml [, fd2. types.ps1xml,...]|셸에 포함할 형식 데이터의 쉼표로 구분 된 목록입니다. 이 매개 변수를 지정 하지 않으면 Windows PowerShell에서 제공 하는 형식 데이터만 포함 하는 셸이 생성 됩니다.|
|-update-typedata td1 types.ps1xml [, td2. types.ps1xml,...]|셸에 포함할 데이터 형식의 쉼표로 구분 된 목록입니다. 이 매개 변수를 지정 하지 않으면 Windows PowerShell에서 제공 하는 형식 데이터만 포함 하는 셸이 생성 됩니다.|
|-source c1.cs [, c2.cs,...]|셸을 빌드하는 데 필요한 소스 코드를 포함 하는 셸 개발자가 제공 하는 파일의 이름입니다.<br /><br /> 소스 코드 파일에는 다음 소스 코드가 포함 될 수 있습니다.<br /><br /> -기본 권한 부여 관리자를 재정의 하는 권한 부여 관리자 구현입니다. 이는 어셈블리로 컴파일될 수도 있습니다.<br />-어셈블리 정보 특성 선언 (예: e, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, System.reflection.assemblyinformationalversionattribute>, Assembly제품 특성 및) AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|권한 부여 관리자 구현을 포함 하는 형식입니다. 이는 소스 코드에서 정의 되거나 어셈블리로 컴파일될 수 있습니다 (`reference` 매개 변수로 지정). 이 매개 변수를 지정 하지 않으면 기본 보안 관리자가 사용 됩니다. 값은 네임 스페이스를 포함 한 전체 형식 이름 이어야 합니다.|
|-win32icon i .ico|셸의 .exe 파일에 대 한 아이콘입니다. 지정 하지 않으면 셸에는 c # 컴파일러에 포함 된 아이콘 (있는 경우)이 포함 됩니다.|
|-initscript p. ps1|셸의 시작 프로필입니다. 파일은 "있는 그대로" 포함 되어 있습니다. -셸에서 유효성 검사를 수행 하지 않습니다.|
|-builtinscript s1. ps1 [, s2. ps1,...]|셸에 대 한 기본 제공 스크립트 목록입니다. 이러한 스크립트는 경로의 스크립트 이전에 검색 되며, 셸을 빌드한 후에는 해당 콘텐츠를 변경할 수 없습니다.<br /><br /> 파일은 "있는 그대로" 포함 되어 있습니다. -셸에서 유효성 검사를 수행 하지 않습니다.|
|-resource resourcefile|셸에 대 한 도움말 및 배너 리소스를 포함 하는 .txt 파일입니다. 첫 번째 리소스는 ShellHelp로 이름이 지정 되 고, `help` 매개 변수를 사용 하 여 셸을 호출 하는 경우 표시 되는 텍스트를 포함 합니다. 두 번째 리소스는 ShellBanner 이름이 지정 되 고, 대화형 모드에서 셸이 시작 될 때 표시 되는 텍스트 및 저작권 정보를 포함 합니다.<br /><br /> 이 매개 변수를 제공 하지 않거나 이러한 리소스가 없으면 일반 도움말과 배너가 사용 됩니다.|
|-cscflags cscFlags|C# 컴파일러 (csc.exe)에 전달 되어야 하는 플래그입니다. 이러한 기능은 변경 되지 않은 상태로 전달 됩니다. 이 매개 변수에 공백이 포함 되어 있으면 큰따옴표로 묶어야 합니다.|
|-?<br /><br /> -도움말|저작권 메시지와 셸 명령줄 옵션을 표시 합니다.|
|-verbose|셸이 만들어지는 동안 자세한 정보를 표시 합니다.|

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)