---
ms.date: 06/09/2017
title: 스크립트에 대한 라이선스 동의 필요
description: 이 문서에서는 PowerShell 갤러리에 게시되고 최종 사용자 라이선스 동의가 필요한 스크립트를 사용하는 방법을 설명합니다.
ms.openlocfilehash: d82974810fd1e73ef8d9e5771fc430d0f7964e87
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656084"
---
# <a name="requiring-license-acceptance-for-scripts"></a>스크립트에 대한 라이선스 동의 필요

스크립트에 대한 라이선스 동의가 지원되지 않습니다. 그러나 라이선스 동의가 필요한 모듈에서 스크립트가 사용되는 시나리오는 지원됩니다.

PowerShellGet 스크립트 명령은 사용자가 라이선스를 확인한 것처럼 동작하는 매개 변수 **AcceptLicense** 를 지원합니다. **AcceptLicense** 가 지정되지 않으면 종속 모듈에 대한 `license.txt` 파일이 사용자에게 표시되고 라이선스에 동의하라는 메시지가 표시됩니다.

## <a name="examples"></a>예제

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>예제 1: 라이선스 동의가 필요한 종속성이 있는 스크립트 설치

‘ScriptRequireLicenseAcceptance’ 스크립트는 'ModuleRequireLicenseAcceptance' 모듈에 종속됩니다. 사용자에게 라이선스에 동의하라는 메시지가 표시됩니다.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>예제 2: 라이선스 동의 및 -AcceptLicense가 필요한 종속성이 있는 스크립트 설치

‘ScriptRequireLicenseAcceptance’ 스크립트는 'ModuleRequireLicenseAcceptance' 모듈에 종속됩니다. -AcceptLicense가 지정되면 사용자에게 라이선스에 동의하라는 메시지가 표시되지 않습니다.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>자세한 내용

- [모듈에 대한 라이선스 동의 지원 필요](module-license-acceptance.md)
- [PowerShellGallery에서 라이선스 동의 지원 필요](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Azure Automation에 배포에 대한 라이선스 동의 필요](../how-to/working-with-packages/deploy-to-azure-automation.md)
