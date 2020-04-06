---
title: Fehlerbehebung bei der Registrierung von RegPkg-Paketen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebae9f7c5b4d1a6dcfee20c3b36c02f8ead2e0bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704330"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Problembehandlung bei der Registrierung des RegPkg-Pakets
> [!NOTE]
> Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio ist die Verwendung von .pkgdef-Dateien. Dies ermöglicht die Erweiterungsbereitstellung, ohne auf die Systemregistrierung zugreifen zu müssen. Pkgdef-Dateien werden mit dem [Dienstprogramm CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md)erstellt.

 Um ein Paket mithilfe von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]RegPkg in zu registrieren, müssen Sie die für Ihr Paket geeignete Version von RegPkg verwenden.

## <a name="regpkg-versions-related-to-package-versions"></a>RegPkg-Versionen im Zusammenhang mit Paketversionen
 Es gibt zwei Versionen von RegPkg. Eine Version ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]in enthalten. Verwenden Sie diese Version, um Pakete zu registrieren, die mithilfe einer der folgenden Assemblys erstellt wurden:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Es können keine Pakete registriert werden, die mithilfe der früheren Microsoft.VisualStudio.Shell.dll-Assembly erstellt wurden.

   Die frühere Version von RegPkg kann Pakete registrieren, die mithilfe der Microsoft.VisualStudio.Shell.dll-Assembly erstellt wurden. Es kann jedoch keine Pakete registrieren, die mithilfe neuerer Versionen dieser Assembly erstellt wurden.

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../../extensibility/internals/vspackages.md)
