---
title: Windows PowerShell 참조 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: c00590df4d07e0f5ed9e93fd84a2780329753e39
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870866"
---
# <a name="windows-powershell-reference"></a>Windows PowerShell 참조

Windows PowerShell은 관리 자동화를 위해 설계 된 Microsoft .NET 프레임 워크 연결 환경입니다. Windows PowerShell은 명령을 작성 하 고, 솔루션을 작성 하 고, 그래픽 사용자 인터페이스 기반 관리 도구를 만드는 새로운 방법을 제공 합니다.

Windows PowerShell을 통해 시스템 관리자는 직접 또는 스크립트를 통해 명령을 실행 하 여 시스템 리소스의 관리를 자동화할 수 있습니다.

## <a name="developer-audience"></a>개발자 대상

Windows powershell SDK (소프트웨어 개발 키트)는 Windows PowerShell에서 제공 하는 Api에 대 한 참조 정보를 요구 하는 명령 개발자를 위해 작성 되었습니다. 명령 개발자는 windows PowerShell을 사용 하 여 Windows PowerShell에서 수행할 수 있는 작업을 확장 하는 명령과 공급자를 모두 만듭니다.

## <a name="windows-powershell-resources"></a>Windows PowerShell 리소스

Windows PowerShell SDK 외에도 다음 리소스에서 추가 정보를 제공 합니다.

[Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell) Windows PowerShell 소개: 언어, cmdlet, 공급자 및 개체 사용에 대해 설명 합니다.

[Windows PowerShell 모듈 작성](./module/writing-a-windows-powershell-module.md) Windows PowerShell 모듈을 사용 하 여 Windows PowerShell 솔루션을 패키지 하 고 배포 해야 하는 관리자, 스크립트 개발자 및 cmdlet 개발자를 위한 정보 및 예제를 제공 합니다.

[Windows PowerShell Cmdlet 작성](./cmdlet/writing-a-windows-powershell-cmdlet.md) Cmdlet을 디자인 하는 프로그램 관리자와 cmdlet 코드를 구현 하는 개발자를 위한 정보 및 코드 예제를 제공 합니다.

[Windows PowerShell 팀 블로그](https://blogs.msdn.microsoft.com/PowerShell/) 다른 Windows PowerShell 사용자의 학습 및 공동 작업에 가장 적합 한 리소스입니다. Windows PowerShell 팀 블로그를 읽은 다음 Windows PowerShell 사용자 포럼 (microsoft. w i m.
Windows 실시간 검색을 사용 하 여 다른 Windows PowerShell 블로그 및 리소스를 찾을 수 있습니다. 그런 다음 전문 지식을 개발 하면서 아이디어를 자유롭게 기여 하세요.

[PowerShell 모듈 브라우저](/powershell/module/) 명령줄 도움말 항목의 최신 버전을 제공 합니다.

## <a name="class-libraries"></a>클래스 라이브러리

[System.object](/dotnet/api/System.Management.Automation) 이 네임 스페이스는 Windows PowerShell에 대 한 루트 네임 스페이스입니다. 사용자 지정 cmdlet을 구현 하는 데 필요한 클래스, 열거형 및 인터페이스를 포함 합니다. 특히, [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 클래스는 모든 Cmdlet 클래스가 파생 되어야 하는 기본 클래스입니다. Cmdlet에 대 한 자세한 내용은을 참조 하십시오.

[System.object](/dotnet/api/System.Management.Automation.Provider) 이 네임 스페이스는 Windows PowerShell 공급자를 구현 하는 데 필요한 클래스, 열거형 및 인터페이스를 포함 합니다. 특히, [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 클래스는 모든 Windows PowerShell 공급자 클래스가 파생 되어야 하는 기본 클래스입니다.

[Microsoft](/dotnet/api/Microsoft.PowerShell.Commands) powershell .이 네임 스페이스에는 Windows PowerShell에서 구현 하는 cmdlet 및 공급자에 대 한 클래스가 포함 되어 있습니다. 마찬가지로 *YourName*를 만드는 것이 좋습니다. 구현 하는 cmdlet에 대 한 명령 네임 스페이스입니다.

[이 네임](/dotnet/api/System.Management.Automation.Host) 스페이스는 cmdlet이 사용자와 Windows PowerShell 간의 상호 작용을 정의 하는 데 사용 하는 클래스, 열거형 및 인터페이스를 포함 합니다.

[System.object](/dotnet/api/System.Management.Automation.Internal) .이 네임 스페이스는 다른 네임 스페이스 클래스에서 사용 되는 기본 클래스를 포함 합니다. 예를 들어, [system.web. Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) 클래스는 [system.object](/dotnet/api/System.Management.Automation.CmdletAttribute) 클래스에 대 한 기본 클래스입니다.

[Runspace](/dotnet/api/System.Management.Automation.Runspaces) 이 네임 스페이스는 Windows PowerShell runspace를 만드는 데 사용 되는 클래스, 열거형 및 인터페이스를 포함 합니다. 이 컨텍스트에서 Windows PowerShell runspace는 하나 이상의 Windows PowerShell 파이프라인이 cmdlet을 호출 하는 컨텍스트입니다. 즉, cmdlet은 Windows PowerShell runspace 컨텍스트 내에서 작동 합니다. PowerShell runspace aboutWindows에 대 한 자세한 내용은 [Windows Powershell runspace](hosting/creating-runspaces.md)을 참조 하세요.
