---
title: Der Support-Website | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 09b43963d657e8d1fe7aa24e98632d2ca46240c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="web-site-support"></a>Der Support-Website
Ein Projektsystem Website ist ein Projektsystem, das Webprojekte erstellt. Webprojekte erstellen wiederum Webanwendungen. Ein Website-Projekt generiert eine ausführbare Datei für jede Webseite, die Code verknüpft ist. Zusätzliche ausführbare Dateien werden aus der Quellcodedateien im Ordner "App_Code" generiert.  
  
 Website-Projektsysteme werden durch Hinzufügen von Vorlagen und Registrierungsattribute zu einem vorhandenen Projektsystem erstellt. Eines dieser Attribute wählt der IntelliSense-Anbieter für die Sprache aus. Die Implementierung eines Anbieters IntelliSense Verweise verarbeitet und des Sprachcompilers aufruft, wenn eine intelligente Webseite, die nicht zwischengespeichert wird angefordert wird.  
  
 Sprachcompiler, die zum Kompilieren von Webseiten verwendet muss registriert werden, mit [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. Können Sie die [ \<Compiler >-Element](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) in einer Datei "Web.config" So registrieren den Compiler an, wie im folgenden Beispiel gezeigt:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorlagen für die Websiteunterstützung](../../extensibility/internals/web-site-support-templates.md)  
 Listet die Vorlagen, die Sie verwenden können, um neue Websiteprojekte und zugehörige Elemente zu erstellen.  
  
 [Attribute der Websiteunterstützung](../../extensibility/internals/web-site-support-attributes.md)  
 Zeigt die Registrierungsattribute, die einem Websiteprojekt zu verbinden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Webprojekte](../../extensibility/internals/web-projects.md)  
 Bietet eine Übersicht über die zwei Arten von Webprojekten, Websiteprojekte und Webanwendungsprojekte.