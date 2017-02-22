---
title: "Starten Visual Studio-Erweiterungen entwickeln | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Erste Schritte, Visual Studio-integration"
  - "Integration mit Visual Studio"
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Starten Visual Studio-Erweiterungen entwickeln
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie Visual Studio\-Erweiterung vor nie geschrieben haben, haben Sie wahrscheinlich einige Fragen. Wir haben einige der häufigsten Probleme aufgeführt. Wenn Sie die Informationen Sie suchen sehen, verwenden Sie die Feedback\-Schaltflächen \(**war diese Seite hilfreich?** am unteren Bildschirmrand\) stellen möchten.  
  
## Welche Software brauche ich Visual Studio\-Erweiterungen entwickeln?  
 Sie müssen Visual Studio 2015 SDK zusätzlich zu Visual Studio 2015 installieren, um Visual Studio\-Erweiterungen zu entwickeln.   Sie können Visual Studio 2015 SDK installieren, als Teil der normalen Installation oder später installieren. Weitere Informationen zum Installieren von Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Welche Arten von Elementen kann ich mit Visual Studio\-Erweiterungen?  
 Der Himmel einer das Limit, wenn es darum geht, so vor anderen Visual Studio\-Erweiterungen. Natürlich müssen die meisten etwas zu tun, mit dem Schreiben von Code, jedoch muss, die nicht der Fall sein. Hier sind einige Beispiele für die Arten von Erweiterungen, die Sie erstellen können:  
  
-   Unterstützung für Sprachen, die mit Farben für Syntax, IntelliSense und Unterstützung für Compiler und Debuggen in Visual Studio enthalten sind  
  
-   Produktivitätstools, die den Kern erweitern IDE Erfahrung im Umgang mit zusätzlichen Vorlagen, Code umgestaltet, neue Dialogfelder und Toolfenster  
  
-   Domänenspezifische Designern für Szenarios wie Daten Entwurfs\- oder Cloud\-Unterstützung  
  
 Beispiele für Erweiterungen, sehen Sie sich die [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/). Sie können auch sehen Sie sich [Visual Studio Open\-Source\-Erweiterungen](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).  
  
## Die Visual Studio\-Funktionen können werden erweitert?  
 Theoretisch kann nahezu jeden Teil von Visual Studio: Menüs, Symbolleisten, Befehle, Windows, Projektmappen, Projekte, Editoren und usw..  
  
 In der Praxis haben wir die Funktionen, die meisten Benutzer erweitern möchten, sind Befehle, Menüs und Symbolleisten, Windows, IntelliSense und Projekte gefunden. Hier sind Links zu den relevanten Abschnitten:  
  
-   [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md): Fügen Sie Ihre eigenen Artikel zu Visual Studio\-Menüs und Symbolleisten. Sie können um neue Visual Studio\-Funktionen oder eigene externe Hilfsprogramme zu starten. Sie können auch benutzerdefinierte Tastenkombinationen für den Menüelementen angeben.  
  
-   [Erweitern und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md): vorhandene Toolfenster zu erweitern oder eigene Toolfenster erstellen. Z. B. könnten Sie neue Eigenschaften zum Hinzufügen der **Eigenschaften**, oder erstellen Sie ein neues Toolfenster, um zusätzliche Funktionen hinzuzufügen.  
  
-   [\-Editor, und Language Service Extensions](../extensibility/editor-and-language-service-extensions.md): Fügen Sie Ihre eigenen Anpassungen IntelliSense für Visual Studio\-Sprachen bereitgestellt, oder erstellen Sie Unterstützung für neue Programmiersprachen. Sie können neue anweisungsvervollständigungen, Vorschläge und neue QuickInfos erstellen. Mit Glühbirnen Sie können die Umgestaltung Vorschläge hinzufügen und Code behoben, um neue Programmiersprachen zu unterstützen.  
  
-   [Erweitern von Projekten](../extensibility/extending-projects.md)  
  
-   [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)  
  
-   [Erweitern von Eigenschaften und das Eigenschaftenfenster](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio Shell Isolated](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a> Welche Projektvorlagen von VSSDK bereitgestellt werden?  
 Die beiden wichtigsten Arten von Erweiterungen sind VSPackages und MEF\-Erweiterungen. VSPackage\-Erweiterungen werden im Allgemeinen für Erweiterungen verwendet, die Befehle, Toolfenstern und Projekte zu erweitern oder verwenden. MEF\-Erweiterungen werden zum Erweitern oder Anpassen der Visual Studio\-Editor.  
  
 Für Visual c\# und Visual Basic\-Erweiterungen bietet VSSDK eine leere VSIX\-Projektvorlage, die Sie zusammen mit den neuen Vorlagen verwenden können, die Menübefehle, Toolfenstern und Editor\-Erweiterungen zu erstellen. Weitere Informationen finden Sie unter [Was ist neu in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md). Sie können diese Vorlage Paket Projektvorlagen, Codeausschnitte und andere Artefakte auch für die Verteilung an andere Benutzer verwenden.  
  
 Für C\+\+ bietet der VSPackage\-Assistent den Code zum Hinzufügen von Menübefehlen, Toolfenstern und benutzerdefinierte Editoren.  
  
 Die isolierte Shell\-Vorlage wird verwendet, eine Erweiterung in einer Version von Visual Studio\-Shell zu verpacken, die Sie an Ihre Marke und als eigene verteilen können. Die folgenden Themen zeigen Ihnen, wie mit jeder Art von Erweiterung beginnen:  
  
-   Befehle im Menü: [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Toolfenster: [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Editor\-Erweiterungen: [Erstellen eine Erweiterung mit einer Elementvorlage\-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   Grundlegende VSPackages: [Erstellen eine Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   VSIX\-Projektvorlage: [Erste Schritte mit der VSIX\-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio isolated Shell: [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## Wie erhalte ich meine Erweiterung von Visual Studio aussehen?  
 Hervorragende Tipps zum Entwerfen der Benutzeroberfläche für die Erweiterung im [Visual Studio\-Richtlinien für die Gestaltung der Benutzeroberfläche](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## Wo finde ich Beispiele für VSSDK Code?  
 Jede der im vorherigen Abschnitt aufgeführten Links haben schrittweise exemplarische Vorgehensweisen, die veranschaulichen bestimmte Features zu implementieren. Sie finden auch open\-Source VSSDK Beispiele auf GitHub unter [Visual Studio\-Beispiele](https://aka.ms/vs2015sdksamples).  
  
## Wie kann ich meiner Erweiterung verteilen?  
 Sie können die Erweiterung auf einem anderen Computer installieren oder an Ihre Freunde senden, als eine VSIX\-Datei, die Sie installieren, indem Sie darauf doppelklicken. Sie können weitere Informationen zu VSIX\-Pakete zur [Lieferung von Visual Studio\-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).  
  
 Sie können auch die Erweiterung in der Visual Studio Gallery veröffentlichen für eine große Anzahl von Visual Studio\-Kunden angezeigt werden. Ein Beispiel für eine Erweiterung für die Galerie Verpacken, finden Sie unter [Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio\-Erweiterungs](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Weitere Informationen, was Sie tun, um im Katalog veröffentlichen müssen, finden Sie unter [Produkte und Erweiterungen für Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).