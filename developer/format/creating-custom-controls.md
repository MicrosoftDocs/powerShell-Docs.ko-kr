---
title: 사용자 지정 컨트롤 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066688"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="c6a32-102">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="c6a32-102">Creating Custom Controls</span></span>

<span data-ttu-id="c6a32-103">사용자 지정 컨트롤은 형식 지정 파일의 가장 유연한 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c6a32-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="c6a32-104">테이블, 목록 및 데이터 테이블 같은 데이터 형식 구조를 정의 하는 와이드 뷰가 달리 사용자 지정 컨트롤을 통해 데이터의 개별 부분을 표시 되는 방식을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6a32-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="c6a32-105">서식 파일의 모든 보기에 사용할 수 있는 사용자 지정 컨트롤의 공통 집합을 정의할 수 있습니다, 특정 보기를 사용할 수 있는 사용자 지정 컨트롤을 정의할 수 있습니다 또는 개체 그룹을 사용할 수 있는 컨트롤의 집합을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6a32-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="c6a32-106">사용자 지정 컨트롤 예제</span><span class="sxs-lookup"><span data-stu-id="c6a32-106">Custom Control Example</span></span>

<span data-ttu-id="c6a32-107">다음 예제에서는 Certificates.Format.ps1xml 파일에 정의 된 사용자 지정 컨트롤을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c6a32-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="c6a32-108">이 사용자 지정 컨트롤 구분 하는데 사용 되는 [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) 테이블 뷰에 표시 되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="c6a32-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a><span data-ttu-id="c6a32-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6a32-109">See Also</span></span>

[<span data-ttu-id="c6a32-110">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="c6a32-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
