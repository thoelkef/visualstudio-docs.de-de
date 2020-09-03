---
title: Erstellen von XML-Dokumentations Kommentaren für JavaScript IntelliSense | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21fdc15b161b7d1cef30effe82e518a174bc9666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619546"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Erstellen von XML-Dokumentationskommentaren für JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*XML-Dokumentations Kommentare* sind JavaScript-Kommentare, die Sie einem Skript hinzufügen, um Informationen zu Code Elementen, wie z. b. Funktionen, Feldern und Variablen, bereitzustellen. In Visual Studio werden diese Textbeschreibungen mit IntelliSense angezeigt, wenn Sie auf die Skriptfunktion verweisen.

 Dieses Thema enthält ein einfaches Tutorial zur Verwendung von XML-Dokumentations Kommentaren. Weitere Informationen zur Verwendung anderer Elemente, wie z. b. [\<var>](../ide/var-javascript.md) und [\<value>](../ide/value-javascript.md) , sowie weitere Codebeispiele finden Sie unter [XML-Dokumentations Kommentare](../ide/xml-documentation-comments-javascript.md). Informationen zum Bereitstellen von IntelliSense-Informationen für einen asynchronen Rückruf, wie z `Promise` . b., finden Sie unter [\<returns>](../ide/returns-javascript.md) .

> [!NOTE]
> XML-Dokumentationskommentare sind nur in den Dateien, Assemblys und Diensten verfügbar, auf die verwiesen wurde.

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>So erstellen Sie XML-Dokumentations Kommentare für eine JavaScript-Funktion

- Fügen Sie in der-Funktion die [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) Elemente, und vor [\<returns>](../ide/returns-javascript.md) jedem Element mit drei Schrägstrichen (///) hinzu.

    > [!NOTE]
    > Jedes Element muss sich in einer einzelnen Zeile befinden.

     Das folgende Beispiel zeigt eine JavaScript-Funktion.

    ```javascript
    function getArea(radius)
    {
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>
        /// <param name="radius" type="Number">The radius of the circle.</param>
        /// <returns type="Number">The area.</returns>
        var areaVal;
        areaVal = Math.PI * radius * radius;
        return areaVal;
    }
    ```

- Wenn Sie die XML-Dokumentations Kommentare anzeigen möchten, geben Sie den Namen und die öffnende Klammer einer Funktion ein, die mit XML-Dokumentations Kommentaren markiert ist, wie im folgenden Beispiel gezeigt:

    ```javascript
    var areaVal = getArea(
    ```

     Wenn Sie die öffnende Klammer der Funktion eingeben, die die XML-Dokumentations Kommentare enthält, verwendet der Code-Editor IntelliSense, um die in XML-Dokumentations Kommentaren definierten Informationen anzuzeigen.

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>So erstellen Sie XML-Dokumentations Kommentare für ein JavaScript-Feld

- Fügen Sie in einer Konstruktorfunktion oder Objektdefinition ein [\<field>](../ide/field-javascript.md) -Element mit vorangestelltem drei Schrägstrich (///) hinzu.

     Das folgende Beispiel zeigt die Verwendung des- `<field>` Elements in einer Konstruktorfunktion. Weitere Beispiele finden Sie unter [\<field>](../ide/field-javascript.md) .

    ```javascript
    function Engine() {
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
        this.HorsePower = 150;
    }
    ```

- Um die XML-Dokumentations Kommentare anzuzeigen, erstellen Sie ein-Objekt, indem Sie den funktionskonstruktor verwenden, der mit XML-Dokumentations Kommentaren markiert ist, wie im folgenden Beispiel gezeigt.

    ```javascript
    var eng = new Engine();
    ```

- Geben Sie in der nächsten Zeile den Namen des Objekts und einen Zeitraum ein, um IntelliSense-Informationen für das Feld anzuzeigen.

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>So erstellen Sie XML-Dokumentations Kommentare für eine überladene Funktion

1. Fügen Sie in der-Funktion ein- [\<signature>](../ide/signature-javascript.md) Element für jede Überladung hinzu. Fügen Sie in diesen Elementen weitere Elemente (z. b. `<summary>` , `<param>` und `<returns>` ) vor jedem Element mit drei Schrägstrichen (///) hinzu.

     Das folgende Beispiel zeigt eine überladene JavaScript-Funktion. In diesem Beispiel unterscheiden sich die über Ladungen je nach Parametertyp.

    ```javascript
    function calc(a) {
        /// <signature>
        /// <summary>Function summary 1.</summary>
        /// <param name="a" type="Number">A number.</param>
        /// <returns type="Number" />
        /// </signature>
        /// <signature>
        /// <summary>Function summary 2.</summary>
        /// <param name="a" type="String">A string.</param>
        /// <returns type="Number" />
        /// </signature>
        return a;
    }
    ```

2. Wenn Sie die XML-Dokumentations Kommentare anzeigen möchten, geben Sie den Namen und die öffnende Klammer der Funktion ein, die mit XML-Dokumentations Kommentaren markiert ist, wie im folgenden Beispiel gezeigt:

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>So erstellen Sie einen lokalisierten IntelliSense

1. Erstellen Sie eine XML-Datei mit Dokumentations Kommentaren im OpenAjax messagebundle-Format.

    > [!IMPORTANT]
    > Messagebundle ist das empfohlene Format. Dieses Format wird in Microsoft AJAX oder in winmd-Dateien nicht unterstützt. Weitere Informationen zur Verwendung des alternativen `VSDoc` Formats finden Sie unter [\<loc>](../ide/loc-javascript.md) .

     Im folgenden Beispiel wird der Inhalt einer Sidecar-Datei gezeigt, die die lokalisierten IntelliSense-Informationen enthält. Dies ist eine XML-Datei, die sich in einem Kultur abhängigen Ordner befindet, z. b. "Ja". Der Ordner muss sich am selben Speicherort befinden wie die JS-Datei, die das- `<loc>` Element enthält. Der Dateiname der XML-Datei muss mit dem `filename` im-Element angegebenen Parameter identisch sein `<loc>` .

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. Fügen Sie in ihrer JS-Datei den folgenden Code hinzu. Das `<loc>` -Element muss vor jedem Skript deklariert werden, und befolgt die gleichen Verwendungs Regeln wie das- `<reference>` Element. Weitere Informationen finden Sie unter [JavaScript IntelliSense](../ide/javascript-intellisense.md) und [\<loc>](../ide/loc-javascript.md) .

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. Fügen Sie in ihrer JS-Datei die XML-Dokumentations Elemente und die Standard Beschreibungen hinzu. Legen `locid` Sie die Attributwerte so fest, dass Sie den entsprechenden `name` Attributwerten aus der Sidecar-Datei entsprechen. Die Standard Beschreibungen werden durch lokalisierte IntelliSense-Informationen ersetzt, sofern diese verfügbar sind.

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. Wenn Sie die XML-Dokumentations Kommentare anzeigen möchten, geben Sie den Namen und die öffnende Klammer der Funktion ein, wie im folgenden Beispiel gezeigt:

    ```javascript
    add(
    ```

## <a name="see-also"></a>Weitere Informationen
 [JavaScript IntelliSense](../ide/javascript-intellisense.md) [XML-Dokumentations Kommentare](../ide/xml-documentation-comments-javascript.md) [NIB: Exemplarische Vorgehensweise: JavaScript IntelliSense in ASP.net](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
