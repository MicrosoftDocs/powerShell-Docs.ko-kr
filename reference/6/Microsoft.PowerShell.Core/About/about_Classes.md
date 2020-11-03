---
description: 클래스를 사용 하 여 사용자 고유의 사용자 지정 형식을 만드는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes
ms.openlocfilehash: e4e3379c18b8e63e5c494b71485d6dab5c7689f2
ms.sourcegitcommit: 16d62a98449e3ddaf8d7c65bc1848ede1fd8a3e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "93219970"
---
# <a name="about-classes"></a><span data-ttu-id="845b7-104">클래스 정보</span><span class="sxs-lookup"><span data-stu-id="845b7-104">About Classes</span></span>

## <a name="short-description"></a><span data-ttu-id="845b7-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="845b7-105">Short description</span></span>
<span data-ttu-id="845b7-106">클래스를 사용 하 여 사용자 고유의 사용자 지정 형식을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-106">Describes how you can use classes to create your own custom types.</span></span>

## <a name="long-description"></a><span data-ttu-id="845b7-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-107">Long description</span></span>

<span data-ttu-id="845b7-108">PowerShell 5.0은 클래스 및 기타 사용자 정의 형식을 정의 하는 공식 구문을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-108">PowerShell 5.0 adds a formal syntax to define classes and other user-defined types.</span></span> <span data-ttu-id="845b7-109">개발자와 IT 전문가는 클래스를 추가 하 여 더 광범위 한 사용 사례에 PowerShell을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-109">The addition of classes enables developers and IT professionals to embrace PowerShell for a wider range of use cases.</span></span> <span data-ttu-id="845b7-110">PowerShell 아티팩트의 개발을 간소화 하 고 관리 표면의 범위를 가속화 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-110">It simplifies development of PowerShell artifacts and accelerates coverage of management surfaces.</span></span>

<span data-ttu-id="845b7-111">클래스 선언은 런타임에 개체의 인스턴스를 만드는 데 사용 되는 청사진입니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-111">A class declaration is a blueprint used to create instances of objects at run time.</span></span> <span data-ttu-id="845b7-112">클래스를 정의 하는 경우 클래스 이름은 형식의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-112">When you define a class, the class name is the name of the type.</span></span> <span data-ttu-id="845b7-113">예를 들어 **device** 라는 클래스를 선언 하 고 변수를 `$dev` **장치의** 새 인스턴스로 초기화 하는 경우 `$dev` 는 **장치** 형식의 개체 또는 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-113">For example, if you declare a class named **Device** and initialize a variable `$dev` to a new instance of **Device** , `$dev` is an object or instance of type **Device**.</span></span> <span data-ttu-id="845b7-114">각 **장치** 인스턴스의 속성에는 서로 다른 값이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-114">Each instance of **Device** can have different values in its properties.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="845b7-115">지원되는 시나리오</span><span class="sxs-lookup"><span data-stu-id="845b7-115">Supported scenarios</span></span>

- <span data-ttu-id="845b7-116">클래스, 속성, 메서드, 상속 등과 같은 친숙 한 개체 지향 프로그래밍 의미 체계를 사용 하 여 PowerShell에서 사용자 지정 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-116">Define custom types in PowerShell using familiar object-oriented programming semantics like classes, properties, methods, inheritance, etc.</span></span>
- <span data-ttu-id="845b7-117">PowerShell 언어를 사용 하는 디버그 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-117">Debug types using the PowerShell language.</span></span>
- <span data-ttu-id="845b7-118">형식 메커니즘을 사용 하 여 예외를 생성 하 고 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-118">Generate and handle exceptions using formal mechanisms.</span></span>
- <span data-ttu-id="845b7-119">PowerShell 언어를 사용 하 여 DSC 리소스 및 관련 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-119">Define DSC resources and their associated types by using the PowerShell language.</span></span>

## <a name="syntax"></a><span data-ttu-id="845b7-120">구문</span><span class="sxs-lookup"><span data-stu-id="845b7-120">Syntax</span></span>

<span data-ttu-id="845b7-121">클래스는 다음 구문을 사용 하 여 선언 됩니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-121">Classes are declared using the following syntax:</span></span>

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

