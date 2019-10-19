---
title: Regelbedingungs-Editor (Dialog Feld) (Legacy) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 93aef1e4466bd88d87ebce71161dcd1665178317
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663349"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Dialogfeld "Regelbedingungs-Editor" (Vorgängerversion)
In diesem Thema wird beschrieben, wie Sie das Dialogfeld **Regelbedingungs-Editor** in der Legacy-[!INCLUDE[wfd1](../includes/wfd1-md.md)] verwenden. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 Deklarative Regel Bedingungen werden mithilfe des Dialog Felds **Regelbedingungs-Editor** erstellt und geändert. Diese Regelbedingungen werden in den folgenden vordefinierten Windows Workflow Foundation-Aktivitäten als Eigenschaften angegeben:

- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

  Sie greifen auf das Dialogfeld **Regelbedingungs-Editor** zu, indem Sie das [Dialogfeld Bedingung auswählen (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md)verwenden.

  In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds **Regelbedingungs-Editor** beschrieben.

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Anlage**|Geben Sie den Ausdruck für die Regelbedingung ein.|
|**Okay**|Klicken Sie, um die Regelbedingung zu speichern.|

## <a name="entering-condition-expressions"></a>Eingeben von Bedingungsausdrücken
 Bedingungsausdrücke werden als Text eingegeben. Sie können **diese eingeben.** , um im Editor auf Felder, Eigenschaften und Methoden zu verweisen, die im Workflow verwendet werden, mit einem IntelliSense-ähnlichen Menü. Alternativ können Sie einen Workflowmembernamen auch direkt eingeben. Sie können logische Operatoren, wie z. B. UND, ODER und NICHT, zur Bedingung hinzufügen. Sie können auch Prädikate hinzufügen. Ein Prädikat besteht aus einem binären Operator und zwei Operanden. Die unterstützten binären Operatoren sind **==** , **>** , **\<** , **>=** und **<=** . Unterstützte Operanden sind konstanter Wert, arithmetische Funktion und geschützte öffentliche Member.

 Sie können den Typ für den Vergleich angeben, und Sie können mit **null** oder einer leeren Zeichenfolge vergleichen. Sie können verschachtelte Aufrufe von Membern für eine Variable durchführen, die einen komplexen Typ enthält, wie z. B. `this.Address.State == "WA"`.

 Der Regelbedingungs-Editor unterstützt die folgenden Operatoren:

- Relationale Operatoren: ==, =, !=

- Vergleichs Operatoren: <, \< =, >, > =

- Arithmetische Operatoren: +, - , *, /, MOD

- Logische Operatoren: and, & & oder, &#124; &#124;, not,!

- Bitweise Operatoren: &&#124;

  Ausdrucksoperatorvorrang folgt C#-Operator-Vorrangregeln.

  Der Regelbedingungs-Editor unterstützt die folgenden numerischen Ausdrücke:

  this.i == 1D (wird zu 1.0 aufgelöst)

  this.i == 1E1 (wird zu 10.0 aufgelöst)

  this.i == 1L (wird zu einem long-Wert aufgelöst)

  this.i == 1M (wird zu einem decimal-Wert aufgelöst)

  this.i == 1F (wird zu einem single-Wert aufgelöst)

  this.i == 1U (wird zu einem vorzeichenlosen int-Wert aufgelöst)

  Weitere Informationen zu Bedingungen finden Sie unter [Verwenden von Bedingungen in Workflows](http://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Siehe auch
 [Ifelst Activity](http://go.microsoft.com/fwlink?LinkID=65033) [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) [replieractivity](http://go.microsoft.com/fwlink?LinkID=65039) [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049) [Select Condition Dialog Feld (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md) [Verwenden von Bedingungen in Workflows](http://go.microsoft.com/fwlink?LinkID=65009) [Legacy-Designer für Windows Workflow Hilfe zu Foundation-UI](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)