---
title: Die Formatbezeichner im Debugger (C#) | Microsoft-Dokumentation
ms.date: 11/21/2018
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fe922960b0571593cc15581c29244798fd0f671e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018734"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Formatbezeichner in C# in Visual Studio-Debugger
Sie können das Format, in dem ein Wert, im angezeigt wird, Ändern der **Watch** mithilfe von Formatbezeichnern. Sie können auch die Formatbezeichner in der **direkt** Fenster die **Befehl** Fenster im [Ablaufverfolgungspunkte](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints), und in den Quellcodefenstern. Wenn Sie auf einem Ausdruck in diesen Fenstern anhalten, erscheint das Ergebnis einem [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) in der Anzeige des angegebenen Formats.  
  
 Um einen Formatbezeichner verwenden, geben Sie in des Variablen Ausdrucks gefolgt von einem Komma und den entsprechenden Bezeichner.  
  
## <a name="set-format-specifiers"></a>Satz von Formatbezeichnern  
Wir verwenden den folgenden aus:   
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Hinzufügen der `my_var1` Variable die **Überwachen** Fenster während des Debuggens **Debuggen** > **Windows** > **ansehen**  >  **Überwachen 1**. Als Nächstes mit der rechten Maustaste in der Variablenwerts, und wählen Sie **Hexadezimale Anzeige**. Jetzt die **Watch** Fenster zeigt den Wert 0 x 0065. Um diesen Wert als ganze Dezimalzahl und nicht in eine hexadezimale ganze Zahl anzuzeigen, fügen Sie dem Dezimalformatbezeichner **, d** in die **Namen** Spalte nach dem Variablennamen ein. Die **Wert** Spalte zeigt jetzt **101**.   
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Formatbezeichner  
 Die folgende Tabelle beschreibt die C# Formatbezeichner für Visual Studio-Debugger.  
  
|Bezeichner|Format|Ursprünglicher Wert in "Überwachen"|Anzeige|  
|---------------|------------|--------------------------|--------------|  
|ac|Erzwingen der Auswertung eines Ausdrucks, dies kann hilfreich sein, wenn implizite Auswertung von Eigenschaften und implizite Funktionsaufrufe deaktiviert ist.|Meldung „Implizite Funktionsevaluierung durch den Benutzer deaktiviert“|\<Wert>|  
|T|Ganze Dezimalzahl|0x0065|101|  
|dynamic|Zeigt das angegebene Objekt mit einer dynamischen Ansicht an.|Zeigt alle Member des Objekts einschließlich der dynamischen Ansicht an.|Zeigt nur die dynamische Ansicht an.|  
|h|Ganze Hexadezimalzahl|61541|0x0000F065|  
|nq|Zeichenfolge ohne Anführungszeichen|"Meine Zeichenfolge"|Meine Zeichenfolge|  
|nse|Gibt das Verhalten, nicht-Format. Wertet den Ausdruck mit "Keine Nebeneffekte". Wenn der Ausdruck kann nicht interpretiert werden und nur durch eine Auswertung (z. B. auf ein Funktionsaufruf) aufgelöst werden kann, werden Sie stattdessen ein Fehler angezeigt.|Nicht zutreffend|Nicht zutreffend|
|hidden|Zeigt alle öffentlichen und nicht öffentlichen Member an.|Zeigt öffentliche Member an.|Zeigt alle Member an.|  
|raw|Zeigt ein Element so an, wie es im Knoten für Rohdatenelemente dargestellt wird. Nur für Proxyobjekte gültig.|Wörterbuch\<T >|Rohdatenansicht von Dictionary\<T >|  
|results|Wird mit einer Variablen eines Typs, die "IEnumerable" oder "IEnumerable" implementiert\<T >, in der Regel das Ergebnis eines Abfrageausdrucks. Zeigt nur die das Abfrageergebnis enthaltenden Member an.|Zeigt alle Member an.|Zeigt die Member an, die die Bedingungen der Abfrage erfüllen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Watch and QuickWatch windows (Fenster „Überwachen“ und „Schnellüberwachung“)](../debugger/watch-and-quickwatch-windows.md)   
 [Autos and Locals windows (Fenster „Auto“ und „Lokal“)](../debugger/autos-and-locals-windows.md)
