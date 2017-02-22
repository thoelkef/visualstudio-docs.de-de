---
title: "Unterst&#252;tzung f&#252;r Websitevorlagen | Microsoft Docs"
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
  - "Wir Websiteprojekte, Vorlagen"
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Unterst&#252;tzung f&#252;r Websitevorlagen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Websiteprojekt und Elementvorlagen enthalten wiederverwendbare und anpassbare Website projekt\- und \- Element stubs, die den Entwicklungsprozess beschleunigen, indem sie die Anforderung entfernen, neue Websiteprojekte und \- Elemente von Grund auf neu zu erstellen.  Weitere Informationen zu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Vorlagen finden Sie unter [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../../ide/creating-project-and-item-templates.md).  
  
## Projektvorlagen\-Ordner  
 Webprojekt Vorlage Vorlagen in der Regel auf installiert sind*Visual Studio\-Installations\-Pfad*\[\] \\ Common7 \\ IDE \\ ProjectTemplates \\ Web \\, die jeweils in einem Unterordner, der nach der Internet\-Programmiersprache benannt ist.  
  
## Projektdatei  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung \(IDE\) erfordert eine Projektdatei Namespaceerweiterung, um eine Vorlage an den entsprechenden Projekttyp zuzuordnen.  Da Webprojekte keine Projektdatei angegeben haben, wird die Erweiterung .webproj blinde Projektdatei registriert, um dies zu unterstützen.  
  
 Optional kann eine Zeichenfolge der Sprachennamen der Vorlage hinzugefügt werden, um das Webprojekt System zu aktivieren, um den Sprachen standardmäßig im **Neues Element hinzufügen** Dialogfeld für Elemente auf Grundlage festzulegen.  Die Zeichenfolge muss die erste Zeile der Datei sein und muss den Namen, der mit AddItemLanguageName IntelliSense\-Modul in der Registrierung registriert sein und mit dem Namen übereinstimmen, der unter Projekt\-Untertyp \(VsTemplate\) registriert ist.  Weitere Informationen finden Sie unter [Website\-Support\-Attribute](../../extensibility/internals/web-site-support-attributes.md).  
  
 Wenn die Zeichenfolge nicht vorhanden ist, versucht das Webprojekt, die Standardsprache auf das Sprachattribut sowie die Dateierweiterungen der Seiten zu bestimmen, die dem Webprojekt über die Projektvorlagen\-Vorlage hinzugefügt werden.  
  
## Projektvorlagen  
 Website projektvorlagen werden verwendet, um neue Websites als Reaktion auf den **Neue Website** Befehl für das **Datei** Menü zu erstellen.  Drei Website Projekttypen werden aktuell unterstützt:  
  
-   Leere Websiteprojekte  
  
-   Websiteprojekte  
  
-   Webdienst von Projekten  
  
### Leeren von Websiteprojekten  
 Diese Dateien geben eine neue leere Website als Reaktion auf den **Leere Website** Befehl, der verfügbar ist, nachdem es auf **Neue Website** im Menü **Datei** selbst dargestellt:  
  
-   EmptyWeb.vstemplate  
  
     Die Vorlagendatei, die die Erstellung der neuen leeren Site führt.  
  
-   EmptyWeb.webproj  
  
     Diese Datei ist ein Artefakt von Projektvorlagen systems.  Es stellt den Verweis in der Projektdatei EmptyWeb.vstemplate\-Datei erfüllt.  
  
### Websiteprojekten  
 Diese Dateien geben eine neue Website als Reaktion auf den **ASP.NET\-Website** Befehl, der verfügbar ist, nachdem es auf **Neue Website** im Menü **Datei** selbst dargestellt:  
  
-   Default.aspx  
  
     Die Homepage für die neue Website.  Das Sprachattribut gibt die codebehind Sprache angezeigt, und das CodeFile\-Attribut gibt die abhängige Datei an, die den codebehind Code enthält, der dieser Seite zugeordnet ist.  
  
-   Default.aspx.*Erweiterung*  
  
     Die abhängige Datei, die den codebehind Code für die Standardhomepage enthält.  Die codebehind Sprache bestimmt *Erweiterung* dieser Datei.  
  
-   web.config  
  
     Die Konfigurationsdatei des Stamms web.site.  
  
-   WebApplication.vstemplate  
  
     Die Vorlagendatei, die den Inhalt der Projektmappe Website und die Erstellung des App\_Data\-Ordners erzwingt.  
  
-   WebApplication.webproj  
  
     Diese Datei ist ein Artefakt von Projektvorlagen systems.  Es stellt den Verweis in der Projektdatei WebApplication.vstemplate\-Datei erfüllt.  
  
### Webdienst\-Projekte  
 Diese Dateien geben eine neue Website als Reaktion auf den **ASP.NET\-Webdienst** Befehl, der verfügbar ist, nachdem es auf **Neue Website** im Menü **Datei** selbst dargestellt:  
  
-   Service.asmx  
  
     Die HTML\-Seite für den neuen Webdienst.  Das Sprachattribut gibt die codebehind Sprache angezeigt, und das CodeBehind\-Attribut gibt die abhängige Datei an, die den codebehind Code enthält, der diesen Dienst zugeordnet sind.  
  
-   Dienst. *Erweiterung*  
  
     Die abhängige Datei, in der die Dienstklasse implementiert.  Die codebehind Sprache bestimmt *Erweiterung* dieser Datei.  
  
-   web.config  
  
-   Die Konfigurationsdatei des Stamms web.site.  
  
-   WebService.vstemplate  
  
     Die Vorlagendatei, die den Inhalt der Website ermittelt und die Erstellung der Projektmappe mit der rechten Maustaste auf den Ordner App\_Data, und App\_Code erzwingt.  Der Dienst.*Erweiterung* Datei wird dem Ordner App\_Code kopiert.  
  
