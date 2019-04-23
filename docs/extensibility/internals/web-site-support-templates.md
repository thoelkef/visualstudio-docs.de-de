---
title: Vorlagen für die Websiteunterstützung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc5370db9c090fe5a7dcd9852d3df94e05f08e1f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116497"
---
# <a name="web-site-support-templates"></a>Vorlagen für die Websiteunterstützung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Website Projekt- und Elementvorlagen bieten wiederverwendbare und anpassbare Website Projekt- und Stubs, die den Entwicklungsprozess zu beschleunigen, durch das Entfernen der neuen Website-Projekte und Elemente von Grund auf neu erstellen zu müssen. Weitere Informationen zu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Vorlagen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Vorlage-Projektordner
 Vorlagen für Webprojekte werden in der Regel auf installiert [*Visual Studio-Installationspfad*] \Common7\IDE\ProjectTemplates\Web\\, jeweils in einem Unterordner mit dem die Web-Programmiersprache.

## <a name="project-file"></a>Projektdatei
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) erfordert eine Dateierweiterung des Projekts als eine Möglichkeit, eine Vorlage das richtige Projekt-Typ zugeordnet werden. Da Webprojekte keine Projektdatei, ist dem dummyprojekt Datei Erweiterung WEBPROJ registriert, um die Vorlage für den Projekttyp zuzuordnen.

 Optional kann eine Namenszeichenfolge Sprache hinzugefügt werden, für die Vorlage so aktivieren Sie die Web-Projektsystem an, legen Sie die Standardsprache in der **neues Element hinzufügen** Dialogfeld für Elemente auf Grundlage der Vorlage. Die Zeichenfolge muss es sich um die erste Zeile der Datei sein. Er muss sowohl der Name, unter AddItemLanguageName in der IntelliSense-Engine-Registrierung registriert und der Name, unter dem Projekt Subtype(VsTemplate) registriert übereinstimmen. Weitere Informationen finden Sie unter [Attribute der Websiteunterstützung](../../extensibility/internals/web-site-support-attributes.md).

 Wenn die Zeichenfolge nicht vorhanden ist, versucht das Web-Projektsystem ab, die Standardsprache, die basierend auf den spracherweiterungen-Attribut und den Dateinamen der Seiten, die dem Webprojekt hinzugefügt werden, von der Projektvorlage zu bestimmen.

## <a name="project-templates"></a>Projektvorlagen
 Website-Projektvorlagen werden verwendet, um als Reaktion auf neue Websites erstellen die **neue Website** Befehl die **Datei** Menü. Drei Typen von Website-Projekt werden derzeit unterstützt:

- Leere Website-Projekten

- Website-Projekten

- Web Service-Projekte

### <a name="empty-web-site-projects"></a>Leere Website-Projekten
 Diese Dateien erstellt eine neue leere Website als Reaktion auf die **leere Website** Befehl, der nach der Auswahl verfügbar ist **Datei** > **neue Website**:

- EmptyWeb.vstemplate

     Die Vorlagendatei, die die Erstellung der neue, leere Website führt.

- EmptyWeb.webproj

     Diese Datei ist ein Artefakt des Projektsystems Vorlage. Es erfüllt den Projektverweis für die Datei in der Datei EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Website-Projekten
 Diese Dateien eine neue Website erstellen, als Reaktion auf die **ASP.NET-Website** Befehl, der nach der Auswahl verfügbar ist **Datei** > **neue Website**:

- Default.aspx

     Standard-Startseite für die neue Website. Language-Attribut gibt an, die Codebehind-Sprache, und das CodeFile-Attribut gibt an, die abhängige Datei, die den auf dieser Seite zugeordneten Codebehind-Code enthält.

- Default.aspx.*extension*

     Die abhängige Datei, die den Codebehind-Code für die Standard-Startseite enthält. Die Codebehind-Sprache bestimmt das *Erweiterung* dieser Datei.

