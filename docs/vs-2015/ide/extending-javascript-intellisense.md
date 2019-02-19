---
title: Erweitern von JavaScript IntelliSense | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 81aab6e0eea808c8dcb9b37d5772144a863329aa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797446"
---
# <a name="extending-javascript-intellisense"></a>Erweitern von JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die JavaScript-IntelliSense-Erweiterbarkeit-Funktion können Sie zum Anpassen des IntelliSense-Ergebnisse in der JavaScript-Editor für Drittanbieter-Bibliotheken. Dies kann Entwickler die benutzerfreundlichkeit verbessern, die diese Bibliotheken verwenden.  
  
 JavaScript Language Service bietet IntelliSense-Funktionen für JavaScript-Bibliotheken von Drittanbietern, die zu einem Projekt hinzugefügt werden. Für die meisten Bibliotheken verwenden wird die Anweisungsvervollständigung automatisch vom Sprachdienst bereitgestellt. Die folgende Abbildung zeigt ein Beispiel für Anweisungsvervollständigung:  
  
 ![Beispiel für Anweisungsvervollständigung](../ide/media/js-intellisense-completion.png "Js_intellisense_completion")  
  
 Wenn Ihre Bibliothek eine Beschreibung der Variablen, Funktionen und Objekte in der standardmäßigen JavaScript-Kommentartags enthält (/ /), Sie automatisch profitieren zu können, in der Standardeinstellung von IntelliSense-Erweiterungs-Features, die beschreibende Informationen in einem Popup-Feld, das Bereitstellen rechts von Elementen in einer Liste oder wenn Sie die öffnende Klammer eines Funktionsaufrufs eingeben wird angezeigt. Die Kommentare in das Popup-Feld enthalten, die Beschreibung des Elements. Das folgende Beispiel zeigt das Popup-Feld für eine Vervollständigungsliste.  
  
 ![Beispiel für eine Quick Info Pop&#45;Box](../ide/media/js-intellisense-quickinfo.png "Js_intellisense_quickinfo")  
  
 Um die entwicklererfahrung weiter zu verbessern, empfiehlt es sich um die Bereitstellung von Typinformationen für Entwickler, die Sie im Popupmenü. Sie können die Informationen bereitstellen, mithilfe von JavaScript [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md) anstelle von standard-Kommentartags. Sie können XML-Dokumentationskommentare mithilfe von Kommentartags mit drei Schrägstrichen (/ / /) und einem definierten Satz von XML-Elemente hinzufügen.  
  
 Alternativ können Sie Informationen bereitstellen, mithilfe von JavaScript-IntelliSense-Erweiterbarkeit. Dieses Feature können Sie IntelliSense-Ergebnisse zu anpassen, indem Sie JavaScript-Erweiterungen erstellen und den Skriptkontext hinzufügen. In der Erweiterung, die eine JavaScript-Datei ist, abonnieren Sie Ereignisse, die von verfügbar gemacht werden die `intellisense` -Objekt des Sprachdiensts. JavaScript-IntelliSense-Erweiterbarkeit ist die bevorzugte Lösung für die Bibliotheken aus, wenn ein Verhaltensmuster in der Bibliothek für JavaScript Language Service wird verhindert, dass das gewünschte Maß IntelliSense-Unterstützung und eine Alternative zum deklarativen XML Kommentare zur Dokumentation ist auch erforderlich. Durch das Anpassen der IntelliSense-Ergebnisse, können Sie IntelliSense deutlich vereinfacht, unabhängig von der alle Verhaltensmuster erstellen, die der Sprachdienst-Standardfunktionen einschränken kann. Weitere Informationen finden Sie unter [Anweisungsvervollständigung für Bezeichner](../ide/statement-completion-for-identifiers.md).  
  
## <a name="adding-an-extension-to-the-script-context"></a>Hinzufügen einer Erweiterung auf den Skriptkontext  
 Für eine IntelliSense-Erweiterung ausgeführt werden muss sie den aktuellen Skriptkontext hinzugefügt werden. Die Erweiterung kann automatisch auf den Skriptkontext hinzugefügt werden, durch den automatischen Ermittlungsmechanismus, oder Sie können die Erweiterung auf den Skriptkontext manuell hinzufügen mithilfe von Verweisen auf Gruppen oder die Reference-Direktive.  
  
 Der Mechanismus für die automatische Ermittlung aktiviert den Sprachdienst, um Erweiterungen automatisch zu ermitteln, die die-Benennungskonvention folgen *Libraryname*. intellisense.js und, befinden sich in demselben Verzeichnis wie der Bibliothek die Erweiterung angewendet wird. Beispielsweise wäre eine gültige Erweiterung für die jQuery-Bibliothek jQuery.intellisense.js. Für mehr restriktiv jQuery-Erweiterungen können Sie den Dateinamen z. B. jQuery-1.7.1.intellisense.js (mit der Erweiterung hängt von der Version) oder jQuery.ui.intellisense.js (eine Erweiterung für eine Bereichsbezogene jQuery-Bibliothek) verwenden. Die restriktivste Version der Erweiterung wird verwendet, wenn mehr als eine Erweiterung für eine bestimmte Bibliothek gefunden wird.  
  
 Wenn Sie die Erweiterung für die JavaScript-Projektdateien verwenden möchten, können Sie stattdessen auswählen, zum Hinzufügen der Erweiterung zu einer Vergleichsgruppe hinzu. Es gibt mehrere Typen von Verweisen auf Gruppen, entweder, die implizite Verweise enthalten, und die dedizierten workerserver Verweise enthalten. Um eine Erweiterung hinzufügen, müssen Sie normalerweise eine Gruppe verweist implizit auf die Datei entweder hinzugefügt **implizit (Windows)**, **implizit (Internet)**. Implizite Verweise werden im Bereich für jede JS-Datei, die im Code-Editor geöffnet. Wenn Sie diese Methode verwenden, müssen Sie sowohl die Erweiterung und die Datei, die die Erweiterung zu ergänzen, wird hinzugefügt.  
  
 Verwenden der **IntelliSense** auf der Seite die **Optionen** Dialogfeld zum Hinzufügen einer Erweiterung als einer Vergleichsgruppe hinzu. Sie können den Zugriff auf die **IntelliSense** Seite durch Auswahl **Tools**, **Optionen** auf der Menüleiste, und klicken Sie dann auswählen **Text-Editor**, **JavaScript**, **IntelliSense**, **Verweise**. Weitere Informationen zum Verweisen auf Gruppen finden Sie unter [JavaScript IntelliSense](../ide/javascript-intellisense.md) und [Optionen, Text-Editor, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
 Wenn Sie die Erweiterung für einen bestimmten Satz von Dateien verwenden möchten, verwenden Sie eine Reference-Direktive. Wenn Sie diese Methode verwenden, müssen Sie sowohl für die Erweiterung als auch für die Datei, die die Erweiterung zu ergänzen, wird zu verweisen. Weitere Informationen zum Verwenden der Reference-Direktive, finden Sie unter [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
## <a name="handling-intellisense-events"></a>Behandeln von Ereignissen von IntelliSense  
 Die Erweiterbarkeitsfunktion können Sie IntelliSense-Ergebnisse anpassen, indem Sie beim Abonnieren von Ereignissen wie z. B. die `statementcompletion` Ereignis des Sprachdiensts `intellisense` Objekt. Das folgende Beispiel zeigt eine einfache Erweiterung, die vom Sprachdienst verwendet wird, um Elemente auszublenden, die mit einem Unterstrich aus Anweisungsvervollständigung beginnen. Dieser Code ist in underscorefilter.js enthalten und befindet sich in der \\ \\ *Visual Studio-Installationspfad*\JavaScript\References-Ordner.  
  
```javascript  
intellisense.addEventListener('statementcompletion', function (event) {  
    if (event.targetName === "this") return;  
  
    var filterRegex;  
  
    if (event.target === undefined || event.target === window)  
        filterRegex = /^_.*\d{2,}/;  
    else  
        filterRegex = /^_.*/;  
  
    event.items = event.items.filter(function (item) {  
        return !filterRegex.test(item.name);  
    });  
});  
```  
  
 Im obigen Code wird die Erweiterung überprüft die [TargetName Eigenschaft](#TargetName) und [Zieleigenschaft](#Target) Eigenschaften der `statementcompletion` Ereignisobjekt zum Ausschließen von Objekten wie z. B. `this` und `window`, und stellen Sie sicher, dass eine gültige Anweisungsvervollständigungsliste identifiziert werden kann. Wenn eine Vervollständigungsliste identifiziert werden kann, wird die Erweiterung aktualisiert die Anweisungsvervollständigung [-Elementeigenschaft](#Items) Auflistung durch die Filterung Elemente, die mit einem Unterstrich beginnen.  
  
 Weitere Beispiele finden Sie in der \\ \\ *Visual Studio-Installationspfad*\JavaScript\References-Ordner. Die showPlainComments.js-Datei in diesem Ordner enthält Beispiele für die Verwendung von anderen Ereignissen zu Standard-IntelliSense-Unterstützung für den standardmäßigen JavaScript-Kommentartags (/ /). Wie underscorefilter.js showPlainComments.js ist bereits als eine Erweiterung für die Arbeit zur Verfügung, und sehen Sie die resultierende IntelliSense-Informationen beim Kommentartags für Variablen, Funktionen und Objekte in Ihrem Code verwenden. Weitere Beispiele finden Sie unter [Codebeispiele](#CodeExamples).  
  
> [!WARNING]
>  Wenn Sie die Erweiterungsdateien in Visual Studio enthaltenen ändern, können Sie JavaScript-IntelliSense oder die Funktion, die von der Erweiterung unterstützten deaktivieren.  
  
 Sie können Handler für die folgenden Ereignistypen in Ihrem Erweiterungscode erstellen, mit `addEventListener`:  
  
- `statementcompletion`, einen Handler für ein Abschlussereignis Anweisung hinzugefügt. Anweisungsvervollständigung enthält eine Liste von Elementen für einen bestimmten Typ, der angezeigt wird, nachdem Sie ein Sonderzeichen wie z. B. einen Punkt (.) eingeben, oder eine Liste der Bezeichner, die angezeigt wird, während der Eingabe, oder drücken Sie STRG + J. Der Handler empfängt ein Ereignisobjekt des Typs `CompletionEvent`, unterstützt die folgenden Member: [-Elementeigenschaft](#Items), [Zieleigenschaft](#Target), [TargetName Eigenschaft](#TargetName), und [Bereich Eigenschaft](#Scope).  
  
- `signaturehelp`, die Fügt einen Ereignishandler für die IntelliSense-Parameterinformationen. Informationen zu den Parametern erhalten Sie Informationen zu Anzahl, Namen und Typen der Parameter, die von einer Funktion erforderlich. Der Handler empfängt ein Ereignisobjekt des Typs `SignatureHelpEvent`, unterstützt die folgenden Member: [Zieleigenschaft](#Target), [ParentObject Eigenschaft](#ParentObject), [FunctionComments-Eigenschaft](#FunctionComments), [FunctionHelp Eigenschaft](#FunctionHelp).  
  
- `statementcompletionhint`, die für IntelliSense-QuickInfo Fügt einen Handler hinzu. Das QuickInfo-Popupfeld zeigt die vollständige Deklaration für Bezeichner in Ihrem Code. Der Handler empfängt ein Ereignisobjekt des Typs `CompletionHintEvent`, unterstützt die folgenden Member: [CompletionItem Eigenschaft](#CompletionItem), und [SymbolHelp Eigenschaft](#SymbolHelp).  
  
  Beispiele, die IntelliSense-Features wie Anweisungsvervollständigung, Informationen zu den Parametern und QuickInfo anzeigen, finden Sie unter [Verwenden von IntelliSense](../ide/using-intellisense.md).  
  
> [!NOTE]
>  In JavaScript bezieht sich auf das Popup-Feld, das rechts vom eine Vervollständigungsliste angezeigt wird. "QuickInfo". Sie können keine QuickInfo manuell aufrufen.  
  
##  <a name="intellisenseObject"></a> IntelliSense-Objekt  
 Die folgende Tabelle zeigt die verfügbaren Funktionen für die `intellisense` Objekt. Die `intellisense` Objekt steht nur zur Entwurfszeit.  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|`addEventListener(type, handler);`|Fügt einen Ereignishandler für ein IntelliSense-Ereignis hinzu.<br /><br /> `type` ist ein Zeichenfolgenwert. Gültige Werte sind u.a. `statementcompletion`, `signaturehelp` und `statementcompletionhint`.<br /><br /> `handler` ist eine Ereignishandlerfunktion, die empfängt ein Ereignisobjekt, eines der folgenden Typen:<br /><br /> -   `CompletionEvent`, verwendet für die `statementcompletion` Ereignis.<br />-   `SignatureHelpEvent`, verwendet für die `signaturehelp` Ereignis.<br />-   `CompletionHintEvent`, verwendet für die `statementcompletionhint` Ereignis.<br /><br /> Beispiele, die diese Funktion verwenden, finden Sie unter [Codebeispiele](#CodeExamples).|  
|`annotate(obj, doc);`|Gibt die Dokumentation für ein Objekt durch Kopieren der Kommentare zur Dokumentation von einem Objekt in ein anderes Objekt an.<br /><br /> `obj` Gibt das Objekt, in der Dokumentation zu kopieren.<br /><br /> `doc` Gibt das Objekt aus der Dokumentation zu kopieren.<br /><br /> Ein Beispiel, das zeigt, wie Sie diese Funktion verwenden, finden Sie unter [Hinzufügen von IntelliSense Anmerkungen](#Annotations).|  
|`getFunctionComments(func);`|Gibt die Kommentare für eine angegebene Funktion zurück.<br /><br /> `func` Gibt die Funktion für die Kommentare zurückgegeben werden.<br /><br /> Sie können festlegen, die `func` Parameter, indem `completionItem.value`.<br /><br /> Das zurückgegebene `functionComments` Objekt enthält die folgenden Elemente: `above`, `inside`, und `paramComment`. Weitere Informationen finden Sie unter den [FunctionComments Eigenschaft](#FunctionComments) Eigenschaft.<br /><br /> `getFunctionComments` kann nur aufgerufen werden, in einem Ereignishandler, die von registriert werden `addEventListener`.<br /><br /> Ein Beispiel, das zeigt, wie Sie diese Funktion verwenden, finden Sie unter \\ \\ *Visual Studio-Installationspfad*\JavaScript\References\showPlainComments.js.|  
|`logMessage(msg);`|Sendet diagnosemeldungen im Ausgabefenster.<br /><br /> `msg` ist eine Zeichenfolge, die die Nachricht enthält.<br /><br /> Ein Beispiel, das zeigt, wie Sie diese Funktion verwenden, finden Sie unter [Senden von Nachrichten an das Fenster "Ausgabe"](#Logging).|  
|`nullWithCompletionsOf(value);`|Gibt einen speziellen null-Wert für die die Vervollständigungsliste wird durch das übergebene Objekt bestimmt der `value` Parameter.<br /><br /> `value` Bestimmt die Vervollständigungsliste für den zurückgegebenen Wert an. `value` Jeder Typ kann sein.<br /><br /> Der Rückgabewert von null wird als Null, während der Entwurfsphase behandelt, aber die Vervollständigungsliste für den zurückgegebenen Wert entspricht der Vervollständigungsliste für die `value` Parameter.<br /><br /> Eine Verwendung für diese Funktion ist, geben Sie IntelliSense für einen Rückgabewert, wenn der Rückgabetyp zur Laufzeit vorhersagbar ist, aber der Rückgabewert ist `null` zur Entwurfszeit.|  
|`redirectDefinition(func, definition);`|Weist IntelliSense zur Verwendung der Funktion für die angegebene Definition anstelle der ursprünglichen Func-Funktion, wenn Parameterhilfe oder **Gehe zu Definition** angefordert wird.<br /><br /> `func` Gibt die Zielfunktion.<br /><br /> `definition` Gibt die Funktion, die anstelle der Zielfunktion für Informationen zu den Parametern verwendet werden und **Gehe zu Definition**.|  
|`setCallContext(func, thisArg);`|Legt fest, die Aufrufkontext, oder den Bereich, für die angegebene Funktion.<br /><br /> `func` Gibt die Funktion für die beim Festlegen des Bereichs.<br /><br /> `thisArg` ist ein Objekt, dem literal die `this` ,-Schlüsselwort verweisen kann, die den neuen Bereich für den Member angibt. Sie können z. B. in diesen Parameter zu übergebenden Argumente einschließen, `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` bietet ähnliche `Function.prototype.bind`, außer dass sie nur für die Entwurfszeit-IntelliSense-Unterstützung verwendet. Sie können `setCallContext` zum Festlegen des Gültigkeitsbereichs der Funktion müssen Sie einen Aufruf von Code zu simulieren, die andernfalls nicht erreichbar, ist, damit beim Aufruf der Funktion, wird der Funktionsaufruf den richtigen Bereich und die Argumente enthalten.|  
|`undefinedWithCompletionsOf(value);`|Gibt einen speziellen nicht definierten Wert, der die Vervollständigungsliste wird für die durch das übergebene Objekt bestimmt der `value` Parameter.<br /><br /> `value` Bestimmt die Vervollständigungsliste für den zurückgegebenen Wert an. `value` Jeder Typ kann sein.<br /><br /> Der undefined zurückgegeben Wert behandelt wird als nicht definiert, während der Entwurfszeit, aber auf den Abschluss Liste für den zurückgegebenen Wert entspricht der Vervollständigungsliste für die `value` Parameter.<br /><br /> Eine Verwendung für diese Funktion ist IntelliSense für einen Rückgabewert angeben, wenn der Rückgabetyp zur Laufzeit vorhersagbar ist, aber der Rückgabewert zur Entwurfszeit nicht definiert ist.|  
|`version()`|Die Visual Studio-Version zurückgegeben.|  
  
## <a name="event-members"></a>Ereignismember  
 Die folgenden Abschnitte beschreiben die Elemente, die in das Ereignisobjekt für die folgenden Ereignisse verfügbar gemacht werden: `statementcompletion`, `signaturehelp`, und `statementcompletionhint`.  
  
###  <a name="CompletionItem"></a> CompletionItem-Eigenschaft  
 Gibt den Bezeichner, bekannt als die vervollständigungselement, für die eine QuickInfo-Popupfeld angefordert werden. Diese Eigenschaft steht für die `statementcompletionhint` Ereignisobjekt und für die [-Elementeigenschaft](#Items) Eigenschaft der `statementcompletion` Ereignisobjekt.  
  
 Rückgabewert: `completionItem` Objekt  
  
 Folgende Elemente gehören die `completionItem` Objekt:  
  
-   `name`. Lese-/Schreibzugriff, bei der Verwendung in der `items` Auflistung, andernfalls schreibgeschützt. Gibt eine Zeichenfolge, die dem Abschlusselement identifiziert.  
  
-   `kind`. Lese-/Schreibzugriff, bei der Verwendung in der `items` Auflistung, andernfalls schreibgeschützt. Gibt eine Zeichenfolge, die den Typ des Elements Vervollständigung darstellt. Die möglichen Werte sind-Methode, Feld, Eigenschaft, Parameter, Variablen, und reserviert.  
  
-   `glyph`. Lese-/Schreibzugriff, bei der Verwendung in der `items` Auflistung, andernfalls schreibgeschützt. Gibt eine Zeichenfolge, die ein Symbol darstellt, die in der Vervollständigungsliste angezeigt wird. Die möglichen Werte für `glyph` verwenden das folgende Format: Visual Studio:*GlyphType*, wobei *GlyphType* entspricht die sprachunabhängige Elemente in der <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> Enumeration. Z. B. `vs:GlyphGroupMethod` ist ein möglicher Wert für `glyph`. Wenn `glyph` nicht festgelegt ist, die `kind` -Eigenschaft bestimmt das Standardsymbol.  
  
-   `parentObject`. Schreibgeschützt. Gibt das übergeordnete Objekt zurück.  
  
-   `value`. Schreibgeschützt. Gibt ein Objekt, das den Wert des Elements der Vervollständigung darstellt.  
  
-   `comments`. Schreibgeschützt. Gibt eine Zeichenfolge, die die Kommentare enthält, die über das Feld oder Variable.  
  
-   `scope`. Schreibgeschützt. Gibt den Bereich des Elements der Vervollständigung zurück. Die möglichen Werte sind global, lokal, Parameter und Member.  
  
###  <a name="Items"></a> -Elementeigenschaft  
 Übernimmt oder bestimmt das Array der Anweisung Vervollständigungselemente. Jedes Element im Array ist ein [CompletionItem Eigenschaft](#CompletionItem) Objekt. Die `items` Eigenschaft steht für die `statementcompletion` Ereignisobjekt.  
  
 Rückgabewert: Array  
  
###  <a name="FunctionComments"></a> FunctionComments-Eigenschaft  
 Gibt die Kommentare für die Funktion zurück. Diese Eigenschaft steht für die `signaturehelp` Ereignisobjekt.  
  
 Rückgabewert: `comments` Objekt  
  
 Folgende Elemente gehören die `comments` Objekt:  
  
-   `above`. Gibt die Kommentare über die Funktion zurück.  
  
-   `inside`. Gibt die Kommentare innerhalb der Funktion, die in der Regel in VSDoc-Format zurück.  
  
-   `paramComments`. Gibt ein Array, der Kommentare für jeden Parameter in der Funktion darstellt. Die Elemente des Arrays enthalten:  
  
    -   `name`. Gibt eine Zeichenfolge, die den Namen des Parameters darstellt.  
  
    -   `comment`. Gibt eine Zeichenfolge, die die Parameter-Kommentar enthält.  
  
###  <a name="FunctionHelp"></a> FunctionHelp-Eigenschaft  
 Gibt die Hilfe für die Funktion zurück. Diese Eigenschaft steht für die `signaturehelp` Ereignisobjekt.  
  
 Rückgabewert: `functionHelp` Objekt  
  
 Folgende Elemente gehören die `functionHelp` Objekt:  
  
-   `functionName`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die den Namen der Funktion enthält.  
  
-   `signatures`. Lese-/Schreibzugriff. Übernimmt oder bestimmt das Array von Funktionssignaturen. Jedes Element im Array ist ein `signature` Objekt. Einige `signature` Eigenschaften, z. B. `locid`, entsprechen allgemeinen [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md) Attribute.  
  
     Die Mitglieder der `signature` Objekt einfügen möchten:  
  
    -   `description`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die die Funktion beschreibt.  
  
    -   `locid`. Lese-/Schreibzugriff. Gibt einen Zeichenfolgenbezeichner, der Lokalisierungsinformationen über die Funktion enthält.  
  
    -   `helpKeyword`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die das Hilfeschlüsselwort enthält.  
  
    -   `externalFile`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die die Datei darstellt, die Member-ID. enthält  
  
    -   `externalid`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die die Element-ID der Funktion darstellt.  
  
    -   `params`. Lese-/Schreibzugriff. Ruft ab oder legt das Array von Parametern für die Funktion fest. Jedes Element im Parameterarray ist eine `parameter` Objekt mit Eigenschaften, die die folgenden Attribute des entsprechen, den [ \<Param >](../ide/param-javascript.md) Element:  
  
        -   `name`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die den Namen des Parameters darstellt.  
  
        -   `type`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die den Parameter darstellt.  
  
        -   `elementType`. Lese-/Schreibzugriff. Wenn der Typ ist `Array`, gibt eine Zeichenfolge, die den Typ der Elemente im Array darstellt.  
  
        -   `description`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die die Parameter beschreibt.  
  
        -   `locid`. Lese-/Schreibzugriff. Gibt einen Zeichenfolgenbezeichner, der Lokalisierungsinformationen über die Funktion enthält.  
  
        -   `optional`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die angibt, ob der Parameter optional ist. `true` Gibt an, dass der Parameter optional ist; `false` gibt an, dass dies nicht der Fall.  
  
    -   `returnValue`. Lese-/Schreibzugriff. Übernimmt oder bestimmt ein Rückgabewert-Objekt mit Eigenschaften, entsprechen die folgenden Attribute des der [ \<gibt >](../ide/returns-javascript.md) Element:  
  
        -   `type`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die den Rückgabetyp darstellt.  
  
        -   `elementType`. Lese-/Schreibzugriff. Wenn der Typ ist `Array`, gibt eine Zeichenfolge, die den Typ der Elemente im Array darstellt.  
  
        -   `description`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die den Rückgabewert beschreibt.  
  
        -   `locid`. Lese-/Schreibzugriff. Gibt einen Zeichenfolgenbezeichner, der Lokalisierungsinformationen über die Funktion enthält.  
  
        -   `helpKeyword`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die das Hilfeschlüsselwort enthält.  
  
        -   `externalFile`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die die Datei darstellt, die Member-ID. enthält  
  
        -   `externalid`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die die Element-ID der Funktion darstellt.  
  
###  <a name="ParentObject"></a> ParentObject-Eigenschaft  
 Gibt das übergeordnete Objekt einer Memberfunktion zurück. Beispielsweise `document.getElementByID`, `parentObject` gibt die `document` Objekt. Diese Eigenschaft steht für die `signaturehelp` Ereignisobjekt.  
  
 Rückgabewert: Objekt  
  
###  <a name="Target"></a> Zieleigenschaft  
 Gibt ein Objekt, das Element auf der linken Seite des Zeichens, Trigger, darstellt, die einen Punkt (.) ist. Für Funktionen `target` gibt die Funktion für die Parameterinformationen angefordert wird. Diese Eigenschaft steht für die `statementcompletion` und `signaturehelp` solcher Objekte.  
  
 Rückgabewert: Objekt  
  
###  <a name="TargetName"></a> TargetName-Eigenschaft  
 Gibt eine Zeichenfolge, die das Ziel darstellt. "This.", z. B. für `targetName` gibt "this" zurück. Für "A.B" (wenn der Cursor hinter "B") `targetName` "B" zurückgegeben. Diese Eigenschaft steht für die `statementcompletion` Ereignisobjekt.  
  
 Rückgabewert: Zeichenfolge  
  
###  <a name="SymbolHelp"></a> SymbolHelp-Eigenschaft  
 Gibt zurück, dem Abschlusselement für das eine QuickInfo-Popupfeld angefordert wird. Diese Eigenschaft steht für die `statementcompletionhint` Ereignisobjekt.  
  
 Rückgabewert: `symbolHelp` Objekt.  
  
 Einige Eigenschaften der `symbolHelp` Objekt, z. B. `locid`, entsprechen allgemeinen [XML-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md) Attribute.  
  
 Folgende Elemente gehören die `symbolHelp` Objekt:  
  
-   `name`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die den Namen des Bezeichners enthält.  
  
-   `symbolType`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die den Symboltyp darstellt. Mögliche Werte sind unbekannt, boolescher Wert, Zahl, Zeichenfolge, Objekt, Funktion, Array, Datum und Regex.  
  
-   `symbolDisplayType`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die der Typname enthält angezeigt. Wenn `symbolDisplayType` ist nicht festgelegt, `symbolType` verwendet wird.  
  
-   `elementType`. Lese-/Schreibzugriff. Wenn die `symbolType` ist `Array`, gibt eine Zeichenfolge, die den Typ der Elemente im Array darstellt.  
  
-   `scope`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die den Bereich des Symbols darstellt. Mögliche Werte sind global, lokal, Parameter und Member.  
  
-   `description`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die eine Beschreibung des Symbols enthält, zurück.  
  
-   `locid`. Lese-/Schreibzugriff. Gibt einen Zeichenfolgenbezeichner, der Lokalisierungsinformationen über das Symbol enthält.  
  
-   `helpKeyword`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die das Hilfeschlüsselwort enthält.  
  
-   `externalFile`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die die Datei darstellt, die Member-ID. enthält  
  
-   `externalid`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge, die die Element-ID des Symbols darstellt.  
  
-   `functionHelp`. Lese-/Schreibzugriff. Gibt eine [FunctionHelp Eigenschaft](#FunctionHelp), die enthalten möglicherweise Informationen bei der `symbolType` Funktion.  
  
###  <a name="Scope"></a> Scope-Eigenschaft  
 Gibt den Bereich "Abschluss" des Ereignisses an. Die möglichen Werte für den Abschluss Bereich sind global und Member. Diese Eigenschaft steht für die `statementcompletion` Ereignisobjekt.  
  
 Rückgabewert: Zeichenfolge  
  
## <a name="debugging-intellisense-extensions"></a>Debuggen von IntelliSense-Erweiterungen  
 Sie können die Erweiterungen nicht debuggen, jedoch können Sie die [Intellisense-Objekt](#intellisenseObject) Funktion zum Senden von Informationen an das Ausgabefenster von Visual Studio-Fenster. Ein Beispiel, das zeigt, wie Sie diese Funktion verwenden, finden Sie unter [Senden von Nachrichten an das Fenster "Ausgabe"](#Logging) weiter unten in diesem Thema. Für `logMessage` funktioniert, muss mindestens ein Ereignishandler in einer Erweiterung registriert werden.  
  
##  <a name="CodeExamples"></a> Codebeispiele  
 Dieser Abschnitt enthält Codebeispiele, die zeigen, wie Sie mit der IntelliSense-Erweiterbarkeits-APIs. Es gibt auch andere Möglichkeiten, diese APIs verwenden. Weitere Beispiele finden Sie unter den folgenden Dateien in die \\ \\ *Visual Studio-Installationspfad*\JavaScript\References-Ordner. Diese arbeiten Beispiele von JavaScript Language Service.  
  
-   underscoreFilter.js. Dieser Code wird die Private Member von IntelliSense ausgeblendet. Es enthält die Ereignishandler für die `statementcompletion` Ereignis.  
  
-   showPlainComments.js. Dieser Code bietet IntelliSense-Unterstützung für standard-Kommentare. Es enthält die Ereignishandler für die `signaturehelp` und `statementcompletionhint` Ereignisse.  
  
###  <a name="Annotations"></a> Hinzufügen von IntelliSense-Anmerkungen  
 Das folgende Verfahren zeigt, wie Dokumentation IntelliSense-Unterstützung für eine Drittanbieter-Bibliothek bereitgestellt werden, ohne die Bibliothek direkt ändern. Zu diesem Zweck können Sie `intellisense.annotate` in einer Erweiterung.  
  
 Damit dieses Beispiel funktioniert, benötigen Sie die folgenden JavaScript-Dateien im Projekt:  
  
-   demoLib.js, d.h. eine Projektdatei, die eine Drittanbieter-Bibliothek darstellt.  
  
-   demoLib.intellisense.js, das den IntelliSense-Erweiterung ist. Diese Datei muss nicht in das Projekt aufgenommen werden, muss sich aber im gleichen Ordner wie "exampleLib.js" befinden.  
  
-   appCode.js, eine Projektdatei, die App-Code darstellt.  
  
##### <a name="to-add-an-intellisense-annotation"></a>Zum Hinzufügen einer IntelliSense-Anmerkung  
  
1.  Fügen Sie den folgenden Code, um demoLib.js.  
  
    ```javascript  
    function someFunc(a) { };  
    var rectangle;  
  
    ```  
  
2.  Fügen Sie den folgenden Code, um demoLib.intellisense.js.  
  
    ```javascript  
    intellisense.annotate(someFunc, function (a) {  
        /// <signature>  
        /// <summary>Description of someFunc</summary>  
        /// <param name="a">Param a</param>  
        /// </signature>  
    });  
  
    intellisense.annotate(window, {  
        // This is a comment on a global variable named rectangle.  
        rectangle: undefined  
    });  
    ```  
  
3.  Fügen Sie die folgende Reference-Anweisung als erste Zeile in appCode.js hinzu. Der hier verwendete Pfad gibt an, dass sich die JavaScript-Dateien im gleichen Ordner befinden.  
  
    ```javascript  
    /// <reference path="demoLib.js" />  
  
    ```  
  
4.  Geben Sie in appCode.js den folgenden Code ein. Sie sehen, dass die XML-Dokumentationskommentare in der Erweiterung, die als IntelliSense-ParameterInfo angezeigt.  
  
     ![Beispiel für die Verwendung von intellisense.annotate](../ide/media/js-intellisense-annotate-paraminfo.png "Js_intellisense_annotate_paraminfo")  
  
5.  Geben Sie in appCode.js den folgenden Code ein. Während der Eingabe, sehen Sie die standard-Kommentare in der Erweiterung, die als IntelliSense-QuickInfo angezeigt.  
  
     ![Beispiel für die Verwendung von intellisense.annotate](../ide/media/js-intellisense-annotations.png "Js_intellisense_annotations")  
  
###  <a name="Logging"></a> Senden von Nachrichten an das Fenster "Ausgabe"  
 Das folgende Verfahren veranschaulicht das Senden von Nachrichten an das Fenster "Ausgabe". Sie können Nachrichten zum Debuggen von IntelliSense-Erweiterungen senden.  
  
 Damit dieses Beispiel funktioniert, benötigen Sie die folgenden JavaScript-Dateien im Projekt:  
  
-   "examplelib.js", d.h. eine Projektdatei, die eine Drittanbieter-Bibliothek darstellt.  
  
-   exampleLib.intellisense.js, das den IntelliSense-Erweiterung ist. Diese Datei muss nicht in das Projekt aufgenommen werden, muss sich aber im gleichen Ordner wie "exampleLib.js" befinden.  
  
-   appCode.js, eine Projektdatei, die App-Code darstellt.  
  
##### <a name="to-send-a-message-to-the-output-window"></a>Zum Senden einer Nachricht an das Ausgabefenster  
  
1.  Fügen Sie den folgenden Code, um "examplelib.js".  
  
    ```javascript  
    var someVar = {  
        a: 1,  
        b: 'hello'  
    };  
    ```  
  
2.  Fügen Sie den folgenden Code, um exampleLib.intellisense.js.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        // Prints out statement completion info: Either (1) the member   
        // list, if the trigger character was typed, or (2) the   
        // statement completion identifiers.  
        // e.target represents the object left of the trigger character.  
        intellisense.logMessage(  
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');  
  
        // Prints out all statement completion items.  
        e.items.forEach(function (item) {  
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);  
        });  
    });  
    ```  
  
3.  Fügen Sie die folgende Reference-Direktive als erste Zeile in appCode.js hinzu. Der hier verwendete Pfad gibt an, dass sich die JavaScript-Dateien im gleichen Ordner befinden.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  Wählen Sie im Ausgabefenster **JavaScript Language Service** in die **Ausgabe anzeigen von** Liste. (Wählen Sie zum Anzeigen im Ausgabefenster **Ausgabe** aus dem Menü "Ansicht".)  
  
5.  Geben Sie in appCode.js den folgenden Code ein. Während der Eingabe, zeigt das Fenster "Ausgabe" Nachrichten aus den Sprachdienst. Die erste Nachricht in das Fenster "Ausgabe" gibt an, dass die Anweisungsvervollständigung für den aktuellen Bereich angefordert wurde.  
  
    ```javascript  
    some  
    ```  
  
     Es folgt eine Teilansicht der Ausgabe sehen Sie.  
  
    ```scr  
    03:16:14.3113: statement completion for current scope requested  
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined  
  
    …  
    ```  
  
6.  Wählen Sie die **alle löschen** Schaltfläche im Ausgabefenster angezeigt.  
  
7.  Geben Sie den folgenden Code ein. Die erste Nachricht in das Fenster "Ausgabe" zeigt an, dass es sich bei eine Memberliste angefordert wurde.  
  
    ```javascript  
    someVar.  
    ```  
  
     Es folgt eine Teilansicht der Ausgabe sehen Sie:  
  
    ```scr  
    03:17:43.4032: member list requested, target: someVar  
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1  
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello  
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:  
  
    …  
    ```  
  
###  <a name="Icons"></a> Ändern die IntelliSense-Symbole  
 Das folgende Verfahren zeigt, wie so ändern Sie die Symbole, die von IntelliSense wird standardmäßig angezeigt wird. Dies kann nützlich sein, wenn Sie angeben, dass IntelliSense-Informationen zur Bibliothek-spezifische Konzepte beziehen, z. B. Namespaces, Klassen, Schnittstellen und Enumerationen.  
  
 Symbol "verfügbar"-Werte finden Sie unter <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>.  
  
 Damit dieses Beispiel funktioniert, benötigen Sie die folgenden JavaScript-Dateien im Projekt:  
  
-   in der Datei "examplelib.js", die ein Projekt ist diese Represens ein Drittanbieter-Bibliothek.  
  
-   exampleLib.intellisense.js, das den IntelliSense-Erweiterung ist. Diese Datei muss nicht in das Projekt aufgenommen werden, muss sich aber im gleichen Ordner wie "exampleLib.js" befinden.  
  
-   appCode.js, eine Projektdatei, die App-Code darstellt.  
  
##### <a name="to-change-the-icons"></a>So ändern Sie die Symbole  
  
1.  Fügen Sie den folgenden Code, um "examplelib.js".  
  
    ```javascript  
    function Namespace(name) {  
        this._isNamespace = true;  
        window[name] = this;  
    };  
  
    function Enum(values) {  
        var e = Object.create(values);  
        e._isEnum = true;  
        return e;  
    };  
  
    var SomeNamespace = new Namespace('SomeNamespace');  
    // A constructor function is considered a class.  
    SomeNamespace.SomeClass1 = function () { }  
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });  
    ```  
  
2.  Fügen Sie den folgenden Code, um exampleLib.intellisense.js.  
  
    ```javascript  
    intellisense.addEventListener('statementcompletion', function (e) {  
        e.items.forEach(function (item) {  
            // Detect a namespace by using the _isNamespace flag.  
            if (item.value && item.value._isNamespace) {  
                item.glyph = 'vs:GlyphGroupNamespace';  
                }  
  
            if (item.parentObject && item.parentObject._isNamespace) {  
                // The item is a member of a namespace.   
  
                // All constructor functions that are part of a namespace   
                // are considered classes.   
                // A constructor function starts with  
                // an uppercase letter by convention.    
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()   
                    == item.name[0])) {  
                    item.glyph = 'vs:GlyphGroupClass';  
                }  
  
                // Detect an enumeration by using the _isEnum flag.  
                if (item.value && item.value._isEnum) {  
                    item.glyph = 'vs:GlyphGroupEnum';  
                }  
            }  
        });  
    });  
  
    intellisense.addEventListener('statementcompletionhint', function (e) {  
        if (e.completionItem.value) {  
            if (e.completionItem.value._isNamespace) {  
                e.symbolHelp.symbolDisplayType = 'Namespace';  
            }  
            if (e.completionItem.value._isEnum) {  
                e.symbolHelp.symbolDisplayType = 'Enum';  
            }  
        }  
    });  
    ```  
  
3.  Fügen Sie die folgende Reference-Direktive als erste Zeile in appCode.js hinzu. Der hier verwendete Pfad gibt an, dass sich die JavaScript-Dateien im gleichen Ordner befinden.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4.  Geben Sie in appCode.js den folgenden Code ein. Während der Eingabe, werden Sie feststellen, dass das Symbol für den Namespace, um geändert hat "{}", wie in dient C#.  
  
     ![Beispiel für die Verwendung der Symboleigenschaft](../ide/media/js-intellisense-glyph-namespace.png "Js_intellisense_glyph_namespace")  
  
5.  Geben Sie in appCode.js den folgenden Code ein. Während der Eingabe, sehen Sie ein neues Symbol "Enumeration" für das Enum1-Element, und ein neues Klassensymbol für den SomeClass1-Member.  
  
     ![Beispiel zur Verwendung der Symboleigenschaft](../ide/media/js-intellisense-glyph-class-enum.png "Js_intellisense_glyph_class_enum")  
  
###  <a name="Overriding"></a> Vermeiden von Run-Time-Auswirkungen auf IntelliSense-Ergebnisse  
 JavaScript Language Service führt Code aus, um die IntelliSense-Informationen dynamisch bereitzustellen. Daher kann gelegentlich Laufzeitverhalten gewünschten Ergebnisse beeinflussen. Das folgende Verfahren veranschaulicht das Überschreiben von IntelliSense-Ergebnisse, wenn der falsche IntelliSense Laufzeitverhalten führt.  
  
 Damit dieses Beispiel funktioniert, benötigen Sie die folgenden JavaScript-Dateien im Projekt:  
  
-   "examplelib.js", d.h. eine Projektdatei, die eine Drittanbieter-Bibliothek darstellt.  
  
-   exampleLib.intellisense.js, das den IntelliSense-Erweiterung ist. Diese Datei muss nicht in das Projekt aufgenommen werden, muss sich aber im gleichen Ordner wie "exampleLib.js" befinden.  
  
-   appCode.js, eine Projektdatei, die App-Code darstellt.  
  
##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Um zur Laufzeit Auswirkungen auf IntelliSense-Ergebnisse zu vermeiden.  
  
1.  Fügen Sie den folgenden Code, um "examplelib.js".  
  
    ```javascript  
    function after(count, func) {  
        return function () {  
            if (--times < 1) {  
                return func.apply(this, arguments);  
            }  
        };  
    };  
    ```  
  
     Im vorangehenden Code ignoriert der umschlossene Funktion basierend auf den Wert des ersten Aufrufe `count`, und keine Ergebnisse zurückgeben.  
  
2.  Fügen Sie die folgende Reference-Anweisung als erste Zeile in appCode.js hinzu. Der hier verwendete Pfad gibt an, dass sich die JavaScript-Dateien im gleichen Ordner befinden.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
3.  Geben Sie in appCode.js den folgenden Code ein. Die bezeichnerliste wird anstelle von IntelliSense angezeigt, da die umschlossene Funktion nie aufgerufen wird, bedeutet, dass, die `throttled` Funktion keine Ergebnisse zurück.  
  
     ![Beispiel zum Überschreiben der Intellisense-Ergebnisse](../ide/media/js-intellisense-override.png "Js_intellisense_override")  
  
4.  Fügen Sie den folgenden Code, um exampleLib.intellisense.js. Dadurch wird das Verhalten während der Entwurfszeit geändert, damit, dass IntelliSense für die umschlossene Funktion angezeigt wird, wie erwartet.  
  
    ```javascript  
    window.after = function (count, func) {  
        // Just return func.   
        return func;  
    };  
    ```  
  
5.  Testen Sie die Ergebnisse in appcode.js hinzu Geben Sie den gleichen Code, den Sie zuvor eingegeben. Dieses Mal bietet IntelliSense die gewünschte Informationen.  
  
     ![Beispiel zum Überschreiben der IntelliSense-Ergebnisse](../ide/media/js-intellisense-override-fixed.png "Js_intellisense_override_fixed")  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript-IntelliSense](../ide/javascript-intellisense.md)   
 [Anweisungsvervollständigung für Bezeichner](../ide/statement-completion-for-identifiers.md)
