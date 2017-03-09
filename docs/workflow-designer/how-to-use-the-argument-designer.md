---
title: "Vorgehensweise: Verwenden des Argument-Designers | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.ArgumentDesigner.UI"
  - "System.Activities.Presentation.View.DesignTimeArgument.UI"
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Verwenden des Argument-Designers
Verglichen mit früheren Versionen von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], ist es mit dem Argument\-Designer einfach, Daten in eine und aus einer Aktivität fließen zu lassen.Sie greifen auf den Designer zu, indem Sie auf die Schaltfläche **Argumente** in der linken unteren Ecke der Entwurfsfläche klicken.Der Designer enthält eine Liste von Argumenten, die in einer Tabelle angezeigt werden und nach jedem Spaltenkopf sortiert werden können, außer nach der Spalte **Standardwert**.Für jedes Argument werden der Name, die Richtung \(ein\/aus\/ein\/aus\/Eigenschaft\), der Typ und ein Standardausdruckswert \(sofern vorhanden\) angegeben.Der Name und der Standardausdruckswert sind bearbeitbare Textfelder, und der Typ und die Richtung sind Dropdownlisten.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zu Argumenten finden Sie unter [Variablen und Argumente](../Topic/Variables%20and%20Arguments.md).  
  
### So erstellen Sie ein neues Argument  
  
1.  Öffnen Sie in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] eine Workflow\- oder Aktivitätsprojektmappe.  
  
2.  Öffnen Sie den Argument\-Designer, indem Sie auf die Schaltfläche **Argumente** in der linken unteren Ecke der Entwurfsfläche klicken.Der Argument\-Designer wird angezeigt.  
  
3.  Klicken Sie auf die leere Zeile mit der Bezeichnung **Argument erstellen**.Daraufhin wird eine neue Zeile mit einem neuen Argument hinzugefügt, wobei die folgenden Standardwerte verwendet werden: argumentx für den **Namen**, wobei x eine ganze Zahl mit einem Anfangswert von 1 ist, der inkrementiert wird, um automatisch eindeutige Argumentnamen zu erstellen, **In** für die **Richtung** und **Zeichenfolge** für den **Argumenttyp**.Für **Standardwert** wird kein Wert hinzugefügt.Sie können diese Werte jederzeit während des Workflowentwurfs ändern.  
  
    > [!NOTE]
    >  Um ein Argument zu löschen, wählen Sie das Argument aus, indem Sie darauf klicken, und drücken Sie dann die Taste **ENTF**.  
  
## Siehe auch  
 [Verwenden des Workflow\-Designers](../workflow-designer/using-the-workflow-designer.md)   
 [Variablen und Argumente](../Topic/Variables%20and%20Arguments.md)