---
title: RegPkg-Dienstprogramm | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cebfd7a9782a2760eb33f7e56bfe16b126fc6251
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705637"
---
# <a name="regpkg-utility"></a>RegPkg-Hilfsprogramm
> [!NOTE]
> Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio ist die Verwendung von .pkgdef-Dateien. Dies ermöglicht die Erweiterungsbereitstellung, ohne auf die Systemregistrierung zugreifen zu müssen, was eine Voraussetzung für die VSIX-Bereitstellung ist. Pkgdef-Dateien werden mit dem [Dienstprogramm CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md)erstellt. Weitere Informationen zur Visual Studio-Paketbereitstellung finden Sie unter [Versand von Visual Studio-Erweiterungen](../../extensibility/shipping-visual-studio-extensions.md).

 Das Dienstprogramm RegPkg.exe registriert ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage mit und bereitet es für die Bereitstellung vor. Dieses Dienstprogramm wird während der VSPackage-Entwicklung hinter den Kulissen verwendet. Es wird als Teil des Buildprozesses ausgeführt, sodass Sie ein VSPackage im experimentellen Bienenstock erstellen und ausführen können.

 RegPkg kann Systemregistrierungsskripte in verschiedenen Formaten generieren. Sie können diese Skripts in Bereitstellungsprojekte wie MSI-Projekte oder Windows Installer XML Toolset-Dateien integrieren.

 RegPkg.exe befindet sich \<in der Regel unter *Visual Studio SDK-Installationspfad*>-VisualStudioIntegration-Tools-Bin-RegPkg.exe. RegPkg folgt dieser Syntax:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Führt die Registrierung unter der angegebenen

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] root

 /regfile:FileName Erstellt eine .reg-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit /vrgfile oder /rgsfile oder /wixfile verwendet werden.

 /rgsfile:FileName Erstellt eine .rgs-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit /vrgfile oder /regfile oder /wixfile verwendet werden.

 /vrgfile:FileName Erstellt eine VRG-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit /regfile oder /rgsfile oder /wixfile verwendet werden.

 /rgm Erstellt zusätzlich zur datei rgs eine .rgm-Datei.  Muss mit /rgsfile kombiniert werden.

 /wixfile:FileName Erstellt eine Windows Installer XML Toolset-kompatible Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit /regfile oder /rgsfile oder /vrgfile verwendet werden.

 /codebase Erzwingt die Registrierung mit CodeBase anstelle von Assembly.

 /assembly Erzwingt die Registrierung mit Assembly anstelle von CodeBase.

 /unregister Entregistriert dieses Paket.  Kann nicht verwendet werden

 mit /regfile oder /vrgfile oder /rgsfile oder /wixfile.

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Problembehandlung bei der Registrierung des RegPkg-Pakets](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
