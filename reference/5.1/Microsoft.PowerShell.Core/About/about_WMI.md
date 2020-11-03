---
description: WMI(Windows Management Instrumentation) (WMI)는 CIM(Common Information Model) (CIM)를 사용 하 여 최신 기업의 시스템, 응용 프로그램, 네트워크, 장치 및 기타 관리 가능한 구성 요소를 나타냅니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI
ms.openlocfilehash: d24b952ee167e51815d6d9920e95bbc9a6bb9608
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223209"
---
# <a name="about-wmi"></a>WMI 정보

## <a name="short-description"></a>간단한 설명

WMI(Windows Management Instrumentation) (WMI)는 CIM(Common Information Model) (CIM)를 사용 하 여 최신 기업의 시스템, 응용 프로그램, 네트워크, 장치 및 기타 관리 가능한 구성 요소를 나타냅니다.

## <a name="long-description"></a>자세한 설명

WMI(Windows Management Instrumentation) (WMI)는 업계 표준으로, Microsoft의 WBEM (Web-Based Enterprise Management) 구현입니다.

클래식 WMI는 DCOM을 사용 하 여 원격 시스템을 관리 하는 네트워크 장치와 통신 합니다. Windows PowerShell 3.0에서는 WinRM을 사용 하 여 DCOM에 대 한 종속성을 제거 하는 CIM 공급자 모델을 소개 합니다. 또한이 CIM 공급자 모델은 개발자가 네이티브 코드 (C)로 Windows PowerShell cmdlet을 작성할 수 있도록 하는 새로운 WMI 공급자 Api를 사용 \+ \+ 합니다.

WMI 공급자와 Windows PowerShell 공급자를 혼동 하지 마십시오. 많은 Windows 기능에는 관리 기능을 제공 하는 연결 된 WMI 공급자가 있습니다. WMI 공급자를 가져오려면 다음 쿼리와 같이 __Provider WMI 클래스의 인스턴스를 가져오는 WMI 쿼리를 실행 합니다.

```powershell
Get-WmiObject -Class __Provider
```

## <a name="three-components-of-wmi"></a>WMI의 세 가지 구성 요소

WMI의 다음 세 가지 구성 요소는 Windows PowerShell과 상호 작용 합니다. 네임 스페이스, 공급자 및 클래스입니다.

Wmi 네임 스페이스는 WMI 공급자와 WMI 클래스를 관련 구성 요소 그룹으로 구성 합니다. 이러한 방식으로 .NET Framework 네임 스페이스와 유사 합니다.
네임 스페이스는 물리적 위치가 아니라 논리적 데이터베이스와 유사 합니다.
모든 WMI 네임 스페이스는 __Namespace 시스템 클래스의 인스턴스입니다. 기본 WMI 네임 스페이스는 Root \/ CIMV2 (Microsoft Windows 2000 이후)입니다. Windows PowerShell을 사용 하 여 현재 세션에서 WMI 네임 스페이스를 가져오려면 다음 형식의 명령을 사용 합니다.

```powershell
Get-WmiObject -Class __Namespace
```

다른 네임 스페이스에 있는 WMI 네임 스페이스를 가져오려면 Namespace 매개 변수를 사용 하 여 검색 위치를 변경 합니다. 다음 명령은 Root/Cimv2/Applications 네임 스페이스에 상주 하는 WMI 네임 스페이스를 찾습니다.

```powershell
Get-WmiObject -Class __Namespace -Namespace root/CIMv2/applications
```

WMI 네임 스페이스는 계층 구조입니다. 따라서 특정 시스템에서 모든 네임 스페이스 목록을 가져오려면 루트 네임 스페이스에서 시작 하는 재귀 쿼리를 수행 해야 합니다.

WMI 공급자는 Windows 관리 가능한 개체에 대 한 정보를 노출 합니다. 공급자는 구성 요소에서 데이터를 검색 하 고 WMI를 통해 Windows PowerShell과 같은 관리 응용 프로그램으로 해당 데이터를 전달 합니다. 대부분의 WMI 공급자는 동적 공급자 이므로 관리 응용 프로그램을 통해 요청 될 때 데이터를 동적으로 가져옵니다.

## <a name="finding-wmi-classes"></a>WMI 클래스 찾기

Windows 8의 기본 설치에서 Root Cimv2에는 1100 개가 넘는 WMI 클래스가 있습니다 \/ . 이 많은 WMI 클래스를 사용 하면 특정 작업을 수행 하는 데 사용할 적절 한 WMI 클래스를 식별 하 게 됩니다. Windows PowerShell 3.0에서는 두 가지 방법으로 특정 항목과 관련 된 WMI 클래스를 찾을 수 있습니다.

예를 들어, \\ 디스크와 관련 된 루트 CIMV2 wmi 네임 스페이스에서 wmi 클래스를 찾으려면 여기에 표시 된 것과 같은 쿼리를 사용할 수 있습니다.

```powershell
Get-WmiObject -List *disk*
```

메모리와 관련 된 WMI 클래스를 찾으려면 여기에 표시 된 것과 같은 쿼리를 사용할 수 있습니다.

```powershell
Get-WmiObject -List *memory*
```

CIM cmdlet은 WMI 클래스를 검색 하는 기능도 제공 합니다. 이렇게 하려면 Get-CIMClass cmdlet을 사용 합니다. 여기에 표시 된 명령은 비디오와 관련 된 WMI 클래스를 나열 합니다.

```powershell
Get-CimClass *video*
```

탭 확장은 WMI 네임 스페이스를 변경할 때 작동 하므로 탭 확장을 사용 하면 하위 WMI 네임 스페이스를 쉽게 검색할 수 있습니다. 다음 예제에서 Get-CimClass cmdlet은 전원 설정과 관련 된 WMI 클래스를 나열 합니다.
이를 찾으려면 네임 스페이스를 입력 한 `root/CIMV2/` 다음 power 네임 스페이스가 나타날 때까지 tab 키를 여러 번 누릅니다. 명령은 다음과 같습니다.

```powershell
Get-CimClass *power* -Namespace root/cimv2/power
```
