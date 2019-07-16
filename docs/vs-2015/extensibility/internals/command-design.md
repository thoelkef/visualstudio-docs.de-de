---
title: Befehl Entwurf | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6e9eaf69be62b38a880b07fd8eb51cfc9c256a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195077"
---
# <a name="command-design"></a>Befehlsentwurf
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie einen Befehl für ein VSPackage hinzufügen, müssen Sie angeben, in dem es angezeigt werden, wenn es verfügbar ist, und wie sie behandelt werden.  
  
## <a name="defining-commands"></a>Definieren von Befehlen  
 Um neue Befehle definieren, müssen schließen Sie eine Visual Studio Command Table (.vsct)-Datei in Ihrem VSPackage-Projekt ein. Wenn Sie eine VSPackage mit der Visual Studio-Paketvorlage erstellt haben, enthält das Projekt eine dieser Dateien. Weitere Informationen finden Sie unter [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio führt die VSCT-Dateien, die sie findet, damit die Befehle angezeigt werden können. Da diese Dateien aus dem VSPackage binäre unterscheiden, ist Visual Studio keine beim Laden des Pakets, um die Befehle zu suchen. Weitere Informationen finden Sie unter [wie VSPackages hinzufügen Benutzeroberflächenelemente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio verwendet die <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Registrierungsattribut Menüressourcen und Befehle zu definieren. Weitere Informationen finden Sie unter [Implementierung](../../extensibility/internals/command-implementation.md).  
  
 Befehle können in einer Reihe von Möglichkeiten zur Laufzeit geändert werden. Sie können angezeigt oder ausgeblendet, aktiviert oder deaktiviert werden. Sie können verschiedene Text oder Symbolen, oder Sie können verschiedene Werte enthalten. Bevor Visual Studio das VSPackage lädt, kann eine umfangreiche Anpassung ausgeführt werden. Weitere Informationen finden Sie unter [wie VSPackages hinzufügen Benutzeroberflächenelemente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Befehlshandler  
 Wenn Sie einen Befehl erstellen, müssen Sie einen Ereignishandler zum Ausführen des Befehls angeben. Wenn der Benutzer den Befehl auswählt, muss dieser entsprechend weitergeleitet werden. Routing von einem Befehl bedeutet das Senden an das richtige VSPackage zu aktivieren oder deaktivieren, ausblenden oder anzeigen und führen Sie es, wenn der Benutzer dazu. Weitere Informationen finden Sie unter [Routing Algorithmus](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Visual Studio-Befehl-Umgebung  
 Visual Studio kann eine beliebige Anzahl von VSPackages hosten und kann jeweils einen eigenen Befehlssatz beitragen. Die Umgebung zeigt nur die Befehle, die für den aktuellen Task geeignet sind. Weitere Informationen finden Sie unter [Verfügbarkeit](../../extensibility/internals/command-availability.md) und [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md).  
  
 Eine VSPackage, die definiert, neue Befehle, Menüs, Symbolleisten oder Kontextmenüs bietet die Befehlsinformationen in Visual Studio bei der Installation über die Registrierungseinträge, die Ressourcen in systemeigenen oder verwalteten Assemblys verweisen. Jede Ressource verweist dann auf eine binäre Daten (CTO) Ressourcendatei, die erstellt wird, wenn Sie eine Visual Studio Command Table (.vsct)-Datei kompilieren. Dadurch wird Visual Studio, um die zusammengeführte Befehle, Menüs und Symbolleisten bereitstellen, ohne dass alle installierten VSPackage zu laden.  
  
### <a name="command-organization"></a>Befehls-Organisation  
 Die Umgebung positioniert Befehle nach Gruppe, Priorität und im Menü.  
  
- Gruppen sind logische Sammlungen von verwandten Befehlen, z. B. die **Ausschneiden**, **Kopie**, und **einfügen** Befehlsgruppe. Gruppen sind die Befehle, die in Menüs angezeigt werden.  
  
- Priorität bestimmt die Reihenfolge, in der einzelnen Befehle in einer Gruppe im Menü angezeigt werden.  
  
- Menüs dienen als Container für Gruppen.  
  
  Die Umgebung sind einige Befehle, Gruppen und Menüs vordefiniert. Weitere Informationen finden Sie unter [Standard-Befehl, Gruppe und Symbolleiste Platzierung](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Ein Befehl kann auf eine primäre Gruppe zugewiesen werden. Die primäre Gruppe steuert die Position des Befehls in der Struktur im Hauptmenü und in der **anpassen** Dialogfeld. Ein Befehl kann in mehrere Gruppen angezeigt werden; Beispielsweise kann ein Befehl im Hauptmenü auf ein Kontextmenü aufrufen und auf einer Symbolleiste sein. Weitere Informationen finden Sie unter [wie VSPackages hinzufügen Benutzeroberflächenelemente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Befehlsrouting  
 Der Prozess der aufrufen und das routing von Befehlen für VSPackages, unterscheidet sich von den Prozess des Aufrufens von Methoden einer Objektinstanz.  
  
 Die Umgebung leitet Befehle nacheinander von den innersten (local) Befehlskontext, basierend auf der aktuellen Auswahl, bis der äußerste Kontext angegeben (global). Der erste Kontext, der zum Ausführen des Befehls kann ist der, die ihn verarbeitet. Weitere Informationen finden Sie unter [Routing Algorithmus](../../extensibility/internals/command-routing-algorithm.md).  
  
 In den meisten Fällen verarbeitet die Umgebung Befehle mithilfe der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Da das Befehl-routing-Schema, viele verschiedene Objekte zum Verarbeiten von Befehlen ermöglicht, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> kann von einer beliebigen Anzahl von Objekten implementiert werden; dazu gehören Microsoft ActiveX-Steuerelemente, Fenster anzeigen Implementierungen, Document-Objekte, projekthierarchien und das VSPackage-Objekten selbst (für globale Befehle). In einigen speziellen Fällen, z. B. routing von Befehlen in einer Hierarchie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> -Schnittstelle muss implementiert werden.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Implementation (Implementierung)](../../extensibility/internals/command-implementation.md)|Beschreibt, wie Befehle in einem VSPackage implementiert.|  
|[Verfügbarkeit](../../extensibility/internals/command-availability.md)|Beschreibt, wie Visual Studio-Kontext bestimmt, welche Befehle verfügbar sind.|  
|[Routingalgorithmus](../../extensibility/internals/command-routing-algorithm.md)|Beschreibt, wie Visual Studio-routing-befehlsarchitektur Befehle aus, um die von anderen VSPackages behandelt werden.|  
|[Richtlinien zur Platzierung](../../extensibility/internals/command-placement-guidelines.md)|Schlägt vor, wie Sie Befehle in Visual Studio-Umgebung zu positionieren.|  
|[Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Beschreibt, wie der Visual Studio-befehlsarchitektur VSPackages optimal nutzen können.|  
|[Standardplatzierung von Befehlen, Gruppen und Symbolleisten](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Beschreibt, wie VSPackages am besten die Befehle verwenden können, die in Visual Studio enthalten sind.|  
|[Verwalten von VSPackages](../../extensibility/managing-vspackages.md)|Beschreibt, wie VSPackages von Visual Studio lädt.|  
|[VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Enthält Informationen zu XML-basierte VSCT-Dateien, die verwendet werden, um das Layout und die Darstellung von Befehlen in VSPackages zu beschreiben.|
