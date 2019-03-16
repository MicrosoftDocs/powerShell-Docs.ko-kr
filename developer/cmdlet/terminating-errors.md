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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059238"
---
# <a name="terminating-errors"></a>종료 오류

이 항목에서는 오류를 종료 하는 보고서는 방법을 설명 합니다. Cmdlet 내에서 메서드를 호출 하는 방법을 설명 하 고 메서드를 호출 하는 경우 Windows PowerShell 런타임에 의해 반환 될 수 있는 예외에 설명 합니다.

종료 오류가 발생 하면 cmdlet을 호출 하 여 오류를 보고 해야 합니다 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드. 이 메서드는 cmdlet이 종료 오류를 발생 시키는 조건을 설명 하는 오류 레코드를 보낼 수 있도록 합니다. 오류 레코드에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)합니다.

경우는 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드가 호출 되 면 Windows PowerShell 런타임에 영구적으로 파이프라인의 실행을 중지 하 고 throw 된 [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) 예외입니다. 후속 호출 하려고 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)를 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), 또는 다른 몇 가지 Api throw 를호출하면[ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) 예외입니다.

합니다 [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) 파이프라인의 다른 cmdlet에 파이프라인을 중지 하 라는 메시지가 표시 되는 경우 종료 오류를 보고 하는 경우 또는 파이프라인이 중지 된 경우에 예외가 발생할 수 있습니다 전에 어떤 이유로 든 완료 합니다. Cmdlet을 catch 하지 않아도 합니다 [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) 예외 리소스 또는 내부 상태 정리를 열어야 하는 경우가 아니면 합니다.

Cmdlet은 종료 오류를 보고 하기 전에 임의 개수의 출력 개체 또는 종료 되지 않는 오류를 작성할 수 있습니다. 그러나 파이프라인 및 종료, 아무 것도 추가 출력을 영구적으로 종료 오류 중지 또는 종료 되지 않는 오류를 보고할 수 있습니다.

Cmdlet를 호출할 수 있습니다 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 호출한 스레드에서만 합니다 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), 또는 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 처리 방법을 입력 합니다. 호출 하려고 하지 마세요 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 하거나 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 다른 스레드에서 합니다. 대신 오류를 주 스레드로 다시 전달 해야 합니다.

구현에서 예외를 throw 하는 cmdlet에 대 한 가능성이 합니다 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)를 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), 또는 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드. (Windows PowerShell 호스트를 중지 하는 몇 가지 심각한 오류 조건) 제외 하 고 이러한 메서드에서 throw 된 예외는 파이프라인 하지만 전체적으로 Windows PowerShell이 아닌 중지 종료 오류로 해석 됩니다. (기본 cmdlet 스레드에만 적용 됩니다. Cmdlet에 의해 생성 된 스레드의 예외로 일반적으로 중단 Windows PowerShell 호스트 합니다.) 사용 하는 것이 좋습니다 [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) error 레코드 오류 조건에 대 한 추가 정보를 제공 하기 때문에 예외가 발생 하는 대신 하는 데 유용 최종 사용자입니다. Catch 및 처리 하는 모든 예외에 대 한 관리 되는 코드 지침 따르도록 Cmdlet (`catch (Exception e)`). 알려진 형식의 예외만 오류 레코드로 변환 합니다.

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell 오류 레코드](./windows-powershell-error-records.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
