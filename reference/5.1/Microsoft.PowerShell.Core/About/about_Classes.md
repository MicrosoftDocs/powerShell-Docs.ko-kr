---
description: 클래스를 사용 하 여 사용자 고유의 사용자 지정 형식을 만드는 방법을 설명 합니다.
Locale: en-US
ms.date: 01/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes
ms.openlocfilehash: 6459ee4e80515360dcd1c16ac027ead8fa17bacc
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98620084"
---
# <a name="about-classes"></a>클래스 정보

## <a name="short-description"></a>간단한 설명
클래스를 사용 하 여 사용자 고유의 사용자 지정 형식을 만드는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell 5.0은 클래스 및 기타 사용자 정의 형식을 정의 하는 공식 구문을 추가 합니다. 개발자와 IT 전문가는 클래스를 추가 하 여 더 광범위 한 사용 사례에 PowerShell을 적용할 수 있습니다. PowerShell 아티팩트의 개발을 간소화 하 고 관리 표면의 범위를 가속화 합니다.

클래스 선언은 런타임에 개체의 인스턴스를 만드는 데 사용 되는 청사진입니다. 클래스를 정의 하는 경우 클래스 이름은 형식의 이름입니다. 예를 들어 **device** 라는 클래스를 선언 하 고 변수를 `$dev` **장치의** 새 인스턴스로 초기화 하는 경우 `$dev` 는 **장치** 형식의 개체 또는 인스턴스입니다. 각 **장치** 인스턴스의 속성에는 서로 다른 값이 있을 수 있습니다.

## <a name="supported-scenarios"></a>지원되는 시나리오

- 클래스, 속성, 메서드, 상속 등과 같은 친숙 한 개체 지향 프로그래밍 의미 체계를 사용 하 여 PowerShell에서 사용자 지정 형식을 정의 합니다.
- PowerShell 언어를 사용 하는 디버그 형식입니다.
- 형식 메커니즘을 사용 하 여 예외를 생성 하 고 처리 합니다.
- PowerShell 언어를 사용 하 여 DSC 리소스 및 관련 형식을 정의 합니다.

## <a name="syntax"></a>구문

클래스는 다음 구문을 사용 하 여 선언 됩니다.

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

클래스는 다음 구문 중 하나를 사용 하 여 인스턴스화됩니다.

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> 구문을 사용 하는 경우 `[<class-name>]::new()` 클래스 이름 주위의 대괄호가 필수입니다. 대괄호는 PowerShell에 대 한 형식 정의를 신호로 알립니다.

### <a name="example-syntax-and-usage"></a>구문 및 사용법 예

이 예제에서는 사용 가능한 클래스를 만드는 데 필요한 최소 구문을 보여 줍니다.

```powershell
class Device {
    [string]$Brand
}

$dev = [Device]::new()
$dev.Brand = "Microsoft"
$dev
```

```Output
Brand
-----
Microsoft
```

## <a name="class-properties"></a>클래스 속성

속성은 클래스 범위에서 선언 된 변수입니다. 속성은 기본 제공 형식이 나 다른 클래스의 인스턴스일 수 있습니다. 클래스에 포함 된 속성 수에는 제한이 없습니다.

### <a name="example-class-with-simple-properties"></a>간단한 속성을 사용 하는 예제 클래스

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

$device = [Device]::new()
$device.Brand = "Microsoft"
$device.Model = "Surface Pro 4"
$device.VendorSku = "5072641000"

$device
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-complex-types-in-class-properties"></a>클래스 속성의 예제 복합 형식

이 예제에서는 **장치** 클래스를 사용 하 여 빈 **랙** 클래스를 정의 합니다. 이 예제 다음에 나오는 예제에서는 랙에 장치를 추가 하는 방법과 미리 로드 된 랙에 시작 하는 방법을 보여 줍니다.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

class Rack {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new(8)

}

$rack = [Rack]::new()

$rack
```

```Output

Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, $null, $null...}


