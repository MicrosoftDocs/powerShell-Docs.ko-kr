---
description: 기본 Get-Member 결과에서 클래스 멤버를 숨기는 Hidden 키워드에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hidden?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hidden
ms.openlocfilehash: 641ebdc942186db90a23f4c784a0f1b3c295cae9
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224969"
---
# <a name="about_hidden"></a>about_Hidden

## <a name="short-description"></a>간단한 설명
기본 Get-Member 결과에서 클래스 멤버를 숨기는 Hidden 키워드에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

스크립트에서 Hidden 키워드를 사용 하는 경우 기본적으로 클래스의 멤버를 숨깁니다. Hidden 키워드는 속성, 메서드 (생성자, 이벤트, 별칭 속성 및 정적 멤버를 비롯 한 다른 멤버 형식 (Get-Member cmdlet의 기본 결과) 및 IntelliSense 및 탭 완성 결과를 숨길 수 있습니다. 숨겨진 키워드를 사용 하 여 숨겨진 멤버를 표시 하려면-Force 매개 변수를 Get-Member 명령에 추가 합니다.

숨겨진 멤버를 정의 하는 클래스에서 완료가 발생 하지 않은 경우에는 탭 완성 또는 IntelliSense를 사용 하 여 숨겨진 멤버를 표시 하지 않습니다.

새 특성인 System.management.automation.hiddenattribute가 추가 되어 C \# 코드가 PowerShell 내에서 동일한 의미 체계를 가질 수 있습니다.

Hidden 키워드는 클래스 내에서 다른 사용자가 보거나 편집할 수 없는 속성 및 메서드를 만드는 데 유용 합니다.

Hidden 키워드는 클래스의 멤버를 보거나 변경 하는 방법에는 영향을 주지 않습니다. PowerShell의 모든 언어 키워드와 마찬가지로 Hidden은 대/소문자를 구분 하지 않으며 숨겨진 멤버는 여전히 public입니다.

Hidden은 사용자 지정 클래스와 함께 PowerShell 5.0에서 도입 되었습니다.

## <a name="example"></a>예제

다음 예제에서는 클래스 정의에서 Hidden 키워드를 사용 하는 방법을 보여 줍니다. Car 클래스 메서드 드라이브에는 탑승 속성이 있습니다 .이 속성은 확인 하거나 변경할 필요가 없습니다. (차량 클래스에서 드라이브가 호출 되는 횟수, 클래스의 사용자에 게 중요 하지 않은 메트릭)만 포함 됩니다. 예를 들어 자동차를 구입할 때 자동차를 구입할 때 판매자에 게 판매를 요청 하지 않을 수 있습니다.

클래스의 사용자가이 속성을 변경할 필요는 거의 없으므로 Hidden 키워드를 사용 하 여 Get-Member 및 자동 완성 결과에서 속성을 숨길 수 있습니다.

숨겨진 키워드를 속성과 해당 데이터 형식의 동일한 문 줄에 입력 하 여 추가 합니다. 키워드는이 줄에서 순서에 관계 없이 사용할 수 있지만 숨겨진 키워드를 사용 하 여 문을 시작 하면 나중에 숨겨진 모든 멤버를 더 쉽게 식별할 수 있습니다.

```powershell
class Car
{
   # Properties
   [String] $Color
   [String] $ModelYear
   [int] $Distance

   # Method
   [int] Drive ([int]$miles)
   {
      $this.Distance += $miles
      $this.rides++
      return $this.Distance
   }

   # Hidden property of the Drive method
    hidden [int] $rides = 0
}
```

이제 Car 클래스의 새 인스턴스를 만들고 \$ testcar 변수에 저장 합니다.

```powershell
$TestCar = [Car]::new()
```

새 인스턴스를 만든 후에는 $TestCar 변수의 내용을 Get 멤버에 파이프 합니다. 탑승 속성은 Get-Member 명령 결과에 나열 된 멤버에 속하지 않습니다.

```output
PS C:\Windows\system32> $TestCar | Get-Member

   TypeName: Car

Name        MemberType Definition
----        ---------- ----------
Drive       Method     int Drive(int miles)
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
ToString    Method     string ToString()
Color       Property   string Color {get;set;}
Distance    Property   int Distance {get;set;}
ModelYear   Property   string ModelYear {get;set;}

```

이제 Get-Member를 다시 실행 해 보세요. 하지만 이번에는-Force 매개 변수를 추가 합니다.
결과에는 기본적으로 숨겨져 있는 다른 멤버 중 숨겨진 탑승 속성이 포함 됩니다.

```output
PS C:\Windows\system32> $TestCar | Get-Member -Force

   TypeName: Car

Name          MemberType   Definition
----          ----------   ----------
pstypenames   CodeProperty System.Collections.ObjectModel.Collection`1
psadapted     MemberSet    psadapted {Color, ModelYear, Distance,
psbase        MemberSet    psbase {Color, ModelYear, Distance,...
psextended    MemberSet    psextended {}
psobject      MemberSet    psobject {BaseObject, Members,...
Drive         Method       int Drive(int miles)
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
get_Color     Method       string get_Color()
get_Distance  Method       int get_Distance()
get_ModelYear Method       string get_ModelYear()
get_rides     Method       int get_rides()
set_Color     Method       void set_Color(string )
set_Distance  Method       void set_Distance(int )
set_ModelYear Method       void set_ModelYear(string )
set_rides     Method       void set_rides(int )
ToString      Method       string ToString()
Color         Property     string Color {get;set;}
Distance      Property     int Distance {get;set;}
ModelYear     Property     string ModelYear {get;set;}
rides         Property     int rides {get;set;}

```

## <a name="see-also"></a>참고 항목

[about_Classes](about_Classes.md)

[about_Language_Keywords](about_Language_Keywords.md)

[about_Wildcards](about_Wildcards.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)
