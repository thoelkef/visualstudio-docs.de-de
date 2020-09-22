---
title: Regpkg-Hilfsprogramm | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1895d3b57e5109f824728021cb1d64f0c527384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841177"
---
# <a name="regpkg-utility"></a>RegPkg-Hilfsprogramm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio besteht darin, pkgdef-Dateien zu verwenden. Dies ermöglicht die Erweiterungs Bereitstellung, ohne auf die Systemregistrierung zugreifen zu müssen. Dies ist eine Voraussetzung für die VSIX-Bereitstellung. Pkgdef-Dateien werden mit dem [Dienstprogramm](../../extensibility/internals/createpkgdef-utility.md)"|" erstellt. Weitere Informationen zur Bereitstellung von Visual Studio-Paketen finden Sie unter [Versand von Visual Studio-Erweiterungen](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Das RegPkg.exe-Hilfsprogramm registriert ein VSPackage bei [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und bereitet es für die Bereitstellung vor. Dieses Hilfsprogramm wird im Hintergrund während der VSPackage-Entwicklung verwendet. Sie wird als Teil des Buildprozesses ausgeführt, sodass Sie ein VSPackage in der experimentellen Struktur erstellen und ausführen können.  
  
 Regpkg kann System Registrierungs Skripts in verschiedenen Formaten generieren. Sie können diese Skripts in Bereitstellungs Projekte wie MSI-Projekte oder Windows Installer XML-toolsetdateien integrieren.  
  
 RegPkg.exe befindet sich in der Regel unter \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. Regpkg folgt der folgenden Syntax:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root: root  
 Führt die Registrierung unter dem angegebenen aus.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] root  
  
 /regfile: Dateiname  
 Erstellt eine REG-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/vrgfile oder/rgsfile oder/wixfile. verwendet werden.  
  
 /rgsfile: Dateiname  
 Erstellt eine RGS-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/vrgfile oder/regfile oder/wixfile. verwendet werden.  
  
 /vrgfile: Dateiname  
 Erstellt eine VRG-Datei, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/regfile oder/rgsfile oder/wixfile. verwendet werden.  
  
 /rgm  
 Erstellt eine RGM-Datei zusätzlich zur RGS-Datei.  Muss mit/rgsfile. kombiniert werden  
  
 /wixfile: Dateiname  
 Erstellt eine Datei mit Windows Installer XML-Toolsets, anstatt die Registrierung zu aktualisieren.  Kann nicht mit/regfile oder/rgsfile oder/vrgfile. verwendet werden.  
  
 /codebase  
 Erzwingt die Registrierung bei CodeBase anstelle der Assembly.  
  
 /Assembly  
 Erzwingt die Registrierung bei der Assembly anstelle der Codebasis.  
  
 /Unregister  
 Hebt die Registrierung dieses Pakets auf.  Kann nicht verwendet werden  
  
 mit/regfile oder/vrgfile oder/rgsfile oder/wixfile.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Freigeben eines Produkts](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Problembehandlung bei der Registrierung des RegPkg-Pakets](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
