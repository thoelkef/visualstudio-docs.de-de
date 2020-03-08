---
title: Nur eigenen Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efcabf9c7dc201f95515cd24bf3a14727f7149fe
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410153"
---
# <a name="just-my-code"></a>Nur eigenen Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entwickler, die .NET Framework-Sprachen verwenden, sind mit der Debuggerfunktion „Nur eigenen Code“ vertraut, die System-, Framework- und andere Nichtbenutzeraufrufe überspringt und diese Aufrufe in den Aufruflistenfenstern reduziert. „Nur eigener Code“ wurde die C++- und JavaScript-Sprachen erweitert. In diesem Thema werden die Einzelheiten der Verwendung von "Nur eigenen Code" in .NET Framework-, in systemeigenen C++- und in JavaScript-Projekten beschrieben.  
  
## <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Aktivieren oder Deaktivieren von „Nur eigenen Code“  
 Um nur eigenen Code zu aktivieren oder zu deaktivieren, wählen Sie im Menü **Debuggen** die **Option Optionen und Einstellungen** aus. Wählen Sie im Knoten **Debugging** / **Allgemein** die Option **nur eigenen Code aktivieren**aus.  
  
 ![Aktivieren von nur eigenen Code im Dialogfeld "Optionen"](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> Die Einstellung **nur eigenen Code aktivieren** ist eine globale Einstellung, die auf alle Visual Studio-Projekte in allen Sprachen angewendet wird.  
  
### <a name="BKMK_Override_call_stack_filtering"></a>Überschreiben der aufrufstackfilterung  
 In den Aufruflistenanzeigen wie den Fenstern "Aufrufliste" und "Aufgaben" reduziert "Nur eigenen Code" den Nichtbenutzercode in einen mit Anmerkungen versehenen Frame mit der Bezeichnung `[External Code]`. Um die reduzierten Frames anzuzeigen, wählen Sie im Kontextmenü der Anzeige der Anzeigeliste **externer Code anzeigen** aus.  
  
> [!NOTE]
> Die Einstellung **externen Code anzeigen** wird im Profiler des aktuellen Benutzers gespeichert. Sie wird auf alle Projekte in allen Sprachen angewendet, die von dem Benutzer geöffnet werden.  
  
## <a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Framework nur eigenen Code  
  
### <a name="BKMK_NET_User_and_non_user_code"></a>Benutzer-und Nichtbenutzer Code  
 Um Benutzercode von Nichtbenutzer Code zu unterscheiden, prüft nur eigenen Code Symbol Dateien (PDB-Dateien) und Programm Optimierungen. Der Debugger behandelt Code als Nichtbenutzercode, wenn die Binärdatei optimiert oder die PDB-Datei nicht verfügbar ist.  
  
 Drei Attribute beeinflussen außerdem, was der Debugger als eigenen Code ansieht:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> teilt dem Debugger mit, dass der Code, auf den er angewendet wird, kein eigener Code ist.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> blendet den Code für den Debugger aus, auch wenn Nur mein Code deaktiviert wird.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> veranlasst den Debugger, den vorliegenden Code nicht in Einzelschritten, sondern in Prozedurschritten zu durchlaufen.  
  
  Der übrige Code wird als Benutzercode angesehen.  
  
### <a name="BKMK_NET_Stepping_behavior"></a>Schritt Verhalten  
 Wenn Sie Einzel **Schritt** (Tastenkombination: F11) Nichtbenutzer Code ausführen, führt der Debugger den Code bis zur nächsten Benutzer Anweisung aus. Wenn Sie einen **Schritt ausführen** (Tastatur: UMSCHALT + F11), wird der Debugger zur nächsten Zeile des Benutzercodes ausgeführt. Wenn kein Benutzercode gefunden wird, läuft die Ausführung weiter, bis die App beendet wird, ein Haltepunkt erreicht wird oder eine Ausnahme auftritt.  
  
### <a name="BKMK_NET_Breakpoint_behavior"></a>Haltepunkt Verhalten  
 Wenn nur eigenen Code aktiviert ist, können Sie **Alle unterbrechen** (Tastatur: Strg + Alt + Pause) auswählen und die Ausführung an einer Stelle beenden, an der kein Benutzer Code zur Anzeige vorhanden ist. Wenn dies geschieht, wird das Fenster "Kein Quellcode" angezeigt. Wenn Sie anschließend einen Schrittbefehl auswählen, wechselt der Debugger zur nächsten Zeile von Benutzercode.  
  
### <a name="BKMK_NET_Exception_behavior"></a>Ausnahme Verhalten  
 Wenn ein Ausnahmefehler im Nichtbenutzercode auftritt, unterbricht der Debugger an der Zeile im Benutzercode, in der die Ausnahme generiert wurde.  
  
 Wenn Ausnahmen (erste Chance) für die Ausnahme aktiviert sind, wird die Benutzercodezeile grün hervorgehoben. In der aufrufsstapel wird ein mit Anmerkungen versehene Frame mit der Bezeichnung **[externer Code]** angezeigt.  
  
## <a name="BKMK_C___Just_My_Code"></a> „Nur eigenen Code“ in C++  
  
### <a name="BKMK_CPP_User_and_non_user_code"></a>Benutzer-und Nichtbenutzer Code  
 "Nur eigenen Code" in C++ ist anders als "Nur eigenen Code" in .NET Framework und JavaScript, da das Schrittverhalten vom Aufruflistenverhalten unabhängig ist.  
  
 **Aufruf Listen**  
  
 Standardmäßig behandelt der Debugger diese Funktionen als Nichtbenutzercode in Aufruflistenfenstern:  
  
- Funktionen mit entfernten Quellinformationen in ihrer Symboldatei.  
  
- Funktionen, bei denen die Symboldateien angeben, dass keine Quelldatei vorhanden ist, die dem Stapelrahmen entspricht.  
  
- Die Funktionen sind in den `*.natjmc`-Dateien im Ordner `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` definiert.  
  
  **Einspringen**  
  
  Standardmäßig werden nur Funktionen, die in `*.natstepfilter`-Dateien im `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`-Ordner festgelegt sind, als Nichhtbenutzercode angesehen.  
  
  Sie können Ihre eigenen `.natstepfilter` und `.natjmc` erstellen, um das Schrittverhalten und das Verhalten der Aufruflistenfenster in `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` anzupassen.  
  
### <a name="BKMK_CPP_Stepping_behavior"></a>Schritt Verhalten  
 Wenn Sie Einzel **Schritt** (Tastenkombination: F11) Nichtbenutzer Code aus Benutzercode einfügen, führt der Debugger den Code bis zur nächsten Zeile des Benutzercodes aus. Wenn Sie einen **Schritt ausführen** (Tastatur: UMSCHALT + F11), wird der Debugger zur nächsten Zeile des Benutzercodes ausgeführt. Wenn kein Benutzercode gefunden wird, läuft die Ausführung weiter, bis die App beendet wird, ein Haltepunkt erreicht wird oder eine Ausnahme auftritt.  
  
 Wenn der Debugger beim Nichtbenutzercode unterbricht (zum Beispiel, wenn ein Befehl "Alle unterbrechen" in Nichtbenutzercode anhält), wird die schrittweise Ausführung im Nichtbenutzercode weitergeführt.  
  
### <a name="BKMK_CPP_Exception_behavior"></a>Ausnahme Verhalten  
 Wenn der Debugger auf eine Ausnahme trifft, hält er bei der Ausnahme an, unabhängig davon, ob sie im Benutzer- oder Nichtbenutzercode auftritt. Die vom **Benutzer unbehandelten** Optionen im Dialogfeld **Ausnahmen** werden ignoriert.  
  
### <a name="BKMK_CPP_Customize_stepping_behavior"></a>Anpassen des schrittweisen Verhaltens  
 Sie können Funktionen angeben, die zu überspringen sind, indem Sie sie als Nichtbenutzercode in `*.natstepfilter`-Dateien auflisten.  
  
- Um Nichtbenutzer Code für alle Benutzer des Visual Studio-Computers anzugeben, fügen Sie die natstepfilter-Datei dem Ordner `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` hinzu.  
  
- Fügen Sie dem `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` Ordner die natstepfilter-Datei hinzu, um Nichtbenutzer Code für einen einzelnen Benutzer anzugeben.  
  
  NATSTEPFILTER-Dateien sind XML-Dateien mit folgender Syntax:  
  
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
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|Funktion|Erforderlich. Gibt eine oder mehreren Funktionen als Nichtbenutzerfunktionen an.|  
|`Name`|Erforderlich. Ein ECMA-262-formatierter regulärer Ausdruck, der den vollständigen Funktionsnamen angibt, der übereinstimmen muss. Beispiel:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> teilt dem Debugger mit, dass alle Methoden in `MyNS::MyClass` als Nichtbenutzercode behandelt werden sollen. Bei der Übereinstimmung muss die Groß-/Kleinschreibung beachtet werden.|  
|`Module`|Optional. Ein ECMA-262-formatierter regulärer Ausdruck, der den vollständigen Pfad zu dem Modul angibt, das die Funktion enthält. Die Groß- und Kleinschreibung wird bei der Übereinstimmung nicht berücksichtigt.|  
|`Action`|Erforderlich. Einer dieser Werte, bei denen die Groß-/Kleinschreibung beachtet werden muss.<br /><br /> -   `NoStepInto` – weist den Debugger an, die übereinstimmende Funktion zu überspringen.<br />-   `StepInto` – weist den Debugger an, die übereinstimmenden Funktionen schrittweise zu durchlaufen und alle anderen `NoStepInto` für die übereinstimmenden Funktionen überschreiben.|  
  
### <a name="BKMK_CPP_Customize_call_stack_behavior"></a>Anpassen des Verhaltens von aufrufstapeln  
 Sie können Module, Quelldateien und Funktionen angeben, die als Nichtbenutzercode in Aufruflisten behandelt werden, indem sie in `*.natjmc`-Dateien angegeben werden.  
  
- Um Nichtbenutzer Code für alle Benutzer des Visual Studio-Computers anzugeben, fügen Sie die natjmc-Datei dem Ordner `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` hinzu.  
  
- Um Nichtbenutzer Code für einen einzelnen Benutzer anzugeben, fügen Sie die natjmc-Datei dem Ordner `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` hinzu.  
  
  NATJMC-Dateien sind XML-Dateien mit folgender Syntax:  
  
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
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der vollständige Pfad des Moduls oder der Module. Sie können die Windows-Platzhalterzeichen `?` (null oder ein Zeichen) und `*` (null oder mehr Zeichen) verwenden. Beispiel:<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> weist den Debugger an, alle Module in `\3rdParty\UtilLibs` auf einem Laufwerk als externen Code zu behandeln.|  
|`Company`|Optional. Der Name des Unternehmens, das das Modul veröffentlicht, das in die ausführbare Datei eingebettet ist. Sie können dieses Attribut verwenden, um die Module zu unterscheiden.|  
  
 **Dateielementattribute**  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der vollständige Pfad der Quelldatei oder -dateien, die als externer Code behandelt werden sollen. Sie können die Windows-Platzhalterzeichen `?` und `*` verwenden, wenn Sie den Pfad angeben.|  
  
 **Funktionselementattribute**  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der vollqualifizierte Name der Funktion, die als externer Code behandelt werden soll.|  
|`Module`|Optional. Der Name oder der vollständige Pfad zu dem Modul, das die Funktion enthält. Sie können dieses Attribut verwenden, um Funktionen mit demselben Namen zu unterscheiden.|  
|`ExceptionImplementation`|Bei Festlegung auf `true` zeigt die Aufrufliste die Funktion an, die die Ausnahme und nicht diese Funktion ausgelöst hat.|  
  
## <a name="BKMK_JavaScript_Just_My_Code"></a> „Nur eigenen Code“ in JavaScript  
  
### <a name="BKMK_JS_User_and_non_user_code"></a>Benutzer-und Nichtbenutzer Code  
 **Code Klassifizierungen**  
  
 "Nur eigenen Code" in JavaScript steuert die schrittweise Ausführung und die Aufruflistenanzeige durch Kategorisieren von Code in einer dieser Klassifizierungen:  
  
|||  
|-|-|  
|**MyCode**|Benutzercode, den Sie besitzen und steuern.|  
|**LibraryCode**|Nichtbenutzercode aus Bibliotheken, den Sie regelmäßig verwenden und die für das ordnungsgemäße Funktionieren Ihrer Anwendung erforderlich sind (z. B. WinJS oder jQuery).|  
|**UnrelatedCode**|Nichtbenutzer Code, der in Ihrer Anwendung ausgeführt werden kann, aber Sie sind nicht Besitzer, und Ihre Anwendung wird nicht direkt darauf angewiesen, ordnungsgemäß zu funktionieren (z. b. ein Werbe-SDK, das ADS anzeigt). In Windows Store-Projekten gilt jeder Code, der von einem HTTP- oder HTTPS-URI in Ihre App geladen wird, als UnrelatedCode.|  
  
 Der JavaScript-Debugger klassifiziert automatisch diese Codetypen:  
  
- Skript, das ausgeführt wird, indem eine Zeichenfolge an die vom Host bereitgestellte `eval`-Funktion übergeben wird, wird als **MyCode**klassifiziert.  
  
- Skript, das ausgeführt wird, indem eine Zeichenfolge an den `Function`-Konstruktor übergeben wird, wird als **librarycode**klassifiziert.  
  
- Skripts, die in einem frameworkverweis (z. b. winjs oder Azure SDK) enthalten sind, werden als **librarycode**klassifiziert.  
  
- Skript, das ausgeführt wird, indem eine Zeichenfolge an die Funktionen `setTimeout`, `setImmediate`oder `setInterval` übergeben wird, wird als **unrelatedcode**klassifiziert.  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` legt anderen Benutzer- und Nichtbenutzercode für alle Visual Studio-JavaScript-Projekte fest.  
  
  Sie können die Standardklassifizierungen ändern und bestimmte Dateien und URLs klassifizieren, indem Sie dem Stammordner eines Projekts eine JSON-Datei mit dem Namen `mycode.json` hinzufügen.  
  
  Der restliche Code wird als **MyCode** klassifiziert.  
  
### <a name="BKMK_JS_Stepping_behavior"></a>Schritt Verhalten  
  
- Wenn es sich bei einer Funktion nicht um Benutzercode (**MyCode**) handelt, verhält sich der Einzel **Schritt** (Tastenkombination: F11) als Prozedur **Schritt** (Tastatur: F10).  
  
- Wenn ein Schritt in einem Nichtbenutzer Code (**librarycode** oder **unrelatedcode**) beginnt, verhält sich die schrittweise temporär, als ob nur eigenen Code nicht aktiviert ist. Sobald Sie zurück zum Benutzercode wechseln, wird die schrittweise Ausführung für "Nur eigenen Code" erneut aktiviert.  
  
- Wenn ein Schritt im Benutzercode dazu führt, dass der aktuelle Ausführungskontext (wie etwa das Durchführen eines Schritts in der letzten Zeile eines Ereignishandlers) verlassen wird, hält der Debugger bei der nächsten ausgeführten Benutzercodezeile an. Wenn ein Rückruf beispielsweise in **librarycode** -Code ausgeführt wird, wird der Debugger so lange fortgesetzt, bis die nächste Zeile des Benutzercodes ausgeführt wird.  
  
- Rück **Sprung** (Tastatur: UMSCHALT + F11) wird in der nächsten Zeile des Benutzercodes angehalten. Wenn kein Benutzercode gefunden wird, läuft die Ausführung weiter, bis die App beendet wird, ein Haltepunkt erreicht wird oder eine Ausnahme auftritt.  
  
### <a name="BKMK_JS_Breakpoint_behavior"></a>Haltepunkt Verhalten  
  
- Haltepunkte, die im Code festgelegt wurden, werden immer erreicht, unabhängig von der Klassifizierung dieses Codes.  
  
- Wenn das `debugger`-Schlüsselwort gefunden wird in:  
  
  - **Librarycode** -Code, der Debugger unterbricht immer.  

  - **Unrelatedcode** -Code, der Debugger wird nicht angehalten.  
  
### <a name="BKMK_JS_Exception_behavior"></a>Ausnahme Verhalten  
 Wenn ein Ausnahmefehler auftritt in:  
  
- **MyCode** -oder **librarycode** -Code, der Debugger unterbricht immer.  
  
- **Unrelatedcode** -Code, und **MyCode** -oder **librarycode** -Code befindet sich in der-aufrufsstapel, der Debugger wird unterbrochen.  
  
  Wenn Ausnahmen der ersten Chance für die Ausnahme im Dialogfeld Ausnahmen aktiviert sind und die Ausnahme in **librarycode** -oder **unrelatedcode** -Code ausgelöst wird:  
  
- Wenn die Ausnahme behandelt wird, unterbricht der Debugger nicht.  
  
- Wenn die Ausnahme nicht behandelt wird, unterbricht der Debugger.  
  
### <a name="BKMK_JS_Customize_Just_My_Code"></a>Nur eigenen Code anpassen  
 Um Benutzer- und Nichtbenutzercode für ein einzelnes Visual Studio-Projekt zu kategorisieren, fügen Sie dem Stammordner des Projekts eine JSON-Datei mit dem Namen `mycode.json` hinzu.  
  
 Klassifizierungen werden in dieser Reihenfolge ausgeführt:  
  
1. Standardklassifizierungen  
  
2. Klassifizierungen in der `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Datei  
  
3. Klassifizierungen in der Datei `mycode. json` des aktuellen Projekts  
  
   Jeder Klassifizierungsschritt überschreibt die vorherigen Schritte. Eine JSON-Datei muss nicht alle Schlüssel-Wert-Paare auflisten, und **MyCode**, **Bibliotheken**und verknüpfte **Werte können** leere Arrays sein.  
  
   JSON-Dateien für eigenen Code verwenden folgende Syntax:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval, Function und ScriptBlock**  
  
 Die Schlüssel-Wert-Paare **eval**, **Function**und **ScriptBlock** legen fest, wie dynamisch generierter Code klassifiziert wird.  
  
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
  
  Die Paare **MyCode**, **Libraries**und nicht verknüpfte **Schlüsselwerte** geben die URLs oder Dateien an, die Sie in eine Klassifizierung einschließen möchten:  
  
|||  
|-|-|  
|**MyCode**|Ein Array von URLs oder Dateien, die als **MyCode**klassifiziert werden.|  
|**Bibliotheken**|Ein Array von URLs oder Dateien, die als **librarycode**klassifiziert werden.|  
|**Unrelated**|Ein Array von URLs oder Dateien, die als **unrelatedcode**klassifiziert werden.|  
  
 Die URL-Zeichenfolge oder Dateizeichenfolge kann eine oder mehrere `*`-Zeichen enthalten, die mit null oder mehr Zeichen übereinstimmen. `*` entspricht dem regulären Ausdruck `.*`.
