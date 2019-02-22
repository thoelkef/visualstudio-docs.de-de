---
title: RegPkg-Hilfsprogramm | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b9b07bc801e687da9ce93968dbac59966328484
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619237"
---
# <a name="regpkg-utility"></a>RegPkg-Hilfsprogramm
> [!NOTE]
>  Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio wird mithilfe der PKGDEF-Dateien. Dadurch für die erweiterungsbereitstellung ohne Zugriff auf die systemregistrierung, die für die VSIX-Bereitstellung erforderlich ist. PKGDEF-Dateien werden erstellt, mit der [CreatePkgDef-Hilfsprogramm](../../extensibility/internals/createpkgdef-utility.md). Weitere Informationen zu Visual Studio-Paket-Bereitstellung, finden Sie unter [Auslieferung von Visual Studio-Erweiterungen](../../extensibility/shipping-visual-studio-extensions.md).

 Das Dienstprogramm "RegPkg.exe" registriert ein VSPackage mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und bereitet es für die Bereitstellung vor. Dieses Hilfsprogramm wird während der Entwicklung von VSPackages im Hintergrund verwendet. Er führt im Rahmen des Buildprozesses, sodass Sie erstellen können, und führen Sie eine VSPackage in der experimentellen Struktur.

 RegPkg kann System-Registrierungs-Skripts in verschiedenen Formaten generieren. Sie können diese Skripts im Bereitstellungsprojekte z. B. msi-Projekten oder Windows Installer XML Toolset Dateien einbinden.

 RegPkg.exe befindet sich gewöhnlich \< *Visual Studio SDK-Installationspfad*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg folgt diese Syntax:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /Root:Root führt Eintragung unter der angegebenen

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Stamm.

 /regfile:FileName erstellt eine REG-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit /vrgfile oder /rgsfile oder /wixfile verwendet werden.

 /rgsfile:FileName erstellt eine RGS-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit /vrgfile oder/regfile oder /wixfile verwendet werden.

 /vrgfile:FileName erstellt eine Datei .vrg, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/regfile oder /rgsfile oder /wixfile verwendet werden.

 /rgm erstellt eine Datei .rgm und in der Rgs-Datei.  Muss mit /rgsfile kombiniert werden.

 /wixfile:FileName erstellt eine Windows Installer XML Toolset-kompatible Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/regfile oder /rgsfile oder /vrgfile verwendet werden.

 / codebase erzwingt, dass die Registrierung mit Codebasis und nicht als Assembly.

 / Assembly erzwingt, dass die Registrierung mit Assembly anstelle der Codebasis.

 / unregister von Unregisters dieses Paket.  Kann nicht verwendet werden

 mit/regfile oder /vrgfile /rgsfile oder /wixfile.

## <a name="see-also"></a>Siehe auch
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Problembehandlung bei der Registrierung des RegPkg-Pakets](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)