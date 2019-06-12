---
title: Windows PowerShell 형식 지정 파일 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830256"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell 형식 지정 파일

몇 가지 서식 파일을 제공 하는 Windows PowerShell (. format.ps1xml) 설치 디렉터리에 있는 (`$pshome`). 이러한 각 파일에는.NET 개체의 특정 집합에 대 한 기본 표시를 정의합니다. 이러한 파일을 변경할 수 없습니다. 그러나 사용자 고유의 사용자 지정 서식 파일 만들기에 대 한 참조로 사용할 수 있습니다.

`Certificate.Format.ps1xml` X.509 인증서와 같은 인증서 저장소 및 인증서 저장소에서 개체의 표시를 정의합니다.

`DotNetTypes.Format.ps1xml` CultureInfo, FileVersionInfo, 및 EventLogEntry 개체와 같은 기타.NET 개체의 표시를 정의합니다.

`FileSystem.Format.ps1xml` 파일 및 디렉터리 개체와 같은 파일 시스템 개체의 표시를 정의합니다.

`Help.Format.ps1xml` 사용 하는 다른 뷰를 정의 합니다 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) 자세한 전체, 매개 변수 및 예제 뷰와 같은 cmdlet.

`PowerShellCore.Format.ps1xml` 반환 된 개체와 같은 Windows PowerShell 핵심 cmdlet에서 생성 된 개체의 표시를 정의 합니다 [Get-member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) 하 고 [Get-history](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlet.

`PowerShellTrace.Format.ps1xml` 생성 된 것과 같은 추적 개체의 표시를 정의 합니다 [Trace-command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet.

`Registry.Format.ps1xml` 키 및 항목 개체와 같은 레지스트리 개체의 표시를 정의합니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
