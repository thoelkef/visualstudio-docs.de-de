---
title: "emoveFromCollection&lt;T&gt;-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.RemoveFromCollection`1.UI"
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# emoveFromCollection&lt;T&gt;-Aktivit&#228;tsdesigner
Der **RemoveFromCollection\<T\>**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.RemoveFromCollection%601>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die RemoveFromCollection\<T\>\-Aktivität  
 Die <xref:System.Activities.Statements.RemoveFromCollection%601>\-Aktivität entfernt ein angegebenes Element aus der angegebenen Auflistung.  
  
### Verwenden des RemoveFromCollection\<T\>\-Aktivitätsdesigners  
 Der **RemoveFromCollection\<T\>**\-Aktivitätsdesigner befindet sich in der Kategorie **Auflistung** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **RemoveFromCollection\<T\>**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitätsdesigner normalerweise platziert werden, z. B. in einer <xref:System.Activities.Statements.Sequence>.Dadurch wird eine <xref:System.Activities.Statements.RemoveFromCollection%601>\-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A>\-Namen RemoveFromCollection\<Int32\> erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **RemoveFromCollection\<T\>**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.Die anderen Eigenschaften müssen im Eigenschaftenraster bearbeitet werden.  
  
### Die RemoveFromCollection\<T\>\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.RemoveFromCollection%601>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.RemoveFromCollection%601>\-Aktivität.Der Standardname lautet RemoveFromCollection\<Int32\>.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht  zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Das Element, das der **Collection\<T\>** hinzugefügt werden soll.Dieses Element hat den Typ *T*, der Typ, den *TypeArgument* besitzt.Geben Sie im Eigenschaftenraster einen Visual Basic\-Ausdruck ein, um das Element anzugeben.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Die Auflistung, zu der das Element hinzugefügt werden soll.Diese Auflistung hat den Typ **ICollection\<TypeArgument\>.** Geben Sie die Auflistung an, indem Sie einen Visual Basic\-Ausdruck im Eigenschaftenraster eingeben.|  
|*TypeArgument*|True|Der Typ T der in der <xref:System.Collections.Generic.ICollection%601> enthaltenen Elemente.Standardmäßig ist der *TypeArgument*\-Typ auf **Int32** festgelegt.Sie ändern den Typ von *TypeArgument*, indem Sie im Kombinationsfeld des Eigenschaftenrasters einen anderen Wert auswählen.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Ein Wert, der angibt, ob das angegebene Element aus der Auflistung entfernt wurde.Um eine Variable anzugeben, die an das Ergebnis gebunden werden soll, geben Sie im Eigenschaftenraster eine Variable ein.|  
  
## Siehe auch  
 [Auflistung](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)