- web.config

     Die Konfigurationsdatei für den Stamm web.site.

- WebApplication.vstemplate

     Die Vorlagendatei, die bestimmt den Inhalt der Website-Lösung und erzwingt die Erstellung des dem App_Data-Ordner.

- WebApplication.webproj

     Diese Datei ist ein Artefakt des Projektsystems Vorlage. Es erfüllt den Projektverweis für die Datei in der Datei WebApplication.vstemplate.

### <a name="web-service-projects"></a>Web Service-Projekte
 Diese Dateien eine neue Website erstellen, als Reaktion auf die **ASP.NET-Webdienst** Befehl, der nach der Auswahl verfügbar ist **Datei** > **neue Website**:

- Service.asmx

     Die HTML-Seite für den neuen Webdienst. Language-Attribut gibt an, die Codebehind-Sprache, und das CodeBehind-Attribut gibt an, die abhängige Datei, die den Codebehind-Code, der diesem Dienst zugeordnete enthält.

- -Dienst. *extension*

     Die abhängige Datei, die die Dienstklasse implementiert wird. Die Codebehind-Sprache bestimmt das *Erweiterung* dieser Datei.

- web.config

- Die Konfigurationsdatei für den Stamm web.site.

- WebService.vstemplate

     Die Vorlagendatei, die bestimmt den Inhalt der Website-Lösung und erzwingt die Erstellung der Ordner App_Data und "App_Code". Der Dienst. *Erweiterung* Datei in den Ordner "App_Code" kopiert.

- WebService.webproj

     Diese Datei ist ein Artefakt des Projektsystems Vorlage. Es erfüllt den Projektverweis für die Datei in der Datei WebService.vstemplate.

## <a name="project-item-template-folder"></a>Vorlage-Projektelementordners.
 Web-Projekt-Item-Vorlagen werden in der Regel im installiert [*Visual Studio-Installationspfad*] \Common7\IDE\ItemTemplates\Web\\, jeweils in einem Unterordner mit dem das Web Programmiersprache.

## <a name="project-item-templates"></a>Projektelementvorlagen
 Website-Projektelementvorlagen werden verwendet, um das Hinzufügen neuer Web-Seiten zu einer Website als Reaktion auf die **vorhandenes Element hinzufügen** Befehl. Diese Arten von Webseiten werden derzeit unterstützt:

- Neue Klasse

- Neue HTML-Seite

- Neues Web Form

- Neue Masterseite

### <a name="new-class"></a>Neue Klasse
 Diese Vorlage erstellt eine neue Quelldatei, die als Reaktion auf eine leere Klasse definiert die **neue Klasse hinzufügen** Befehl.

- Klasse. *extension*

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

 Wählen Sie zum Erstellen einer abhängigen Codebehind-Quelldatei **Code in eigener Datei platzieren**. Andernfalls eine einzelne Webseite wird erstellt, die einen leeren Block ein Skript keinen und \<% Page % > Anweisungen für eine abhängige Datei einbinden.

 Wählen Sie zum Erstellen einer Inhaltsseite für eine ausgewählte Masterseite **Masterseite auswählen**.

- WebForm.aspx

     Der ab Inhalt der Webseite. Diese Webseite hat keine abhängigen zugeordneten Codebehind-Datei.

- WebForm_cb.aspx

     Der ab Inhalt der Webseite. Diese Webseite ist eine abhängige zugeordneten Codebehind-Datei.

- Codebehind. *extension*

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

- Codebehind.*extension*

     Die abhängige Datei, die die Masterseite-Klasse implementiert. Die Codebehind-Sprache bestimmt das *Erweiterung* dieser Datei.

- MasterPage.vstemplate

     Die Vorlagendatei, die bestimmt, den Inhalt der neuen Masterseite und die abhängige Datei, sofern vorhanden.

## <a name="see-also"></a>Siehe auch
- [Websiteunterstützung](../../extensibility/internals/web-site-support.md)