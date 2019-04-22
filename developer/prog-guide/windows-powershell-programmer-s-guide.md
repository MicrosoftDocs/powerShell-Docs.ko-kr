---
title: Windows PowerShell 프로그래머&#39;가이드 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 75425fbd38141fc82dd834835912c357ecfa6d2b
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58920393"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell 프로그래머&#39;가이드

이 프로그래머 가이드는 시스템 관리자에 대 한 명령줄 관리 환경을 제공 하려는 개발자 대상으로 합니다. Windows PowerShell에는 대부분의 작업을 수행 하는 Windows PowerShell를 허용 하는 동안.NET 개체를 노출 하는 관리 명령을 작성 하는 간편한 방법을 제공 합니다.

기존 개발에서 파서를 매개 변수, 매개 변수 바인더, 필터 및 각 명령에 의해 노출 하는 다른 모든 기능을 작성 해야 합니다. Windows PowerShell 명령에 쓸 수를 쉽게 확인 하려면 다음을을 제공 합니다.

- 사용 하는 강력한 Windows PowerShell 런타임 (실행 엔진) 자체 파서 및 명령 매개 변수를 자동으로 바인딩하기 위한 메커니즘입니다.

- 서식 지정 하 고 명령줄 인터프리터 (CLI)를 사용 하 여 명령 결과 표시 하기 위한 유틸리티입니다.

- 저장 된 데이터에 액세스할 수 있도록 하는 높은 수준의 (Windows PowerShell 공급자)를 통해 기능을 지원 합니다.

  적은 비용으로 다양 한 명령이 나는 관리자에 게는 전체 명령줄 환경을 제공 하는 명령 집합으로.NET 개체를 나타낼 수 있습니다.

  다음 섹션에서는 핵심 Windows PowerShell 개념 및 용어를 설명합니다. 이러한 개념과 개발 시작 하기 전에 사용 약관을 잘 이해 합니다.

## <a name="about-windows-powershell"></a>Windows PowerShell에 대한 자세한 정보

Windows PowerShell 개발에서 명령 사용할 수 있는 여러 유형의 정의 합니다. 이러한 명령에 포함: 함수, 필터, 스크립트, 별칭 및 실행 파일 (응용 프로그램). 이 가이드에 설명 된 기본 명령 유형은 "cmdlet"을 호출 하는 간단 하 고 작은 명령을 합니다. Windows PowerShell cmdlet 집합을 제공 하 고 사용자 환경에 맞게 사용자 지정 cmdlet를 완벽 하 게 지원 합니다. Windows PowerShell 런타임이 cmdlet을 파이프라인을 사용 하는 것 처럼 모든 명령 유형을 처리 합니다.

명령 외에도 Windows PowerShell cmdlet의 특정 집합을 사용할 수 있도록 다양 한 사용자 지정 가능한 Windows PowerShell 공급자를 지원 합니다. 셸에서 Windows PowerShell이 제공 하는 호스트 응용 프로그램 (Windows PowerShell.exe) 내에서 작동 하지만 특정 요구 사항에 맞게 개발할 수 있는 사용자 지정 호스트 응용 프로그램에서 동일 하 게 액세스할 수 있습니다. 자세한 내용은 [Windows PowerShell 작동 방식](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)합니다.

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell Cmdlet

Cmdlet는 Windows PowerShell 환경에서 사용 되는 간단한 명령입니다. Windows PowerShell 런타임에 명령줄에 제공 되는 자동화 스크립트의 컨텍스트 내에서 이러한 cmdlet을 호출 하 고 Windows PowerShell 런타임에 호출을 프로그래밍 방식으로 Windows PowerShell Api를 통해 키를 누릅니다.

Cmdlet에 대 한 자세한 내용은 참조 하십시오 [Windows PowerShell Cmdlet 작성](../cmdlet/writing-a-windows-powershell-cmdlet.md)합니다.

### <a name="windows-powershell-providers"></a>Windows PowerShell 공급자

관리 작업을 수행 합니다 사용자 (예: 파일 시스템, Windows 레지스트리 또는 인증서 저장소)는 데이터 저장소에 저장 된 데이터를 검사 해야 할 수도 있습니다. Windows PowerShell은 이러한 작업을 더 쉽게 Windows 레지스트리와 같은 특정 데이터 저장소에 액세스 하는 데 사용할 수 있는 Windows PowerShell 공급자를 호출 하는 모듈로 정의 합니다. 각 공급자는 저장소에 데이터의 대칭 뷰를 사용자에 게 관련 된 cmdlet 집합을 지원 합니다.

Windows PowerShell에서는 여러 기본 Windows PowerShell 공급자를 제공합니다. 예를 들어 레지스트리 공급자는 탐색 및 조작 Windows 레지스트리를 지원합니다. 레지스트리 키 항목으로 표시 됩니다 하 고 레지스트리 값 속성으로 처리 됩니다.

에 설명 된 대로 사용자 고유의 Windows PowerShell 공급자를 작성 해야 할 수는 사용자가 액세스 해야 하는 데이터 저장소를 노출 하는 경우 [Windows PowerShell 공급자를 만드는](./how-to-create-a-windows-powershell-provider.md)합니다. 자세한 내용은 aboutWindows PowerShell 공급자에 대 한 참조 [Windows PowerShell 작동 방식](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)합니다.

### <a name="host-application"></a>호스트 응용 프로그램

Windows PowerShell에는 사용자와 상호 작용 하 고 콘솔 창을 사용 하 여 Windows PowerShell 런타임을 호스트 하는 콘솔 응용 프로그램을 기본 호스트 응용 프로그램이 powershell.exe를 포함 합니다.

