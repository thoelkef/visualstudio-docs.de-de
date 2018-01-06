---
title: "Unterstützung für Websitevorlagen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b17674b8cd5058ec20db4c483b2c3508aa275b29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="web-site-support-templates"></a>Unterstützung für Websitevorlagen
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Website Projekt- und Elementvorlagen bieten wiederverwendbare und anpassbare Website Projekt- und elementeigenschaftenänderungen Stubs, die den Entwicklungsprozess beschleunigen, durch das Entfernen der neuen Website-Projekten und Elementen von Grund auf neu erstellen zu müssen. Weitere Informationen zu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Vorlagen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Vorlage-Projektordner  
 Vorlagen für Webprojekte-Vorlage in der Regel auf installiert [*Visual Studio-Installationspfad*] \Common7\IDE\ProjectTemplates\Web\\, jeweils in einem Unterordner mit dem im Web Programmiersprache.  
  
## <a name="project-file"></a>Projektdatei  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) erfordert eine Dateierweiterung Projekt als Möglichkeit zum Zuordnen von einer Vorlage in den richtigen Projekt-Typ. Da Webprojekte keine Projektdatei, ist die dummy-Projekt Datei Erweiterung WEBPROJ registriert, um dies zu unterstützen.  
  
 Optional kann eine Namenszeichenfolge Sprache hinzugefügt werden, auf die Vorlage so aktivieren Sie das Web-Projektsystem die Standardsprache festlegen, in der **neues Element hinzufügen** Dialogfeld für Elemente basierend auf der Vorlage. Die Zeichenfolge muss die erste Zeile der Datei und muss übereinstimmen, den Namen, die in der Intellisense-Engine-Registrierung unter AddItemLanguageName registriert und der Name, unter dem Projekt Subtype(VsTemplate) registriert. Weitere Informationen finden Sie unter [Website Unterstützung Attribute](../../extensibility/internals/web-site-support-attributes.md).  
  
 Wenn die Zeichenfolge nicht vorhanden ist, versucht das Projektsystem Web, bestimmen die Standardsprache, die basierend auf den spracherweiterungen Attribut und den Dateinamen der Seiten, die von der Projektvorlage für die Vorlage das Webprojekt hinzugefügt.  
  
## <a name="project-templates"></a>Projektvorlagen  
 Website-Projektvorlagen werden verwendet, um das Erstellen neuen Websites als Antwort auf die **neue Website** Befehl die **Datei** Menü. Drei Typen von Website-Projekt werden derzeit unterstützt:  
  
-   Leere Website-Projekte  
  
-   Website-Projekten  
  
-   Webdienstprojekte  
  
### <a name="empty-web-site-projects"></a>Leere Website-Projekte  
 Erstellen dieser Dateien eine neue leere Website als Antwort auf die **leere Website** Befehl, der verfügbar ist, nach dem auf **neue Website** auf die **Datei** Menü:  
  
-   EmptyWeb.vstemplate  
  
     Die Vorlagendatei, die die Erstellung der neuen leere Website führt.  
  
-   EmptyWeb.webproj  
  
     Diese Datei ist ein Artefakt des Projektsystems Vorlage. Er entspricht den Projektverweis-Datei in der Datei EmptyWeb.vstemplate.  
  
### <a name="web-site-projects"></a>Website-Projekten  
 Diese Dateien eine neue Website zu erstellen, als Antwort auf die **ASP.NET-Website** Befehl, der verfügbar ist, nach dem auf **neue Website** auf die **Datei** Menü:  
  
-   Default.aspx  
  
     Standard-Startseite für die neue Website. Language-Attribut gibt die Codebehind-Sprache, und das CodeFile-Attribut gibt an, die abhängige Datei, die mit der Codebehind-Code, der auf dieser Seite zugeordnet.  
  
-   "Default.aspx". *Erweiterung*  
  
     Die abhängige Datei, die für die Standardstartseite den Codebehind-Code enthält. Die Codebehind-Sprache bestimmt, die *Erweiterung* dieser Datei.  
  
-   web.config  
  
     Die Konfigurationsdatei für den Stamm web.site.  
  
-   WebApplication.vstemplate  
  
     Die Vorlagendatei, die bestimmt den Inhalt der Website-Lösung und erzwingt die Erstellung der Ordner "App_Data".  
  
-   WebApplication.webproj  
  
     Diese Datei ist ein Artefakt des Projektsystems Vorlage. Er entspricht den Projektverweis-Datei in der Datei WebApplication.vstemplate.  
  
### <a name="web-service-projects"></a>Webdienstprojekte  
 Diese Dateien eine neue Website zu erstellen, als Antwort auf die **ASP.NET-Webdienst** Befehl verfügbar ist, nachdem auf **neue Website** auf die **Datei** Menü:  
  
-   Service.asmx  
  
     Die HTML-Seite für den neuen Web-Dienst. Language-Attribut gibt die Codebehind-Sprache, und das CodeBehind-Attribut gibt an, die abhängige Datei, die mit der Codebehind-Code, der diesem Dienst zugeordnet.  
  
-   -Dienst. *Erweiterung*  
  
     Die abhängige Datei, die die Dienstklasse implementiert. Die Codebehind-Sprache bestimmt, die *Erweiterung* dieser Datei.  
  
-   web.config  
  
-   Die Konfigurationsdatei für den Stamm web.site.  
  
-   WebService.vstemplate  
  
     Die Vorlagendatei, die bestimmt den Inhalt der Website-Lösung und erzwingt die Erstellung der Ordner App_Data und App_Code. Der Dienst. *Erweiterung* Datei in Ordner "App_Code" kopiert.  
  
