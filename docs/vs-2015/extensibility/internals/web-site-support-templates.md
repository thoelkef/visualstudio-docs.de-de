---
title: Vorlagen für die Websiteunterstützung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dca7768f31219328648d457d188086e0185e2ffc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200962"
---
# <a name="web-site-support-templates"></a>Vorlagen für die Websiteunterstützung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Website Projekt- und Elementvorlagen bieten wiederverwendbare und anpassbare Website Projekt- und Stubs, die den Entwicklungsprozess zu beschleunigen, durch das Entfernen der neuen Website-Projekte und Elemente von Grund auf neu erstellen zu müssen. Weitere Informationen zu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Vorlagen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Vorlage-Projektordner  
 Vorlagen für Webprojekte-Vorlage werden in der Regel auf installiert [*Visual Studio-Installationspfad*] \Common7\IDE\ProjectTemplates\Web\\, jeweils in einem Unterordner mit dem die Web-Programmiersprache.  
  
## <a name="project-file"></a>Projektdatei  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE) erfordert eine Dateierweiterung des Projekts als eine Möglichkeit, eine Vorlage das richtige Projekt-Typ zugeordnet werden. Da Webprojekte nicht über eine Projektdatei verfügen, ist die dummyprojekt Datei Erweiterung WEBPROJ registriert, um dies zu unterstützen.  
  
 Optional kann eine Namenszeichenfolge Sprache hinzugefügt werden, auf die Vorlage so aktivieren Sie die Web-Projektsystem an, legen Sie die Standardsprache in der **neues Element hinzufügen** Dialogfeld für Elemente auf Grundlage der Vorlage. Die Zeichenfolge muss die erste Zeile der Datei sein und muss übereinstimmen, den unter AddItemLanguageName registriert werden, bei der Registrierung der Intellisense-Engine und der Name, unter dem Projekt Subtype(VsTemplate) registriert. Weitere Informationen finden Sie unter [Attribute der Websiteunterstützung](../../extensibility/internals/web-site-support-attributes.md).  
  
 Wenn die Zeichenfolge nicht vorhanden ist, versucht das Web-Projektsystem, die Standardsprache, die basierend auf den spracherweiterungen-Attribut und den Dateinamen der Seiten, die dem Webprojekt hinzugefügt werden, von der Projektvorlage für die Vorlage zu bestimmen.  
  
## <a name="project-templates"></a>Projektvorlagen  
 Website-Projektvorlagen werden verwendet, um als Reaktion auf neue Websites erstellen die **neue Website** Befehl die **Datei** Menü. Drei Typen von Website-Projekt werden derzeit unterstützt:  
  
- Leere Website-Projekten  
  
- Website-Projekten  
  
- Web Service-Projekte  
  
### <a name="empty-web-site-projects"></a>Leere Website-Projekten  
 Erstellen dieser Dateien eine neue leere Website als Reaktion auf die **leere Website** Befehl, der verfügbar ist, nachdem auf **neue Website** auf die **Datei** Menü:  
  
- EmptyWeb.vstemplate  
  
     Die Vorlagendatei, die die Erstellung der neue, leere Website führt.  
  
- EmptyWeb.webproj  
  
     Diese Datei ist ein Artefakt des Projektsystems Vorlage. Es erfüllt den Projektverweis für die Datei in der Datei EmptyWeb.vstemplate.  
  
### <a name="web-site-projects"></a>Website-Projekten  
 Diese Dateien eine neue Website erstellen, als Reaktion auf die **ASP.NET-Website** Befehl, der verfügbar ist, nachdem auf **neue Website** auf die **Datei** Menü:  
  
- Default.aspx  
  
     Standard-Startseite für die neue Website. Language-Attribut gibt an, die Codebehind-Sprache, und das CodeFile-Attribut gibt an, die abhängige Datei, die den Codebehind-Code, der mit dieser Seite verknüpft sind.  
  
- "Default.aspx". *Erweiterung*  
  
     Die abhängige Datei, die den Codebehind-Code für die Standard-Startseite enthält. Die Codebehind-Sprache bestimmt das *Erweiterung* dieser Datei.  
  
- web.config  
  
     Die Konfigurationsdatei für den Stamm web.site.  
  
- WebApplication.vstemplate  
  
     Die Vorlagendatei, die bestimmt den Inhalt der Website-Lösung und erzwingt die Erstellung des dem App_Data-Ordner.  
  
- WebApplication.webproj  
  
     Diese Datei ist ein Artefakt des Projektsystems Vorlage. Es erfüllt den Projektverweis für die Datei in der Datei WebApplication.vstemplate.  
  
### <a name="web-service-projects"></a>Web Service-Projekte  
 Diese Dateien eine neue Website erstellen, als Reaktion auf die **ASP.NET Web Service** Befehl der verfügbar ist, nachdem auf **neue Website** auf die **Datei** Menü:  
  
- Service.asmx  
  
     Die HTML-Seite für den neuen Webdienst. Language-Attribut gibt an, die Codebehind-Sprache, und das CodeBehind-Attribut gibt an, die abhängige Datei, die den Codebehind-Code, der diesem Dienst zugeordnet.  
  
- -Dienst. *Erweiterung*  
  
     Die abhängige Datei, die die Dienstklasse implementiert wird. Die Codebehind-Sprache bestimmt das *Erweiterung* dieser Datei.  
  
- web.config  
  
- Die Konfigurationsdatei für den Stamm web.site.  
  
