---
title: "FlowSwitch&lt;T&gt; Aktivitäts-Designer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: c3e757d8ffea7e91c2d5e51bc4a04e6225d1064f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch&lt;T&gt; Aktivitäts-Designer
Die <xref:System.Activities.Statements.FlowSwitch%601>-Aktivität ist ein bedingter Knoten, der eine Verzweigung auf der Grundlage von Übereinstimmungskriterien für den Steuerungsverlauf bereitstellt, wenn mehr als zwei alternative Verzweigungen erforderlich sind. Wenn der Steuerungsverlauf nur zwei Pfade erfordert, verwenden Sie stattdessen die <xref:System.Activities.Statements.FlowDecision>-Aktivität.  
  
## <a name="the-flowswitcht-activity"></a>Die FlowSwitch < T\> Aktivität  
 Die <xref:System.Activities.Statements.FlowSwitch%601> -Aktivität enthält eine <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> , die einen Wert des Typs zurückgibt *T* (angegeben durch den generischen Parameter) bei der Auswertung. Die Aktivität enthält auch einen Satz von <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>-Fällen, der eine eindeutige Zuordnung von möglichen Ergebnissen dieser Auswertung zu einem Satz von <xref:System.Activities.Statements.FlowNode>-Objekten angibt. Die <xref:System.Activities.Statements.FlowNode> ausgeführt wird, dessen Objekt des Typs *T* entspricht dem Wert des ausgewerteten <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Ein <xref:System.Activities.Statements.FlowSwitch%601.Default%2A>-Fall kann (optional) für den Fall bereitgestellt werden, in dem keine Übereinstimmung gefunden wird.  
  
### <a name="using-the-flowswitcht-activity-designer"></a>Verwenden die FlowSwitch\<T >-Aktivitätsdesigners  
 Die **FlowSwitch\<T >** Aktivitäts-Designer finden Sie in der **Flussdiagramm** Kategorie von der **Toolbox**, indem Sie auf die zugegriffenwird**Toolbox** auf der linken Seite der Registerkarte die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)  
  
 Die **FlowSwitch\<T >** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche innerhalb einer **Flussdiagramm** Aktivitäts-Designer. Verwenden der **Typen auswählen** Fenster, das angezeigt wird, um den Typ angeben (verknüpft sind, im Code mit der <xref:System.Activities.Statements.FlowSwitch%601> durch den generischen Parameter) abgerufen werden, aus der Auswertung der <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Diese Prozedur erstellt eine <xref:System.Activities.Statements.FlowSwitch%601> Aktivität mit der Bezeichnung **Switch** innerhalb der <xref:System.Activities.Statements.Flowchart> Aktivität. Die <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> eingegeben werden können, der **Ausdruck** im Feld der **Eigenschaften** Fenster durch Klicken auf die in den Bereich der Hinweistext "VB-Ausdruck eingeben".  
  
 Mit der Maus über die **FlowSwitch\<T >** Aktivitätsdesigner, die dazu führen, dass die quadratische Handles, die verwendet werden, um Links <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> seinen Rändern angezeigt werden. Nach dem Ziehvorgang die **FlowSwitch < T\>**  Aktivitäts-Designer und andere Aktivitätsdesigner in der **Flussdiagramm**die <xref:System.Activities.Activity> Objekte, die sie darstellen, miteinander verknüpft werden können um die Reihenfolge der Ausführung anzugeben. Zum Erstellen eines der <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> zugeordneten der <xref:System.Activities.Statements.FlowSwitch%601>, klicken Sie auf eines der quadratischen Handles auf dem Umkreis des der **FlowSwitch < T\>**  und ziehen Sie ihn auf einem der Handles (indem Sie die Maustaste gedrückt) die wird auf ähnliche Weise Umrisslinie der Zielaktivität angezeigt, wenn die Maus über ihren Designer bewegt wird. Version die Maustaste gedrückt und ein Pfeil aus der **FlowSwitch < T\>**  zum zieldesigner zeigender angezeigt wird, der diesen Fall darstellt. Der Standardwert für diesen Fall zeigt an, auf den Pfeil und und kann bearbeitet werden, der **Fall** im Feld der **Eigenschaften** Fenster.  
  
### <a name="the-flowswitcht-properties"></a>Die FlowSwitch < T\> Eigenschaften  
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