---
title: "Gewusst wie: Erstellen von JavaScript-XML-Dokumentationskommentaren | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Codekommentare, JavaScript IntelliSense"
  - "Dokumentationskommentare [JavaScript]"
  - "IntelliSense [JavaScript], XML-Dokumentationskommentare"
  - "XML-Dokumentationskommentare, JavaScript IntelliSense"
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Erstellen von JavaScript-XML-Dokumentationskommentaren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*XML\-Dokumentationskommentare* sind JavaScript Kommentare, dass Sie ein Skript, um Informationen zu Code\-Elemente, z. B. Variablen, Funktionen und Felder hinzufügen.  In Visual Studio werden diese Textbeschreibungen mit IntelliSense angezeigt, wenn Sie die Skriptfunktion verweisen.  
  
 Dieses Thema enthält ein Lernprogramm zur Verwendung von XML\-Dokumentationskommentare.  Informationen über andere Elemente, z. B. [\<var\>](../ide/var-javascript.md) und [\<value\>](../ide/value-javascript.md), und Weitere Codebeispiele finden Sie unter [XML\-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md).  Informationen zum Bereitstellen von IntelliSense Informationen für ein asynchroner Rückruf wie z. B. ein `Promise`, finden Sie unter [\<returns\>](../ide/returns-javascript.md).  
  
> [!NOTE]
>  XML\-Dokumentationskommentare stehen nur aus referenzierten Dateien, Assemblys und Services zur Verfügung.  
  
### Erstellen von XML\-Dokumentationskommentaren für eine JavaScript\-Funktion  
  
-   Fügen Sie in der Funktion [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md), und [\<returns\>](../ide/returns-javascript.md) Elemente, und jedes Element mit drei Schrägstrichen \(\/ \/ \/\) vorausgehen.  
  
    > [!NOTE]
    >  Jedes Element muss in einer Zeile sein.  
  
     Das folgende Beispiel zeigt eine JavaScript\-Funktion.  
  
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
  
-   Um die XML\-Dokumentationskommentare anzuzeigen, geben Sie den Namen und die öffnende Klammer einer Funktion, die mit XML\-Dokumentationskommentare, wie im folgenden Beispiel markiert ist:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     Wenn Sie die öffnende Klammer der Funktion, die die XML\-Dokumentationskommentare enthält eingeben, verwendet der Code\-Editor IntelliSense zum Anzeigen der Informationen, die in XML\-Dokumentationskommentare definiert ist.  
  
### Erstellen von XML\-Dokumentationskommentaren für eine JavaScript\-Feld  
  
-   Fügen Sie in einer Funktion oder das Objekt Konstruktordefinition, ein [\<field\>](../ide/field-javascript.md) Element von drei Schrägstriche \(\/ \/ \/\) vorangestellt.  
  
     Das folgende Beispiel zeigt die Verwendung der `<field>` \-Element in eine Konstruktorfunktion.  Weitere Beispiele finden Sie unter [\<field\>](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   Um die XML\-Dokumentationskommentare anzuzeigen, erstellen Sie ein Objekt mithilfe des Function\-Konstruktors, der markiert ist mit XML\-Dokumentationskommentaren, wie im folgenden Beispiel.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   Geben Sie den Namen des Objekts und einen Zeitraum IntelliSense Informationen für das Feld an, in der nächsten Zeile.  
  
    ```javascript  
    eng.  
    ```  
  
### Erstellen von XML\-Dokumentationskommentaren für eine überladene Funktion  
  
1.  Fügen Sie in der Funktion einer [\<signature\>](../ide/signature-javascript.md) \-Element für jede Überladung.  Fügen Sie in diese Elemente andere Elemente, z. B. `<summary>`, `<param>`, und `<returns>`, jedes Element mit drei Schrägstrichen \(\/ \/ \/\) vor.  
  
     Das folgende Beispiel zeigt eine überladene JavaScript\-Funktion.  In diesem Beispiel unterscheiden sich die Überladungen von Parametertyp.  
  
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
  
2.  Um die XML\-Dokumentationskommentare anzuzeigen, geben Sie den Namen und die öffnende Klammer, die Funktion, die mit XML\-Dokumentationskommentare, wie im folgenden Beispiel markiert ist:  
  
    ```javascript  
    calc(  
    ```  
  
### Erstellen von lokalisierten IntelliSense  
  
1.  Erstellen Sie eine XML\-Datei, die Dokumentationskommentare im Format OpenAjax MessageBundle hat.  
  
    > [!IMPORTANT]
    >  MessageBundle ist das empfohlene Format.  Dieses Format wird nicht in der Microsoft Ajax oder .winmd\-Dateien unterstützt.  Informationen zum Verwenden der Alternative `VSDoc` formatieren, finden Sie unter [\<loc\>](../ide/loc-javascript.md).  
  
     Das folgende Beispiel zeigt Inhalte in einem sogenannten Filialdokument, das die lokalisierte IntelliSense Informationen enthält.  Dies ist eine XML\-Datei, die in einem Ordner kulturspezifische wie JA befindet.  Der Ordner muss sich in demselben Speicherort wie die js\-Datei enthält die `<loc>` Element.  Der Dateiname der XML\-Datei muss übereinstimmen die `filename` Parameter angegeben wird, der `<loc>` Element.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  Fügen Sie den folgenden Code in der js\-Datei.  Die `<loc>` Element muss vor jedem Skript deklariert werden, und folgt denselben Verwendungsregeln als die `<reference>` Element.  Weitere Informationen finden Sie unter [JavaScript IntelliSense](../ide/javascript-intellisense.md) und [\<loc\>](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  In der js\-Datei können fügen Sie die Elemente der XML\-Dokumentation und Standard\-Beschreibungen hinzu.  Legen Sie die `locid` Attributwerte entsprechend den entsprechenden `name` Attributwerte aus der Datei Beiwagen.  Lokalisierte IntelliSense Informationen ersetzt die Standard\-Beschreibungen Wenn es verfügbar ist.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  Um die XML\-Dokumentationskommentare anzuzeigen, geben Sie den Namen und die öffnende Klammer der Funktion, wie im folgenden Beispiel:  
  
    ```javascript  
    add(  
    ```  
  
## Siehe auch  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [XML\-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Walkthrough: JavaScript IntelliSense in ASP.NET](http://msdn.microsoft.com/de-de/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)