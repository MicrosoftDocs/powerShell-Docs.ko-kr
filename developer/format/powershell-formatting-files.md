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
ms.openlocfilehash: 49344d32dfcef36a904772b4a7237646a63cb12a
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794640"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell 형식 지정 파일

몇 가지 서식 파일을 제공 하는 Windows PowerShell (. format.ps1xml) 설치 디렉터리에 있는 (`$pshome`). 이러한 각 파일에는.NET 개체의 특정 집합에 대 한 기본 표시를 정의합니다. 이러한 파일을 변경할 수 없습니다. 그러나 사용자 고유의 사용자 지정 서식 파일 만들기에 대 한 참조로 사용할 수 있습니다.

Certificate.Format.ps1xml은 x.509 인증서와 같은 인증서 저장소 및 인증서 저장소에서 개체의 표시를 정의합니다.

DotNetTypes.Format.ps1xml은 CultureInfo, FileVersionInfo, 및 EventLogEntry 개체와 같은 기타.NET 개체의 표시를 정의합니다.

FileSystem.Format.ps1xml 파일 및 디렉터리 개체와 같은 파일 시스템 개체의 표시를 정의합니다.

Help.Format.ps1xml 정의에서 사용 하는 다양 한 보기를 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) 자세한 전체, 매개 변수 및 예제 뷰와 같은 cmdlet.

PowerShellCore.Format.ps1xml 반환한 개체와 같은 Windows PowerShell 핵심 cmdlet에서 생성 된 개체의 표시를 정의 합니다 [Get-member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) 하 고 [Get-history](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlet.

PowerShellTrace.Format.ps1xml 등에서 생성 된 항목 추적 개체의 표시를 정의 합니다 [Trace-command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet.

Registry.Format.ps1xml 키 및 항목 개체와 같은 레지스트리 개체의 표시를 정의합니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
