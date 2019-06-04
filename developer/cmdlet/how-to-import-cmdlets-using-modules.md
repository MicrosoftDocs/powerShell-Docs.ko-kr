---
title: 모듈을 사용 하 여 Cmdlet을 가져오는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067980"
---
# <a name="how-to-import-cmdlets-using-modules"></a>모듈을 사용하여 Cmdlet을 가져오는 방법

이 항목에서는 이진 모듈을 사용 하 여 Windows PowerShell 세션에 cmdlet을 가져오는 방법을 설명 합니다.

> [!NOTE]
> 모듈의 멤버 cmdlet, 공급자, 함수, 변수, 별칭 및 등을 포함할 수 있습니다. 스냅인에는 cmdlet과 공급자만 포함 될 수 있습니다.

## <a name="how-to-load-cmdlets-using-a-module"></a>모듈을 사용 하 여 cmdlet을 로드 하는 방법

1. Cmdlet 구현 되는 어셈블리 파일 이름이 같은 모듈 폴더를 만듭니다. 이 절차에서는 모듈 폴더에 만들어집니다는 `system32` 폴더입니다.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. 했는지를 `PSModulePath` 환경 변수는 새 모듈 폴더에 경로 포함 합니다. 기본적으로 시스템 폴더는 이미 추가 하 여 `PSModulePath` 환경 변수입니다.

3. Cmdlet은 어셈블리 모듈 폴더에 복사 합니다.

4. Cmdlet은 세션에 추가 하려면 다음 명령을 실행 합니다.

   `import-module [Module_Name]`

   Cmdlet을 테스트 하려면이 절차를 사용할 수 있습니다. 세션에 어셈블리의 모든 cmdlet을 추가합니다. 모듈에 대 한 자세한 내용은 다양 한 유형의 모듈을 로드할 모듈 및 내보낸 된 모듈의 요소를 제한 하는 방법에 대 한 다양 한 방법 참조 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)합니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[모듈 설치](../module/installing-a-powershell-module.md)