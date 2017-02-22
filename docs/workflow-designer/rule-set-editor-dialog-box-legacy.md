---
title: "Dialogfeld &quot;Regelsatz-Editor&quot; (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleSetDialog.UI"
helpviewer_keywords: 
  - "Regelsatz-Editor (Dialogfeld)"
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dialogfeld &quot;Regelsatz-Editor&quot; (Vorg&#228;ngerversion)
In diesem Thema wird die Verwendung des Dialogfelds **Regelsatz\-Editor** in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] beschrieben.Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.  
  
 Mit dem Dialogfeld **Regelsatz\-Editor** werden [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)\-Regelsätze \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\) erstellt und bearbeitet, die als RULES\-Datei serialisiert wurden.  
  
> [!NOTE]
>  Soll die .rules\-Datei mit dem **XML\-Editor mit Codierung** geöffnet werden, müssen Sie zunächst das zugewiesene Designerfenster für den Workflow oder die Aktivität schließen.  
  
 Informationen zum Zugriff auf das Dialogfeld **Regelsatz\-Editor** finden Sie unter [Vorgehensweise: Erstellen eines PolicyActivity\-Regelsatzes \(Vorgängerversion\)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
>  Der Regel\-Editor der Vorgängerversion von  [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], der zum Abzielen auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] verwendet wird, unterstützt die Festlegung von Zielversionen nicht.  
  
 In der folgenden Tabelle werden die Benutzeroberflächenelemente des Dialogfelds **Regelsatz\-Editor** beschrieben.  
  
|Benutzeroberflächenelement|Beschreibung|  
|--------------------------------|------------------|  
|**Regel hinzufügen**|Fügt dem Regelsatz eine neue Regeldefinition hinzu.|  
|**Löschen**|Löscht die ausgewählte Regel aus dem Regelsatz.|  
|**Verketten**|Gibt an, welcher Vorwärtsverkettungstyp mit dem Regelsatz verwendet werden soll.Die folgenden Optionen sind verfügbar:<br /><br /> -   **Vollständiges Verketten**, womit die Verwendung aller Vorwärtsverkettungsmechanismen festgelegt wird: implizit, Attributzuweisung für Methoden und explizit mit einer **Update**\-Funktion.<br />-   **Sequenziell**, womit festgelegt wird, dass keine Vorwärtsverkettung verwendet werden darf.<br />-   **Nur explizites Update**, womit angegeben wird, dass nur für **Aktualisierungs**aktionen Vorwärtsverkettung durchgeführt wird.<br /><br /> Weitere Informationen zum Vorwärtsverketten finden Sie unter [Verwenden der PolicyActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004). \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)|  
|**Name**|Regelsatzlisten\-Spaltenüberschrift.Klicken Sie, um die Liste der Regeln nach Namen zu sortieren.|  
|**Priorität**|Regelsatzlisten\-Spaltenüberschrift.Klicken Sie, um die Liste der Regeln nach Priorität zu sortieren.|  
|**Erneute Auswertung**|Regelsatzlisten\-Spaltenüberschrift.Klicken Sie, um die Liste der Regeln nach Typ der erneuten Auswertung zu sortieren.|  
|**Regelvorschau**|Regelsatzlisten\-Spaltenüberschrift.Klicken Sie, um die Liste der Regeln nach der Vorschau der Bedingung und Aktionen einer Regel zu sortieren.|  
|**Name:**|Geben Sie den Namen der Regel ein.|  
|**Priorität:**|Geben Sie eine Priorität für die Regel ein.Die Standardpriorität ist 0.|  
|**Erneute Auswertung:**|Gibt an, welcher erneute Auswertungstyp mit der Regel verwendet werden soll.Die folgenden Optionen sind verfügbar:<br /><br /> -   **Immer**, womit die Regel nach Bedarf neu ausgewertet wird.<br />-   **Nie**, womit die Regel nie neu ausgewertet wird.In diesem Fall wird eine Regel nur einmal ausgeführt.|  
|**Aktiv**|Aktivieren, damit die Regel aktiv wird.|  
|**Bedingung:**|Geben Sie einen Ausdruck für die Regelbedingung ein.Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs\- und Aktionsausdrücken" dieser Seite.|  
|**Then\-Aktionen:**|Geben Sie einen Ausdruck für Then\-Aktionen ein.Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs\- und Aktionsausdrücken" dieser Seite.|  
|**Else\-Aktionen:**|Geben Sie einen Ausdruck für Else\-Aktionen ein.Informationen zur Ausdruckssyntax finden Sie im Abschnitt "Eingeben von Bedingungs\- und Aktionsausdrücken" dieser Seite.|  
|**OK**|Klicken Sie, um den Regelsatz in einer .rules\-Datei zu speichern.|  
  
 Weitere Informationen zu Regelsätzen finden Sie unter [Verwenden der PolicyActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004). \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)  
  
