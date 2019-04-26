---
title: 필터 매개 변수를 입력 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067691"
---
# <a name="input-filter-parameters"></a>입력 필터 매개 변수

Cmdlet을 정의할 수 있습니다 `Filter`, `Include`, 및 `Exclude` 매개 변수를 cmdlet에 영향을 주는 입력된 개체 집합을 필터링 합니다.

입력된 개체 집합으로 지정 됩니다는 일반적으로 `InputObject`, `Path`, 또는 `Name` 매개 변수입니다. 예를 들어 cmdlet을 가질 수 있습니다는 `Path` 와일드 카드 문자 및 각 경로 지점을 입력 개체를 사용 하 여 여러 경로 허용 하는 매개 변수입니다. 함께 사용 합니다 `Filter`, `Include`, 및 `Exclude` 매개 변수 추가 cmdlet를 호출할 때마다에서 작동 하는 경로 정규화 합니다.

## <a name="include-and-exclude-parameters"></a>Include 및 Exclude 매개 변수

합니다 `Include` 고 `Exclude` 매개 변수를 cmdlet으로 전달 하는 입력된 개체 집합에서 제외 되거나 포함 되는 개체를 식별 합니다. 필터는 표준 와일드 카드 언어로 표현 될 수 있습니다 하는 경우 이러한 매개 변수를 사용 합니다. (와일드 카드 문자에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수에서 와일드 카드를 지 원하는](./supporting-wildcard-characters-in-cmdlet-parameters.md).) `Include` 매개 변수 이름이 포함 필터와 일치 하는 모든 개체를 포함 합니다. `Exclude` 매개 변수 이름이 필터와 일치 하는 모든 개체를 제외 합니다.

## <a name="filter-parameter"></a>Filter 매개 변수

`Filter` 매개 변수는 표준 와일드 카드 언어로 표시 되지 않을 필터를 지정 합니다. 예를 들어, 서비스 인터페이스 ADSI (Active Directory) 또는 SQL 필터 전달 될 수 있는 cmdlet을 통해 해당 `Filter` 매개 변수입니다. Windows PowerShell에서 제공 하는 cmdlet에 이러한 필터는 cmdlet을 사용 하 여 데이터 저장소에 액세스 하는 Windows PowerShell 공급자에 의해 지정 됩니다. 각 공급자는 일반적으로 자체 필터를 정의합니다.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>필터링 입력된 개체 집합이 지정 된 경우

입력된 개체 집합이 지정 된 경우 일반적으로 즉, 모든 개체에 대해 필터링 합니다. 자세한 내용은[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)합니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)