---
title: "Formatbezeichner in C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "CSharp"
helpviewer_keywords: 
  - "Debugger, Formatbezeichner erkannt von"
  - "Ausdrücke [C#], Formatieren von Werten"
  - "Formatbezeichner, Debugger"
  - "Schnellüberwachung (Dialogfeld), Formatbezeichner in C#"
  - "Schnellüberwachung (Dialogfeld), Verwenden von Formatbezeichnern"
  - "Bezeichner"
  - "Bezeichner, Überwachungsvariablenformat"
  - "Symbole, Überwachungsvariablenformatierung"
  - "Variablen [Debugger], Überwachungsvariablensymbole"
  - "Überwachungsvariablensymbole"
  - "Überwachungsfenster, Formatbezeichner in C#"
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Formatbezeichner in C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können das Format, in dem ein Wert im Fenster **Überwachen** angezeigt wird, mithilfe von Formatbezeichnern ändern. Formatbezeichner können auch im Fenster **Direkt**, im Fenster **Befehl** und sogar in den Quellcodefenstern verwendet werden. Wenn Sie in einen Ausdruck in diesen Fenstern anhalten, wird das Ergebnis in einem DataTip angezeigt. DataTips geben den Formatbezeichner in der DataTip\-Anzeige wieder.  
  
 Zum Verwenden eines Formatbezeichners geben Sie den von einem Komma gefolgten Ausdruck ein. Fügen Sie nach dem Komma den entsprechenden Bezeichner hinzu.  
  
## Verwenden von Formatbezeichnern  
 Wenn Ihr Code folgendermaßen lautet:  
  
```  
{ int my_var1 = 0x0065; int my_var2 = 0x0066; int my_var3 = 0x0067; }  
```  
  
 Fügen Sie die Variable `my_var1` dem Fenster "Überwachen" hinzu \(beim Debugging, **Debuggen\/Fenster\/Überwachen\/Überwachen 1**\), und legen Sie die Anzeige auf hexadezimal fest \(klicken Sie im Fenster **Überwachen** mit der rechten Maustaste auf die Variable, und wählen Sie **Hexadezimale Anzeige** aus\). Im Fenster **Überwachen** wird nun angezeigt, dass der Wert 0x0065 enthalten ist. Um diesen Wert als ganze Dezimalzahl und nicht als ganze Hexadezimalzahl auszudrücken, geben Sie in der Spalte "Name" nach dem Variablennamen den Dezimalformatbezeichner **, d** ein. In der Spalte "Wert" wird nun der Dezimalwert 101 angezeigt.  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## Formatbezeichner  
 In der folgenden Tabelle wird der C\#\-Formatbezeichner angezeigt, die vom Debugger erkannt werden.  
  
|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Anzeige|  
|----------------|------------|-----------------------------------------|-------------|  
|ac|Erzwingen der Auswertung eines Ausdrucks. Dies kann nützlich sein, wenn die implizite Auswertung von Eigenschaften sowie implizite Funktionsaufrufe deaktiviert sind. Siehe [Nebeneffekte und Ausdrücke](../Topic/Side%20Effects%20and%20Expressions.md).|Meldung "Implizite Funktionsevaluierung durch den Benutzer deaktiviert"|\<value\>|  
|d|Ganze Dezimalzahl|0x0065|101|  
|dynamic|Zeigt das angegebene Objekt mit einer dynamischen Ansicht an.|Zeigt alle Member des Objekts einschließlich der dynamischen Ansicht an.|Zeigt nur die dynamische Ansicht an.|  
|h|Ganze Hexadezimalzahl|61541|0x0000F065|  
|nq|Zeichenfolge ohne Anführungszeichen|"Meine Zeichenfolge"|Meine Zeichenfolge|  
|hidden|Zeigt alle öffentlichen und nicht öffentlichen Member an.|Zeigt öffentliche Member an.|Zeigt alle Member an.|  
|raw|Zeigt ein Element so an, wie es im Knoten für Rohdatenelemente dargestellt wird. Nur für Proxyobjekte gültig.|Dictionary\<T\>|Rohdatenansicht von Dictionary\<T\>|  
|results|Wird mit einer Variablen eines Typs verwendet, durch den "IEnumerable" oder "IEnumerable\<T\>" implementiert wird; normalerweise das Ergebnis eines Abfrageausdrucks. Zeigt nur die das Abfrageergebnis enthaltenden Member an.|Zeigt alle Member an.|Zeigt die Elemente an, die die Bedingungen der Abfrage erfüllen.|  
  
## Siehe auch  
 [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)   
 [Variablenfenster](../Topic/Variable%20Windows.md)