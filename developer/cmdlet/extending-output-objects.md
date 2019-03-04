---
title: 출력 개체를 확장 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861929"
---
# <a name="extending-output-objects"></a>출력 개체 확장

유형 파일 (.ps1xml)를 사용 하 여 cmdlet, 함수 및 스크립트에서 반환 되는.NET Framework 개체를 확장할 수 있습니다. 형식 파일은 기존 개체에 메서드와 속성을 추가할 수 있도록 하는 XML 기반 파일입니다. 예를 들어, Windows PowerShell에는 여러 기존.NET Framework 개체에 요소를 추가 하는 Types.ps1xml 파일을 제공 합니다. Types.ps1xml 파일은 Windows PowerShell 설치 디렉터리에 있습니다 (`$pshome`). 이러한 개체를 확장 하는 추가 하거나 다른 개체를 확장 하 고유한 형식 파일을 만들 수 있습니다. 형식 파일을 사용 하 여 개체를 확장 하는 경우 개체의 모든 인스턴스에 새 요소를 사용 하 여 확장 됩니다.

## <a name="extending-the-systemarray-object"></a>System.Array 개체를 확장합니다.

다음 예제에서는 Windows PowerShell을 확장 하는 방법을 보여 줍니다.는 [System.Array](/dotnet/api/System.Array) Types.ps1xml 파일에는 개체입니다. 기본적으로 [System.Array](/dotnet/api/System.Array) 개체는 `Length` 배열의 개체의 수를 나열 하는 속성입니다. 그러나 이름 "길이" 속성을 명확 하 게 설명 하지는 않습니다, 때문에 Windows PowerShell 변수를 추가 합니다 `Count` 와 같은 값을 표시 하는 별칭 속성을 `Length` 속성입니다. 다음 XML을 추가 합니다 `Count` 속성을 합니다 [System.Array](/dotnet/api/System.Array) 형식입니다.

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

이 새 별칭 속성을 보려면 사용 하 여는 [Get-member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) 다음 예제에서와 같이 모든 배열에 명령 합니다.

```powershell
Get-Member -InputObject (1,2,3,4)
```

이 명령은 다음 결과 반환합니다.
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
사용할 수 있습니다 합니다 `Count` 속성 또는 `Length` 속성 배열에서 개체의 수를 결정 합니다. 예:

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

## <a name="custom-types-files"></a>사용자 지정 파일 형식

사용자 지정 형식 파일을 만들려면 기존 형식 파일을 복사 하 여 시작 합니다. 새 파일은 어떤 이름도 가질 수 있지만. ps1xml 파일 이름 확장명을 있어야 합니다. 파일을 복사 하면 Windows PowerShell에 액세스할 수 있는 모든 디렉터리에 새 파일을 배치할 수 있습니다 하지만 Windows PowerShell 설치 디렉터리에 파일을 배치 하는 데 유용 (`$pshome`) 또는 설치 디렉터리의 하위 디렉터리에 있습니다.

파일에 사용자 고유의 확장된 유형을 추가 하려면 확장 하려는 각 개체에 대 한 형식 요소를 추가 합니다. 다음 항목에서는 예제를 제공 합니다.

- 속성 및 속성 집합을 추가 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 속성](./extending-properties-for-objects.md)

- 메서드를 추가 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 메서드](./defining-default-methods-for-objects.md)합니다.

- 멤버를 추가 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 된 멤버 집합](./defining-default-member-sets-for-objects.md)합니다.

사용자 고유의 확장된 형식의 정의한 후에 확장 된 개체를 사용할 수 있도록 하려면 다음 방법 중 하나를 사용 합니다.

- 확장 된 형식 파일을 현재 세션에 사용할 수 있도록 하려면 사용 합니다 [Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) 새 파일을 추가 하는 cmdlet입니다. 다른 형식의 파일 (Types.ps1xml 파일 포함)에 정의 된 형식 보다 우선적으로 적용 하기 위한 형식을 원하는 경우, 사용 된 `PrependData` 의 매개 변수를 [Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.
- 확장된 유형 파일을 이후의 모든 세션에 사용할 수 있도록 하려면 유형 파일 모듈을 추가, 현재 세션을 내보내거나 추가 합니다 [Update-typedata](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) 명령을 Windows PowerShell 프로필에 있습니다.

## <a name="signing-types-files"></a>형식 파일에 서명

형식 파일 XML 스크립트 블록을 포함할 수 있으므로 변조를 방지 하기 위해 디지털 서명 되어야 합니다. 디지털 서명을 추가 하는 방법에 대 한 자세한 내용은 참조 하세요. [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>참고 항목

[개체에 대 한 기본 속성을 정의합니다.](./extending-properties-for-objects.md)

[개체에 대 한 기본 메서드를 정의합니다.](./defining-default-methods-for-objects.md)

[개체에 대 한 기본 멤버 집합을 정의합니다.](./defining-default-member-sets-for-objects.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
