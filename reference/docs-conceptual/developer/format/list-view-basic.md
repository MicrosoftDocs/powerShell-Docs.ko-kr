---
title: 목록 뷰 (기본) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362812"
---
# <a name="list-view-basic"></a>목록 보기(기본)

이 예제에서는 Servicecontroller를 표시 하는 기본 목록 뷰를 구현 하는 방법을 보여 줍니다 [. Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) [cmdlet에서](/powershell/module/microsoft.powershell.management/get-service) 반환 되는 Fullname 개체입니다. 목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.

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

- 표시 되는 속성을 정의 하는 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소입니다.

## <a name="example"></a>예제

다음 XML은 Servicecontroller의 네 가지 속성을 표시 하는 목록 뷰를 정의 합니다. [ Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다. 각 행에 속성의 이름이 표시 되 고 그 다음에 속성 값이 표시 됩니다.

```xml
<Configuration>
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
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

다음 예제에서는 Windows PowerShell에서 Servicecontroller를 표시 하는 방법을 보여 줍니다 [. Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 이 서식 파일이 로드 된 후의 Fullname 개체입니다.

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a>참고 항목

[서식 파일의 예](./examples-of-formatting-files.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