<span data-ttu-id="845b7-122">클래스는 다음 구문 중 하나를 사용 하 여 인스턴스화됩니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-122">Classes are instantiated using either of the following syntaxes:</span></span>

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> <span data-ttu-id="845b7-123">구문을 사용 하는 경우 `[<class-name>]::new()` 클래스 이름 주위의 대괄호가 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-123">When using the `[<class-name>]::new()` syntax, brackets around the class name are mandatory.</span></span> <span data-ttu-id="845b7-124">대괄호는 PowerShell에 대 한 형식 정의를 신호로 알립니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-124">The brackets signal a type definition for PowerShell.</span></span>

### <a name="example-syntax-and-usage"></a><span data-ttu-id="845b7-125">구문 및 사용법 예</span><span class="sxs-lookup"><span data-stu-id="845b7-125">Example syntax and usage</span></span>

<span data-ttu-id="845b7-126">이 예제에서는 사용 가능한 클래스를 만드는 데 필요한 최소 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-126">This example shows the minimum syntax needed to create a usable class.</span></span>

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

## <a name="class-properties"></a><span data-ttu-id="845b7-127">클래스 속성</span><span class="sxs-lookup"><span data-stu-id="845b7-127">Class properties</span></span>

<span data-ttu-id="845b7-128">속성은 클래스 범위에서 선언 된 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-128">Properties are variables declared at class scope.</span></span> <span data-ttu-id="845b7-129">속성은 기본 제공 형식이 나 다른 클래스의 인스턴스일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-129">A property may be of any built-in type or an instance of another class.</span></span> <span data-ttu-id="845b7-130">클래스에 포함 된 속성 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-130">Classes have no restriction in the number of properties they have.</span></span>

### <a name="example-class-with-simple-properties"></a><span data-ttu-id="845b7-131">간단한 속성을 사용 하는 예제 클래스</span><span class="sxs-lookup"><span data-stu-id="845b7-131">Example class with simple properties</span></span>

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

### <a name="example-complex-types-in-class-properties"></a><span data-ttu-id="845b7-132">클래스 속성의 예제 복합 형식</span><span class="sxs-lookup"><span data-stu-id="845b7-132">Example complex types in class properties</span></span>

<span data-ttu-id="845b7-133">이 예제에서는 **장치** 클래스를 사용 하 여 빈 **랙** 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-133">This example defines an empty **Rack** class using the **Device** class.</span></span> <span data-ttu-id="845b7-134">이 예제 다음에 나오는 예제에서는 랙에 장치를 추가 하는 방법과 미리 로드 된 랙에 시작 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-134">The examples, following this one, show how to add devices to the rack and how to start with a pre-loaded rack.</span></span>

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

## <a name="class-methods"></a><span data-ttu-id="845b7-135">클래스 메서드</span><span class="sxs-lookup"><span data-stu-id="845b7-135">Class methods</span></span>

<span data-ttu-id="845b7-136">메서드는 클래스가 수행할 수 있는 작업을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-136">Methods define the actions that a class can perform.</span></span> <span data-ttu-id="845b7-137">메서드는 입력 데이터를 제공 하는 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-137">Methods may take parameters that provide input data.</span></span> <span data-ttu-id="845b7-138">메서드는 출력을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-138">Methods can return output.</span></span> <span data-ttu-id="845b7-139">메서드에 의해 반환 되는 데이터는 정의 된 모든 데이터 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-139">Data returned by a method can be any defined data type.</span></span>

<span data-ttu-id="845b7-140">클래스에 대 한 메서드를 정의 하는 경우 자동 변수를 사용 하 여 현재 클래스 개체를 참조 합니다 `$this` .</span><span class="sxs-lookup"><span data-stu-id="845b7-140">When defining a method for a class, you reference the current class object by using the `$this` automatic variable.</span></span> <span data-ttu-id="845b7-141">이렇게 하면 현재 클래스에 정의 된 속성 및 기타 메서드에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-141">This allows you to access properties and other methods defined in the current class.</span></span>

### <a name="example-simple-class-with-properties-and-methods"></a><span data-ttu-id="845b7-142">속성 및 메서드를 사용 하는 예제 간단한 클래스</span><span class="sxs-lookup"><span data-stu-id="845b7-142">Example simple class with properties and methods</span></span>

<span data-ttu-id="845b7-143">**랙** 클래스를 확장 하 여 장치를 추가 및 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-143">Extending the **Rack** class to add and remove devices to or from it.</span></span>

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

## <a name="output-in-class-methods"></a><span data-ttu-id="845b7-144">클래스 메서드의 출력</span><span class="sxs-lookup"><span data-stu-id="845b7-144">Output in class methods</span></span>

