---
title: 형식 지정 데이터를 내보내고 로드 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065209"
---
# <a name="loading-and-exporting-formatting-data"></a>형식 지정 데이터 로드 및 내보내기

서식 파일을 만든 후에 현재 세션으로 파일을 로드 하 여 세션의 형식 데이터를 업데이트 해야 합니다. (Windows PowerShell에서 제공 하는 서식 파일은 현재 세션에 열려 있을 때 등록 된 스냅인에서 로드 됩니다.) 현재 세션의 형식으로 데이터 업데이트 되 면 Windows PowerShell에서 로드 된 형식 지정 파일에 정의 된 보기와 연결 된.NET 개체를 표시 하려면 해당 데이터를 사용 합니다. 현재 세션으로 로드할 수 있는 형식 지정 파일의 수 제한은 없습니다. 형식 지정 데이터를 업데이트 하는 것 외에도 형식 지정 파일에 다시 현재 세션의 형식 데이터를 내보낼 수 있습니다.

## <a name="loading-format-data"></a>형식으로 데이터 로드

다음 메서드를 사용 하 여 현재 세션에 형식 지정 파일을 로드할 수 있습니다.

- 명령줄에서 현재 세션으로 형식 지정 파일을 가져올 수 있습니다. 사용 된 [Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) 다음 절차에 설명 된 대로 cmdlet.

- 서식 파일을 참조 하는 모듈 매니페스트를 만들 수 있습니다. 모듈을 사용 하면 배포에 대 한 파일 서식 지정 하면 패키지 있습니다. 사용 합니다 [New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) 매니페스트를 만드는 cmdlet 및 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 현재 세션으로 모듈을 로드 하는 cmdlet입니다. 모듈에 대 한 자세한 내용은 참조 하십시오 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)합니다.

- 서식 파일을 참조 하는 스냅인 만들 수 있습니다. 사용 된 [System.Management.Automation.PSSnapIn.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) 서식 파일을 참조 합니다. 것 배포용 패키지 cmdlet 모듈 및 모든 관련 형식 및 형식 파일을 사용 하는 것이 좋습니다. 모듈에 대 한 자세한 내용은 참조 하십시오 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)합니다.

- 호출 하는 경우 명령을 프로그래밍 방식으로, 여기서 명령이 실행 되는 초기 세션 상태 runspace에 형식 지정 파일 항목을 추가할 수 있습니다. 서식 파일을 추가 하는 데 사용 되는.NET 형식에 대 한 자세한 내용은 참조는 [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty =](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) 클래스입니다.

형식 지정 파일 로드 되 면 추가 됩니다 내부 목록에 Windows PowerShell 명령줄에서 개체를 표시할 때 사용 하는 뷰를 확인 하는. 목록의 시작 부분에 형식 지정 파일을 앞 수 또는 목록 끝에 추가할 수 있습니다. 서식 파일에이 목록에 추가 되는 위치를 파악 하는 것이 중요 Windows PowerShell 핵심 cmdlet에서 반환 되는 개체는 어떻게 변경 하려는 경우 같은 정의 된 기존 뷰를 포함 하는 개체에 대 한 뷰를 정의 하는 서식 파일을 로드 하는 경우  표시 됩니다. 개체에 대 한 전용 뷰를 정의 하는 서식 파일을 로드 하는 경우에 앞에서 설명한 방법 중 하나를 사용할 수 있습니다.  개체에 대 한 다른 뷰를 정의 하는 서식 파일을 로드 하는 경우 사용 해야 합니다 [Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 및 목록의 시작 부분에 대 한 파일 앞에 추가 합니다.

## <a name="storing-your-formatting-file"></a>서식 파일에 저장합니다.

서식 파일은 디스크에 저장 하는 것에 대 한 사항은 없습니다. 그러나으로 다음 폴더에 저장 하는 것이 좋습니다 강력한: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>가져오기-FormatData를 사용 하 여 서식 파일 로드

1. 디스크에 대 한 서식 파일을 저장 합니다.

2. 실행 합니다 [Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) 다음 명령 중 하나를 사용 하 여 cmdlet.

   목록 맨 앞으로는 파일 형식을 추가 하려면이 명령을 사용 하 여 합니다. 개체로 표시 되는 방식을 변경 하는 경우이 명령을 사용 합니다.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   형식을 추가 하려면 목록의 끝에는 파일에는이 명령을 사용 합니다.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   사용 하 여 파일을 추가 하는 [Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet을 제거할 수 없습니다 파일 목록에서 세션이 열려 있는 동안. 목록에서 서식 파일을 제거 하려면 세션을 닫아야 합니다.

## <a name="exporting-format-data"></a>내보내기 형식 데이터

여기에 지정 된 섹션 본문을 삽입 합니다.
