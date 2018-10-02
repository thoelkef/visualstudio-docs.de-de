---
title: 'Erste Schritte mit PTVS: Bearbeiten von Code | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: f70e551fd44c18c9dbfc37437703ca092e982d6a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521227"
---
# <a name="getting-started-with-ptvs-editing-code"></a>Erste Schritte mit PTVS: Bearbeiten von Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS stellt die produktive Erfahrung von Visual Studio-Editor für Python bereit.  
  
 Sie können diese Anweisungen in einem sehr kurzen [YouTube-Video](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) ansehen.  
  
 Beginnen Sie mit der grundlegenden leeren Projektvorlage für Python-Anwendungen.  
  
 Beginnen mit der Eingabe einer Zeile mit `from … import` im Editor.  Es wird eine Vervollständigungsliste mit allen für den Import verfügbaren Modulen angezeigt.  Diese Liste hängt von Ihrer Version von Python und den installierten Bibliotheken ab.  Verwenden Sie als Beispiel die math-Bibliothek.  Sie werden bemerken, dass während der Eingabe der Vervollständigungsliste Filter auf diese Elemente, einschließlich der von Ihnen eingegebenen Zeichen, angewendet werden.  Vervollständigen Sie die Anweisung durch Importieren der `sin`-Bezeichner.  
  
```python  
from math import sin  
  
```  
  
 Wenn Sie beim Programmieren einen ungebundenen Bezeichner verwenden, der jedoch in Ihren Bibliotheken enthalten ist, bietet PTVS in einer Schnellkorrektur die entsprechende import-Anweisung für die benötigte Anweisung an.  Angenommen, Sie typisierte `cos`, würde **importieren aus mathematischen** angeboten.  
  
 Sie können einen Ausschnitt zum Generieren von Code verwenden.  Wählen Sie im Menü "Bearbeiten" die Option "IntelliSense" und dann "Ausschnitt einfügen" aus.  Wählen Sie dann Python und "def" aus.  Rufen Sie die `make_dot_string`-Funktion auf, und fügen Sie den Parameter `x` hinzu.  Sie können der Datei Assertionsanweisungen für die testgesteuerte Entwicklung hinzufügen. PTVS kann dann direkt die neue Funktion in Vervollständigungslisten bereitstellen.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 Wechseln Sie zurück zu der neuen Funktion, und beginnen Sie mit der Eingabe von folgendem Text:  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 Sie sehen, dass PTVS davon ausgeht, dass der Parameter eine ganze Zahl ist, da PTVS die Aufrufpositionen für diese Funktion analysiert hat.   Sie müssen auch in diesem Fall die Schnellkorrektur verwenden, um `radians` zu importieren.  
  
 Verwenden Sie einen anderen Codeausschnitt, um einen main-Block zu erstellen. Geben Sie dazu `main` auf der obersten Ebene ein, rufen Sie die SmartTag-Benutzeroberfläche auf, und wählen Sie mit der Tabulatortaste "def main..." aus.  Schreiben Sie eine einfache Schleife zum Aufrufen von `make_dot_string`.  PTVS weiß bereits, wenn Sie den Punkt eingeben, dass die Funktion eine Zeichenfolge zurückgibt, was Sie anhand der angebotenen Optionen erkennen können.  Diese Typinformationen durchlaufen das gesamte Programm. Es ist also egal, wo Ihre Werte am Ende verwendet werden: Es stehen immer QuickInfos und Vervollständigungsmöglichkeiten bereit, die Ihnen helfen, Ihren Code besser zu verstehen und zu schreiben.  
  
 Fügen Sie einen Aufruf zum Drucken hinzu. Ihre "main"-Funktion sollte nun der folgenden ähneln:  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 Wenn Sie F5 drücken, wird der Code in einem Fenster von "cmd.exe" ausgeführt. Sie sehen einen Punkt , der hin und her oszilliert.  
  
 Sie können diese Anweisungen in einem sehr kurzen [YouTube-Video](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) ansehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Wiki-Dokumentation](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [PTVS-Videos: Einstieg und ausführliche Erläuterungen](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

