---
title: Befehlsdesign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aa58813623dc8150cafb4fbfee6496d09f889ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709658"
---
# <a name="command-design"></a>Befehlsentwurf
Wenn Sie einem VSPackage einen Befehl hinzufügen, müssen Sie angeben, wo es angezeigt werden soll, wann er verfügbar ist und wie er behandelt werden soll.

## <a name="define-commands"></a>Definieren von Befehlen
 Um neue Befehle zu definieren, fügen Sie eine Visual Studio-Befehlstabelle (*.vsct*) in Ihr VSPackage-Projekt ein. Wenn Sie ein VSPackage mithilfe der Visual Studio-Paketvorlage erstellt haben, enthält das Projekt eine dieser Dateien. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabellendateien (.vsct) .](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Visual Studio führt alle *gefundenen .vsct-Dateien* zusammen, sodass die Befehle angezeigt werden können. Da sich diese Dateien von der VSPackage-Binärdatei unterscheiden, muss Visual Studio das Paket nicht laden, um die Befehle zu finden. Weitere Informationen finden Sie unter Hinzufügen von [Benutzeroberflächenelementen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)durch VSPackages .

 Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> verwendet das Registrierungsattribut, um Menüressourcen und Befehle zu definieren. Weitere Informationen finden Sie unter [Befehlsimplementierung](../../extensibility/internals/command-implementation.md).

 Befehle können zur Laufzeit auf verschiedene Arten geändert werden. Sie können angezeigt oder ausgeblendet, aktiviert oder deaktiviert werden. Sie können unterschiedlichen Text oder Symbole anzeigen oder unterschiedliche Werte enthalten. Bevor Visual Studio Ihr VSPackage lädt, kann eine Vielzahl von Anpassungen durchgeführt werden. Weitere Informationen finden Sie unter Hinzufügen von [Benutzeroberflächenelementen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)durch VSPackages .

## <a name="command-handlers"></a>Befehlshandler
 Wenn Sie einen Befehl erstellen, müssen Sie einen Ereignishandler bereitstellen, um den Befehl auszuführen. Wenn der Benutzer den Befehl auswählt, muss er entsprechend weitergeleitet werden. Wenn Sie einen Befehl weiterleiten, bedeutet dies, ihn an das richtige VSPackage zu senden, um ihn zu aktivieren oder zu deaktivieren, auszublenden oder anzuzeigen und auszuführen, wenn der Benutzer dies auswählt. Weitere Informationen finden Sie unter [Befehlsroutingalgorithmus](../../extensibility/internals/command-routing-algorithm.md).

## <a name="visual-studio-command-environment"></a>Visual Studio-Befehlsumgebung
 Visual Studio kann eine beliebige Anzahl von VSPackages hosten, und jeder kann einen eigenen Befehlssatz beisteuern. In der Umgebung werden nur die Befehle angezeigt, die für die aktuelle Aufgabe geeignet sind. Weitere Informationen finden Sie unter [Befehlsverfügbarkeit](../../extensibility/internals/command-availability.md) und [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md).

 Ein VSPackage, das neue Befehle, Menüs, Symbolleisten oder Kontextmenüs definiert, stellt seine Befehlsinformationen zur Installationszeit über Registrierungseinträge bereit, die auf Ressourcen in systemeigenen oder verwalteten Assemblys verweisen. Jede Ressource verweist dann auf eine binäre Datenressource (*.cto*) Datei, die beim Kompilieren einer Visual Studio-Befehlstabelle (*.vsct*) erstellt wird. Dadurch kann Visual Studio zusammengeführte Befehlssätze, Menüs und Symbolleisten bereitstellen, ohne dass jedes installierte VSPackage geladen werden muss.

### <a name="command-organization"></a>Befehlsorganisation
 Die Umgebung positioniert Befehle nach Gruppe, Priorität und Menü.

- Gruppen sind logische Auflistungen verwandter Befehle, z. B. der **Befehlsgruppe Ausschneiden**, **Kopieren**und **Einfügen.** Gruppen sind die Befehle, die in Menüs angezeigt werden.

- Priorität bestimmt die Reihenfolge, in der einzelne Befehle in einer Gruppe im Menü angezeigt werden.

- Menüs dienen als Container für Gruppen.

  Die Umgebung definiert einige Befehle, Gruppen und Menüs vor. Weitere Informationen finden Sie unter [Standardbefehl, Gruppen- und Symbolleistenplatzierung](../../extensibility/internals/default-command-group-and-toolbar-placement.md).

  Ein Befehl kann einer primären Gruppe zugewiesen werden. Die primäre Gruppe steuert die Position des Befehls in der Hauptmenüstruktur und im Dialogfeld **Anpassen.** Ein Befehl kann in mehreren Gruppen angezeigt werden. Ein Befehl kann sich z. B. im Hauptmenü, in einem Kontextmenü und auf einer Symbolleiste befinden. Weitere Informationen finden Sie unter Hinzufügen von [Benutzeroberflächenelementen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)durch VSPackages .

### <a name="command-routing"></a>Befehlsrouting
 Der Prozess des Aufrufens und Routings von Befehlen für VSPackages unterscheidet sich vom Prozess des Aufrufens von Methoden für Objektinstanzen.

 Die Umgebung leitet Befehle sequenziell vom innersten (lokalen) Befehlskontext, der auf der aktuellen Auswahl basiert, an den äußersten (globalen) Kontext weiter. Der erste Kontext, der in der Lage ist, den Befehl auszuführen, ist der Kontext, der ihn verarbeitet. Weitere Informationen finden Sie unter [Befehlsroutingalgorithmus](../../extensibility/internals/command-routing-algorithm.md).

 In den meisten Fällen verarbeitet die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Umgebung Befehle mithilfe der Schnittstelle. Da das Befehlsroutingschema viele verschiedene <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Objekte zum Behandeln von Befehlen ermöglicht, kann eine beliebige Anzahl von Objekten implementiert werden. Dazu gehören Microsoft ActiveX-Steuerelemente, Fensteransichtsimplementierungen, Dokumentobjekte, Projekthierarchien und VSPackage-Objekte selbst (für globale Befehle). In einigen speziellen Fällen, z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> beim Routing von Befehlen in einer Hierarchie, muss die Schnittstelle implementiert werden.

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Befehlsimplementierung](../../extensibility/internals/command-implementation.md)|Beschreibt das Implementieren von Befehlen in einem VSPackage.|
|[Befehlsverfügbarkeit](../../extensibility/internals/command-availability.md)|Beschreibt, wie der Visual Studio-Kontext bestimmt, welche Befehle verfügbar sind.|
|[Befehlsroutingalgorithmus](../../extensibility/internals/command-routing-algorithm.md)|Beschreibt, wie die Visual Studio-Befehlsroutingarchitektur die Verarbeitung von Befehlen durch verschiedene VSPackages ermöglicht.|
|[Richtlinien für die Befehlsplatzierung](../../extensibility/internals/command-placement-guidelines.md)|Hier wird vorgeschlagen, wie Befehle in der Visual Studio-Umgebung positioniert werden.|
|[Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Beschreibt, wie VSPackages die Visual Studio-Befehlsarchitektur am besten nutzen kann.|
|[Standardbefehls-, Gruppen- und Symbolleistenplatzierung](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Beschreibt, wie VSPackages die in Visual Studio enthaltenen Befehle am besten verwenden kann.|
|[Verwalten von VSPackages](../../extensibility/managing-vspackages.md)|Beschreibt, wie Visual Studio VSPackages lädt.|
|[Visual Studio-Befehlstabellendateien (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Enthält Informationen zu XML-basierten *.vsct-Dateien,* die verwendet werden, um das Layout und die Darstellung von Befehlen in VSPackages zu beschreiben.|
