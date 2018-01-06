---
title: "Befehle, Menüs und Symbolleisten | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: "60"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa1513bcd61ac63fb9d2a59f69a8b2ce22cf5114
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="commands-menus-and-toolbars"></a>Befehle, Menüs und Symbolleisten
Menüs und Symbolleisten sind, dass Benutzer Befehle im VSPackage zugreifen. Befehle sind Funktionen, mit denen Aufgaben wie das Drucken eines Dokuments, das Aktualisieren einer Ansicht oder das Erstellen einer neuen Datei ausgeführt werden können. Menüs und Symbolleisten stellen eine praktische Methode für die grafische Darstellung von Befehlen für Benutzer dar. In der Regel sind verwandte Befehle zusammen im gleichen Menü oder auf derselben Symbolleiste gruppiert.  
  
-   Menüs werden in der Regel als aus einem Wort bestehende Zeichenfolgen in einer Zeile im oberen Bereich der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) oder oben in einem Toolfenster gruppiert angezeigt. Menüs können auch durch Klicken mit der rechten Maustaste angezeigt werden. In diesem Kontext werden sie als Kontextmenüs bezeichnet. Beim Klicken auf ein Menü wird das Menü erweitert, sodass mindestens ein Befehl angezeigt wird. Wenn Sie auf Befehle klicken, können Aufgaben ausgeführt oder Untermenüs, die zusätzliche Befehle enthaltenen, geöffnet werden. Einige bekannte Menünamen sind "Datei", "Bearbeiten", "Ansicht" und "Fenster". Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
-   Symbolleisten sind in der Regel Zeilen, in denen Schaltflächen und andere Steuerelemente wie Kombinationsfelder, Listenfelder, Textfelder und Menüsteuerelemente angezeigt werden. Allen Symbolleisten-Steuerelementen sind Befehle zugeordnet. Wenn Sie auf eine Symbolleistenschaltfläche klicken, wird der zugeordnete Befehl aktiviert. Symbolleistenschaltflächen weisen normalerweise Symbole auf, die die zugrunde liegenden Befehle veranschaulichen. Ein Beispiel hierfür ist ein Drucker für den Befehl "Drucken". Bei Dropdownlisten-Steuerelementen ist jedes Element in der Liste einem anderen Befehl zugeordnet. Ein Menüsteuerelement ist eine Mischform, bei der eine Seite des Steuerelements eine Symbolleistenschaltfläche und die andere Seite ein Dropdownpfeil ist. Wenn Sie auf den Dropdownpfeil klicken, werden zusätzliche Befehle angezeigt. Weitere Informationen finden Sie unter [einer Symbolleiste ein Menücontroller hinzugefügt](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler für diesen Befehl erstellen. Der Ereignishandler bestimmt, wann der Befehl angezeigt oder aktiviert wird, ermöglicht Ihnen, den zugehörigen Text zu ändern, und stellt sicher, dass der Befehl entsprechend "reagiert", wenn er aktiviert wird. In den meisten Fällen verarbeitet die IDE Befehle mit der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Befehle in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Route hierarchisch, beginnend mit dem innersten Befehlskontext, basierend auf der lokalen Auswahl, und es wird bis zum äußersten Kontext, basierend auf der globalen Auswahl. Befehle, die dem Hauptmenü hinzugefügt werden, sind sofort für die Skripterstellung verfügbar. Weitere Informationen finden Sie unter [MenuCommand-und. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md) und [Auswahl Kontextobjekte](../../extensibility/internals/selection-context-objects.md).  
  
 Wenn Sie neue Menüs und Symbolleisten definieren möchten, müssen Sie diese in einer VSCT-Datei (Visual Studio Command Table) beschreiben. Diese Datei wird von der Visual Studio-Paketvorlage zusammen mit den erforderlichen Elementen zur Unterstützung der von Ihnen in der Vorlage ausgewählten Befehle, Symbolleisten und Editoren erstellt. Alternativ Sie können schreiben eigene VSCT-Datei mit den hier beschriebenen Xml-Schema: [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md).  
  
 Weitere Informationen zum Arbeiten mit VSCT-Dateien finden Sie unter [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Die Themen in diesem Abschnitt erläutern die Funktionsweise von Befehlen, Menüs und Symbolleisten in VSPackages.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Eine ausführliche Beschreibung der Tabelle Befehlsformat-Spezifikation.  
  
 [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Beschreibt eine XML-basierte Syntax und -Compiler für Befehlstabellen.  
  
 [Standardplatzierung von Befehlen, Gruppen und Symbolleisten](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Beschreibt, vordefinierten Befehle, Gruppen, Menüs und Symbolleisten.  
  
 [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Gibt an, die vordefinierte Menüs, Befehle und Befehlsgruppen verfügbar für die Verwendung durch die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Befehlsentwurf](../../extensibility/internals/command-design.md)  
 Erläutert, wie Befehle zu entwerfen.  
  
 [Optimieren von Menü- und Symbolleistenbefehlen](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Bietet Richtlinien für Befehle.  
  
 [Verfügbarmachen von Befehlen](../../extensibility/internals/making-commands-available.md)  
 Erläutert, wie Visual Studio Befehle zur Verfügung stellen.  
  
 [Befehle und Menüs, die Interop-Assemblys verwenden](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Erläutert, wie Befehle implementiert, die Interop-Assemblys verwenden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Erläutert das Befehlsrouting in VSPackages.