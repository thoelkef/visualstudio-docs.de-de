---
title: Dialogfeld "Regelbedingungs-Editor" (Vorgängerversion) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62b74956dc12e19a5594585e8d356b77ae5549b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Dialogfeld "Regelbedingungs-Editor" (Vorgängerversion)

In diesem Thema wird beschrieben, wie die **Regelbedingungs-Editor** in älteren Windows Workflow-Designer im Dialogfeld. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.

Sie erstellen und ändern deklarative regelbedingungen mit dem **Regelbedingungs-Editor** (Dialogfeld). Diese Regelbedingungen werden in den folgenden vordefinierten Windows Workflow Foundation-Aktivitäten als Eigenschaften angegeben:

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

Sie Zugriff auf die **Regelbedingungs-Editor** Dialogfeld mithilfe der [wählen Sie im Dialogfeld Bedingung (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).

Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Regelbedingungs-Editor** (Dialogfeld).

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Bedingung:**|Geben Sie den Ausdruck für die Regelbedingung ein.|
|**OK**|Klicken Sie, um die Regelbedingung zu speichern.|

## <a name="entering-condition-expressions"></a>Eingeben von Bedingungsausdrücken

Bedingungsausdrücke werden als Text eingegeben. Sie können eingeben **dies.** in den Editor, Felder, Eigenschaften und Methoden, die im Workflow zu verweisen verwenden eine IntelliSense-ähnliches Menü aus. Alternativ können Sie einen Workflowmembernamen auch direkt eingeben. Sie können logische Operatoren, wie z. B. UND, ODER und NICHT, zur Bedingung hinzufügen. Sie können auch Prädikate hinzufügen. Ein Prädikat besteht aus einem binären Operator und zwei Operanden. Die binären Operatoren unterstützt werden **==**, **>**, **\<**, **>=**, und **<=**. Unterstützte Operanden sind konstanter Wert, arithmetische Funktion und geschützte öffentliche Member.

Können Sie den Typ für den Vergleich angeben, und Sie können mit vergleichen **null** oder eine leere Zeichenfolge. Sie können verschachtelte Aufrufe von Membern für eine Variable durchführen, die einen komplexen Typ enthält, wie z. B. `this.Address.State == "WA"`.

Der Regelbedingungs-Editor unterstützt die folgenden Operatoren:

-   Relationale Operatoren: ==, =, !=

-   Vergleichsoperatoren: <, \<=, >, > =

-   Arithmetische Operatoren: +, -, \*, /, MOD

-   Logische Operatoren: und, & &, OR, &#124; &#124;, NOT,!

-   Bitweise Operatoren: &&#124;

Ausdrucksoperatorvorrang folgt C#-Operator-Vorrangregeln.

Der Regelbedingungs-Editor unterstützt die folgenden numerischen Ausdrücke:

this.i == 1D (wird zu 1.0 aufgelöst)

this.i == 1E1 (wird zu 10.0 aufgelöst)

this.i == 1L (wird zu einem long-Wert aufgelöst)

this.i == 1M (wird zu einem decimal-Wert aufgelöst)

this.i == 1F (wird zu einem single-Wert aufgelöst)

this.i == 1U (wird zu einem vorzeichenlosen int-Wert aufgelöst)

Weitere Informationen zu Bedingungen finden Sie unter [Using Conditions in Workflows](http://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Siehe auch

- [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)
- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)
- [Dialogfeld "Regelbedingungs-Editor auswählen" (Vorgängerversion)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [Verwenden von Bedingungen in Workflows](http://go.microsoft.com/fwlink?LinkID=65009)
- [Benutzeroberflächenhilfe von Visual Studio Designer für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)