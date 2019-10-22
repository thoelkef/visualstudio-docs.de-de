---
title: Debuggen von Benutzercode mit nur eigenen Code | Microsoft-Dokumentation
ms.date: 02/13/2019
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c1d474b388dd8f116eb53febb8a472d4c5b8150
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535996"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Nur Benutzercode mit nur eigenen Code Debuggen

*Nur eigenen Code* ist ein Visual Studio-Debugfeature, das automatisch Aufrufe von System-, Framework-und anderen Nichtbenutzer Code überschreitet. Im Fenster **Aufruf Stapel** reduziert nur eigenen Code diese Aufrufe in **[externer Code]** -Frames.

Nur eigenen Code funktioniert in .net-, C++-und JavaScript-Projekten anders.

## <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Aktivieren oder Deaktivieren von „Nur eigenen Code“

Für die meisten Programmiersprachen ist nur eigenen Code standardmäßig aktiviert.

- Wenn Sie nur eigenen Code in Visual Studio aktivieren oder deaktivieren möchten, klicken **Sie unter Extras**  > **Optionen** (oder **Debuggen**  > **Optionen**) > **Debuggen**  > **Allgemein**auf **nur eigenen Code aktivieren**.

![Aktivieren von nur eigenen Code im Dialogfeld "Optionen"](../debugger/media/dbg_justmycode_options.png "Nur meinen Code aktivieren")

> [!NOTE]
> **Aktivieren von nur eigenen Code** ist eine globale Einstellung, die für alle Visual Studio-Projekte in allen Sprachen gilt.

## <a name="just-my-code-debugging"></a>Nur mein Code (Debugoption)

