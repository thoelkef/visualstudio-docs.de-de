---
title: Starten Visual Studio-Erweiterungen entwickeln | Microsoft Docs
ms.custom: 
ms.date: 09/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7bc03568465efa022981ade059b0de68019a5978
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Entwickeln von Visual Studio-Erweiterungen wird gestartet...
Wenn Sie eine Visual Studio-Erweiterung, bevor Sie nie geschrieben haben, haben Sie wahrscheinlich einige Fragen. Wir haben einige der häufigsten Probleme aufgeführt. Wenn Sie die Informationen Sie wünschen sehen, verwenden Sie die Feedback-Schaltflächen (**war diese Seite hilfreich?** am unteren Rand des Bildschirms) für die gewünschten um Unterstützung bitten.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Welche Software benötige ich zum Entwickeln von Visual Studio-Erweiterungen?  
 Sie müssen das Visual Studio SDK neben Visual Studio zu installieren, um Visual Studio-Erweiterungen entwickeln. Sie können das Visual Studio SDK installieren, im Rahmen des normalen Setup oder später installieren. Weitere Informationen zum Installieren von Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Welche Arten von Aufgaben kann ich mit Visual Studio-Erweiterungen tun?  
 Wenn es darum geht, so vor anderen Visual Studio-Erweiterungen in der die Sky den Grenzwert werden. Natürlich bei den meisten Erweiterungen haben Ihnen etwas mit Code zu schreiben, braucht jedoch, die die Groß-/Kleinschreibung. Hier sind einige Beispiele für die Arten von Erweiterungen, die Sie erstellen können:  
  
-   Unterstützung für Sprachen, die nicht mit Syntaxfarben, IntelliSense und den Compiler und Debug-Unterstützung in Visual Studio enthalten sind  
  
-   Produktivitätstools, die den Kern erweitern IDE-Erfahrung mit zusätzlichen Vorlagen, Code umgestaltet, neue Dialogfelder und Toolfenster  
  
-   Domänenspezifische-Designern für Szenarien wie die Daten Entwurfs- oder Cloud-Unterstützung  
  
 Beispiele für Erweiterungen, sehen Sie sich die [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Zahlreiche Erweiterungen sind open Source und Marketplace enthält Links zu ihren GitHub-Repository. 
  
## <a name="which-visual-studio-features-can-i-extend"></a>Welche Visual Studio-Funktionen können werden erweitert?  
 Theoretisch können Sie fast jeden Teil von Visual Studio erweitern: Menüs, Symbolleisten, Befehle, Windows, Projektmappen, Projekte, Editoren und usw.  
  
 In der Praxis gefunden wird, dass die Funktionen, die meisten Personen erweitern möchten Befehle, Menüs und Symbolleisten, Windows, IntelliSense und Projekte. Hier sind Links zu den relevanten Abschnitten:  
  
-   [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md): Visual Studio-Menüs und Symbolleisten eigene Elemente hinzugefügt. Sie können diese verwenden, um neue Funktionen von Visual Studio oder eine eigene externe Hilfsprogramme zu starten. Sie können auch benutzerdefinierte Tastenkombinationen für den Menüelementen bereitstellen.  
  
-   [Zum Erweitern von und Anpassen von Toolfenstern](../extensibility/extending-and-customizing-tool-windows.md): vorhandene Toolfenster erweitern oder eigene Toolfenster erstellen. Sie konnten z. B. neue Eigenschaften hinzufügen der **Eigenschaften**, oder Sie erstellen ein neue Toolfenster, um zusätzliche Funktionen hinzuzufügen.  
  
-   [Editor und Dienst Spracherweiterungen](../extensibility/editor-and-language-service-extensions.md): Fügen Sie eigene Anpassungen IntelliSense für Visual Studio-Sprachen bereitgestellt, oder erstellen Sie Unterstützung für neue Programmiersprachen. Sie können neue anweisungsvervollständigungen, Vorschläge und neue QuickInfos erstellen. Mit Glühbirnen können Sie die Umgestaltung Vorschläge hinzufügen und Code behoben, um neue Programmiersprachen zu unterstützen.  
  
-   [Erweitern von Projekten](../extensibility/extending-projects.md)  
  
-   [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)  
  
-   [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a>Welche Projektvorlagen von VSSDK bereitgestellt werden?  
 Die zwei Haupttypen von Erweiterungen sind VSPackages und MEF-Erweiterungen. Im Allgemeinen dienen VSPackage-Erweiterungen für Erweiterungen, die verwenden oder Erweitern von Befehlen, Toolfenster und Projekte. MEF-Erweiterungen dienen zum Erweitern oder Anpassen der Visual Studio-Editor.  
  
 Für Visual c# und Visual Basic-Erweiterungen bietet VSSDK eine leere VSIX-Projektvorlage, die Sie zusammen mit den neuen Vorlagen verwenden können, die Menübefehle, Toolfenster und editorerweiterungen erstellen. Sie können auch diese Vorlage zum Paket-Projektvorlage, Codeausschnitte und andere Artefakte für die Verteilung an andere Benutzer.  
  
 Bei C++ bietet der VSPackage-Assistent den Code, um Menübefehle, Toolfenster und benutzerdefinierte Editoren hinzufügen.  
  
 Die Isolated Shell-Vorlage wird verwendet, um eine Erweiterung in einer Version von Visual Studio-Shell zu verpacken, die Marke und als eigene verteilen können. Die folgenden Themen zeigen Ihnen, wie mit jeder Art von Erweiterung beginnen:  
  
-   Befehle im Menü: [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Toolfenster: [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Editorerweiterungen: [erstellen eine Erweiterung mit einer Elementvorlage-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   Grundlegende VSPackages: [erstellen eine Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   VSIX-Projektvorlage: [Einstieg in die VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio isolierte Shell: [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierten Shell-Anwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Wie erhalte ich meiner Erweiterung Visual Studio aussehen?  
 Erhalten Sie hilfreiche Tipps zum Entwerfen der Benutzeroberflächenautomatisierungs für die Erweiterung im [Visual Studio-Umgebung Leitfäden](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>Wo finde ich die Beispiele für VSSDK Code?  
 Da jedes der im vorherigen Abschnitt aufgeführten Links aufweisen schrittweise beschriebenen exemplarischen Vorgehensweisen, die zeigen, wie bestimmte Features implementiert werden. Sie erhalten auch open-Source VSSDK-Beispiele auf GitHub unter [Visual Studio-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  
  
## <a name="how-can-i-distribute-my-extension"></a>Wie kann ich meiner Erweiterung verteilen?  
 Sie können die Erweiterung auf einem anderen Computer installieren oder per für Ihre Freunde als eine VSIX-Datei, die Sie installieren, indem Sie darauf doppelklicken. Sie erhalten weitere Informationen zu VSIX-Pakete auf [Versand der Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).  
  
 Sie können auch die Erweiterung für Visual Studio Marketplace veröffentlichen, wodurch das für eine große Anzahl von Visual Studio-Kunden sichtbar. Ein Beispiel zum Verpacken einer Erweiterung Marketplace finden Sie unter [Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Weitere Informationen, welche Schritte Sie zum Veröffentlichen in Marketplace ausführen müssen, finden Sie unter [Produkte und -Erweiterungen für Visual Studio](/vsts/integrate/ide/extensions/overview).
