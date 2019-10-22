---
title: 'Vorgehensweise: Festlegen von Breakpoints in Workflows | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d1bbb18a9015b52b3d65cb8f8fd02674693abc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659136"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Gewusst wie: Festlegen von Haltepunkten in Workflows
Wenn Sie [!INCLUDE[wfd1](../includes/wfd1-md.md)] verwenden, können Sie Haltepunkte für die grafischen Workflows genauso festlegen, wie Sie es in Visual Basic oder C#-Code machen würden. Wie erwartet, hält die Workflowausführung an jedem festgelegten Haltepunkt an.

 Ein Haltepunkt hat drei Zustände: " *Pending*", " *Bound*" und " *Error*". Wenn Sie einen Haltepunkt festlegen, erhält dieser den Status "Ausstehend". Dieser wird durch ein rot ausgefülltes Symbol dargestellt. Wenn die Laufzeit den Workflowtyp geladen hat, wechselt der Haltepunktstatus zu "Gebunden". Haben Sie ein falsches Format für den Haltepunkt angegeben, etwa einen ungültigen Aktivitätsnamen, dann erscheint eine Fehlermeldung. Der Haltepunkt wird immer noch dem Haltepunktfenster hinzugefügt, er wird jedoch mit einem kleinen "x" markiert.

> [!NOTE]
> Das Festlegen von Haltepunkten für aufgerufene Workflows wird nicht unterstützt.
>
> [!WARNING]
> Stellen Sie sicher, dass Sie die Option **nur eigenen Code aktivieren (nur verwaltet)** **im Menü Extras,** **Optionen**, **Debuggen** aktivieren, bevor Sie Debuggen. Wenn zwei Sequenzen in einer anderen Sequenz geschachtelt sind und Sie einen Haltepunkt für die erste innere Sequenz festlegen, wird durch Drücken von **F11** nicht in die zweite innere Sequenz debuggt, wenn die Option <strong>nur eigenen Code aktivieren (nur verwaltet) nicht aktiviert</strong>ist.
>
> [!WARNING]
> Haltepunkte in einem Workflow werden nicht erreicht, wenn der vollständige Pfad zur XAML-Dateieigenschaft nicht korrekt ist. Der vollständige Pfad der XAML-Datei ist nicht korrekt, nachdem das Projekt/die Projektmappe in einen anderen Ordner oder auf einen anderen Computer verschoben wurde. Drücken Sie STRG+S, um die vollständige Pfadeigenschaft zu speichern und zu aktualisieren.

### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>So legen Sie einen Haltepunkt für eine Aktivität in der Entwurfsansicht fest

1. Wählen Sie die Aktivität aus, bei der der Debugger unterbrechen soll.

2. Klicken Sie im Menü **Debuggen** auf halte **Punkt umschalten**. Ein rotes Symbol wird am oberen linken Rand der Aktivität angezeigt.

     Alternativ können Sie auch die Tastenkombination **F9** drücken, nachdem Sie die Aktivität ausgewählt haben, oder Sie können mit der rechten Maustaste auf die Aktivität klicken und halte **Punkt** auswählen und dann im Kontextmenü halte **Punkt einfügen** .

## <a name="see-also"></a>Siehe auch
 Gewusst [wie: Aufrufen der Workflow Debugger](../workflow-designer/how-to-invoke-the-workflow-debugger.md) - [debuggingworkflows mit dem Workflow-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) Gewusst [wie: Debuggen von XAML mit dem Workflow-Designer](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)