- WebService.vstemplate  
  
     Die Vorlagendatei, die bestimmt den Inhalt der Website-Lösung und erzwingt die Erstellung der Ordner App_Data und "App_Code". Der Dienst. *Erweiterung* Datei in den Ordner "App_Code" kopiert.  
  
- WebService.webproj  
  
     Diese Datei ist ein Artefakt des Projektsystems Vorlage. Es erfüllt den Projektverweis für die Datei in der Datei WebService.vstemplate.  
  
## <a name="project-item-template-folder"></a>Vorlage-Projektelementordners.  
 Web-Vorlage Projektelementvorlagen werden in der Regel auf installiert [*Visual Studio-Installationspfad*] \Common7\IDE\ItemTemplates\Web\\, jeweils in einem Unterordner mit dem das Web Programmiersprache.  
  
## <a name="project-item-templates"></a>Projektelementvorlagen  
 Website-Projektelementvorlagen werden verwendet, um das Hinzufügen neuer Web-Seiten zu einer Website als Reaktion auf die **vorhandenes Element hinzufügen** Befehl. Diese Arten von Webseiten werden derzeit unterstützt:  
  
- Neue Klasse  
  
- Neue HTML-Seite  
  
- Neues Web Form  
  
- Neue Masterseite  
  
### <a name="new-class"></a>Neue Klasse  
 Diese Vorlage erstellt eine neue Quelldatei, die als Reaktion auf eine leere Klasse definiert die **neue Klasse hinzufügen** Befehl.  
  
- Klasse. *Erweiterung*  
  
     Die Quelldatei, die die leere Klasse implementiert. Die Codebehind-Sprache bestimmt das *Erweiterung* dieser Datei.  
  
- Class.VSTEMPLATE  
  
     Die Vorlagendatei, die die Quelldatei erstellt und seinen Inhalt bestimmt.  
  
### <a name="new-html-page"></a>Neue HTML-Seite  
 Diese Vorlage erstellt eine neue Webseite in Reaktion auf die **neue HTML-Seite hinzufügen** Befehl.  
  
- HTMLPage.htm  
  
     Der ab Inhalt der Webseite. Diese Webseite weist normalerweise keine abhängigen zugeordneten Codebehind-Datei. Um eine intelligente Seite mit einer zugeordneten Codebehind-Datei zu erstellen, verwenden Sie stattdessen die Web Form-Vorlage.  
  
- HTMLPage.vstemplate  
  
     Die Vorlagendatei, die die Webseite erstellt und dessen Inhalt bestimmt.  
  
### <a name="new-webform"></a>Neue WebForm  
 Diese Vorlage erstellt eine neue intelligente Webseite in Reaktion auf die **Web-Formulars** Befehl.  
  
 Wählen Sie zum Erstellen einer abhängigen Codebehind-Quelldatei **Code in eigener Datei platzieren**. Andernfalls wird eine einzelne Webseite erstellt, die einen leeren Block ein Skript keinen und \<% Page % > Anweisungen für eine abhängige Datei einbinden.  
  
 Wählen Sie zum Erstellen einer Inhaltsseite für eine ausgewählte Masterseite **Masterseite auswählen**.  
  
- WebForm.aspx  
  
     Der ab Inhalt der Webseite. Diese Webseite hat keine abhängigen zugeordneten Codebehind-Datei.  
  
- WebForm_cb.aspx  
  
     Der ab Inhalt der Webseite. Diese Webseite ist eine abhängige zugeordneten Codebehind-Datei.  
  
- CodeBehind. *Erweiterung*  
  
     Die abhängige Datei, die der Webform-Klasse implementiert. Die Codebehind-Sprache bestimmt das *Erweiterung* dieser Datei.  
  
- ContentPage.aspx  
  
     Der ab Inhalt der Webseite als Inhaltsseite. Diese Webseite hat keine abhängigen zugeordneten Codebehind-Datei.  
  
- ContentPage_cb.aspx  
  
     Der ab Inhalt der Webseite als Inhaltsseite. Diese Webseite ist eine abhängige zugeordneten Codebehind-Datei.  
  
- WebForm.vstemplate  
  
     Die Vorlagendatei, die bestimmt, den Inhalt, der die neue Webseite und der abhängigen Datei, sofern vorhanden.  
  
### <a name="new-master-page"></a>Neue Masterseite  
 Diese Vorlage erstellt eine neue Masterseite als Reaktion auf die **neue Masterseite hinzufügen** Befehl.  
  
 Wählen Sie zum Erstellen einer abhängigen Codebehind-Quelldatei **Code in eigener Datei platzieren**. Andernfalls wird eine einzelne Webseite erstellt, die einen leeren Block ein Skript keinen und \<% Page % > Anweisungen für eine abhängige Datei einbinden.  
  
- MasterPage.master  
  
     Der ab Inhalt der Masterseite. Diese Masterseite besitzt keine abhängigen zugeordneten Codebehind-Datei.  
  
- MasterPage_cb.master  
  
     Der ab Inhalt der Masterseite. Diese Masterseite verfügt über eine abhängige zugeordneten Codebehind-Datei.  
  
- CodeBehind. *Erweiterung*  
  
     Die abhängige Datei, die die Masterseite-Klasse implementiert. Die Codebehind-Sprache bestimmt das *Erweiterung* dieser Datei.  
  
- MasterPage.vstemplate  
  
     Die Vorlagendatei, die bestimmt, den Inhalt der neuen Masterseite und die abhängige Datei, sofern vorhanden.  
  
## <a name="see-also"></a>Siehe auch  
 [Websiteunterstützung](../../extensibility/internals/web-site-support.md)
