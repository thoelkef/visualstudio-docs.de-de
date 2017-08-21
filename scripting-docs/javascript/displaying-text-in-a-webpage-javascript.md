---
title: Anzeigen von Text auf einer Webseite (JavaScript) | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, write
- JavaScript, writing text
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: a8c9ea9d0e0300a0d9b71b0b33d7c99c9ac3935c
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

---
# <a name="displaying-text-in-a-webpage-javascript"></a>Anzeigen von Text auf einer Webseite (JavaScript)
Es gibt mehrere Möglichkeiten, Text auf einer Webseite anzuzeigen. Jede hat Vor- und Nachteile und unterstützt bestimmte Verwendungsmöglichkeiten.  
  
## <a name="displaying-text"></a>Anzeigen von Text  
  
-   Um Text anzuzeigen, wird empfohlen, ein Element zu erstellen und in seine textContent-Eigenschaft zu schreiben.  
  
    ```JavaScript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     In diesem Beispiel ist „my text“ der Wert des `text`-Parameters. Der Wert, der von der Eigenschaft `textContent` auf einem übergeordneten Knoten abgerufen bzw. in dieser festgelegt wird, kann jedoch Text von den untergeordneten Elementen des Knotens enthalten. Das folgende Beispiel zeigt, dass der `textContent`, der in einem untergeordneten Knoten festgelegt ist, im `textContent`-Wert des übergeordneten Knotens enthalten ist:  
  
    ```JavaScript  
    <div id="textDiv">  
        <div id="nested"></div>  
    </div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        var nestedDiv = document.getElementById("nested");  
        nestedDiv.textContent = "nested";  
  
        var text = "[" + div.textContent + "]";  
    </script>  
    ```  
  
     In diesem Beispiel ist „[nested]“ der Wert von `text`.  
  
-   Sie können auch ein Element erstellen und in seine [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx)- oder [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx)-Eigenschaften schreiben. Das Festlegen dieser Eigenschaften beeinflusst nur den Text im Element selbst, nicht den in den untergeordneten Elementen. Diese Eigenschaften haben allerdings auch einige Nachteile:  
  
    -   Die [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx)-Eigenschaft wird nicht in allen Browsern unterstützt. Sie sollten sie aus Gründen der Kompatibilität vermeiden.  
  
    -   Die [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx)-Eigenschaft wird von CSS-Stilen beeinflusst und wird nicht angezeigt, wenn das Element ausgeblendet ist.  
  
    -   Mit der [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx)-Eigenschaft werden sowohl geschachtelte Knoten als auch Text festgelegt bzw. abgerufen. Wenn sie nicht geschützt ist, kann sie für Script-Injection-Angriffe verwendet werden. Außerdem werden durch die Festlegung auf Text ohne HTML-Tags alle zuvor festgelegten Knoten entfernt.  
  
-   Sie können die `document.write`-Methode verwenden, ohne ein Element erstellen zu müssen. Allerdings wird mit dieser Methode die gesamte Webseite gelöscht, was möglicherweise unerwünscht ist.  
  
     Das folgende Beispiel zeigt einen der Nachteile der Verwendung von `document.write`. Das Skript zeigt nicht, wie beabsichtigt, die Zeit alle 5 Sekunden an, sondern nur zweimal. Bis `document.write` beim zweiten Mal aufgerufen wird, hat die Seite das Laden beendet, und `document.write` löscht dann die gesamte Seite (sie ruft `document.open` auf.) An diesem Punkt ist die `ShowTime`-Funktion nicht mehr vorhanden.  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
    <script type="text/javascript">  
        function ShowTime()  
        {  
            var dt = new Date();  
            document.write(dt.toTimeString());  
            // var elem = document.getElementById("divElem");  
            // elem.textContent = dt.toTimeString();  
            window.setTimeout("ShowTime();", 5000);  
        }  
    </script>  
    </head>  
  
    <body>  
    <script type="text/javascript">  
        ShowTime();  
    </script>  
    <div id="myDiv"></div>  
    </body>  
    </html>  
  
    ```  
  
     Zur Behebung des vorangehenden Codes entfernen Sie die Codezeile, die `document.write` enthält, und heben Sie die Auswahl der zwei kommentierten Codezeilen, die folgen, auf.  
  
-   Sie können auch eine `alert``prompt`- oder `confirm`-Funktion verwenden, die eine Meldung in einem Popupfenster anzeigt. In den meisten Fällen ist es nicht empfehlenswert, ein Popupfenster in einem Webbrowser zu verwenden. Die meisten modernen Browser verwenden Einstellungen, die Popupfenster blockieren, sodass die Meldung nicht angezeigt wird. Außerdem ist es mit Popupfenstern möglich, in eine Endlosschleife zu geraten. Der Benutzer kann die Webseite dann nicht auf die übliche Weise schließen.
