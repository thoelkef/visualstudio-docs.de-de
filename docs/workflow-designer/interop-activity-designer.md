---
title: "Interop-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Interop.UI"
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Interop-Aktivit&#228;tsdesigner
Der **Interop**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.Interop>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die Interop\-Aktivität  
 Die <xref:System.Activities.Statements.Interop>\-Aktivität verwaltet die Ausführung von Typen, die sich von <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> innerhalb eines Workflows ableiten.  
  
### Verwenden des Interop\-Aktivitätsdesigners  
 Der **Interop**\-Aktivitätsdesigner befindet sich in die Kategorie **Migration** der **Toolbox**, auf die Sie durch Klicken auf die Registerkarte **Toolbox** zugreifen können. \(Sie können stattdessen auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X.\)  
  
 Die Kategorie [Migration](../workflow-designer/migration-activity-designers.md), die die <xref:System.Activities.Statements.Interop>\-Aktivität enthält, wird nur dann in der **Toolbox** angezeigt, wenn das Projekt [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] als Zielplattform hat.  
  
 Bei C\#\-Projekte können Sie [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] als Zielplattform festlegen, indem Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt klicken und **Eigenschaften** auswählen.Aktivieren Sie auf der Registerkarte **Anwendung** unter **Zielframework** die Option die **.NET Framework 4**.Wählen Sie die Schaltfläche **Ja** im Dialogfeld **Änderung des Zielframeworks** aus, in dem Sie aufgefordert werden, diese Änderung zu bestätigen.  
  
 Bei VB\-Projekte können Sie [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] als Zielplattform festlegen, indem Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt klicken und **Eigenschaften** auswählen.Klicken Sie auf der Registerkarte **Kompilieren** auf die Schaltfläche **Erweiterte Kompilierungsoptionen**.Wählen Sie unter **Zielframeworkliste** die Option **.NET Framework 4** aus, und klicken Sie dann auf **OK**.Klicken Sie auf die Schaltfläche **Ja** im Dialogfeld **Änderung des Zielframeworks**, in dem Sie aufgefordert werden, diese Änderung zu bestätigen.  
  
 Der **Interop**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Daraufhin wird eine <xref:System.Activities.Statements.Interop>\-Aktivität mit dem **DisplayName**\-Standardwert Interop erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **Interop**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
 Klicken Sie entweder im **Interop** \-Aktivitätsdesigner oder im Eigenschaftenraster im Feld **ActivityType** auf den Text **Zum Durchsuchen klicken**, um das Dialogfeld **.NET\-Typ suchen und auswählen** zu öffnen.Nur Typen für Workflow 3.0\- oder Workflow 3.5\-Aktivitäten werden angezeigt \(d. h., nur Typen, die von <xref:System.Workflow.ComponentModel.Activity> abgeleitet sind\).[!INCLUDE[crabout](../test/includes/crabout_md.md)] zur Verwendung dieses Dialogfelds zum Angeben eines Typs finden Sie im Thema [Dialogfeld '.NET\-Typ suchen und auswählen'](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).  
  
### Die Interop\-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Interop>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster oder in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den Anzeigenamen der <xref:System.Activities.Statements.Interop>\-Aktivität an.Der Standardwert lautet Interop.Obwohl der Anzeigename nicht unbedingt erforderlich ist, ist es eine Best Practice, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Gibt den Typ der in der <xref:System.Activities.Statements.Interop>\-Aktivität enthaltenen Aktivität an.Der angegebene Typ muss von <xref:System.Workflow.ComponentModel.Activity> abgeleitet sein.|  
  
## Siehe auch  
 [Migration](../workflow-designer/migration-activity-designers.md)