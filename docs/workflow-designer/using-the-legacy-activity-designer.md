---
title: "Verwenden des Aktivit&#228;tsdesigners der Vorg&#228;ngerversion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Aktivitäten, Hinzufügen untergeordneter"
  - "Aktivitäten, Konfigurieren"
  - "Aktivitäten, Erstellen benutzerdefinierter"
  - "Aktivitätsdesigner"
  - "untergeordnete Aktivitäten, hinzufügen"
  - "benutzerdefinierte Aktivitäten"
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Verwenden des Aktivit&#228;tsdesigners der Vorg&#228;ngerversion
In diesem Thema wird beschrieben, wie der Aktivitätsdesigner in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] verwendet wird.Verwenden Sie den Designer der Vorgängerversion, wenn Sie auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.  
  
 Mit dem Aktivitätsdesigner können Sie benutzerdefinierte Aktivitäten erstellen.  
  
## Erstellen einer benutzerdefinierten Aktivität  
 Führen Sie die nachstehenden Schritte aus, um mit dem Aktivitätsdesigner eine benutzerdefinierte Aktivität zu erstellen:  
  
1.  Klicken Sie im Menü **Projekt** auf **Aktivität hinzufügen**.  
  
2.  Wählen Sie die Vorlage **Aktivität** oder **Aktivität \(mit getrenntem Code\)**.  
  
    1.  Erstellen Sie mit der Vorlage **Aktivität** eine Aktivität mit der Aktivitätsdefinition und dem Benutzercode in derselben Codedatei.  
  
    2.  Erstellen Sie mit der Vorlage **Aktivität \(mit getrenntem Code\)** eine Aktivität mit der als Workflowmarkup ausgedrückten Aktivitätsdefinition und dem Benutzercode in einer eigenen Codedatei.  
  
3.  Geben Sie einen Aktivitätsnamen ein, oder behalten Sie den Standardnamen bei, und klicken Sie auf **Hinzufügen**.  
  
 Sie können auch einen Satz benutzerdefinierter Aktivitäten erstellen, indem Sie ein neues Projekt des Typs **Workflow Activity Library** erstellen.Weitere Informationen über diesen Projekttyp finden Sie unter [Vorgehensweise: Erstellen einer Workflowaktivitätsbibliothek \(Vorgängerversion\)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).  
  
## Konfigurieren einer Aktivität  
 Wenn der Aktivitätsdesigner aktiv ist, können Sie mit dem Eigenschaftenbrowser die in der folgenden Tabelle aufgeführten Eigenschaften konfigurieren.  
  
|Eigenschaft|Kommentare|  
|-----------------|----------------|  
|**Name**|Der Name der Aktivität.|  
|**Base Class**|Die Basisklasse, von der die Aktivität abgeleitet wird.Die Standardbasisklasse ist [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)Klicken Sie im Fenster **Eigenschaften** auf die Auslassungspunkte von **Basisklasse\[…\]**, um eine andere Basisklasse im [Dialogfeld '.NET\-Typ suchen und auswählen' \(Vorgängerversion\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) auszuwählen.|  
|**Description**|Die benutzerdefinierte Beschreibung der Aktivität.|  
|**Enabled**|Standardmäßig auf **True** gesetzt, um die Aktivitätsausführung und die Validierung zu aktivieren.Standardmäßig auf **False** gesetzt, um die Aktivitätsausführung und die Validierung zu deaktivieren.Informationen über die Aktivitätsausführung und die Validierung finden Sie unter [Developing Workflow Activities](http://go.microsoft.com/fwlink?LinkID=65024). \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)|  
  
## Hinzufügen von untergeordneten Aktivitäten  
 Sie können untergeordnete Aktivitäten von der Toolbox zu der Aktivität ziehen, die Sie entwerfen.Sie können anschließend jede untergeordnete Aktivität mit dem Eigenschaftenbrowser konfigurieren.  
  
## Siehe auch  
 [Entwickeln von Workflowaktivitäten](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Erstellen von benutzerdefinierten Aktivitäten](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)   
 [Beispiele für benutzerdefinierte Aktivitäten](http://go.microsoft.com/fwlink?LinkID=65022)   
 [Vorgehensweise: Erstellen einer Workflowaktivitätsbibliothek \(Vorgängerversion\)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [Verwenden des Legacyworkflow\-Designers](../workflow-designer/using-the-legacy-workflow-designer.md)