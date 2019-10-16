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
ms.openlocfilehash: 44a9c970d32dc6f98456227f8b02101280541dd9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360052"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell 프로그래머&#39;가이드

이 프로그래머 가이드는 시스템 관리자를 위한 명령줄 관리 환경을 제공 하는 데 관심이 있는 개발자를 대상으로 합니다. Windows PowerShell은 Windows PowerShell에서 대부분의 작업을 수행할 수 있도록 하는 동시에 .NET 개체를 노출 하는 관리 명령을 빌드하는 간단한 방법을 제공 합니다.

기존의 명령 개발에서는 매개 변수 파서, 매개 변수 바인더, 필터 및 각 명령에 의해 노출 되는 기타 모든 기능을 작성 해야 합니다. Windows PowerShell은 명령을 쉽게 작성할 수 있도록 다음과 같은 기능을 제공 합니다.

- 자체 파서가 있는 강력한 Windows PowerShell 런타임 (실행 엔진) 및 명령 매개 변수를 자동으로 바인딩하는 메커니즘이 포함 되어 있습니다.

- 명령줄 인터프리터 (CLI)를 사용 하 여 명령 결과를 포맷 하 고 표시 하는 유틸리티입니다.

- 저장 된 데이터에 쉽게 액세스할 수 있도록 하는 높은 수준의 기능 (Windows PowerShell 공급자를 통해)을 지원 합니다.

  적은 비용으로 관리자에 게 완전 한 명령줄 환경을 제공 하는 명령 집합 또는 다양 한 명령으로 .NET 개체를 나타낼 수 있습니다.

  다음 섹션에서는 Windows PowerShell의 주요 개념 및 용어에 대해 설명 합니다. 개발을 시작 하기 전에 이러한 개념과 용어를 숙지 합니다.

## <a name="about-windows-powershell"></a>Windows PowerShell에 대한 자세한 정보

Windows PowerShell은 개발에 사용할 수 있는 여러 가지 유형의 명령을 정의 합니다. 이러한 명령에는 함수, 필터, 스크립트, 별칭 및 실행 파일 (응용 프로그램)이 포함 됩니다. 이 가이드에서 설명 하는 기본 명령 유형은 "cmdlet" 이라는 간단한 작은 명령입니다. Windows PowerShell은 cmdlet 집합을 furnishes 하 고 사용자 환경에 맞게 cmdlet 사용자 지정을 완벽 하 게 지원 합니다. Windows PowerShell 런타임은 파이프라인을 사용 하 여 cmdlet과 마찬가지로 모든 명령 유형을 처리 합니다.

