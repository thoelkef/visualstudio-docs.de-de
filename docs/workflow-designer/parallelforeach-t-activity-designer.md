---
title: Workflow-Designer - ParallelForEach&lt;T&gt; Aktivitäts-Designer
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfd7d3220bc67b764b96033ad516eb857bec6014
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31978270"
---
# <a name="parallelforeach-activity-designer"></a>ParallelForEach-Aktivitäts-Designer

Die <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität listet die Elemente einer Auflistung auf und führt gleichzeitig, asynchron im gleichen Thread, eine eingebettete Anweisung für jedes Element der Auflistung aus. Verwenden Sie diese Flusssteuerungsaktivität statt der <xref:System.Activities.Statements.Sequence>-Aktivität, wenn von den untergeordneten Aktivitäten dieser Aktivität erwartet werden kann, dass sie in den Leerlauf übergehen.

Die <xref:System.Activities.Statements.ParallelForEach%601> Aktivität verfügt über eine <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> -Eigenschaft, die einen Benutzer enthält angegeben, Visual Basic-Ausdruck. Die <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität wertet diese Eigenschaft aus, nachdem alle Verzweigungen abgeschlossen sind. Ergibt die Auswertung **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.ParallelForEach%601> -Aktivität abgeschlossen, ohne die anderen Verzweigungen auszuführen. Wenn die <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> wird nicht ausgewertet **"true"**, und klicken Sie dann die <xref:System.Activities.Statements.ParallelForEach%601> Aktivität abgeschlossen wird, wenn alle untergeordneten Aktivitäten abgeschlossen sind.

## <a name="the-parallelforeacht-activity"></a>Die ParallelForEach < T\> Aktivität

<xref:System.Activities.Statements.ParallelForEach%601> listet seine Werte auf und plant die <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>-Ausführung für jeden aufgelisteten Wert. Es wird nur der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> geplant. Wie der Textkörper ausgeführt wird, hängt davon ab, ob der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> in den Leerlauf übergeht.

Geht der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nicht in den Leerlauf über, erfolgt die Ausführung in umgekehrter Reihenfolge, da die geplanten Aktivitäten als Stapel behandelt werden, also die letzte geplante Aktivität als erste ausgeführt wird. Angenommen, Sie haben eine Auflistung von {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> und Verwenden einer **WriteLine** als Textkörper, um den Wert schreiben. Dann werden die Werte 4, 3, 2, 1 auf der Konsole ausgegeben. Grund hierfür ist, **WriteLine** geht nicht so nach 4 im Leerlauf **WriteLine** Aktivitäten geplant haben, die sie mithilfe eines Verhaltens Stapel ausgeführt (zuerst in den letzten Out).

Wenn aber Aktivitäten im <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> in den Leerlauf übergehen können, etwa eine <xref:System.ServiceModel.Activities.Receive>-Aktivität oder eine <xref:System.Activities.Statements.Delay>-Aktivität, ergibt sich Folgendes. Dann ist es nicht notwendig, auf den Abschluss zu warten. <xref:System.Activities.Statements.ParallelForEach%601> versucht dann, die nächste geplante Textkörperaktivität auszuführen. Wenn auch diese in den Leerlauf übergeht, bewegt sich <xref:System.Activities.Statements.ParallelForEach%601> zum Textkörper der nächsten Aktivität.

### <a name="using-the-parallelforeacht-activity-designer"></a>Verwenden die ParallelForEach\<T >-Aktivitätsdesigners

Die **ParallelForEach\<T >** Aktivitäts-Designer finden Sie in der **Control Flow** Kategorie von der **Toolbox**, indem Sie auf die zugegriffenwird **Toolbox** Registerkarte auf der linken Seite im Workflow-Designer (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)

Die **ParallelForEach\<T >** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, wo Aktivitätsdesigner normalerweise platziert werden, für Innere z. B. eine **Sequenz** Aktivitäts-Designer. Nachdem sie an den Workflow-Designer ablegen, erstellt er eine <xref:System.Activities.Statements.ParallelForEach%601> -Aktivität, die in der Standardeinstellung enthält eine <xref:System.Activities.Activity.DisplayName%2A> von **ParallelForEach < Int32\>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T\> Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert ist **ParallelForEach\<Int32 >**. Der Wert kann optional bearbeitet werden, der **Eigenschaften** Raster oder direkt im Header Aktivitätsdesigners.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Die Aktivität, die für jedes Element in der Auflistung ausgeführt werden soll. Hinzufügen der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> Aktivität, indem Sie eine Aktivität aus der Toolbox in den **Text** Feld der **ParallelForEach\<T >** Aktivitäts-Designer mit dem Hinweistext "Aktivität hier ablegen".|
|**TypeArgument**|True|Der Typ der Elemente in der <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> durch den generischen Parameter angegebene Sammlung *T*. Standardmäßig **TypeArgument** festgelegt ist, um **Int32**. So ändern Sie den Typ "T" in der **ParallelForEach < T\>**  Aktivitäts-Designer, ändern Sie den Wert, der die **TypeArgument** Kombinationsfeld im Eigenschaftenraster.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Die Auflistung, deren Elemente durchlaufen werden. Festlegen der <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, geben Sie einen Visual Basic-Ausdruck in der **Werte** Feld der **ForEach < T\>**  Aktivitäts-Designer in das Feld mit dem Hinweistext "VB-Ausdruck eingeben" oder  **Werte** Feld der **Eigenschaften** Fenster.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Die Auswertung erfolgt nach Abschluss der einzelnen Iterationen. Ergibt die Auswertung True, werden die geplanten ausstehenden Iterationen abgebrochen. Wenn diese Eigenschaft nicht festgelegt ist, werden alle geplanten Anweisungen bis zur Beendigung ausgeführt.|

Standardmäßig hat der Schleifeniterator die Bezeichnung "item". Sie können den Namen der Iteratorvariablen im Ändern der **ForEach** im Feld **ParallelForEach\<T >** Aktivitäts-Designer. Der Schleifeniterator kann in den untergeordneten Elementen der <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität in Ausdrücken verwendet werden.

## <a name="see-also"></a>Siehe auch

- [Sequenz](../workflow-designer/sequence-activity-designer.md)
- [Parallele](../workflow-designer/parallel-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)