-   WebService.webproj  
  
     Diese Datei ist ein Artefakt von Projektvorlagen systems.  Sie stellt den Verweis in der Projektdatei WebService.vstemplate\-Datei erfüllt.  
  
## Projektelement\-Vorlagen\-Ordner  
 Internet Projektelement Vorlage Vorlagen in der Regel auf installiert sind*Visual Studio\-Installations\-Pfad*\[\] \\ Common7 \\ IDE \\ ItemTemplates \\ Web \\, die jeweils in einem Unterordner nach seiner Internet\-Programmiersprache benannt ist.  
  
## Projektelementvorlagen  
 Projektelement Website Vorlagen werden verwendet, um neue Webseiten einer Website als Reaktion auf den **Vorhandenes Element hinzufügen** Befehl hinzuzufügen.  Diese Art von Webseiten werden aktuell unterstützt:  
  
-   Die neue Klasse  
  
-   Die neue HTML\-Seite  
  
-   Neue Web Form  
  
-   Die neue Masterseite  
  
### Die neue Klasse  
 Diese Vorlage erstellt eine neue Quelldatei, die eine leere Klasse als Reaktion auf den **Neue Klasse hinzufügen** Befehl definiert.  
  
-   \- Klasse. *Erweiterung*  
  
     Die Quelldatei, die die leere Klasse implementiert.  Die codebehind Sprache bestimmt *Erweiterung* dieser Datei.  
  
-   Class.vstemplate  
  
     Die Vorlagendatei, die die Quelldatei erstellt und dessen Inhalt bestimmt.  
  
### Die neue HTML\-Seite  
 Diese Vorlage erstellt eine neue Webseite als Reaktion auf den **Neue HTML\-Seite hinzufügen** Befehl.  
  
-   HTMLPage.htm  
  
     Der Inhalt der Webseite starten.  Diese Webseite enthält i. d. R. keine zugeordnete Datei codebehind abhängigen Elements.  Um eine intelligente Seite mit einer zugeordneten codebehind Datei zu erstellen, verwenden Sie die Vorlage Webformular.  
  
-   HTMLPage.vstemplate  
  
     Die Vorlagendatei, die die Webseite erstellt und dessen Inhalt bestimmt.  
  
### Eine neue WebForm  
 Diese Vorlage erstellt eine neue intelligente Webseite als Reaktion auf den **Neues Web Form hinzufügen** Befehl.  
  
 So erstellen Sie eine abhängige codebehind Quelldatei erstellen, wählen Sie **\_Code in gesonderter Datei ablegen**.  Andernfalls wird eine einzelne Webseite erstellt, die einen leeren Skripterstellungs Datenbindungsausdrücken und keine Direktiven \<% Seite %\> zum Einbinden eine abhängige Datei besitzt.  
  
 So erstellen Sie eine Inhaltsseite für eine ausgewählte Masterseite erstellen, wählen Sie **Gestaltungsvorlage auswählen**.  
  
-   WebForm.aspx  
  
     Der Inhalt der Webseite starten.  Diese Webseite enthält keine zugeordnete Datei codebehind abhängigen Elements.  
  
-   WebForm\_cb.aspx  
  
     Der Inhalt der Webseite starten.  Diese Webseite verfügt über eine zugeordnete Datei codebehind abhängigen Elements.  
  
-   Codebehind. *Erweiterung*  
  
     Die abhängige Datei, die die webform Klasse implementiert.  Die codebehind Sprache bestimmt *Erweiterung* dieser Datei.  
  
-   ContentPage.aspx  
  
     Der Inhalt der Webseite als Inhaltsseite starten.  Diese Webseite enthält keine zugeordnete Datei codebehind abhängigen Elements.  
  
-   ContentPage\_cb.aspx  
  
     Der Inhalt der Webseite als Inhaltsseite starten.  Diese Webseite verfügt über eine zugeordnete Datei codebehind abhängigen Elements.  
  
-   WebForm.vstemplate  
  
     Die Vorlagendatei, die den Inhalt der neuen Webseite und ihrer abhängigen Datei bestimmt, sofern vorhanden.  
  
### Die neue Masterseite  
 Diese Vorlage erstellt eine neue Masterseite als Reaktion auf den **Neue Gestaltungsvorlage hinzufügen** Befehl.  
  
 So erstellen Sie eine abhängige codebehind Quelldatei erstellen, wählen Sie **\_Code in gesonderter Datei ablegen**.  Andernfalls wird eine einzelne Webseite erstellt, die einen leeren Skripterstellungs Datenbindungsausdrücken und keine Direktiven \<% Seite %\> zum Einbinden eine abhängige Datei besitzt.  
  
-   MasterPage.master  
  
     Der Inhalt der Masterseite starten.  Diese Masterseite verfügt über keine zugeordneten Datei codebehind abhängigen Elements.  
  
-   MasterPage\_cb.master  
  
     Der Inhalt der Masterseite starten.  Diese Masterseite verfügt über eine zugeordnete Datei codebehind abhängigen Elements.  
  
-   Codebehind.*Erweiterung*  
  
     Die abhängige Datei, die die Masterseiten \- Klasse implementiert.  Die codebehind Sprache bestimmt *Erweiterung* dieser Datei.  
  
-   MasterPage.vstemplate  
  
     Die Vorlagendatei, die den Inhalt der neuen Masterseite und ihrer abhängigen Datei bestimmt, sofern vorhanden.  
  
## Siehe auch  
 [Der Support\-Website](../../extensibility/internals/web-site-support.md)