```

## <a name="class-methods"></a>클래스 메서드

메서드는 클래스가 수행할 수 있는 작업을 정의합니다. 메서드는 입력 데이터를 제공 하는 매개 변수를 사용할 수 있습니다. 메서드는 출력을 반환할 수 있습니다. 메서드에 의해 반환 되는 데이터는 정의 된 모든 데이터 형식일 수 있습니다.

클래스에 대 한 메서드를 정의 하는 경우 자동 변수를 사용 하 여 현재 클래스 개체를 참조 합니다 `$this` . 이렇게 하면 현재 클래스에 정의 된 속성 및 기타 메서드에 액세스할 수 있습니다.

### <a name="example-simple-class-with-properties-and-methods"></a>속성 및 메서드를 사용 하는 예제 간단한 클래스

**랙** 클래스를 확장 하 여 장치를 추가 및 제거 합니다.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    [string]ToString(){
        return ("{0}|{1}|{2}" -f $this.Brand, $this.Model, $this.VendorSku)
    }
}

class Rack {
    [int]$Slots = 8
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void]RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }

    [int[]] GetAvailableSlots(){
        [int]$i = 0
        return @($this.Devices.foreach{ if($_ -eq $null){$i}; $i++})
    }
}

$rack = [Rack]::new()

$surface = [Device]::new()
$surface.Brand = "Microsoft"
$surface.Model = "Surface Pro 4"
$surface.VendorSku = "5072641000"

$rack.AddDevice($surface, 2)

$rack
$rack.GetAvailableSlots()
```

```Output

Slots     : 8
Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, Microsoft|Surface Pro 4|5072641000, $null...}

0
1
3
4
5
6
7

```

## <a name="output-in-class-methods"></a>클래스 메서드의 출력

메서드에는 반환 형식이 정의 되어 있어야 합니다. 메서드가 출력을 반환 하지 않는 경우 출력 형식은 이어야 합니다 `[void]` .

클래스 메서드에서 문에 언급 된 개체를 제외 하 고 파이프라인으로 전송 되는 개체는 없습니다 `return` . 코드에서 파이프라인에 대 한 실수로 출력 되지 않습니다.

> [!NOTE]
> 이는 기본적으로 PowerShell 함수가 출력을 처리 하는 방식과 다르며, 모든 것이 파이프라인으로 이동 합니다.

클래스 메서드 내부에서 오류 스트림에 작성 된 종료 되지 않는 오류는로 전달 되지 않습니다. 종료 오류를 표시 하려면를 사용 해야 합니다 `throw` .
`Write-*`Cmdlet을 사용 하면 클래스 메서드 내에서 PowerShell의 출력 스트림에 계속 쓸 수 있습니다. 그러나 메서드가 문만 사용 하 여 개체를 내보내는 경우에는이를 피해 야 합니다 `return` .

### <a name="method-output"></a>메서드 출력

이 예제에서는 문을 제외 하 고 클래스 메서드에서 파이프라인에 대 한 실수로의 출력을 보여 줍니다 `return` .

```powershell
class FunWithIntegers
{
    [int[]]$Integers = 0..10

    [int[]]GetOddIntegers(){
        return $this.Integers.Where({ ($_ % 2) })
    }

    [void] GetEvenIntegers(){
        # this following line doesn't go to the pipeline
        $this.Integers.Where({ ($_ % 2) -eq 0})
    }

    [string]SayHello(){
        # this following line doesn't go to the pipeline
        "Good Morning"

        # this line goes to the pipeline
        return "Hello World"
    }
}

$ints = [FunWithIntegers]::new()
$ints.GetOddIntegers()
$ints.GetEvenIntegers()
$ints.SayHello()
```

```Output
1
3
5
7
9
Hello World

```

## <a name="constructor"></a>생성자

생성자를 사용 하면 클래스의 인스턴스를 만드는 순간에 기본값을 설정 하 고 개체 논리의 유효성을 검사할 수 있습니다. 생성자의 이름은 클래스와 동일 합니다. 생성자에는 새 개체의 데이터 멤버를 초기화 하는 인수가 있을 수 있습니다.

