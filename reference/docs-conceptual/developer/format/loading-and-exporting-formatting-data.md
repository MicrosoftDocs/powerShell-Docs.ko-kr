---
ms.date: 09/13/2016
ms.topic: reference
title: 형식 지정 데이터 로드 및 내보내기
description: 형식 지정 데이터 로드 및 내보내기
ms.openlocfilehash: 38857526801051bf6d31d300d5be1a3fd2c80391
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666521"
---
# <a name="loading-and-exporting-formatting-data"></a>형식 지정 데이터 로드 및 내보내기

서식 파일을 만든 후에는 현재 세션으로 파일을 로드 하 여 세션의 형식 데이터를 업데이트 해야 합니다. Windows PowerShell에서 제공 하는 형식 지정 파일은 현재 세션을 열 때 등록 된 스냅인에 의해 로드 됩니다. 현재 세션의 형식 데이터가 업데이트 되 면 Windows PowerShell은 해당 데이터를 사용 하 여 로드 된 서식 지정 파일에 정의 된 뷰와 관련 된 .NET 개체를 표시 합니다. 현재 세션으로 로드할 수 있는 형식 지정 파일의 수에는 제한이 없습니다. 형식 지정 데이터를 업데이트 하는 것 외에도 현재 세션의 형식 데이터를 서식 파일에 다시 내보낼 수 있습니다.

## <a name="loading-format-data"></a>서식 데이터 로드

다음 메서드를 사용 하 여 형식 지정 파일을 현재 세션으로 로드할 수 있습니다.

- 명령줄에서 현재 세션으로 서식 파일을 가져올 수 있습니다. 다음 절차에서 설명 하는 것 처럼 [업데이트 FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet을 사용 합니다.

- 서식 파일을 참조 하는 모듈 매니페스트를 만들 수 있습니다. 모듈을 사용 하 여 배포용으로 서식 지정 파일을 패키지할 수 있습니다. [New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet을 사용 하 여 매니페스트를 만들고 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet을 사용 하 여 모듈을 현재 세션으로 로드 합니다. 모듈에 대 한 자세한 내용은 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)을 참조 하세요.

- 서식 파일을 참조 하는 스냅인을 만들 수 있습니다. [Add-pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) 를 사용 하 여 형식 지정 파일을 참조 합니다. Cmdlet을 패키지 하는 데 모듈을 사용 하 고 배포를 위해 관련 형식 지정 및 형식 파일을 사용 하는 것이 좋습니다. 모듈에 대 한 자세한 내용은 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)을 참조 하세요.

- 명령을 프로그래밍 방식으로 호출 하는 경우 명령이 실행 되는 runspace의 초기 세션 상태에 서식 파일 항목을 추가할 수 있습니다. 형식 지정 파일을 추가 하는 데 사용 되는 .NET 형식에 대 한 자세한 내용은 Runspace를 참조 하세요. [ Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) 클래스입니다.

서식 파일이 로드 되 면 Windows PowerShell에서 명령줄에 개체를 표시할 때 사용할 뷰를 결정 하는 데 사용 하는 내부 목록에 추가 됩니다. 서식 파일 앞에 서식 파일을 추가 하거나 목록의 끝에 추가할 수 있습니다. Windows PowerShell core cmdlet에 의해 반환 되는 개체가 표시 되는 방법을 변경 하려는 경우와 같이 기존 보기가 정의 된 개체에 대 한 뷰를 정의 하는 서식 파일을 로드 하는 경우 서식 파일을이 목록에 추가 하는 것이 중요 합니다. 개체에 대 한 유일한 뷰를 정의 하는 서식 파일을 로드 하는 경우 앞에서 설명한 방법 중 하나를 사용할 수 있습니다.  개체에 대 한 다른 뷰를 정의 하는 서식 파일을 로드 하는 경우에는 [업데이트 FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet을 사용 하 고 파일 앞에 파일을 추가 해야 합니다.

## <a name="storing-your-formatting-file"></a>서식 파일 저장

포맷 파일이 디스크에 저장 되는 위치에 대 한 요구 사항은 없습니다. 그러나 다음 폴더에 저장 하는 것이 좋습니다. `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Import-FormatData를 사용 하 여 서식 파일 로드

1. 포맷 파일을 디스크에 저장 합니다.

2. 다음 명령 중 하나를 사용 하 여 [업데이트 FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet을 실행 합니다.

   목록 앞에 서식 파일을 추가 하려면이 명령을 사용 합니다. 개체 표시 방법을 변경 하는 경우이 명령을 사용 합니다.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   형식 지정 파일을 목록의 끝에 추가 하려면이 명령을 사용 합니다.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   [업데이트-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet을 사용 하 여 파일을 추가한 후에는 세션이 열려 있는 동안 목록에서 파일을 제거할 수 없습니다. 목록에서 서식 파일을 제거 하려면 세션을 닫아야 합니다.

## <a name="exporting-format-data"></a>서식 데이터 내보내기

여기에 본문 섹션을 삽입합니다.
