---
title: GetProc03 샘플 코드 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: 0cfb5c203c97a4d20e7fadf8183e608e9e31b881
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058252"
---
# <a name="getproc03-vbnet-sample-code"></a>GetProc03(VB.NET) 코드 샘플

다음 코드의 구현을 보여 줍니다는 `Get-Process` 받아들일 수 있는 cmdlet은 파이프라인 입력 합니다. 이 구현에서 정의 된 `Name` 파이프라인 입력을 허용 하는 매개 변수는 제공 된 이름을 기반으로 로컬 컴퓨터에서 프로세스 정보를 검색 하 고 사용 하 여는 [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) 메서드 개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 합니다.

## <a name="code-sample"></a>코드 예제

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->