## Eingeben von Bedingungs\- und Aktionsausdrücken  
 Sie geben Ausdrücke für die Bedingung und die Then\- und Else\-Aktionen als Text in die entsprechenden Textfelder des Dialogfelds **Regelsatz\-Editor** ein.Sie können **this.** in den Editor eingeben, um auf im Workflow verwendete Felder, Eigenschaften und Methoden zu verweisen. Hierfür wird ein IntelliSense\-Menü verwendet.Alternativ können Sie einen Workflowmembernamen auch direkt eingeben.Sie können statische Methoden für Typen, auf die verwiesen wird, aufrufen, indem Sie den Klassennamen gefolgt vom Methodennamen eingeben.  
  
 Sie können logische Operatoren, wie z. B. UND, ODER und NICHT, zur Bedingung hinzufügen.Sie können auch Prädikate hinzufügen.Ein Prädikat besteht aus einem binären Operator und zwei Operanden.Es werden die binären Operatoren \=\=, \>, \<, \>\= und \<\= unterstützt.Unterstützte Operanden sind konstanter Wert, arithmetische Funktion und geschützte öffentliche Member.  
  
 Sie können den Typ für den Vergleich angeben, und Sie können mit **null** oder einer leeren Zeichenfolge vergleichen.Sie können Aufrufe von Membern in einer Variable schachteln, die einen komplexen Typ enthält, wie z. B. `this.Address.State == "WA"`.  
  
 Ausdrücke unterstützen die folgenden Operatoren:  
  
-   Relationale Operatoren: \=\=, \=, \!\=  
  
-   Vergleichsoperatoren: \<, \<\=, \>, \>\=  
  
-   Arithmetische Operatoren: \+, \- , \*, \/, MOD  
  
-   Logische Operatoren: UND, &&, ODER, &#124;&#124;, NICHT, \!  
  
-   Bitweise Operatoren: &, &#124;  
  
 Ausdrucksoperatorvorrang folgt C\#\-Operator\-Vorrangregeln.  
  
 Weitere Informationen zu Bedingungen finden Sie unter [Using Conditions in Workflows](http://msdn.microsoft.com/de-de/541211f5-d382-4810-894f-71f00b34fa77).  
  
### Halt\-Funktion und Update\-Funktion  
 **Then\-Aktionen:**\-Ausdrücke und **Else\-Aktionen:**\-Ausdrücke unterstützen **Halt**\-Funktionen und **Update**\-Funktionen.Zur Verwendung der **Halt**\-Funktion geben Sie **Halt** in ein **Then\-Aktion:**\-Textfeld oder **Else\-Aktion:**\-Textfeld ein.Die **Halt**\-Aktion bewirkt das sofortige Anhalten der Regelsatzausführung, und die Steuerung wird an den aufrufenden Code zurückgegeben.Sie verwenden die **Update**\-Funktion mit Vorwärtsverketten.  
  
 Eine **Update**\-Anweisung kann im Editor mit ein oder zwei Formen ausgedrückt werden. Beide Formen sind im nachstehenden Beispiel dargestellt:  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Weitere Informationen zur Verwendung von **Update** mit Vorwärtsverkettung finden Sie unter [Verwenden der PolicyActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004). \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)  
  
## Siehe auch  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Dialogfeld "Regelsatz\-Editor auswählen" \(Vorgängerversion\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Verwenden der PolicyActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Verwenden der Bedingungen in Workflows](http://go.microsoft.com/fwlink?LinkID=65009)