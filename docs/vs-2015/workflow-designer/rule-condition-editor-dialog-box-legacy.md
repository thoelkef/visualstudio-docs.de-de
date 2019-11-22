---
title: Rule Condition Editor Dialog Box (Legacy) | Microsoft Docs
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
ms.openlocfilehash: a632b90e89e58c26ec72083fe3f4ed9223826dae
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302853"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Dialogfeld "Regelbedingungs-Editor" (Vorgängerversion)
This topic describes how use the **Rule Condition Editor** dialog box in the legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 You create and modify declarative rule conditions by using the **Rule Condition Editor** dialog box. Diese Regelbedingungen werden in den folgenden vordefinierten Windows Workflow Foundation-Aktivitäten als Eigenschaften angegeben:

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

  You access the **Rule Condition Editor** dialog box by using the [Select Condition Dialog Box (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).

  The following table describes the user interface (UI) elements of the **Rule Condition Editor** dialog box.

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Condition:**|Geben Sie den Ausdruck für die Regelbedingung ein.|
|**OK**|Klicken Sie, um die Regelbedingung zu speichern.|

## <a name="entering-condition-expressions"></a>Eingeben von Bedingungsausdrücken
 Bedingungsausdrücke werden als Text eingegeben. You can type **this.** into the editor to reference fields, properties, and methods used in the workflow, using an IntelliSense-like menu. Alternativ können Sie einen Workflowmembernamen auch direkt eingeben. Sie können logische Operatoren, wie z. B. UND, ODER und NICHT, zur Bedingung hinzufügen. Sie können auch Prädikate hinzufügen. Ein Prädikat besteht aus einem binären Operator und zwei Operanden. The binary operators supported are **==** , **>** , **\<** , **>=** , and **<=** . Unterstützte Operanden sind konstanter Wert, arithmetische Funktion und geschützte öffentliche Member.

 You can specify the type for the comparison, and you can compare to **null** or an empty string. Sie können verschachtelte Aufrufe von Membern für eine Variable durchführen, die einen komplexen Typ enthält, wie z. B. `this.Address.State == "WA"`.

 Der Regelbedingungs-Editor unterstützt die folgenden Operatoren:

- Relationale Operatoren: ==, =, !=

- Comparison operators: <, \<=, >, >=

- Arithmetische Operatoren: +, - , *, /, MOD

- Logical operators: AND, &&, OR, &#124;&#124;, NOT, !

- Bitwise operators: &, &#124;

  Ausdrucksoperatorvorrang folgt C#-Operator-Vorrangregeln.

  Der Regelbedingungs-Editor unterstützt die folgenden numerischen Ausdrücke:

  this.i == 1D (wird zu 1.0 aufgelöst)

  this.i == 1E1 (wird zu 10.0 aufgelöst)

  this.i == 1L (wird zu einem long-Wert aufgelöst)

  this.i == 1M (wird zu einem decimal-Wert aufgelöst)

  this.i == 1F (wird zu einem single-Wert aufgelöst)

  this.i == 1U (wird zu einem vorzeichenlosen int-Wert aufgelöst)

  For more information about conditions, see [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Siehe auch
 [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033) [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039) [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049) [Select Condition Dialog Box (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md) [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009) [Legacy Designer for Windows Workflow Foundation UI Help](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)