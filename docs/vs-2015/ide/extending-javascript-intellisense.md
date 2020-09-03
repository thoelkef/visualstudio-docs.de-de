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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf16b6fdc307e11875f30cfad6e4bb35580b0b04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665754"
---
# <a name="extending-javascript-intellisense"></a>Erweitern von JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das JavaScript IntelliSense-Erweiterbarkeits Feature ermöglicht Ihnen das Anpassen von IntelliSense-Ergebnissen im JavaScript-Editor für Bibliotheken von Drittanbietern. Dadurch können Entwickler, die diese Bibliotheken verwenden, die Möglichkeiten verbessern.

 Der JavaScript-Sprachdienst bietet IntelliSense-Funktionen für JavaScript-Bibliotheken von Drittanbietern, die zu einem Projekt hinzugefügt werden. Bei den meisten Bibliotheken wird die Anweisungs Vervollständigung automatisch vom Sprachdienst bereitgestellt. Die folgende Abbildung zeigt ein Beispiel für die Anweisungs Vervollständigung:

 ![Beispiel für Anweisungsvervollständigung](../ide/media/js-intellisense-completion.png "js_intellisense_completion")

 Wenn Ihre Bibliothek Beschreibungen von Variablen, Funktionen und Objekten in standardmäßigen JavaScript-Kommentar Tags (//) enthält, wird standardmäßig automatisch von den IntelliSense-Erweiterbarkeits Funktionen profitieren, die beschreibende Informationen in einem Popup Fenster bereitstellen, das rechts neben Elementen in einer Vervollständigungsliste angezeigt wird, oder wenn Sie die öffnende Klammer in einem Funktions aufrufstyp eingeben. Die Kommentare im Popup Fenster enthalten die Beschreibung des Members. Das folgende Beispiel zeigt das Popup Feld für eine Vervollständigungsliste.

 ![Beispiel für eine QuickInfo-Popup&#45;](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")

 Um die Entwickler Funktion weiter zu verbessern, sollten Sie Entwicklern im Popup Fenster Typinformationen bereitstellen. Sie können Typinformationen mithilfe von JavaScript- [XML-Dokumentations Kommentaren](../ide/xml-documentation-comments-javascript.md) anstelle von Standardkommentar Tags bereitstellen. XML-Dokumentations Kommentare werden mithilfe von Kommentar Tags (///) mit dreifacher Schrägstrich und einem definierten Satz von XML-Elementen hinzugefügt.

 Alternativ können Sie Typinformationen mithilfe der JavaScript-IntelliSense-Erweiterbarkeit bereitstellen. Diese Funktion ermöglicht es Ihnen, IntelliSense-Ergebnisse anzupassen, indem Sie JavaScript-Erweiterungen erstellen und Sie dem Skript Kontext hinzufügen. In der-Erweiterung, bei der es sich um eine JavaScript-Datei handelt, abonnieren Sie Ereignisse, die vom- `intellisense` Objekt des sprach Dienstanbieter bereitgestellt werden. Die JavaScript-IntelliSense-Erweiterbarkeit ist die bevorzugte Lösung für Bibliotheken, wenn ein Verhaltensmuster in der Bibliothek verhindert, dass der JavaScript-Sprachdienst die gewünschte Ebene der IntelliSense-Unterstützung bereitstellt und eine Alternative zu deklarativen XML-Dokumentations Kommentaren ebenfalls benötigt wird. Durch die Anpassung der IntelliSense-Ergebnisse können Sie eine erstklassige IntelliSense-Funktionalität erstellen, unabhängig von den Verhaltensmustern, durch die die Standardfunktionen des sprach dienstantors eingeschränkt werden können. Weitere Informationen finden Sie unter [Anweisungsvervollständigung für Bezeichner](../ide/statement-completion-for-identifiers.md).

## <a name="adding-an-extension-to-the-script-context"></a>Hinzufügen einer Erweiterung zum Skript Kontext
 Damit eine IntelliSense-Erweiterung ausgeführt werden kann, muss Sie dem aktuellen Skript Kontext hinzugefügt werden. Die Erweiterung kann dem Skript Kontext vom automatischen Ermittlungs Mechanismus automatisch hinzugefügt werden, oder Sie können die Erweiterung dem Skript Kontext manuell hinzufügen, indem Sie Verweis Gruppen oder die Reference-Direktive verwenden.

 Der Mechanismus für die automatische Ermittlung ermöglicht es dem Sprachdienst, automatisch Erweiterungen zu suchen, die der Datei Namenskonvention *Libraryname*.intellisense.js, und die sich im gleichen Verzeichnis befinden wie die Bibliothek, auf die die Erweiterung angewendet wird. Eine gültige Erweiterung für die jQuery-Bibliothek wäre z. b. jQuery.intellisense.js. Bei restriktiveren jQuery-Erweiterungen können Sie Dateinamen verwenden, z. b. jQuery-1.7.1.intellisense.js (versionsspezifische Erweiterung) oder jQuery.ui.intellisense.js (eine Erweiterung für eine Bereichs bezogene jQuery-Bibliothek). Die restriktivste Version der Erweiterung wird verwendet, wenn mehr als eine Erweiterung für eine bestimmte Bibliothek gefunden wird.

 Wenn Sie die Erweiterung für alle JavaScript-Projektdateien verwenden möchten, können Sie stattdessen die Erweiterung einer Verweis Gruppe hinzufügen. Es gibt mehrere Typen von Verweis Gruppen, entweder solche, die implizite Verweise enthalten, und solche, die dedizierte workerverweise enthalten. Zum Hinzufügen einer Erweiterung müssen Sie die Datei in der Regel als implizite Verweis Gruppe hinzufügen, entweder **implizit (Windows)**, **implizit (Web)**. Implizite Verweise befinden sich im Gültigkeitsbereich für jede JS-Datei, die im Code-Editor geöffnet ist. Wenn Sie diese Methode verwenden, müssen Sie die Erweiterung und die Datei hinzufügen, die von der Erweiterung ergänzt wird.

 Verwenden Sie die Seite **IntelliSense** des Dialog Felds **Optionen** , um eine Erweiterung als Verweis Gruppe hinzuzufügen. Sie können auf die **IntelliSense** -Seite zugreifen **, indem**Sie auf der Menüleiste Extras, **Optionen** und dann **Text-Editor**, **JavaScript**, **IntelliSense**und **Verweise**auswählen. Weitere Informationen zu Verweis Gruppen finden Sie unter [JavaScript IntelliSense](../ide/javascript-intellisense.md) und [Optionen, Text-Editor, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

 Wenn Sie die Erweiterung für einen bestimmten Satz von Dateien verwenden möchten, verwenden Sie eine Reference-Direktive. Wenn Sie diese Methode verwenden, müssen Sie sowohl auf die Erweiterung als auch auf die Datei verweisen, die von der Erweiterung ergänzt wird. Weitere Informationen zur Verwendung der Reference-Direktive finden Sie unter [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="handling-intellisense-events"></a>Behandeln von IntelliSense-Ereignissen
 Mithilfe der Erweiterbarkeits Funktion können Sie IntelliSense-Ergebnisse anpassen, indem Sie Ereignisse wie das- `statementcompletion` Ereignis des Sprachdienst Objekts abonnieren `intellisense` . Das folgende Beispiel zeigt eine einfache Erweiterung, die vom Sprachdienst verwendet wird, um Member auszublenden, die mit einem Unterstrich der Anweisungs Vervollständigung beginnen. Dieser Code ist in underscorefilter.js enthalten und befindet sich im \\ \\ Ordner " *Visual Studio-Installationspfad*\javascript\references".

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

 Im vorangehenden Code überprüft die Erweiterung die [Eigenschaft TargetName](#TargetName) und die [Ziel Eigenschaft](#Target) des `statementcompletion` Ereignis Objekts, um Objekte wie `this` und auszuschließen `window` , und um sicherzustellen, dass eine gültige Anweisungs Vervollständigungsliste identifiziert werden kann. Wenn eine Vervollständigungsliste identifiziert werden kann, aktualisiert die Erweiterung die Eigenschaften Sammlung der Anweisungs Vervollständigungs [Elemente](#Items) , indem Member herausgefiltert werden, die mit einem Unterstrich beginnen.

 Weitere Beispiele finden Sie im Ordner " \\ \\ *Visual Studio-Installationspfad*\javascript\references". Die showPlainComments.js-Datei in diesem Ordner enthält Beispiele für die Verwendung anderer Ereignisse, um standardmäßige IntelliSense-Unterstützung für standardmäßige JavaScript-Kommentar Tags (//) bereitzustellen. Wie underscorefilter.js ist showPlainComments.js bereits als funktionierende Erweiterung verfügbar, und Sie können die resultierenden IntelliSense-Informationen sehen, wenn Sie im Code Kommentar Tags für Variablen, Funktionen und Objekte verwenden. Weitere Beispiele finden Sie unter [Code Beispiele](#CodeExamples).

> [!WARNING]
> Wenn Sie die in Visual Studio enthaltenen Erweiterungs Dateien ändern, deaktivieren Sie möglicherweise JavaScript IntelliSense oder das von der Erweiterung unterstützte Feature.

 In Ihrem Erweiterungs Code können Sie Handler für die folgenden Ereignis Typen erstellen, indem Sie Folgendes verwenden `addEventListener` :

- `statementcompletion`, wodurch ein Handler für ein Anweisungs Vervollständigungs Ereignis hinzugefügt wird. Mit der Anweisungs Vervollständigung wird eine Liste von Membern für einen bestimmten Typ bereitgestellt, der angezeigt wird, nachdem Sie ein Sonderzeichen (z. b. einen Zeitraum (.)) oder eine Liste der Bezeichner angezeigt haben, die beim Eingeben von oder beim Drücken von STRG + J Der Handler empfängt ein Ereignis Objekt vom Typ `CompletionEvent` , das die folgenden Member unterstützt [: Items-Eigenschaft](#Items), [Ziel Eigenschaft](#Target), [TargetName-Eigenschaft](#TargetName)und Scope- [Eigenschaft](#Scope).

- `signaturehelp`, wodurch ein Handler für IntelliSense-Parameter Informationen hinzugefügt wird. Parameterinformationen gibt Aufschluss über die Anzahl, die Namen und die Typen von Parametern, die für eine Funktion erforderlich sind. Der Handler empfängt ein Ereignis Objekt vom Typ `SignatureHelpEvent` , das die folgenden Member unterstützt: [Ziel Eigenschaft](#Target), [Eigenschaften Objekt Eigenschaft](#ParentObject), [functioncomments-Eigenschaft](#FunctionComments), [functionhelp-Eigenschaft](#FunctionHelp).

- `statementcompletionhint`, wodurch ein Handler für IntelliSense-Quick Infos hinzugefügt wird. Das Popup Fenster Quick Info zeigt die gesamte Deklaration für Bezeichner in Ihrem Code. Der Handler empfängt ein Ereignis Objekt vom Typ `CompletionHintEvent` , das die folgenden Member unterstützt: [completionitem-Eigenschaft](#CompletionItem)und [symbolhelp-Eigenschaft](#SymbolHelp).

  Beispiele für IntelliSense-Funktionen, wie Anweisungs Vervollständigung, Parameterinformationen und QuickInfo, finden [Sie unter Verwenden von IntelliSense](../ide/using-intellisense.md).

> [!NOTE]
> In JavaScript bezieht sich die QuickInfo auf das Popup Fenster, das rechts neben einer Vervollständigungsliste angezeigt wird. Quick Infos können nicht manuell aufgerufen werden.

## <a name="intellisense-object"></a><a name="intellisenseObject"></a> IntelliSense-Objekt
 In der folgenden Tabelle sind die Funktionen aufgeführt, die für das-Objekt verfügbar sind `intellisense` . Das- `intellisense` Objekt ist nur zur Entwurfszeit verfügbar.

|Funktion|Beschreibung|
|--------------|-----------------|
|`addEventListener(type, handler);`|Fügt einen Ereignishandler für ein IntelliSense-Ereignis hinzu.<br /><br /> `type`Bei  handelt es sich um einen Zeichenfolgenwert. Gültige Werte sind unter anderem `statementcompletion`, `signaturehelp` und `statementcompletionhint`.<br /><br /> `handler` ist eine Ereignishandlerfunktion, die ein Ereignis Objekt eines der folgenden Typen empfängt:<br /><br /> -   `CompletionEvent`, der für das-Ereignis verwendet wird `statementcompletion` .<br />-   `SignatureHelpEvent`, der für das-Ereignis verwendet wird `signaturehelp` .<br />-   `CompletionHintEvent`, der für das-Ereignis verwendet wird `statementcompletionhint` .<br /><br /> Beispiele für die Verwendung dieser Funktion finden Sie unter [Code Beispiele](#CodeExamples).|
|`annotate(obj, doc);`|Gibt die Dokumentation für ein Objekt an, indem Dokumentations Kommentare aus einem Objekt in ein anderes Objekt kopiert werden.<br /><br /> `obj` Gibt das-Objekt an, in das die Dokumentation kopiert werden soll.<br /><br /> `doc` Gibt das-Objekt an, aus dem die Dokumentation kopiert werden soll.<br /><br /> Ein Beispiel für die Verwendung dieser Funktion finden Sie unter [Hinzufügen von IntelliSense](#Annotations)-Anmerkungen.|
|`getFunctionComments(func);`|Gibt die Kommentare für eine angegebene Funktion zurück.<br /><br /> `func` Gibt die Funktion an, für die Kommentare zurückgegeben werden.<br /><br /> Sie können den- `func` Parameter mit festlegen `completionItem.value` .<br /><br /> Das zurückgegebene- `functionComments` Objekt enthält die folgenden Member: `above` , `inside` und `paramComment` . Weitere Informationen finden Sie unter der [Eigenschaft "functioncomments](#FunctionComments) ".<br /><br /> `getFunctionComments` kann nur innerhalb eines der Ereignishandler aufgerufen werden, die von registriert werden `addEventListener` .<br /><br /> Ein Beispiel für die Verwendung dieser Funktion finden Sie unter \\ \\ *Visual Studio-Installationspfad*\JavaScript\References\showPlainComments.js.|
|`logMessage(msg);`|Sendet Diagnosemeldungen an das Ausgabefenster.<br /><br /> `msg` ist eine Zeichenfolge, die die Meldung enthält.<br /><br /> Ein Beispiel für die Verwendung dieser Funktion finden [Sie unter Senden von Nachrichten an den Ausgabefenster](#Logging).|
|`nullWithCompletionsOf(value);`|Gibt einen speziellen NULL-Wert zurück, für den die Vervollständigungsliste durch das-Objekt bestimmt wird, das im-Parameter übergeben wird `value` .<br /><br /> `value` bestimmt die Vervollständigungsliste für den zurückgegebenen Wert. `value` kann ein beliebiger Typ sein.<br /><br /> Der NULL-Rückgabewert wird zur Entwurfszeit als NULL behandelt, aber die Vervollständigungsliste für den Rückgabewert ist identisch mit der Vervollständigungsliste für den `value` Parameter.<br /><br /> Eine Verwendung für diese Funktion besteht darin, IntelliSense für einen Rückgabewert bereitzustellen, wenn der Rückgabetyp zur Laufzeit vorhersagbar ist, der Rückgabewert jedoch `null` zur Entwurfszeit liegt.|
|`redirectDefinition(func, definition);`|Weist IntelliSense an, die bereitgestellte Definitions Funktion anstelle der ursprünglichen Func-Funktion zu verwenden, wenn Parameter Hilfe oder **Gehe zu Definition** angefordert werden.<br /><br /> `func` Gibt die Zielfunktion an.<br /><br /> `definition` Gibt die Funktion an, die anstelle der Zielfunktion für Parameterinformationen und **Gehe zu Definition**verwendet werden soll.|
|`setCallContext(func, thisArg);`|Legt den Aufrufkontext (oder den Gültigkeitsbereich) für die angegebene Funktion fest.<br /><br /> `func` Gibt die Funktion an, für die der Bereich festgelegt werden soll.<br /><br /> `thisArg` ist ein Objektliteral, auf das das- `this` Schlüsselwort verweisen kann, das den neuen Bereich für den Member angibt. Sie können Argumente einschließen, die an diesen Parameter übergeben werden, z. b. `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` bietet ein ähnliches Verhalten wie `Function.prototype.bind` , mit der Ausnahme, dass es nur zur Entwurfszeit-IntelliSense-Unterstützung verwendet wird. Sie können verwenden `setCallContext` , um den Funktionsbereich festzulegen, wenn Sie einen Code Code simulieren müssen, der nicht anderweitig erreichbar ist, sodass der Funktions Aufrufwert beim aufruft der Funktion den korrekten Bereich und die richtigen Argumente enthält.|
|`undefinedWithCompletionsOf(value);`|Gibt einen besonderen, nicht definierten Wert zurück, für den die Vervollständigungsliste durch das im-Parameter übergebenen-Objekt bestimmt wird `value` .<br /><br /> `value` bestimmt die Vervollständigungsliste für den zurückgegebenen Wert. `value` kann ein beliebiger Typ sein.<br /><br /> Der nicht definierte Rückgabewert wird zur Entwurfszeit als nicht definiert behandelt, aber die Vervollständigungsliste für den Rückgabewert ist identisch mit der Vervollständigungsliste für den `value` Parameter.<br /><br /> Eine Verwendung für diese Funktion besteht darin, IntelliSense für einen Rückgabewert bereitzustellen, wenn der Rückgabetyp zur Laufzeit vorhersagbar ist, aber der Rückgabewert zur Entwurfszeit nicht definiert ist.|
|`version()`|Gibt die Visual Studio-Version zurück.|

## <a name="event-members"></a>Ereignismember
 In den folgenden Abschnitten werden die Elemente beschrieben, die im Ereignis Objekt für die folgenden Ereignisse verfügbar gemacht werden: `statementcompletion` , `signaturehelp` und `statementcompletionhint` .

### <a name="completionitem-property"></a><a name="CompletionItem"></a> completionitem (Eigenschaft)
 Gibt den Bezeichner zurück, der als Vervollständigungs Element bezeichnet wird, für den ein QuickInfo-Popup-Popup Element angefordert wird. Diese Eigenschaft ist für das `statementcompletionhint` Ereignis Objekt und für die [Eigenschaft Items-Eigenschaft](#Items) des `statementcompletion` Ereignis Objekts verfügbar.

 Rückgabewert: `completionItem` Objekt

 Im folgenden sind die Member des- `completionItem` Objekts aufgeführt:

- `name`. Lese-/Schreibzugriff bei Verwendung in der Auflistung, andernfalls schreibgeschützt `items` . Gibt eine Zeichenfolge zurück, die das Vervollständigungs Element bezeichnet.

- `kind`. Lese-/Schreibzugriff bei Verwendung in der Auflistung, andernfalls schreibgeschützt `items` . Gibt eine Zeichenfolge zurück, die den Typ des Vervollständigungs Elements darstellt. Mögliche Werte sind Methode, Feld, Eigenschaft, Parameter, Variable und reserviert.

- `glyph`. Lese-/Schreibzugriff bei Verwendung in der Auflistung, andernfalls schreibgeschützt `items` . Gibt eine Zeichenfolge zurück, die ein Symbol darstellt, das in der Vervollständigungsliste angezeigt wird. Die möglichen Werte für `glyph` verwenden das folgende Format: vs:*GlyphType*, wobei *GlyphType* den sprachunabhängigen Membern in der- <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> Enumeration entspricht. Beispielsweise `vs:GlyphGroupMethod` ist ein möglicher Wert für `glyph` . Wenn `glyph` nicht festgelegt ist, `kind` bestimmt die-Eigenschaft das Standard Symbol.

- `parentObject`. Schreibgeschützt. Gibt das übergeordnete Objekt zurück.

- `value`. Schreibgeschützt. Gibt ein-Objekt zurück, das den Wert des Vervollständigungs Elements darstellt.

- `comments`. Schreibgeschützt. Gibt eine Zeichenfolge zurück, die die Kommentare über dem Feld oder der Variablen enthält.

- `scope`. Schreibgeschützt. Gibt den Gültigkeitsbereich des Vervollständigungs Elements zurück. Mögliche Werte sind Global, local, Parameter und Member.

### <a name="items-property"></a><a name="Items"></a> Items-Eigenschaft
 Ruft das Array der Anweisungs Vervollständigungs Elemente ab oder legt es fest. Jedes Element im Array ist ein [completionitem-Eigenschafts](#CompletionItem) Objekt. Die- `items` Eigenschaft ist für das `statementcompletion` Ereignis Objekt verfügbar.

 Rückgabewert: Array

### <a name="functioncomments-property"></a><a name="FunctionComments"></a> functioncomments (Eigenschaft)
 Gibt die Kommentare für die Funktion zurück. Diese Eigenschaft ist für das `signaturehelp` Ereignis Objekt verfügbar.

 Rückgabewert: `comments` Objekt

 Im folgenden sind die Member des- `comments` Objekts aufgeführt:

- `above`. Gibt die Kommentare oberhalb der Funktion zurück.

- `inside`. Gibt die Kommentare in der Funktion zurück, in der Regel im vsdoc-Format.

- `paramComments`. Gibt ein Array zurück, das Kommentare für jeden Parameter in der Funktion darstellt. Die Elemente des Arrays umfassen Folgendes:

  - `name`. Gibt eine Zeichenfolge zurück, die den Parameternamen darstellt.

  - `comment`. Gibt eine Zeichenfolge zurück, die den Parameter Kommentar enthält.

### <a name="functionhelp-property"></a><a name="FunctionHelp"></a> functionhelp (Eigenschaft)
 Gibt die Hilfe für die Funktion zurück. Diese Eigenschaft ist für das `signaturehelp` Ereignis Objekt verfügbar.

 Rückgabewert: `functionHelp` Objekt

 Im folgenden sind die Member des- `functionHelp` Objekts aufgeführt:

- `functionName`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die den Funktionsnamen enthält.

- `signatures`. Lese-/Schreibzugriff. Ruft das Array von Funktions Signaturen ab oder legt es fest. Jedes Element im Array ist ein- `signature` Objekt. Einige `signature` Eigenschaften, z `locid` . b., entsprechen allgemeinen [XML-Dokumentations Kommentaren](../ide/xml-documentation-comments-javascript.md) -Attributen.

  Zu den Membern des- `signature` Objekts gehören:

  - `description`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die die Funktion beschreibt.

  - `locid`. Lese-/Schreibzugriff. Gibt einen Zeichen folgen Bezeichner zurück, der Lokalisierungs Informationen über die Funktion enthält.

  - `helpKeyword`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die das Hilfe Schlüsselwort enthält.

  - `externalFile`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die die Datei darstellt, die die Element-ID enthält.

  - `externalid`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die die Element-ID der Funktion darstellt.

  - `params`. Lese-/Schreibzugriff. Ruft das Array von Parametern für die Funktion ab oder legt es fest. Jedes Element im Parameter Array ist ein- `parameter` Objekt, das über Eigenschaften verfügt, die den folgenden Attributen des- [\<param>](../ide/param-javascript.md) Elements entsprechen:

    - `name`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die den Parameternamen darstellt.

    - `type`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die den Parametertyp darstellt.

    - `elementType`. Lese-/Schreibzugriff. Wenn der Typ ist `Array` , gibt eine Zeichenfolge zurück, die den Typ der Elemente im Array darstellt.

    - `description`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die den-Parameter beschreibt.

    - `locid`. Lese-/Schreibzugriff. Gibt einen Zeichen folgen Bezeichner zurück, der Lokalisierungs Informationen über die Funktion enthält.

    - `optional`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die angibt, ob der Parameter optional ist. `true` Gibt an, dass der Parameter optional ist. `false` gibt an, dass es nicht ist.

  - `returnValue`. Lese-/Schreibzugriff. Ruft ein Rückgabewert Objekt mit Eigenschaften ab, die den folgenden Attributen des-Elements entsprechen, oder legt es fest [\<returns>](../ide/returns-javascript.md) :

    - `type`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die den Rückgabetyp darstellt.

    - `elementType`. Lese-/Schreibzugriff. Wenn der Typ ist `Array` , gibt eine Zeichenfolge zurück, die den Typ der Elemente im Array darstellt.

    - `description`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die den Rückgabewert beschreibt.

    - `locid`. Lese-/Schreibzugriff. Gibt einen Zeichen folgen Bezeichner zurück, der Lokalisierungs Informationen über die Funktion enthält.

    - `helpKeyword`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die das Hilfe Schlüsselwort enthält.

    - `externalFile`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die die Datei darstellt, die die Element-ID enthält.

    - `externalid`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die die Element-ID der Funktion darstellt.

### <a name="parentobject-property"></a><a name="ParentObject"></a> para Object-Eigenschaft
 Gibt das übergeordnete Objekt einer Member-Funktion zurück. Beispielsweise gibt für `document.getElementByID` `parentObject` das- `document` Objekt zurück. Diese Eigenschaft ist für das `signaturehelp` Ereignis Objekt verfügbar.

 Rückgabewert: Objekt

### <a name="target-property"></a><a name="Target"></a> Ziel Eigenschaft
 Gibt ein Objekt zurück, das das Element auf der linken Seite des auslöserzeichens darstellt, bei dem es sich um einen Punkt (.) handelt. Gibt für-Funktionen `target` die Funktion zurück, für die Parameter Informationen angefordert werden. Diese Eigenschaft ist für die `statementcompletion` -und- `signaturehelp` Ereignis Objekte verfügbar.

 Rückgabewert: Objekt

### <a name="targetname-property"></a><a name="TargetName"></a> TargetName-Eigenschaft
 Gibt eine Zeichenfolge zurück, die das Ziel darstellt. Für "this." gibt z. b. `targetName` "This" zurück. Für "A. B" (wenn sich der Cursor hinter "b" befindet) `targetName` gibt "b" zurück. Diese Eigenschaft ist für das `statementcompletion` Ereignis Objekt verfügbar.

 Rückgabewert: Zeichenfolge

### <a name="symbolhelp-property"></a><a name="SymbolHelp"></a> symbolhelp (Eigenschaft)
 Gibt das Vervollständigungs Element zurück, für das eine QuickInfo-Popup Anforderung angefordert wird. Diese Eigenschaft ist für das `statementcompletionhint` Ereignis Objekt verfügbar.

 Rückgabewert:- `symbolHelp` Objekt.

 Einige Eigenschaften des `symbolHelp` Objekts (z. b `locid` .) entsprechen allgemeinen [XML-Dokumentations Kommentaren](../ide/xml-documentation-comments-javascript.md) -Attributen.

 Im folgenden sind die Member des- `symbolHelp` Objekts aufgeführt:

- `name`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die den Bezeichnernamen enthält.

- `symbolType`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die den Symboltyp darstellt. Mögliche Werte sind unknown, Boolean, Number, String, Object, Function, Array, Date und Regex

- `symbolDisplayType`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die den anzuzeigenden Typnamen enthält. Wenn `symbolDisplayType` nicht festgelegt ist, `symbolType` wird verwendet.

- `elementType`. Lese-/Schreibzugriff. Wenn den `symbolType` Wert `Array` hat, wird eine Zeichenfolge zurückgegeben, die den Typ der Elemente im Array darstellt.

- `scope`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die den Gültigkeitsbereich des Symbols darstellt. Mögliche Werte sind Global, local, Parameter und Member.

- `description`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die eine Beschreibung des Symbols enthält.

- `locid`. Lese-/Schreibzugriff. Gibt einen Zeichen folgen Bezeichner zurück, der Lokalisierungs Informationen über das Symbol enthält.

- `helpKeyword`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die das Hilfe Schlüsselwort enthält.

- `externalFile`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die die Datei darstellt, die die Element-ID enthält.

- `externalid`. Lese-/Schreibzugriff. Gibt eine Zeichenfolge zurück, die die Element-ID des Symbols darstellt.

- `functionHelp`. Lese-/Schreibzugriff. Gibt eine [functionhelp-Eigenschaft](#FunctionHelp)zurück, die möglicherweise Informationen enthält, wenn die `symbolType` Funktion von ist.

### <a name="scope-property"></a><a name="Scope"></a> Scope-Eigenschaft
 Gibt den Abschluss Bereich des Ereignisses zurück. Die möglichen Werte für den Vervollständigungs Bereich sind global und Members. Diese Eigenschaft ist für das `statementcompletion` Ereignis Objekt verfügbar.

 Rückgabewert: Zeichenfolge

## <a name="debugging-intellisense-extensions"></a>IntelliSense-Erweiterungen Debuggen
 Sie können keine Erweiterungen Debuggen, aber Sie können die [IntelliSense-Objekt](#intellisenseObject) Funktion verwenden, um Informationen an das Ausgabefenster von Visual Studio zu senden. Ein Beispiel für die Verwendung dieser Funktion finden [Sie unter Senden von Nachrichten an die Ausgabefenster weiter](#Logging) unten in diesem Thema. Damit `logMessage` funktioniert, muss mindestens ein Ereignishandler in einer Erweiterung registriert werden.

## <a name="code-examples"></a><a name="CodeExamples"></a> Codebeispiele
 Dieser Abschnitt enthält Codebeispiele, die zeigen, wie die IntelliSense-Erweiterbarkeits-APIs verwendet werden. Es gibt auch andere Möglichkeiten, diese APIs zu verwenden. Weitere Beispiele finden Sie in den folgenden Dateien im Ordner " \\ \\ *Visual Studio-Installationspfad*\javascript\references". Dies sind funktionierende Beispiele, die vom JavaScript-Sprachdienst verwendet werden.

- underscoreFilter.js. Dieser Code verbirgt private Member aus IntelliSense. Sie enthält Ereignishandler für das- `statementcompletion` Ereignis.

- showPlainComments.js. Dieser Code bietet IntelliSense-Unterstützung für Standard Kommentare. Sie enthält Ereignishandler für das `signaturehelp` -Ereignis und das-Ereignis `statementcompletionhint` .

### <a name="adding-intellisense-annotations"></a><a name="Annotations"></a> Hinzufügen von IntelliSense-Anmerkungen
 Im folgenden Verfahren wird gezeigt, wie Sie die IntelliSense-Dokumentations Unterstützung für eine Drittanbieter Bibliothek bereitstellen, ohne die Bibliothek direkt zu ändern. Zu diesem Zweck können Sie `intellisense.annotate` in einer-Erweiterung verwenden.

 Damit dieses Beispiel funktioniert, benötigen Sie die folgenden JavaScript-Dateien im Projekt:

- demoLib.js, eine Projektdatei, die eine Bibliothek eines Drittanbieters darstellt.

- demoLib.intellisense.js, die die IntelliSense-Erweiterung ist. Diese Datei muss nicht in das Projekt aufgenommen werden, muss sich aber im gleichen Ordner wie "exampleLib.js" befinden.

- appCode.js, eine Projektdatei, die App-Code darstellt.

##### <a name="to-add-an-intellisense-annotation"></a>So fügen Sie eine IntelliSense-Anmerkung hinzu

1. Fügen Sie demoLib.js den folgenden Code hinzu.

    ```javascript
    function someFunc(a) { };
    var rectangle;

    ```

2. Fügen Sie demoLib.intellisense.js den folgenden Code hinzu.

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

3. Fügen Sie die folgende Reference-Direktive als erste Zeile in appCode.js hinzu. Der hier verwendete Pfad gibt an, dass sich die JavaScript-Dateien im gleichen Ordner befinden.

    ```javascript
    /// <reference path="demoLib.js" />

    ```

4. Geben Sie in appCode.js den folgenden Code ein. Die XML-Dokumentations Kommentare in der Erweiterung werden als IntelliSense-Parameter Info angezeigt.

     ![Beispiel für die Verwendung von intellisense.annotate](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")

5. Geben Sie in appCode.js den folgenden Code ein. Wenn Sie eingeben, sehen Sie, dass die Standard Kommentare in der Erweiterung als IntelliSense-QuickInfo angezeigt werden.

     ![Beispiel für die Verwendung von intellisense.annotate](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")

### <a name="sending-messages-to-the-output-window"></a><a name="Logging"></a> Senden von Nachrichten an den Ausgabefenster
 Im folgenden Verfahren wird gezeigt, wie Nachrichten an das Ausgabefenster gesendet werden. Sie können Nachrichten senden, um IntelliSense-Erweiterungen zu debuggen.

 Damit dieses Beispiel funktioniert, benötigen Sie die folgenden JavaScript-Dateien im Projekt:

- exampleLib.js, eine Projektdatei, die eine Bibliothek eines Drittanbieters darstellt.

- exampleLib.intellisense.js, die die IntelliSense-Erweiterung ist. Diese Datei muss nicht in das Projekt aufgenommen werden, muss sich aber im gleichen Ordner wie "exampleLib.js" befinden.

- appCode.js, eine Projektdatei, die App-Code darstellt.

##### <a name="to-send-a-message-to-the-output-window"></a>So senden Sie eine Nachricht an das Ausgabefenster

1. Fügen Sie exampleLib.js den folgenden Code hinzu.

    ```javascript
    var someVar = {
        a: 1,
        b: 'hello'
    };
    ```

2. Fügen Sie exampleLib.intellisense.js den folgenden Code hinzu.

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

3. Fügen Sie die folgende Reference-Direktive als erste Zeile in appCode.js hinzu. Der hier verwendete Pfad gibt an, dass sich die JavaScript-Dateien im gleichen Ordner befinden.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. Wählen Sie im Fenster Ausgabe in der Liste **Ausgabe anzeigen von** die Option **JavaScript Language Service** aus. (Um das Ausgabefenster anzuzeigen, wählen Sie im Menü Ansicht die Option **Ausgabe** aus.)

5. Geben Sie in appCode.js den folgenden Code ein. Beim Eingeben von zeigt das Fenster Ausgabemeldungen des sprach Dienstanbieter an. Die erste Meldung im Ausgabefenster gibt an, dass die Anweisungs Vervollständigung für den aktuellen Bereich angefordert wurde.

    ```javascript
    some
    ```

     Im folgenden finden Sie eine partielle Ansicht der Ausgabe, die angezeigt werden sollte.

    ```scr
    03:16:14.3113: statement completion for current scope requested
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined

    …
    ```

6. Wählen Sie im Fenster Ausgabe die Schaltfläche **Alle löschen** aus.

7. Geben Sie den folgenden Code ein. Die erste Meldung im Ausgabefenster gibt an, dass eine Elementliste angefordert wurde.

    ```javascript
    someVar.
    ```

     Im folgenden finden Sie eine partielle Ansicht der Ausgabe, die angezeigt werden sollte:

    ```scr
    03:17:43.4032: member list requested, target: someVar
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:

    …
    ```

### <a name="changing-the-intellisense-icons"></a><a name="Icons"></a> Ändern der IntelliSense-Symbole
 Im folgenden Verfahren wird gezeigt, wie die von IntelliSense angezeigten Symbole standardmäßig geändert werden. Dies kann hilfreich sein, wenn Sie IntelliSense-Informationen zu Bibliotheks spezifischen Konzepten wie Namespaces, Klassen, Schnittstellen und Enumerationen bereitstellen.

 Verfügbare Symbol Werte finden Sie unter <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> .

 Damit dieses Beispiel funktioniert, benötigen Sie die folgenden JavaScript-Dateien im Projekt:

- exampleLib.js, eine Projektdatei, die eine Bibliothek eines Drittanbieters neu präsentiert.

- exampleLib.intellisense.js, die die IntelliSense-Erweiterung ist. Diese Datei muss nicht in das Projekt aufgenommen werden, muss sich aber im gleichen Ordner wie "exampleLib.js" befinden.

- appCode.js, eine Projektdatei, die App-Code darstellt.

##### <a name="to-change-the-icons"></a>So ändern Sie die Symbole

1. Fügen Sie exampleLib.js den folgenden Code hinzu.

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

2. Fügen Sie exampleLib.intellisense.js den folgenden Code hinzu.

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

3. Fügen Sie die folgende Reference-Direktive als erste Zeile in appCode.js hinzu. Der hier verwendete Pfad gibt an, dass sich die JavaScript-Dateien im gleichen Ordner befinden.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. Geben Sie in appCode.js den folgenden Code ein. Wenn Sie eingeben, sehen Sie, dass sich das Symbol für den Namespace in "" geändert hat {} , wie es in c# verwendet wird.

     ![Beispiel für die Verwendung der Symboleigenschaft](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")

5. Geben Sie in appCode.js den folgenden Code ein. Wenn Sie eingeben, wird ein neues enumerationssymbol für das Enum1-Element und ein neues Klassen Symbol für den SomeClass1-Member angezeigt.

     ![Beispiel für die Verwendung der Symboleigenschaft](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")

### <a name="avoiding-run-time-effects-on-intellisense-results"></a><a name="Overriding"></a> Vermeiden von Lauf Zeit Effekten in IntelliSense-Ergebnissen
 Der JavaScript-Sprachdienst führt Code aus, um IntelliSense-Informationen dynamisch bereitzustellen. Folglich kann das Laufzeitverhalten die gewünschten Ergebnisse gelegentlich beeinträchtigen. Im folgenden Verfahren wird gezeigt, wie IntelliSense-Ergebnisse überschrieben werden, wenn das Laufzeitverhalten zu fehlerhaftem IntelliSense führt.

 Damit dieses Beispiel funktioniert, benötigen Sie die folgenden JavaScript-Dateien im Projekt:

- exampleLib.js, eine Projektdatei, die eine Bibliothek eines Drittanbieters darstellt.

- exampleLib.intellisense.js, die die IntelliSense-Erweiterung ist. Diese Datei muss nicht in das Projekt aufgenommen werden, muss sich aber im gleichen Ordner wie "exampleLib.js" befinden.

- appCode.js, eine Projektdatei, die App-Code darstellt.

##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>So vermeiden Sie Lauf Zeiteffekte für IntelliSense-Ergebnisse

1. Fügen Sie exampleLib.js den folgenden Code hinzu.

    ```javascript
    function after(count, func) {
        return function () {
            if (--times < 1) {
                return func.apply(this, arguments);
            }
        };
    };
    ```

     Im vorangehenden Code ignoriert die umschließende Funktion anfängliche Aufrufe basierend auf dem Wert von `count` und gibt keine Ergebnisse zurück.

2. Fügen Sie die folgende Reference-Direktive als erste Zeile in appCode.js hinzu. Der hier verwendete Pfad gibt an, dass sich die JavaScript-Dateien im gleichen Ordner befinden.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

3. Geben Sie in appCode.js den folgenden Code ein. Die bezeichnerliste wird anstelle von IntelliSense angezeigt, da die umschließende Funktion niemals aufgerufen wird, was bedeutet, dass die `throttled` Funktion keine Ergebnisse zurückgibt.

     ![Beispiel zum Überschreiben der IntelliSense-Ergebnisse](../ide/media/js-intellisense-override.png "js_intellisense_override")

4. Fügen Sie exampleLib.intellisense.js den folgenden Code hinzu. Dadurch wird das Entwurfszeit Verhalten geändert, sodass IntelliSense wie erwartet für die umschließende Funktion angezeigt wird.

    ```javascript
    window.after = function (count, func) {
        // Just return func.
        return func;
    };
    ```

5. Testen Sie in appCode.js die Ergebnisse, indem Sie denselben Code eingeben, den Sie zuvor eingegeben haben. Dieses Mal stellt IntelliSense die gewünschten Informationen bereit.

     ![Beispiel für das Überschreiben von IntelliSense-Ergebnissen](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")

## <a name="see-also"></a>Weitere Informationen
 [JavaScript-IntelliSense](../ide/javascript-intellisense.md) - [Anweisungs Vervollständigung für](../ide/statement-completion-for-identifiers.md) Bezeichner
