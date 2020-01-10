---
title: Dialog Feld "Regelsatz-Editor" (Legacy) | Microsoft-Dokumentation
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
ms.openlocfilehash: 8010bbbc38dee980ebe89dc60ccb513379103a26
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846316"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Dialogfeld "Regelsatz-Editor" (Vorgängerversion)
In diesem Thema wird beschrieben, wie Sie das Dialogfeld **Regelsatz-Editor** in der Legacy-[!INCLUDE[wfd1](../includes/wfd1-md.md)]verwenden. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 Das Dialogfeld **Regelsatz-Editor** wird verwendet, um [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) -Regelsätze zu erstellen und zu ändern, die in eine rules-Datei serialisiert werden.

> [!NOTE]
> Wenn Sie die rules-Datei mit dem **XML-Editor mit Codierung**öffnen möchten, müssen Sie zunächst das zugehörige Designer Fenster für den Workflow oder die Aktivität schließen.

 Weitere Informationen zum Zugreifen auf das Dialogfeld **Regelsatz-Editor** finden Sie unter Vorgehens [Weise: Erstellen eines PolicyActivity-Regelsatzes (Legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> Der Regel-Editor der Vorgängerversion von  [!INCLUDE[wfd2](../includes/wfd2-md.md)], der zum Abzielen auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] verwendet wird, unterstützt die Festlegung von Zielversionen nicht.

 In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds **Regelsatz-Editor** beschrieben.

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Regel hinzufügen**|Fügt dem Regelsatz eine neue Regeldefinition hinzu.|
|**Löschen**|Löscht die ausgewählte Regel aus dem Regelsatz.|
|**Verkettung**|Gibt an, welcher Vorwärtsverkettungstyp mit dem Regelsatz verwendet werden soll. Die folgenden Optionen sind verfügbar:<br /><br /> -   **vollständige Verkettung**, die angibt, dass alle vorwärts Verkettungs Mechanismen verwendet werden sollen: implizit, Methoden Zuweisung und explizite Verwendung einer **Update** -Funktion.<br />-   **sequenziell**, das angibt, dass keine vorwärts Verkettung verwendet werden soll.<br />-   **explizites Update**, das angibt, dass für **Aktualisierungs** Aktionen nur eine vorwärts Verkettung durchgeführt werden soll.<br /><br /> Weitere Informationen zur vorwärts Verkettung finden Sie unter [Verwenden der PolicyActivity-Aktivität](https://msdn2.microsoft.com/library/bb675229.aspx).|
|**Name**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Namen zu sortieren.|
|**Priority**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Priorität zu sortieren.|
|**Erneute Bewertung**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Typ der erneuten Auswertung zu sortieren.|
|**Regel Vorschau**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach der Vorschau der Bedingung und Aktionen einer Regel zu sortieren.|
|**Name:**|Geben Sie den Namen der Regel ein.|
|**Priority:**|Geben Sie eine Priorität für die Regel ein. Die Standardpriorität ist 0.|
|**Erneute Bewertung**|Gibt an, welcher erneute Auswertungstyp mit der Regel verwendet werden soll. Die folgenden Optionen sind verfügbar:<br /><br /> -   **immer**, was bewirkt, dass die Regel bei Bedarf neu ausgewertet wird.<br />-   **nie**, was bewirkt, dass die Regel nie erneut ausgewertet wird. In diesem Fall wird eine Regel nur einmal ausgeführt.|
|**Active**|Aktivieren, damit die Regel aktiv wird.|
|**Bedingung:**|Geben Sie einen Ausdruck für die Regelbedingung ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|
|**Aktionen ausführen:**|Geben Sie einen Ausdruck für Then-Aktionen ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|
|**Else-Aktionen:**|Geben Sie einen Ausdruck für Else-Aktionen ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|
|**OK**|Klicken Sie, um den Regelsatz in einer .rules-Datei zu speichern.|

 Weitere Informationen zu Regelsätzen finden Sie unter [Verwenden der PolicyActivity-Aktivität](https://msdn2.microsoft.com/library/bb675229.aspx).

## <a name="entering-condition-and-action-expressions"></a>Eingeben von Bedingungs- und Aktionsausdrücken
 Sie geben Ausdrücke für die Bedingung und die then-und Else-Aktionen als Text in die entsprechenden Textfelder im Dialogfeld **Regelsatz-Editor** ein. Sie können **diese eingeben.** , um im Editor auf Felder, Eigenschaften und Methoden zu verweisen, die im Workflow verwendet werden. verwenden Sie dazu den Menübefehl IntelliSense. Alternativ können Sie einen Workflowmembernamen auch direkt eingeben. Sie können statische Methoden für Typen, auf die verwiesen wird, aufrufen, indem Sie den Klassennamen gefolgt vom Methodennamen eingeben.

 Sie können logische Operatoren, wie z. B. UND, ODER und NICHT, zur Bedingung hinzufügen. Sie können auch Prädikate hinzufügen. Ein Prädikat besteht aus einem binären Operator und zwei Operanden. Die unterstützten binären Operatoren sind = =, > \<, > = und < =. Unterstützte Operanden sind konstanter Wert, arithmetische Funktion und geschützte öffentliche Member.

 Sie können den Typ für den Vergleich angeben, und Sie können mit **null** oder einer leeren Zeichenfolge vergleichen. Sie können Aufrufe von Membern in einer Variable schachteln, die einen komplexen Typ enthält, wie z. B. `this.Address.State == "WA"`.

 Ausdrücke unterstützen die folgenden Operatoren:

- Relationale Operatoren: ==, =, !=

- Vergleichs Operatoren: <, \<=, >, > =

- Arithmetische Operatoren: +, - , *, /, MOD

- Logische Operatoren: and, & & oder, &#124; &#124;, not,!

- Bitweise Operatoren: &&#124;

  Ausdrucksoperatorvorrang folgt C#-Operator-Vorrangregeln.

  Weitere Informationen zu Bedingungen finden Sie unter [Verwenden von Bedingungen in Workflows](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Halt-Funktion und Update-Funktion
 **Aktionen:** und **Else-Aktionen:** -Ausdrücke unterstützen **Halt** -und **Update** -Funktionen. Wenn Sie die **Halt** -Funktion verwenden möchten, geben Sie **Halt** in ein **Then Action:** -oder **else Action:** Textfeld ein. Die **Halt** -Aktion bewirkt, dass die Ausführung der Regelsätze sofort beendet wird und die Steuerung an den aufrufenden Code zurückgegeben wird. Sie verwenden die **Update** -Funktion mit vorwärts Verkettung.

 Eine **Update** -Anweisung kann im Editor in einer von zwei Formen ausgedrückt werden. beide Formen werden im folgenden Beispiel gezeigt:

```
Update(this.Address.State)
Update("this/Address/State")
```

 Weitere Informationen zur Verwendung von **Update** mit vorwärts Verkettung finden Sie unter [Verwenden der PolicyActivity-Aktivität](https://msdn2.microsoft.com/library/bb675229.aspx).

## <a name="see-also"></a>Siehe auch
 [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) - [Dialog Feld "Regelsatz auswählen" (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [mithilfe der PolicyActivity-Aktivität unter](https://msdn2.microsoft.com/library/bb675229.aspx) [Verwendung von Bedingungen in Workflows](https://msdn2.microsoft.com/library/bb628447.aspx)
