---
title: Vorlagen für den Website-Support | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3c139ae6f2f9ec618e6382a1551a9e35eee7ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703454"
---
# <a name="web-site-support-templates"></a>Vorlagen für die Websiteunterstützung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Websiteprojekt- und Elementvorlagen stellen wiederverwendbare und anpassbare Websiteprojekt- und Elementstubs bereit, die den Entwicklungsprozess beschleunigen, da keine neuen Websiteprojekte und -elemente von Grund auf neu erstellt werden müssen. Weitere Informationen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zu Vorlagen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../../ide/creating-project-and-item-templates.md).

## <a name="project-template-folder"></a>Projektvorlagenordner
 Webprojektvorlagen werden in der Regel auf [*Visual Studio-Installationspfad*]\\, Common7-IDE-ProjectTemplates-Web , jeweils in einem Unterordner installiert, der nach der Webprogrammiersprache benannt ist.

## <a name="project-file"></a>Projektdatei
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) erfordert eine Projektdateierweiterung, um eine Vorlage dem richtigen Projekttyp zuzuordnen. Da Webprojekte keine Projektdatei haben, wird die Dummy-Projektdateierweiterung .webproj registriert, um die Vorlage dem Projekttyp zuzuordnen.

 Optional kann der Vorlage eine Sprachnamenszeichenfolge hinzugefügt werden, damit das Webprojektsystem den Sprachstandard im Dialogfeld **Neues Element hinzufügen** für Elemente festlegen kann, die auf der Vorlage basieren. Die Zeichenfolge muss die erste Zeile der Datei sein. Er muss sowohl mit dem Namen übereinstimmen, der in der IntelliSense-Modulregistrierung unter AddItemLanguageName registriert ist, als auch mit dem Namen, der unter Project Subtype(VsTemplate) registriert ist. Weitere Informationen finden Sie unter [Websitesupportattribute](../../extensibility/internals/web-site-support-attributes.md).

 Wenn die Zeichenfolge nicht vorhanden ist, versucht das Webprojektsystem, die Standardsprache basierend auf dem Language-Attribut und den Dateierweiterungen der Seiten zu ermitteln, die dem Webprojekt von der Projektvorlage hinzugefügt wurden.

## <a name="project-templates"></a>Projektvorlagen
 Websiteprojektvorlagen werden verwendet, um neue Websites als Reaktion auf den Befehl **Neue Website** im Menü **Datei** zu erstellen. Derzeit werden drei Websiteprojekttypen unterstützt:

- Leere Websiteprojekte

- Websiteprojekte

- Webdienstprojekte

### <a name="empty-web-site-projects"></a>Leere Websiteprojekte
 Diese Dateien erstellen eine neue leere Website als Antwort auf den Befehl **Leere Website,** der nach **Auswahl** > der Datei**neue Website**verfügbar ist:

- EmptyWeb.vstemplate

     Die Vorlagendatei, die die Erstellung der neuen leeren Website leitet.

- EmptyWeb.webproj

     Diese Datei ist ein Artefakt des Projektvorlagensystems. Es erfüllt den Projektdateiverweis in der Datei EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Websiteprojekte
 Diese Dateien erstellen eine neue Website als Reaktion auf den **ASP.NET Website-Befehl,** der nach Auswahl der Datei **File** > neue**Website**verfügbar ist:

- Default.aspx

     Die Standard-Startseite für die neue Website. Das Language-Attribut gibt die CodeBehind-Sprache an, und das CodeFile-Attribut gibt die abhängige Datei an, die den CodeBehind-Code enthält, der dieser Seite zugeordnet ist.

- Default.aspx. *Erweiterung*

     Die abhängige Datei, die den CodeBehind-Code für die Standard-Startseite enthält. Die CodeBehind-Sprache bestimmt die *Erweiterung* dieser Datei.

- web.config

     Die root web.site Konfigurationsdatei.

- WebApplication.vstemplate

     Die Vorlagendatei, die den Inhalt der Websitelösung bestimmt und die Erstellung des ordnerApp_Data-Ordners erzwingt.

- WebApplication.webproj

     Diese Datei ist ein Artefakt des Projektvorlagensystems. Es erfüllt den Projektdateiverweis in der Datei WebApplication.vstemplate.

### <a name="web-service-projects"></a>Webdienstprojekte
 Diese Dateien erstellen eine neue Website als Reaktion auf den **Befehl ASP.NET Web Dienst,** der nach **Auswahl** > der Datei**neue Website**verfügbar ist:

- Service.asmx

     Die HTML-Seite für den neuen Webdienst. Das Language-Attribut gibt die CodeBehind-Sprache an, und das CodeBehind-Attribut gibt die abhängige Datei an, die den CodeBehind-Code enthält, der diesem Dienst zugeordnet ist.

- Dienst: *Erweiterung*

     Die abhängige Datei, die die Dienstklasse implementiert. Die CodeBehind-Sprache bestimmt die *Erweiterung* dieser Datei.

- web.config

- Die root web.site Konfigurationsdatei.

- WebService.vstemplate

     Die Vorlagendatei, die den Inhalt der Websitelösung bestimmt und die Erstellung der App_Data und App_Code Ordnerererererererer erzwingt. Der Dienst. *Erweiterungsdatei* wird in den Ordner App_Code kopiert.

