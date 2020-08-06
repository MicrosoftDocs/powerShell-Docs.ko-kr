---
title: 'GetProc04 (c #) 샘플 코드 | Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: dd3965ee504641b1b629ba203090ee14c670da43
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771892"
---
# <a name="getproc04-c-sample-code"></a>GetProc04(C#) 코드 샘플

다음 코드에서는 `Get-Process` 종료 되지 않는 오류를 보고 하는 cmdlet의 구현을 보여 줍니다. 이 구현은 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하 여 종료 되지 않는 오류를 보고 합니다.

> [!NOTE]
> Windows Vista 및 .NET Framework 3.0 런타임 구성 요소에 대 한 Microsoft Windows 소프트웨어 개발 키트를 사용 하 여이 getprov04.cs cmdlet에 대 한 c # 소스 파일 ()을 다운로드할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
> 다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .

## <a name="code-sample"></a>코드 예제

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs" range="11-98":::

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
