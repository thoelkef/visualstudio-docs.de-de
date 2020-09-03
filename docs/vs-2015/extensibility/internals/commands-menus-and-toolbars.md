---
title: Befehle, Menüs und Symbolleisten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 61
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 337bc4de9171d2f98bf0be0068b298b7f600b979
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155835"
---
# <a name="commands-menus-and-toolbars"></a>Befehle, Menüs und Symbolleisten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mit Menüs und Symbolleisten können Benutzer auf Befehle in Ihrem VSPackage zugreifen. Befehle sind Funktionen, mit denen Aufgaben wie das Drucken eines Dokuments, das Aktualisieren einer Ansicht oder das Erstellen einer neuen Datei ausgeführt werden können. Menüs und Symbolleisten stellen eine praktische Methode für die grafische Darstellung von Befehlen für Benutzer dar. In der Regel sind verwandte Befehle zusammen im gleichen Menü oder auf derselben Symbolleiste gruppiert.  
  
- Menüs werden in der Regel als aus einem Wort bestehende Zeichenfolgen in einer Zeile im oberen Bereich der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) oder oben in einem Toolfenster gruppiert angezeigt. Menüs können auch durch Klicken mit der rechten Maustaste angezeigt werden. In diesem Kontext werden sie als Kontextmenüs bezeichnet. Beim Klicken auf ein Menü wird das Menü erweitert, sodass mindestens ein Befehl angezeigt wird. Wenn Sie auf Befehle klicken, können Aufgaben ausgeführt oder Untermenüs, die zusätzliche Befehle enthaltenen, geöffnet werden. Einige bekannte Menünamen sind "Datei", "Bearbeiten", "Ansicht" und "Fenster". Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
- Symbolleisten sind in der Regel Zeilen, in denen Schaltflächen und andere Steuerelemente wie Kombinationsfelder, Listenfelder, Textfelder und Menüsteuerelemente angezeigt werden. Allen Symbolleisten-Steuerelementen sind Befehle zugeordnet. Wenn Sie auf eine Symbolleistenschaltfläche klicken, wird der zugeordnete Befehl aktiviert. Symbolleistenschaltflächen weisen normalerweise Symbole auf, die die zugrunde liegenden Befehle veranschaulichen. Ein Beispiel hierfür ist ein Drucker für den Befehl "Drucken". Bei Dropdownlisten-Steuerelementen ist jedes Element in der Liste einem anderen Befehl zugeordnet. Ein Menüsteuerelement ist eine Mischform, bei der eine Seite des Steuerelements eine Symbolleistenschaltfläche und die andere Seite ein Dropdownpfeil ist. Wenn Sie auf den Dropdownpfeil klicken, werden zusätzliche Befehle angezeigt. Weitere Informationen finden Sie unter [Hinzufügen eines Menü Controllers zu einer Symbolleiste](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
- Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler für diesen Befehl erstellen. Der Ereignishandler bestimmt, wann der Befehl angezeigt oder aktiviert wird, ermöglicht Ihnen, den zugehörigen Text zu ändern, und stellt sicher, dass der Befehl entsprechend "reagiert", wenn er aktiviert wird. In den meisten Fällen verarbeitet die IDE Befehle mit der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>-Schnittstelle. In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] werden Befehle hierarchisch weitergeleitet, beginnend mit dem innersten Befehlskontext, basierend auf der lokalen Auswahl, bis zum äußersten Kontext, basierend auf der globalen Auswahl. Befehle, die dem Hauptmenü hinzugefügt werden, sind sofort für die Skripterstellung verfügbar. Weitere Informationen finden Sie unter [MenuCommands im Vergleich zu olemenucommands](../../misc/menucommands-vs-olemenucommands.md) und [Auswahl Kontext Objekten](../../extensibility/internals/selection-context-objects.md).  
  
  Wenn Sie neue Menüs und Symbolleisten definieren möchten, müssen Sie diese in einer VSCT-Datei (Visual Studio Command Table) beschreiben. Diese Datei wird von der Visual Studio-Paketvorlage zusammen mit den erforderlichen Elementen zur Unterstützung der von Ihnen in der Vorlage ausgewählten Befehle, Symbolleisten und Editoren erstellt. Alternativ können Sie Ihre eigene VSCT-Datei mithilfe des unter [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md)beschriebenen XML-Schemas schreiben.  
  
  Weitere Informationen zum Arbeiten mit vsct-Dateien finden Sie unter [Visual Studio Command Table (. Vsct-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
  In den Themen in diesem Abschnitt wird erläutert, wie Befehle, Menüs und Symbolleisten in VSPackages funktionieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Eine ausführliche Beschreibung der Befehls Tabellen-Format Spezifikation.  
  
 [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Beschreibt eine XML-basierte Syntax und einen Compiler für Befehls Tabellen.  
  
 [Standardplatzierung von Befehlen, Gruppen und Symbolleisten](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Beschreibt vordefinierte Befehle, Gruppen, Menüs und Symbolleisten.  
  
 [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Gibt die vordefinierten Menüs, Befehle und Befehls Gruppen an, die für die Verwendung durch die IDE verfügbar sind [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Befehlsentwurf](../../extensibility/internals/command-design.md)  
 Erläutert das Entwerfen von Befehlen.  
  
 [Optimieren von Menü- und Symbolleistenbefehlen](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Gibt Richtlinien für Befehle an.  
  
 [Verfügbarmachen von Befehlen](../../extensibility/internals/making-commands-available.md)  
 Erläutert, wie Sie Visual Studio Befehle zur Verfügung stellen können.  
  
 [Befehle und Menüs, die Interop-Assemblys verwenden](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Erläutert das Implementieren von Befehlen, die Interop-Assemblys verwenden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Erläutert das Befehls Routing in VSPackages.
