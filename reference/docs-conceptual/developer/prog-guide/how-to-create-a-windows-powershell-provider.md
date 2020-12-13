---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 공급자를 만드는 방법
description: Windows PowerShell 공급자를 만드는 방법
ms.openlocfilehash: 51f19bf0dfa5f976a5045ae1342730c8f22f695e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647480"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Windows PowerShell 공급자를 만드는 방법

이 섹션에서는 Windows PowerShell 공급자를 빌드하는 방법을 설명 합니다. Windows PowerShell 공급자를 두 가지 방법으로 고려할 수 있습니다. 사용자에 게 공급자는 저장 된 데이터 집합을 나타냅니다. 예를 들어 저장 된 데이터는 인터넷 정보 서비스 (IIS) 메타 베이스, Microsoft Windows 레지스트리, Windows 파일 시스템, Active Directory, Windows PowerShell에서 저장 한 변수 및 별칭 데이터 일 수 있습니다.

개발자에 게 Windows PowerShell 공급자는 사용자가 액세스 해야 하는 데이터와 사용자 간의 인터페이스입니다. 이 섹션에서 설명 하는 각 유형의 공급자는 Windows PowerShell 런타임에서 특정 cmdlet을 일반적인 방법으로 사용자에 게 노출 하는 데 사용할 수 있는 특정 기본 클래스 및 인터페이스 집합을 지원 합니다.

## <a name="providers-provided-by-windows-powershell"></a>Windows PowerShell에서 제공 하는 공급자

Windows PowerShell은 알려진 데이터 저장소에 액세스 하는 데 사용 되는 여러 공급자 (예: 파일 시스템 공급자, 레지스트리 공급자 및 별칭 공급자)를 제공 합니다. Windows PowerShell에서 제공 하는 공급자에 대 한 자세한 내용은 다음 명령을 사용 하 여 온라인 도움말에 액세스 합니다.

**PS>get-help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Windows PowerShell 경로를 사용 하 여 저장 된 데이터에 액세스

Windows powershell 공급자는 windows powershell 런타임 및 windows PowerShell 경로를 사용 하 여 프로그래밍 방식으로 명령에 액세스할 수 있습니다. 대부분의 경우 이러한 경로는 공급자를 통해 데이터에 직접 액세스 하는 데 사용 됩니다. 그러나 일부 경로는 cmdlet이 비 Windows PowerShell Api (응용 프로그래밍 인터페이스)를 사용 하 여 데이터에 액세스할 수 있도록 하는 공급자 내부 경로로 확인 될 수 있습니다. Windows powershell에서 windows powershell 공급자가 작동 하는 방식에 대 한 자세한 내용은 [Windows Powershell 작동 방법](/previous-versions/ms714658(v=vs.85))을 참조 하세요.

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Windows PowerShell 드라이브를 사용 하 여 공급자 Cmdlet 노출

Windows PowerShell 공급자는 가상 Windows PowerShell 드라이브를 사용 하 여 지원 되는 cmdlet을 노출 합니다.
Windows PowerShell은 Windows PowerShell 드라이브에 대해 다음 규칙을 적용 합니다.

- 드라이브 이름은 영숫자 시퀀스가 될 수 있습니다.
- 드라이브는 "root" 라는 경로의 모든 유효한 지점에서 지정할 수 있습니다.
- 파일 시스템 뿐만 아니라 저장 된 모든 데이터에 대해 드라이브를 구현할 수 있습니다.
- 각 드라이브는 자신의 현재 작업 위치를 유지 하므로 사용자는 드라이브 간을 이동할 때 컨텍스트를 유지할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용

다음 표에서는 서로를 구성 하는 코드 예제를 포함 하는 항목을 보여 줍니다. 두 번째 항목부터 Windows PowerShell 런타임으로 기본 Windows PowerShell 공급자를 초기화 하 고 초기화 하지 않을 수 있습니다. 다음 항목에서는 데이터에 액세스 하는 기능을 추가 하 고, 다음 항목에서는 데이터 조작을 위한 기능 (저장 된 데이터의 항목)을 추가 합니다.

|                                                    항목                                                    |                                                                                         정의                                                                                          |
| ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Windows PowerShell 공급자 설계](./designing-your-windows-powershell-provider.md)               | 이 항목에서는 Windows PowerShell 공급자를 구현 하기 전에 고려해 야 할 사항에 대해 설명 합니다. 사용 되는 Windows PowerShell 공급자 기본 클래스 및 인터페이스를 요약 합니다. |
| [기본 Windows PowerShell 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)           | 이 항목에서는 Windows PowerShell 런타임에서 공급자를 초기화 하 고 초기화 하지 않도록 허용 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.                                        |
| [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)           | 이 항목에서는 사용자가 Windows PowerShell 드라이브를 통해 데이터 저장소에 액세스할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.                                                |
| [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)             | 이 항목에서는 사용자가 데이터 저장소의 항목을 조작할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.                                                                  |
| [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)   | 이 항목에서는 사용자가 다중 계층 데이터 저장소에서 작업할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.                                                                        |
| [Windows PowerShell 탐색 공급자 만들기](./creating-a-windows-powershell-navigation-provider.md) | 이 항목에서는 사용자가 계층적 방식으로 데이터 저장소의 항목을 탐색할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.                                           |
| [Windows PowerShell 콘텐츠 공급자 만들기](./creating-a-windows-powershell-content-provider.md)       | 이 항목에서는 사용자가 데이터 저장소에 있는 항목의 내용을 조작할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.                                                       |
| [Windows PowerShell 속성 공급자 만들기](./creating-a-windows-powershell-property-provider.md)     | 이 항목에서는 사용자가 데이터 저장소에 있는 항목의 속성을 조작할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법을 보여 줍니다.                                                    |

## <a name="see-also"></a>참고 항목

[Windows PowerShell 작동 방법](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)
