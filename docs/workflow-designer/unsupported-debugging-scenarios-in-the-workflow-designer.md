---
title: Nicht unterstützte Debugszenarien im Workflow-Designer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e2b250c44e6aa1fbbdf7c546c8e9bf15ffbbe008
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Im Workflow-Designer nicht unterstützte Debugszenarien
Im Workflow-Designer in [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] wurden viele neue Funktionen hinzugefügt. Es gibt jedoch nach wie vor einige Debugszenarien, die nicht unterstützt werden. In diesem Dokument werden die vom Workflow-Designer nicht unterstützten Debugszenarien ausführlich beschrieben.  
  
-   Nach dem Bearbeiten von Code kann die Ausführung nicht fortgesetzt werden.  
  
-   Die Ausführung kann an einem beliebigen Punkt im Workflow nicht fortgesetzt werden (Nächste Anweisung festlegen).  
  
-   Die Ausführung kann nicht bis zum Cursor fortgesetzt werden (Ausführen bis Cursor).  
  
-   Der Workflow-Designer kann nicht verwendet werden, um Workflows zu debuggen, die ohne den Designer direkt im Code erstellt wurden.  
  
-   Ein Debuggen von Workflows, die mit früheren Versionen von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] erstellt wurden, ist im Designer von [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] nicht möglich.  
  
-   Es können keine Haltepunkte auf Verknüpfungen zwischen Aktivitäten oder <xref:System.Activities.Statements.Flowchart>-Knoten definiert werden.  
  
-   Die Zwischenablage steht während des Debuggens nicht zur Verfügung.  
  
-   Haltepunkte werden nicht beibehalten, wenn Aktivitäten kopiert oder eingefügt werden.  
  
-   Im Fenster Aufrufliste können keine Workflowhaltepunkte festgelegt werden.  
  
-   Beim Erstellen von Haltepunkten im Designer die **Zeile** und **Zeichen** Einstellungen in der **Neuer Haltepunkt** Dialogfeld werden nicht verwendet.  
  
-   Im Haltepunktfenster und im Kontextmenü werden die folgenden Spalten bzw. Optionen für das Debuggen von Workflows nicht unterstützt:  
  
    -   Bedingung  
  
    -   Trefferanzahl  
  
    -   Bei Treffer  
  
    -   Funktion  
  
    -   Daten  
  
    -   Prozess  
  
    -   Gehe zu Disassembly