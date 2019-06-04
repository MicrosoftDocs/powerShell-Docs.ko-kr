---
title: Windows PowerShell 공급자를 만드는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 06910f32752668f13400f9be0767a2179133df04
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081753"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Windows PowerShell 공급자를 만드는 방법

이 섹션에는 Windows PowerShell 공급자를 빌드하는 방법을 설명 합니다. Windows PowerShell 공급자는 두 가지 방법으로 간주할 수 있습니다. 사용자에 게 공급자는 저장 된 데이터의 집합을 나타냅니다. 예를 들어 저장된 된 데이터는 인터넷 정보 서비스 (IIS) 메타 베이스, Microsoft Windows 레지스트리, Windows 파일 시스템, Active Directory 및 Windows PowerShell에서 저장 된 변수 및 별칭 데이터 수 있습니다.

개발자가 Windows PowerShell 공급자는 사용자와 사용자가 액세스 해야 하는 데이터 간의 인터페이스입니다. 이러한 관점에서이 섹션에 설명 된 공급자의 각 유형에 특정 기본 클래스 및 일반적인 방식으로 사용자에 게 특정 cmdlet을 노출 하는 Windows PowerShell 런타임에 사용할 수 있는 인터페이스 집합을 지원 합니다.

## <a name="providers-provided-by-windows-powershell"></a>Windows PowerShell에서 제공 하는 공급자

Windows PowerShell 알려진된 데이터 저장소에 액세스 하는 데 사용 되는 여러 공급자 (예: 파일 시스템 공급자, 레지스트리 공급자 및 별칭 공급자)를 제공 합니다. Windows PowerShell에서 제공 하는 공급자에 대 한 자세한 내용은 온라인 도움말에 액세스 하려면 다음 명령을 사용 합니다.

**PS > about_providers 도움말 얻기**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Windows PowerShell 경로 사용 하 여 저장된 된 데이터에 액세스

Windows PowerShell 공급자는 Windows PowerShell 런타임에 프로그래밍 방식으로 Windows PowerShell 경로 사용 하 여 명령에 액세스할 수 있습니다. 대부분의 경우 이러한 경로 공급자를 통해 데이터를 직접 액세스에 사용 됩니다. 그러나 일부 경로 데이터에 액세스 하려면 Windows PowerShell이 아닌 Api (응용 프로그래밍 인터페이스)를 사용 하는 cmdlet을 사용할 수 있는 공급자-내부 경로를 확인할 수 있습니다. Windows PowerShell 공급자를 Windows PowerShell 내에서 작동 하는 방법에 대 한 자세한 내용은 참조 하십시오 [Windows PowerShell 작동 방식](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)합니다.

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>드라이브 공급자 Cmdlet Windows PowerShell을 사용 하 여 노출

Windows PowerShell 공급자는 가상 Windows PowerShell 드라이브를 사용 하 여 지원 되는 cmdlet을 제공 합니다. Windows PowerShell에는 다음 Windows PowerShell 드라이브를 규칙에 적용 됩니다.

- 드라이브의 이름에는 영숫자 시퀀스 수 있습니다.

- "Root" 라는 경로 올바른 시점에서 드라이브를 지정할 수 있습니다.

- 파일 시스템 뿐 아니라 저장 된 모든 데이터에 대 한 드라이브를 구현할 수 있습니다.

- 각 드라이브는 드라이브 간에 이동 하는 경우 컨텍스트를 보존할 수 있도록 자신의 현재 작업 위치를 유지 합니다.

## <a name="in-this-section"></a>이 섹션의 내용

다음 표에서 서로 토대로 하는 코드 예제를 포함 하는 항목을 나열 합니다. 두 번째 항목 부터는 기본 Windows PowerShell 공급자를 초기화 하 고 Windows PowerShell 런타임에 의해 초기화 되지 않은 수의 데이터에 액세스 하기 위한 기능을 추가 하는 다음 항목, 데이터 (조작 기능을 추가 하는 다음 항목 항목에 저장된 된 데이터), 등입니다.

|항목|정의|
|-----------|----------------|
|[Windows PowerShell 공급자를 디자인합니다.](./designing-your-windows-powershell-provider.md)|이 항목에서는 Windows PowerShell 공급자를 구현 하기 전에 고려해 야 하는 작업을 설명 합니다. Windows PowerShell 공급자에 대 한 기본 클래스 및 인터페이스에 사용 되는 요약 합니다.|
|[기본 Windows PowerShell 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)|이 항목에서는 Windows PowerShell 런타임 초기화 하 고 공급자를 초기화 취소할 수 있도록 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.|
|[Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)|이 항목에는 Windows PowerShell 드라이브를 통해 데이터 저장소에 액세스할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.|
|[Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)|이 항목에는 데이터 저장소에서 항목을 조작할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.|
|[Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)|이 항목에서는 multilayer 데이터 저장소에서 작업할 수 있도록 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.|
|[Windows PowerShell 탐색 공급자 만들기](./creating-a-windows-powershell-navigation-provider.md)|이 항목에서는 사용자를 계층적 방식으로 데이터 저장소의 항목을 탐색할 수 있도록 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.|
|[Windows PowerShell 콘텐츠 공급자 만들기](./creating-a-windows-powershell-content-provider.md)|이 항목에는 데이터 저장소에 있는 항목의 콘텐츠를 조작할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.|
|[Windows PowerShell 속성 공급자 만들기](./creating-a-windows-powershell-property-provider.md)|이 항목에는 데이터 저장소에 있는 항목의 속성을 조작할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.|

## <a name="see-also"></a>참고 항목

[Windows PowerShell의 작동 원리](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)
