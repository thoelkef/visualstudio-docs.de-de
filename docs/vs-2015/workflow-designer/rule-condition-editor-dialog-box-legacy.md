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
ms.openlocfilehash: 00df917b05f5073634b0956a0b44e5b0fc6026a6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846332"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Dialogfeld "Regelbedingungs-Editor" (Vorgängerversion)
In diesem Thema wird beschrieben, wie Sie das Dialogfeld **Regelbedingungs-Editor** in der Legacy-[!INCLUDE[wfd1](../includes/wfd1-md.md)]verwenden. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 Deklarative Regel Bedingungen werden mithilfe des Dialog Felds **Regelbedingungs-Editor** erstellt und geändert. Diese Regelbedingungen werden in den folgenden vordefinierten Windows Workflow Foundation-Aktivitäten als Eigenschaften angegeben:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

  Sie greifen auf das Dialogfeld **Regelbedingungs-Editor** zu, indem Sie das [Dialogfeld Bedingung auswählen (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md)verwenden.

  In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds **Regelbedingungs-Editor** beschrieben.

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Bedingung:**|Geben Sie den Ausdruck für die Regelbedingung ein.|
|**OK**|Klicken Sie, um die Regelbedingung zu speichern.|

## <a name="entering-condition-expressions"></a>Eingeben von Bedingungsausdrücken
 Bedingungsausdrücke werden als Text eingegeben. Sie können **diese eingeben.** , um im Editor auf Felder, Eigenschaften und Methoden zu verweisen, die im Workflow verwendet werden, mit einem IntelliSense-ähnlichen Menü. Alternativ können Sie einen Workflowmembernamen auch direkt eingeben. Sie können logische Operatoren, wie z. B. UND, ODER und NICHT, zur Bedingung hinzufügen. Sie können auch Prädikate hinzufügen. Ein Prädikat besteht aus einem binären Operator und zwei Operanden. Die unterstützten binären Operatoren sind **==** , **>** , **\<** , **>=** und **<=** . Unterstützte Operanden sind konstanter Wert, arithmetische Funktion und geschützte öffentliche Member.

 Sie können den Typ für den Vergleich angeben, und Sie können mit **null** oder einer leeren Zeichenfolge vergleichen. Sie können verschachtelte Aufrufe von Membern für eine Variable durchführen, die einen komplexen Typ enthält, wie z. B. `this.Address.State == "WA"`.

 Der Regelbedingungs-Editor unterstützt die folgenden Operatoren:

- Relationale Operatoren: ==, =, !=

- Vergleichs Operatoren: <, \<=, >, > =

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

  Weitere Informationen zu Bedingungen finden Sie unter [Verwenden von Bedingungen in Workflows](https://msdn2.microsoft.com/library/bb628447.aspx).

## <a name="see-also"></a>Siehe auch
 [Ifelst Activity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelseactivity.aspx) [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx) [replieractivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx) [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx) [Select Condition](../workflow-designer/select-condition-dialog-box-legacy.md) (Dialog Feld Windows Workflow Foundation) [Select Condition ](https://msdn2.microsoft.com/library/bb628447.aspx) [Legacy Designer for Windows Workflow Foundation UI Help](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)
