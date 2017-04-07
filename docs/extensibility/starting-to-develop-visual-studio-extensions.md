---
title: Starten Visual Studio-Erweiterungen entwickeln | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 29
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: dc5416fe979ed3e52ef2df77e5b495cb98038dcd
ms.lasthandoff: 03/07/2017

---
# <a name="starting-to-develop-visual-studio-extensions"></a>Starten Visual Studio-Erweiterungen entwickeln
Wenn Sie Visual Studio-Erweiterung vor nie geschrieben haben, haben Sie wahrscheinlich einige Fragen. Wir haben einige der häufigsten Probleme aufgeführt. Wenn Sie die Informationen Sie suchen sehen, verwenden Sie die Feedback-Schaltflächen (**war diese Seite hilfreich?** am unteren Bildschirmrand) stellen möchten.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Welche Software brauche ich Visual Studio-Erweiterungen entwickeln?  
 Sie müssen Visual Studio SDK zusätzlich zu Visual Studio installieren, um Visual Studio-Erweiterungen zu entwickeln. Sie können das Visual Studio SDK installieren, als Teil der normalen Installation oder später installieren. Weitere Informationen zum Installieren von Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Welche Arten von Elementen kann ich mit Visual Studio-Erweiterungen?  
 Der Himmel einer das Limit, wenn es darum geht, so vor anderen Visual Studio-Erweiterungen. Natürlich müssen die meisten etwas zu tun, mit dem Schreiben von Code, jedoch muss, die nicht der Fall sein. Hier sind einige Beispiele für die Arten von Erweiterungen, die Sie erstellen können:  
  
-   Unterstützung für Sprachen, die mit Farben für Syntax, IntelliSense und Unterstützung für Compiler und Debuggen in Visual Studio enthalten sind  
  
-   Produktivitätstools, die den Kern erweitern IDE Erfahrung im Umgang mit zusätzlichen Vorlagen, Code umgestaltet, neue Dialogfelder und Toolfenster  
  
-   Domänenspezifische Designern für Szenarios wie Daten Entwurfs- oder Cloud-Unterstützung  
  
 Beispiele für Erweiterungen, sehen Sie sich die [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/). Sie können auch sehen Sie sich [Visual Studio Open-Source-Erweiterungen](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).  
  
## <a name="which-visual-studio-features-can-i-extend"></a>Die Visual Studio-Funktionen können werden erweitert?  
 Theoretisch kann nahezu jeden Teil von Visual Studio: Menüs, Symbolleisten, Befehle, Windows, Projektmappen, Projekte, Editoren und usw..  
  
 In der Praxis haben wir die Funktionen, die meisten Benutzer erweitern möchten, sind Befehle, Menüs und Symbolleisten, Windows, IntelliSense und Projekte gefunden. Hier sind Links zu den relevanten Abschnitten:  
  
-   [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md): Fügen Sie Ihre eigenen Artikel zu Visual Studio-Menüs und Symbolleisten. Sie können um neue Visual Studio-Funktionen oder eigene externe Hilfsprogramme zu starten. Sie können auch benutzerdefinierte Tastenkombinationen für den Menüelementen angeben.  
  
-   [Zum Erweitern von und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md): vorhandene Toolfenster zu erweitern oder eigene Toolfenster erstellen. Z. B. könnten Sie neue Eigenschaften zum Hinzufügen der **Eigenschaften**, oder erstellen Sie ein neues Toolfenster, um zusätzliche Funktionen hinzuzufügen.  
  
-   [-Editor, und Language Service Extensions](../extensibility/editor-and-language-service-extensions.md): Fügen Sie Ihre eigenen Anpassungen IntelliSense für Visual Studio-Sprachen bereitgestellt, oder erstellen Sie Unterstützung für neue Programmiersprachen. Sie können neue anweisungsvervollständigungen, Vorschläge und neue QuickInfos erstellen. Mit Glühbirnen Sie können die Umgestaltung Vorschläge hinzufügen und Code behoben, um neue Programmiersprachen zu unterstützen.  
  
-   [Erweitern von Projekten](../extensibility/extending-projects.md)  
  
-   [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)  
  
-   [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a>Welche Projektvorlagen von VSSDK bereitgestellt werden?  
 Die beiden wichtigsten Arten von Erweiterungen sind VSPackages und MEF-Erweiterungen. VSPackage-Erweiterungen werden im Allgemeinen für Erweiterungen verwendet, die Befehle, Toolfenstern und Projekte zu erweitern oder verwenden. MEF-Erweiterungen werden zum Erweitern oder Anpassen der Visual Studio-Editor.  
  
 Für Visual c# und Visual Basic-Erweiterungen bietet VSSDK eine leere VSIX-Projektvorlage, die Sie zusammen mit den neuen Vorlagen verwenden können, die Menübefehle, Toolfenstern und Editor-Erweiterungen zu erstellen. Sie können diese Vorlage Paket Projektvorlagen, Codeausschnitte und andere Artefakte auch für die Verteilung an andere Benutzer verwenden.  
  
 Für C++ bietet der VSPackage-Assistent den Code zum Hinzufügen von Menübefehlen, Toolfenstern und benutzerdefinierte Editoren.  
  
 Die isolierte Shell-Vorlage wird verwendet, eine Erweiterung in einer Version von Visual Studio-Shell zu verpacken, die Sie an Ihre Marke und als eigene verteilen können. Die folgenden Themen zeigen Ihnen, wie mit jeder Art von Erweiterung beginnen:  
  
-   Menübefehle: [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Toolfenster: [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Editor-Erweiterungen: [erstellen eine Erweiterung mit einer Elementvorlage-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   Grundlegende VSPackages: [erstellen eine Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   VSIX-Projektvorlage: [Einstieg in die VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio isolated Shell: [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung für isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Wie erhalte ich meine Erweiterung von Visual Studio aussehen?  
 Hervorragende Tipps zum Entwerfen der Benutzeroberfläche für die Erweiterung im [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>Wo finde ich Beispiele für VSSDK Code?  
 Jede der im vorherigen Abschnitt aufgeführten Links haben schrittweise exemplarische Vorgehensweisen, die veranschaulichen bestimmte Features zu implementieren. Sie finden auch open-Source VSSDK Beispiele auf GitHub unter [Visual Studio-Beispiele](https://aka.ms/vs2015sdksamples).  
  
## <a name="how-can-i-distribute-my-extension"></a>Wie kann ich meiner Erweiterung verteilen?  
 Sie können die Erweiterung auf einem anderen Computer installieren oder an Ihre Freunde senden, als eine VSIX-Datei, die Sie installieren, indem Sie darauf doppelklicken. Sie können weitere Informationen zu VSIX-Pakete auf [Versand der Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).  
  
 Sie können auch die Erweiterung in der Visual Studio Gallery veröffentlichen für eine große Anzahl von Visual Studio-Kunden angezeigt werden. Ein Beispiel für eine Erweiterung für die Galerie Verpacken, finden Sie unter [Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Weitere Informationen, was Sie tun, um im Katalog veröffentlichen müssen, finden Sie unter [Produkte und Erweiterungen für Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).
