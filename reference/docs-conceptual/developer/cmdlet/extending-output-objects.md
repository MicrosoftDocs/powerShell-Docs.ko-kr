---
ms.date: 09/13/2016
ms.topic: reference
title: 출력 개체 확장
description: 출력 개체 확장
ms.openlocfilehash: 9fea476e3032002bd206609313581cc6373dfddc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652907"
---
# <a name="extending-output-objects"></a>출력 개체 확장

형식 파일 (. types.ps1xml)을 사용 하 여 cmdlet, 함수 및 스크립트에 의해 반환 되는 .NET Framework 개체를 확장할 수 있습니다. 형식 파일은 기존 개체에 속성 및 메서드를 추가할 수 있는 XML 기반 파일입니다. 예를 들어 Windows PowerShell은 몇 가지 기존 .NET Framework 개체에 요소를 추가 하는 Types.ps1xml 파일을 제공 합니다. Types.ps1xml 파일은 Windows PowerShell 설치 디렉터리 ()에 있습니다 `$pshome` . 사용자 고유의 형식 파일을 만들어 이러한 개체를 추가로 확장 하거나 다른 개체를 확장할 수 있습니다. 형식 파일을 사용 하 여 개체를 확장 하는 경우 개체의 모든 인스턴스가 새 요소로 확장 됩니다.

## <a name="extending-the-systemarray-object"></a>System.object 개체 확장

다음 예에서는 Windows PowerShell이 Types.ps1xml 파일에서 [system.object](/dotnet/api/System.Array) 개체를 확장 하는 방법을 보여 줍니다. 기본적으로 [system.object](/dotnet/api/System.Array) 개체에는 `Length` 배열의 개체 수를 나열 하는 속성이 있습니다. 그러나 이름 "length"는 속성을 명확 하 게 설명 하지 않으므로 Windows PowerShell은 속성의 `Count` 값과 동일한 값을 표시 하는 alias 속성을 추가 합니다 `Length` . 다음 XML은 `Count` [system.object](/dotnet/api/System.Array) 형식에 속성을 추가 합니다.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

이 새 별칭 속성을 보려면 다음 예제에 표시 된 것 처럼 모든 배열에서 [Get Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) 명령을 사용 합니다.

```powershell
Get-Member -InputObject (1,2,3,4)
```

이 명령은 다음 결과를 반환 합니다.

```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```

`Count`속성 또는 속성 중 하나 `Length` 를 사용 하 여 배열에 있는 개체 수를 확인할 수 있습니다. 예를 들어:

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a>사용자 지정 형식 파일

사용자 지정 형식 파일을 만들려면 기존 형식 파일을 복사 하 여 시작 합니다. 새 파일에는 아무 이름이 나 사용할 수 있지만 types.ps1xml 파일 이름 확장명을 포함 해야 합니다. 파일을 복사할 때 Windows PowerShell에 액세스할 수 있는 모든 디렉터리에 새 파일을 저장할 수 있지만 Windows PowerShell 설치 디렉터리 ( `$pshome` ) 또는 설치 디렉터리의 하위 디렉터리에 파일을 저장 하는 것이 유용 합니다.

자체 확장 형식을 파일에 추가 하려면 확장 하려는 각 개체의 types 요소를 추가 합니다. 다음 항목에서는 예제를 제공 합니다.

- 속성 및 속성 집합을 추가 하는 방법에 대 한 자세한 내용은 [확장 속성](./extending-properties-for-objects.md) 을 참조 하세요.

- 메서드를 추가 하는 방법에 대 한 자세한 내용은 [확장 메서드](./defining-default-methods-for-objects.md)를 참조 하세요.

- 멤버 집합을 추가 하는 방법에 대 한 자세한 내용은 [확장 멤버 집합](./defining-default-member-sets-for-objects.md)을 참조 하세요.

사용자 고유의 확장 형식을 정의한 후 다음 방법 중 하나를 사용 하 여 확장 개체를 사용할 수 있도록 합니다.

- 확장 형식 파일을 현재 세션에서 사용할 수 있도록 설정 하려면 [update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet을 사용 하 여 새 파일을 추가 합니다. 형식이 다른 형식 파일 (Types.ps1xml 파일 포함)에 정의 된 형식 보다 우선적으로 적용 되도록 하려면 `PrependData` [update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet의 매개 변수를 사용 합니다.
- 모든 이후 세션에서 확장 형식 파일을 사용할 수 있도록 하려면 형식 파일을 모듈에 추가 하 고 현재 세션을 내보내거나 [update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) 명령을 Windows PowerShell 프로필에 추가 합니다.

## <a name="signing-types-files"></a>형식 파일 서명

XML에 스크립트 블록이 포함 될 수 있으므로 변조를 방지 하기 위해 형식 파일을 디지털 서명 해야 합니다. 디지털 서명을 추가 하는 방법에 대 한 자세한 내용은 [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[개체의 기본 속성 정의](./extending-properties-for-objects.md)

[개체에 대한 기본 메서드 정의](./defining-default-methods-for-objects.md)

[개체에 대한 기본 멤버 집합 정의](./defining-default-member-sets-for-objects.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
