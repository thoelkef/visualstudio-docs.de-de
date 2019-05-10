---
title: Regelsatz-Editor-Dialogfeld (Legacy) | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3827ef20ae5eb67c1052b6c7f6147d736013490
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438885"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Dialogfeld "Regelsatz-Editor" (Vorgängerversion)
In diesem Thema wird beschrieben, wie die **Regelsatz-Editor** Dialogfeld in der Vorgängerversion [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.  
  
 Die **Regelsatz-Editor** Dialogfeld wird verwendet, um das Erstellen und Ändern von [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) -Regelsätze, die als rules-Datei serialisiert wurden.  
  
> [!NOTE]
> Wenn Sie die zu öffnende die rules-Datei mit den **XML-Editor mit Codierung**, müssen Sie zunächst das zugewiesene Designerfenster für den Workflow oder eine Aktivität schließen.  
  
 Informationen über den Zugriff auf die **Regelsatz-Editor** im Dialogfeld finden Sie unter [Vorgehensweise: Erstellen ein PolicyActivity-Regelsatzes (Vorgängerversion)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
> Der Regel-Editor der Vorgängerversion von  [!INCLUDE[wfd2](../includes/wfd2-md.md)], der zum Abzielen auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] verwendet wird, unterstützt die Festlegung von Zielversionen nicht.  
  
 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Regelsatz-Editor** Dialogfeld.  
  
|Benutzeroberflächenelement|Beschreibung|  
|----------------|-----------------|  
|**Regel hinzufügen**|Fügt dem Regelsatz eine neue Regeldefinition hinzu.|  
|**Löschen**|Löscht die ausgewählte Regel aus dem Regelsatz.|  
|**Verketten von**|Gibt an, welcher Vorwärtsverkettungstyp mit dem Regelsatz verwendet werden soll. Die folgenden Optionen sind verfügbar:<br /><br /> -   **Vollständiges verketten**, die Verwendung aller angibt: implizit methodenzuweisung und explizit mit einem **Update** Funktion.<br />-   **Sequenzielle**, dadurch keine vorwärtsverkettung verwendet wird.<br />-   **Nur explizites Update**, die angibt, nur auszuführen, für die vorwärtsverkettung **Update** Aktionen.<br /><br /> Weitere Informationen zum vorwärtsverketten finden Sie unter [verwenden der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004).|  
|**Name**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Namen zu sortieren.|  
|**Priorität**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Priorität zu sortieren.|  
|**Eine erneute Auswertung**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach Typ der erneuten Auswertung zu sortieren.|  
|**Regel-Preview**|Regelsatzlisten-Spaltenüberschrift. Klicken Sie, um die Liste der Regeln nach der Vorschau der Bedingung und Aktionen einer Regel zu sortieren.|  
|**Name:**|Geben Sie den Namen der Regel ein.|  
|**Priorität:**|Geben Sie eine Priorität für die Regel ein. Die Standardpriorität ist 0.|  
|**Eine erneute Auswertung:**|Gibt an, welcher erneute Auswertungstyp mit der Regel verwendet werden soll. Die folgenden Optionen sind verfügbar:<br /><br /> -   **Immer**, womit die Regel neu ausgewertet werden, je nach Bedarf.<br />-   **Nie**, womit die Regel nie neu ausgewertet wird. In diesem Fall wird eine Regel nur einmal ausgeführt.|  
|**Active**|Aktivieren, damit die Regel aktiv wird.|  
|**Bedingung:**|Geben Sie einen Ausdruck für die Regelbedingung ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|  
|**Then-Aktionen:**|Geben Sie einen Ausdruck für Then-Aktionen ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|  
|**Else-Aktionen:**|Geben Sie einen Ausdruck für Else-Aktionen ein. Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs- und Aktionsausdrücken" dieser Seite.|  
|**OK**|Klicken Sie, um den Regelsatz in einer .rules-Datei zu speichern.|  
  
 Weitere Informationen zu Regelsätzen finden Sie unter [verwenden der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="entering-condition-and-action-expressions"></a>Eingeben von Bedingungs- und Aktionsausdrücken  
 Sie geben Ausdrücke für die Bedingung und die Then- und Else Aktionen als Text in die entsprechenden Felder der **Regelsatz-Editor** Dialogfeld. Sie können eingeben **dies.** Verwenden in den Editor auf Felder, Eigenschaften und Methoden, die im Workflow verwendet werden soll einen IntelliSense-Typ des Menüs "ein. Alternativ können Sie einen Workflowmembernamen auch direkt eingeben. Sie können statische Methoden für Typen, auf die verwiesen wird, aufrufen, indem Sie den Klassennamen gefolgt vom Methodennamen eingeben.  
  
 Sie können logische Operatoren, wie z. B. UND, ODER und NICHT, zur Bedingung hinzufügen. Sie können auch Prädikate hinzufügen. Ein Prädikat besteht aus einem binären Operator und zwei Operanden. Werden die unterstützte binäre Operatoren ==, >, \<, > = und < =. Unterstützte Operanden sind konstanter Wert, arithmetische Funktion und geschützte öffentliche Member.  
  
 Sie können den Typ für den Vergleich angeben, und Sie können mit vergleichen **null** oder eine leere Zeichenfolge. Sie können Aufrufe von Membern in einer Variable schachteln, die einen komplexen Typ enthält, wie z. B. `this.Address.State == "WA"`.  
  
 Ausdrücke unterstützen die folgenden Operatoren:  
  
- Relationale Operatoren: ==, =, !=  
  
- Vergleichsoperatoren: <, \<=, >, > =  
  
- Arithmetische Operatoren: +, - , *, /, MOD  
  
- Logische Operatoren: AND, &&, OR, &#124;&#124;, NOT, !  
  
- Bitweise Operatoren: &,&#124;  
  
  Ausdrucksoperatorvorrang folgt C#-Operator-Vorrangregeln.  
  
  Weitere Informationen zu Bedingungen finden Sie unter [Using Conditions in Workflows](http://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).  
  
### <a name="halt-and-update-functions"></a>Halt-Funktion und Update-Funktion  
 **Then-Aktionen:** und **Else-Aktionen:** Ausdrücke unterstützen **anhalten** und **Update** Funktionen. Verwenden der **anhalten** funktionieren, geben Sie **anhalten** in einer **Then-Aktion:** oder **Else-Aktion:** Textfeld. Die **anhalten** Aktion bewirkt sofort beendet, und die Steuerung an den aufrufenden Code zurückgibt. Sie verwenden die **Update** -Funktion mit vorwärtsverketten.  
  
 Ein **Update** Anweisung in den Editor in einer von zwei Formen ausgedrückt werden kann; beide Formen sind im folgenden Beispiel gezeigt:  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Weitere Informationen zur Verwendung von **Update** mit vorwärtsverkettung finden Sie unter [verwenden der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="see-also"></a>Siehe auch  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Regel für die Auswahl festlegen (Dialogfeld) (Vorgängerversion)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Verwenden der PolicyActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Verwenden von Bedingungen in Workflows](http://go.microsoft.com/fwlink?LinkID=65009)