클래스에는 0 개 이상의 생성자가 정의 될 수 있습니다. 생성자가 정의 되지 않은 경우 클래스에 매개 변수가 없는 기본 생성자가 제공 됩니다. 이 생성자는 모든 멤버를 기본값으로 초기화 합니다. 개체 형식 및 문자열에는 null 값이 지정 됩니다. 생성자를 정의 하는 경우 매개 변수가 없는 기본 생성자가 생성 되지 않습니다. 매개 변수가 필요한 경우 매개 변수가 없는 생성자를 만듭니다.

### <a name="constructor-basic-syntax"></a>생성자 기본 구문

이 예제에서 장치 클래스는 속성과 생성자를 사용 하 여 정의 됩니다.
이 클래스를 사용 하려면 사용자가 생성자에 나열 된 매개 변수에 대 한 값을 제공 해야 합니다.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$surface
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-with-multiple-constructors"></a>여러 생성자를 사용 하는 예제

이 예제에서 **장치** 클래스는 속성, 기본 생성자 및 인스턴스를 초기화 하는 생성자를 사용 하 여 정의 됩니다.

기본 생성자는 **브랜드** 를 **Undefined** 로 설정 하 고 **모델** 및 **공급 업체-sku** 에서 null 값을 유지 합니다.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(){
        $this.Brand = 'Undefined'
    }

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$somedevice = [Device]::new()
[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$somedevice
$surface
```

```Output
Brand       Model           VendorSku
-----       -----           ---------
Undefined
Microsoft   Surface Pro 4   5072641000
```

## <a name="hidden-attribute"></a>Hidden 특성

`hidden`특성은 속성 또는 메서드를 숨깁니다. 속성 또는 메서드는 계속 사용자가 액세스할 수 있으며 개체를 사용할 수 있는 모든 범위에서 사용할 수 있습니다. 숨겨진 멤버는 cmdlet에서 숨겨지고 `Get-Member` 클래스 완성 또는 IntelliSense를 사용 하 여 클래스 정의 외부에서 표시할 수 없습니다.

자세한 내용은 [About_hidden](About_hidden.md)를 참조 하세요.

### <a name="example-using-hidden-attributes"></a>숨겨진 특성 사용 예

**랙** 개체가 생성 될 때 장치에 대 한 슬롯 수는 언제 든 지 변경 될 수 없는 고정 된 값입니다. 이 값은 생성 시에 알려져 있습니다.

숨겨진 특성을 사용 하면 개발자는 슬롯의 수를 숨기고 의도 하지 않은 랙 크기 변경을 방지할 수 있습니다.

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    [int] hidden $Slots = 8
    [string]$Brand
    [string]$Model
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)
    }
}

[Rack]$r1 = [Rack]::new("Microsoft", "Surface Pro 4", 16)

$r1
$r1.Devices.Length
$r1.Slots
```

```Output
Brand     Model         Devices
-----     -----         -------
Microsoft Surface Pro 4 {$null, $null, $null, $null...}
16
16
```

알림 **슬롯** 속성은 출력에 표시 되지 않습니다 `$r1` . 그러나이 크기는 생성자에 의해 변경 되었습니다.

## <a name="static-attribute"></a>정적 특성

`static`특성은 클래스에 존재 하 고 인스턴스를 필요로 하지 않는 속성 또는 메서드를 정의 합니다.

정적 속성은 클래스 인스턴스화와 독립적인 항상 사용할 수 있습니다. 정적 속성은 클래스의 모든 인스턴스에서 공유 됩니다. 정적 메서드는 항상 사용할 수 있습니다. 전체 세션 범위에 대해 활성 상태인 모든 정적 속성입니다.

### <a name="example-using-static-attributes-and-methods"></a>정적 특성 및 메서드를 사용 하는 예제

여기에서 인스턴스화된 랙이 데이터 센터에 있는 것으로 가정 합니다. 따라서 코드에서 랙을 추적 하는 것이 좋습니다.

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    hidden [int] $Slots = 8
    static [Rack[]]$InstalledRacks = @()
    [string]$Brand
    [string]$Model
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [string]$id, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.AssetId = $id
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)

        ## add rack to installed racks
        [Rack]::InstalledRacks += $this
    }

    static [void]PowerOffRacks(){
        foreach ($rack in [Rack]::InstalledRacks) {
            Write-Warning ("Turning off rack: " + ($rack.AssetId))
        }
    }
}
```

### <a name="testing-static-property-and-method-exist"></a>정적 속성 및 메서드 테스트가 있습니다.

```
PS> [Rack]::InstalledRacks.Length
0

