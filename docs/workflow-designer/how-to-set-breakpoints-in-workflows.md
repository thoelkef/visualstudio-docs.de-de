---
title: 'Workflow-Designer - Vorgehensweise: Festlegen von Haltepunkten in Workflows'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2ef863bfb899c218a65673236c284bed63aed11
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973528"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Gewusst wie: Festlegen von Haltepunkten in Workflows

Wenn Sie Windows Workflow-Designer verwenden, können Sie Haltepunkte für die grafischen Workflows festlegen, wie Sie in Visual Basic- oder C#-Code tun. Wie erwartet, hält die Workflowausführung an jedem festgelegten Haltepunkt an.

 Ein Haltepunkt verfügt über drei Zustände: *ausstehende*, *gebunden*, und *Fehler*. Wenn Sie einen Haltepunkt festlegen, erhält dieser den Status "Ausstehend". Dieser wird durch ein rot ausgefülltes Symbol dargestellt. Wenn die Laufzeit den Workflowtyp geladen hat, wechselt der Haltepunktstatus zu "Gebunden". Haben Sie ein falsches Format für den Haltepunkt angegeben, etwa einen ungültigen Aktivitätsnamen, dann erscheint eine Fehlermeldung. Der Haltepunkt wird immer noch dem Haltepunktfenster hinzugefügt, er wird jedoch mit einem kleinen "x" markiert.

> [!NOTE]
> Das Festlegen von Haltepunkten für aufgerufene Workflows wird nicht unterstützt.

> [!WARNING]
> Stellen Sie sicher, dass Sie die Option **nur eigenen Code aktivieren (nur verwaltet)** aus der **Tools**, **Optionen**, **Debuggen** Menü vor Debuggen. Wenn zwei in einer anderen Sequenz verschachtelt Sequenzen, und Sie einen Haltepunkt auf der ersten inneren Sequenz festlegen, drücken **F11** wird nicht in die zweite innere Sequenz Debuggen, wenn die **nur eigenen Code aktivieren (nur verwaltet)** nicht ausgewählt ist.

> [!WARNING]
> Haltepunkte in einem Workflow werden nicht erreicht, wenn der vollständige Pfad zur XAML-Dateieigenschaft nicht korrekt ist. Der vollständige Pfad der XAML-Datei ist nicht korrekt, nachdem das Projekt/die Projektmappe in einen anderen Ordner oder auf einen anderen Computer verschoben wurde. Drücken Sie STRG+S, um die vollständige Pfadeigenschaft zu speichern und zu aktualisieren.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>So legen Sie einen Haltepunkt für eine Aktivität in der Entwurfsansicht fest

1.  Wählen Sie die Aktivität aus, bei der der Debugger unterbrechen soll.

2.  Auf der **Debuggen** klicken Sie im Menü **Haltepunkt ein/aus**. Ein rotes Symbol wird am oberen linken Rand der Aktivität angezeigt.

     Alternativ können Sie auch die Tastenkombination drücken **F9** Schlüssel nach dem Auswählen der Aktivität oder Sie können mit der rechten Maustaste in der Aktivitäts und auswählen **Haltepunkt** dann **Haltepunkt einfügen**aus dem Kontextmenü.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Aufrufen des Workflow-Debuggers](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
- [Debuggen von Workflows mit dem Workflow-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)