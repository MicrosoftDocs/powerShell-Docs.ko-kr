---
title: PowerShell 이진 모듈을 작성 하는 방법 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 92395bd6b8be1bd3741888eb3716d62f0253e213
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779270"
---
# <a name="how-to-write-a-powershell-binary-module"></a>PowerShell 이진 모듈을 작성하는 방법

이진 모듈은 cmdlet 클래스를 포함 하는 모든 어셈블리 (.dll)가 될 수 있습니다. 기본적으로 이진 모듈을 가져올 때 어셈블리의 모든 cmdlet을 가져옵니다. 그러나 루트 모듈이 어셈블리인 모듈 매니페스트를 만들어 가져오는 cmdlet을 제한할 수 있습니다. 예를 들어 매니페스트의 CmdletsToExport 키를 사용 하 여 필요한 cmdlet만 내보낼 수 있습니다. 또한 이진 모듈에는 단일 cmdlet에서 사용할 수 없는 추가 파일, 디렉터리 구조 및 유용한 관리 정보의 다른 부분이 포함 될 수 있습니다.

다음 절차에서는 PowerShell 이진 모듈을 만들고 설치 하는 방법을 설명 합니다.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>PowerShell 이진 모듈을 만들고 설치 하는 방법

1. 필요한 기능이 포함 된 이진 PowerShell 솔루션 (예: c #으로 작성 된 cmdlet)을 만들고 제대로 실행 되는지 확인 합니다.

   코드 관점에서 이진 모듈의 핵심은 단순히 cmdlet 어셈블리입니다. 실제로 PowerShell은 로드 및 언로드 측면에서 단일 cmdlet 어셈블리를 모듈로 처리 하며 개발자의 추가 작업은 필요 하지 않습니다. Cmdlet을 작성 하는 방법에 대 한 자세한 내용은 [Windows PowerShell Cmdlet 작성](../cmdlet/writing-a-windows-powershell-cmdlet.md)을 참조 하세요.

2. 필요한 경우 추가 cmdlet, XML 파일 등의 나머지 솔루션을 만들고 모듈 매니페스트를 사용 하 여 설명 합니다.

   모듈 매니페스트는 솔루션의 cmdlet 어셈블리를 설명 하는 것 외에도 모듈을 내보내고 가져오는 방법, 노출 되는 cmdlet 및 모듈에 추가 되는 추가 파일을 설명할 수 있습니다.
   앞서 설명한 것 처럼 PowerShell은 추가 작업 없이 모듈 처럼 이진 cmdlet을 처리할 수 있습니다.
   따라서 모듈 매니페스트는 주로 여러 파일을 단일 패키지로 결합 하거나 지정 된 어셈블리에 대 한 게시를 명시적으로 제어 하는 데 유용 합니다.
   자세한 내용은 [PowerShell 모듈 매니페스트를 작성 하는 방법](how-to-write-a-powershell-module-manifest.md)을 참조 하세요.

   다음 코드는 모듈로 사용할 수 있는 동일한 파일에 세 개의 cmdlet이 포함 된 매우 간단한 c # 코드 블록입니다.

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. 솔루션을 패키지 하 고 PowerShell 모듈 경로의 어딘가에 패키지를 저장 합니다.

   `PSModulePath`전역 환경 변수는 PowerShell이 모듈을 찾는 데 사용 하는 기본 경로를 설명 합니다. 예를 들어 시스템에 모듈을 저장 하는 일반적인 경로는 `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>` 입니다. 기본 경로를 사용 하지 않는 경우 설치 하는 동안 모듈의 위치를 명시적으로 명시 해야 합니다. 솔루션에 대 한 여러 어셈블리와 파일을 저장 하는 폴더가 필요할 수 있으므로 모듈을 저장할 폴더를 만들어야 합니다.

   기술적으로는의 어디에 나 모듈을 설치할 필요가 없습니다. 즉, `PSModulePath` PowerShell이 모듈을 찾을 기본 위치입니다. 그러나 모듈을 다른 위치에 저장 해야 하는 경우를 제외 하 고이 작업을 수행 하는 것이 좋습니다. 자세한 내용은 [Powershell 모듈](./installing-a-powershell-module.md) 설치 및 [Powershell 모듈 설치 경로 수정](./modifying-the-psmodulepath-installation-path.md)을 참조 하세요.

4. [Import-module에 대 한](/powershell/module/Microsoft.PowerShell.Core/Import-Module)호출을 사용 하 여 모듈을 PowerShell로 가져옵니다.

   [Import-module을 호출 하면 모듈이](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 활성 메모리에 로드 됩니다. PowerShell 3.0 이상 버전을 사용 하는 경우 코드에서 모듈의 이름만 호출 하면 해당 모듈의 이름도 가져옵니다. 자세한 내용은 [PowerShell 모듈 가져오기](./importing-a-powershell-module.md)를 참조 하세요.

## <a name="importing-snap-in-assemblies-as-modules"></a>스냅인 어셈블리를 모듈로 가져오기

스냅인 어셈블리에 존재 하는 cmdlet 및 공급자를 이진 모듈로 로드할 수 있습니다. 스냅인 어셈블리를 이진 모듈로 로드 하면 해당 스냅인의 cmdlet 및 공급자가 사용자에 게 제공 되지만 어셈블리의 스냅인 클래스는 무시 되 고 스냅인이 등록 되지 않습니다. 따라서 Windows PowerShell에서 제공 하는 스냅인 cmdlet은 cmdlet 및 공급자를 세션에서 사용할 수 있는 경우에도 스냅인을 검색할 수 없습니다.

또한 스냅인에서 참조 하는 서식 지정 또는 형식 파일은 이진 모듈의 일부로 가져올 수 없습니다.
서식 지정 및 형식 파일을 가져오려면 모듈 매니페스트를 만들어야 합니다.
[PowerShell 모듈 매니페스트를 작성 하는 방법](how-to-write-a-powershell-module-manifest.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)
