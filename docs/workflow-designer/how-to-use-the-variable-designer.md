---
title: "Vorgehensweise: Verwenden des Variablen-Designers | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.DesignTimeVariable.UI"
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 14
caps.handback.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Verwenden des Variablen-Designers
Der Variablen\-Designer dient zum Erstellen von Variablen in Datenbindungsszenarios und bedingten Anweisungen.Zum Öffnen dieses Designers klicken Sie in der unteren linken Ecke des Zeichenbereichs auf **Variablen**.Der Designer enthält eine Liste von Variablen, die in einer Tabelle angezeigt werden und nach jedem Spaltenkopf sortiert werden können, außer nach der Spalte **Standard**.Jede Variable verfügt über einen Namen, einen Variablentyp, einen Gültigkeitsbereich und ggf. über einen Standardwert.Der Name und der Standardwert sind bearbeitbare Textfelder, der Typ und der Gültigkeitsbereich sind Dropdownlisten.Der Gültigkeitsbereich entspricht der Aktivität, die beim Aufrufen des Variablen\-Designers ausgewählt wurde.Wenn eine Variable innerhalb des Gültigkeitsbereichs der Auswahl nicht erstellt werden kann, wird standardmäßig der Gültigkeitsbereich der nächsten Vorgängeraktivität der Auswahl verwendet, in dem die Variable erstellt werden kann.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zu Variablen finden Sie unter [Variablen und Argumente](../Topic/Variables%20and%20Arguments.md).  
  
 Die Sortierreihenfolge wird erst übernommen, wenn der Benutzer eines der Sortiersteuerelemente explizit verwendet, den Variablen\-Designer schließt und erneut öffnet oder eine andere Variable erstellt.  
  
### So erstellen Sie eine neue Variable  
  
1.  Öffnen Sie in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] eine Workflow\- oder eine Aktivitätsprojektmappe.  
  
2.  Wählen Sie im Zeichenbereich eine Aktivität im Workflow aus.  
  
3.  Öffnen Sie den Variablen\-Designer, indem Sie in der unteren linken Ecke des Zeichenbereichs auf **Variablen** klicken.Der Variablen\-Designer wird angezeigt.  
  
4.  Klicken Sie auf die leere Zeile mit der Bezeichnung **Variable erstellen**.Hierdurch wird eine neue Zeile mit einer neuen Variable und den folgenden Standardwerten hinzugefügt: Der **Name** ist variablex, wobei x eine ganze Zahl mit dem Anfangswert 1 darstellt, der zur Erstellung eindeutiger Variablennamen automatisch erhöht wird, der **Variablentyp** ist **String**, und der **Bereich** ist **Sequence**.Für **Standardwert** wird kein Wert hinzugefügt.Sie können diese Werte jederzeit während des Workflowentwurfs ändern.  
  
    > [!NOTE]
    >  Um eine Variable zu löschen, wählen Sie die Variable aus, indem Sie darauf klicken, und drücken Sie dann die Taste **ENTF**.  
  
## Siehe auch  
 [Verwenden des Workflow\-Designers](../workflow-designer/using-the-workflow-designer.md)   
 [Variablen und Argumente](../Topic/Variables%20and%20Arguments.md)   
 [Vorgehensweise: Verwenden des Argument\-Designers](../workflow-designer/how-to-use-the-argument-designer.md)