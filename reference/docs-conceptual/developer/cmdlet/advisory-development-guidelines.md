---
title: 자문 개발 지침 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370042"
---
# <a name="advisory-development-guidelines"></a>권장되는 개발 지침

이 섹션에서는 적절 한 개발과 사용자 환경을 보장 하기 위해 고려해 야 할 지침을 설명 합니다. 경우에 따라 적용 될 수도 있고 그렇지 않을 수도 있습니다.

## <a name="design-guidelines"></a>디자인 지침

Cmdlet을 디자인할 때 다음 지침을 고려해 야 합니다. 상황에 적용 되는 디자인 지침을 찾았으면 유사한 지침에 대 한 코드 지침을 확인 해야 합니다.

### <a name="support-an-inputobject-parameter-ad01"></a>InputObject 매개 변수 지원 (AD01)

Windows PowerShell은 Microsoft .NET Framework 개체와 직접 연동 되므로 사용자가 특정 작업을 수행 하는 데 필요한 형식과 정확히 일치 하는 .NET Framework 개체를 사용할 수 있습니다. `InputObject`는 이러한 개체를 입력으로 사용 하는 매개 변수의 표준 이름입니다. 예를 들어 [Stopproc 자습서](./stopproc-tutorial.md) 의 샘플 **Stop proc** cmdlet은 파이프라인에서 입력을 지 원하는 Process 형식의 `InputObject` 매개 변수를 정의 합니다. 사용자는 프로세스 개체 집합을 가져온 다음이를 조작 하 여 중지할 정확한 개체를 선택 하 고이를 **중지 프로시저** cmdlet에 직접 전달할 수 있습니다.

### <a name="support-the-force-parameter-ad02"></a>Force 매개 변수 지원 (AD02)

경우에 따라 cmdlet은 요청 된 작업을 수행 하지 못하도록 사용자를 보호 해야 합니다. 이러한 cmdlet은 사용자가 작업을 수행할 수 있는 권한이 있는 경우 사용자가 해당 보호를 재정의할 수 있도록 `Force` 매개 변수를 지원 해야 합니다.

예를 들어, [항목 제거](/powershell/module/microsoft.powershell.management/remove-item) cmdlet은 일반적으로 읽기 전용 파일을 제거 하지 않습니다. 그러나이 cmdlet은 `Force` 매개 변수를 지원 하므로 사용자가 읽기 전용 파일을 강제로 제거할 수 있습니다. 사용자에 게 읽기 전용 특성을 수정할 수 있는 권한이 이미 있는 경우 사용자가 파일을 제거 하면 `Force` 매개 변수를 사용 하면 작업이 간단해 집니다. 그러나 사용자에 게 파일을 제거할 수 있는 권한이 없는 경우 `Force` 매개 변수는 영향을 주지 않습니다.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Windows PowerShell을 통해 자격 증명 처리 (AD03)

Cmdlet은 자격 증명을 나타내는 `Credential` 매개 변수를 정의 해야 합니다. 이 매개 변수는 [system.object](/dotnet/api/System.Management.Automation.PSCredential) 형식 이어야 하며 자격 증명 특성 선언을 사용 하 여 정의 해야 합니다. 이 지원은 자동으로 전체 자격 증명을 제공 하지 않을 때 사용자 이름, 암호 또는 둘 다를 사용자에 게 묻는 메시지를 자동으로 표시 합니다. 자격 증명 특성에 대 한 자세한 내용은 [자격 증명 특성 선언](./credential-attribute-declaration.md)을 참조 하세요.

### <a name="support-encoding-parameters-ad04"></a>인코딩 매개 변수 지원 (AD04)

Cmdlet이 파일 시스템의 파일에 쓰거나 파일을 읽는 등 이진 형식에서 텍스트를 읽거나 쓰는 경우에는 cmdlet에 이진 형식으로 텍스트를 인코딩하는 방법을 지정 하는 Encoding 매개 변수가 있어야 합니다.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>테스트 Cmdlet은 부울 (AD05)을 반환 해야 합니다.

리소스에 대해 테스트를 수행 하는 cmdlet은 [부울](/dotnet/api/System.Boolean) 형식을 조건식에 반환 하 여 조건식에 사용할 수 있도록 해야 합니다.

## <a name="code-guidelines"></a>코드 지침

Cmdlet 코드를 작성할 때는 다음 지침을 고려해 야 합니다. 상황에 적용 되는 지침을 찾았으면 유사한 지침에 대 한 디자인 지침을 확인 해야 합니다.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Cmdlet 클래스 명명 규칙 (AC01)을 따릅니다.

표준 명명 규칙을 사용 하 여 cmdlet을 더 검색 가능 하 게 만들고, 사용자가 cmdlet이 수행 하는 작업을 정확 하 게 이해할 수 있도록 도와줍니다. 이 방법은 cmdlet이 공용 형식 이므로 Windows PowerShell을 사용 하는 다른 개발자에 게 특히 중요 합니다.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>올바른 네임 스페이스에 Cmdlet을 정의 합니다.

