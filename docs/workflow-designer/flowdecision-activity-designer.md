---
title: Workflow-Designer - FlowDecision-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08c8aadb3c452a59f1b44cd030331164384d23bb
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758336"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision-Aktivitätsdesigner

Der <xref:System.Activities.Statements.FlowDecision>-Knoten ist ein bedingter Knoten, der eine Verzweigung für den Steuerungsverlauf in eine von zwei Alternativen bereitstellt, die auf der Erfüllung einer angegebenen Bedingung basiert. Wenn der Verlauf mehr als zwei Verzweigungen erfordert, verwenden Sie stattdessen <xref:System.Activities.Statements.FlowSwitch%601>.

## <a name="the-flowdecision-node"></a>Der FlowDecision-Knoten

Verwenden Sie <xref:System.Activities.Statements.FlowDecision>, wenn der Verlauf in zwei Pfade verzweigt werden kann. Ein <xref:System.Activities.Statements.FlowDecision>-Knoten verfügt über ein <xref:System.Activities.Statements.FlowDecision.Condition%2A>-Objekt und ein <xref:System.Activities.Statements.FlowNode>-Objekt, das den beiden möglichen Ergebnissen zugeordnet ist: <xref:System.Activities.Statements.FlowDecision.True%2A> oder <xref:System.Activities.Statements.FlowDecision.False%2A>. Die <xref:System.Activities.Statements.FlowDecision.Condition%2A>-Instanz wird ausgewertet, und der Wert dieser Auswertung bestimmt, welcher <xref:System.Activities.Statements.FlowNode>-Knoten als Nächstes innerhalb des <xref:System.Activities.Statements.Flowchart>-Flussdiagramms verarbeitet werden soll.

### <a name="using-the-flowdecision-designer"></a>Verwenden des FlowDecision-Designers

Die **FlowDecision** Designer finden Sie in der **Flussdiagramm** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** Registerkarte "im Workflow-Designer. Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menü, oder drücken Sie **STRG**+**Alt** + **X**.

Die **FlowDecision** Designer gezogen werden kann, aus der **Toolbox** und gelöscht werden, an der Workflow-Designer-Oberfläche innerhalb einer **Flussdiagramm** Aktivitäts-Designer. Dies erstellt eine <xref:System.Activities.Statements.FlowDecision> mit der Bezeichnung **Entscheidung** innerhalb der <xref:System.Activities.Statements.Flowchart> Aktivität. Die Maus über den Designer und die **"true"** und **"false"** quadratische Handles für die beiden Branches angezeigt werden.

Nach dem Ziehen der **FlowDecision** -Designer und andere Designer auf die **Flussdiagramm**, können die Knoten verknüpft werden zusammen, um die Reihenfolge der Ausführung anzugeben. Zum Erstellen eines Links zwischen einem Quellknoten (einschließlich der **"true"** und **"false"** branches der **FlowDecision**) und einen Zielknoten, die Maus über den Designer für den Quellknoten und quadratischen Handles angezeigt werden, auf jeder Seite des Zertifikats. Klicken Sie auf eines der quadratischen Handles, und ziehen Sie es mit gedrückter Maustaste zu einem der Handles, die in ähnlicher Weise um den Zielknoten angezeigt werden, wenn Sie den Mauszeiger darüber halten. Lassen Sie die Maustaste los. Daraufhin wird zwischen beiden Knoten einen Link erstellt, der als vom Quelldesigner zum Zieldesigner zeigender Pfeil dargestellt wird.

Der Ausdruck, der besagt die <xref:System.Activities.Statements.FlowDecision.Condition%2A> eingegeben werden können, der **Bedingung** im Feld der **Eigenschaften** Fenster, indem Sie auf, wo der Hinweistext "VB-Ausdruck eingeben".

### <a name="the-flowdecision-properties"></a>Die FlowDecision-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.FlowDecision>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder in der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|Die Bedingung, die bestimmt, welchen Pfad die Flusssteuerung einschlägt.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Der von der Flusssteuerung eingeschlagene Pfad, wenn die <xref:System.Activities.Statements.FlowDecision.Condition%2A>-Bedingung erfüllt wird.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Der von der Flusssteuerung eingeschlagene Pfad, wenn die <xref:System.Activities.Statements.FlowDecision.Condition%2A>-Bedingung nicht erfüllt wird.|

## <a name="see-also"></a>Siehe auch

- [Flussdiagramm](../workflow-designer/flowchart-activity-designers.md)
- [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)