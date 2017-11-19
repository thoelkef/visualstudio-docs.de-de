---
title: Formatbezeichner im Debugger (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edb41f8fea8447f8616b4c20f442ffd4fa8b48c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Formatbezeichner in c# in Visual Studio-debugger
Sie können das Format ändern, in dem ein Wert im Fenster **Überwachen** mithilfe von Formatbezeichnern angezeigt wird. Formatbezeichner können im Fenster **Direkt** , im Fenster **Befehl** und sogar in den Quellcodefenstern verwendet werden. Wenn Sie in einen Ausdruck in diesen Fenstern anhalten, wird das Ergebnis in einem DataTip angezeigt. DataTips geben den Formatbezeichner in der DataTip-Anzeige wieder.  
  
 Zum Verwenden eines Formatbezeichners geben Sie den von einem Komma gefolgten Ausdruck ein. Fügen Sie nach dem Komma den entsprechenden Bezeichner hinzu.  
  
## <a name="using-format-specifiers"></a>Verwenden von Formatbezeichnern  
 Wenn Ihr Code folgendermaßen lautet:  
  
```CSharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Hinzufügen der `my_var1` Variablen im Fenster "überwachen" (während des Debuggens **Debuggen > Windows > Überwachen > Überwachen 1**), und legen Sie die Anzeige auf hexadezimal (in der **Überwachen** Fenster mit der rechten Maustaste in der Variablenwerts und Wählen Sie **Hexadezimale Anzeige**). Im Fenster **Überwachen** wird nun angezeigt, dass der Wert 0x0065 enthalten ist. Um diesen Wert als ganze Dezimalzahl und nicht als ganze Hexadezimalzahl auszudrücken, geben Sie in der Spalte "Name" nach dem Variablennamen den Dezimalformatbezeichner **, d**ein. In der Spalte "Wert" wird nun der Dezimalwert 101 angezeigt.  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Formatbezeichner  
 In der folgenden Tabelle wird der C#-Formatbezeichner angezeigt, die vom Debugger erkannt werden.  
  
|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Anzeige|  
|---------------|------------|--------------------------|--------------|  
|ac|Erzwingen der Auswertung eines Ausdrucks. Dies kann nützlich sein, wenn die implizite Auswertung von Eigenschaften sowie implizite Funktionsaufrufe deaktiviert sind.|Meldung "implizite funktionsevaluierung wird durch den Benutzer deaktiviert"|\<Wert >|  
|T|Ganze Dezimalzahl|0x0065|101|  
|dynamic|Zeigt das angegebene Objekt mit einer dynamischen Ansicht an.|Zeigt alle Member des Objekts einschließlich der dynamischen Ansicht an.|Zeigt nur die dynamische Ansicht an.|  
|h|Ganze Hexadezimalzahl|61541|0x0000F065|  
|nq|Zeichenfolge ohne Anführungszeichen|"Meine Zeichenfolge"|Meine Zeichenfolge|  
|hidden|Zeigt alle öffentlichen und nicht öffentlichen Member an.|Zeigt öffentliche Member an.|Zeigt alle Member an.|  
|raw|Zeigt ein Element so an, wie es im Knoten für Rohdatenelemente dargestellt wird. Nur für Proxyobjekte gültig.|Wörterbuch\<T >|Rohdatenansicht von Dictionary\<T >|  
|results|Wird mit einer Variablen eines Typs, der IEnumerable "oder" IEnumerable implementiert\<T >, in der Regel das Ergebnis eines Abfrageausdrucks. Zeigt nur die das Abfrageergebnis enthaltenden Member an.|Zeigt alle Member an.|Zeigt die Elemente an, die die Bedingungen der Abfrage erfüllen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen "und" Schnellüberwachung Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Fenster „Auto“ und „Lokal“](../debugger/autos-and-locals-windows.md)
