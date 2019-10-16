---
title: RunSpace03 (C#) 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 49911f2779110c04c0e89f09fdf76ee9cd930edb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360212"
---
# <a name="runspace03-c-code-sample"></a>RunSpace03(C#) 코드 샘플

다음은 " C# 지정 된 스크립트를 실행 하는 콘솔 응용 프로그램 만들기"에 설명 된 콘솔 응용 프로그램의 소스 코드입니다. 이 샘플에서는 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하 여 스크립트에 전달 된 프로세스 이름 목록을 사용 하 여 프로세스 정보를 검색 하는 스크립트를 실행 합니다. 입력 개체를 스크립트에 전달 하는 방법 및 출력 개체 뿐만 아니라 오류 개체를 검색 하는 방법을 보여 줍니다.

> [!NOTE]
> Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 샘플에 대 한 소스 파일 (runspace03.cs)을 다운로드할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
> 다운로드 된 원본 파일은 **\<PowerShell 샘플 >** 디렉터리에서 사용할 수 있습니다.

## <a name="code-sample"></a>코드 샘플

[!code-csharp[Runspace03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
