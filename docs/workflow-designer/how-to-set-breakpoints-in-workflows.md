---
title: 'Workflow-Designer – Vorgehensweise: Festlegen von Haltepunkten in Workflows'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7503d0b0bee201a9617e90966c9f75ac6333f228
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949518"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Vorgehensweise: Festlegen von Haltepunkten in Workflows

Wenn Sie die Workflow-Designer verwenden, können Sie Haltepunkte für die grafischen Workflows festlegen, wie Sie in Visual Basic- oder C#-Code tun würden. Wie erwartet, hält die Workflowausführung an jedem festgelegten Haltepunkt an.

Ein Haltepunkt verfügt über drei Zustände: *Ausstehende*, *gebunden*, und *Fehler*. Wenn Sie einen Haltepunkt festlegen, erhält dieser den Status "Ausstehend". Dieser wird durch ein rot ausgefülltes Symbol dargestellt. Wenn die Laufzeit den Workflowtyp geladen hat, wechselt der Haltepunktstatus zu "Gebunden". Haben Sie ein falsches Format für den Haltepunkt angegeben, etwa einen ungültigen Aktivitätsnamen, dann erscheint eine Fehlermeldung. Der Haltepunkt wird immer noch dem Haltepunktfenster hinzugefügt, er wird jedoch mit einem kleinen "x" markiert.

> [!NOTE]
> Das Festlegen von Haltepunkten für aufgerufene Workflows wird nicht unterstützt.

> [!NOTE]
> Stellen Sie sicher, dass Sie die Option **nur eigenen Code aktivieren (nur verwaltet)** aus der **Tools** > **Optionen** > **Debuggen**  Menü vor dem Debuggen. Wenn die Option nicht aktiviert ist und Sie einen Haltepunkt für die ersten inneren Sequenz festlegen, Sie zwei Sequenzen, die in einer anderen Sequenz verschachtelt haben, drücken **F11** ist nicht die zweite innere Sequenz debuggt.

> [!NOTE]
> Haltepunkte in einem Workflow werden nicht erreicht werden, wenn der vollständige Pfad zur XAML-Dateieigenschaft nicht korrekt ist. Der vollständige Pfad zur XAML-Datei ist nicht korrekt, nach dem Verschieben das Projekt oder Projektmappe in einen anderen Ordner oder einem anderen Computer. Wählen Sie **STRG**+**S** speichern und aktualisieren Sie die vollständige-Eigenschaft.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>So legen Sie einen Haltepunkt für eine Aktivität in der Entwurfsansicht fest

1. Wählen Sie die Aktivität aus, bei der der Debugger unterbrechen soll.

2. Auf der **Debuggen** , wählen Sie im Menü **Haltepunkt ein/aus**. Ein rotes Symbol wird am oberen linken Rand der Aktivität angezeigt.

   Sie können alternativ drücken **F9** nach dem Auswählen der Aktivität, oder Sie können mit der rechten Maustaste in der Aktivitäts und wählen Sie **Haltepunkt** > **Haltepunkt einfügen** über das Kontextmenü.

## <a name="see-also"></a>Siehe auch

- [Debuggen von Workflows mit dem Workflow-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)