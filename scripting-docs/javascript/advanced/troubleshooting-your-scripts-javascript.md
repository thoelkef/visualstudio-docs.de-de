---
title: Problembehandlung bei Skripts (JavaScript) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- automative type conversion
- troubleshooting scripts
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e0193e6dc0996d5e2d0d3df7103c7705d29477
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569280"
---
# <a name="troubleshooting-your-scripts-javascript"></a>Problembehandlung bei Skripts (JavaScript)
Jede Programmiersprache birgt Überraschungen. Beispielsweise verhält sich der Wert `null` in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] anders als der Wert `Null` in den Sprachen C oder C++.  
  
 Hier werden einige Bereiche aufgelistet, in denen es zu Problemen beim Schreiben von [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Skripts kommen kann.  
  
## <a name="syntax-errors"></a>Syntaxfehler  
 Es ist besonders wichtig, beim Schreiben von Skripts auf Details zu achten. Beispielsweise müssen alle Zeichenfolgen in Anführungszeichen stehen.  
  
## <a name="order-of-script-interpretation"></a>Reihenfolge der Skriptinterpretation  
 Die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]-Interpretation ist Teil der HTML-Analyseprozesses Ihres Webbrowsers. Wenn Sie Ihr Skript in einem Dokument in ein \<HEAD>-Tag platzieren, wird es vor allen Teilen des \<BODY>-Tags interpretiert. Wenn Objekte in dem \<BODY>-Tag erstellt werden, sind diese bei der Analyse des \<HEAD>-Tags noch nicht vorhanden und können daher auch nicht vom Skript bearbeitet werden.  
  
> [!NOTE]
>  Dieses Verhalten ist spezifisch für Internet Explorer. Der ASP und der WSH verfügen (genauso wie andere Hosts) über verschiedene Ausführungsmodelle.  
  
## <a name="automatic-type-coercion"></a>Automatische Typkoersion  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ist eine lose typisierte Erweiterung mit automatischer Koersion. Obwohl Werte verschiedene ungleiche Typen haben, ergeben die Ausdrücke in den folgenden Beispielen den Wert **TRUE**.  
  
```JavaScript  
"100" == 100;  
false == 0;  
```  
  
 Verwenden Sie den strengen Gleichheitsoperator (===), um zu prüfen, dass der Typ dem Wert entspricht. Im folgenden Beispiel ergeben beide den Wert FALSE.  
  
```JavaScript  
"100" === 100;  
false === 0;  
```  
  
## <a name="operator-precedence"></a>Operatorrangfolge  
 Die [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md) wird bestimmt, wenn ein Vorgang bei der Überprüfung eines Ausdrucks ausgeführt wird. Im folgenden Beispiel wird vor der Subtraktion multipliziert, obwohl die Subtraktion vor der Multiplikation in dem Ausdruck platziert ist.  
  
```JavaScript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## <a name="using-forin-loops-with-objects"></a>Verwenden einer For...In-Schleife mit Objekten  
 Wenn Sie die Eigenschaften eines Objekts mit einer [For...In](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)-Schleife durchlaufen, können Sie die Reihenfolge nicht vorhersehen, in der die Objektfelder der Schleifenzählervariable zugeordnet werden. Des Weiteren kann sich die Reihenfolge in einer anderen Implementierung der Sprache ändern.  
  
## <a name="with-keyword"></a>With-Schlüsselwort  
 Die [With](../../javascript/reference/with-statement-javascript.md)-Anweisung eignet sich zwar für den Zugriff auf bereits in einem angegebenen Objekt bestehende Eigenschaften, jedoch können sie nicht verwendet werden, um Eigenschaften zu einem Objekt hinzuzufügen. Sie müssen ausdrücklich auf das Objekt verweisen, um darin neue Eigenschaften zu erstellen.  
  
## <a name="this-keyword"></a>This-Schlüsselwort  
 Auch wenn Sie das `this`-Schlüsselwort in der Definition eines Objekts verwenden, um auf das Objekt zu verweisen, können Sie `this` oder ähnliche Schlüsselwörter nicht verwenden, um auf die aktuell ausgeführte Funktion zu verweisen, wenn es sich bei dieser Funktion nicht um eine Objektdefinition handelt. Wenn die Funktion als Methode einem Objekt zugeordnet wird, können Sie das `this`-Schlüsselwort in der Funktion verwenden, um auf ein Objekt zu verweisen.  
  
## <a name="writing-a-script-that-writes-a-script-in-internet-explorer"></a>Schreiben eines Skript, das ein Skript in Internet Explorer schreibt  
 Das \</SCRIPT>-Tag beendet das aktuelle Skript, wenn der Interpreter darauf stößt. Um das „\</SCRIPT>“-Tag alleine anzuzeigen, schreiben Sie es als mindestens zwei Zeichenfolgen: z.B. „\</SCR“ und „IPT>“, die Sie dann in der Anweisung verketten, die diese schreibt.  
  
## <a name="implicit-window-references-in-internet-explorer"></a>Implizite Verweise auf Fenster in Internet Explorer  
 Da mehrere Fenster gleichzeitig geöffnet sein können, zeigen alle impliziten Verweispunkte auf Fenster auf das aktuelle Fenster. Für andere Fenster benötigen Sie einen expliziten Verweis.