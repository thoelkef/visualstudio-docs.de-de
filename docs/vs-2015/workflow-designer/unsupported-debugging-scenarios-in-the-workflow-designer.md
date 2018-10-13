---
title: Nicht unterstützte Debugszenarien im Workflow-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: aece5a71965a1935218027dd97b1b8363a646388
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184482"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Im Workflow-Designer nicht unterstützte Debugszenarien
Im Workflow-Designer in [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] wurden viele neue Funktionen hinzugefügt. Es gibt jedoch nach wie vor einige Debugszenarien, die nicht unterstützt werden. In diesem Dokument werden die vom Workflow-Designer nicht unterstützten Debugszenarien ausführlich beschrieben.  
  
-   Nach dem Bearbeiten von Code kann die Ausführung nicht fortgesetzt werden.  
  
-   Die Ausführung kann an einem beliebigen Punkt im Workflow nicht fortgesetzt werden (Nächste Anweisung festlegen).  
  
-   Die Ausführung kann nicht bis zum Cursor fortgesetzt werden (Ausführen bis Cursor).  
  
-   Der Workflow-Designer kann nicht verwendet werden, um Workflows zu debuggen, die ohne den Designer direkt im Code erstellt wurden.  
  
-   Ein Debuggen von Workflows, die mit früheren Versionen von [!INCLUDE[wf](../includes/wf-md.md)] erstellt wurden, ist im Designer von [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] nicht möglich.  
  
-   Es können keine Haltepunkte auf Verknüpfungen zwischen Aktivitäten oder <xref:System.Activities.Statements.Flowchart>-Knoten definiert werden.  
  
-   Die Zwischenablage steht während des Debuggens nicht zur Verfügung.  
  
-   Haltepunkte werden nicht beibehalten, wenn Aktivitäten kopiert oder eingefügt werden.  
  
-   Im Fenster Aufrufliste können keine Workflowhaltepunkte festgelegt werden.  
  
-   Beim Erstellen von Haltepunkten im Designer die **Zeile** und **Zeichen** Einstellungen in der **Neuer Haltepunkt** Dialogfeld nicht verwendet werden.  
  
-   Im Haltepunktfenster und im Kontextmenü werden die folgenden Spalten bzw. Optionen für das Debuggen von Workflows nicht unterstützt:  
  
    -   Bedingung  
  
    -   Trefferanzahl  
  
    -   Bei Treffer  
  
    -   Funktion  
  
    -   Daten  
  
    -   Prozess  
  
    -   Gehe zu Disassembly