<span data-ttu-id="845b7-145">메서드에는 반환 형식이 정의 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-145">Methods should have a return type defined.</span></span> <span data-ttu-id="845b7-146">메서드가 출력을 반환 하지 않는 경우 출력 형식은 이어야 합니다 `[void]` .</span><span class="sxs-lookup"><span data-stu-id="845b7-146">If a method doesn't return output, then the output type should be `[void]`.</span></span>

<span data-ttu-id="845b7-147">클래스 메서드에서 문에 언급 된 개체를 제외 하 고 파이프라인으로 전송 되는 개체는 없습니다 `return` .</span><span class="sxs-lookup"><span data-stu-id="845b7-147">In class methods, no objects get sent to the pipeline except those mentioned in the `return` statement.</span></span> <span data-ttu-id="845b7-148">코드에서 파이프라인에 대 한 실수로 출력 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-148">There's no accidental output to the pipeline from the code.</span></span>

> [!NOTE]
> <span data-ttu-id="845b7-149">이는 기본적으로 PowerShell 함수가 출력을 처리 하는 방식과 다르며, 모든 것이 파이프라인으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-149">This is fundamentally different from how PowerShell functions handle output, where everything goes to the pipeline.</span></span>

<span data-ttu-id="845b7-150">클래스 메서드 내부에서 오류 스트림에 작성 된 종료 되지 않는 오류는로 전달 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-150">Non-terminating errors written to the error stream from inside a class method are not passed through.</span></span> <span data-ttu-id="845b7-151">종료 오류를 표시 하려면를 사용 해야 합니다 `throw` .</span><span class="sxs-lookup"><span data-stu-id="845b7-151">You must use `throw` to surface a terminating error.</span></span>
<span data-ttu-id="845b7-152">`Write-*`Cmdlet을 사용 하면 클래스 메서드 내에서 PowerShell의 출력 스트림에 계속 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-152">Using the `Write-*` cmdlets, you can still write to PowerShell's output streams from within a class method.</span></span> <span data-ttu-id="845b7-153">그러나 메서드가 문만 사용 하 여 개체를 내보내는 경우에는이를 피해 야 합니다 `return` .</span><span class="sxs-lookup"><span data-stu-id="845b7-153">However, this should be avoided so that the method emits objects using only the `return` statement.</span></span>

### <a name="method-output"></a><span data-ttu-id="845b7-154">메서드 출력</span><span class="sxs-lookup"><span data-stu-id="845b7-154">Method output</span></span>

<span data-ttu-id="845b7-155">이 예제에서는 문을 제외 하 고 클래스 메서드에서 파이프라인에 대 한 실수로의 출력을 보여 줍니다 `return` .</span><span class="sxs-lookup"><span data-stu-id="845b7-155">This example demonstrates no accidental output to the pipeline from class methods, except on the `return` statement.</span></span>

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

## <a name="constructor"></a><span data-ttu-id="845b7-156">생성자</span><span class="sxs-lookup"><span data-stu-id="845b7-156">Constructor</span></span>

<span data-ttu-id="845b7-157">생성자를 사용 하면 클래스의 인스턴스를 만드는 순간에 기본값을 설정 하 고 개체 논리의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-157">Constructors enable you to set default values and validate object logic at the moment of creating the instance of the class.</span></span> <span data-ttu-id="845b7-158">생성자의 이름은 클래스와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-158">Constructors have the same name as the class.</span></span> <span data-ttu-id="845b7-159">생성자에는 새 개체의 데이터 멤버를 초기화 하는 인수가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-159">Constructors might have arguments, to initialize the data members of the new object.</span></span>

<span data-ttu-id="845b7-160">클래스에는 0 개 이상의 생성자가 정의 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-160">The class can have zero or more constructors defined.</span></span> <span data-ttu-id="845b7-161">생성자가 정의 되지 않은 경우 클래스에 매개 변수가 없는 기본 생성자가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-161">If no constructor is defined, the class is given a default parameterless constructor.</span></span> <span data-ttu-id="845b7-162">이 생성자는 모든 멤버를 기본값으로 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-162">This constructor initializes all members to their default values.</span></span> <span data-ttu-id="845b7-163">개체 형식 및 문자열에는 null 값이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-163">Object types and strings are given null values.</span></span> <span data-ttu-id="845b7-164">생성자를 정의 하는 경우 매개 변수가 없는 기본 생성자가 생성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-164">When you define constructor, no default parameterless constructor is created.</span></span> <span data-ttu-id="845b7-165">매개 변수가 필요한 경우 매개 변수가 없는 생성자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-165">Create a parameterless constructor if one is needed.</span></span>

