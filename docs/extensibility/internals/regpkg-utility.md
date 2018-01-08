---
title: RegPkg-Dienstprogramm | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c4a4a3481b6ff1a5b8af0581e2c04602073adeae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="regpkg-utility"></a>RegPkg-Dienstprogramm
> [!NOTE]
>  Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio ist mit der PKGDEF-Dateien. Dies ermöglicht Erweiterung Bereitstellung ohne Zugriff auf die systemregistrierung, die dies eine Voraussetzung für die VSIX-Bereitstellung ist. PKGDEF-Dateien werden erstellt, mit der [CreatePkgDef Utility](../../extensibility/internals/createpkgdef-utility.md). Weitere Informationen zu Visual Studio-Paket-Bereitstellung, finden Sie unter [Versand der Visual Studio-Erweiterungen](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Das Hilfsprogramm RegPkg.exe registriert eine VSPackage mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für die Bereitstellung vorbereiten. Dieses Dienstprogramm wird im Hintergrund während der Entwicklung des VSPackage verwendet. Er führt als Teil des Buildprozesses, sodass Sie erstellen können, und führen Sie eine VSPackage in der experimentellen Struktur.  
  
 RegPkg kann in verschiedenen Formaten System Registrierungsskripts generieren. Sie können diese Skripts im Bereitstellungsprojekte z. B. msi-Projekten oder Windows Installer XML-Toolset-Dateien einbeziehen.  
  
 RegPkg.exe befindet sich gewöhnlich unter \< *Visual Studio SDK-Installationspfad*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg folgt diese Syntax:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /Root:Root  
 Führt die Registrierung unter dem angegebenen  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Stamm.  
  
 /regfile:FileName  
 Erstellt eine REG-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit /vrgfile oder /rgsfile oder /wixfile verwendet werden.  
  
 /rgsfile:FileName  
 Erstellt eine RGS-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit /vrgfile oder/regfile oder /wixfile verwendet werden.  
  
 /vrgfile:FileName  
 Erstellt eine .vrg-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/regfile oder /rgsfile oder /wixfile verwendet werden.  
  
 /rgm  
 Erstellt eine Datei .rgm zusätzlich zu der Rgs-Datei.  Muss mit /rgsfile kombiniert werden.  
  
 /wixfile:FileName  
 Erstellt eine Windows Installer XML-Toolset-kompatible Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/regfile oder /rgsfile oder /vrgfile verwendet werden.  
  
 /codebase  
 Erzwingt, dass die Registrierung Codebasis anstelle der Assembly.  
  
 / Assembly  
 Erzwingt, dass die Registrierung Assembly anstelle der Codebasis.  
  
 / unregister  
 Hebt die Registrierung dieses Pakets.  Kann nicht verwendet werden  
  
 mit/regfile oder /vrgfile oder /rgsfile oder /wixfile.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 [Problembehandlung bei der Registrierung des RegPkg-Pakets](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)