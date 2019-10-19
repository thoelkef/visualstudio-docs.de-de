---
title: FlowSwitch-&lt;T &gt; Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 27abb660766a7c04742eca221432af19f05f0d28
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656644"
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch-&lt;T &gt; Aktivitäts Designer
Die <xref:System.Activities.Statements.FlowSwitch%601>-Aktivität ist ein bedingter Knoten, der einen Branch auf der Grundlage von Übereinstimmungskriterien für den Steuerungsverlauf bereitstellt, wenn mehr als zwei alternative Branches erforderlich sind. Wenn der Steuerungsverlauf nur zwei Pfade erfordert, verwenden Sie stattdessen die <xref:System.Activities.Statements.FlowDecision>-Aktivität.

## <a name="the-flowswitcht-activity"></a>Der FlowSwitch-\<T >-Aktivität
 Die <xref:System.Activities.Statements.FlowSwitch%601>-Aktivität enthält eine <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, die einen Wert vom Typ *t* zurückgibt (angegeben durch den generischen Parameter), wenn Sie ausgewertet wird. Die Aktivität enthält auch einen Satz von <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>-Fällen, der eine eindeutige Zuordnung von möglichen Ergebnissen dieser Auswertung zu einem Satz von <xref:System.Activities.Statements.FlowNode>-Objekten angibt. Der <xref:System.Activities.Statements.FlowNode> ausgeführt wird, dessen Objekt vom Typ *t* mit dem Wert des ausgewerteten <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> übereinstimmt. Ein <xref:System.Activities.Statements.FlowSwitch%601.Default%2A>-Fall kann (optional) für den Fall bereitgestellt werden, in dem keine Übereinstimmung gefunden wird.

### <a name="using-the-flowswitcht-activity-designer"></a>Verwenden des FlowSwitch-\<T >-Aktivitäts Designers
 Der **FlowSwitch-\<T >** -Aktivitäts Designer befindet sich in der Kategorie **Flussdiagramm** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite des [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie können auch **Toolbar** auswählen). über das Menü **Ansicht** oder STRG + ALT + X.)

 Der **FlowSwitch-\<T >** Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche innerhalb eines **Flowchart** -Aktivitäts Designers abgelegt werden. Verwenden Sie das Fenster **Typen auswählen** , das angezeigt wird, um den Typ (der mit dem <xref:System.Activities.Statements.FlowSwitch%601> des generischen Parameters verknüpft ist) anzugeben, der aus der Auswertung des <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> abgerufen wurde. Mit dieser Prozedur wird eine <xref:System.Activities.Statements.FlowSwitch%601> Aktivität mit der Bezeichnung **Switch** innerhalb der <xref:System.Activities.Statements.Flowchart>-Aktivität erstellt. Die <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> kann in das Feld **Ausdruck** des Fensters **Eigenschaften** eingegeben werden, indem Sie auf die Stelle klicken, an der der Hinweis Text "VB-Ausdruck eingeben" lautet.

 Bewegen Sie den Mauszeiger über den **FlowSwitch-\<T >** Aktivitäts Designer, damit die quadratischen Handles, die zum Verknüpfen von <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> verwendet werden, um Ihre Ränder herum angezeigt werden. Nachdem die **FlowSwitch-< T \>** Aktivitäts Designer und andere Aktivitäts Designer auf das **Flussdiagramm**gezogen wurden, können die <xref:System.Activities.Activity> Objekte, die Sie darstellen, miteinander verknüpft werden, um die Ausführungsreihenfolge anzugeben. Um eine der <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> zu erstellen, die dem <xref:System.Activities.Statements.FlowSwitch%601> zugeordnet ist, klicken Sie auf einen der quadratischen Case-Handles im Umkreis Bereich der **FlowSwitch-\<T >** und ziehen Sie ihn (durchgedrückt halten der Maustaste) zu einem der Handles, die auf ähnliche Weise um das Ziel Aktivität, wenn der Mauszeiger über den Designer bewegt wird. Lassen Sie die Maustaste los, und ein Pfeil aus dem **FlowSwitch-\<T >** an den Ziel-Designer wird angezeigt, der diesen Fall darstellt. Der Standardwert für diesen Fall wird auf dem Pfeil angezeigt und kann im Feld **Fall** des Fensters **Eigenschaften** bearbeitet werden.

### <a name="the-flowswitcht-properties"></a>Die FlowSwitch-\<T > Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.FlowSwitch%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder in der Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Gibt den Ausdruck an, der ausgewertet wird, um zu bestimmen, zu welchem der <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>-Fälle im Ausführungspfad gewechselt werden soll.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Gibt eine eindeutige Zuordnung von möglichen Ergebnissen an, die durch die Auswertung von <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> für einen Satz von <xref:System.Activities.Statements.FlowNode>-Objekten ermittelt wurden.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Gibt die Zuordnung an, wenn das Auswertungsergebnis von <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> mit keinem der Werte übereinstimmt, die im <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>-Objekt enthalten sind.|

## <a name="see-also"></a>Siehe auch
 Fluss [Diagramm Fluss](../workflow-designer/flowchart-activity-designers.md) [Diagramm](../workflow-designer/flowchart-activity-designer.md) [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)