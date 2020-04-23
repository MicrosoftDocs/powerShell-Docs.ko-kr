---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 프린터 작업
ms.openlocfilehash: 1d6b9a57ec61f06af694757dc8017d50b4dd40fe
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "78935205"
---
# <a name="working-with-printers-in-windows"></a>Windows에서 프린터 작업

WSH의 WMI 및 **WScript.Network** COM 개체를 사용하여 PowerShell을 통해 프린터를 관리할 수 있습니다. 이 가이드에서는 두 도구를 모두 사용하여 프린터를 관리하는 방법을 보여 줍니다.

## <a name="listing-printer-connections"></a>프린터 연결 표시

컴퓨터에 설치된 프린터를 표시하는 가장 간단한 방법은 다음과 같이 WMI **Win32_Printer** 클래스를 사용하는 것입니다.

```powershell
Get-CimInstance -Class Win32_Printer
```

일반적으로 WSH 스크립트에서 사용되는 **WScript.Network** COM 개체를 통해 프린터를 표시할 수도 있습니다.

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

이 명령을 사용하면 고유 레이블 없이 포트 이름 및 프린터 디바이스 이름의 간단한 문자열 컬렉션만 반환되기 때문에 쉽게 해석할 수 없습니다.

## <a name="adding-a-network-printer"></a>네트워크 프린터 추가

새 네트워크 프린터를 추가하려면 다음과 같이 **WScript.Network**를 사용합니다.

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>기본 프린터 설정

WMI를 사용하여 기본 프린터를 설정하려면 **Win32_Printer** 컬렉션에서 프린터를 찾은 다음 **SetDefaultPrinter** 메서드를 호출합니다.

```powershell
$printer = Get-CimInstance -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'"
Invoke-CimMethod -InputObject $printer -MethodName SetDefaultPrinter
```

**WScript.Network**가 좀더 사용하기 쉽습니다. 프린터 이름만 인수로 받아들이는 **SetDefaultPrinter** 메서드가 있기 때문입니다.

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>프린터 연결 제거

프린터 연결을 제거하려면 **WScript.Network RemovePrinterConnection** 메서드를 사용합니다.

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
