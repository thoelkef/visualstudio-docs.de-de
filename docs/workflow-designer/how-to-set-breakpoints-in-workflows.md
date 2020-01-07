---
title: 'Workflow-Designer: Gewusst wie: Festlegen von Breakpoints in Workflows'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ebebd0efe689c2f3f83e776c0cb3889ee64add2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593888"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Vorgehensweise: Festlegen von Breakpoints in Workflows

Wenn Sie Workflow-Designer verwenden, können Sie Haltepunkte in ihren grafischen Workflows wie Visual Basic oder C# Code festlegen. Wie erwartet, hält die Workflowausführung an jedem festgelegten Haltepunkt an.

Ein Haltepunkt hat drei Zustände: " *Pending*", " *Bound*" und " *Error*". Wenn Sie einen Haltepunkt festlegen, erhält dieser den Status "Ausstehend". Dieser wird durch ein rot ausgefülltes Symbol dargestellt. Wenn die Laufzeit den Workflowtyp geladen hat, wechselt der Haltepunktstatus zu "Gebunden". Haben Sie ein falsches Format für den Haltepunkt angegeben, etwa einen ungültigen Aktivitätsnamen, dann erscheint eine Fehlermeldung. Der Haltepunkt wird immer noch dem Haltepunktfenster hinzugefügt, er wird jedoch mit einem kleinen "x" markiert.

> [!NOTE]
> Das Festlegen von Haltepunkten für aufgerufene Workflows wird nicht unterstützt.

> [!NOTE]
> Stellen Sie sicher, dass Sie die Option **nur eigenen Code aktivieren (nur verwaltet)** **im Menü Extras > ** **Optionen** > Menü **Debuggen** aktivieren, bevor Sie Debuggen. Wenn die Option nicht ausgewählt ist und zwei Sequenzen in einer anderen Sequenz geschachtelt sind und Sie einen Haltepunkt für die erste innere Sequenz festgelegt haben, wird durch Drücken von **F11** nicht in die zweite innere Sequenz debuggt.

> [!NOTE]
> Haltepunkte in einem Workflow werden nicht getroffen, wenn der vollständige Pfad zur XAML-Datei Eigenschaft nicht korrekt ist. Der vollständige Pfad zur XAML-Datei ist nicht korrekt, nachdem das Projekt oder die Projekt Mappe in einen anderen Ordner oder auf einen anderen Computer verschoben wurde. Wählen Sie **STRG**+**S** aus, um die vollständige Pfadeigenschaft zu speichern und zu aktualisieren.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>So legen Sie einen Haltepunkt für eine Aktivität in der Entwurfsansicht fest

1. Wählen Sie die Aktivität aus, bei der der Debugger unterbrechen soll.

2. Klicken Sie im Menü **Debuggen** auf halte **Punkt umschalten**. Ein rotes Symbol wird am oberen linken Rand der Aktivität angezeigt.

   Alternativ können Sie **F9** drücken, nachdem Sie die Aktivität ausgewählt haben, oder Sie können mit der rechten Maustaste auf die Aktivität klicken und im Kontextmenü halte **Punkt > halte** **Punkt einfügen** auswählen.

## <a name="see-also"></a>Siehe auch

- [Debuggen von Workflows mit dem Workflow-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Vorgehensweise: Debuggen von XAML mit dem Workflow-Designer](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