- WebService.webproj

     Diese Datei ist ein Artefakt des Projektvorlagensystems. Es erfüllt den Projektdateiverweis in der Datei WebService.vstemplate.

## <a name="project-item-template-folder"></a>Projektelementvorlagenordner
 Webprojektelementvorlagen werden in der Regel in [*Visual Studio-Installationspfad*] -\\Common7-IDE-ItemTemplates-Web , jeweils in einem Unterordner installiert, der nach seiner Webprogrammiersprache benannt ist.

## <a name="project-item-templates"></a>Projektelementvorlagen
 Websiteprojektelementvorlagen werden verwendet, um einer Website als Antwort auf den Befehl **Vorhandenes Element** hinzufügen neue Webseiten hinzuzufügen. Diese Arten von Webseiten werden derzeit unterstützt:

- Neue Klasse

- Neue HTML-Seite

- Neues Webformular

- Neue Masterseite

### <a name="new-class"></a>Neue Klasse
 Diese Vorlage erstellt eine neue Quelldatei, die eine leere Klasse als Antwort auf den Befehl **Neue Klasse hinzufügen** definiert.

- Klasse. *Erweiterung*

     Die Quelldatei, die die leere Klasse implementiert. Die CodeBehind-Sprache bestimmt die *Erweiterung* dieser Datei.

- Class.vstemplate

     Die Vorlagendatei, die die Quelldatei erstellt und deren Inhalt bestimmt.

### <a name="new-html-page"></a>Neue HTML-Seite
 Diese Vorlage erstellt eine neue Webseite als Antwort auf den Befehl **Neue HTML-Seite hinzufügen.**

- HTMLPage.htm

     Der Anfangsinhalt der Webseite. Diese Webseite hat in der Regel keine codeBehind-abhängige Datei zugeordnet. Um eine Smartpage mit einer zugeordneten CodeBehind-Datei zu erstellen, verwenden Sie stattdessen die Webformularvorlage.

- HTMLPage.vstemplate

     Die Vorlagendatei, die die Webseite erstellt und deren Inhalt bestimmt.

### <a name="new-webform"></a>Neues WebForm
 Diese Vorlage erstellt eine neue intelligente Webseite als Antwort auf den Befehl **Neues Formular hinzufügen.**

 Um eine abhängige CodeBehind-Quelldatei zu erstellen, wählen Sie **Code in einer separaten Datei**platzieren aus. Andernfalls wird eine einzelne Webseite mit einem leeren Skriptblock und keine \<% Seite %> Direktiven erstellt, um eine abhängige Datei zu verbinden.

 Um eine Inhaltsseite für eine ausgewählte Masterseite zu erstellen, wählen Sie **Masterseite auswählen**aus.

- WebForm.aspx

     Der Anfangsinhalt der Webseite. Dieser Webseite ist keine codeBehind-abhängige Datei zugeordnet.

- WebForm_cb.aspx

     Der Anfangsinhalt der Webseite. Diese Webseite verfügt über eine codeBehind-abhängige Datei.

- CodeBehind. *Erweiterung*

     Die abhängige Datei, die die Webformklasse implementiert. Die CodeBehind-Sprache bestimmt die *Erweiterung* dieser Datei.

- ContentPage.aspx

     Der Anfangsinhalt der Webseite als Inhaltsseite. Dieser Webseite ist keine codeBehind-abhängige Datei zugeordnet.

- ContentPage_cb.aspx

     Der Anfangsinhalt der Webseite als Inhaltsseite. Diese Webseite verfügt über eine codeBehind-abhängige Datei.

- WebForm.vstemplate

     Die Vorlagendatei, die den Inhalt der neuen Webseite und der abhängigen Datei bestimmt, falls vorhanden.

### <a name="new-master-page"></a>Neue Masterseite
 Diese Vorlage erstellt eine neue Masterseite als Antwort auf den Befehl **Neue Masterseite hinzufügen.**

 Um eine abhängige CodeBehind-Quelldatei zu erstellen, wählen Sie **Code in einer separaten Datei**platzieren aus. Andernfalls wird eine einzelne Webseite mit einem leeren \<Skriptblock und keinen % Page %>-Anweisungen zum Verbinden einer abhängigen Datei erstellt.

- MasterPage.master

     Der Anfangsinhalt der Masterseite. Dieser Masterseite ist keine codeBehind-abhängige Datei zugeordnet.

- MasterPage_cb.master

     Der Anfangsinhalt der Masterseite. Diese Masterseite verfügt über eine codeBehind-abhängige Datei.

- CodeBehind. *Erweiterung*

     Die abhängige Datei, die die Masterseitenklasse implementiert. Die CodeBehind-Sprache bestimmt die *Erweiterung* dieser Datei.

- MasterPage.vstemplate

     Die Vorlagendatei, die den Inhalt der neuen Masterseite und der abhängigen Datei bestimmt, falls vorhanden.

## <a name="see-also"></a>Weitere Informationen
- [Websiteunterstützung](../../extensibility/internals/web-site-support.md)
