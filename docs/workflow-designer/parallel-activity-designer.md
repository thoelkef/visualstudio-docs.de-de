---
title: Workflow-Designer - Parallel-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2315c27bc0a35ac1dc839b5fd98003105d92bd4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977236"
---
# <a name="parallel-activity-designer"></a>Parallel-Aktivitätsdesigner

Die <xref:System.Activities.Statements.Parallel>-Aktivität führt eine Sammlung von untergeordneten Aktivitäten parallel aus.

## <a name="the-parallel-activity"></a>Die Parallel-Aktivität

Die <xref:System.Activities.Statements.Parallel>-Aktivität speichert ihre untergeordneten Aktivitäten in einer <xref:System.Activities.Statements.Parallel.Branches%2A>-Auflistung. Verwenden Sie die <xref:System.Activities.Statements.Parallel>-Aktivität statt der <xref:System.Activities.Statements.Sequence>-Aktivität, wenn einige der untergeordneten Aktivitäten sich möglicherweise im Leerlauf befinden könnten.

Die <xref:System.Activities.Statements.Parallel> Aktivität verfügt über eine <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> -Eigenschaft, die einen Benutzer enthält angegeben, Visual Basic-Ausdruck. Die <xref:System.Activities.Statements.Parallel>-Aktivität wertet diese Eigenschaft aus, nachdem alle Verzweigungen abgeschlossen sind. Ergibt die Auswertung **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.Parallel> -Aktivität abgeschlossen, ohne die anderen Verzweigungen auszuführen. Wenn die <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> wird nicht ausgewertet **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.Parallel> Aktivität abgeschlossen wird, wenn alle untergeordneten Aktivitäten abgeschlossen sind.

### <a name="using-the-parallel-activity-designer"></a>Verwenden des Parallel-Aktivitätsdesigners

Die **Parallel** Aktivitäts-Designer finden Sie in der **Control Flow** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte auf der linken Seite im Workflow-Designer (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)

Die **parallele** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, wo Aktivitätsdesigner normalerweise, z. B. in einem platziertwerden**Sequenz** Aktivitäts-Designer. Nachdem sie an den Workflow-Designer ablegen, erstellt er eine <xref:System.Activities.Statements.Parallel> -Aktivität, die in der Standardeinstellung enthält eine <xref:System.Activities.Activity.DisplayName%2A> von **Parallel**

Eine Aktivität zum Hinzufügen der <xref:System.Activities.Statements.Parallel.Branches%2A> -Auflistung der parallelen Aktivität ziehen beliebigen anderen Aktivitätsdesigner aus der **Toolbox** und legen Sie es auf dem Dreieck innerhalb der **parallele** Aktivitäts-Designer. Die Dreiecke flankieren die in den Branches enthaltenen Aktivitäten. Zusätzliche Aktivitäten können hinzugefügt werden, indem diese Prozedur wiederholt wird. Die Aktivitäten können neu angeordnet werden, per Drag & Drop innerhalb der **parallele** Aktivitäts-Designer.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Eigenschaften der Parallel-Aktivität im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der Parallel-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert ist **parallele**. Der Wert kann optional bearbeitet werden, der **Eigenschaften** Raster oder direkt im Header Aktivitätsdesigners.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Enthält die Auflistung von untergeordneten Aktivitäten, die ausgeführt werden sollen.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Die Auswertung erfolgt nach Beendigung eines Branches. Ergibt die Auswertung **"true"**, die geplanten ausstehenden Verzweigungen abgebrochen. Wenn diese Eigenschaft nicht festgelegt oder ergibt **"false"**, die Aktivität abgeschlossen wird, wenn alle untergeordneten Aktivitäten abgeschlossen sind. Der Standardwert ist **null**.|

## <a name="see-also"></a>Siehe auch

- [Sequenz](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)