---
title: FlowSwitch&lt;T&gt; Aktivitäts-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ed39806fdca8eec3deccf5383c2386d07f0af929
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254752"
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch&lt;T&gt; Aktivitäts-Designer
Die <xref:System.Activities.Statements.FlowSwitch%601>-Aktivität ist ein bedingter Knoten, der einen Branch auf der Grundlage von Übereinstimmungskriterien für den Steuerungsverlauf bereitstellt, wenn mehr als zwei alternative Branches erforderlich sind. Wenn der Steuerungsverlauf nur zwei Pfade erfordert, verwenden Sie stattdessen die <xref:System.Activities.Statements.FlowDecision>-Aktivität.  
  
## <a name="the-flowswitcht-activity"></a>Die FlowSwitch\<T >-Aktivität  
 Die <xref:System.Activities.Statements.FlowSwitch%601> Aktivität enthält eine <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> , der einen Wert vom Typ zurückgibt *T* (angegeben durch den generischen Parameter) bei der Auswertung. Die Aktivität enthält auch einen Satz von <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>-Fällen, der eine eindeutige Zuordnung von möglichen Ergebnissen dieser Auswertung zu einem Satz von <xref:System.Activities.Statements.FlowNode>-Objekten angibt. Die <xref:System.Activities.Statements.FlowNode> ausgeführt wird, dessen Objekt des Typs *T* entspricht dem Wert, der den ausgewerteten <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Ein <xref:System.Activities.Statements.FlowSwitch%601.Default%2A>-Fall kann (optional) für den Fall bereitgestellt werden, in dem keine Übereinstimmung gefunden wird.  
  
### <a name="using-the-flowswitcht-activity-designer"></a>Verwenden des FlowSwitch\<T >-Aktivitätsdesigner  
 Die **FlowSwitch\<T >** Aktivitäts-Designer finden Sie in der **Flussdiagramm** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** auf der linken Seite der Registerkarte die [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü oder STRG + ALT + X.)  
  
 Die **FlowSwitch\<T >** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche innerhalb einer **Flussdiagramm** Aktivitäts-Designer. Verwenden der **Typen auswählen** Fenster, das angezeigt wird, um den Typ angeben (verknüpft ist, im Code mit der <xref:System.Activities.Statements.FlowSwitch%601> durch den generischen Parameter) abgerufen, die aus der Auswertung der <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Diese Prozedur erstellt eine <xref:System.Activities.Statements.FlowSwitch%601> Aktivität mit der Bezeichnung **Switch** innerhalb der <xref:System.Activities.Statements.Flowchart> Aktivität. Die <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> eingegeben werden können, der **Ausdruck** im Feld der **Eigenschaften** Fenster, indem Sie auf, wo der Hinweistext "VB-Ausdruck eingeben".  
  
 Bewegen Sie den Mauszeiger über die **FlowSwitch\<T >** Aktivitätsdesigner, damit die dazu führen, dass die quadratischen Handles, die verwendet werden, um Links <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> rund um die Ränder angezeigt werden. Nach dem Ziehen der **FlowSwitch < T\>**  Aktivitätsdesigner und andere Aktivitätsdesigner in der **Flussdiagramm**, <xref:System.Activities.Activity> Objekte, die sie darstellen, miteinander verknüpft werden können um die Reihenfolge der Ausführung anzugeben. Zum Erstellen eines der <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> zugeordneten der <xref:System.Activities.Statements.FlowSwitch%601>, klicken Sie auf eines der quadratischen fallhandles auf dem Umkreis des der **FlowSwitch\<T >** und ziehen Sie es (bei gedrückter Maustaste) zu einem der Handles Das wird in der Umrisslinie der Zielaktivität angezeigt, wenn der Mauszeiger auf den Aktivitätsdesigner zeigt. Lassen Sie die Maustaste gedrückt und einen Pfeil aus der **FlowSwitch\<T >** zum Ziel-Designer angezeigt wird, der diesen Fall darstellt. Der Standardwert für diesen Fall zeigt an, auf den Pfeil, und bearbeitet werden kann die **Fall** im Feld der **Eigenschaften** Fenster.  
  
### <a name="the-flowswitcht-properties"></a>Die FlowSwitch\<T > Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.FlowSwitch%601>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder in der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Gibt den Ausdruck an, der ausgewertet wird, um zu bestimmen, zu welchem der <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>-Fälle im Ausführungspfad gewechselt werden soll.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Gibt eine eindeutige Zuordnung von möglichen Ergebnissen an, die durch die Auswertung von <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> für einen Satz von <xref:System.Activities.Statements.FlowNode>-Objekten ermittelt wurden.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Gibt die Zuordnung an, wenn das Auswertungsergebnis von <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> mit keinem der Werte übereinstimmt, die im <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>-Objekt enthalten sind.|  
  
## <a name="see-also"></a>Siehe auch  
 [Flussdiagramm](../workflow-designer/flowchart-activity-designers.md)   
 [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)