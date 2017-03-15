---
title: "Rethrow-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Rethrow.UI"
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Rethrow-Aktivit&#228;tsdesigner
Der **Rethrow**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.Rethrow>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die Rethrow\-Aktivität  
 Die <xref:System.Activities.Statements.Rethrow>\-Aktivität löst eine zuvor ausgelöste Ausnahme aus.Diese Aktivität kann nur in einem <xref:System.Activities.Statements.Catch>\-Handler in der <xref:System.Activities.Statements.TryCatch> \-Aktivität verwendet werden.  
  
### Verwenden des Rethrow\-Aktivitätsdesigners  
 Der **Rethrow**\-Aktivitätsdesigner befindet sich in der Kategorie **Fehlerbehandlung** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **Rethrow**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Daraufhin wird eine <xref:System.Activities.Statements.Rethrow>\-Aktivität mit dem **DisplayName**\-Standardwert Rethrow erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **Rethrow**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die Rethrow\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Rethrow>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.ReThrow>\-Aktivität an.Der Standardwert lautet Rethrow.|  
  
## Siehe auch  
 [Auflistung](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)