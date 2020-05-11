---
title: Befehle, Menüs und Symbolleisten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2be2f719d0f123328d5c518c08e30df2185e2a19
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709500"
---
# <a name="commands-menus-and-toolbars"></a>Befehle, Menüs und Symbolleisten
Menüs und Symbolleisten sind die Art und Weise, wie Benutzer auf Befehle in Ihrem VSPackage zugreifen. Befehle sind Funktionen, mit denen Aufgaben wie das Drucken eines Dokuments, das Aktualisieren einer Ansicht oder das Erstellen einer neuen Datei ausgeführt werden können. Menüs und Symbolleisten stellen eine praktische Methode für die grafische Darstellung von Befehlen für Benutzer dar. In der Regel sind verwandte Befehle zusammen im gleichen Menü oder auf derselben Symbolleiste gruppiert.

- Menüs werden in der Regel als aus einem Wort bestehende Zeichenfolgen in einer Zeile im oberen Bereich der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) oder oben in einem Toolfenster gruppiert angezeigt. Menüs können auch durch Klicken mit der rechten Maustaste angezeigt werden. In diesem Kontext werden sie als Kontextmenüs bezeichnet. Beim Klicken auf ein Menü wird das Menü erweitert, sodass mindestens ein Befehl angezeigt wird. Wenn Sie auf Befehle klicken, können Aufgaben ausgeführt oder Untermenüs, die zusätzliche Befehle enthaltenen, geöffnet werden. Einige bekannte Menünamen sind **Datei**, **Bearbeiten**, **Ansicht**und **Fenster**. Weitere Informationen finden Sie unter Erweitern von [Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

- Symbolleisten sind in der Regel Zeilen, in denen Schaltflächen und andere Steuerelemente wie Kombinationsfelder, Listenfelder, Textfelder und Menüsteuerelemente angezeigt werden. Allen Symbolleisten-Steuerelementen sind Befehle zugeordnet. Wenn Sie auf eine Symbolleistenschaltfläche klicken, wird der zugeordnete Befehl aktiviert. Symbolleistenschaltflächen weisen normalerweise Symbole auf, die die zugrunde liegenden Befehle veranschaulichen. Ein Beispiel hierfür ist ein Drucker für den Befehl "Drucken". Bei Dropdownlisten-Steuerelementen ist jedes Element in der Liste einem anderen Befehl zugeordnet. Ein Menüsteuerelement ist eine Mischform, bei der eine Seite des Steuerelements eine Symbolleistenschaltfläche und die andere Seite ein Dropdownpfeil ist. Wenn Sie auf den Dropdownpfeil klicken, werden zusätzliche Befehle angezeigt. Weitere Informationen finden Sie unter [Hinzufügen eines Menücontrollers zu einer Symbolleiste](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler für diesen Befehl erstellen. Der Ereignishandler bestimmt, wann der Befehl angezeigt oder aktiviert wird, ermöglicht Ihnen, den zugehörigen Text zu ändern, und stellt sicher, dass der Befehl entsprechend "reagiert", wenn er aktiviert wird. In den meisten Fällen verarbeitet die IDE Befehle mit der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>-Schnittstelle. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] werden Befehle hierarchisch weitergeleitet, beginnend mit dem innersten Befehlskontext, basierend auf der lokalen Auswahl, bis zum äußersten Kontext, basierend auf der globalen Auswahl. Befehle, die dem Hauptmenü hinzugefügt werden, sind sofort für die Skripterstellung verfügbar. Weitere Informationen finden Sie unter [MenuCommands im Vergleich zu OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015) und [Auswahlkontextobjekten](../../extensibility/internals/selection-context-objects.md).

  Um neue Menüs und Symbolleisten zu definieren, müssen Sie diese in einer Visual Studio-Befehlstabelle (*.vsct*) beschreiben. Die Visual Studio-Paketvorlage erstellt diese Datei für Sie zusammen mit den erforderlichen Elementen, um alle Befehle, Symbolleisten und Editoren zu unterstützen, die Sie in der Vorlage ausgewählt haben. Alternativ können Sie eine eigene *.vsct-Datei* schreiben, indem Sie das hier beschriebene XML-Schema verwenden: [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md).

  Weitere Informationen zum Arbeiten mit *.vsct-Dateien* finden Sie unter [Visual Studio-Befehlstabelle (.vsct)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

  In den Themen in diesem Abschnitt wird erläutert, wie Befehle, Menüs und Symbolleisten in VSPackages funktionieren.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Eine ausführliche Beschreibung der Spezifikation des Befehlstabellenformats.

- [Visual Studio-Befehlstabellendateien (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Beschreibt eine XML-basierte Syntax und einen Compiler für Befehlstabellen.

- [Standardbefehls-, Gruppen- und Symbolleistenplatzierung](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Beschreibt vordefinierte Befehle, Gruppen, Menüs und Symbolleisten.

- [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Gibt die vordefinierten Menüs, Befehle und Befehlsgruppen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] an, die für die Verwendung durch die IDE verfügbar sind.

- [Befehlsentwurf](../../extensibility/internals/command-design.md)

 Erläutert das Entwerfen von Befehlen.

- [Optimieren von Menü- und Symbolleistenbefehlen](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Gibt Richtlinien für Befehle an.

- [Befehle verfügbar machen](../../extensibility/internals/making-commands-available.md)

 Erläutert, wie Befehle für Visual Studio verfügbar sind.

- [Befehle und Menüs, die Interopassemblys verwenden](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Erläutert das Implementieren von Befehlen, die Interopassemblys verwenden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Erläutert das Befehlsrouting in VSPackages.
