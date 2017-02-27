---
title: "FlowDecision-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.FlowDecision.UI"
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# FlowDecision-Aktivit&#228;tsdesigner
Der <xref:System.Activities.Statements.FlowDecision>\-Knoten ist ein bedingter Knoten, der eine Verzweigung für den Steuerungsverlauf in eine von zwei Alternativen bereitstellt, die auf der Erfüllung einer angegebenen Bedingung basiert.Wenn der Verlauf mehr als zwei Verzweigungen erfordert, verwenden Sie stattdessen <xref:System.Activities.Statements.FlowSwitch%601>.  
  
## Der FlowDecision\-Knoten  
 Verwenden Sie <xref:System.Activities.Statements.FlowDecision>, wenn der Verlauf in zwei Pfade verzweigt werden kann.Ein <xref:System.Activities.Statements.FlowDecision>\-Knoten verfügt über ein <xref:System.Activities.Statements.FlowDecision.Condition%2A>\-Objekt und ein <xref:System.Activities.Statements.FlowNode>\-Objekt, das den beiden möglichen Ergebnissen zugeordnet ist: <xref:System.Activities.Statements.FlowDecision.True%2A> oder <xref:System.Activities.Statements.FlowDecision.False%2A>.Die <xref:System.Activities.Statements.FlowDecision.Condition%2A>\-Instanz wird ausgewertet, und der Wert dieser Auswertung bestimmt, welcher <xref:System.Activities.Statements.FlowNode>\-Knoten als Nächstes innerhalb des <xref:System.Activities.Statements.Flowchart>\-Flussdiagramms verarbeitet werden soll.  
  
### Verwenden des FlowDecision\-Designers  
 Der **FlowDecision**\-Designer befindet sich in der Kategorie **Flussdiagramm** der **Toolbox**, auf die Sie durch Klicken auf die Registerkarte **Toolbox** im [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] zugreifen können. \(Stattdessen können Sie auch im Menü **Ansicht** die Option **Toolbox** wählen oder STRG\+ALT\+X drücken.\)  
  
 Der **FlowDecision**\-Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche innerhalb eines **Flowchart**\-Aktivitätsdesigners abgelegt werden.Daraufhin wird eine <xref:System.Activities.Statements.FlowDecision>\-Aktivität mit der Bezeichnung **Decision** in der <xref:System.Activities.Statements.Flowchart>\-Aktivität erstellt.Wenn Sie die Maus über den Designer halten, werden die quadratische Handles **True** und **False** für die beiden Verzweigungen angezeigt.  
  
 Die Knoten können miteinander verknüpft werden, um die Reihenfolge der Ausführung anzugeben, nachdem Sie den **FlowDecision**\-Designer und andere Designer auf das **Flussdiagramm** gezogen haben.Um einen Link zwischen einem Quellknoten \(einschließlich der Verzweigungen **True** und  **False** von **FlowDecision**\) und einem Zielknoten zu erstellen, halten Sie den Mauszeiger über den Designer für den Quellknoten. Daraufhin werden auf beiden Seiten des Knotens quadratische Handles angezeigt.Klicken Sie auf eines der quadratischen Handles, und ziehen Sie es mit gedrückter Maustaste zu einem der Handles, die in ähnlicher Weise um den Zielknoten angezeigt werden, wenn Sie den Mauszeiger darüber halten.Lassen Sie die Maustaste los. Daraufhin wird zwischen beiden Knoten einen Link erstellt, der als vom Quelldesigner zum Zieldesigner zeigender Pfeil dargestellt wird.  
  
 Der Ausdruck, der angibt, dass der <xref:System.Activities.Statements.FlowDecision.Condition%2A>\-Wert im Feld **Bedingung** des Fensters **Eigenschaften** eingegeben werden kann, indem Sie dorthin klicken, wo der Hinweistext "VB\-Ausdruck eingeben" angezeigt wird.  
  
### Die FlowDecision\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.FlowDecision>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster oder in der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|Die Bedingung, die bestimmt, welchen Pfad die Flusssteuerung einschlägt.|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Der von der Flusssteuerung eingeschlagene Pfad, wenn die <xref:System.Activities.Statements.FlowDecision.Condition%2A>\-Bedingung erfüllt wird.|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Der von der Flusssteuerung eingeschlagene Pfad, wenn die <xref:System.Activities.Statements.FlowDecision.Condition%2A>\-Bedingung nicht erfüllt wird.|  
  
## Siehe auch  
 [Flussdiagramm](../workflow-designer/flowchart-activity-designers.md)   
 [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T\>](../workflow-designer/flowswitch-t-activity-designer.md)