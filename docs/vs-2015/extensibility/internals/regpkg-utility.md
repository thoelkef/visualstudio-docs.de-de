---
title: RegPkg-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da637b365eec260a7c1c34bbe7ba96c785cc18fc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781282"
---
# <a name="regpkg-utility"></a>RegPkg-Hilfsprogramm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
>  Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio wird mithilfe der PKGDEF-Dateien. Dadurch für die erweiterungsbereitstellung ohne Zugriff auf die systemregistrierung, die für die VSIX-Bereitstellung erforderlich ist. PKGDEF-Dateien werden erstellt, mit der [CreatePkgDef-Hilfsprogramm](../../extensibility/internals/createpkgdef-utility.md). Weitere Informationen zu Visual Studio-Paket-Bereitstellung, finden Sie unter [Auslieferung von Visual Studio-Erweiterungen](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Das Dienstprogramm "RegPkg.exe" registriert ein VSPackage mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und bereitet es für die Bereitstellung vor. Dieses Hilfsprogramm wird während der Entwicklung von VSPackages im Hintergrund verwendet. Er führt im Rahmen des Buildprozesses, sodass Sie erstellen können, und führen Sie eine VSPackage in der experimentellen Struktur.  
  
 RegPkg kann System-Registrierungs-Skripts in verschiedenen Formaten generieren. Sie können diese Skripts im Bereitstellungsprojekte z. B. msi-Projekten oder Windows Installer XML Toolset Dateien einbinden.  
  
 RegPkg.exe befindet sich gewöhnlich \< *Visual Studio SDK-Installationspfad*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg folgt diese Syntax:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /Root:Root  
 Führt die Registrierung unter der angegebenen  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Stamm.  
  
 /regfile:FileName  
 Erstellt eine REG-Datei, statt die Registrierung aktualisiert.  Kann nicht mit /vrgfile oder /rgsfile oder /wixfile verwendet werden.  
  
 /rgsfile:FileName  
 Erstellt eine RGS-Datei, statt die Registrierung aktualisiert.  Kann nicht mit /vrgfile oder/regfile oder /wixfile verwendet werden.  
  
 /vrgfile:FileName  
 Erstellt eine Datei .vrg, statt die Registrierung aktualisiert.  Kann nicht mit/regfile oder /rgsfile oder /wixfile verwendet werden.  
  
 /rgm  
 Erstellt eine Datei .rgm zusätzlich zu der Rgs-Datei.  Muss mit /rgsfile kombiniert werden.  
  
 /wixfile:FileName  
 Erstellt eine Windows Installer XML Toolset-kompatible Datei, statt die Registrierung aktualisiert.  Kann nicht mit/regfile oder /rgsfile oder /vrgfile verwendet werden.  
  
 /codebase  
 Erzwingt, dass die Registrierung mit Codebasis und nicht als Assembly.  
  
 / Assembly  
 Erzwingt, dass die Registrierung mit Assembly anstelle der Codebasis.  
  
 / unregister  
 Hebt die Registrierung dieses Pakets.  Kann nicht verwendet werden  
  
 mit/regfile oder /vrgfile /rgsfile oder /wixfile.  
  
## <a name="see-also"></a>Siehe auch  
 [Freigeben eines Produkts](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Problembehandlung bei der Registrierung des RegPkg-Pakets](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)

