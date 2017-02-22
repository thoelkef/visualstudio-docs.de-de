---
title: "RegPkg-Dienstprogramm | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Regpkg Registrierung-Dienstprogramm"
  - "Registrierung Regpkg-Dienstprogramm"
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# RegPkg-Dienstprogramm
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio ist mit der PKGDEF\-Dateien. Dies ermöglicht Erweiterung Bereitstellung ohne Zugriff auf die systemregistrierung, die für die VSIX\-Bereitstellung erforderlich ist. PKGDEF\-Dateien werden erstellt, mit der [CreatePkgDef\-Dienstprogramm](../../extensibility/internals/createpkgdef-utility.md). Weitere Informationen zur Bereitstellung von Visual Studio\-Paket finden Sie unter [Lieferung von Visual Studio\-Erweiterungen](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Das Dienstprogramm RegPkg.exe registriert ein VSPackage mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für die Bereitstellung vorbereiten. Dieses Dienstprogramm ist im Hintergrund während der Entwicklung von VSPackages verwendet. Er führt im Rahmen des Buildprozesses, sodass können Sie erstellen und Ausführen von einem VSPackage in der experimentellen Struktur.  
  
 RegPkg kann in verschiedenen Formaten Registrierungsskripts System generieren. Sie können diese Skripte in Bereitstellungsprojekte wie MSI\-Projekte oder Windows Installer XML Toolset Dateien einschließen.  
  
 RegPkg.exe befindet sich gewöhnlich unter \<*Visual Studio SDK\-Installationspfad*\> \\VisualStudioIntegration\\Tools\\Bin\\RegPkg.exe. RegPkg folgt diese Syntax:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 \/Root:Root  
 Führt die Registrierung unter dem angegebenen  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Stamm.  
  
 \/regfile:FileName  
 Erstellt eine REG\-Datei, statt die Registrierung aktualisiert.  Kann mit \/vrgfile oder \/rgsfile oder \/wixfile verwendet werden.  
  
 \/rgsfile:FileName  
 Erstellt eine .rgs\-Datei, statt die Registrierung aktualisiert.  Kann mit \/vrgfile oder\/regfile oder \/wixfile verwendet werden.  
  
 \/vrgfile:FileName  
 Erstellt eine .vrg\-Datei, statt die Registrierung aktualisiert.  Kann nicht mit\/regfile oder \/rgsfile oder \/wixfile verwendet werden.  
  
 \/rgm  
 Erstellt eine Datei .rgm zusätzlich zu der Rgs\-Datei.  Muss mit \/rgsfile kombiniert werden.  
  
 \/wixfile:FileName  
 Erstellt eine Windows Installer XML Toolset\-kompatible Datei, statt die Registrierung aktualisiert.  Kann nicht mit\/regfile oder \/rgsfile oder \/vrgfile verwendet werden.  
  
 \/codebase  
 Erzwingt die Registrierung mit Codebasis anstelle der Assembly.  
  
 \/ Assembly  
 Erzwingt die Registrierung mit Assembly statt Codebasis.  
  
 \/ unregister  
 Hebt die Registrierung dieses Pakets.  Kann nicht verwendet werden  
  
 mit\/regfile oder \/vrgfile oder \/rgsfile oder \/wixfile.  
  
## Siehe auch  
 [Freigeben eines Produkts](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Problembehandlung RegPkg\-Paket\-Registrierung](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)