---
title: "Erste Schritte mit PTVS: Debuggen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82803559-1d60-4c57-98fb-2dc1e0182b42
caps.latest.revision: 4
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
caps.handback.revision: 4
---
# Erste Schritte mit PTVS: Debuggen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der interaktive Debugger von Visual Studio erleichtert die Diagnose und das Beheben von Problemen in Ihrem Python\-Code.  
  
 Sie können sich diese Anweisungen in einem kurzen [Youtube\-Video](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4) ansehen.  
  
 Im vorherigen Einstiegsthema haben Sie ein leeres Projekt für eine Python\-Anwendung erstellt und den folgenden Code in "PythonApplication1.py" eingegeben:  
  
```python  
from math import sin, cos, radians  
import sys  
  
def make_dot_string(x):  
    return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
  
assert make_dot_string(90) == "          o"  
assert make_dot_string(180) == "o"  
  
def main():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
  
if __name__ == "__main__":  
    sys.exit(int(main() or 0))  
```  
  
 Normalerweise führen Sie Code, den Sie in Visual Studio erstellen, durch Drücken von F5 aus.  Dieser Befehl erstellt alle Teile des Projekts, die erstellt werden müssen, und startet dann die Ausführung des Codes im Debugger.  Sie können aber auch STRG\+F5 drücken, um Code ohne den Debugger zu starten.  Mit dem Debugger wird der Code etwas langsamer ausgeführt, aber Sie erhalten im Gegenzug hervorragende Debugfunktionen.  
  
 Eine weitere Möglichkeit zur Codeausführung bietet der Befehl zum schrittweisen Ausführen \(normalerweise F11\).  Wie bei F5 wird die Ausführung bei jeder Anweisung unterbrochen.  Wenn Sie das Programm an einem bestimmten Punkt unterbrechen möchten, klicken Sie im Code\-Editor auf den linken Rand, um einen Haltepunkt festzulegen.  Wenn Sie F5 drücken, wird die Ausführung des Programms an der Zeile mit dem Haltepunkt angehalten.  Das Menü "Debuggen" enthält weitere Optionen für die schrittweise Ausführung. Dazu gehören z. B. das Überspringen von Funktionen \(F10\), schrittweise Funktionsaufrufe \(F11\) oder das Überspringen am Ende einer Funktion \(UMSCHALTTASTE\+F11\).  
  
 Es gibt bei einer Unterbrechung im Debugger eine Vielzahl von Möglichkeiten.  Das Fenster "Lokal" enthält die aktuellen Werte der lokalen Variablen.  Wenn Sie den Code schrittweise durchgehen, wird die Anzeige in "Lokal" automatisch aktualisiert.  Das Fenster "Auto" enthält die Variablen in der Nähe der aktuellen Zeile, an der die Ausführung angehalten wurde.  Im Fenster "Überwachen" können Sie beliebige Python\-Ausdrücke eingeben, die der Debugger automatisch bei jeder Unterbrechung der Ausführung aktualisiert.  Sie können auch den Mauszeiger über Variablen in Editor\-Fenstern bewegen, um eine Popupansicht der Variablenwerte anzuzeigen. In dieser Datenanzeige können Sie Objekte überprüfen.  Für einige Datentypen gibt es spezielle Visualisierungen, die über die Anzeige der QuickInfo verfügbar sind \(z. B. Zeichenfolgen mit speziellen Formatierungen wie HTML, XML oder JSON\).  
  
 Das Fenster "Aufrufliste" zeigt die ausstehenden Funktionsaufrufe, die zur aktuellen Anweisung, in der der Debugger angehalten wurde, geführt haben.  Sie können verschiedene Stapelrahmen \(Zeilen in der Aufrufliste\) als Sprungziele auswählen. Der Code wird dann in jeder Funktion fortgesetzt, und Sie können die Werte von Variablen prüfen usw.  
  
 Sie können sich diese Anweisungen in einem kurzen [Youtube\-Video](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4) ansehen.  
  
## Siehe auch  
 [Wiki\-Dokumentation](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [PTVS\-Videos – Einstieg und detaillierte Informationen](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)