-   WebService.webproj  
  
     Diese Datei ist ein Artefakt des Projektsystems Vorlage. Er entspricht den Projektverweis-Datei in der Datei WebService.vstemplate.  
  
## <a name="project-item-template-folder"></a>Projektelementordner Vorlage  
 Web Project-Vorlage Elementvorlagen sind in der Regel auf installiert [*Visual Studio-Installationspfad*] \Common7\IDE\ItemTemplates\Web\\, jeweils in einem Unterordner mit dem das Web Programmiersprache.  
  
## <a name="project-item-templates"></a>Projektelementvorlagen  
 Website-Projektelementvorlagen werden verwendet, um neue Webseiten als Antwort auf eine Website hinzufügen die **vorhandenes Element hinzufügen** Befehl. Diese Arten von Webseiten werden derzeit unterstützt:  
  
-   Neue Klasse  
  
-   Neue HTML-Seite  
  
-   Neue Webformular  
  
-   Neue Gestaltungsvorlage  
  
### <a name="new-class"></a>Neue Klasse  
 Diese Vorlage erstellt eine neue Quelldatei, die als Antwort auf eine leere Klasse definiert die **neue Klasse hinzufügen** Befehl.  
  
-   Klasse. *Erweiterung*  
  
     Die Quelldatei, die der leere Klasse implementiert. Die Codebehind-Sprache bestimmt, die *Erweiterung* dieser Datei.  
  
-   Class.VSTEMPLATE  
  
     Die Vorlagendatei, die die Quelldatei erstellt und seinen Inhalt bestimmt.  
  
### <a name="new-html-page"></a>Neue HTML-Seite  
 Diese Vorlage erstellt eine neue Webseite als Antwort auf die **neue HTML-Seite hinzufügen** Befehl.  
  
-   HTMLPage.htm  
  
     Der Start Inhalt der Webseite. Diese Webseite weist normalerweise keine abhängigen zugeordneten Codebehind-Datei. Um eine intelligente Seite mit einer zugeordneten Codebehind-Datei zu erstellen, verwenden Sie stattdessen das Web Form-Vorlage.  
  
-   HTMLPage.vstemplate  
  
     Die Vorlagendatei, die auf der Webseite erstellt und seinen Inhalt bestimmt.  
  
### <a name="new-webform"></a>Neue WebForm  
 Diese Vorlage erstellt eine neue Webseite intelligenten als Antwort auf die **neue Webformular hinzufügen** Befehl.  
  
 Wählen Sie zum Erstellen einer Quelldatei abhängige Codebehind **fügen Sie Code in separate Datei**. Andernfalls wird eine Webseite erstellt, die einen leeren scripting Block keine und \<% Seite % > Anweisungen hinzu, um eine abhängige Datei zu verknüpfen.  
  
 Wählen Sie zum Erstellen einer Inhaltsseite für eine ausgewählte Gestaltungsvorlage **Masterseite auswählen**.  
  
-   "Webform.aspx"  
  
     Der Start Inhalt der Webseite. Diese Webseite weist keine abhängigen zugeordneten Codebehind-Datei.  
  
-   WebForm_cb.aspx  
  
     Der Start Inhalt der Webseite. Diese Webseite ist eine abhängige zugeordneten Codebehind-Datei.  
  
-   CodeBehind. *Erweiterung*  
  
     Die abhängige Datei, die der Webform-Klasse implementiert. Die Codebehind-Sprache bestimmt, die *Erweiterung* dieser Datei.  
  
-   ContentPage.aspx  
  
     Der Start Inhalt der Webseite als Inhaltsseite. Diese Webseite weist keine abhängigen zugeordneten Codebehind-Datei.  
  
-   ContentPage_cb.aspx  
  
     Der Start Inhalt der Webseite als Inhaltsseite. Diese Webseite ist eine abhängige zugeordneten Codebehind-Datei.  
  
-   WebForm.vstemplate  
  
     Die Vorlagendatei, die den Inhalt der neuen Webseite und dessen abhängige Datei ggf. bestimmt.  
  
### <a name="new-master-page"></a>Neue Gestaltungsvorlage  
 Diese Vorlage erstellt eine neue Masterseite als Antwort auf die **neue Gestaltungsvorlage hinzufügen** Befehl.  
  
 Wählen Sie zum Erstellen einer Quelldatei abhängige Codebehind **fügen Sie Code in separate Datei**. Andernfalls wird eine Webseite erstellt, die einen leeren scripting Block keine und \<% Seite % > Anweisungen hinzu, um eine abhängige Datei zu verknüpfen.  
  
-   MasterPage.master  
  
     Der Start Inhalt der Masterseite. Diese Masterseite besitzt keine abhängigen zugeordneten Codebehind-Datei.  
  
-   MasterPage_cb.master  
  
     Der Start Inhalt der Masterseite. Diese Masterseite besitzt eine abhängige zugeordneten Codebehind-Datei.  
  
-   CodeBehind. *Erweiterung*  
  
     Die abhängige Datei, die der Gestaltungsvorlage-Klasse implementiert. Die Codebehind-Sprache bestimmt, die *Erweiterung* dieser Datei.  
  
-   MasterPage.vstemplate  
  
     Die Vorlagendatei, die den Inhalt der neuen Masterseite und dessen abhängige Datei ggf. bestimmt.  
  
## <a name="see-also"></a>Siehe auch  
 [Websiteunterstützung](../../extensibility/internals/web-site-support.md)