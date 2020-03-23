---
title: Nur mein Code | Microsoft Docs
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301392"
---
# <a name="just-my-code"></a>Nur eigenen Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entwickler, die .NET Framework-Sprachen verwenden, sind mit der Debuggerfunktion „Nur eigenen Code“ vertraut, die System-, Framework- und andere Nichtbenutzeraufrufe überspringt und diese Aufrufe in den Aufruflistenfenstern reduziert. „Nur eigener Code“ wurde die C++- und JavaScript-Sprachen erweitert. In diesem Thema werden die Einzelheiten der Verwendung von "Nur eigenen Code" in .NET Framework-, in systemeigenen C++- und in JavaScript-Projekten beschrieben.  
  
## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Aktivieren oder Deaktivieren von „Nur eigenen Code“  
 Um Just My Code zu aktivieren oder zu deaktivieren, wählen Sie im **Menü Debug** die Option Optionen **und Einstellungen** aus. Wählen Sie im**Knoten** **"Allgemeines Debuggen"** /  **"Nur meinen Code aktivieren"** aus.  
  
 ![Option zum Aktivieren nur des eigenen Codes im Dialogfeld "Optionen"](../debugger/media/dbg-justmycode-options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
> Die Einstellung **Nur meinen Code aktivieren** ist eine globale Einstellung, die auf alle Visual Studio-Projekte in allen Sprachen angewendet wird.  
  
### <a name="override-call-stack-filtering"></a><a name="BKMK_Override_call_stack_filtering"></a>Überschreiben der Anruflistenfilterung  
 In den Aufruflistenanzeigen wie den Fenstern "Aufrufliste" und "Aufgaben" reduziert "Nur eigenen Code" den Nichtbenutzercode in einen mit Anmerkungen versehenen Frame mit der Bezeichnung `[External Code]`. Um die reduzierten Frames anzuzeigen, wählen Sie Externe **minadien** im Kontextmenü der Aufruflistenanzeige aus.  
  
> [!NOTE]
> Die Einstellung **Externer Code anzeigen** wird im Profiler des aktuellen Benutzers gespeichert. Sie wird auf alle Projekte in allen Sprachen angewendet, die von dem Benutzer geöffnet werden.  
  
## <a name="net-framework-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET Framework Nur mein Code  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_NET_User_and_non_user_code"></a>Benutzer- und Nichtbenutzercode  
 Um Benutzercode von Nicht-Benutzercode zu unterscheiden, betrachtet Just My Code Symboldateien (.pdb) und Programmoptimierungen. Der Debugger behandelt Code als Nichtbenutzercode, wenn die Binärdatei optimiert oder die PDB-Datei nicht verfügbar ist.  
  
 Drei Attribute beeinflussen außerdem, was der Debugger als eigenen Code ansieht:  
  
- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> teilt dem Debugger mit, dass der Code, auf den er angewendet wird, kein eigener Code ist.  
  
- <xref:System.Diagnostics.DebuggerHiddenAttribute> blendet den Code für den Debugger aus, auch wenn Nur mein Code deaktiviert wird.  
  
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> veranlasst den Debugger, den vorliegenden Code nicht in Einzelschritten, sondern in Prozedurschritten zu durchlaufen.  
  
  Der übrige Code wird als Benutzercode angesehen.  
  
### <a name="stepping-behavior"></a><a name="BKMK_NET_Stepping_behavior"></a>Stepping-Verhalten  
 Wenn Sie **Schrittweise einsteigen** (Tastaturverknüpfung: F11) Nicht-Benutzercode, führt der Debugger den Code zur nächsten Benutzeranweisung. Wenn Sie **aussteigen** (Tastatur: Shift + F11), wird der Debugger mit der nächsten Zeile des Benutzercodes ausgeführt. Wenn kein Benutzercode gefunden wird, läuft die Ausführung weiter, bis die App beendet wird, ein Haltepunkt erreicht wird oder eine Ausnahme auftritt.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_NET_Breakpoint_behavior"></a>Breakpoint-Verhalten  
 Wenn Nur mein Code aktiviert ist, können Sie **Alle unterbrechen** (Tastatur: Strg + Alt + Pause) auswählen und die Ausführung an einer Stelle beenden, an der kein Benutzercode angezeigt werden soll. Wenn dies geschieht, wird das Fenster "Kein Quellcode" angezeigt. Wenn Sie anschließend einen Schrittbefehl auswählen, wechselt der Debugger zur nächsten Zeile von Benutzercode.  
  
### <a name="exception-behavior"></a><a name="BKMK_NET_Exception_behavior"></a>Ausnahmeverhalten  
 Wenn ein Ausnahmefehler im Nichtbenutzercode auftritt, unterbricht der Debugger an der Zeile im Benutzercode, in der die Ausnahme generiert wurde.  
  
 Wenn Ausnahmen (erste Chance) für die Ausnahme aktiviert sind, wird die Benutzercodezeile grün hervorgehoben. Die Aufrufliste zeigt einen mit Anmerkungen versehenen Rahmen mit der Bezeichnung **[Externer Code]** an.  
  
## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> „Nur eigenen Code“ in C++  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_CPP_User_and_non_user_code"></a>Benutzer- und Nichtbenutzercode  
 "Nur eigenen Code" in C++ ist anders als "Nur eigenen Code" in .NET Framework und JavaScript, da das Schrittverhalten vom Aufruflistenverhalten unabhängig ist.  
  
 **Aufruflisten**  
  
 Standardmäßig behandelt der Debugger diese Funktionen als Nichtbenutzercode in Aufruflistenfenstern:  
  
- Funktionen mit entfernten Quellinformationen in ihrer Symboldatei.  
  
- Funktionen, bei denen die Symboldateien angeben, dass keine Quelldatei vorhanden ist, die dem Stapelrahmen entspricht.  
  
- Die Funktionen sind in den `*.natjmc`-Dateien im Ordner `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` definiert.  
  
  **Schrittweises Ausführen**  
  
  Standardmäßig werden nur Funktionen, die in `*.natstepfilter`-Dateien im `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`-Ordner festgelegt sind, als Nichhtbenutzercode angesehen.  
  
  Sie können Ihre eigenen `.natstepfilter` und `.natjmc` erstellen, um das Schrittverhalten und das Verhalten der Aufruflistenfenster in `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` anzupassen.  
  
### <a name="stepping-behavior"></a><a name="BKMK_CPP_Stepping_behavior"></a>Stepping-Verhalten  
 Wenn Sie **Schritt in** (Tastaturverknüpfung: F11) Nicht-Benutzercode aus Benutzercode, der Debugger Schritte über den Code zur nächsten Zeile des Benutzercodes. Wenn Sie **aussteigen** (Tastatur: Shift + F11), wird der Debugger mit der nächsten Zeile des Benutzercodes ausgeführt. Wenn kein Benutzercode gefunden wird, läuft die Ausführung weiter, bis die App beendet wird, ein Haltepunkt erreicht wird oder eine Ausnahme auftritt.  
  
 Wenn der Debugger beim Nichtbenutzercode unterbricht (zum Beispiel, wenn ein Befehl "Alle unterbrechen" in Nichtbenutzercode anhält), wird die schrittweise Ausführung im Nichtbenutzercode weitergeführt.  
  
### <a name="exception-behavior"></a><a name="BKMK_CPP_Exception_behavior"></a>Ausnahmeverhalten  
 Wenn der Debugger auf eine Ausnahme trifft, hält er bei der Ausnahme an, unabhängig davon, ob sie im Benutzer- oder Nichtbenutzercode auftritt. Die vom **Benutzer nicht behandelten** Optionen im Dialogfeld **Ausnahmen** werden ignoriert.  
  
### <a name="customize-stepping-behavior"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a>Anpassen des Schrittverhaltens  
 Sie können Funktionen angeben, die zu überspringen sind, indem Sie sie als Nichtbenutzercode in `*.natstepfilter`-Dateien auflisten.  
  
- Um Nichtbenutzercode für alle Benutzer des Visual Studio-Computers anzugeben, fügen `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` Sie dem Ordner die .natstepfilter-Datei hinzu.  
  
- Um Nichtbenutzercode für einen einzelnen Benutzer anzugeben, fügen Sie `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` dem Ordner die .natstepfilter-Datei hinzu.  
  
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
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Funktion|Erforderlich. Gibt eine oder mehreren Funktionen als Nichtbenutzerfunktionen an.|  
|`Name`|Erforderlich. Ein ECMA-262-formatierter regulärer Ausdruck, der den vollständigen Funktionsnamen angibt, der übereinstimmen muss. Beispiel:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> teilt dem Debugger mit, dass alle Methoden in `MyNS::MyClass` als Nichtbenutzercode behandelt werden sollen. Bei der Übereinstimmung muss die Groß-/Kleinschreibung beachtet werden.|  
|`Module`|Optional. Ein ECMA-262-formatierter regulärer Ausdruck, der den vollständigen Pfad zu dem Modul angibt, das die Funktion enthält. Die Groß- und Kleinschreibung wird bei der Übereinstimmung nicht berücksichtigt.|  
|`Action`|Erforderlich. Einer dieser Werte, bei denen die Groß-/Kleinschreibung beachtet werden muss.<br /><br /> -   `NoStepInto`– weist den Debugger an, die übereinstimmende Funktion zu überschreiten.<br />-   `StepInto`– weist den Debugger an, in die `NoStepInto` übereinstimmenden Funktionen einzutreten und alle anderen Funktionen für die übereinstimmenden Funktionen zu überschreiben.|  
  
### <a name="customize-call-stack-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a>Anpassen des Anruflistenverhaltens  
 Sie können Module, Quelldateien und Funktionen angeben, die als Nichtbenutzercode in Aufruflisten behandelt werden, indem sie in `*.natjmc`-Dateien angegeben werden.  
  
- Um Nichtbenutzercode für alle Benutzer des Visual Studio-Computers anzugeben, fügen `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` Sie dem Ordner die .natjmc-Datei hinzu.  
  
- Um Nichtbenutzercode für einen einzelnen Benutzer anzugeben, fügen Sie `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` dem Ordner die .natjmc-Datei hinzu.  
  
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
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der vollständige Pfad des Moduls oder der Module. Sie können die Windows-Platzhalterzeichen `?` (null oder ein Zeichen) und `*` (null oder mehr Zeichen) verwenden. Beispiel:<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> weist den Debugger an, alle Module in `\3rdParty\UtilLibs` auf einem Laufwerk als externen Code zu behandeln.|  
|`Company`|Optional. Der Name des Unternehmens, das das Modul veröffentlicht, das in die ausführbare Datei eingebettet ist. Sie können dieses Attribut verwenden, um die Module zu unterscheiden.|  
  
 **Dateielementattribute**  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der vollständige Pfad der Quelldatei oder -dateien, die als externer Code behandelt werden sollen. Sie können die Windows-Platzhalterzeichen `?` und `*` verwenden, wenn Sie den Pfad angeben.|  
  
 **Funktionselementattribute**  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der vollqualifizierte Name der Funktion, die als externer Code behandelt werden soll.|  
|`Module`|Optional. Der Name oder der vollständige Pfad zu dem Modul, das die Funktion enthält. Sie können dieses Attribut verwenden, um Funktionen mit demselben Namen zu unterscheiden.|  
|`ExceptionImplementation`|Bei Festlegung auf `true` zeigt die Aufrufliste die Funktion an, die die Ausnahme und nicht diese Funktion ausgelöst hat.|  
  
## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> „Nur eigenen Code“ in JavaScript  
  
### <a name="user-and-non-user-code"></a><a name="BKMK_JS_User_and_non_user_code"></a>Benutzer- und Nichtbenutzercode  
 **Codeklassifizierungen**  
  
 "Nur eigenen Code" in JavaScript steuert die schrittweise Ausführung und die Aufruflistenanzeige durch Kategorisieren von Code in einer dieser Klassifizierungen:  
  
|||  
|-|-|  
|**MyCode**|Benutzercode, den Sie besitzen und steuern.|  
|**LibraryCode**|Nichtbenutzercode aus Bibliotheken, den Sie regelmäßig verwenden und die für das ordnungsgemäße Funktionieren Ihrer Anwendung erforderlich sind (z. B. WinJS oder jQuery).|  
|**UnrelatedCode**|Nicht-Benutzercode, der in Ihrer Anwendung ausgeführt werden könnte, aber nicht eigentümer wird und Ihre Anwendung sich nicht direkt darauf verlässt, dass er ordnungsgemäß funktioniert (z. B. ein Werbe-SDK, das Anzeigen anzeigt). In Windows Store-Projekten gilt jeder Code, der von einem HTTP- oder HTTPS-URI in Ihre App geladen wird, als UnrelatedCode.|  
  
 Der JavaScript-Debugger klassifiziert automatisch diese Codetypen:  
  
- Skript, das durch Übergeben einer Zeichenfolge an `eval` die vom Host bereitgestellte Funktion ausgeführt wird, wird als **MyCode**klassifiziert.  
  
- Skript, das durch Übergeben einer `Function` Zeichenfolge an den Konstruktor ausgeführt wird, wird als **LibraryCode**klassifiziert.  
  
- Skripts, die in einem Frameworkverweis enthalten sind, z. B. WinJS oder das Azure SDK, werden als **LibraryCode**klassifiziert.  
  
- Skript, das durch Übergeben einer `setTimeout`Zeichenfolge `setImmediate`an `setInterval` die , ausgeführt wird, oder Funktionen werden als **UnrelatedCode**klassifiziert.  
  
- `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` legt anderen Benutzer- und Nichtbenutzercode für alle Visual Studio-JavaScript-Projekte fest.  
  
  Sie können die Standardklassifizierungen ändern und bestimmte Dateien und URLs klassifizieren, indem Sie dem Stammordner eines Projekts eine JSON-Datei mit dem Namen `mycode.json` hinzufügen.  
  
  Der restliche Code wird als **MyCode** klassifiziert.  
  
### <a name="stepping-behavior"></a><a name="BKMK_JS_Stepping_behavior"></a>Stepping-Verhalten  
  
- Wenn eine Funktion nicht Benutzer (**MyCode**) Code ist, verhält sich **Step Into** (Tastaturverknüpfung: F11) wie **Step Over** (Tastatur: F10).  
  
- Wenn ein Schritt im Nicht-Benutzercode (**LibraryCode** oder **UnrelatedCode**) beginnt, verhält sich das Stepping vorübergehend so, als ob Nur mein Code nicht aktiviert wäre. Sobald Sie zurück zum Benutzercode wechseln, wird die schrittweise Ausführung für "Nur eigenen Code" erneut aktiviert.  
  
- Wenn ein Schritt im Benutzercode dazu führt, dass der aktuelle Ausführungskontext (wie etwa das Durchführen eines Schritts in der letzten Zeile eines Ereignishandlers) verlassen wird, hält der Debugger bei der nächsten ausgeführten Benutzercodezeile an. Wenn z. B. ein Rückruf im **LibraryCode-Code** ausgeführt wird, wird der Debugger fortgesetzt, bis die nächste Zeile des Benutzercodes ausgeführt wird.  
  
- **Step Out** (Tastatur: Umschalt + F11) stoppt in der nächsten Zeile des Benutzercodes. Wenn kein Benutzercode gefunden wird, läuft die Ausführung weiter, bis die App beendet wird, ein Haltepunkt erreicht wird oder eine Ausnahme auftritt.  
  
### <a name="breakpoint-behavior"></a><a name="BKMK_JS_Breakpoint_behavior"></a>Breakpoint-Verhalten  
  
- Haltepunkte, die im Code festgelegt wurden, werden immer erreicht, unabhängig von der Klassifizierung dieses Codes.  
  
- Wenn das `debugger`-Schlüsselwort gefunden wird in:  
  
  - **LibraryCode-Code,** der Debugger wird immer unterbrochen.  

  - **UnrelatedCode-Code,** der Debugger wird nicht beendet.  
  
### <a name="exception-behavior"></a><a name="BKMK_JS_Exception_behavior"></a>Ausnahmeverhalten  
 Wenn ein Ausnahmefehler auftritt in:  
  
- **MyCode-** oder **LibraryCode-Code** wird immer unterbrochen.  
  
- **UnrelatedCode-Code,** und **MyCode-** oder **LibraryCode-Code** befindet sich auf der Aufrufliste, der Debugger wird unterbrochen.  
  
  Wenn Ausnahmen der ersten Chance für die Ausnahme im Dialogfeld Ausnahmen aktiviert sind und die Ausnahme in **LibraryCode** oder **UnrelatedCode-Code** ausgelöst wird:  
  
- Wenn die Ausnahme behandelt wird, unterbricht der Debugger nicht.  
  
- Wenn die Ausnahme nicht behandelt wird, unterbricht der Debugger.  
  
### <a name="customize-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a>Anpassen von Just My Code  
 Um Benutzer- und Nichtbenutzercode für ein einzelnes Visual Studio-Projekt zu kategorisieren, fügen Sie dem Stammordner des Projekts eine JSON-Datei mit dem Namen `mycode.json` hinzu.  
  
 Klassifizierungen werden in dieser Reihenfolge ausgeführt:  
  
1. Standardklassifizierungen  
  
2. Klassifizierungen in der `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Datei  
  
3. Klassifizierungen in der Datei `mycode. json` des aktuellen Projekts  
  
   Jeder Klassifizierungsschritt überschreibt die vorherigen Schritte. Eine JSon-Datei muss nicht alle Schlüsselwertpaare auflisten, und die **Werte MyCode**, **Libraries**und **Unrelated** können leere Arrays sein.  
  
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
  
 Die Schlüsselwertpaare **Eval**, **Function**und **ScriptBlock** bestimmen, wie dynamisch generierter Code klassifiziert wird.  
  
|||  
|-|-|  
|**Eval**|Skript, das ausgeführt wird, indem eine Zeichenfolge an die vom Host bereitgestellte `eval`-Funktion übergeben wird. Standardmäßig wird ein Eval-Skript als **MyCode** klassifiziert.|  
|**Funktion**|Skript, das ausgeführt wird, indem eine Zeichenfolge an den `Function`-Konstruktor übergeben wird. Standardmäßig wird ein Function-Skript als **LibraryCode** klassifiziert.|  
|**ScriptBlock**|Skript, das ausgeführt wird, indem eine Zeichenfolge an die Funktionen `setTimeout`, `setImmediate` oder `setInterval` übergeben wird. Standardmäßig wird ein ScriptBlock-Skript als **UnrelatedCode** klassifiziert.|  
  
 Sie können den Wert auf eines dieser Schlüsselwörter ändern:  
  
- `MyCode`klassifiziert das Skript als **MyCode**.  
  
- `Library`klassifiziert das Skript als **LibraryCode**.  
  
- `Unrelated`klassifiziert das Skript als **UnrelatedCode**.  
  
  **MyCode, Libraries und Unrelated**  
  
  Die Schlüsselwertpaare **MyCode**, **Libraries**und **Nicht verwandte** Schlüsselwert geben die URLs oder Dateien an, die Sie in eine Klassifizierung einbeziehen möchten:  
  
|||  
|-|-|  
|**MyCode**|Ein Array von URLs oder Dateien, die als **MyCode**klassifiziert sind.|  
|**Bibliotheken**|Ein Array von URLs oder Dateien, die als **LibraryCode**klassifiziert sind.|  
|**Unrelated**|Ein Array von URLs oder Dateien, die als **UnrelatedCode**klassifiziert sind.|  
  
 Die URL-Zeichenfolge oder Dateizeichenfolge kann eine oder mehrere `*`-Zeichen enthalten, die mit null oder mehr Zeichen übereinstimmen. `*` entspricht dem regulären Ausdruck `.*`.
