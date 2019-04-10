---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 프린터 작업
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 77ebb26369b6a40e9c8c7bbbc52347d614cbf083
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292996"
---
# <a name="working-with-printers"></a><span data-ttu-id="6e021-103">프린터 작업</span><span class="sxs-lookup"><span data-stu-id="6e021-103">Working with Printers</span></span>

<span data-ttu-id="6e021-104">WSH의 WMI 및 WScript.Network COM 개체를 사용하여 Windows PowerShell을 통해 프린터를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e021-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="6e021-105">이 가이드에서는 두 도구를 모두 사용하여 프린터를 관리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6e021-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="6e021-106">프린터 연결 표시</span><span class="sxs-lookup"><span data-stu-id="6e021-106">Listing Printer Connections</span></span>

<span data-ttu-id="6e021-107">컴퓨터에 설치된 프린터를 표시하는 가장 간단한 방법은 다음과 같이 WMI **Win32_Printer** 클래스를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6e021-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="6e021-108">일반적으로 WSH 스크립트에서 사용되는 **WScript.Network** COM 개체를 통해 프린터를 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e021-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="6e021-109">이 명령을 사용하면 고유 레이블 없이 포트 이름 및 프린터 디바이스 이름의 간단한 문자열 컬렉션만 반환되기 때문에 쉽게 해석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e021-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="6e021-110">네트워크 프린터 추가</span><span class="sxs-lookup"><span data-stu-id="6e021-110">Adding a Network Printer</span></span>

<span data-ttu-id="6e021-111">새 네트워크 프린터를 추가하려면 다음과 같이 **WScript.Network**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e021-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="6e021-112">기본 프린터 설정</span><span class="sxs-lookup"><span data-stu-id="6e021-112">Setting a Default Printer</span></span>

<span data-ttu-id="6e021-113">WMI를 사용하여 기본 프린터를 설정하려면 **Win32_Printer** 컬렉션에서 프린터를 찾은 다음 **SetDefaultPrinter** 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6e021-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="6e021-114">**WScript.Network**가 좀더 사용하기 쉽습니다. 프린터 이름만 인수로 받아들이는 **SetDefaultPrinter** 메서드가 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="6e021-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="6e021-115">프린터 연결 제거</span><span class="sxs-lookup"><span data-stu-id="6e021-115">Removing a Printer Connection</span></span>

<span data-ttu-id="6e021-116">프린터 연결을 제거하려면 **WScript.Network RemovePrinterConnection** 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e021-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```