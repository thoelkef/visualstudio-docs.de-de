---
title: "Befehle, Men&#252;s und Symbolleisten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Menüs [Visual Studio SDK] Befehle"
  - "Befehle [Visual Studio]"
  - "Symbolleisten [Visual Studio] Befehle"
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 60
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 60
---
# Befehle, Men&#252;s und Symbolleisten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Menüs und Symbolleisten werden den Benutzern Zugriff auf die Befehle der VSPackage. Befehle sind Funktionen, die Aufgaben, z. B. ein Dokument zu drucken, eine Sicht aktualisieren oder Erstellen einer neuen Datei. Menüs und Symbolleisten stellen eine bequeme Methode grafisch auf Ihre Befehle Benutzern angezeigt werden. In der Regel sind verwandte Befehle zusammen im gleichen Menü oder Symbolleiste gruppiert.  
  
-   Menüs werden in der Regel als Wort Zeichenfolgen in einer Zeile am Anfang der integrierten Entwicklungsumgebung \(IDE\) oder ein Toolfenster gruppiert angezeigt. Menüs auch können als Ergebnis eines Ereignisses mit der rechten Maustaste angezeigt werden und werden als Kontextmenüs in diesem Kontext bezeichnet. Beim Klicken auf Erweitern Menüs, um eine oder mehrere Befehle anzuzeigen. Befehle, wenn geklickt haben, können Aufgaben ausführen oder starten Sie Untermenüs, die zusätzliche Befehle enthalten. Einige bekannte Menünamen werden Datei, bearbeiten, anzeigen und Fenster. Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
-   Symbolleisten sind in der Regel Zeilen von Schaltflächen und andere Steuerelemente, z. B. Kombinationsfelder, Listenfelder, Textfelder und Menücontroller. Es werden alle Steuerelemente der Symbolleiste Befehle zugeordnet. Wenn Sie eine Symbolleisten\-Schaltfläche klicken, wird der Befehl aktiviert. Symbolleisten\-Schaltflächen weisen normalerweise Symbole, die die zugrunde liegenden Befehle, wie z. B. einen Drucker, einen Druckbefehl vorgeschlagen. In einem Dropdown\-Listenfeld\-Steuerelement wird jedes Element in der Liste einen anderen Befehl zugeordnet. Ein Menü\-Controller ist eine Mischung aus, in dem eine Seite des Steuerelements eine Symbolleisten\-Schaltfläche und die andere Seite wird ein Pfeil nach unten, der zusätzliche Befehle, die beim Klicken auf angezeigt. Weitere Informationen finden Sie unter [Hinzufügen eines Controllers im Menü auf einer Symbolleiste](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler für ihn erstellen. Der Ereignishandler stellt fest, wenn der Befehl sichtbar oder aktiviert ist, ist, können Sie den Text zu ändern, und stellt sicher, dass der Befehl antwortet \("Routen"\), wenn aktiviert. In den meisten Fällen verarbeitet die IDE\-Befehle mit den <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Befehle im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Route hierarchisch der innersten Befehlskontext, basierend auf der lokalen Auswahl, bis der äußersten Kontexts angegeben, basierend auf der globalen Auswahl ab. Befehle, die dem Hauptmenü hinzugefügt, stehen sofort für Skripting. Weitere Informationen finden Sie unter [MenuCommand\- und OleMenuCommand\-Objekte](../../misc/menucommands-vs-olemenucommands.md) und [Auswahl Kontextobjekte](../../extensibility/internals/selection-context-objects.md).  
  
 Um neue Menüs und Symbolleisten zu definieren, müssen Sie sie in einer Visual Studio\-Befehl\-Tabelle \(VSCT\) Datei beschreiben. Der Visual Studio\-Paketvorlage erstellt diese Datei, sowie die erforderlichen Elemente zur Unterstützung, beliebige Befehle, Symbolleisten und Editoren, die Sie in der Vorlage ausgewählt. Alternativ Sie können Schreiben eigener VSCT\-Datei mit dem XML\-Schema hier: [VSCT XML\-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md).  
  
 Weitere Informationen zum Arbeiten mit VSCT\-Dateien finden Sie unter [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Die Themen in diesem Abschnitt wird erläutert, wie Befehle, Menüs und Symbolleisten in VSPackages funktionieren.  
  
## In diesem Abschnitt  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Eine detaillierte Beschreibung der Tabelle Befehlsformat\-Spezifikation.  
  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Beschreibt eine XML\-basierte Syntax und die Compiler für Befehlstabellen.  
  
 [Standardbefehl, Gruppen\- und Platzierung der Symbolleiste](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Beschreibt vordefinierten Befehle, Gruppen, Menüs und Symbolleisten.  
  
 [IDE\-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Gibt an, die vordefinierte Menüs, Befehle und Befehlsgruppen zur Verwendung durch die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Befehl Design](../../extensibility/internals/command-design.md)  
 Erläutert, wie Befehle zu entwerfen.  
  
 [Optimieren der Menü\- und Symbolleistenbefehle](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Enthält Richtlinien für Befehle.  
  
 [Befehle stellen zur Verfügung](../../extensibility/internals/making-commands-available.md)  
 Erläutert, wie Visual Studio Befehle zur Verfügung stellen.  
  
 [Befehle und Menüs, die mithilfe von Interop\-Assemblys](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Erläutert die Befehle zu implementieren, die Interop\-Assemblys verwenden.  
  
## Verwandte Abschnitte  
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Erläutert das Befehlsrouting in VSPackages.