PS> [Rack]::PowerOffRacks()

PS> (1..10) | ForEach-Object {
>>   [Rack]::new("Adatum Corporation", "Standard-16",
>>     $_.ToString("Std0000"), 16)
>> } > $null

PS> [Rack]::InstalledRacks.Length
10

PS> [Rack]::InstalledRacks[3]
Brand              Model       AssetId Devices
-----              -----       ------- -------
Adatum Corporation Standard-16 Std0004 {$null, $null, $null, $null...}

PS> [Rack]::PowerOffRacks()
WARNING: Turning off rack: Std0001
WARNING: Turning off rack: Std0002
WARNING: Turning off rack: Std0003
WARNING: Turning off rack: Std0004
WARNING: Turning off rack: Std0005
WARNING: Turning off rack: Std0006
WARNING: Turning off rack: Std0007
WARNING: Turning off rack: Std0008
WARNING: Turning off rack: Std0009
WARNING: Turning off rack: Std0010
```

이 예제를 실행할 때마다 랙 수가 늘어납니다.

## <a name="property-validation-attributes"></a>속성 유효성 검사 특성

유효성 검사 특성을 사용 하 여 속성에 지정 된 값이 정의 된 요구 사항을 충족 하는지 테스트할 수 있습니다. 유효성 검사는 값이 할당 된 순간에 트리거됩니다. [About_functions_advanced_parameters](about_functions_advanced_parameters.md)를 참조 하세요.

### <a name="example-using-validation-attributes"></a>유효성 검사 특성 사용 예

```powershell
class Device {
    [ValidateNotNullOrEmpty()][string]$Brand
    [ValidateNotNullOrEmpty()][string]$Model
}

[Device]$dev = [Device]::new()

Write-Output "Testing dev"
$dev

$dev.Brand = ""
```

```Output
Testing dev

Brand Model
----- -----

Exception setting "Brand": "The argument is null or empty. Provide an
argument that is not null or empty, and then try the command again."
At C:\tmp\Untitled-5.ps1:11 char:1
+ $dev.Brand = ""
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], SetValueInvocationException
    + FullyQualifiedErrorId : ExceptionWhenSetting
```

## <a name="inheritance-in-powershell-classes"></a>PowerShell 클래스의 상속

기존 클래스에서 파생 되는 새 클래스를 만들어 클래스를 확장할 수 있습니다. 파생 클래스는 기본 클래스의 속성을 상속 합니다. 필요에 따라 메서드 및 속성을 추가 하거나 재정의할 수 있습니다.

PowerShell은 다중 상속을 지원 하지 않습니다. 클래스는 둘 이상의 클래스에서 상속할 수 없습니다. 그러나 이러한 용도로 인터페이스를 사용할 수 있습니다.

상속 구현은 연산자에 의해 정의 됩니다. `:` 이는이 클래스를 확장 하거나 이러한 인터페이스를 구현 하는 것을 의미 합니다. 파생 클래스는 항상 클래스 선언에서 맨 왼쪽에 있어야 합니다.

### <a name="example-using-simple-inheritance-syntax"></a>간단한 상속 구문을 사용한 예

이 예제에서는 간단한 PowerShell 클래스 상속 구문을 보여 줍니다.

```powershell
Class Derived : Base {...}
```

이 예제에서는 기본 클래스 다음에 오는 인터페이스 선언으로 상속을 보여 줍니다.

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a>PowerShell 클래스의 간단한 상속 예제

이 예제에서는 이전 예제에서 사용 되는 **랙** 및 **장치** 클래스를 정의 하는 것이 더 효율적입니다. 속성 반복 방지, 공용 속성 맞춤 및 공통 비즈니스 논리 다시 사용.

데이터 센터의 대부분의 개체는 회사 자산으로, 자산으로 추적을 시작 하는 데 적합 합니다. 장치 유형은 열거형에 의해 정의 됩니다 `DeviceType` . 열거에 대 한 자세한 내용은 [about_Enum](about_Enum.md) 를 참조 하세요.

이 예제에서는 및를 정의 하 고 `Rack` , `ComputeServer` 두 확장을 모두 클래스에 대해 정의 `Device` 합니다.

```powershell
enum DeviceType {
    Undefined = 0
    Compute = 1
    Storage = 2
    Networking = 4
    Communications = 8
    Power = 16
    Rack = 32
}

