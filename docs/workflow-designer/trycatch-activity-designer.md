---
title: "TryCatch-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TryCatch.UI"
  - "System.Activities.Statements.Catch`1.UI"
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# TryCatch-Aktivit&#228;tsdesigner
Der **TryCatch**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.TryCatch>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die TryCatch\-Aktivität  
 Die <xref:System.Activities.Statements.TryCatch>\-Aktivität enthält eine <xref:System.Activities.Statements.TryCatch.Try%2A>\-Aktivität, eine **Catch\<TException\>**\-Auflistung und eine <xref:System.Activities.Statements.TryCatch.Finally%2A>\-Aktivität.Ein <xref:System.Activities.Statements.Catch%601>\-Element vom Typ **TException** enthält ein <xref:System.Activities.Statements.Catch%601.ExceptionType%2A>\-Element und ein <xref:System.Activities.Statements.Catch%601.Action%2A>\-Element.Zusammen werden diese verwendet, um einen typischen ausnahmebasierten Fehlerbehandlungsmechanismus zu implementieren.Eine <xref:System.Activities.Statements.TryCatch>\-Aktivität versucht, die zugehörige <xref:System.Activities.Statements.TryCatch.Try%2A>\-Aktivität auszuführen.Wenn die <xref:System.Activities.Statements.TryCatch.Try%2A>\-Aktivität eine Ausnahme auslöst, ordnet die <xref:System.Activities.Statements.TryCatch>\-Aktivität die Ausnahme anhand der **Catch\<TException\>**\-Auflistung zu.Wenn eine Übereinstimmung vorhanden ist, wird das <xref:System.Activities.Statements.Catch%601.Action%2A>\-Element des entsprechenden **Catch\<TException\>**\-Elements ausgeführt und dient als Fehlerbehandlungslogik für die Ausnahme.Wenn die Aktivitäten im Abschnitt <xref:System.Activities.Statements.TryCatch.Try%2A> erfolgreich abgeschlossen werden oder die Aktivitäten in <xref:System.Activities.Statements.TryCatch.Catches%2A> erfolgreich abgeschlossen werden, führt die <xref:System.Activities.Statements.TryCatch>\-Aktivität die zugehörige <xref:System.Activities.Statements.TryCatch.Finally%2A>\-Aktivität aus.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Ausnahmen](../Topic/Exceptions.md).  
  
### Verwenden des TryCatch\-Aktivitätsdesigners  
 Der **TryCatch**\-Aktivitätsdesigner befindet sich in der Kategorie **Fehlerbehandlung** der **Toolbox**, auf die Sie zugreifen, indem Sie im linken Bereich von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Alternativ können Sie **Symbolleiste** im Menü **Ansicht** wählen oder die Tastenkombination STRG\+ALT\+X verwenden.\)  
  
 Sie können den **TryCatch**\-Aktivitätsdesigner aus der **Toolbox** ziehen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche ablegen, wo normalerweise Aktivitäten platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>\-Element.Hierdurch erstellen Sie eine <xref:System.Activities.Statements.TryCatch>\-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>\-Standardwert TryCatch.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **TryCatch**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters geändert werden.Die anderen Eigenschaften müssen auf der Oberfläche des **TryCatch**\-Aktivitätsdesigners bearbeitet werden.  
  
 Klicken Sie in der rechten oberen Ecke im **TryCatch**\-Designer auf die Erweiterungsschaltfläche, um die Felder **Try**, **Catches** und **Finally** in der erweiterten Ansicht anzuzeigen.Um einen Catch hinzuzufügen, klicken Sie im **TryCatch**\-Designer auf die Schaltfläche **Neuen Catch hinzufügen**.Die Schaltfläche nimmt die Form eines Kombinationsfelds an.Wählen Sie einen Ausnahmetyp aus, und drücken Sie die EINGABETASTE, um den Catch hinzuzufügen.Nachdem Sie einen **Catch** hinzugefügt haben, wird der Catch\-Bereich erweitert, und Sie können eine Aktivität im Catch ablegen, um die Ausführungslogik für den Catch zu definieren.Auf der rechten Seite des erweiterten Catch\-Bereichs befindet sich ein Textfeld.In dieses Textfeld können Sie den Namen einer Ausnahmevariablen eingeben.Die Ausnahmevariable kann nur für Aktivitäten im gleichen **Catch** verwendet werden.  
  
 Sie können den **Catch** im **TryCatch**\-Designer nicht bearbeiten.Wenn Sie den Ausnahmetyp ändern möchten, müssen Sie den **Catch** löschen und einen neuen Catch hinzufügen.Um einen **Catch** zu löschen, wählen Sie ihn aus und drücken Sie die ENTF\-Taste, oder klicken Sie mit der rechten Maustaste, und wählen Sie im Kontextmenü die Option **Löschen**.  
  
### Die TryCatch\-Eigenschaften  
 Die folgende Tabelle enthält die <xref:System.Activities.Statements.TryCatch>\-Eigenschaften und eine Beschreibung zu deren Verwendung im Designer.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.TryCatch>\-Aktivität an.Der Standardwert ist "TryCatch".|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Die Aktivität wird erstmalig ausgeführt wird, wenn <xref:System.Activities.Statements.TryCatch> ausgeführt wird.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Die Auflistung von **Catch**\-Elementen, die überprüft werden müssen, wenn die <xref:System.Activities.Statements.TryCatch.Try%2A>\-Aktivität eine Ausnahme auslöst.<br /><br /> Sie müssen mindestens eine Aktivität in der <xref:System.Activities.Statements.TryCatch.Catches%2A>\-Auflistung oder eine Aktivität im <xref:System.Activities.Statements.TryCatch.Finally%2A>\-Block hinzufügen.|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Die Aktivität, die ausgeführt werden soll, wenn die Ausführung von <xref:System.Activities.Statements.TryCatch.Try%2A> und aller erforderlichen Aktivitäten in der <xref:System.Activities.Statements.TryCatch.Catches%2A>\-Auflistung abgeschlossen wurde.<br /><br /> Sie müssen mindestens eine Aktivität in der <xref:System.Activities.Statements.TryCatch.Catches%2A>\-Auflistung oder eine Aktivität im <xref:System.Activities.Statements.TryCatch.Finally%2A>\-Block hinzufügen.|  
  
## Siehe auch  
 [Auflistung](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)