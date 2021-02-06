---
description: '**CimSession** 개체와 CIM 세션과 PowerShell 세션 간의 차이점에 대해 설명 합니다.'
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CimSession
ms.openlocfilehash: 556c3db21ea5e410b28f5546cdd8a433e0bc3e50
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605252"
---
# <a name="about-cimsession"></a>CimSession 정보

## <a name="short-description"></a>간단한 설명
**CimSession** 개체와 CIM 세션과 PowerShell 세션 간의 차이점에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

CIM (CIM(Common Information Model)) 세션은 로컬 컴퓨터 또는 원격 컴퓨터에 대 한 연결을 나타내는 클라이언트 쪽 개체입니다. PowerShell 세션 (PSSessions) 대신 CIM 세션을 사용할 수 있습니다. 두 방법 모두 이점이 있습니다.

Cmdlet을 사용 `New-CimSession` 하 여 컴퓨터 이름, 연결에 사용 되는 프로토콜, 세션 id 및 인스턴스 id와 같은 연결 정보가 포함 된 CIM 세션을 만들 수 있습니다.

연결을 설정 하는 데 필요한 정보를 지정 하는 **CimSession** 개체를 만든 후에 PowerShell은 연결을 즉시 설정 하지 않습니다. Cmdlet에서 CIM 세션을 사용 하는 경우 PowerShell은 지정 된 컴퓨터에 연결한 다음 cmdlet이 완료 되 면 PowerShell에서 연결을 종료 합니다.

CIM 세션을 사용 하는 대신 **PSSession** 을 만드는 경우 PowerShell에서 연결 설정의 유효성을 검사 한 다음 연결을 설정 하 고 유지 관리 합니다. CIM 세션을 사용 하는 경우 PowerShell은 필요할 때까지 네트워크 연결을 열지 않습니다. PowerShell 세션에 대 한 자세한 내용은 [about_PSSessions](about_PSSessions.md)를 참조 하세요.

## <a name="when-to-use-a-cim-session"></a>CIM 세션을 사용 하는 경우

WMI(Windows Management Instrumentation) (WMI) 공급자 또는 CIM을 사용 하는 cmdlet만 CIM 세션을 허용 WS-Man 합니다. 다른 cmdlet의 경우에는 pssession **을 사용 합니다**.

CIM 세션을 사용 하는 경우 PowerShell은 로컬 클라이언트에서 cmdlet을 실행 합니다. CIM 세션을 사용 하 여 WMI 공급자에 연결 합니다. 대상 컴퓨터에는 PowerShell 또는 Windows 운영 체제 버전도 필요 하지 않습니다.

반대로, **PSSession** 을 사용 하 여 실행 되는 cmdlet은 대상 컴퓨터에서 실행 됩니다.
대상 시스템의 PowerShell이 필요 합니다. 또한 cmdlet은 로컬 컴퓨터에 데이터를 다시 보냅니다. PowerShell은 연결을 통해 전송 되는 데이터를 관리 하 고 Windows 원격 관리 (WinRM)로 설정 된 제한 내에 크기를 유지 합니다. CIM 세션은 WinRM 제한을 적용 하지 않습니다.

## <a name="using-cdxml-cmdlets"></a>CDXML cmdlet 사용

CIM 기반 CDXML (Cmdlet 정의 XML) cmdlet은 WMI 공급자를 사용 하도록 작성할 수 있습니다. 모든 WMI 공급자는 **CimSession** 개체를 사용 합니다. CDXML에 대 한 자세한 내용은 [cdxml 정의 및 용어](/previous-versions/windows/desktop/wmi_v2/cdxml-overview)를 참조 하세요.

CDXML cmdlet에는 **CimSession** 개체의 배열을 사용할 수 있는 자동 **CimSession** 매개 변수가 있습니다. 기본적으로 PowerShell은 동시 CIM 연결 수를 15로 제한 합니다. 이 제한은 **ThrottleLimit** 을 구현 하는 CDXML cmdlet에 의해 재정의 될 수 있습니다. **ThrottleLimit** 을 이해 하려면 개별 cmdlet 설명서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[New-CimSession](xref:CimCmdlets.New-CimSession)

[about_PSSessions](about_PSSessions.md)