### <a name="constructor-basic-syntax"></a><span data-ttu-id="845b7-166">생성자 기본 구문</span><span class="sxs-lookup"><span data-stu-id="845b7-166">Constructor basic syntax</span></span>

<span data-ttu-id="845b7-167">이 예제에서 장치 클래스는 속성과 생성자를 사용 하 여 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-167">In this example, the Device class is defined with properties and a constructor.</span></span>
<span data-ttu-id="845b7-168">이 클래스를 사용 하려면 사용자가 생성자에 나열 된 매개 변수에 대 한 값을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-168">To use this class, the user is required to provide values for the parameters listed in the constructor.</span></span>

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

### <a name="example-with-multiple-constructors"></a><span data-ttu-id="845b7-169">여러 생성자를 사용 하는 예제</span><span class="sxs-lookup"><span data-stu-id="845b7-169">Example with multiple constructors</span></span>

<span data-ttu-id="845b7-170">이 예제에서 **장치** 클래스는 속성, 기본 생성자 및 인스턴스를 초기화 하는 생성자를 사용 하 여 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-170">In this example, the **Device** class is defined with properties, a default constructor, and a constructor to initialize the instance.</span></span>

<span data-ttu-id="845b7-171">기본 생성자는 **브랜드** 를 **Undefined** 로 설정 하 고 **모델** 및 **공급 업체-sku** 에서 null 값을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-171">The default constructor sets the **brand** to **Undefined** , and leaves **model** and **vendor-sku** with null values.</span></span>

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

## <a name="hidden-attribute"></a><span data-ttu-id="845b7-172">Hidden 특성</span><span class="sxs-lookup"><span data-stu-id="845b7-172">Hidden attribute</span></span>

<span data-ttu-id="845b7-173">`hidden`특성은 속성 또는 메서드를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-173">The `hidden` attribute hides a property or method.</span></span> <span data-ttu-id="845b7-174">속성 또는 메서드는 계속 사용자가 액세스할 수 있으며 개체를 사용할 수 있는 모든 범위에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-174">The property or method is still accessible to the user and is available in all scopes in which the object is available.</span></span> <span data-ttu-id="845b7-175">숨겨진 멤버는 cmdlet에서 숨겨지고 `Get-Member` 클래스 완성 또는 IntelliSense를 사용 하 여 클래스 정의 외부에서 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-175">Hidden members are hidden from the `Get-Member` cmdlet and can't be displayed using tab completion or IntelliSense outside the class definition.</span></span>

