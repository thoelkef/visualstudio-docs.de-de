---
title: Befehl Entwurf | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42b41ee59f842c277400ba03ff682a757d5343e8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009829"
---
# <a name="command-design"></a>Befehlsentwurf
Wenn Sie einen Befehl für ein VSPackage hinzufügen, müssen Sie angeben, in dem es angezeigt werden, wenn es verfügbar ist, und wie sie behandelt werden.  
  
## <a name="define-commands"></a>Definieren von Befehlen  
 Um neue Befehle definieren, sind Sie ein Visual Studio-Befehlstabelle (*VSCT*) Datei in Ihrem VSPackage-Projekt. Wenn Sie eine VSPackage mit der Visual Studio-Paketvorlage erstellt haben, enthält das Projekt eine dieser Dateien. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabellen (VSCT) Befehlsdateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio führt alle die *VSCT* -Dateien sucht, damit die Befehle angezeigt werden können. Da diese Dateien aus dem VSPackage binäre unterscheiden, ist Visual Studio keine beim Laden des Pakets, um die Befehle zu suchen. Weitere Informationen finden Sie unter [wie VSPackages hinzufügen, Elemente der Benutzeroberfläche](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio verwendet die <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Registrierungsattribut Menüressourcen und Befehle zu definieren. Weitere Informationen finden Sie unter [befehlsimplementierung](../../extensibility/internals/command-implementation.md).  
  
 Befehle können in einer Reihe von Möglichkeiten zur Laufzeit geändert werden. Sie können angezeigt oder ausgeblendet, aktiviert oder deaktiviert werden. Sie können verschiedene Text oder Symbolen, oder Sie können verschiedene Werte enthalten. Bevor Visual Studio das VSPackage lädt, kann eine umfangreiche Anpassung ausgeführt werden. Weitere Informationen finden Sie unter [wie VSPackages hinzufügen, Elemente der Benutzeroberfläche](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Befehlshandler  
 Wenn Sie einen Befehl erstellen, müssen Sie einen Ereignishandler zum Ausführen des Befehls angeben. Wenn der Benutzer den Befehl auswählt, muss dieser entsprechend weitergeleitet werden. Routing von einem Befehl bedeutet das Senden an das richtige VSPackage zu aktivieren oder deaktivieren, ausblenden oder anzeigen und führen Sie es, wenn der Benutzer dazu. Weitere Informationen finden Sie unter [Algorithmus für das Befehlsrouting](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="visual-studio-command-environment"></a>Visual Studio-Befehl-Umgebung  
 Visual Studio kann eine beliebige Anzahl von VSPackages hosten und kann jeweils einen eigenen Befehlssatz beitragen. Die Umgebung zeigt nur die Befehle, die für den aktuellen Task geeignet sind. Weitere Informationen finden Sie unter [Befehl Verfügbarkeit](../../extensibility/internals/command-availability.md) und [auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md).  
  
 Eine VSPackage, die definiert, neue Befehle, Menüs, Symbolleisten oder Kontextmenüs bietet die Befehlsinformationen in Visual Studio bei der Installation über die Registrierungseinträge, die Ressourcen in systemeigenen oder verwalteten Assemblys verweisen. Jede Ressource verweist dann auf eine binäre Ressource (*CTO*)-Datei, die erstellt wird, wenn Sie eine Visual Studio-Befehlstabelle kompilieren (*VSCT*) Datei. Dadurch wird Visual Studio, um die zusammengeführte Befehle, Menüs und Symbolleisten bereitstellen, ohne dass alle installierten VSPackage zu laden.  
  
### <a name="command-organization"></a>Befehls-Organisation  
 Die Umgebung positioniert Befehle nach Gruppe, Priorität und im Menü.  
  
- Gruppen sind logische Sammlungen von verwandten Befehlen, z. B. die **Ausschneiden**, **Kopie**, und **einfügen** Befehlsgruppe. Gruppen sind die Befehle, die in Menüs angezeigt werden.  
  
- Priorität bestimmt die Reihenfolge, in der einzelnen Befehle in einer Gruppe im Menü angezeigt werden.  
  
- Menüs dienen als Container für Gruppen.  
  
  Die Umgebung sind einige Befehle, Gruppen und Menüs vordefiniert. Weitere Informationen finden Sie unter [standardplatzierung-Befehl, Gruppe und Symbolleiste](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Ein Befehl kann auf eine primäre Gruppe zugewiesen werden. Die primäre Gruppe steuert die Position des Befehls in der Struktur im Hauptmenü und in der **anpassen** Dialogfeld. Ein Befehl kann in mehrere Gruppen angezeigt werden; Beispielsweise kann ein Befehl im Hauptmenü auf ein Kontextmenü aufrufen und auf einer Symbolleiste sein. Weitere Informationen finden Sie unter [wie VSPackages hinzufügen, Elemente der Benutzeroberfläche](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Befehlsrouting  
 Der Prozess der aufrufen und das routing von Befehlen für VSPackages, unterscheidet sich von den Prozess des Aufrufens von Methoden einer Objektinstanz.  
  
 Die Umgebung leitet Befehle nacheinander von den innersten (local) Befehlskontext, basierend auf der aktuellen Auswahl, bis der äußerste Kontext angegeben (global). Der erste Kontext, der zum Ausführen des Befehls kann ist der, die ihn verarbeitet. Weitere Informationen finden Sie unter [Algorithmus für das Befehlsrouting](../../extensibility/internals/command-routing-algorithm.md).  
  
 In den meisten Fällen verarbeitet die Umgebung Befehle mithilfe der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Da das Befehl-routing-Schema, viele verschiedene Objekte zum Verarbeiten von Befehlen ermöglicht, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> kann von einer beliebigen Anzahl von Objekten implementiert werden; dazu gehören Microsoft ActiveX-Steuerelemente, Fenster anzeigen Implementierungen, Document-Objekte, projekthierarchien und das VSPackage-Objekten selbst (für globale Befehle). In einigen speziellen Fällen, z. B. routing von Befehlen in einer Hierarchie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> -Schnittstelle muss implementiert werden.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Befehlsimplementierung](../../extensibility/internals/command-implementation.md)|Beschreibt, wie Befehle in einem VSPackage implementiert.|  
|[Befehlsverfügbarkeit](../../extensibility/internals/command-availability.md)|Beschreibt, wie Visual Studio-Kontext bestimmt, welche Befehle verfügbar sind.|  
|[Algorithmus für das Befehlsrouting](../../extensibility/internals/command-routing-algorithm.md)|Beschreibt, wie Visual Studio-routing-befehlsarchitektur Befehle aus, um die von anderen VSPackages behandelt werden.|  
|[Richtlinien zur befehlsplatzierung](../../extensibility/internals/command-placement-guidelines.md)|Schlägt vor, wie Sie Befehle in Visual Studio-Umgebung zu positionieren.|  
|[Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Beschreibt, wie der Visual Studio-befehlsarchitektur VSPackages optimal nutzen können.|  
|[Standardplatzierung-Befehl, Gruppe und Symbolleiste](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Beschreibt, wie VSPackages am besten die Befehle verwenden können, die in Visual Studio enthalten sind.|  
|[Verwalten von VSPackages](../../extensibility/managing-vspackages.md)|Beschreibt, wie VSPackages von Visual Studio lädt.|  
|[Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Enthält Informationen zu XML-basierte *VSCT* -Dateien, die zum Beschreiben von Layout und Darstellung von Befehlen in VSPackages verwendet werden.|