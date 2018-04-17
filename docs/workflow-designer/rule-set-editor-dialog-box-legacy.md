---
title: Regelsatz-Editor (Dialogfeld) (Legacy) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7284b4a318f1d6c182f1d7d27e41f6c77092ad00
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Dialogfeld "Regelsatz-Editor" (Vorgängerversion)
In diesem Thema wird beschrieben, wie die **Regelsatz-Editor** in älteren Windows Workflow-Designer im Dialogfeld. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.

 Die **Regelsatz-Editor** Dialogfeld dient zum Erstellen und Ändern von [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) -Regelsätze, die in einer rules-Datei serialisiert werden.

> [!NOTE]
> Wenn Sie mit die rules-Datei öffnen möchten die **XML-Editor mit Codierung**, müssen Sie zunächst das zugewiesene Designerfenster für den Workflow oder eine Aktivität schließen.

 Informationen über den Zugriff auf die **Regelsatz-Editor** (Dialogfeld), finden Sie unter [Vorgehensweise: Erstellen einer PolicyActivity Regelsatz (Legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> Der Regel-Editor der Vorgängerversion von  [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], der zum Abzielen auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] verwendet wird, unterstützt die Festlegung von Zielversionen nicht.

 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Regelsatz-Editor** (Dialogfeld).

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Regel hinzufügen**|Fügt dem Regelsatz eine neue Regeldefinition hinzu.|
|**Löschen**|Löscht die ausgewählte Regel aus dem Regelsatz.|
|**Verkettung**|Gibt an, welcher Vorwärtsverkettungstyp mit dem Regelsatz verwendet werden soll. Die folgenden Optionen sind verfügbar:<br /><br /> -   **Vollständiges verketten**, die Verwendung aller vorwärtsverkettungsmechanismen angibt: implizit, attributzuweisung und explizit mit einem **Update** Funktion.<br />-   **Sequenzielle**, dadurch wird keine vorwärtsverkettung verwendet.<br />-   **Nur explizites Update**, gibt an, nur auszuführen, auf vorwärtsverkettung **Update** Aktionen.<br /><br /> Weitere Informationen zum vorwärtsverketten finden Sie unter [verwenden der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004).|
|**Name**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Namen zu sortieren.|
|**Priorität**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Priorität zu sortieren.|
|**Erneute Auswertung**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Typ der erneuten Auswertung zu sortieren.|
|**Regelvorschau**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach der Vorschau der Bedingung und Aktionen einer Regel zu sortieren.|
|**Name:**|Geben Sie den Namen der Regel ein.|
|**Priorität:**|Geben Sie eine Priorität für die Regel ein. Die Standardpriorität ist 0.|
|**Erneute Auswertung:**|Gibt an, welcher erneute Auswertungstyp mit der Regel verwendet werden soll. Die folgenden Optionen sind verfügbar:<br /><br /> -   **Immer**, womit die Regel nach Bedarf neu ausgewertet werden.<br />-   **Nie**, womit die Regel nie neu ausgewertet wird. In diesem Fall wird eine Regel nur einmal ausgeführt.|
|**Aktive**|Aktivieren, damit die Regel aktiv wird.|
|**Bedingung:**|Geben Sie einen Ausdruck für die Regelbedingung ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|
|**Then-Aktionen:**|Geben Sie einen Ausdruck für Then-Aktionen ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|
|**Else-Aktionen:**|Geben Sie einen Ausdruck für Else-Aktionen ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|
|**OK**|Klicken Sie, um den Regelsatz in einer .rules-Datei zu speichern.|

 Weitere Informationen zu Regelsätzen finden Sie unter [verwenden der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="entering-condition-and-action-expressions"></a>Eingeben von Bedingungs- und Aktionsausdrücken
 Sie geben Ausdrücke für die Bedingung und die Then- und Else Aktionen als Text in die entsprechenden Felder der **Regelsatz-Editor** (Dialogfeld). Sie können eingeben **dies.** in den Editor, Felder, Eigenschaften und Methoden, die im Workflow zu verweisen verwenden einen IntelliSense-Typ des Menüs aus. Alternativ können Sie einen Workflowmembernamen auch direkt eingeben. Sie können statische Methoden für Typen, auf die verwiesen wird, aufrufen, indem Sie den Klassennamen gefolgt vom Methodennamen eingeben.

 Sie können logische Operatoren, wie z. B. UND, ODER und NICHT, zur Bedingung hinzufügen. Sie können auch Prädikate hinzufügen. Ein Prädikat besteht aus einem binären Operator und zwei Operanden. Die binären Operatoren unterstützt werden ==, >, \<, > =, und < =. Unterstützte Operanden sind konstanter Wert, arithmetische Funktion und geschützte öffentliche Member.

 Können Sie den Typ für den Vergleich angeben, und Sie können mit vergleichen **null** oder eine leere Zeichenfolge. Sie können Aufrufe von Membern in einer Variable schachteln, die einen komplexen Typ enthält, wie z. B. `this.Address.State == "WA"`.

 Ausdrücke unterstützen die folgenden Operatoren:

-   Relationale Operatoren: ==, =, !=

-   Vergleichsoperatoren: <, \<=, >, > =

-   Arithmetische Operatoren: +, - , *, /, MOD

-   Logische Operatoren: und, & &, OR, &#124; &#124;, NOT,!

-   Bitweise Operatoren: &&#124;

 Ausdrucksoperatorvorrang folgt C#-Operator-Vorrangregeln.

 Weitere Informationen zu Bedingungen finden Sie unter [Using Conditions in Workflows](http://msdn.microsoft.com/en-us/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Halt-Funktion und Update-Funktion
 **Then-Aktionen:** und **Else-Aktionen:** Ausdrücke unterstützen **anhalten** und **Update** Funktionen. Verwenden der **anhalten** funktionieren, geben Sie **anhalten** in einer **Then-Aktion:** oder **Else-Aktion:** Textfeld. Die **anhalten** Aktion führt dazu, dass regelsatzausführung sofort beendet und die Steuerung an den aufrufenden Code zurückgegeben. Verwenden Sie die **Update** -Funktion mit vorwärtsverketten.

 Ein **Update** Anweisung kann im Editor in einer von zwei Formen ausgedrückt werden; beide Formen sind im folgenden Beispiel gezeigt:

```
Update(this.Address.State)
Update("this/Address/State")
```

 Weitere Informationen zur Verwendung von **Update** vorwärtsverketten finden Sie unter [verwenden der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="see-also"></a>Siehe auch

- [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [Dialogfeld "Regelsatz-Editor auswählen" (Vorgängerversion)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [Verwenden der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004)
- [Verwenden von Bedingungen in Workflows](http://go.microsoft.com/fwlink?LinkID=65009)