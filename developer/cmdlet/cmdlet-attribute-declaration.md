---
title: Cmdlet 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068626"
---
# <a name="cmdlet-attribute-declaration"></a>Cmdlet 특성 선언

Cmdlet 특성 cmdlet으로 Microsoft.NET Framework 클래스를 식별 하 고 동사와 명사는 cmdlet을 호출 하는 데를 지정 합니다.

## <a name="syntax"></a>구문

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>매개 변수

`VerbName` ([System.String](/dotnet/api/System.String)) 필요 합니다. Cmdlet 동사를 지정합니다. 이 동사는 cmdlet에서 수행 하는 동작을 지정 합니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md) 하 고 [개발 지침 필요한](./required-development-guidelines.md)합니다.

`NounName` ([System.String](/dotnet/api/System.String)) 필요 합니다. Cmdlet 명사를 지정합니다. 이 명사는 cmdlet을 실행 하는 리소스를 지정 합니다. Cmdlet 명사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 선언](./cmdlet-class-declaration.md) 하 고 [개발 지침 것이 좋습니다 강력한](./strongly-encouraged-development-guidelines.md)합니다.

`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) 명명 된 매개 변수는 선택 사항입니다. `True` cmdlet에 대 한 호출을 지원함을 나타냅니다 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) cmdlet을 사용 하 여 시스템을 변경 하는 동작을 수행 하기 전에 사용자에 게 제공 하는 메서드. `False`를 기본값인 cmdlet에 대 한 호출을 지원 하지 않음을 나타냅니다 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드. 확인 요청에 대 한 자세한 내용은 참조 하십시오 [요청 확인](./requesting-confirmation-from-cmdlets.md)합니다.

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) 명명 된 매개 변수는 선택 사항입니다. 호출 하 여 cmdlet의 작업은 확인 하는 경우 지정 된 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 메서드. [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (기본값: 보통) 하 여 cmdlet의 ConfirmImpact 값이 값 보다 크거나 같은 경우에 호출 수를 `$ConfirmPreference` 변수입니다. 이 매개 변수를 지정 해야 경우에만 `SupportsShouldProcess` 매개 변수를 지정 합니다.

`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) 명명 된 매개 변수는 선택 사항입니다. Windows PowerShell 런타임이 사용 하도록 설정 하는 매개 변수를 확인할 수를 사용 하는 기본 매개 변수 집합을 지정 합니다. 이 경우 unique 매개 변수 각 매개 변수의 필수 매개 변수를 설정 하 여 제거할 수 있다는 것을 확인 합니다.

한 경우에 Windows PowerShell 기본 매개 변수 집합 이름을 지정 하는 경우에 설정 기본 매개 변수를 사용할 수 없습니다. Windows PowerShell 런타임만 개체 형식에 따라 매개 변수 집합을 구분할 수 없습니다. 예를 들어 있는 경우 파일 경로 및 다른 집합으로 문자열을 사용 하는 하나의 매개 변수 집합은는 **FileInfo** Windows PowerShell에 전달 된 값을 기준으로 사용 하도록 설정 하는 매개 변수를 확인할 수 없습니다를 직접 개체를 cmdlet을 기본 매개 변수 집합을 사용 하지 않습니다. 이 경우 기본 매개 변수 세트 이름을 지정 하는 경우에 Windows PowerShell 모호한 매개 변수 집합 오류 메시지를 throw 합니다.

`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) 명명 된 매개 변수는 선택 사항입니다. `True` 트랜잭션 내에서 cmdlet을 사용할 수 있음을 나타냅니다. 때 `True` 를 지정 하면 Windows PowerShell 런타임에 추가 된 `UseTransaction` cmdlet의 매개 변수 목록에 매개 변수입니다. `False`를 기본값인 트랜잭션 내에서 cmdlet을 사용할 수 없음을 나타냅니다.

## <a name="remarks"></a>설명

- 함께 동사와 명사 등록된 cmdlet를 확인 하 고 스크립트 내에서 cmdlet을 호출 하려면 사용 됩니다.

- Cmdlet은 Windows PowerShell 콘솔에서 호출 되 면이 명령은 명령을 유사 합니다.

**VerbName-NounName**

- Windows PowerShell의 외부 리소스를 변경 하는 모든 cmdlet이 포함 되어야 합니다 `SupportsShouldProcess` cmdlet이 호출을 허용 하는 Cmdlet 특성을 선언할 때 키워드를 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) cmdlet은 해당 작업을 수행 하기 전에 합니다. 경우는 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 반환 `false`는 작업도 수행 되지 않아야 합니다. 생성 된 확인 요청에 대 한 자세한 내용은 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 호출을 참조 하십시오 [요청 확인](./requesting-confirmation-from-cmdlets.md)합니다.

합니다 `Confirm` 하 고 `WhatIf` cmdlet 매개 변수를 지 원하는 cmdlet에 대해서만 사용할 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 호출 합니다.

## <a name="example"></a>예제

다음 클래스 정의 대 한.NET Framework 클래스를 식별 하려면 Cmdlet 특성을 사용 하는 **Get-proc** 로컬 컴퓨터에서 실행 중인 프로세스에 대 한 정보를 검색 하는 cmdlet입니다.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

에 대 한 자세한 내용은 합니다 **Get-proc** cmdlet을 참조 하십시오 [GetProc 자습서](./getproc-tutorial.md)합니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
