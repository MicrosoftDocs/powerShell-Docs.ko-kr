---
title: 목록 뷰 (레이블) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362792"
---
# <a name="list-view-labels"></a>목록 보기(레이블)

이 예제에서는 목록의 각 행에 대 한 사용자 지정 레이블을 표시 하는 목록 뷰를 구현 하는 방법을 보여 줍니다. 이 목록 보기에는 Servicecontroller의 속성이 표시 됩니다. [ Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) [cmdlet에](/powershell/module/Microsoft.PowerShell.Management/Get-Service) 의해 반환 되는 Fullname 개체입니다. 목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.

### <a name="to-load-this-formatting-file"></a>이 서식 파일을 로드 하려면

1. 이 항목의 예제 섹션에서 XML을 텍스트 파일로 복사 합니다.

2. 텍스트 파일을 저장 합니다. 파일에 `format.ps1xml` 확장을 추가 하 여 서식 파일 인지 확인 해야 합니다.

3. Windows PowerShell을 열고 다음 명령을 실행 하 여 현재 세션에 형식 지정 파일을 로드 합니다. `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > 이 서식 파일은 Windows PowerShell 서식 파일에 의해 이미 정의 된 개체의 표시를 정의 합니다. Cmdlet을 실행할 때 `prependPath` 매개 변수를 사용 해야 하며,이 서식 파일을 모듈로 로드할 수 없습니다.

## <a name="demonstrates"></a>보여

이 서식 파일은 다음 XML 요소를 보여 줍니다.

- 뷰의 [Name](./name-element-for-view-format.md) 요소입니다.

- 뷰가 표시 하는 개체를 정의 하는 [Viewselectedby](./viewselectedby-element-format.md) 요소입니다.

- 뷰가 표시 하는 속성을 정의 하는 [이 listcontrol](./listcontrol-element-format.md) 요소입니다.

- 목록 뷰의 행에 표시 되는 항목을 정의 하는 [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) 요소입니다.

- 목록 뷰의 행에 표시 되는 항목을 정의 하는 [Label](./label-element-for-listitem-for-listcontrol-format.md) 요소입니다.

- 표시 되는 속성을 정의 하는 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소입니다.

## <a name="example"></a>예제

다음 XML은 각 행에 사용자 지정 레이블을 표시 하는 목록 뷰를 정의 합니다. 이 경우 레이블에는 각 글자가 대문자 인 속성 이름과 "property" 라는 단어가 포함 됩니다. 각 행에 속성의 이름이 표시 되 고 그 다음에 속성 값이 표시 됩니다.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

다음 예제에서는 Windows PowerShell에서 Servicecontroller를 표시 하는 방법을 보여 줍니다 [. Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 이 서식 파일이 로드 된 후의 Fullname 개체입니다.

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a>참고 항목

[서식 파일의 예](./examples-of-formatting-files.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