class Asset {
    [string]$Brand
    [string]$Model
}

class Device : Asset {
    hidden [DeviceType]$devtype = [DeviceType]::Undefined
    [string]$Status

    [DeviceType] GetDeviceType(){
        return $this.devtype
    }
}

class ComputeServer : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Compute
    [string]$ProcessorIdentifier
    [string]$Hostname
}

class Rack : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Rack
    hidden [int]$Slots = 8

    [string]$Datacenter
    [string]$Location
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack (){
        ## Just create the default rack with 8 slots
    }

    Rack ([int]$s){
        ## Add argument validation logic here
        $this.Devices = [Device[]]::new($s)
    }

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void] RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }
}

$FirstRack = [Rack]::new(16)
$FirstRack.Status = "Operational"
$FirstRack.Datacenter = "PNW"
$FirstRack.Location = "F03R02.J10"

(0..15).ForEach({
    $ComputeServer = [ComputeServer]::new()
    $ComputeServer.Brand = "Fabrikam, Inc."       ## Inherited from Asset
    $ComputeServer.Model = "Fbk5040"              ## Inherited from Asset
    $ComputeServer.Status = "Installed"           ## Inherited from Device
    $ComputeServer.ProcessorIdentifier = "x64"    ## ComputeServer
    $ComputeServer.Hostname = ("r1s" + $_.ToString("000")) ## ComputeServer
    $FirstRack.AddDevice($ComputeServer, $_)
  })

$FirstRack
$FirstRack.Devices
```

```Output
Datacenter : PNW
Location   : F03R02.J10
Devices    : {r1s000, r1s001, r1s002, r1s003...}
Status     : Operational
Brand      :
Model      :

ProcessorIdentifier : x64
Hostname            : r1s000
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

ProcessorIdentifier : x64
Hostname            : r1s001
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

<... content truncated here for brevity ...>

ProcessorIdentifier : x64
Hostname            : r1s015
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040
```

### <a name="calling-base-class-constructors"></a>기본 클래스 생성자 호출

하위 클래스에서 기본 클래스 생성자를 호출 하려면 키워드를 추가 `base` 합니다.

```powershell
class Person {
    [int]$Age

    Person([int]$a)
    {
        $this.Age = $a
    }
}

class Child : Person
{
    [string]$School

    Child([int]$a, [string]$s ) : base($a) {
        $this.School = $s
    }
}

[Child]$littleone = [Child]::new(10, "Silver Fir Elementary School")

$littleone.Age
```

```Output

10
```

### <a name="invoke-base-class-methods"></a>기본 클래스 메서드 호출

서브 클래스의 기존 메서드를 재정의 하려면 동일한 이름과 서명을 사용 하 여 메서드를 선언 합니다.

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
}

[ChildClass1]::new().days()
```

```Output

2
```

재정의 된 구현에서 기본 클래스 메서드를 호출 하려면 호출할 때 기본 클래스 ([baseclass] $this)로 캐스팅 합니다.

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
    [int]basedays() {return ([BaseClass]$this).days()}
}

[ChildClass1]::new().days()
[ChildClass1]::new().basedays()
```

```Output

