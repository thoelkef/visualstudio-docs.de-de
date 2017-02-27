---
title: "FlowSwitch&lt;T&gt;-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Core.Presentation.FlowSwitchLink.UI"
  - "System.Activities.Statements.FlowSwitch`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLink`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI"
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# FlowSwitch&lt;T&gt;-Aktivit&#228;tsdesigner
Die <xref:System.Activities.Statements.FlowSwitch%601>\-Aktivität ist ein bedingter Knoten, der eine Verzweigung auf der Grundlage von Übereinstimmungskriterien für den Steuerungsverlauf bereitstellt, wenn mehr als zwei alternative Verzweigungen erforderlich sind.Wenn der Steuerungsverlauf nur zwei Pfade erfordert, verwenden Sie stattdessen die <xref:System.Activities.Statements.FlowDecision>\-Aktivität.  
  
## Die FlowSwitch\<T\>\-Aktivität  
 Die <xref:System.Activities.Statements.FlowSwitch%601>\-Aktivität enthält einen <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>\-Ausdruck, der einen Wert des Typs *T* \(der im generischen Parameter angegeben wird\) zurückgibt, wenn er ausgewertet wird.Die Aktivität enthält auch einen Satz von <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>\-Fällen, der eine eindeutige Zuordnung von möglichen Ergebnissen dieser Auswertung zu einem Satz von <xref:System.Activities.Statements.FlowNode>\-Objekten angibt.Es wird der <xref:System.Activities.Statements.FlowNode>\-Knoten ausgeführt, dessen Objekt des Typs *T* dem Wert des ausgewerteten <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>\-Ausdrucks entspricht.Ein <xref:System.Activities.Statements.FlowSwitch%601.Default%2A>\-Fall kann \(optional\) für den Fall bereitgestellt werden, in dem keine Übereinstimmung gefunden wird.  
  
### Verwenden des FlowSwitch\<T\>\-Aktivitätsdesigners  
 Der **FlowSwitch\<T\>**\-Aktivitätsdesigner befindet sich in der Kategorie **Flowchart** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **FlowSwitch\<T\>**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen werden und in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche innerhalb eines **Flowchart**\-Aktivitätsdesigners abgelegt werden.Verwenden Sie das angezeigte Fenster **Typen auswählen**, um den Typ zuzuordnen \(der im Code mit dem <xref:System.Activities.Statements.FlowSwitch%601> durch den generischen Parameter zugeordnet wird\), der aus der Auswertung von <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> resultiert.Damit wird eine <xref:System.Activities.Statements.Flowchart>\-Aktivität mit der Bezeichnung **Switch** in der <xref:System.Activities.Statements.FlowSwitch%601>\-Aktivität erstellt.Der <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>\-Ausdruck kann im Feld **Ausdruck** des Fensters **Eigenschaften** eingegeben werden, indem auf die Stelle geklickt wird, an der der Hinweistext "VB\-Ausdruck eingeben" erscheint.  
  
 Bewegen Sie den Mauszeiger über den **FlowSwitch\<T\>**\-Aktivitätsdesigner, damit an seinen Rändern die quadratischen Handles angezeigt werden, die verwendet werden, um Links für <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> zu definieren.Nachdem der **FlowSwitch\<T\>**\-Aktivitätsdesigner und andere Aktivitätsdesigner in das **Flussdiagramm** gezogen wurden, können die <xref:System.Activities.Activity>\-Objekte, welche sie darstellen, miteinander verknüpft werden, um die Ausführungsreihenfolge festzulegen.Um einen der <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>\-Fälle zu erstellen, der dem <xref:System.Activities.Statements.FlowSwitch%601>\-Objekt zugeordnet ist, klicken Sie auf eines der quadratischen Fallhandles auf der Umrisslinie des **FlowSwitch\-\<T\>**\-Elements und ziehen Sie es \(bei gedrückter Maustaste\) zu einem der Handles, die auf der Umrisslinie der Zielaktivität angezeigt werden, wenn der Mauszeiger auf den Aktivitätsdesigner zeigt.Lassen Sie die Maustaste los. Daraufhin wird ein vom **FlowSwitch\-\<T\>**\-Element zum Ziel\-Designer gerichteter Pfeil angezeigt, der diesen Fall darstellt.Der Standardwert für diesen Fall wird auf dem Pfeil angezeigt und kann im Feld **Fall** des Fensters **Eigenschaften** bearbeitet werden.  
  
### Die FlowSwitch\-\<T\>\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.FlowSwitch%601>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster oder in der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Gibt den Ausdruck an, der ausgewertet wird, um zu bestimmen, zu welchem der <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>\-Fälle im Ausführungspfad gewechselt werden soll.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Gibt eine eindeutige Zuordnung von möglichen Ergebnissen an, die durch die Auswertung von <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> für einen Satz von <xref:System.Activities.Statements.FlowNode>\-Objekten ermittelt wurden.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Gibt die Zuordnung an, wenn das Auswertungsergebnis von <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> mit keinem der Werte übereinstimmt, die im <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>\-Objekt enthalten sind.|  
  
## Siehe auch  
 [Flussdiagramm](../workflow-designer/flowchart-activity-designers.md)   
 [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)