명령 외에도 Windows PowerShell은 특정 cmdlet 집합을 사용할 수 있도록 하는 다양 한 사용자 지정 가능 Windows PowerShell 공급자를 지원 합니다. Shell은 Windows PowerShell에서 제공 하는 호스트 응용 프로그램 (Windows PowerShell .exe) 내에서 작동 하지만 특정 요구 사항을 충족 하기 위해 개발할 수 있는 사용자 지정 호스트 응용 프로그램 에서도 동일 하 게 액세스할 수 있습니다. 자세한 내용은 [Windows PowerShell의 작동 방식](/previous-versions//ms714658(v=vs.85))을 참조 하세요.

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell Cmdlet

Cmdlet은 Windows PowerShell 환경에서 사용 되는 간단한 명령입니다. Windows powershell 런타임은 명령줄에서 제공 되는 자동화 스크립트의 컨텍스트 내에서 이러한 cmdlet을 호출 하 고 windows powershell 런타임은 Windows PowerShell Api를 통해 프로그래밍 방식으로 호출 합니다.

Cmdlet에 대 한 자세한 내용은 [Windows PowerShell Cmdlet 작성](../cmdlet/writing-a-windows-powershell-cmdlet.md)을 참조 하세요.

### <a name="windows-powershell-providers"></a>Windows PowerShell 공급자

관리 작업을 수행 하는 동안 사용자는 데이터 저장소 (예: 파일 시스템, Windows 레지스트리 또는 인증서 저장소)에 저장 된 데이터를 검사 해야 할 수 있습니다. 이러한 작업을 더 쉽게 수행 하기 위해 windows PowerShell은 windows 레지스트리와 같은 특정 데이터 저장소에 액세스 하는 데 사용할 수 있는 Windows PowerShell 공급자 라는 모듈을 정의 합니다. 각 공급자는 사용자에 게 저장소에 있는 데이터의 대칭 보기를 제공 하는 일련의 관련 cmdlet을 지원 합니다.

Windows PowerShell은 몇 가지 기본 Windows PowerShell 공급자를 제공 합니다. 예를 들어 레지스트리 공급자는 Windows 레지스트리 탐색 및 조작을 지원 합니다. 레지스트리 키는 항목으로 표시 되 고 레지스트리 값은 속성으로 처리 됩니다.

사용자가 액세스 해야 하는 데이터 저장소를 노출 하는 경우 [Windows Powershell 공급자 만들기](./how-to-create-a-windows-powershell-provider.md)에 설명 된 대로 사용자 고유의 windows powershell 공급자를 작성 해야 할 수 있습니다. PowerShell 공급자에 대 한 자세한 내용은 [Windows Powershell 작동 방법](/previous-versions//ms714658(v=vs.85))aboutWindows을 참조 하세요.

### <a name="host-application"></a>호스트 응용 프로그램

Windows PowerShell에는 사용자와 상호 작용 하 고 콘솔 창을 사용 하 여 Windows PowerShell 런타임을 호스트 하는 콘솔 응용 프로그램에 해당 하는 기본 호스트 응용 프로그램 wsdl.exe가 포함 되어 있습니다.

사용자 지정이 지원 되기는 하지만 Windows PowerShell에 대 한 고유한 호스트 응용 프로그램을 작성 해야 하는 경우는 거의 없습니다. 사용자 고유의 응용 프로그램이 필요할 수 있는 한 가지 경우는 기본 호스트 응용 프로그램에서 제공 하는 인터페이스 보다 풍부한 GUI 인터페이스를 요구 하는 경우입니다. 명령줄에서 GUI를 기반으로 하는 경우 사용자 지정 응용 프로그램을 사용할 수도 있습니다. 자세한 내용은 [Windows PowerShell 호스트 응용 프로그램을 만드는 방법](/powershell/developer/hosting/writing-a-windows-powershell-host-application)을 참조 하세요.

### <a name="windows-powershell-runtime"></a>Windows PowerShell 런타임

Windows PowerShell runtime은 명령 처리를 구현 하는 실행 엔진입니다. 호스트 응용 프로그램과 Windows PowerShell 명령 및 공급자 간의 인터페이스를 제공 하는 클래스를 포함 합니다. Windows PowerShell 런타임은 현재 Windows PowerShell 세션의 runspace 개체로 구현 됩니다 .이 개체는 셸과 명령이 실행 되는 환경입니다. 작업 세부 정보 [는 Windows PowerShell의 작동 방식](/previous-versions//ms714658(v=vs.85))을 참조 하세요.

### <a name="windows-powershell-language"></a>Windows PowerShell 언어

Windows PowerShell 언어는 명령을 호출 하는 스크립팅 함수 및 메커니즘을 제공 합니다. 전체 스크립팅 정보는 windows PowerShell과 함께 제공 되는 Windows PowerShell 언어 참조를 참조 하세요.

### <a name="extended-type-system-ets"></a>확장 유형 시스템 (추가)

Windows PowerShell은 .NET 및 XML 개체와 같은 다양 한 개체에 대 한 액세스를 제공 합니다. 결과적으로 모든 개체 형식에 대 한 일반적인 추상화를 제공 하기 위해 셸에서는 해당 확장 유형 시스템 (추가)을 사용 합니다. 대부분의 작업 기능은 사용자에 게 투명 하지만 스크립트나 .NET 개발자는 다음 용도로 사용 됩니다.

- 특정 개체의 멤버 하위 집합 보기 Windows PowerShell은 몇 가지 특정 개체 유형에 대 한 "조정 된" 보기를 제공 합니다.

- 기존 개체에 멤버 추가

- Serialize 된 개체에 액세스 합니다.

- 사용자 지정 개체 작성

  사용자를 사용 하 여 Windows PowerShell 언어와 호환 되는 유연한 새 "형식"을 만들 수 있습니다. .NET 개발자 인 경우 스크립트에 적용 되는 것과 같은 의미 체계를 사용 하 여 개체 작업을 수행할 수 있습니다. 예를 들어 개체가-0 @no__t로 계산 되는지 여부를 확인할 수 있습니다.

  추가 정보 및 Windows PowerShell에서 개체를 사용 하는 방법에 대 한 자세한 내용은 [Windows Powershell 개체 개념](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6)을 참조 하십시오.

## <a name="programming-for-windows-powershell"></a>Windows PowerShell 프로그래밍

Windows PowerShell은 .NET Framework를 사용 하 여 명령, 공급자 및 기타 프로그램 모듈에 대 한 코드를 정의 합니다. 이 가이드에서 제공 하는 샘플은이 도구에서 실행 되는 것으로 알려져 있지만 Windows PowerShell에 대 한 사용자 지정 모듈을 만드는 데 Microsoft Visual Studio를 사용 하는 것으로 제한 되지 않습니다. 클래스 상속 및 특성 사용을 지 원하는 모든 .NET 언어를 사용할 수 있습니다. 경우에 따라 Windows PowerShell Api에는 제네릭 형식에 액세스할 수 있는 프로그래밍 언어가 필요 합니다.

## <a name="programmers-reference"></a>프로그래머 참조

Windows PowerShell 용 개발 시 참조는 [Windows POWERSHELL SDK](../windows-powershell-reference.md)를 참조 하세요.

## <a name="getting-started-using-windows-powershell"></a>Windows PowerShell을 사용 하 여 시작

Windows PowerShell shell 사용을 시작 하는 방법에 대 한 자세한 내용은 windows powershell과 함께 제공 되는 windows powershell [시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell) 을 참조 하세요. 빠른 참조 3-접기 문서도 cmdlet 사용 입문으로 제공 됩니다.

## <a name="contents-of-this-guide"></a>이 가이드의 내용

|항목|정의|
|-----------|----------------|
|[Windows PowerShell 공급자를 만드는 방법](./how-to-create-a-windows-powershell-provider.md)|이 섹션에서는 windows powershell 용 Windows PowerShell 공급자를 빌드하는 방법을 설명 합니다.|
|[Windows PowerShell 호스트 응용 프로그램을 만드는 방법](/powershell/developer/hosting/writing-a-windows-powershell-host-application)|이 섹션에서는 runspace를 조작 하는 호스트 응용 프로그램을 작성 하는 방법과 자체 사용자 지정 호스트를 구현 하는 호스트 응용 프로그램을 작성 하는 방법을 설명 합니다.|
|[Windows PowerShell 스냅인을 만드는 방법](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|이 섹션에서는 어셈블리의 모든 cmdlet 및 공급자를 등록 하는 데 사용 되는 스냅인을 만드는 방법과 사용자 지정 스냅인을 만드는 방법에 대해 설명 합니다.|
|[콘솔 셸을 만드는 방법](./how-to-create-a-console-shell.md)|이 섹션에서는 확장할 수 없는 콘솔 셸을 만드는 방법을 설명 합니다.|
|[Windows PowerShell 개념](./windows-powershell-concepts.md)|이 섹션에는 개발자의 관점에서 Windows PowerShell을 이해 하는 데 도움이 되는 개념 정보가 포함 되어 있습니다.|

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