2
1
```

### <a name="inheriting-from-interfaces"></a>인터페이스에서 상속

PowerShell 클래스는 기본 클래스를 확장 하는 데 사용 되는 것과 동일한 상속 구문을 사용 하 여 인터페이스를 구현할 수 있습니다. 인터페이스는 여러 상속을 허용 하기 때문에 인터페이스를 구현 하는 PowerShell 클래스는 콜론 () 뒤의 형식 이름을 `:` 쉼표 ()로 구분 하 여 여러 형식에서 상속할 수 있습니다 `,` . 인터페이스를 구현 하는 PowerShell 클래스는 해당 인터페이스의 모든 멤버를 구현 해야 합니다. 구현을 인터페이스 멤버를 생략 하면 스크립트에서 구문 분석 시간 오류가 발생 합니다.

> [!NOTE]
> PowerShell은 현재 PowerShell 스크립트에서 새 인터페이스 선언을 지원 하지 않습니다.

```powershell
class MyComparable : System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="importing-classes-from-a-powershell-module"></a>PowerShell 모듈에서 클래스 가져오기

`Import-Module` 및 `#requires` 문은 모듈에서 정의한 대로 모듈 함수, 별칭 및 변수만 가져옵니다. 클래스는 가져올 수 없습니다. `using module`문은 모듈에 정의 된 클래스를 가져옵니다. 모듈이 현재 세션에서 로드 되지 않으면 `using` 문이 실패 합니다. 문에 대 한 자세한 내용은 `using` [about_Using](about_Using.md)를 참조 하세요.

`using module`문은 `ModuleToProcess` 스크립트 모듈 또는 이진 모듈의 루트 모듈 ()에서 클래스를 가져옵니다. 모듈에 대 한 점 소스인 스크립트에 정의 된 클래스 또는 중첩 된 모듈에 정의 된 클래스를 일관 되 게 가져오지 않습니다. 모듈 외부의 사용자가 사용할 수 있도록 하려는 클래스는 루트 모듈에서 정의 해야 합니다.

## <a name="loading-newly-changed-code-during-development"></a>개발 하는 동안 새로 변경 된 코드 로드

스크립트 모듈을 개발 하는 동안 코드를 변경한 다음 `Import-Module` **Force** 매개 변수를 사용 하 여 새 버전의 모듈을 로드 하는 것이 일반적입니다. 이는 루트 모듈의 함수를 변경 하는 경우에만 작동 합니다. `Import-Module` 중첩 된 모듈을 다시 로드 하지 않습니다. 또한 업데이트 된 클래스를 로드 하는 방법은 없습니다.

최신 버전을 실행 하 고 있는지 확인 하려면 cmdlet을 사용 하 여 모듈을 언로드해야 합니다 `Remove-Module` . `Remove-Module` 모듈에 정의 된 루트 모듈, 모든 중첩 된 모듈 및 클래스를 제거 합니다. 그런 다음 및 문을 사용 하 여 모듈과 클래스를 다시 로드할 수 있습니다 `Import-Module` `using module` .

또 다른 일반적인 개발 방법은 코드를 서로 다른 파일로 분리 하는 것입니다. 다른 모듈에 정의 된 클래스를 사용 하는 한 파일에 함수를 사용 하는 경우 문을 사용 하 여 `using module` 함수에 필요한 클래스 정의가 있는지 확인 해야 합니다.

## <a name="the-psreference-type-is-not-supported-with-class-members"></a>PSReference 형식은 클래스 멤버에서 지원 되지 않습니다.

`[ref]`클래스 멤버와 함께 형식 캐스팅을 자동으로 사용 하면 오류가 발생 합니다. 매개 변수를 사용 하는 Api는 `[ref]` 클래스 멤버와 함께 사용할 수 없습니다. **Psreference** 클래스는 COM 개체를 지원 하도록 디자인 되었습니다. COM 개체에는의 값을 참조로 전달 해야 하는 경우가 있습니다.

형식에 대 한 자세한 내용은 `[ref]` [Psreference 클래스](/dotnet/api/system.management.automation.psreference)를 참조 하세요.

## <a name="see-also"></a>참조

- [About_hidden](About_hidden.md)
- [about_Enum](about_Enum.md)
- [about_Language_Keywords](about_language_keywords.md)
- [about_Methods](about_methods.md)
- [about_Using](about_using.md)
