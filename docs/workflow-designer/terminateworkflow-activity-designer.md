---
title: "TerminateWorkflow-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TerminateWorkflow.UI"
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# TerminateWorkflow-Aktivit&#228;tsdesigner
Der **TerminateWorkflow**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.TerminateWorkflow>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die TerminateWorkflow\-Aktivität  
 Mit der <xref:System.Activities.Statements.TerminateWorkflow>\-Aktivität können Sie die Ausführung eines Workflows beenden.  
  
### Verwenden des TerminateWorkflow\-Aktivitätsdesigners  
 Der **TerminateWorkflow**\-Aktivitätsdesigner befindet sich in der Kategorie **Laufzeit** der **Toolbox**, auf die Sie durch Klicken auf die Registerkarte **Toolbox** zugreifen. \(Alternativ können Sie **Toolbox** im Menü **Ansicht** wählen oder die Tastenkombination STRG\+ALT\+X verwenden.\)  
  
 Sie können den **TerminateWorkflow**\-Aktivitätsdesigner aus der **Toolbox** ziehen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche ablegen, wo normalerweise Aktivitäten platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>\-Element.Hierdurch erstellen Sie eine <xref:System.Activities.Statements.TerminateWorkflow>\-Aktivität mit dem **DisplayName**\-Standardwert TerminateWorkflow.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **TerminateWorkflow**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters geändert werden.  
  
### Die TerminateWorkflow\-Eigenschaften  
 Die folgende Tabelle enthält die <xref:System.Activities.Statements.TerminateWorkflow>\-Eigenschaften und eine Beschreibung zu deren Verwendung im Designer.Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Nein|Der Anzeigename der <xref:System.Activities.Statements.TerminateWorkflow>\-Aktivität.Der Standardwert ist TerminateWorkflow.Der Anzeigename ist zwar nicht unbedingt erforderlich, die Verwendung wird jedoch empfohlen.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Nein|Die Ausnahme, die beim Beenden des Workflows ausgelöst werden soll.Legen Sie diese Eigenschaft im Eigenschaftenraster fest.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Nein|Die Ursache für das Beenden des Workflows.Legen Sie diese Eigenschaft im Eigenschaftenraster fest.|  
  
## Siehe auch  
 [Laufzeit](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)