---
title: "Throw-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Throw.UI"
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Throw-Aktivit&#228;tsdesigner
Der **Throw**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.Throw>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die Throw\-Aktivität  
 Die <xref:System.Activities.Statements.Throw>\-Aktivität löst eine Ausnahme aus.  
  
### Verwenden des Throw\-Aktivitätsdesigners  
 Der **Throw**\-Aktivitätsdesigner befindet sich in der Kategorie **Fehlerbehandlung** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **Throw**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Daraufhin wird eine <xref:System.Activities.Statements.Throw>\-Aktivität mit dem **DisplayName**\-Standardwert Throw erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **Throw**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.Diese <xref:System.Activities.Statements.Throw.Exception%2A>\-Eigenschaft muss im Eigenschaftenraster bearbeitet werden.  
  
### Die Throw\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Throw>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Throw>\-Aktivität an.Der Standardwert lautet Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Die auszulösende Ausnahme.Diese Ausnahme muss sich von <xref:System.Exception> ableiten.Geben Sie im Eigenschaftenraster einen Visual Basic\-Ausdruck ein, um die Ausnahme anzugeben.|  
  
## Siehe auch  
 [Auflistung](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw Activity Designer](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)