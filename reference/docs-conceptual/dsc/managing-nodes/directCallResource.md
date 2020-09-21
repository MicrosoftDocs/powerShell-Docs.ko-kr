---
ms.date: 08/11/2020
keywords: dsc,powershell,configuration,setup
title: DSC 리소스 메서드를 직접 호출
ms.openlocfilehash: 029a278c938e414820e172b85fac3cb3ad4b4afa
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162497"
---
# <a name="calling-dsc-resource-methods-directly"></a>DSC 리소스 메서드를 직접 호출

>적용 대상: Windows PowerShell 5.0

[Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet을 사용해 DSC 리소스의 함수 또는 메서드(MOF 기반 리소스의 `Get-TargetResource`, `Set-TargetResource` 및 `Test-TargetResource` 함수 또는 클래스 기반 리소스의 **Get**, **Set** 및 **Test** 메서드)를 직접 호출할 수 있습니다. 이 기능은 DSC 리소스를 사용하려는 타사에서, 또는 리소스를 개발하는 유용한 도구로 사용될 수 있습니다.

> [!NOTE]
> PowerShell 7.0 이상에서 `Invoke-DscResource`는 더 이상 WMI DSC 리소스 호출을 지원하지 않습니다. 여기에는 **PSDesiredStateConfiguration**의 **File** 및 **Log** 리소스가 포함됩니다.

일반적으로 이 cmdlet은 메타구성 속성 `refreshMode = 'Disabled'`와 함께 사용되지만 **refreshMode**의 설정과 관계없이 사용할 수 있습니다.

`Invoke-DscResource` cmdlet을 호출하는 경우 **Method** 매개 변수를 사용해 호출할 메서드 또는 함수를 지정합니다. 해시 테이블을 **Property** 매개 변수 값으로 전달해 리소스의 속성을 지정합니다.

다음은 리소스 메서드를 직접 호출하는 예입니다.

## <a name="ensure-a-file-is-present"></a>파일이 있는지 확인

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>파일이 있는지 테스트

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>파일의 내용 가져오기

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>[!NOTE]
> 복합 리소스 메서드를 직접 호출할 수 없습니다. 대신 복합 리소스를 구성하는 기본 리소스의 메서드를 호출합니다.

## <a name="see-also"></a>참고 항목

- [MOF를 사용하여 사용자 지정 DSC 리소스 작성](../resources/authoringResourceMOF.md)
- [PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성](../resources/authoringResourceClass.md)
- [DSC 리소스 디버그](../troubleshooting/debugResource.md)
