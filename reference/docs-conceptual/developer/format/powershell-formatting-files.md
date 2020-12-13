---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 형식 지정 파일
description: Windows PowerShell 형식 지정 파일
ms.openlocfilehash: 7fa58a3463dc4b2a23d38d161d83387744334d44
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666368"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell 형식 지정 파일

Windows PowerShell에서는 설치 디렉터리 ()에 있는 여러 서식 파일 (.format.ps1xml)을 제공 `$pshome` 합니다. 이러한 각 파일은 특정 .NET 개체 집합에 대 한 기본 표시를 정의 합니다. 이러한 파일은 변경 하면 안 됩니다. 그러나 사용자 지정 서식 파일을 만들기 위한 참조로 사용할 수 있습니다.

`Certificate.Format.ps1xml` 인증서 저장소에 있는 개체 (예: x.509 인증서 및 인증서 저장소)의 표시를 정의 합니다.

`DotNetTypes.Format.ps1xml` CultureInfo, FileVersionInfo 및 EventLogEntry 개체와 같은 기타 .NET 개체의 표시를 정의 합니다.

`FileSystem.Format.ps1xml` 파일 및 디렉터리 개체와 같은 파일 시스템 개체의 표시를 정의 합니다.

`Help.Format.ps1xml` Detailed, full, parameters 및 example 뷰와 같이 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet에서 사용 하는 다양 한 뷰를 정의 합니다.

`PowerShellCore.Format.ps1xml` Windows PowerShell 핵심 cmdlet에 의해 생성 된 개체의 표시를 정의 합니다 (예: [Get Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) 및 [get History](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlet에서 반환 된 개체).

`PowerShellTrace.Format.ps1xml` 추적 [명령](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet에 의해 생성 된 것과 같은 추적 개체의 표시를 정의 합니다.

`Registry.Format.ps1xml` 키 및 항목 개체와 같은 레지스트리 개체의 표시를 정의 합니다.

## <a name="see-also"></a>관련 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](../cmdlet/writing-a-windows-powershell-cmdlet.md)
