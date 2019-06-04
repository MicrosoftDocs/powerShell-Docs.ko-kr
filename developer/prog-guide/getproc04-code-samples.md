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
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081668"
---
# <a name="getproc04-code-samples"></a>GetProc04 코드 샘플

GetProc04 샘플 cmdlet에 대 한 코드 예제는 다음과 같습니다. 이 `Get-Process` 에 설명 된 cmdlet 샘플 [Your cmdlet 종료 되지 않는 오류 보고를 추가](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)합니다. 이렇게 `Get-Process` cmdlet 호출을 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드 때마다 프로세스 정보를 검색 하는 동안 잘못 된 작업 예외가 throw 됩니다.

> [!NOTE]
> 다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 Get-proc cmdlet에 대 한 소스 파일 (getprov04.cs). 다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.
>
> 다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.

전체 샘플 코드를 다음 항목을 참조 하십시오.

|Language|항목|
|--------------|-----------|
|C#|[GetProc04 (C#) 코드 샘플](./getproc04-csharp-sample-code.md)|
|VB.NET|[GetProc04 (VB.NET) 샘플 코드](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)