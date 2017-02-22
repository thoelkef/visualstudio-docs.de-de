---
title: "Dialogfeld &quot;Regelbedingungs-Editor&quot; (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI"
helpviewer_keywords: 
  - "Regelbedingungs-Editor (Dialogfeld)"
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dialogfeld &quot;Regelbedingungs-Editor&quot; (Vorg&#228;ngerversion)
In diesem Thema wird die Verwendung des Dialogfelds **Regelbedingungs\-Editor** in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] beschrieben.Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.  
  
 Sie erstellen und ändern deklarative Regelbedingungen mit dem Dialogfeld **Regelbedingungs\-Editor**.Diese Regelbedingungen werden in den folgenden vordefinierten Windows Workflow Foundation\-Aktivitäten als Eigenschaften angegeben:  
  
-   [ConditionedActivityGroup  \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity  \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity  \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity  \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity  \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65045)  
  
 Sie greifen auf das Dialogfeld **Regelbedingungs\-Editor** mit dem [Dialogfeld "Regelbedingungs\-Editor auswählen" \(Vorgängerversion\)](../workflow-designer/select-condition-dialog-box-legacy.md) zu.  
  
 In der folgenden Tabelle werden die Benutzeroberflächenelemente des Dialogfelds **Regelbedingungs\-Editor** beschrieben.  
  
|Benutzeroberflächenelement|Beschreibung|  
|--------------------------------|------------------|  
|**Bedingung:**|Geben Sie den Ausdruck für die Regelbedingung ein.|  
|**OK**|Klicken Sie, um die Regelbedingung zu speichern.|  
  
## Eingeben von Bedingungsausdrücken  
 Bedingungsausdrücke werden als Text eingegeben.Sie können **this.** in den Editor eingeben, um auf im Workflow verwendete Felder, Eigenschaften und Methoden zu verweisen. Hierfür wird ein IntelliSense\-ähnliches Menü verwendet.Alternativ können Sie einen Workflowmembernamen auch direkt eingeben.Sie können logische Operatoren, wie z. B. UND, ODER und NICHT, zur Bedingung hinzufügen.Sie können auch Prädikate hinzufügen.Ein Prädikat besteht aus einem binären Operator und zwei Operanden.Es werden die binären Operatoren **\=\=**, **\>**, **\<**, **\>\=** und **\<\=** unterstützt.Unterstützte Operanden sind konstanter Wert, arithmetische Funktion und geschützte öffentliche Member.  
  
 Sie können den Typ für den Vergleich angeben, und Sie können mit **null** oder einer leeren Zeichenfolge vergleichen.Sie können verschachtelte Aufrufe von Membern für eine Variable durchführen, die einen komplexen Typ enthält, wie z. B. `this.Address.State == "WA"`.  
  
 Der Regelbedingungs\-Editor unterstützt die folgenden Operatoren:  
  
-   Relationale Operatoren: \=\=, \=, \!\=  
  
-   Vergleichsoperatoren: \<, \<\=, \>, \>\=  
  
-   Arithmetische Operatoren: \+, \- , \*, \/, MOD  
  
-   Logische Operatoren: UND, &&, ODER, &#124;&#124;, NICHT, \!  
  
-   Bitweise Operatoren: &, &#124;  
  
 Ausdrucksoperatorvorrang folgt C\#\-Operator\-Vorrangregeln.  
  
 Der Regelbedingungs\-Editor unterstützt die folgenden numerischen Ausdrücke:  
  
 this.i \=\= 1D \(wird zu 1.0 aufgelöst\)  
  
 this.i \=\= 1E1 \(wird zu 10.0 aufgelöst\)  
  
 this.i \=\= 1L \(wird zu einem long\-Wert aufgelöst\)  
  
 this.i \=\= 1M \(wird zu einem decimal\-Wert aufgelöst\)  
  
 this.i \=\= 1F \(wird zu einem single\-Wert aufgelöst\)  
  
 this.i \=\= 1U \(wird zu einem vorzeichenlosen int\-Wert aufgelöst\)  
  
 Weitere Informationen zu Bedingungen finden Sie unter [Using Conditions in Workflows](http://go.microsoft.com/fwlink?LinkID=65009). \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)  
  
## Siehe auch  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Dialogfeld "Regelbedingungs\-Editor auswählen" \(Vorgängerversion\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Verwenden der Bedingungen in Workflows](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Benutzeroberflächenhilfe von Visual Studio Designer für Windows Workflow Foundation \(Vorgängerversion\)](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)