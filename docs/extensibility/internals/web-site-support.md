---
title: Der Support-Website | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 636cbee868bb53be2d0ef85bd309459570eb84c0
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support"></a>Der Support-Website
Ein Website-Projektsystem ist ein Projektsystem, die Webprojekte erstellt. Webprojekte erstellen wiederum von ASP.NET-Webanwendungen. Ein Website-Projekt generiert eine ausführbare Datei für jede Webseite, die Code verknüpft ist. Weitere ausführbare Dateien werden von der Quellcodedateien im Ordner "App_Code" generiert.  
  
 Website-Projektsysteme werden durch Hinzufügen von Vorlagen und Registrierung Attribute mit einem vorhandenen Projektsystem erstellt. Eines dieser Attribute wählt den IntelliSense-Anbieter für die Sprache. Die Implementierung eines Anbieters IntelliSense Verweise verarbeitet und des Sprachcompilers aufruft, wenn angefordert wird, dass Sie eine intelligenten Webseite, die nicht zwischengespeichert wird.  
  
 Der Language-Compiler zum Kompilieren von Webseiten verwendet muss registriert werden [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. Sie können die [ \<Compiler > Element](http://msdn.microsoft.com/Library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) in der Datei Web.config registriert den Compiler an, wie im folgenden Beispiel:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Unterstützung für Websitevorlagen](../../extensibility/internals/web-site-support-templates.md)  
 Listet die Vorlagen, die Sie verwenden können, um neue Websiteprojekte und zugehörige Elemente zu erstellen.  
  
 [Website-Support-Attribute](../../extensibility/internals/web-site-support-attributes.md)  
 Zeigt die Registrierung Attribute, die ein Websiteprojekt zu verbinden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Webprojekte](../../extensibility/internals/web-projects.md)  
 Bietet eine Übersicht über die zwei Arten von Webprojekten, von Websiteprojekten und Webanwendungsprojekten.