Während einer Debugsitzung zeigt das Fenster **Module** an, welche Code Module der Debugger als eigenen Code (Benutzercode) behandelt, zusammen mit dem Symbol Ladestatus. Weitere Informationen finden Sie unter Weitere Informationen zur Art und [Weise, wie der Debugger an Ihre APP angefügt](../debugger/debugger-tips-and-tricks.md#modules_window)wird.

![Benutzercode im Fenster "Module"](../debugger/media/dbg_justmycode_module.png "Benutzercode im Fenster "Module"")

Im Fenster " **aufrufsstapel** " oder " **Aufgaben** " reduziert nur eigenen Code Nichtbenutzer Code in einen mit Anmerkungen versehenen Code Rahmen mit der Bezeichnung `[External Code]`.

![Externer codeframe im Fenster "aufrufsstapel"](../debugger/media/dbg_justmycode_externalcode.png "Externer codeframe")

>[!TIP]
>Um die **Module**, die **aufrufsstapel**, **Tasks**oder die meisten anderen Debuggingfenster zu öffnen, müssen Sie sich in einer Debugsitzung befinden. Wählen Sie beim Debuggen unter **Debuggen**  > **Fenster**die Fenster aus, die Sie öffnen möchten.

<a name="BKMK_Override_call_stack_filtering"></a>Um den Code in einem reduzierten Frame **[externer Code]** anzuzeigen, klicken Sie mit der rechten Maustaste in das Fenster " **Aufrufe** " oder " **Aufgabe** ", und wählen Sie im Kontextmenü **externen Code anzeigen** aus. Die erweiterten externen Codezeilen ersetzen den Frame **[externer Code**].

![Externen Code im Fenster "aufrufsstapel" anzeigen](../debugger/media/dbg_justmycode_showexternalcode.png "Externen Code anzeigen")

> [!NOTE]
> **Externer Code anzeigen** ist eine aktuelle benutzerprofiler-Einstellung, die für alle Projekte in allen Sprachen gilt, die vom Benutzer geöffnet werden.

Durch Doppelklicken auf eine erweiterte externe Codezeile im Fenster **Aufruf Stapel** wird die aufrufende Codezeile in grün im Quellcode hervorgehoben. Wenn DLLs oder andere Module nicht gefunden oder geladen wurden, wird möglicherweise eine Seite Symbol oder Quelle nicht gefunden geöffnet.

## <a name="BKMK__NET_Framework_Just_My_Code"></a>.Net-nur eigenen Code

In .NET-Projekten verwendet nur eigenen Code Symbol Dateien (*PDB*-Dateien) und Programm Optimierungen, um Benutzer-und Nichtbenutzer Code zu klassifizieren. Der .NET-Debugger berücksichtigt optimierte Binärdateien und nicht geladene *PDB* -Dateien als Nichtbenutzer Code.

Drei Compilerattribute wirken sich auch darauf aus, wie sich der .NET-Debugger als Benutzercode ansieht:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> weist den Debugger an, dass der Code, auf den er angewendet wird, kein Benutzercode ist.
- <xref:System.Diagnostics.DebuggerHiddenAttribute> blendet den Code für den Debugger aus, auch wenn Nur mein Code deaktiviert wird.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> weist den Debugger an, den Code, auf den er angewendet wird, schrittweise zu durchlaufen, anstatt in den Code zu gehen.

Der .NET-Debugger betrachtet den gesamten anderen Code als Benutzercode.

Beim .NET-Debuggen:

- **Debuggen** Sie  > **Schritt** Weise (oder **F11**) in Nichtbenutzer Code Schritten über den Code zur nächsten Zeile des Benutzercodes.
- **Debuggen**  >  Rücksprung (oder **UMSCHALT** +**F11**) bei Nichtbenutzer Code wird in die nächste Zeile des Benutzercodes**ausgeführt** .

Wenn kein Benutzercode mehr vorhanden ist, wird das Debuggen bis zum Ende fortgesetzt, es wird ein weiterer Haltepunkt erreicht oder ein Fehler ausgelöst.

<a name="BKMK_NET_Breakpoint_behavior"></a>Wenn der Debugger in Nichtbenutzer Code unterbricht (z. b. Wenn Sie **Debuggen**  > **Alle unterbrechen** und in Nichtbenutzer Code anhalten), wird das Fenster **keine Quelle** angezeigt. Sie können dann einen **Debug**  > **Step** -Befehl verwenden, um zur nächsten Zeile des Benutzercodes zu wechseln.

Wenn eine nicht behandelte Ausnahme in Nichtbenutzer Code auftritt, unterbricht der Debugger an der Benutzer Codezeile, in der die Ausnahme generiert wurde.

Wenn Ausnahmen der ersten Chance für die Ausnahme aktiviert sind, wird die aufrufenden Benutzercode Zeile im Quellcode grün hervorgehoben. Das Fenster " **aufrufsstapel** " zeigt den mit Anmerkungen versehene Frame mit der Bezeichnung **[externer Code]** .

## <a name="BKMK_C___Just_My_Code"></a> „Nur eigenen Code“ in C++

Ab Visual Studio 2017, Version 15,8, werden auch nur eigenen Code für die Code Ausführung unterstützt. Diese Funktion erfordert auch die Verwendung des Compilerschalters [/JMC (nur eigenen Code Debuggen)](/cpp/build/reference/jmc) . Der Schalter ist in C++ -Projekten standardmäßig aktiviert. Für das Fenster " **aufrufsstapel** " und die Unterstützung von aufrufstapeln in nur eigenen Code ist der Schalter/JMC nicht erforderlich

<a name="BKMK_CPP_User_and_non_user_code"></a>Um als Benutzercode klassifiziert zu werden, muss die PDB für die Binärdatei, die den Benutzercode enthält, vom Debugger geladen werden (verwenden Sie das Fenster " **Module** ", um dies zu überprüfen).

Für das Verhalten von aufrufstapeln, wie z. b. im Fenster C++ " **aufrufsstapel** ", berücksichtigt nur eigenen Code in nur diese Funktionen als *Nichtbenutzer Code*:

- Funktionen mit entfernten Quellinformationen in ihrer Symboldatei.
- Funktionen, bei denen die Symboldateien angeben, dass keine Quelldatei vorhanden ist, die dem Stapelrahmen entspricht.
- Funktionen, die in *\* natjmc* -Dateien im Ordner *%vsinstalldirectory%\common7\packages\debugger\visualizers* angegeben sind.

Für Code-Schritt Verhalten berücksichtigt nur eigenen Code C++ in nur diese Funktionen als *Nichtbenutzer Code*:

- Funktionen für den, die die entsprechende PDB-Datei nicht in den Debugger geladen haben.
- Funktionen, die in *\* natjmc* -Dateien im Ordner *%vsinstalldirectory%\common7\packages\debugger\visualizers* angegeben sind.

> [!NOTE]
> Zur Unterstützung von Code Stepping in C++ nur eigenen Code muss Code mithilfe der MSVC-Compiler in Visual Studio 15,8 Preview 3 oder höher kompiliert werden, und der/JMC-Compilerschalter muss aktiviert sein (standardmäßig aktiviert). Weitere Informationen finden Sie unter [anpassen C++ der aufrufsstapel-und Code Schritt Verhalten](#BKMK_CPP_Customize_call_stack_behavior)) und dieses [Blogbeitrags](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/). Bei Code, der mit einem älteren Compiler kompiliert wurde, sind *natstepfilter* -Dateien die einzige Möglichkeit zum Anpassen von Code-Stepping, der unabhängig von nur eigenen Code ist. Siehe [anpassen C++ des schrittweisen Verhaltens](#BKMK_CPP_Customize_stepping_behavior).

<a name="BKMK_CPP_Stepping_behavior"></a>Beim C++ Debuggen:

- **Debuggen** Sie  > **Schritt** Weise (oder **F11**) in Nichtbenutzer Code Schritten über den Code zur nächsten Zeile des Benutzercodes.
- **Debuggen**  >  Rücksprung (oder **UMSCHALT** +**F11**) bei Nichtbenutzer Code wird in die nächste Zeile des Benutzercodes**ausgeführt** .

Wenn kein Benutzercode mehr vorhanden ist, wird das Debuggen bis zum Ende fortgesetzt, es wird ein weiterer Haltepunkt erreicht oder ein Fehler ausgelöst.

Wenn der Debugger in Nichtbenutzer Code unterbricht (z. b. Wenn Sie **Debuggen**  > **Alle unterbrechen** und in Nichtbenutzer Code anhalten), wird die schrittweise Verarbeitung im Nichtbenutzer Code fortgesetzt.

Wenn der Debugger auf eine Ausnahme trifft, wird er bei der Ausnahme angehalten, unabhängig davon, ob er sich im Benutzer-oder Nichtbenutzer Code befindet. Vom **Benutzer nicht behandelte** Optionen im Dialogfeld **Ausnahme Einstellungen** werden ignoriert.

### <a name="BKMK_CPP_Customize_call_stack_behavior"></a>Anpassen C++ der Verhalten von aufrufsstapel und Code schrittweisen

Für C++ -Projekte können Sie die Module, Quelldateien und Funktionen angeben, die das Fenster der **aufrufsstapel** als Nichtbenutzer Code behandelt, indem Sie Sie in *\* natjmc* -Dateien angeben. Diese Anpassung gilt auch für Code-Stepping, wenn Sie den neuesten Compiler verwenden (siehe [ C++ nur eigenen Code](#BKMK_CPP_User_and_non_user_code)).

- Fügen Sie dem Ordner *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* die *NATJMC*-Datei hinzu, um Nichtbenutzercode aller Benutzer des Visual Studio-Computers anzugeben.
- Um Nichtbenutzer Code für einen einzelnen Benutzer anzugeben, fügen Sie die *natjmc* -Datei dem Ordner *%UserProfile%\My Documents \\ < Visual Studio Version \> \visualizers* hinzu.

Eine *natjmc* -Datei ist eine XML-Datei mit der folgenden Syntax:

```xml
<?xml version="1.0" encoding="utf-8"?>
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">

  <!-- Modules -->
  <Module Name="ModuleSpec" />
  <Module Name="ModuleSpec" Company="CompanyName" />

  <!-- Files -->
  <File Name="FileSpec"/>

  <!-- Functions -->
  <Function Name="FunctionSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />

</NonUserCode>

```

 **Modulelementattribute**

|Attribut|Beschreibung|
|---------------|-----------------|
|`Name`|Erforderlich. Der vollständige Pfad des Moduls oder der Module. Sie können die Windows-Platzhalter Zeichen `?` (null oder ein Zeichen) und `*` (null oder mehr Zeichen) verwenden. Ein auf ein Objekt angewendeter<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> weist den Debugger an, alle Module in *\3rdParty\UtilLibs* auf einem Laufwerk als externen Code zu behandeln.|
|`Company`|Dies ist optional. Der Name des Unternehmens, das das Modul veröffentlicht, das in die ausführbare Datei eingebettet ist. Sie können dieses Attribut verwenden, um die Module zu unterscheiden.|

 **Dateielementattribute**

|Attribut|Beschreibung|
|---------------|-----------------|
|`Name`|Erforderlich. Der vollständige Pfad der Quelldatei oder -dateien, die als externer Code behandelt werden sollen. Sie können die Windows-Platzhalterzeichen `?` und `*` verwenden, wenn Sie den Pfad angeben.|

 **Funktionselementattribute**

|Attribut|Beschreibung|
|---------------|-----------------|
|`Name`|Erforderlich. Der vollqualifizierte Name der Funktion, die als externer Code behandelt werden soll.|
|`Module`|Dies ist optional. Der Name oder der vollständige Pfad zu dem Modul, das die Funktion enthält. Sie können dieses Attribut verwenden, um Funktionen mit demselben Namen zu unterscheiden.|
|`ExceptionImplementation`|Bei Festlegung auf `true` zeigt die Aufrufliste die Funktion an, die die Ausnahme und nicht diese Funktion ausgelöst hat.|

### <a name="BKMK_CPP_Customize_stepping_behavior"></a>Anpassen C++ des schrittweisen Verhaltens unabhängig von nur eigenen Code Einstellungen

In C++ -Projekten können Sie Funktionen angeben, die überschritten werden sollen, indem Sie Sie als Nichtbenutzer Code in *\*. natstepfilter* -Dateien auflisten. Die in *\*. natstepfilter* -Dateien aufgeführten Funktionen sind nicht von nur eigenen Code Einstellungen abhängig.

- Fügen Sie dem Ordner *%vsinstalldirectory%\common7\packages\debugger\visualizers* die *natstepfilter* -Datei hinzu, um Nichtbenutzer Code für alle lokalen Benutzer von Visual Studio anzugeben.
- Um Nichtbenutzer Code für einen einzelnen Benutzer anzugeben, fügen Sie die *natstepfilter* -Datei dem Ordner *%UserProfile%\My Documents \\ < Visual Studio Version \> \visualizers* hinzu.

Eine *natstepfilter* -Datei ist eine XML-Datei mit der folgenden Syntax:

```xml
<?xml version="1.0" encoding="utf-8"?>
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">
    <Function>
        <Name>FunctionSpec</Name>
        <Action>StepAction</Action>
    </Function>
    <Function>
        <Name>FunctionSpec</Name>
        <Module>ModuleSpec</Module>
        <Action>StepAction</Action>
    </Function>
</StepFilter>

```

|Element|Beschreibung|
|-------------|-----------------|
|`Function`|Erforderlich. Gibt eine oder mehreren Funktionen als Nichtbenutzerfunktionen an.|
|`Name`|Erforderlich. Ein ECMA-262-formatierter regulärer Ausdruck, der den vollständigen Funktionsnamen angibt, der übereinstimmen muss. Beispiel:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> teilt dem Debugger mit, dass alle Methoden in `MyNS::MyClass` als Nichtbenutzercode behandelt werden sollen. Bei der Übereinstimmung muss die Groß-/Kleinschreibung beachtet werden.|
|`Module`|Dies ist optional. Ein ECMA-262-formatierter regulärer Ausdruck, der den vollständigen Pfad zu dem Modul angibt, das die Funktion enthält. Die Groß- und Kleinschreibung wird bei der Übereinstimmung nicht berücksichtigt.|
|`Action`|Erforderlich. Einer dieser Werte, bei denen die Groß-/Kleinschreibung beachtet werden muss.<br /><br /> `NoStepInto`: weist den Debugger an, die Funktion zu überspringen.<br /> `StepInto`: weist den Debugger an, die Funktion schrittweise zu durchlaufen, wobei alle anderen `NoStepInto` für die passende Funktion überschrieben werden.|

## <a name="BKMK_JavaScript_Just_My_Code"></a> „Nur eigenen Code“ in JavaScript

<a name="BKMK_JS_User_and_non_user_code"></a> „Nur eigenen Code“ in JavaScript steuert die Einzelschrittausführung und die Aufruflistenanzeige durch Kategorisieren von Code in einer dieser Klassifizierungen:

|||
|-|-|
|**MyCode**|Benutzercode, den Sie besitzen und steuern.|
|**LibraryCode**|Nichtbenutzer Code aus Bibliotheken, die Sie regelmäßig verwenden, und Ihre APP ist zur ordnungsgemäßen Funktionsweise (z. b. winjs oder jQuery) angewiesen.|
|**UnrelatedCode**|Nichtbenutzer Code in Ihrer APP, den Sie nicht besitzen, und Ihre APP ist nicht darauf angewiesen, ordnungsgemäß zu funktionieren. Ein Werbe-SDK, das ADS anzeigt, könnte z. b. unrelatedcode lauten. In UWP-Projekten wird jeglicher Code, der von einem http-oder HTTPS-URI in Ihre APP geladen wird, auch als unrelatedcode betrachtet.|

Der JavaScript-Debugger klassifiziert Code als Benutzer oder Nichtbenutzer in dieser Reihenfolge:

1. Die Standard Klassifizierungen.
   - Skript wird ausgeführt, indem eine Zeichenfolge an die vom Host bereitgestellte `eval` Funktion **übergeben wird.**
   - Skript wird ausgeführt, indem eine Zeichenfolge an den `Function`-Konstruktor übergeben wird, ist **librarycode**.
   - Skripts in einem frameworkverweis, wie z. b. winjs oder dem Azure SDK, sind **librarycode**.
   - Skript, das ausgeführt wird, indem eine Zeichenfolge an die Funktionen `setTimeout`, `setImmediate` oder `setInterval` übergeben wird, ist **unrelatedcode**.

2. Klassifizierungen, die für alle Visual Studio JavaScript-Projekte in der *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.WWA.JSON* -Datei angegeben werden.

3. Klassifizierungen in der Datei " *MyCode. JSON* " des aktuellen Projekts.

Jeder Klassifizierungsschritt überschreibt die vorherigen Schritte.

Der restliche Code wird als **MyCode** klassifiziert.

Sie können die Standard Klassifizierungen ändern und bestimmte Dateien und URLs als Benutzer-oder Nichtbenutzer Code klassifizieren, indem Sie eine *JSON* -Datei mit dem Namen " *MyCode. JSON* " zum Stamm Ordner eines JavaScript-Projekts hinzufügen. Siehe [Anpassen von JavaScript-nur eigenen Code](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a>Beim JavaScript-Debuggen:

- Wenn eine Funktion Nichtbenutzer Code ist, verhält sich das **Debuggen** von  >  Einzel**Schritt** (oder **F11**) genauso wie **Debug**  >  Prozedur**Schritt** (oder **F10**).
- Wenn ein Schritt im Nichtbenutzer Code (**librarycode** oder **unrelatedcode**) beginnt, verhält sich die schrittweise Vorgehensweise temporär, als ob nur eigenen Code nicht aktiviert ist. Wenn Sie einen Einzelschritt auf den Benutzercode durchlaufen, wird nur eigenen Code schrittweise wieder aktiviert.
- Wenn ein Benutzercode Schritt dazu führt, dass der aktuelle Ausführungs Kontext verlässt, hält der Debugger bei der nächsten ausgeführten Benutzer Codezeile an. Wenn beispielsweise ein Rückruf in **LibraryCode**-Code ausgeführt wird, fährt der Debugger fort, bis die nächste Zeile des Benutzercodes ausgeführt wird.
- " **Step out** " (oder **UMSCHALT** +**F11**) wird in der nächsten Zeile des Benutzercodes angehalten.

Wenn kein Benutzercode mehr vorhanden ist, wird das Debuggen bis zum Ende fortgesetzt, es wird ein weiterer Haltepunkt erreicht oder ein Fehler ausgelöst.

Breakpoints, die im Code festgelegt sind, werden immer getroffen, aber der Code wird klassifiziert.

- Wenn das `debugger`-Schlüsselwort in **librarycode**auftritt, unterbricht der Debugger immer.
- Wenn das `debugger`-Schlüsselwort in **unrelatedcode**auftritt, wird der Debugger nicht angehalten.

<a name="BKMK_JS_Exception_behavior"></a>Wenn eine nicht behandelte Ausnahme in **MyCode** -oder **librarycode** -Code auftritt, unterbricht der Debugger immer.

Wenn in **unrelatedcode**eine nicht behandelte Ausnahme auftritt und **MyCode** oder **librarycode** in der-aufrufsstapel steht, wird der Debugger unterbrochen.

Wenn Ausnahmen der ersten Chance für die Ausnahme aktiviert sind und die Ausnahme in **librarycode** oder **unrelatedcode**auftritt:

- Wenn die Ausnahme behandelt wird, unterbricht der Debugger nicht.
- Wenn die Ausnahme nicht behandelt wird, unterbricht der Debugger.

### <a name="BKMK_JS_Customize_Just_My_Code"></a>Anpassen von JavaScript-nur eigenen Code

Um Benutzer-und Nichtbenutzer Code für ein einzelnes JavaScript-Projekt zu kategorisieren, können Sie dem Stamm Ordner des Projekts eine *JSON* -Datei mit dem Namen " *MyCode. JSON* " hinzufügen.

Spezifikationen in dieser Datei überschreiben die Standard Klassifizierungen und die Datei " *MyCode. default. WWA. JSON* ". Die Datei " *MyCode. JSON* " muss nicht alle Schlüssel-Wert-Paare auflisten. **MyCode**, **Bibliotheken**und verknüpfte **Werte können** leere Arrays sein.

*MyCode. JSON* -Dateien verwenden diese Syntax:

```json
{
    "Eval" : "Classification",
    "Function" : "Classification",
    "ScriptBlock" : "Classification",
    "MyCode" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ],
    "Libraries" : [
        "UrlOrFileSpec",
        . .
        "UrlOrFileSpec"
    ],
    "Unrelated" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ]
}

```

**Eval, Function und ScriptBlock**

Die Schlüsselwertpaare **Eval**, **Function** und **ScriptBlock** bestimmen, wie dynamisch erzeugter Code klassifiziert wird:

|||
|-|-|
|**Eval**|Skript, das ausgeführt wird, indem eine Zeichenfolge an die vom Host bereitgestellte `eval`-Funktion übergeben wird. Standardmäßig wird ein Eval-Skript als **MyCode** klassifiziert.|
|**Function**|Skript, das ausgeführt wird, indem eine Zeichenfolge an den `Function`-Konstruktor übergeben wird. Standardmäßig wird ein Function-Skript als **LibraryCode** klassifiziert.|
|**ScriptBlock**|Skript, das ausgeführt wird, indem eine Zeichenfolge an die Funktionen `setTimeout`, `setImmediate` oder `setInterval` übergeben wird. Standardmäßig wird ein ScriptBlock-Skript als **UnrelatedCode** klassifiziert.|

Sie können den Wert auf eines dieser Schlüsselwörter ändern:

- `MyCode` klassifiziert das Skript als **MyCode**.
- `Library` klassifiziert das Skript als **LibraryCode**.
- `Unrelated` klassifiziert das Skript als **UnrelatedCode**.

**MyCode, Libraries und Unrelated**

Die Schlüsselwertpaare **MyCode**, **Libraries** und **Unrelated** geben die URLs oder Dateien an, die Sie in eine Klassifikation einschließen möchten:

|||
|-|-|
|**MyCode**|Ein Array von URLs oder Dateien, die als **MyCode** klassifiziert werden.|
|**Libraries**|Ein Array von URLs oder Dateien, die als **LibraryCode** klassifiziert werden.|
|**Unrelated**|Ein Array von URLs oder Dateien, die als **UnrelatedCode** klassifiziert werden.|

Die URL oder Datei Zeichenfolge kann ein oder mehrere `*` Zeichen enthalten, die mit NULL oder mehr Zeichen identisch sind. `*` ist identisch mit dem regulären Ausdruck `.*`.
