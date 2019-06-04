---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 용어집
ms.assetid: b0f88cbe-cb83-4912-a301-184534cb35c7
ms.openlocfilehash: fd15667939fd9b3ea705806686b626645519588a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057359"
---
# <a name="windows-powershell-glossary"></a>Windows PowerShell 용어집


|용어|정의|
|--------|--------------|
|이진 모듈|루트 모듈이 이진 모듈 파일(.dll)인 Windows PowerShell 모듈입니다. 이진 모듈은 모듈 매니페스트를 포함할 수도 있고, 포함하지 않을 수도 있습니다.|
|일반 매개 변수|Windows PowerShell 엔진이 모든 cmdlet, 고급 함수 및 워크플로에 추가하는 매개 변수입니다.|
|도트 소싱|Windows PowerShell에서는 명령 앞에 점과 공백을 입력하여 명령을 시작합니다. 도트 소싱된 명령은 새 범위가 아니라 현재 범위에서 실행됩니다. 명령이 만드는 모든 변수, 별칭, 함수 또는 드라이브는 현재 범위에서 생성되며, 명령이 완료되면 사용자가 사용할 수 있습니다.|
|동적 모듈|메모리에만 존재하는 모듈입니다. NewNew-Module 및 Import-PSSession은 동적 모듈을 만듭니다.|
|동적 매개 변수|특정 조건에서 Windows PowerShell cmdlet, 함수 또는 스크립트에 추가되는 매개 변수입니다. cmdlet, 함수, 공급자 및 스크립트는 동적 매개 변수를 추가할 수 있습니다.|
|서식 파일|확장명이 .format.ps1xml이고 Windows PowerShell에서 .NET Framework 형식에 따라 개체를 표시하는 방법을 정의하는 Windows PowerShell XML 파일입니다.|
|전역 세션 상태|Windows PowerShell 세션의 사용자가 액세스할 수 있는 데이터를 포함하는 세션 상태입니다.|
|호스트|Windows PowerShell 엔진이 사용자와 통신하는 데 사용하는 인터페이스입니다. 예를 들어 호스트는 Windows PowerShell과 사용자 간의 프롬프트 처리 방법을 지정합니다.|
|호스트 애플리케이션|Windows PowerShell 엔진을 해당 프로세스에 로드하고 작업을 수행하는 데 사용하는 프로그램입니다.|
|입력 처리 메서드|cmdlet이 입력으로 받은 레코드를 처리하는 데 사용할 수 있는 메서드입니다. 입력 처리 메서드로는 BeginProcessing 메서드, ProcessRecord 메서드, EndProcessing 메서드 및 StopProcessing 메서드가 있습니다.|
|매니페스트 모듈|매니페스트가 있으며 RootModule 키가 비어 있는 Windows PowerShell 모듈입니다.|
|모듈 매니페스트|모듈 내용을 설명하고 모듈 처리 방법을 제어하는 Windows PowerShell 데이터 파일(.psd1)입니다.|
|모듈 세션 상태|Windows PowerShell 모듈의 공용 및 개인 데이터를 포함하는 세션 상태입니다. 이 세션 상태의 개인 데이터는 Windows PowerShell 세션 사용자가 사용할 수 없습니다.|
|종료되지 않는 오류|Windows PowerShell이 명령 처리를 계속할 수 있는 오류입니다.|
|명사|Windows PowerShell cmdlet 이름에서 하이픈 뒤에 오는 단어입니다. 명사는 cmdlet이 적용되는 리소스를 설명합니다.|
|매개 변수 집합|특정 작업을 수행하기 위해 동일한 명령에 사용할 수 있는 매개 변수 그룹입니다.|
|파이프|Windows PowerShell에서는 이전 명령의 결과를 파이프라인의 다음 명령에 입력으로 보냅니다.|
|파이프라인|파이프라인 연산자(&#124;)(ASCII 124)로 연결된 일련의 명령입니다. 각 파이프라인 연산자는 이전 명령의 결과를 다음 명령에 입력으로 보냅니다.|
|PSSession|사용자가 만들고 관리 및 종료하는 Windows PowerShell 세션의 형식입니다.|
|루트 모듈|모듈 매니페스트의 RootModule 키에 지정된 모듈입니다.|
|Runspace|Windows PowerShell에서는 파이프라인의 각 명령이 실행되는 운영 체제입니다.|
|스크립트 블록|Windows PowerShell 프로그래밍 언어에서는 단일 단위로 사용할 수 있는 문 또는 식의 컬렉션입니다. 스크립트 블록은 인수를 받아서 값을 반환할 수 있습니다.|
|스크립트 모듈|루트 모듈이 스크립트 모듈 파일(.psm1)인 Windows PowerShell 모듈입니다. 스크립트 모듈은 모듈 매니페스트를 포함할 수도 있고, 포함하지 않을 수도 있습니다.|
|스크립트 모듈 파일|Windows PowerShell 스크립트를 포함하는 파일입니다. 스크립트는 스크립트 모듈이 내보내는 멤버를 정의합니다. 스크립트 모듈 파일의 파일 이름 확장명은 .psm1입니다.|
|셸|운영 체제에 명령을 전달하는 데 사용되는 명령 인터프리터입니다.|
|스위치 매개 변수|인수를 사용하지 않는 매개 변수입니다.|
|종료 오류|Windows PowerShell이 명령을 처리할 수 없는 오류입니다.|
|트랜잭션|작업의 원자 단위입니다. 한 트랜잭션의 작업은 전체를 완료해야 합니다. 트랜잭션의 일부가 실패하면 전체 트랜잭션이 실패합니다.|
|형식 파일|확장명이 .ps1xml이고 Windows PowerShell에서 Microsoft .NET Framework 형식의 속성을 확장하는 Windows PowerShell XML 파일입니다.|
|동사|Windows PowerShell cmdlet 이름에서 하이픈 앞에 오는 단어입니다. 동사는 cmdlet이 수행하는 작업을 설명합니다.|
|Windows PowerShell|IT 관리자가 시스템 관리 작업을 포괄적으로 제어하고 자동화할 수 있게 해주는 명령줄 셸 및 작업 기반 스크립팅 기술입니다.|
|Windows PowerShell 명령|작업이 수행되게 하는 파이프라인의 요소입니다. Windows PowerShell 명령은 키보드에서 입력되거나 프로그래밍 방식으로 호출됩니다.|
|Windows PowerShell 데이터 파일|파일 이름 확장명이 .psd1인 텍스트 파일입니다. Windows PowerShell은 모듈 매니페스트 데이터 저장, 스크립트 국제화를 위해 번역된 문자열 저장 등의 다양한 용도로 데이터 파일을 사용합니다.|
|Windows PowerShell 드라이브|데이터 저장소에 대한 직접 액세스를 제공하는 가상 드라이브입니다. Windows PowerShell 공급자가 정의하거나 명령줄에서 만들 수 있습니다. 명령줄에서 만든 드라이브는 세션 전용 드라이브이며 세션을 닫으면 손실됩니다.|
|Windows PowerShell ISE(통합 스크립팅 환경)|명령을 실행할 수 있을 뿐 아니라 구문 색이 지정되는 친숙한 유니코드 규격 환경에서 스크립트를 작성, 테스트 및 디버그할 수 있게 해주는 Windows PowerShell 호스트 애플리케이션입니다.|
|Windows PowerShell 모듈|Windows PowerShell 코드를 분할, 구성 및 추상화할 수 있게 해주는 다시 사용할 수 있는 자체 포함 단위입니다. 모듈에는 cmdlet, 공급자, 함수, 변수 및 단일 단위로 가져올 수 있는 기타 유형의 리소스가 포함될 수 있습니다.|
|Windows PowerShell 공급자|Windows PowerShell에서 특정 데이터 저장소의 데이터를 사용하여 보고 관리할 수 있게 해주는 Microsoft .NET Framework 기반 프로그램입니다.|
|Windows PowerShell 스크립트|Windows PowerShell 언어로 작성된 스크립트입니다.|
|Windows PowerShell 스크립트 파일|확장명이 .ps1이고 Windows PowerShell 언어로 작성된 스크립트를 포함하는 파일입니다.|
|Windows PowerShell 스냅인|Windows PowerShell 환경에 추가할 수 있는 cmdlet, 공급자 및 Microsoft.NET Framework 형식 집합을 정의하는 리소스입니다.|
|Windows PowerShell 워크플로|워크플로는 프로그래밍 방식으로 연결된 단계의 시퀀스로, 장기 실행 작업을 수행하거나 여러 디바이스 또는 관리 노드에서 여러 단계의 조정을 필요로 합니다. Windows PowerShell 워크플로를 통해 IT 전문가와 개발자는 다중 장치 관리 활동 또는 워크플로 내 단일 작업의 시퀀스를 워크플로로 작성할 수 있습니다. Windows PowerShell 워크플로를 통해 Windows PowerShell 스크립트와 XAML 파일 둘 다를 워크플로로 적용하고 실행할 수 있습니다.|