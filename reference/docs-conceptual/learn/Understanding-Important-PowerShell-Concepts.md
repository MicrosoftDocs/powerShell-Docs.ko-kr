---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: 중요한 PowerShell 개념 이해
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: fad64563d1a7a6abd4f0e430331f81f91f43d312
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402175"
---
# <a name="understanding-important-powershell-concepts"></a>중요한 PowerShell 개념 이해

PowerShell 디자인은 다양한 환경의 개념을 통합합니다. 이러한 개념 중 일부는 셸 또는 프로그래밍 환경을 사용하는 사용자에게는 친숙할 것입니다. 그러나 모든 개념을 잘 아는 사용자는 거의 없을 것입니다. 이러한 개념 중 일부를 살펴보면 셸에 대한 전반적인 유용한 정보를 얻을 수 있습니다.

## <a name="output-is-object-based"></a>개체 기반의 출력

기존 명령줄 인터페이스와 달리 PowerShell cmdlet은 개체를 처리하도록 디자인되어 있습니다.
개체는 화면에 표시되는 문자열 이상의 의미를 갖는 구조화된 정보입니다. 명령 출력에는 필요할 때 사용할 수 있는 추가 정보가 항상 포함됩니다.

이전에 텍스트 처리 도구를 사용하여 데이터를 처리한 경우 PowerShell에서는 이러한 도구가 다르게 동작한다는 것을 알게 될 것입니다. 대부분의 경우 텍스트 처리 도구를 사용하여 특정 정보를 추출할 필요가 없습니다. 표준 PowerShell 개체 구문을 사용하여 데이터 부분에 직접 액세스할 수 있습니다.

## <a name="the-command-family-is-extensible"></a>확장 가능한 명령 패밀리

**cmd.exe**와 같은 인터페이스에서는 기본 제공 명령 집합을 직접 확장할 수 없습니다. **cmd.exe**에서 실행되는 외부 명령줄 도구를 만들 수 있습니다. 하지만 이러한 외부 도구에는 도움말 통합과 같은 서비스가 없습니다. **cmd.exe**는 이러한 외부 도구가 유효한 명령이라는 사실을 자동으로 알지 못합니다.

PowerShell의 네이티브 명령은 *cmdlet*(command-lets이라고 읽음)으로 알려져 있습니다. 컴파일된 코드 또는 스크립트를 사용하여 사용자 고유의 cmdlet 모듈과 함수를 만들 수 있습니다. 모듈은 셸에 cmdlet 및 공급자를 추가할 수 있습니다. 또한 PowerShell은 UNIX 셸 스크립트 및 **cmd.exe** 배치 파일과 유사한 스크립트를 지원합니다.

## <a name="powershell-handles-console-input-and-display"></a>Powershell로 콘솔 입력 및 표시 처리

사용자가 명령을 입력하면 PowerShell은 항상 이 명령줄 입력을 직접 처리합니다. 또한 PowerShell은 화면에 표시되는 출력의 형식을 지정합니다. 이러한 차이점은 각 cmdlet에 대해 필요한 작업을 줄여주므로 중요합니다. 또한 사용자가 항상 어떤 cmdlet으로도 동일한 방식으로 작업할 수 있도록 합니다. 따라서 cmdlet 개발자는 명령줄 인수를 구문 분석하거나 출력 형식을 지정하기 위해 코드를 작성할 필요가 없습니다.

이전의 명령줄 도구는 도움말을 요청하고 표시하는 자체 구성을 갖습니다. 일부 명령줄 도구는 **/?** 를 사용하여 도움말 표시를 트리거하고, 일부 명령줄 도구는 **-?** 또는 **/H**뿐 아니라 심지어 **//** 를 사용하여 도움말 표시를 트리거합니다. 또한 일부 명령줄 도구는 콘솔 화면 대신 GUI 창에 도움말을 표시합니다. 사용자가 잘못된 매개 변수를 사용할 경우 이러한 도구는 사용자의 입력 내용을 무시하고 자동으로 작업을 실행할 수 있습니다.
PowerShell에서 자동으로 명령줄을 구문 분석하고 처리하므로 **-?** 매개 변수는 항상 "이 명령에 대한 도움말 표시"를 의미합니다.

> [!NOTE]
> PowerShell에서 그래픽 애플리케이션을 실행하면 해당 애플리케이션의 창이 열립니다.
> PowerShell은 사용자가 제공하는 명령줄 입력이나 콘솔 창에 반환되는 애플리케이션 출력을 처리할 때만 개입합니다. 애플리케이션이 내부적으로 작업을 수행하는 방식에는 영향을 주지 않습니다.

## <a name="powershell-uses-some-c-syntax"></a>일부 C# 구문을 사용하는 PowerShell

PowerShell은 .NET Framework를 토대로 구축되었습니다. 일부 구문 기능과 키워드를 C# 프로그래밍 언어와 공유합니다. PowerShell을 학습하면 C#을 훨씬 더 쉽게 배울 수 있습니다. 이미 C#에 대해 잘 알고 있을 경우 이러한 유사함을 통해 PowerShell을 더 쉽게 익힐 수 있습니다.
