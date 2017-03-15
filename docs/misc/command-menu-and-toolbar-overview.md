---
title: "&#220;bersicht &#252;ber Befehle, Men&#252;s und Symbolleisten | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Grundlegendes zu Menüs [Visual Studio SDK]"
  - "Grundlegendes zu Symbolleisten [Visual Studio SDK]"
ms.assetid: cbdaceaa-7dd3-4a56-aea6-b759e48d83d6
caps.latest.revision: 19
caps.handback.revision: 19
manager: "douge"
---
# &#220;bersicht &#252;ber Befehle, Men&#252;s und Symbolleisten
Über Menüs und Symbolleisten können Benutzer einfach und bequem auf die Befehle im VSPackage zugreifen. Befehle sind Funktionen, mit denen Aufgaben wie das Drucken eines Dokuments, das Aktualisieren einer Ansicht oder das Erstellen einer neuen Datei ausgeführt werden können. Menüs und Symbolleisten stellen eine praktische Methode für die grafische Darstellung von Befehlen für Benutzer dar. In der Regel sind verwandte Befehle zusammen im gleichen Menü oder auf derselben Symbolleiste gruppiert.  
  
-   Menüs werden in der Regel als aus einem Wort bestehende Zeichenfolgen in einer Zeile im oberen Bereich der integrierten Entwicklungsumgebung \(Integrated Development Environment, IDE\) oder oben in einem Toolfenster gruppiert angezeigt. Menüs können auch durch Klicken mit der rechten Maustaste angezeigt werden. In diesem Kontext werden sie als Kontextmenüs bezeichnet. Beim Klicken auf ein Menü wird das Menü erweitert, sodass mindestens ein Befehl angezeigt wird. Wenn Sie auf Befehle klicken, können Aufgaben ausgeführt oder Untermenüs, die zusätzliche Befehle enthaltenen, geöffnet werden. Einige bekannte Menünamen sind "Datei", "Bearbeiten", "Ansicht" und "Fenster". Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md).  
  
-   Symbolleisten sind in der Regel Zeilen, in denen Schaltflächen und andere Steuerelemente wie Kombinationsfelder, Listenfelder, Textfelder und Menüsteuerelemente angezeigt werden. Allen Symbolleisten\-Steuerelementen sind Befehle zugeordnet. Wenn Sie auf eine Symbolleistenschaltfläche klicken, wird der zugeordnete Befehl aktiviert. Symbolleistenschaltflächen weisen normalerweise Symbole auf, die die zugrunde liegenden Befehle veranschaulichen. Ein Beispiel hierfür ist ein Drucker für den Befehl "Drucken". Bei Dropdownlisten\-Steuerelementen ist jedes Element in der Liste einem anderen Befehl zugeordnet. Ein Menüsteuerelement ist eine Mischform, bei der eine Seite des Steuerelements eine Symbolleistenschaltfläche und die andere Seite ein Dropdownpfeil ist. Wenn Sie auf den Dropdownpfeil klicken, werden zusätzliche Befehle angezeigt. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Symbolleisten für Toolfenster](../misc/how-to-create-toolbars-for-tool-windows.md) und [Hinzufügen von Symbolen zu Menübefehlen](../extensibility/adding-icons-to-menu-commands.md).  
  
-   Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler für diesen Befehl erstellen. Der Ereignishandler bestimmt, wann der Befehl angezeigt oder aktiviert wird, ermöglicht Ihnen, den zugehörigen Text zu ändern, und stellt sicher, dass der Befehl entsprechend "reagiert", wenn er aktiviert wird. In den meisten Fällen verarbeitet die IDE Befehle mit der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\-Schnittstelle. In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] werden Befehle hierarchisch weitergeleitet, beginnend mit dem innersten Befehlskontext, basierend auf der lokalen Auswahl, bis zum äußersten Kontext, basierend auf der globalen Auswahl. Befehle, die dem Hauptmenü hinzugefügt werden, sind sofort für die Skripterstellung verfügbar. Weitere Informationen finden Sie unter [MenuCommand\- und OleMenuCommand\-Objekte](../misc/menucommands-vs-olemenucommands.md) und [Auswahl Kontextobjekte](../extensibility/internals/selection-context-objects.md).  
  
 Wenn Sie neue Menüs und Symbolleisten definieren möchten, müssen Sie diese in einer VSCT\-Datei \(Visual Studio Command Table\) beschreiben. Diese Datei wird von der Visual Studio\-Paketvorlage zusammen mit den erforderlichen Elementen zur Unterstützung der von Ihnen in der Vorlage ausgewählten Befehle, Symbolleisten und Editoren erstellt. Alternativ können Sie Ihre eigene VSCT\-Datei mithilfe des unter [VSCT XML\-Schemareferenz](../extensibility/vsct-xml-schema-reference.md) beschriebenen XML\-Schemas schreiben.  
  
 Weitere Informationen zum Arbeiten mit VSCT\-Dateien finden Sie unter [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md), oder lesen Sie [Exemplarische Vorgehensweisen für Elemente der Benutzeroberfläche](../misc/walkthroughs-for-user-interface-elements.md).  
  
 Eine detailliertere Übersicht über Menüs und Symbolleisten finden Sie unter [Befehl Design](../extensibility/internals/command-design.md).  
  
## Siehe auch  
 [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)   
 [VSPackages](../extensibility/internals/vspackages.md)