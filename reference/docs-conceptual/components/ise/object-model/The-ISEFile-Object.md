---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEFile 개체
ms.openlocfilehash: 1069e46aa586b8df2050129194a909b90f77b745
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737001"
---
# <a name="the-isefile-object"></a>ISEFile 개체

**ISEFile** 개체는 Windows PowerShell® ISE(통합 스크립팅 환경)에 있는 파일을 나타내며, **Microsoft.PowerShell.Host.ISE.ISEFile** 클래스의 인스턴스입니다. 이 항목에는 멤버 메서드 및 멤버 속성이 나열됩니다. `$psISE.CurrentFile`과 PowerShell 탭의 파일 컬렉션에 있는 파일이 \*\***Microsoft.PowerShell.Host.ISE.ISEFile** 클래스의 전체 인스턴스입니다.

## <a name="methods"></a>메서드

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

파일을 디스크에 저장합니다.

**\[saveEncoding\]** - 선택적 [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx). 저장된 파일에 사용할 선택적 문자 인코딩 매개 변수입니다. 기본값은 **UTF8**입니다.

### <a name="exceptions"></a>예외

- **System.IO.IOException**: 파일을 저장할 수 없습니다.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(filename, \[saveEncoding\]\)

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

지정한 파일 이름 및 인코딩으로 파일을 저장합니다.

**filename** - 파일을 저장하는 데 사용할 이름입니다.

**\[saveEncoding\]** - 선택적 [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx). 저장된 파일에 사용할 선택적 문자 인코딩 매개 변수입니다. 기본값은 **UTF8**입니다.

### <a name="exceptions"></a>예외

- **System.ArgumentNullException**: **filename** 매개 변수는 null입니다.
- **System.ArgumentException**: **filename** 매개 변수는 비어 있습니다.
- **System.IO.IOException**: 파일을 저장할 수 없습니다.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>속성

### <a name="displayname"></a>DisplayName

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

이 파일의 표시 이름을 포함하는 문자열을 가져오는 읽기 전용 속성입니다. 이름은 편집기의 맨 위에 있는 **파일** 탭에 표시됩니다. 이름의 끝에 별표(`(*)`)가 있다면 파일에 저장되지 않은 변경 내용이 있다는 것입니다.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>편집기

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

지정된 파일에 사용되는 [편집기 개체](The-ISEEditor-Object.md)를 가져오는 읽기 전용 속성입니다.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Encoding

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

원래 파일 인코딩을 가져오는 읽기 전용 속성입니다. **System.Text.Encoding** 개체입니다.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

열려 있는 파일의 전체 경로를 지정하는 문자열을 가져오는 읽기 전용 속성입니다.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

파일이 마지막으로 수정한 후 저장된 경우 `$true`를 반환하는 읽기 전용 부울 속성입니다.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Windows PowerShell ISE 2.0 이상에서 지원됩니다.

파일에 제목이 지정된 적이 없는 경우 `$true`를 반환하는 읽기 전용 속성입니다.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>참고 항목

- [The ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Windows PowerShell ISE 스크립팅 개체 모델의 용도](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 개체 모델 계층 구조](The-ISE-Object-Model-Hierarchy.md)