드물게 있습니다 해야 Windows powershell의 경우 호스트 응용 프로그램 자체를 쓸 사용자 지정은 지원 되지만 합니다. 사용자 고유의 응용 프로그램을 해야 할 수 있습니다 하는 한 가지 경우에는 기본 호스트 응용 프로그램에서 제공 하는 인터페이스 보다 뛰어나며는 GUI 인터페이스에 대 한 요구 사항이 있는 경우는 합니다. 명령줄에서 GUI로 사용 하는 경우에 사용자 지정 응용 프로그램을 수도 있습니다. 자세한 내용은 [Windows PowerShell 호스트 응용 프로그램을 만드는 방법](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)합니다.

### <a name="windows-powershell-runtime"></a>Windows PowerShell 런타임

Windows PowerShell 런타임에 명령 처리를 구현 하는 실행 엔진입니다. 호스트 응용 프로그램 및 Windows PowerShell 명령 및 공급자 간의 인터페이스를 제공 하는 클래스를 포함 합니다. Windows PowerShell 런타임에 셸 및 명령 실행 작업 환경은 현재 Windows PowerShell 세션에 대 한 runspace 개체로 구현 됩니다. 작업 세부 정보를 참조 하세요 [Windows PowerShell 작동 방식](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)합니다.

### <a name="windows-powershell-language"></a>Windows PowerShell 언어

Windows PowerShell 언어는 스크립팅 함수와 명령을 호출 하는 메커니즘을 제공 합니다. 전체 스크립트 정보를 Windows PowerShell과 함께 제공 되는 Windows PowerShell 언어 참조를 참조 하세요.

### <a name="extended-type-system-ets"></a>확장된 형식 시스템 (ETS)

Windows PowerShell 다양 한.NET과 같은 다른 개체 및 XML 개체에 대 한 액세스를 제공합니다. 결과적으로 모든 개체 형식에 대 한 일반적인 추상화를 제공 하는 셸은 해당 확장된 형식 시스템 (ETS)를 사용 합니다. ETS 기능 대부분의 사용자에 게 투명 하 게 되었지만 스크립트 또는.NET 개발자는 다음 용도로 사용 합니다.

- 특정 개체의 멤버의 하위 집합을 봅니다. Windows PowerShell에 몇 가지 특정 개체 형식의 "조정된" 보기를 제공합니다.

- 기존 개체에 멤버를 추가 합니다.

- 직렬화 된 개체에 대 한 액세스.

- 쓰기 사용자 개체를 지정 합니다.

  ETS를 사용 하는 만들 수 있습니다 유연한 새 "형식" Windows PowerShell 언어와 호환 됩니다. 예를 들어 Windows PowerShell 언어 스크립팅에 적용 동일한 의미 체계를 사용 하 여 개체를 사용 하 여 작업에 개체를 계산 하는 경우 확인할 수 있다면.NET 개발자 라면 `true`합니다.

  ETS 및 Windows PowerShell 개체를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 개체 개념](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353)합니다.

## <a name="programming-for-windows-powershell"></a>Windows PowerShell에 대 한 프로그래밍

Windows PowerShell 명령, 공급자 및.NET Framework를 사용 하 여 다른 프로그램 모듈에 대 한 해당 코드를 정의 합니다. 수에 제한 되지 않습니다의 Microsoft Visual Studio를 사용 하 여 Windows PowerShell에 대 한 사용자 지정된 모듈을 만드는이 가이드에서 제공 하는 샘플은이 도구에서 실행할 알려져 있지만. 클래스 상속 및 특성의 사용을 지 원하는 모든.NET 언어를 사용할 수 있습니다. 경우에 따라 Windows PowerShell Api는 프로그래밍 언어를 제네릭 형식에 액세스할 수 있으려면 필요 합니다.

## <a name="programmers-reference"></a>프로그래머 참고 자료

Windows PowerShell에 대 한 개발 하는 경우, 참조를 [Windows PowerShell SDK](../windows-powershell-reference.md)합니다.

## <a name="getting-started-using-windows-powershell"></a>Windows PowerShell을 사용 하 여 시작

Windows PowerShell 셸을 사용 하 여 시작 하는 방법에 대 한 자세한 내용은 참조는 [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) Windows PowerShell을 사용 하 여 제공 합니다. 빠른 참조 세 번 접기 문서 cmdlet 사용에 대 한 입문서로도 제공 됩니다.

## <a name="contents-of-this-guide"></a>이 가이드의 내용

|항목|정의|
|-----------|----------------|
|[Windows PowerShell 공급자를 만드는 방법](./how-to-create-a-windows-powershell-provider.md)|이 섹션에는 Windows PowerShell 용 Windows PowerShell 공급자를 빌드하는 방법을 설명 합니다.|
|[Windows PowerShell 호스트 응용 프로그램을 만드는 방법](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)|이 섹션에서는 runspace를 조작 하는 호스트 응용 프로그램을 작성 하는 방법과 자체 사용자 지정 호스트를 구현 하는 호스트 응용 프로그램을 작성 하는 방법을 설명 합니다.|
|[Windows PowerShell 스냅인을 만드는 방법](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|이 섹션에는 어셈블리의 모든 cmdlet 및 공급자를 등록 하는 데 사용 되는 스냅인을 만드는 방법 및 사용자 지정 스냅인을 만드는 방법을 설명 합니다.|
|[콘솔 셸을 만드는 방법](./how-to-create-a-console-shell.md)|이 섹션에는 확장 가능 하지 않은 콘솔 셸을 만드는 방법을 설명 합니다.|
|[Windows PowerShell 개념](./windows-powershell-concepts.md)|이 섹션에서는 개발자의 관점에서 Windows PowerShell을 이해 하는 데 도움이 되는 개념 정보를 포함 합니다.|

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
