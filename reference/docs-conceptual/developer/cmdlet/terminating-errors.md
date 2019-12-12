---
title: 종료 오류 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369332"
---
# <a name="terminating-errors"></a>종료 오류

이 항목에서는 종료 오류를 보고 하는 데 사용 되는 방법에 대해 설명 합니다. 또한 cmdlet 내에서 메서드를 호출 하는 방법에 대해 설명 하 고, 메서드가 호출 될 때 Windows PowerShell 런타임에 의해 반환 될 수 있는 예외에 대해 설명 합니다.

종료 오류가 발생 하면 cmdlet은 [Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드를 호출 하 여 오류를 보고 해야 합니다. 이 메서드를 사용 하면 cmdlet이 종료 오류를 발생 시킨 조건을 설명 하는 오류 레코드를 보낼 수 있습니다. 오류 레코드에 대 한 자세한 내용은 [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)를 참조 하십시오.

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드가 호출되면 Windows PowerShell 런타임은 파이프라인 실행을 영구적으로 중지하고 Pipelines 및  [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) 예외를 throw합니다. [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)또는 기타 몇 가지 api 호출을 수행 하려고 하면 이러한 호출로 인해 [Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) 예외가 throw 되는 경우를 발생 시킬 수 있습니다.

파이프라인의 다른 cmdlet이 종료 오류를 보고 하거나, 사용자가 파이프라인을 중지 하도록 요청 했거나, 어떤 이유로 완료 되기 전에 파이프라인이 중단 된 경우에도 [Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) 예외가 발생할 수 있습니다. 이 cmdlet은 오픈 리소스나 내부 상태를 정리 해야 하는 경우를 제외 하 고 [Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) 예외를 catch 하지 않아도 됩니다.

Cmdlet은 종료 오류를 보고 하기 전에 원하는 수의 출력 개체 또는 종료 되지 않는 오류를 기록할 수 있습니다. 그러나 종료 오류는 파이프라인을 영구적으로 중지 하며, 추가 출력, 종료 오류 또는 종료 되지 않는 오류를 보고할 수 없습니다.

Cmdlet은 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 또는 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 입력 처리 방법을 부른 스레드에서만 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)를 호출할 수 있습니다. 다른 스레드에서 [Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 또는 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 을 호출 하려고 하지 마십시오. (영문)를 호출 합니다. 대신 오류를 주 스레드로 다시 전달 해야 합니다.

Cmdlet이 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)또는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 의 구현에서 예외를 throw 할 수 [있습니다 (예](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)를 들어, cmdlet을 구현 하는 것이 가능 합니다.-). Windows PowerShell 호스트를 중지 하는 몇 가지 심각한 오류 조건을 제외 하 고 이러한 메서드에서 throw 되는 예외는 종료 오류로 해석 되어 Windows PowerShell 전체가 아니라 파이프라인을 중지 합니다. 이는 주 cmdlet 스레드에만 적용 됩니다. 일반적으로 cmdlet에 의해 생성 된 스레드의 catch 되지 않은 예외는 Windows PowerShell 호스트를 중지 합니다. 오류 레코드는 오류 조건에 대 한 추가 정보를 제공 하기 때문에 예외를 throw 하는 대신 [Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 를 사용 하는 것이 좋습니다 .이는 최종 사용자에 게 유용 합니다. Cmdlet은 모든 예외 (`catch (Exception e)`)를 catch 하 고 처리 하는 것에 대 한 관리 코드 지침을 따라야 합니다. 알려진 형식과 예상 형식의 예외만 오류 레코드로 변환 합니다.

## <a name="see-also"></a>참고 항목

[System.object를 처리 합니다.](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.object..](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[ProcessRecord입니다.](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Pipelinestoppedexception.](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[Throwterminatingerror *입니다.](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[WriteError입니다.](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
