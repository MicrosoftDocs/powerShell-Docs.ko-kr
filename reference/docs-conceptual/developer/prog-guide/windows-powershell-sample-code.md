---
title: Windows PowerShell 샘플 코드 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8dcbe6d8760d77666a8191ca78416ef63dfebdeb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786937"
---
# <a name="windows-powershell-sample-code"></a>Windows PowerShell 코드 샘플

Windows SDK를 통해 Windows PowerShell® 샘플을 사용할 수 있습니다. 이 섹션에는 Windows SDK 샘플에 포함 된 샘플 코드가 포함 되어 있습니다.

> [!NOTE]
> Windows SDK 설치 되 면 모든 Windows PowerShell 샘플을 사용할 수 있는 **samples** 디렉터리가 만들어집니다. 일반적인 설치 디렉터리는 **C:\Program Files\Microsoft SDKs\Windows\v6.0**입니다. Windows PowerShell을 시작 하 고 **"cd Samples\SysMgmt\PowerShell"** 를 입력 하 여 Windows powershell Samples 디렉터리를 찾습니다. 이 문서에서는 Windows PowerShell Samples 디렉터리를 라고 **\<PowerShell Samples>** 합니다.

## <a name="sample-code-listing"></a>샘플 코드 목록

|                                    샘플 코드                                    |                                                                                                                                           설명                                                                                                                                           |
| --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [AccessDbProviderSample01 코드 샘플](./accessdbprovidersample01-code-sample.md) | 이 공급자는 [기본 Windows PowerShell 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)에 설명 된 공급자입니다.                                                                                                                                                            |
| [AccessDbProviderSample02 코드 샘플](./accessdbprovidersample02-code-sample.md) | [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)에 설명 된 공급자입니다.                                                                                                                                                            |
| [AccessDbProviderSample03 코드 샘플](./accessdbprovidersample03-code-sample.md) | [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)에서 설명 하는 공급자입니다.                                                                                                                                                              |
| [AccessDbProviderSample04 코드 샘플](./accessdbprovidersample04-code-sample.md) | [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)에서 설명 하는 공급자입니다.                                                                                                                                                    |
| [AccessDbProviderSample05 코드 샘플](./accessdbprovidersample05-code-sample.md) | [Windows PowerShell 탐색 공급자 만들기](./creating-a-windows-powershell-navigation-provider.md)에서 설명 하는 공급자입니다.                                                                                                                                                  |
| [AccessDbProviderSample06 코드 샘플](./accessdbprovidersample06-code-sample.md) | [Windows PowerShell 콘텐츠 공급자 만들기](./creating-a-windows-powershell-content-provider.md)에 설명 된 공급자입니다.                                                                                                                                                        |
| [GetProc01 코드 샘플](./getproc01-code-samples.md)                             | `Get-Process` [첫 번째 cmdlet 만들기](../cmdlet/creating-a-cmdlet-without-parameters.md)에 설명 된 기본 cmdlet 샘플입니다.                                                                                                                                                     |
| [GetProc02 코드 샘플](./getproc02-code-samples.md)                             | `Get-Process` [명령줄 입력을 처리 하는 매개 변수 추가](../cmdlet/adding-parameters-that-process-command-line-input.md)에서 설명 하는 cmdlet 샘플입니다.                                                                                                                       |
| [GetProc03 코드 샘플](./getproc03-code-samples.md)                             | `Get-Process` [파이프라인 입력을 처리 하는 매개 변수 추가](../cmdlet/adding-parameters-that-process-pipeline-input.md)에서 설명 하는 cmdlet 샘플입니다.                                                                                                                               |
| [GetProc04 코드 샘플](./getproc04-code-samples.md)                             | Cmdlet에 종료 되지 않는 `Get-Process` [오류 보고 추가](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)에 설명 된 cmdlet 샘플입니다.                                                                                                                |
| [GetProc05 코드 샘플](./getproc05-code-samples.md)                             | 이 `Get-Process` cmdlet은 cmdlet에 [비 종료 오류 보고 추가](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)에 설명 된 cmdlet과 유사 합니다.                                                                                                     |
| [StopProc01 코드 샘플](./stopproc01-code-samples.md)                           | 다음은 `Stop-Process` [시스템을 수정 하는 cmdlet 만들기](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md)에서 설명 하는 cmdlet 샘플입니다.                                                                                                                                    |
| [StopProcessSample04 코드 샘플](./stopprocesssample04-code-samples.md)         | `Stop-Process` [Cmdlet에 매개 변수 집합 추가](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)에 설명 된 cmdlet 샘플입니다.                                                                                                                                                      |
| [Runspace01 코드 샘플](./runspace01-code-samples.md)                           | 다음은 [지정 된 명령을 실행 하는 콘솔 응용 프로그램 만들기](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)에서 설명 하는 runspace에 대 한 코드 샘플입니다.                                                                                      |
| [Runspace02 코드 샘플](./runspace02-code-samples.md)                           | 이 샘플에서는 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하 여 cmdlet을 동기적으로 실행 `Get-Process` 합니다.                                                                                                            |
| [RunSpace03 코드 샘플](./runspace03-code-samples.md)                           | 다음은 "지정 된 스크립트를 실행 하는 콘솔 응용 프로그램 만들기"에 설명 된 runspace에 대 한 코드 샘플입니다.                                                                                                                                                                         |
| [RunSpace04 코드 샘플](./runspace04-code-samples.md)                           | 종료 오류를 생성 하는 스크립트를 실행 하기 위해 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하는 runspace에 대 한 코드 샘플입니다.                                                                         |
| [RunSpace05 코드 샘플](./runspace05-code-sample.md)                             | [RunspaceConfiguration를 사용 하 여 Runspace 구성](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2)에 설명 된 Runspace05 샘플의 소스 코드입니다.                                                                                                           |
| [RunSpace06 코드 샘플](./runspace06-code-sample.md)                             | [Windows PowerShell 스냅인을 사용 하 여 Runspace 구성](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83)에 설명 된 Runspace06 샘플의 소스 코드입니다.                                                                                                    |
| [RunSpace07 코드 샘플](./runspace07-code-sample.md)                             | [파이프라인에 명령을 추가 하는 콘솔 응용 프로그램 만들기](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e)에서 설명한 Runspace07 샘플의 소스 코드입니다.                                                                                              |
| [RunSpace08 코드 샘플](./runspace08-code-sample.md)                             | 이 코드는 [명령에 매개 변수를 추가 하는 콘솔 응용 프로그램 만들기](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba)에서 설명한 Runspace08 샘플의 소스 코드입니다.                                                                                             |
| [RunSpace09 코드 샘플](./runspace09-code-sample.md)                             | [파이프라인을 비동기식으로 호출 하는 콘솔 응용 프로그램 만들기](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47)에서 설명한 Runspace09 샘플의 소스 코드입니다.                                                                                        |
| [RunSpace10 코드 샘플](./runspace10-code-sample.md)                             | Runspace10 샘플에 대 한 소스 코드로, [runspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) 에 cmdlet을 추가한 다음 수정 된 구성 정보를 사용 하 여 runspace를 만듭니다. |

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
