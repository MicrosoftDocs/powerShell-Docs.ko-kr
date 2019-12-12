---
title: GetProc04 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 8326d1f47ce07698f09ade9ba97154ecc358465a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417463"
---
# <a name="getproc04-code-samples"></a>GetProc04 코드 샘플

GetProc04 sample cmdlet에 대 한 코드 샘플은 다음과 같습니다. Cmdlet에 종료 되지 않는 [오류 보고 추가](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)에 설명 된 `Get-Process` cmdlet 샘플입니다. 이 `Get-Process` cmdlet은 프로세스 정보를 검색 하는 동안 잘못 된 작업 예외가 throw 될 때마다 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 합니다.

> [!NOTE]
> Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 getprov04.cs cmdlet에 대 한 원본 파일 ()을 다운로드할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
>
> 다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.

전체 샘플 코드는 다음 항목을 참조 하세요.

|Language|항목|
|--------------|-----------|
|C#|[GetProc04 (C#) 샘플 코드](./getproc04-csharp-sample-code.md)|
|VB.NET|[GetProc04 (VB.NET) 샘플 코드](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
