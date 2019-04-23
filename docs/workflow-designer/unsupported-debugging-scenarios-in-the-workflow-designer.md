---
title: Im Workflow-Designer nicht unterstützte Debugszenarien
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 83c9b1158319b580bc860982b6c51c9c28edf5af
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099649"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Im Workflow-Designer nicht unterstützte Debugszenarien

Die Workflow-Designer in .NET Framework 4 viele neue Funktionen hinzugefügt, aber es gibt noch einige Debugszenarien, die nicht unterstützt werden.

Im folgenden sind die nicht unterstützte Debugszenarien Workflow-Designer:

- Nach dem Bearbeiten von Code kann die Ausführung nicht fortgesetzt werden.

- Die Ausführung kann an einem beliebigen Punkt im Workflow nicht fortgesetzt werden (Nächste Anweisung festlegen).

- Die Ausführung kann nicht bis zum Cursor fortgesetzt werden (Ausführen bis Cursor).

- Der Workflow-Designer kann nicht verwendet werden, um Workflows zu debuggen, die ohne den Designer direkt im Code erstellt wurden.

- In früheren Versionen von Windows Workflow Foundation (WF) erstellte Workflows können nicht in der .NET Framework 4-Designer debuggt werden.

- Es können keine Haltepunkte auf Verknüpfungen zwischen Aktivitäten oder <xref:System.Activities.Statements.Flowchart>-Knoten definiert werden.

- Die Zwischenablage steht während des Debuggens nicht zur Verfügung.

- Haltepunkte werden nicht beibehalten, wenn Aktivitäten kopiert oder eingefügt werden.

- Im Fenster Aufrufliste können keine Workflowhaltepunkte festgelegt werden.

- Beim Erstellen von Haltepunkten im Designer die **Zeile** und **Zeichen** Einstellungen in der **Neuer Haltepunkt** Dialogfeld nicht verwendet werden.

- Im Haltepunktfenster und im Kontextmenü werden die folgenden Spalten bzw. Optionen für das Debuggen von Workflows nicht unterstützt:

    - Bedingung

    - Trefferanzahl

    - Bei Treffer

    - Funktion

    - Daten

    - Prozess

    - Gehe zu Disassembly