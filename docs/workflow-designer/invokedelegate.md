---
title: "InvokeDelegate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "InvokeDelegate Designer"
  - "System.Activities.Statements.InvokeDelegate.UI"
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 3
---
# InvokeDelegate
Der **InvokeDelegate**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.InvokeDelegate>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die InvokeDelegate\-Aktivität  
 <xref:System.Activities.Statements.InvokeDelegate> ruft einen öffentlichen Delegaten auf.  
  
### Verwenden des InvokeDelegate\-Aktivitätsdesigners  
 Der **InvokeDelegate**\-Aktivitätsdesigner befindet sich in der Kategorie **Primitives** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **InvokeDelegate**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Daraufhin wird eine <xref:System.Activities.Statements.InvokeDelegate>\-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>\-Standardwert InvokeDelegate erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **InvokeDelegate**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die InvokeDelegate\-Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften von <xref:System.Activities.Statements.InvokeDelegate> gezeigt und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.InvokeDelegate>\-Aktivität.Der Standardwert lautet InvokeDelegate.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Der Name des <xref:System.Activities.Statements.ActivityDelegate>, der bei Ausführung der Aktivität aufgerufen werden soll.Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden.Dies ist eine obligatorische Eigenschaft.|  
|<xref:System.Activities.Statements.InvokeMethod.DelegateArguments%2A>|False|Die Argumentauflistung des aufgerufenen Delegaten.Die Schlüssel sind die Namen der <xref:System.Activities.Statements.ActivityDelegateParameter>\-Objekte auf dem <xref:System.Activities.Statements.ActivityDelegate>, und die Werte sind die Argumente, deren Ausdrücke ausgewertet werden und  den entsprechenden <xref:System.Activities.Statements.ActivityDelegateParameter>\-Objekten zugewiesen werden.Klicken Sie im Eigenschaftenraster im **DelegateArguments**\-Feld auf die Schaltfläche mit den Auslassungspunkten. Daraufhin wird das Dialogfeld **DelegateArguments** angezeigt, in dem Sie diese Eigenschaft festlegen können.Klicken Sie auf das Feld **Argument erstellen**, um die Argumente hinzuzufügen.|  
  
## Siehe auch  
 [Vorgehensweise: Definieren und Verarbeiten von Aktivitätsdelegaten im Workflow\-Designer](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)