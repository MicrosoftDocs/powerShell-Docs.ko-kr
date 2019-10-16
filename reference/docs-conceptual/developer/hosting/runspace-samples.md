---
title: Runspace 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361002"
---
# <a name="runspace-samples"></a>Runspace 샘플

이 섹션에는 다양 한 형식의 runspace를 사용 하 여 동기적으로 비동기적으로 명령을 실행 하는 방법을 보여 주는 샘플 코드가 포함 되어 있습니다. Microsoft Visual Studio를 사용 하 여 콘솔 응용 프로그램을 만든 후이 섹션의 항목에서 호스트 응용 프로그램으로 코드를 복사할 수 있습니다.

## <a name="in-this-section"></a>이 섹션의 내용

> [!NOTE]
> 사용자 지정 호스트 인터페이스를 만드는 호스트 응용 프로그램의 샘플은 [사용자 지정 호스트 샘플](./custom-host-samples.md)을 참조 하세요.

 [Runspace01 샘플](./runspace01-sample.md) 이 샘플에서는 [system.object](/dotnet/api/system.management.automation.powershell) 를 사용 하 여 [프로세스](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 를 동기적으로 실행 하 고 콘솔 창에 출력을 표시 하는 방법을 보여 줍니다.

 [Runspace02 샘플](./runspace02-sample.md) 이 샘플에서는 [system.object](/dotnet/api/system.management.automation.powershell) 를 사용 하 여 [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 및 [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet을 동기적으로 실행 하는 방법을 보여 줍니다. 이러한 명령의 결과는 [Windows Forms](/dotnet/api/System.Windows.Forms.DataGridView) 컨트롤을 사용 하 여 표시 됩니다.

 [Runspace03 샘플](./runspace03-sample.md) 이 샘플에서는 [system.object](/dotnet/api/system.management.automation.powershell) 를 사용 하 여 스크립트를 동기적으로 실행 하는 방법과 종료 되지 않는 오류를 처리 하는 방법을 보여 줍니다. 스크립트는 프로세스 이름 목록을 받은 다음 해당 프로세스를 검색합니다. 스크립트를 실행할 때 생성된 종료되지 않는 오류를 포함하여 스크립트의 결과가 콘솔 창에 표시됩니다.

 [Runspace04 샘플](./runspace04-sample.md) 이 샘플에서는 [system.object](/dotnet/api/system.management.automation.powershell) 를 사용 하 여 명령을 실행 하는 방법과 명령을 실행할 때 throw 되는 종료 오류를 파악 하는 방법을 보여 줍니다. 두 개의 명령이 실행되는데, 마지막 명령은 유효하지 않은 매개 변수 인수를 전달받습니다. 따라서 개체가 반환 되지 않고 종료 오류가 throw 됩니다.

 [Runspace05 샘플](./runspace05-sample.md) 이 샘플에서는 [runspace](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체에 스냅인을 추가 하 여 runspace를 열 때 스냅인의 cmdlet을 사용할 수 있도록 하는 방법을 보여 줍니다. 스냅인은 GetProcessSample01 개체를 사용 하 여 동기적으로 실행 되는 Get Proc cmdlet ( [샘플](../cmdlet/getprocesssample01-sample.md)에서 정의 됨)을 제공 [합니다.](/dotnet/api/system.management.automation.powershell)

 [Runspace06 샘플](./runspace06-sample.md) 이 샘플에서는 [runspace](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체에 모듈을 추가 하 여 runspace를 열 때 모듈이 로드 되도록 하는 방법을 보여 줍니다. 이 모듈은 GetProcessSample02 개체를 사용 하 여 동기적으로 실행 되는 Get Proc cmdlet ( [샘플](../cmdlet/getprocesssample02-sample.md)에서 정의 됨)을 제공 [합니다.](/dotnet/api/system.management.automation.powershell)

 [Runspace07 샘플](./runspace07-sample.md) 이 샘플은 runspace를 만든 다음이 runspace를 사용 하 여 두 개의 cmdlet을 동기적으로 실행 하는 방법을 보여 [줍니다.](/dotnet/api/system.management.automation.powershell)

 [Runspace08 샘플](./runspace08-sample.md) 이 샘플에서는 명령과 인수를 [system.object](/dotnet/api/system.management.automation.powershell) 의 파이프라인에 추가 하는 방법과 명령을 동기적으로 실행 하는 방법을 보여 줍니다.

 [Runspace09 샘플](./runspace09-sample.md) 이 샘플에서는 스크립트를 [system.web. Powershell](/dotnet/api/system.management.automation.powershell) 개체의 파이프라인에 추가 하는 방법과 스크립트를 비동기식으로 실행 하는 방법을 보여 줍니다. 이벤트는 스크립트의 출력을 처리하는 데 사용됩니다.

 [Runspace10 샘플](./runspace10-sample.md) 이 샘플에서는 기본 초기 세션 상태를 만드는 방법, [runspace](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)에 cmdlet을 추가 하는 방법, 초기 세션 상태를 사용 하는 runspace를 만드는 방법 및를 사용 하 여 명령을 실행 하는 방법을 보여 줍니다. [System.object. Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.

 [Runspace11 샘플](./runspace11-sample.md) 이 예에서는 [system.object](/dotnet/api/System.Management.Automation.ProxyCommand) 를 사용 하 여 기존 cmdlet을 호출 하지만 사용 가능한 매개 변수 집합을 제한 하는 프록시 명령을 만드는 방법을 보여 줍니다. 프록시 명령은 제한된 runspace를 만드는 데 사용되는 초기 세션 상태에 추가됩니다. 따라서 사용자가 프록시 명령을 통해서만 cmdlet의 기능에 액세스할 수 있습니다.

## <a name="see-also"></a>참고 항목
