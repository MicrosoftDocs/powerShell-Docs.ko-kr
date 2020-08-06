---
title: 'GetProc03 (c #) 샘플 코드 | Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: 278c3f36bb975f9ea195978853e6539c0bd15084
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787124"
---
# <a name="getproc03-c-sample-code"></a>GetProc03(C#) 코드 샘플

다음 코드는 `Get-Process` 파이프라인 입력을 수락할 수 있는 cmdlet의 구현을 보여 줍니다. 이 구현은 `Name` 파이프라인 입력을 허용 하 고, 제공 된 이름에 따라 로컬 컴퓨터에서 프로세스 정보를 검색 하 고, 개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 [WriteObject (system.string, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 메서드를 사용 하는 매개 변수를 정의 합니다.

> [!NOTE]
> Windows Vista 및 .NET Framework 3.0 런타임 구성 요소에 대 한 Microsoft Windows 소프트웨어 개발 키트를 사용 하 여이 getprov03.cs cmdlet에 대 한 c # 소스 파일 ()을 다운로드할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
> 다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .

## <a name="code-sample"></a>코드 예제

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a>참고 항목

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
