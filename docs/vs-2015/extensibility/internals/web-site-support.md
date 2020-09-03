---
title: Website Unterstützung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a96504783de466551c6fb9d055b95ba38df760
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687691"
---
# <a name="web-site-support"></a>Websiteunterstützung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bei einem Website Projekt System handelt es sich um ein Projekt System, das Webprojekte erstellt. Webprojekte erstellen wiederum Webanwendungen. Ein Website Projekt generiert eine ausführbare Datei für jede Webseite, die über zugeordneten Code verfügt. Aus den Quell Code Dateien im Ordner/App_Code werden zusätzliche ausführbare Dateien generiert.  
  
 Website Projektsysteme werden erstellt, indem einem vorhandenen Projekt Systemvorlagen und Registrierungs Attribute hinzugefügt werden. Eines dieser Attribute wählt den IntelliSense-Anbieter für die Sprache aus. Die IntelliSense-Anbieter Implementierung behandelt Verweise und ruft den sprach Compiler auf, wenn eine nicht zwischengespeicherte SmartWeb Page angefordert wird.  
  
 Der zum Kompilieren von Webseiten verwendete sprach Compiler muss bei registriert werden [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Sie können das- [ \<compiler> Element](https://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) in einer Web.config Datei verwenden, um den Compiler zu registrieren, wie im folgenden Beispiel gezeigt:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorlagen für die Websiteunterstützung](../../extensibility/internals/web-site-support-templates.md)  
 Listet die Vorlagen auf, die Sie zum Erstellen neuer Website Projekte und zugehöriger Elemente verwenden können.  
  
 [Attribute der Websiteunterstützung](../../extensibility/internals/web-site-support-attributes.md)  
 Zeigt die Registrierungs Attribute an, die ein Website Projekt mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und verbinden [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] .  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Webprojekte](../../extensibility/internals/web-projects.md)  
 Bietet eine Übersicht über die zwei Arten von Webprojekten, Website Projekten und Webanwendungs Projekten.
