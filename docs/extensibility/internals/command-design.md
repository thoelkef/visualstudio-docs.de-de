---
title: Befehl Entwurf | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf6d0d7a9aa556aab454f90e4dcfc5dc4f236c03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="command-design"></a>Befehl Entwurf
Wenn Sie einen Befehl für ein VSPackage hinzufügen, müssen Sie angeben, wo es ist, die angezeigt werden, wenn er verfügbar ist und wie ist es, die verarbeitet werden.  
  
## <a name="defining-commands"></a>Definieren Befehle  
 Um neue Befehle definieren, müssen binden Sie eine Visual Studio-Befehlstabelle (VSCT)-Datei in Ihrem VSPackage-Projekt ein. Wenn Sie eine VSPackage mit der Visual Studio-Paketvorlage erstellt haben, enthält das Projekt eine dieser Dateien. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio führt die VSCT-Dateien, die es findet, damit die Befehle angezeigt werden können. Da diese Dateien aus dem VSPackage binäre unterscheiden, Visual Studio keine zum Laden des Pakets, um die Befehle zu suchen. Weitere Informationen finden Sie unter [wie VSPackages hinzufügen Benutzeroberflächenelemente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio verwendet die <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> registrierungsattributs Menüressourcen und Befehle definiert. Weitere Informationen finden Sie unter [Implementierung](../../extensibility/internals/command-implementation.md).  
  
 Befehle können zur Laufzeit in eine Zahl auf verschiedene Weise geändert werden. Sie können angezeigt oder ausgeblendet, aktiviert oder deaktiviert werden. Sie können verschiedene Text oder Symbolen, oder Sie können verschiedene Werte enthalten. Vor Visual Studio das VSPackage lädt, kann eine sehr viel systemverarbeitungszeit in der Anpassung ausgeführt werden. Weitere Informationen finden Sie unter [wie VSPackages hinzufügen Benutzeroberflächenelemente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Befehlshandler  
 Wenn Sie einen Befehl erstellen, müssen Sie einen Ereignishandler zum Ausführen des Befehls angeben. Wenn der Benutzer den Befehl auswählt, müssen sie ordnungsgemäß weitergeleitet werden. Einen Befehl Routing bedeutet senden an das richtige VSPackage zu aktivieren oder deaktivieren, ausblenden oder zeigen Sie es und führen Sie sie aus, wenn der Benutzer entscheidet sich dazu. Weitere Informationen finden Sie unter [Routing Algorithmus](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Visual Studio-Umgebung-Befehl  
 Visual Studio kann als host für eine beliebige Anzahl von VSPackages und kann jeweils einen eigenen Befehlssatz beitragen. Die Umgebung zeigt nur die Befehle, die für den aktuellen Task geeignet sind. Weitere Informationen finden Sie unter [Verfügbarkeit](../../extensibility/internals/command-availability.md) und [Auswahl Kontextobjekte](../../extensibility/internals/selection-context-objects.md).  
  
 Ein VSPackage, das definiert, neue Befehle, Menüs, Symbolleisten und Kontextmenüs bietet seine Befehlsinformationen in Visual Studio, bei der Installation über die Registrierungseinträge, die auf Ressourcen in systemeigenen oder verwalteten Assemblys verweisen. Jede Ressource verweist dann auf eine binäre Daten (CTO) Ressourcendatei, die erzeugt wird, wenn Sie eine Visual Studio-Befehlstabelle (VSCT)-Datei kompilieren. Dies kann Visual Studio zusammengeführte Befehlsgruppen, Menüs und Symbolleisten bereitstellen, ohne alle installierten VSPackage laden zu müssen.  
  
### <a name="command-organization"></a>Befehl Organisation  
 Die Umgebung positioniert Befehle durch Gruppieren, Priorität und Menüs.  
  
-   Gruppen sind logische Gruppen verwandter Befehle, z. B. die **Ausschneiden**, **Kopie**, und **einfügen** Befehlsgruppe. Gruppen sind die Befehle, die in Menüs angezeigt werden.  
  
-   Die Priorität wird bestimmt die Reihenfolge, in der einzelnen Befehle in einer Gruppe im Menü angezeigt werden.  
  
-   Menüs fungieren als Container für Gruppen.  
  
 Die Umgebung verfügt über vordefinierte einige Befehle, Gruppen und Menüs. Weitere Informationen finden Sie unter [Standard-Befehl, Gruppen- und Symbolleiste Platzierung](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 Ein Befehl kann eine primäre Gruppe zugewiesen werden. Die primäre Gruppe steuert die Position des Befehls in der Struktur im Hauptmenü und in der **anpassen** (Dialogfeld). Ein Befehl kann in mehrere Gruppen angezeigt werden; Beispielsweise kann ein Befehl im Hauptmenü auf ein Kontextmenü aufrufen und auf einer Symbolleiste sein. Weitere Informationen finden Sie unter [wie VSPackages hinzufügen Benutzeroberflächenelemente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Befehlsrouting  
 Der Vorgang aufrufen und das routing von Befehlen für VSPackages, unterscheidet sich vom Vorgang zum Aufrufen von Methoden für Objektinstanzen.  
  
 Die Umgebung leitet Befehle sequenziell von den innersten (local) Befehlskontext, basierend auf der aktuellen Auswahl, bis der äußerste Kontext angegeben (global). Der erste Kontext, der beim Ausführen des Befehls kann ist diejenige, die ihn verarbeitet. Weitere Informationen finden Sie unter [Routing Algorithmus](../../extensibility/internals/command-routing-algorithm.md).  
  
 In den meisten Fällen verarbeitet die Umgebung Befehle mithilfe der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Da das routing Befehl-Schema zum Behandeln von Befehlen, viele verschiedene Objekte ermöglicht <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> kann von einer beliebigen Anzahl von Objekten implementiert werden; diese umfassen Microsoft ActiveX-Steuerelemente, Fenster anzeigen Implementierungen, Document-Objekte, Projekt-Hierarchien und VSPackage-Objekten selbst (für globale Befehle). In einigen Fällen spezialisierten z. B. routing von Befehlen in einer Hierarchie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> -Schnittstelle muss implementiert werden.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Implementation (Implementierung)](../../extensibility/internals/command-implementation.md)|Beschreibt, wie Befehle in einem VSPackage implementiert.|  
|[Verfügbarkeit](../../extensibility/internals/command-availability.md)|Beschreibt, wie Visual Studio-Kontext bestimmt, welche Befehle verfügbar sind.|  
|[Routing-Algorithmus](../../extensibility/internals/command-routing-algorithm.md)|Beschreibt, wie Visual Studio-routing befehlsarchitektur Befehle aus, um von anderen VSPackages behandelt werden kann.|  
|[Richtlinien zur Platzierung](../../extensibility/internals/command-placement-guidelines.md)|Schlägt vor, wie Sie Befehle in Visual Studio-Umgebung zu positionieren.|  
|[Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Beschreibt, wie der Visual Studio-befehlsarchitektur VSPackages am besten nutzen können.|  
|[Standardplatzierung von Befehlen, Gruppen und Symbolleisten](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Beschreibt, wie VSPackages am besten die Befehle, die in Visual Studio enthalten sind.|  
|[Verwalten von VSPackages](../../extensibility/managing-vspackages.md)|Beschreibt, wie VSPackages von Visual Studio lädt.|  
|[VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Enthält Informationen zu XML-basierte VSCT-Dateien, die verwendet werden, um das Layout und die Darstellung von Befehlen in VSPackages zu beschreiben.|