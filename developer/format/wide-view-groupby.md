---
title: 넓은 보기 (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083657"
---
# <a name="wide-view-groupby"></a>넓게 보기(GroupBy)

이 예제에서는 그룹을 표시 하는 넓은 보기를 구현 하는 방법을 보여 줍니다 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 반환한 개체는 `Get-Service` cmdlet. 넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.

### <a name="to-load-this-formatting-file"></a>이 서식 파일을 로드 하려면

1. 이 항목의 예제 섹션에서 XML을 텍스트 파일로 복사 합니다.

2. 텍스트 파일을 저장 합니다. 추가 해야 합니다 `format.ps1xml` 서식 파일로 식별 하는 파일 확장명입니다.

3. Windows PowerShell을 열고 현재 세션으로 서식 파일을 로드 하려면 다음 명령을 실행: `Update-formatdata -prependpath PathToFormattingFile`합니다.

   > [!WARNING]
   > 이 형식 지정 파일 형식 지정 파일을 Windows PowerShell에서 이미 정의 되어 있는 개체의 표시를 정의 합니다. 사용 해야 합니다는 `prependPath` 모듈로 파일 매개 변수 cmdlet을 실행 하 고 형식을 로드할 수 없습니다.

## <a name="demonstrates"></a>데모

이 서식 파일에 다음 XML 요소를 보여 줍니다.

- 합니다 [이름을](./name-element-for-view-format.md) 뷰에 대 한 요소입니다.

- 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 어떤 개체를 뷰에 표시를 정의 하는 요소입니다.

- 합니다 [GroupBy](./groupby-element-for-view-format.md) 새 그룹을 표시 될 때를 정의 하는 요소입니다.

- 합니다 [WideItem](./wideitem-element-for-widecontrol-format.md) 어떤 속성은 보기에서 표시를 정의 하는 요소입니다.

## <a name="example"></a>예제

다음 XML 개체 그룹을 표시 하는 넓은 보기를 정의 합니다. 각 새로운 그룹 시작 될 때 값을 [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 속성 변경 합니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

다음 예제에서는 Windows PowerShell의 표시 하는 방법을 보여 줍니다는 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 이 서식 파일 로드 된 후 개체입니다.

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a>참고 항목

[서식 파일의 예](./examples-of-formatting-files.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
