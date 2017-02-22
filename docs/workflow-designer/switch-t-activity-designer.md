---
title: "Switch&lt;T&gt;-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.ModelItemKeyValuePair.UI"
  - "System.Activities.Statements.Switch`1.UI"
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
caps.handback.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Switch&lt;T&gt;-Aktivit&#228;tsdesigner
Die <xref:System.Activities.Statements.Switch%601>\-Aktivität wertet einen angegebenen Ausdruck aus und führt diejenige Aktivität aus einer Auflistung von Aktivitäten aus, deren zugeordneter Schlüssel dem Wert entspricht, der aus der Auswertung hervorging.  
  
 Der **Switch\<T\>**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.Switch%601>\-Aktivität im [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] zu erstellen und zu konfigurieren.  
  
## Die Switch\<T\>\-Aktivität  
 Eine <xref:System.Activities.Statements.Switch%601>\-Aktivität enthält einen <xref:System.Activities.Statements.Switch%601.Expression%2A>\-Ausdruck und ein Wörterbuch von <xref:System.Activities.Statements.Switch%601.Cases%2A>\-Fällen.Jeder Fall im Wörterbuch besteht aus einem Paar, das einen *key*\-Schlüssel und eine Aktivität enthält, die als zugehöriger *value*\-Wert dient.Die <xref:System.Activities.Statements.Switch%601>\-Aktivität wertet den <xref:System.Activities.Statements.Switch%601.Expression%2A>\-Ausdruck aus und vergleicht ihn mit jedem Schlüssel.Wenn eine Übereinstimmung gefunden wird, wird die entsprechende Aktivität ausgeführt.Nur eine Übereinstimmung ist möglich, da die Wörterbuchschlüssel entsprechend der vom Gleichheitsvergleich des Wörterbuchs definierten Gleichheit eindeutig sein müssen.Wenn keine Übereinstimmung gefunden wird, wird die <xref:System.Activities.Statements.Switch%601.Default%2A>\-Aktivität ausgeführt.  
  
## So verwenden Sie den Switch\<T\>\-Aktivitätsdesigner  
 Der **Switch\<T\>**\-Aktivitätsdesigner befindet sich in der Kategorie **Ablaufsteuerung** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\) Nachdem die Aktivität im [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] abgelegt wurde, wird das Dialogfeld **Typen auswählen** angezeigt, damit der Benutzer den generischen Typ *T* angeben kann, der in der <xref:System.Activities.Statements.Switch%601>\-Aktivität verwendet werden soll.Der Standardwert ist **Int32**.Sobald der generische Typ *T* ausgewählt wurde, wird ein **Switch\-\<T\>**\-Designer dem Workflow\-Designer hinzugefügt.  
  
 Nachfolgend werden die Eigenschaften des **Switch\-\<T\>**\-Designers beschrieben.Alle diese Eigenschaften können im Eigenschaftenraster bearbeitet werden.Einige von ihnen können auch in der Designeroberfläche bearbeitet werden.  
  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.Switch%601>\-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen des <xref:System.Activities.Statements.Switch%601>\-Aktivitätsdesigners an.Der Standardwert ist Switch\<Int32\>.Der Wert kann im Fenster **Eigenschaften** oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Gibt den Ausdruck an, mit dem die Schlüssel in der Auflistung der Fälle verglichen wurden, um zu bestimmen, welcher Fall auszuführen ist.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Gibt die Aktivität an, die ausgeführt werden soll, wenn keine Übereinstimmung gefunden wird.Klicken Sie im Designer auf die Schaltfläche **Aktivität hinzufügen**, um das Feld **Standard** zu öffnen, in dem die Aktivität abgelegt werden kann.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Gibt die Fälle an, die ausgewertet werden sollen.Um einen Fall hinzuzufügen, klicken Sie auf die Schaltfläche **Neuen Fall hinzufügen** am unteren Rand des **Switch\-\<T\>**\-Designers.Die Schaltfläche ändert sich in ein Textfeld \(Kombinationsfeld, wenn der generische Typ String oder Enum beim Hinzufügen der Switch\<T\>\-Aktivität ausgewählt wurde\).Nachdem dem Feld **Case\-Wert** ein Schlüssel hinzugefügt wurde, wird der Case\-Bereich erweitert und es kann eine Aktivität im Bereich mit dem Hinweistext "Aktivität hier ablegen" abgelegt werden, um die Ausführungslogik für diesen Fall zu definieren.|  
  
 Solange keine doppelten Fallschlüssel vorkommen, können mehrere Fälle hinzugefügt werden.Andernfalls wird ein Fehlerdialogfeld mit der Meldung angezeigt, dass der angegebene Fallschlüssel bereits vorhanden ist und dass Sie einen anderen Schlüssel auswählen müssen.Im **Switch\-\<T\>**\-Designer können zu einem gegebenen Zeitpunkt nicht mehrere case\-Bereiche erweitert werden.Wenn ein case\-Bereich reduziert angezeigt wird, klicken Sie auf den case\-Bereich, um ihn zu erweitern.Beachten Sie, dass der Designer bei einem reduzierten case\-Bereich den Anzeigenamen der Aktivität rechts neben dem Bereich anzeigt, sofern eine Aktivität vorhanden ist.Andernfalls wird die Schaltfläche **Aktivität hinzufügen** angezeigt. Wenn Sie darauf klicken, wird der case\-Bereich erweitert, und Sie können eine Aktivität hinzufügen.  
  
 Wenn Sie auf den Schlüssel eines vorhandenen Falls klicken, wird der Schlüssel von einer Bezeichnung in ein Textfeld geändert, damit Sie den Fallschlüssel bearbeiten können.  
  
 Es gibt zwei Möglichkeiten, einen Fall zu löschen:  
  
1.  Wählen Sie den Fall aus, und löschen Sie ihn.  
  
2.  Markieren Sie den Fall, drücken Sie rechte Maustaste, um das Kontextmenü anzuzeigen, und wählen Sie den Befehl **Löschen** aus.  
  
 Beachten Sie, dass Sie den Fall selbst markieren müssen, um ihn zu löschen.Wenn Sie die Aktivität in einem Fall markieren und löschen, wird nur Aktivität, nicht der Fall gelöscht.  
  
## Siehe auch  
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)