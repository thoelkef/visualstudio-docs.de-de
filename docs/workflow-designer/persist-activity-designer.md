---
title: "Persist-Aktivit&#228;tsdesigners | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Persist.UI"
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Persist-Aktivit&#228;tsdesigners
Der **Persist**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.Persist>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die Persist\-Aktivität  
 Wenn möglich, speichert die <xref:System.Activities.Statements.Persist>\-Aktivität einen Workflow auf dem Datenträger.Die <xref:System.Activities.Statements.Persist>\-Aktivität kann nicht in einem Bereich ohne Persistenz ausgeführt werden, z. B. innerhalb einer <xref:System.Activities.Statements.TransactionScope>\-Aktivität.Wenn Sie eine <xref:System.Activities.Statements.Persist>\-Aktivität in einem Bereich ohne Persistenz verwenden, wird zur Laufzeit eine Ausnahme ausgelöst.  
  
### Verwenden des Persist\-Aktivitätsdesigners  
 Der **Persist**\-Aktivitätsdesigner befindet sich in der Kategorie **Laufzeit** der **Toolbox**, auf die Sie durch Klicken auf die Registerkarte **Toolbox** zugreifen. \(Sie können stattdessen auch im Menü **Ansicht** die Option **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **Persist**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Daraufhin wird eine <xref:System.Activities.Statements.Persist>\-Aktivität mit dem **DisplayName**\-Standardwert Persist erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **Persist**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die Persist\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Persist>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den Anzeigenamen der <xref:System.Activities.Statements.Persist>\-Aktivität an.Der Standardwert lautet Persist.Obwohl der Anzeigename nicht unbedingt erforderlich ist, ist es eine Best Practice, einen Anzeigenamen zu verwenden.|  
  
## Siehe auch  
 [Laufzeit](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)