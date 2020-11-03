---
description: Windows RT 8.1의 Windows PowerShell 4.0에 대 한 제한 사항을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_rt?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_RT
ms.openlocfilehash: 323f06a7a0d8253417510503c1011ac02c20179f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222434"
---
# <a name="about-windows-rt"></a>Windows RT 정보

## <a name="short-description"></a>간단한 설명

Windows RT 8.1의 Windows PowerShell 4.0에 대 한 제한 사항을 설명 합니다.

## <a name="long-description"></a>자세한 설명

Windows RT 8.1 운영 체제는 ARM (Advanced RISC Machine) 프로세서를 사용 하는 컴퓨터 및 장치 (예: 컴퓨터와 함께 제공 되는 운영 체제가 설치 된 Microsoft Surface 2)에 설치 됩니다.

Windows PowerShell 4.0은 Windows RT 8.1에 포함 되어 있습니다. 모든 cmdlet, 공급자 및 모듈 및 Windows PowerShell 2.0 이상 릴리스를 위해 설계 된 대부분의 스크립트는 Windows RT 8.1에서 변경 없이 실행 됩니다.

Windows RT 8.1에는 모든 Windows 기능이 포함 되어 있지 않기 때문에 일부 Windows PowerShell 기능은 다른 방식으로 작동 하거나 Windows RT 기반 장치에서 작동 하지 않습니다. 다음 목록에서는 이러한 차이점을 설명 합니다.

- Windows PowerShell ISE는에 포함 되어 있지 않으며 Windows RT 8.1에서 실행할 수 없습니다.
  Windows PowerShell ISE에는 Windows RT 8.1에 포함 되지 않은 Windows Presentation Foundation 필요 합니다.

- Windows PowerShell 원격 및 WinRM 서비스는 기본적으로 사용 하지 않도록 설정 되어 있습니다.
  원격 기능을 사용 하도록 설정 하려면 Enable-PSRemoting cmdlet을 실행 합니다. 또한 Set-Service cmdlet을 실행 하 여 WinRM 서비스의 시작 유형을 자동 또는 자동 (지연 된 시작)으로 설정 합니다.

  원격을 사용 하지 않도록 설정 하는 동안 Windows PowerShell 원격을 사용 하 여 다른 컴퓨터에서 명령을 실행할 수 있지만 다른 컴퓨터는 Windows RT 장치에서 명령을 실행할 수 없습니다. 또한 암시적 원격 작업 즉, cmdlet 또는 스크립트에 기본 제공 되 고 추가 매개 변수를 사용 하 여 명시적으로 요청 되지 않은 원격 서비스
  - Windows RT 8.1에서 실행 되는 Windows PowerShell에서는 작동 하지 않습니다.

- 도메인에 가입 된 컴퓨팅 및 Kerberos 인증은 Windows RT 8.1에서 지원 되지 않습니다. Windows PowerShell을 사용 하 여 이러한 기능을 추가 하거나 관리할 수 없습니다.

- Windows RT 8.1에서 지원 되지 않는 Microsoft .NET Framework 클래스도 windows RT 8.1의 Windows PowerShell에서 지원 되지 않습니다.

- 트랜잭션은 Windows RT 8.1에서 사용 하도록 설정 되지 않습니다. 트랜잭션 cmdlet (예: UseTransaction) 및 트랜잭션 매개 변수 (예:)가 제대로 작동 하지 않습니다.

- Windows RT 8.1 장치의 모든 Windows PowerShell 세션은 ConstrainedLanguage 언어 모드를 사용 합니다. ConstrainedLanguage 언어 모드는 UMCI (사용자 모드 코드 무결성)와 함께 사용 됩니다. 모든 Windows cmdlet 및 Windows PowerShell 언어 요소를 허용 하지만, 사용자가 Windows PowerShell을 사용 하 여 UMCI 보호를 우회 하거나 위반할 수 없도록 유형을 제한 합니다.

ConstrainedLanguage 언어 모드에 대 한 자세한 내용은 [about_Language_Modes](about_Language_Modes.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Language_Modes](about_Language_Modes.md)

[about_Remote](about_Remote.md)

[about_Windows_PowerShell_ISE](about_Windows_PowerShell_ISE.md)
