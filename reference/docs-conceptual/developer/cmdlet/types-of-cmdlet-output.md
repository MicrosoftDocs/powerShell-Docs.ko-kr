---
title: Cmdlet 출력의 유형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369292"
---
# <a name="types-of-cmdlet-output"></a>Cmdlet 출력의 유형

PowerShell은 출력을 생성 하기 위해 cmdlet에서 호출할 수 있는 몇 가지 메서드를 제공 합니다. 이러한 메서드는 특정 작업을 사용 하 여 결과를 성공 데이터 스트림 또는 오류 데이터 스트림과 같은 특정 데이터 스트림에 씁니다. 이 문서에서는 출력 형식 및이를 생성 하는 데 사용 되는 메서드를 설명 합니다.

## <a name="types-of-output"></a>출력 유형

### <a name="success-output"></a>성공 출력

Cmdlet은 파이프라인의 다음 명령으로 처리할 수 있는 개체를 반환 하 여 성공 여부를 보고할 수 있습니다. Cmdlet은 작업을 성공적으로 수행한 후 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 호출 합니다. 이 메서드를 호출 [하는 것](/dotnet/api/System.Console.WriteLine) 이 [PSHostUserInterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) 또는 시스템 대신이 메서드를 호출 하는 것이 좋습니다.

일반적으로 개체를 반환 하지 않는 cmdlet에 대 한 **PassThru** 스위치 매개 변수를 제공할 수 있습니다.
명령줄에서 **PassThru** 스위치 매개 변수를 지정 하면 cmdlet에서 개체를 반환 하 라는 메시지가 표시 됩니다. **PassThru** 매개 변수를 포함 하는 cmdlet의 예는 [추가-기록](/powershell/module/Microsoft.PowerShell.Core/Add-History)을 참조 하세요.

### <a name="error-output"></a>오류 출력

Cmdlet은 오류를 보고할 수 있습니다. 종료 오류가 발생 하면 cmdlet이 예외를 throw 합니다. 종료 되지 않는 오류가 발생 하는 경우 cmdlet은 [WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 메서드를 호출 하 여 오류 레코드를 오류 데이터 스트림으로 보냅니다. 오류 보고에 대 한 자세한 내용은 [오류 보고 개념](./error-reporting-concepts.md)을 참조 하십시오.

### <a name="verbose-output"></a>자세한 정보 출력

Cmdlet은 사용자에 게 유용한 정보를 제공할 수 있습니다 .이 cmdlet은 cmdlet이 레코드를 올바르게 처리 하는 동안에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 를 호출 합니다. 메서드는 작업을 진행 하는 방법을 나타내는 자세한 정보 메시지를 생성 합니다.

기본적으로 자세한 정보 표시 메시지는 표시 되지 않습니다. 이러한 메시지를 표시 하기 위해 cmdlet을 실행할 때 **Verbose** 매개 변수를 지정할 수 있습니다. **Verbose** 는 모든 cmdlet에서 사용할 수 있는 일반 매개 변수입니다.

### <a name="progress-output"></a>진행률 출력

Cmdlet은 디렉터리를 재귀적으로 복사 하는 것과 같이 완료 하는 데 시간이 오래 걸리는 작업을 수행할 때 진행률 정보를 사용자에 게 제공할 수 있습니다. 진행률 정보를 표시 하기 위해 cmdlet은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 를 호출 합니다.

### <a name="debug-output"></a>디버그 출력

Cmdlet은 cmdlet 코드 문제를 해결할 때 유용한 디버그 메시지를 제공할 수 있습니다. 디버그 정보를 표시 하기 위해 cmdlet은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 호출 합니다.

기본적으로 디버그 메시지는 표시 되지 않습니다. 이러한 메시지를 표시 하기 위해 cmdlet을 실행할 때 **Debug** 매개 변수를 지정할 수 있습니다. **Debug** 는 모든 cmdlet에서 사용할 수 있는 일반 매개 변수입니다.

### <a name="warning-output"></a>경고 출력

Cmdlet은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 를 호출 하 여 경고 메시지를 표시할 수 있습니다.

기본적으로 경고 메시지가 표시 됩니다. 그러나 `$WarningPreference` 변수를 사용 하거나 cmdlet을 호출할 때 **Verbose** 및 **디버그** 매개 변수를 사용 하 여 경고 메시지를 구성할 수 있습니다.

## <a name="displaying-output"></a>출력 표시

모든 쓰기 메서드 호출에서 콘텐츠 표시는 특정 런타임 변수에 따라 결정 됩니다. 단, [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드는 예외입니다. 이러한 변수를 사용 하 여 코드에서 올바른 위치에 적절 한 쓰기 호출을 수행할 수 있으며, 출력을 표시 해야 하는 경우 나 경우를 걱정 하지 않아도 됩니다.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>호스트 응용 프로그램의 출력 기능에 액세스

PowerShell 런타임을 통해 호스트 응용 프로그램의 출력 기능에 직접 액세스 하는 cmdlet을 디자인할 수도 있습니다. [Console](/dotnet/api/System.Console) 또는 [system.web](/dotnet/api/System.Windows.Forms) 대신 PowerShell에서 제공 하는 호스트 api를 사용 하면 cmdlet이 다양 한 호스트에서 작동 합니다. 예를 들면 **powershell .exe** 콘솔 호스트, **powershell_ise** 그래픽 호스트, powershell 원격 호스트 및 타사 호스트가 있습니다.

## <a name="see-also"></a>참고 항목

[오류 보고 개념](./error-reporting-concepts.md)

[Cmdlet 개요](./cmdlet-overview.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)