일반적으로 "를 추가 하는 .NET Framework 네임 스페이스에서 cmdlet에 대 한 클래스를 정의 합니다. Cmdlet을 실행 하는 제품을 나타내는 네임 스페이스에 대 한 명령입니다. 예를 들어 Windows PowerShell에 포함 된 cmdlet은 `Microsoft.PowerShell.Commands` 네임 스페이스에 정의 되어 있습니다.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Cmdlet 이름과 일치 하도록 Cmdlet 클래스 이름을

Cmdlet을 구현 하는 .NET Framework 클래스의 이름을 " *\<Verb > **\<Noun >** \<Command >* "로 이름을 바꿉니다. 여기서 *\<Verb* *> 및 \<Noun* 자리 표시자를로 바꿉니다. cmdlet 이름에 사용 되는 동사와 명사입니다. 예를 들어, [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet은 `GetProcessCommand` 라는 클래스에 의해 구현 됩니다.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>파이프라인 입력이 BeginProcessing 메서드 (AC02)를 재정의 하지 않는 경우

Cmdlet이 파이프라인의 입력을 허용 하지 않는 경우에는 처리를 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 에서 구현 해야 합니다. 이 방법을 사용 하면 Windows PowerShell에서 cmdlet 간의 순서를 유지할 수 있습니다. 파이프라인의 첫 번째 cmdlet은 항상 파이프라인의 나머지 cmdlet이 해당 개체를 반환 하 여 처리를 시작할 수 있습니다.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>중지 요청을 처리 하려면 StopProcessing 메서드 (AC03)를 재정의 합니다.

Cmdlet이 stop 신호를 처리할 수 있도록 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) 를 재정의 합니다. 일부 cmdlet은 작업을 완료 하는 데 시간이 오래 걸리고, cmdlet이 장기 실행 RPC 호출에서 스레드를 차단 하는 경우와 같이 Windows PowerShell 런타임 호출 사이에 긴 시간을 전달할 수 있습니다. 여기에는 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 호출 하 고, [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드를 호출 하 고, 완료 하는 데 시간이 오래 걸릴 수 있는 기타 피드백 메커니즘을 수행 하는 cmdlet이 포함 됩니다. . 이러한 경우 사용자는 이러한 cmdlet에 중지 신호를 보내야 할 수 있습니다.

### <a name="implement-the-idisposable-interface-ac04"></a>IDisposable 인터페이스 구현 (AC04)

Cmdlet에 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 통해 삭제 되지 않는 개체 (파이프라인에 기록)가 있는 경우 cmdlet에서 추가 개체를 삭제 해야 할 수 있습니다. 예를 들어 cmdlet이 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드에서 파일 핸들을 [열고 해당 핸들](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 을 계속 열어 둘 경우이 핸들을 사용 하 여 해당 핸들을 열어 둘 수 있습니다. 처리가 끝날 때 닫힙니다.

Windows PowerShell 런타임에서는 항상 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드를 호출 하지 않습니다. 예를 들어 cmdlet이 작업을 통해 중간에 취소 되거나 cmdlet의 일부에서 종료 오류가 발생 하는 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 를 호출할 수 없습니다. 따라서 개체 정리를 필요로 하는 cmdlet의 .NET Framework 클래스는 Windows PowerShell 런타임 처리가 완료된 후에 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)와 [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) 방법을 모두 호출할 수 있도록 종료자를 포함한 완전한 [System.IDisposable](/dotnet/api/System.IDisposable) 인터페이스 패턴을 구현해야 합니다.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Serialization 친화적인 매개 변수 형식 사용 (AC05)

원격 컴퓨터에서 cmdlet 실행을 지원 하려면 클라이언트 컴퓨터에서 쉽게 직렬화 할 수 있는 형식을 사용 하 고 서버 컴퓨터에서 함께 사용 합니다. 다음 형식은 serialization에 편리 합니다.

기본 형식:

- Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32 및 UInt64.

- 부울, Guid, Byte [], TimeSpan, DateTime, Uri 및 버전입니다.

- Char, String, XmlDocument.

기본 제공 rehydratable 형식:

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- 유형이

- IPAddress, MailAddress

- CultureInfo

- X509Certificate2, System.security.cryptography.x509certificates.x500distinguishedname

- DirectorySecurity, System.security.accesscontrol.filesecurity, RegistrySecurity

기타 형식:

- SecureString

- 컨테이너 (위 형식의 목록 및 사전)

### <a name="use-securestring-for-sensitive-data-ac06"></a>중요 한 데이터에 SecureString 사용 (AC06)

중요 한 데이터를 처리 하는 경우 항상 [system.web](/dotnet/api/System.Security.SecureString) 데이터 형식을 사용 합니다. 여기에는 매개 변수에 대 한 파이프라인 입력 뿐만 아니라 중요 한 데이터를 파이프라인으로 반환 하는 작업이 포함 될 수 있습니다.

## <a name="see-also"></a>참고 항목

[필수 개발 지침](./required-development-guidelines.md)

[권장 되는 개발 지침](./strongly-encouraged-development-guidelines.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
