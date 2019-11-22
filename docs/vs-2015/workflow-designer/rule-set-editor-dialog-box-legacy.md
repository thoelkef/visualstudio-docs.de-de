---
title: Rule Set Editor Dialog Box (Legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83cdd4f549655be524abdd2a4708b316f6747b3e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302754"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Dialogfeld "Regelsatz-Editor" (Vorgängerversion)
This topic describes how use the **Rule Set Editor** dialog box in the legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 The **Rule Set Editor** dialog box is used to create and modify [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) rule sets, which are serialized to a .rules file.

> [!NOTE]
> If you want to open the .rules file with the **XML Editor with encoding**, you must first close the associated designer window for the workflow or activity.

 For information about how to access the **Rule Set Editor** dialog box, see [How to: Create a PolicyActivity Rule Set (Legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> Der Regel-Editor der Vorgängerversion von  [!INCLUDE[wfd2](../includes/wfd2-md.md)], der zum Abzielen auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] verwendet wird, unterstützt die Festlegung von Zielversionen nicht.

 The following table describes the user interface (UI) elements of the **Rule Set Editor** dialog box.

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Add Rule**|Fügt dem Regelsatz eine neue Regeldefinition hinzu.|
|**Löschen**|Löscht die ausgewählte Regel aus dem Regelsatz.|
|**Chaining**|Gibt an, welcher Vorwärtsverkettungstyp mit dem Regelsatz verwendet werden soll. Die folgenden Optionen sind verfügbar:<br /><br /> -   **Full Chaining**, which specifies to use all forward chaining mechanisms: implicit, method attributing, and explicit using an **Update** function.<br />-   **Sequential**, which specifies not to use any forward chaining.<br />-   **Explicit Update Only**, which specifies to only perform forward chaining on **Update** actions.<br /><br /> For more information about forward chaining, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).|
|**Name**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Namen zu sortieren.|
|**Priority**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Priorität zu sortieren.|
|**Reevaluation**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Typ der erneuten Auswertung zu sortieren.|
|**Rule Preview**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach der Vorschau der Bedingung und Aktionen einer Regel zu sortieren.|
|**Name:**|Geben Sie den Namen der Regel ein.|
|**Priority:**|Geben Sie eine Priorität für die Regel ein. Die Standardpriorität ist 0.|
|**Reevaluation:**|Gibt an, welcher erneute Auswertungstyp mit der Regel verwendet werden soll. Die folgenden Optionen sind verfügbar:<br /><br /> -   **Always**, which causes the rule to be reevaluated as needed.<br />-   **Never**, which causes the rule to never be reevaluated. In diesem Fall wird eine Regel nur einmal ausgeführt.|
|**Active**|Aktivieren, damit die Regel aktiv wird.|
|**Condition:**|Geben Sie einen Ausdruck für die Regelbedingung ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|
|**Then Actions:**|Geben Sie einen Ausdruck für Then-Aktionen ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|
|**Else Actions:**|Geben Sie einen Ausdruck für Else-Aktionen ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|
|**OK**|Klicken Sie, um den Regelsatz in einer .rules-Datei zu speichern.|

 For more information about rule sets, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).

## <a name="entering-condition-and-action-expressions"></a>Eingeben von Bedingungs- und Aktionsausdrücken
 You enter expressions for the Condition and the Then and Else actions as text in their respective text boxes in the **Rule Set Editor** dialog box. You can type **this.** into the editor to reference fields, properties and methods used in the workflow, using an IntelliSense-type of menu. Alternativ können Sie einen Workflowmembernamen auch direkt eingeben. Sie können statische Methoden für Typen, auf die verwiesen wird, aufrufen, indem Sie den Klassennamen gefolgt vom Methodennamen eingeben.

 Sie können logische Operatoren, wie z. B. UND, ODER und NICHT, zur Bedingung hinzufügen. Sie können auch Prädikate hinzufügen. Ein Prädikat besteht aus einem binären Operator und zwei Operanden. The binary operators supported are ==, >, \<, >=, and <=. Unterstützte Operanden sind konstanter Wert, arithmetische Funktion und geschützte öffentliche Member.

 You can specify the type for the comparison, and you can compare to **null** or an empty string. Sie können Aufrufe von Membern in einer Variable schachteln, die einen komplexen Typ enthält, wie z. B. `this.Address.State == "WA"`.

 Ausdrücke unterstützen die folgenden Operatoren:

- Relationale Operatoren: ==, =, !=

- Comparison operators: <, \<=, >, >=

- Arithmetische Operatoren: +, - , *, /, MOD

- Logical operators: AND, &&, OR, &#124;&#124;, NOT, !

- Bitwise operators: &, &#124;

  Ausdrucksoperatorvorrang folgt C#-Operator-Vorrangregeln.

  For more information about conditions, see [Using Conditions in Workflows](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Halt-Funktion und Update-Funktion
 **Then Actions:** and **Else Actions:** expressions support **Halt** and **Update** functions. To use the **Halt** function, type **Halt** into a **Then Action:** or **Else Action:** text box. The **Halt** action causes rule set execution to stop immediately, and control returns to the calling code. You use the **Update** function with forward chaining.

 An **Update** statement can be expressed in the editor in one of two forms; both forms are shown in the following example:

```
Update(this.Address.State)
Update("this/Address/State")
```

 For more information about using **Update** with forward chaining, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).

## <a name="see-also"></a>Siehe auch
 [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004) [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009)