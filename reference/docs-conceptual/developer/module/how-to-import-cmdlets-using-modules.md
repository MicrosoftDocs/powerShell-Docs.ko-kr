---
title: 모듈을 사용 하 여 Cmdlet을 가져오는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 840c5bc92d718ec4e54d864dc5e012cd33f83905
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811322"
---
# <a name="how-to-import-cmdlets-using-modules"></a>모듈을 사용하여 Cmdlet을 가져오는 방법

이 문서에서는 이진 모듈을 사용 하 여 cmdlet을 PowerShell 세션으로 가져오는 방법을 설명 합니다.

> [!NOTE]
> 모듈의 멤버에는 cmdlet, 공급자, 함수, 변수, 별칭 등이 포함 될 수 있습니다. 스냅인은 cmdlet 및 공급자만 포함할 수 있습니다.

## <a name="how-to-load-cmdlets-using-a-module"></a>모듈을 사용 하 여 cmdlet을 로드 하는 방법

1. Cmdlet이 구현 되는 어셈블리 파일과 이름이 같은 모듈 폴더를 만듭니다. 이 절차에서는 Windows 폴더에 module 폴더가 만들어집니다 `system32` .

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. `PSModulePath`환경 변수에 새 모듈 폴더에 대 한 경로가 포함 되어 있는지 확인 합니다. 기본적으로 시스템 폴더는 환경 변수에 이미 추가 되어 `PSModulePath` 있습니다. 를 보려면 `PSModulePath` 을 입력 `$env:PSModulePath` 합니다.

1. Cmdlet 어셈블리를 모듈 폴더에 복사 합니다.

1. `.psd1`모듈의 루트 폴더에 모듈 매니페스트 파일 ()을 추가 합니다. PowerShell은 모듈 매니페스트를 사용 하 여 모듈을 가져옵니다. 자세한 내용은 [PowerShell 모듈 매니페스트를 작성 하는 방법](../module/how-to-write-a-powershell-module-manifest.md)을 참조 하세요.

1. 다음 명령을 실행 하 여 cmdlet을 세션에 추가 합니다.

   `Import-Module [Module_Name]`

   이 절차를 사용 하 여 cmdlet을 테스트할 수 있습니다. 어셈블리의 모든 cmdlet을 세션에 추가 합니다. 모듈에 대 한 자세한 내용은 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[PowerShell 모듈 매니페스트를 작성하는 방법](../module/how-to-write-a-powershell-module-manifest.md)

[PowerShell 모듈 가져오기](../module/importing-a-powershell-module.md)

[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[모듈 설치](../module/installing-a-powershell-module.md)

[PSModulePath 설치 경로 수정](../module/modifying-the-psmodulepath-installation-path.md)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](../cmdlet/cmdlet-overview.md)
