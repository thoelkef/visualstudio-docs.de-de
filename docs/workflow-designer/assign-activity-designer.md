---
title: "Assign-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Assign.UI"
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Assign-Aktivit&#228;tsdesigner
Der **Assign**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.Assign>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die Assign\-Aktivität  
 Die <xref:System.Activities.Statements.Assign>\-Aktivität weist einer Variablen oder einem Argument einen Wert zu.  
  
### Verwenden des Assign\-Aktivitätsdesigners  
 Der **Assign**\-Aktivitätsdesigner befindet sich in der Kategorie **Primitives** der **Toolbox**, auf die Sie durch Klicken auf die Registerkarte **Toolbox** zugreifen. \(Sie können stattdessen auch im Menü **Ansicht** die Option **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **Assign**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Daraufhin wird eine <xref:System.Activities.Statements.Assign>\-Aktivität mit dem **DisplayName**\-Standardwert Assign erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **Assign**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die Assign\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Assign>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.Assign>\-Aktivität an.Der Standardwert lautet Assign.Obwohl der <xref:System.Activities.Activity.DisplayName%2A>\-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|Die Variable oder das Argument, dem der <xref:System.Activities.Statements.Assign.Value%2A> zugewiesen wird.Dies muss ein gültiger Visual Basic\-Bezeichner sein.Um die Eigenschaft festzulegen, geben Sie einen Visual Basic\-Ausdruck im Feld **To** im **Assign**\-Aktivitätsdesigner oder im Eigenschaftenraster ein.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Der der Variablen zugewiesene Wert.Um die <xref:System.Activities.Statements.Assign.Value%2A>\-Eigenschaft festzulegen, geben Sie einen Visual Basic\-Ausdruck im Feld **Wert** im **Assign**\-Aktivitätsdesigner oder im Eigenschaftenraster ein.|  
  
## Siehe auch  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)