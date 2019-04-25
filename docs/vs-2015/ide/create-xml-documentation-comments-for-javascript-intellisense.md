---
title: Erstellen von XML-Dokumentationskommentaren für JavaScript IntelliSense | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7b13931746cc9668ea18ead71babd5140e971818
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079278"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Erstellen von XML-Dokumentationskommentaren für JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*XML-Dokumentationskommentare* werden Kommentare von JavaScript, dass Sie ein Skript zum Bereitstellen von Informationen zu Codeelementen wie z. B. Funktionen, Felder und Variablen hinzufügen. In Visual Studio werden diese textbeschreibungen mit IntelliSense angezeigt, wenn Sie die Skriptfunktion verweisen.  
  
 Dieses Thema enthält ein Lernprogramm zur Verwendung von XML-Dokumentationskommentare. Informationen zur Verwendung von anderen Elementen wie z. B. [ \<Var >](../ide/var-javascript.md) und [ \<Wert >](../ide/value-javascript.md), und Weitere Codebeispiele, finden Sie unter [XML-Dokumentationskommentare ](../ide/xml-documentation-comments-javascript.md). Weitere Informationen zum Bereitstellen von IntelliSense-Informationen für einen asynchronen Rückruf wie z. B. eine `Promise`, finden Sie unter [ \<gibt >](../ide/returns-javascript.md).  
  
> [!NOTE]
>  XML-Dokumentationskommentare sind nur in den Dateien, Assemblys und Diensten verfügbar, auf die verwiesen wurde.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Zum Erstellen von XML-Dokumentationskommentaren für JavaScript-Funktion  
  
- Fügen Sie in der Funktion [ \<summary >](../ide/summary-javascript.md), [ \<Param >](../ide/param-javascript.md), und [ \<gibt >](../ide/returns-javascript.md) Elemente, und stellen Sie jedes Element voran drei Schrägstriche (/ / /).  
  
    > [!NOTE]
    >  Jedes Element muss sich in einer einzelnen Zeile.  
  
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
  
- Um die XML-Dokumentationskommentare zu anzuzeigen, geben Sie den Namen und die öffnende Klammer einer Funktion, die mit XML-Dokumentationskommentare, wie im folgenden Beispiel markiert ist:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     Wenn Sie die öffnende Klammer der Funktion, die XML-Dokumentationskommentare enthält eingeben, verwendet der Code-Editor IntelliSense zum Anzeigen der Informationen, die in XML-Dokumentationskommentare definiert ist.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Zum Erstellen von XML-Dokumentationskommentare für ein JavaScript-Feld  
  
- Fügen Sie in einer Konstruktordefinition Funktion oder das Objekt eine [ \<Feld >](../ide/field-javascript.md) Element vorangestellt drei Schrägstrichen (/ / /).  
  
     Das folgende Beispiel zeigt die Verwendung der `<field>` Element in einer Konstruktorfunktion. Weitere Beispiele finden Sie unter [ \<Feld >](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
- Um die XML-Dokumentationskommentare anzuzeigen, erstellen Sie ein Objekt mithilfe des Function-Konstruktors, die markiert ist, mit XML-Dokumentationskommentare, wie im folgenden Beispiel aus.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
- Geben Sie auf der nächsten Zeile den Namen des Objekts und eines Zeitraums zum Anzeigen der IntelliSense-Informationen für das Feld ein.  
  
    ```javascript  
    eng.  
    ```  
  
### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Zum Erstellen von XML-Dokumentationskommentaren für einer überladenen Funktion  
  
1. Fügen Sie in der Funktion ein [ \<Signatur >](../ide/signature-javascript.md) -Element für jede Überladung. Fügen Sie in der folgenden Elemente, die andere Elemente, z. B. `<summary>`, `<param>`, und `<returns>`, jedes Element mit drei Schrägstrichen (/ / /) vor.  
  
     Das folgende Beispiel zeigt eine überladene JavaScript-Funktion. In diesem Beispiel unterscheiden sich die Überladungen von Parametertyp ein.  
  
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
  
2. Um die XML-Dokumentationskommentare zu anzuzeigen, geben Sie den Namen und die öffnende Klammer der Funktion, die mit XML-Dokumentationskommentare, wie im folgenden Beispiel markiert ist:  
  
    ```javascript  
    calc(  
    ```  
  
### <a name="to-create-localized-intellisense"></a>Um lokalisierte IntelliSense zu erstellen.  
  
1. Erstellen Sie eine XML-Datei, die Dokumentationskommentare im OpenAjax MessageBundle-Format enthält.  
  
    > [!IMPORTANT]
    >  MessageBundle ist das empfohlene Format. Dieses Format wird nicht in der Microsoft Ajax oder in winmd-Dateien unterstützt. Informationen zur Verwendung der Alternative `VSDoc` formatieren, finden Sie unter [ \<Loc >](../ide/loc-javascript.md).  
  
     Das folgende Beispiel zeigt Inhalt in einen sidecardatei, die lokalisierte IntelliSense-Informationen enthält. Dies ist eine XML-Datei, die in einem kulturspezifischen Ordner, wie "JA" befindet. Der Ordner muss sich in demselben Speicherort wie die JS-Datei mit den `<loc>` Element. Der Dateiname der XML-Datei entsprechen muss die `filename` Parameter angegeben wird, der `<loc>` Element.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2. Fügen Sie in der JS-Datei den folgenden Code ein. Die `<loc>` Element muss vor allen möglichen Skripts deklariert werden, und folgt den gleichen Regeln für die Verwendung als die `<reference>` Element. Weitere Informationen finden Sie unter [JavaScript IntelliSense](../ide/javascript-intellisense.md) und [ \<Loc >](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3. Fügen Sie in der JS-Datei XML-dokumentationselemente und standardbeschreibungen aus. Legen Sie die `locid` Attributwerte entsprechend den entsprechenden `name` Attributwerte aus der sidecardatei. Die standardbeschreibungen werden durch lokalisierte IntelliSense-Informationen ersetzt werden, sofern diese verfügbar ist.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4. Um die XML-Dokumentationskommentare zu anzuzeigen, geben Sie den Namen und die öffnende Klammer der Funktion an, wie im folgenden Beispiel aus:  
  
    ```javascript  
    add(  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript-IntelliSense](../ide/javascript-intellisense.md)   
 [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Exemplarische Vorgehensweise: IntelliSense für JavaScript in ASP.NET](http://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