<span data-ttu-id="845b7-176">자세한 내용은 [About_hidden](About_hidden.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="845b7-176">For more information, see [About_hidden](About_hidden.md).</span></span>

### <a name="example-using-hidden-attributes"></a><span data-ttu-id="845b7-177">숨겨진 특성 사용 예</span><span class="sxs-lookup"><span data-stu-id="845b7-177">Example using hidden attributes</span></span>

<span data-ttu-id="845b7-178">**랙** 개체가 생성 될 때 장치에 대 한 슬롯 수는 언제 든 지 변경 될 수 없는 고정 된 값입니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-178">When a **Rack** object is created, the number of slots for devices is a fixed value that shouldn't be changed at any time.</span></span> <span data-ttu-id="845b7-179">이 값은 생성 시에 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-179">This value is known at creation time.</span></span>

<span data-ttu-id="845b7-180">숨겨진 특성을 사용 하면 개발자는 슬롯의 수를 숨기고 의도 하지 않은 랙 크기 변경을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-180">Using the hidden attribute allows the developer to keep the number of slots hidden and prevents unintentional changes the size of the rack.</span></span>

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

<span data-ttu-id="845b7-181">알림 **슬롯** 속성은 출력에 표시 되지 않습니다 `$r1` .</span><span class="sxs-lookup"><span data-stu-id="845b7-181">Notice **Slots** property isn't shown in `$r1` output.</span></span> <span data-ttu-id="845b7-182">그러나이 크기는 생성자에 의해 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-182">However, the size was changed by the constructor.</span></span>

## <a name="static-attribute"></a><span data-ttu-id="845b7-183">정적 특성</span><span class="sxs-lookup"><span data-stu-id="845b7-183">Static attribute</span></span>

<span data-ttu-id="845b7-184">`static`특성은 클래스에 존재 하 고 인스턴스를 필요로 하지 않는 속성 또는 메서드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-184">The `static` attribute defines a property or a method that exists in the class and needs no instance.</span></span>

<span data-ttu-id="845b7-185">정적 속성은 클래스 인스턴스화와 독립적인 항상 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-185">A static property is always available, independent of class instantiation.</span></span> <span data-ttu-id="845b7-186">정적 속성은 클래스의 모든 인스턴스에서 공유 됩니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-186">A static property is shared across all instances of the class.</span></span> <span data-ttu-id="845b7-187">정적 메서드는 항상 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-187">A static method is available always.</span></span> <span data-ttu-id="845b7-188">전체 세션 범위에 대해 활성 상태인 모든 정적 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-188">All static properties live for the entire session span.</span></span>

### <a name="example-using-static-attributes-and-methods"></a><span data-ttu-id="845b7-189">정적 특성 및 메서드를 사용 하는 예제</span><span class="sxs-lookup"><span data-stu-id="845b7-189">Example using static attributes and methods</span></span>

<span data-ttu-id="845b7-190">여기에서 인스턴스화된 랙이 데이터 센터에 있는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-190">Assume the racks instantiated here exist in your data center.</span></span> <span data-ttu-id="845b7-191">따라서 코드에서 랙을 추적 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-191">So, you would like to keep track of the racks in your code.</span></span>

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

### <a name="testing-static-property-and-method-exist"></a><span data-ttu-id="845b7-192">정적 속성 및 메서드 테스트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-192">Testing static property and method exist</span></span>

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

<span data-ttu-id="845b7-193">이 예제를 실행할 때마다 랙 수가 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-193">Notice that the number of racks increases each time you run this example.</span></span>

## <a name="property-validation-attributes"></a><span data-ttu-id="845b7-194">속성 유효성 검사 특성</span><span class="sxs-lookup"><span data-stu-id="845b7-194">Property validation attributes</span></span>

<span data-ttu-id="845b7-195">유효성 검사 특성을 사용 하 여 속성에 지정 된 값이 정의 된 요구 사항을 충족 하는지 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-195">Validation attributes allow you to test that values given to properties meet defined requirements.</span></span> <span data-ttu-id="845b7-196">유효성 검사는 값이 할당 된 순간에 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-196">Validation is triggered the moment that the value is assigned.</span></span> <span data-ttu-id="845b7-197">[About_functions_advanced_parameters](about_functions_advanced_parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="845b7-197">See [about_functions_advanced_parameters](about_functions_advanced_parameters.md).</span></span>

### <a name="example-using-validation-attributes"></a><span data-ttu-id="845b7-198">유효성 검사 특성 사용 예</span><span class="sxs-lookup"><span data-stu-id="845b7-198">Example using validation attributes</span></span>

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

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="845b7-199">PowerShell 클래스의 상속</span><span class="sxs-lookup"><span data-stu-id="845b7-199">Inheritance in PowerShell classes</span></span>

<span data-ttu-id="845b7-200">기존 클래스에서 파생 되는 새 클래스를 만들어 클래스를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-200">You can extend a class by creating a new class that derives from an existing class.</span></span> <span data-ttu-id="845b7-201">파생 클래스는 기본 클래스의 속성을 상속 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-201">The derived class inherits the properties of the base class.</span></span> <span data-ttu-id="845b7-202">필요에 따라 메서드 및 속성을 추가 하거나 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-202">You can add or override methods and properties as required.</span></span>

<span data-ttu-id="845b7-203">PowerShell은 다중 상속을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-203">PowerShell does not support multiple inheritance.</span></span> <span data-ttu-id="845b7-204">클래스는 둘 이상의 클래스에서 상속할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-204">Classes cannot inherit from more than one class.</span></span> <span data-ttu-id="845b7-205">그러나 이러한 용도로 인터페이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-205">However, you can use interfaces for that purpose.</span></span>

<span data-ttu-id="845b7-206">상속 구현은 연산자에 의해 정의 됩니다. `:` 이는이 클래스를 확장 하거나 이러한 인터페이스를 구현 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-206">Inheritance implementation is defined by the `:` operator; which means to extend this class or implements these interfaces.</span></span> <span data-ttu-id="845b7-207">파생 클래스는 항상 클래스 선언에서 맨 왼쪽에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-207">The derived class should always be leftmost in the class declaration.</span></span>

### <a name="example-using-simple-inheritance-syntax"></a><span data-ttu-id="845b7-208">간단한 상속 구문을 사용한 예</span><span class="sxs-lookup"><span data-stu-id="845b7-208">Example using simple inheritance syntax</span></span>

<span data-ttu-id="845b7-209">이 예제에서는 간단한 PowerShell 클래스 상속 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-209">This example shows the simple PowerShell class inheritance syntax.</span></span>

```powershell
Class Derived : Base {...}
```

<span data-ttu-id="845b7-210">이 예제에서는 기본 클래스 다음에 오는 인터페이스 선언으로 상속을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-210">This example shows inheritance with an interface declaration coming after the base class.</span></span>

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a><span data-ttu-id="845b7-211">PowerShell 클래스의 간단한 상속 예제</span><span class="sxs-lookup"><span data-stu-id="845b7-211">Example of simple inheritance in PowerShell classes</span></span>

<span data-ttu-id="845b7-212">이 예제에서는 이전 예제에서 사용 되는 **랙** 및 **장치** 클래스를 정의 하는 것이 더 효율적입니다. 속성 반복 방지, 공용 속성 맞춤 및 공통 비즈니스 논리 다시 사용.</span><span class="sxs-lookup"><span data-stu-id="845b7-212">In this example the **Rack** and **Device** classes used in the previous examples are better defined to: avoid property repetitions, better align common properties, and reuse common business logic.</span></span>

<span data-ttu-id="845b7-213">데이터 센터의 대부분의 개체는 회사 자산으로, 자산으로 추적을 시작 하는 데 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-213">Most objects in the data center are company assets, which makes sense to start tracking them as assets.</span></span> <span data-ttu-id="845b7-214">장치 유형은 열거형에 의해 정의 됩니다 `DeviceType` . 열거에 대 한 자세한 내용은 [about_Enum](about_Enum.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="845b7-214">Device types are defined by the `DeviceType` enumeration, see [about_Enum](about_Enum.md) for details on enumerations.</span></span>

<span data-ttu-id="845b7-215">이 예제에서는 및를 정의 하 고 `Rack` , `ComputeServer` 두 확장을 모두 클래스에 대해 정의 `Device` 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-215">In our example, we're only defining `Rack` and `ComputeServer`; both extensions to the `Device` class.</span></span>

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

### <a name="calling-base-class-constructors"></a><span data-ttu-id="845b7-216">기본 클래스 생성자 호출</span><span class="sxs-lookup"><span data-stu-id="845b7-216">Calling base class constructors</span></span>

<span data-ttu-id="845b7-217">하위 클래스에서 기본 클래스 생성자를 호출 하려면 키워드를 추가 `base` 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-217">To invoke a base class constructor from a subclass, add the `base` keyword.</span></span>

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

### <a name="invoke-base-class-methods"></a><span data-ttu-id="845b7-218">기본 클래스 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="845b7-218">Invoke base class methods</span></span>

<span data-ttu-id="845b7-219">서브 클래스의 기존 메서드를 재정의 하려면 동일한 이름과 서명을 사용 하 여 메서드를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-219">To override existing methods in subclasses, declare methods using the same name and signature.</span></span>

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

<span data-ttu-id="845b7-220">재정의 된 구현에서 기본 클래스 메서드를 호출 하려면 호출할 때 기본 클래스 ([baseclass] $this)로 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-220">To call base class methods from overridden implementations, cast to the base class ([baseclass]$this) on invocation.</span></span>

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

### <a name="inheriting-from-interfaces"></a><span data-ttu-id="845b7-221">인터페이스에서 상속</span><span class="sxs-lookup"><span data-stu-id="845b7-221">Inheriting from interfaces</span></span>

<span data-ttu-id="845b7-222">PowerShell 클래스는 기본 클래스를 확장 하는 데 사용 되는 것과 동일한 상속 구문을 사용 하 여 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-222">PowerShell classes can implement an interface using the same inheritance syntax used to extend base classes.</span></span> <span data-ttu-id="845b7-223">인터페이스는 여러 상속을 허용 하기 때문에 인터페이스를 구현 하는 PowerShell 클래스는 콜론 () 뒤의 형식 이름을 `:` 쉼표 ()로 구분 하 여 여러 형식에서 상속할 수 있습니다 `,` .</span><span class="sxs-lookup"><span data-stu-id="845b7-223">Because interfaces allow multiple inheritance, a PowerShell class implementing an interface may inherit from multiple types, by separating the type names after the colon (`:`) with commas (`,`).</span></span> <span data-ttu-id="845b7-224">인터페이스를 구현 하는 PowerShell 클래스는 해당 인터페이스의 모든 멤버를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-224">A PowerShell class that implements an interface must implement all the members of that interface.</span></span> <span data-ttu-id="845b7-225">구현을 인터페이스 멤버를 생략 하면 스크립트에서 구문 분석 시간 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-225">Omitting the implemention interface members causes a parse-time error in the script.</span></span>

> [!NOTE]
> <span data-ttu-id="845b7-226">PowerShell은 현재 PowerShell 스크립트에서 새 인터페이스 선언을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-226">PowerShell does not currently support declaring new interfaces in PowerShell script.</span></span>

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

## <a name="importing-classes-from-a-powershell-module"></a><span data-ttu-id="845b7-227">PowerShell 모듈에서 클래스 가져오기</span><span class="sxs-lookup"><span data-stu-id="845b7-227">Importing classes from a PowerShell module</span></span>

<span data-ttu-id="845b7-228">`Import-Module` 및 `#requires` 문은 모듈에서 정의한 대로 모듈 함수, 별칭 및 변수만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-228">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="845b7-229">클래스는 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-229">Classes are not imported.</span></span> <span data-ttu-id="845b7-230">`using module`문은 모듈에 정의 된 클래스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-230">The `using module` statement imports the classes defined in the module.</span></span> <span data-ttu-id="845b7-231">모듈이 현재 세션에서 로드 되지 않으면 `using` 문이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-231">If the module isn't loaded in the current session, the `using` statement fails.</span></span> <span data-ttu-id="845b7-232">문에 대 한 자세한 내용은 `using` [about_Using](about_Using.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="845b7-232">For more information about the `using` statement, see [about_Using](about_Using.md).</span></span>

## <a name="the-psreference-type-is-not-supported-with-class-members"></a><span data-ttu-id="845b7-233">PSReference 형식은 클래스 멤버에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-233">The PSReference type is not supported with class members</span></span>

<span data-ttu-id="845b7-234">`[ref]`클래스 멤버와 함께 형식 캐스팅을 자동으로 사용 하면 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-234">Using the `[ref]` type-cast with a class member silently fails.</span></span> <span data-ttu-id="845b7-235">매개 변수를 사용 하는 Api는 `[ref]` 클래스 멤버와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-235">APIs that use `[ref]` parameters cannot be used with class members.</span></span> <span data-ttu-id="845b7-236">**Psreference** 는 COM 개체를 지원 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-236">The **PSReference** was designed to support COM objects.</span></span> <span data-ttu-id="845b7-237">COM 개체에는의 값을 참조로 전달 해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="845b7-237">COM objects have cases where you need to pass a value in by reference.</span></span>

<span data-ttu-id="845b7-238">형식에 대 한 자세한 내용은 `[ref]` [Psreference 클래스](/dotnet/api/system.management.automation.psreference)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="845b7-238">For more information about the `[ref]` type, see [PSReference Class](/dotnet/api/system.management.automation.psreference).</span></span>

## <a name="see-also"></a><span data-ttu-id="845b7-239">참고 항목</span><span class="sxs-lookup"><span data-stu-id="845b7-239">See also</span></span>

- [<span data-ttu-id="845b7-240">About_hidden</span><span class="sxs-lookup"><span data-stu-id="845b7-240">About_hidden</span></span>](About_hidden.md)
- [<span data-ttu-id="845b7-241">about_Enum</span><span class="sxs-lookup"><span data-stu-id="845b7-241">about_Enum</span></span>](about_Enum.md)
- [<span data-ttu-id="845b7-242">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="845b7-242">about_Language_Keywords</span></span>](about_language_keywords.md)
- [<span data-ttu-id="845b7-243">about_Methods</span><span class="sxs-lookup"><span data-stu-id="845b7-243">about_Methods</span></span>](about_methods.md)
- [<span data-ttu-id="845b7-244">about_Using</span><span class="sxs-lookup"><span data-stu-id="845b7-244">about_Using</span></span>](about_using.md)
