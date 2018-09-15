---
title: Debuggen von Benutzercode mit nur mein Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a2873f691fdaa1251a5562e21e2bbd0467eb2e2
ms.sourcegitcommit: 7bb0225e1fd45999ce09e0b49c2cfae515c27e11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2018
ms.locfileid: "45612752"
---
# <a name="specify-whether-to-debug-only-user-code-using-just-my-code-in-visual-studio"></a>Gibt an, ob nur Benutzercode, die mit nur mein Code in Visual Studio debuggen
Sie können konfigurieren, dass Visual Studio für das automatische System-, Framework- und andere Aufrufe überspringen und diese Aufrufe in das Aufruflistenfenster zu reduzieren. Das Feature, das aktiviert oder deaktiviert dieses Verhalten wird aufgerufen, *nur mein Code*. In diesem Thema wird beschrieben, wie nur mein Code in c#, Visual Basic, C++ und JavaScript-Projekten verwendet wird.

Für die meisten Programmiersprachen wird nur mein Code standardmäßig aktiviert.
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Aktivieren Sie oder deaktivieren Sie nur mein Code  
 Wählen Sie zum Aktivieren oder deaktivieren nur mein Code, der **Tools > Optionen** Menü in Visual Studio. In der **Debuggen** > **allgemeine** Knoten auswählen, oder deaktivieren Sie **nur meinen Code aktivieren**.
  
 ![Aktivieren Sie im Dialogfeld "Optionen" nur mein Code](../debugger/media/dbg_justmycode_options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  Die **nur meinen Code aktivieren** ist eine globale Einstellung, die für alle Visual Studio-Projekte in allen Sprachen angewendet wird.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> Nicht benutzerseitiger Code im Aufruflistenansicht anzeigen  
 In Ansichten, die zeigen, wie z. B. die Aufrufliste, die **Aufrufliste** und **Aufgaben** Windows "," nur mein Code reduziert Nichtbenutzercode in einen mit Anmerkungen versehenen Frame mit der Bezeichnung `[External Code]`. Um die reduzierten Frames anzuzeigen, wählen **externen Code anzeigen** im Kontextmenü der Aufrufliste angezeigt.

 ![Externen Code anzeigen, in das Aufruflistenfenster](../debugger/media/dbg_justmycode_showexternalcode.png "DBG_JustMyCode_ShowExternalCode")
  
> [!NOTE]
>  Die **externen Code anzeigen** Einstellung des aktuellen Benutzers Profiler gespeichert ist. Sie wird auf alle Projekte in allen Sprachen angewendet, die von dem Benutzer geöffnet werden.

##  <a name="identify-user-code-while-debugging"></a>Identifizieren von Benutzercode während des Debuggens 

Die **Module** Fenster können Sie ermitteln, welche Codemodule, die der Debugger wird als Benutzercode oder mein Code behandeln, zusammen mit Informationen wie z. B. das Symbol Status für das Modul geladen. Weitere Informationen finden Sie unter [mit, wie der Debugger an Ihre app angefügt vertrauter machen](../debugger/debugger-tips-and-tricks.md#modules_window).
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> Nur eigenen Code für .NET framework  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> Benutzer-und Nichtbenutzercode  
 Nur mein Code untersucht um Benutzercode von Nichtbenutzercode zu unterscheiden, die Symboldateien (.pdb) und programmoptimierungen. Der Debugger behandelt Code als Nichtbenutzercode, wenn die Binärdatei optimiert oder die PDB-Datei nicht verfügbar ist.
  
 Drei Attribute beeinflussen außerdem, was der Debugger als eigenen Code ansieht:  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> teilt dem Debugger mit, dass der Code, auf den er angewendet wird, kein eigener Code ist.  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> blendet den Code für den Debugger aus, auch wenn Nur mein Code deaktiviert wird.  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute> veranlasst den Debugger, den vorliegenden Code nicht in Einzelschritten, sondern in Prozedurschritten zu durchlaufen.  
  
 Der übrige Code wird als Benutzercode angesehen.  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> Schrittverhalten  
 Wenn Sie **Einzelschritt** (Tastenkombination: F11) nicht benutzerseitiger Code, überspringt der Debugger den Code an die nächste benutzeranweisung. Wenn Sie **Ausführen bis Rücksprung** (Tastatur: UMSCHALT + F11), der Debugger, die in die nächste Zeile des Benutzercodes ausgeführt wird. Wenn kein Benutzercode festgestellt wird, wird die Ausführung wird, bis die app fortgeführt beendet wird, ein Haltepunkt erreicht wird, oder eine Ausnahme auftritt.  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> Haltepunktverhalten  
 Wenn nur mein Code aktiviert ist, können Sie **alle unterbrechen** (Tastatur: Strg + Alt + UNTBR) und Beenden der Ausführung an einem Speicherort vorhanden ist kein Benutzercode angezeigt. Wenn dies geschieht, wird das Fenster "Kein Quellcode" angezeigt. Wenn Sie anschließend einen Schrittbefehl auswählen, wechselt der Debugger zur nächsten Zeile von Benutzercode.  
  
###  <a name="BKMK_NET_Exception_behavior"></a> Ausnahmeverhalten  
 Wenn ein Ausnahmefehler im Nichtbenutzercode auftritt, unterbricht der Debugger an der Zeile im Benutzercode, in der die Ausnahme generiert wurde.  
  
 Wenn Ausnahmen (erste Chance) für die Ausnahme aktiviert sind, wird die Benutzercodezeile grün hervorgehoben. Die Aufrufliste zeigt einen mit Anmerkungen versehenen Frame mit der Bezeichnung **[externer Code]**.  
  
##  <a name="BKMK_C___Just_My_Code"></a> C++ nur mein Code  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> Benutzer-und Nichtbenutzercode  
"Nur eigenen Code" in C++ ist anders als "Nur eigenen Code" in .NET Framework und JavaScript, da das Schrittverhalten vom Aufruflistenverhalten unabhängig ist.  

Ab Visual Studio 2017 15.8, Sie können angeben, ob nur mein Code für die Verwendung von C++ **Tools** > **Optionen** > **Debuggen**  >  **Allgemeine** > **nur meinen Code aktivieren** (er ist standardmäßig aktiviert). Dies ist äquivalent zur Verwendung der [/JMC (nur mein Codedebuggen)](/cpp/build/reference/jmc) Compilerschalter.
  
 **Aufruflisten**  
  
 Standardmäßig behandelt der Debugger diese Funktionen als Nichtbenutzercode in Aufruflistenfenstern:  
  
-   Funktionen mit entfernten Quellinformationen in ihrer Symboldatei.  
  
-   Funktionen, bei denen die Symboldateien angeben, dass keine Quelldatei vorhanden ist, die dem Stapelrahmen entspricht.  
  
-   Die Funktionen sind in den `*.natjmc`-Dateien im Ordner `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` definiert.  
  
 **Stepping**  
  
 Standardmäßig werden nur Funktionen, die in `*.natstepfilter`-Dateien im `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`-Ordner festgelegt sind, als Nichhtbenutzercode angesehen.  
  
 Sie können Ihre eigenen `.natstepfilter` und `.natjmc` erstellen, um das Schrittverhalten und das Verhalten der Aufruflistenfenster in `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` anzupassen.  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> Schrittverhalten  
 Wenn Sie **Einzelschritt** (Tastenkombination: F11) Nichtbenutzercode aus Benutzercode, überspringt der Debugger den Code in die nächste Zeile von Benutzercode. Wenn Sie **Ausführen bis Rücksprung** (Tastatur: UMSCHALT + F11), der Debugger, die in die nächste Zeile des Benutzercodes ausgeführt wird. Wenn kein Benutzercode festgestellt wird, wird die Ausführung wird, bis die app fortgeführt beendet wird, ein Haltepunkt erreicht wird, oder eine Ausnahme auftritt.  
  
 Wenn der Debugger beim Nichtbenutzercode unterbricht (zum Beispiel, wenn ein Befehl "Alle unterbrechen" in Nichtbenutzercode anhält), wird die schrittweise Ausführung im Nichtbenutzercode weitergeführt.
  
###  <a name="BKMK_CPP_Exception_behavior"></a> Ausnahmeverhalten  
 Wenn der Debugger eine Ausnahme trifft, wird es für die Ausnahme, unabhängig davon, ob es in Benutzer- oder Nichtbenutzercode beendet. Die **vom Benutzercode unbehandelt** "Optionen" der **Ausnahmen** im Dialogfeld werden ignoriert.  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Anpassen des schrittverhaltens  
 Sie können Funktionen angeben, die zu überspringen sind, indem Sie sie als Nichtbenutzercode in `*.natstepfilter`-Dateien auflisten.  
  
-   Um Nichtbenutzercode für alle Benutzer des Visual Studio-Computers anzugeben, fügen Sie die natstepfilter-Datei, um die `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` Ordner.  
  
-   Um Nichtbenutzercode für einen einzelnen Benutzer anzugeben, fügen Sie die natstepfilter-Datei, um die `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` Ordner.  
  
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
|`Name`|Erforderlich. Ein ECMA-262-formatierter regulärer Ausdruck, der den vollständigen Funktionsnamen angibt, der übereinstimmen muss. Zum Beispiel:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> teilt dem Debugger mit, dass alle Methoden in `MyNS::MyClass` als Nichtbenutzercode behandelt werden sollen. Bei der Übereinstimmung muss die Groß-/Kleinschreibung beachtet werden.|  
|`Module`|Dies ist optional. Ein ECMA-262-formatierter regulärer Ausdruck, der den vollständigen Pfad zu dem Modul angibt, das die Funktion enthält. Die Groß- und Kleinschreibung wird bei der Übereinstimmung nicht berücksichtigt.|  
|`Action`|Erforderlich. Einer dieser Werte, bei denen die Groß-/Kleinschreibung beachtet werden muss.<br /><br /> -   `NoStepInto`  – weist den Debugger an die übereinstimmende Funktion zu überspringen.<br />-   `StepInto`  – weist den Debugger an die übereinstimmenden Funktionen schrittweise überschreiben alle anderen `NoStepInto` für die übereinstimmenden Funktionen.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Anpassen des aufruflistenverhaltens  
 Sie können Module, Quelldateien und Funktionen angeben, die als Nichtbenutzercode in Aufruflisten behandelt werden, indem sie in `*.natjmc`-Dateien angegeben werden.  
  
-   Um Nichtbenutzercode für alle Benutzer des Visual Studio-Computers anzugeben, fügen Sie die natjmc-Datei, um die `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` Ordner.  
  
-   Um Nichtbenutzercode für einen einzelnen Benutzer anzugeben, fügen Sie die natjmc-Datei, um die `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` Ordner.  
  
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
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der vollständige Pfad des Moduls oder der Module. Sie können die Windows-Platzhalterzeichen `?` (kein oder ein Zeichen) und `*` (null oder mehr Zeichen). Ein auf ein Objekt angewendeter<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> weist den Debugger an, alle Module in `\3rdParty\UtilLibs` auf einem Laufwerk als externen Code zu behandeln.|  
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
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> JavaScript nur mein Code  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> Benutzer-und Nichtbenutzercode  
 **Codeklassifizierungen**  
  
 "Nur eigenen Code" in JavaScript steuert die schrittweise Ausführung und die Aufruflistenanzeige durch Kategorisieren von Code in einer dieser Klassifizierungen:  
  
|||  
|-|-|  
|**MyCode**|Benutzercode, den Sie besitzen und steuern.|  
|**LibraryCode**|Nichtbenutzercode aus Bibliotheken, den Sie regelmäßig verwenden und die für das ordnungsgemäße Funktionieren Ihrer Anwendung erforderlich sind (z. B. WinJS oder jQuery).|  
|**UnrelatedCode**|Nichtbenutzercode, die in Ihrer Anwendung, aber Sie ausgeführt werden konnte nicht besitzen, es und Ihrer Anwendung nicht direkt beruht darauf, um ordnungsgemäß funktioniert. (Beispielsweise könnte dies enthalten eine Advertising SDK, das Anzeigen anzeigt.) In UWP-Projekten wird jeglicher Code, der in Ihrer app von einem HTTP- oder HTTPS-URI geladen wird, als UnrelatedCode.|  
  
 Der JavaScript-Debugger klassifiziert automatisch diese Codetypen:  
  
-   Skript, das ausgeführt wird, indem Sie die Übergabe einer Zeichenfolge an der vom Host bereitgestellten `eval` Funktion wird als klassifiziert **MyCode**.  
  
-   Skript, das ausgeführt wird, indem eine Zeichenfolge übergeben, die `Function` Konstruktor wird als klassifiziert **LibraryCode**.  
  
-   Skript, das in einem frameworkverweis, wie z. B. WinJS oder das Azure SDK enthalten ist, wird als klassifiziert **LibraryCode**.  
  
-   Skript, das ausgeführt wird, indem eine Zeichenfolge übergeben, die `setTimeout`, `setImmediate`, oder `setInterval` Funktionen als klassifiziert **UnrelatedCode**.  
  
-   `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` legt anderen Benutzer- und Nichtbenutzercode für alle Visual Studio-JavaScript-Projekte fest.  
  
 Sie können die Standardklassifizierungen ändern und bestimmte Dateien und URLs klassifizieren, indem Sie dem Stammordner eines Projekts eine JSON-Datei mit dem Namen `mycode.json` hinzufügen.  
  
 Alle anderen Code als klassifiziert **MyCode**.  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> Schrittverhalten  
  
-   Wenn eine Funktion nicht Benutzer ist (**MyCode**) Code **Einzelschritt** (Tastenkombination: F11) verhält sich wie **Prozedurschritt** (Tastatur: F10).  
  
-   Wenn ein Schritt im Nichtbenutzercode beginnt (**LibraryCode** oder **UnrelatedCode**) code, und klicken Sie dann die schrittweise Ausführung kurzfristig verhält, als wenn nur mein Code nicht aktiviert ist. Wenn Sie wechseln zurück zum Benutzercode, nur mein Code schrittweise wieder aktiviert ist.  
  
-   Wenn ein Schritt im Benutzercode dazu führt, dass der aktuelle Ausführungskontext (wie etwa das Durchführen eines Schritts in der letzten Zeile eines Ereignishandlers) verlassen wird, hält der Debugger bei der nächsten ausgeführten Benutzercodezeile an. Wenn in ein Rückruf ausgeführt wird z. B. **LibraryCode** Code, die der Debugger wird fortgesetzt, bis die nächste Zeile des Benutzercodes ausführt.
  
-   **Ausführen bis Rücksprung** (Tastatur: UMSCHALT + F11) hält in der nächsten Zeile des Benutzercodes. Wenn kein Benutzercode festgestellt wird, wird die Ausführung wird, bis die app fortgeführt beendet wird, ein Haltepunkt erreicht wird, oder eine Ausnahme auftritt.  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> Haltepunktverhalten  
  
-   Legen Sie im Code Haltepunkte werden unabhängig von der Klassifizierung dieses Codes immer erreicht  
  
-   Wenn das `debugger`-Schlüsselwort gefunden wird in:  
  
    -   **LibraryCode** Code, unterbricht der Debugger immer.  
  
    -   **UnrelatedCode** Code, den Debugger nicht beenden.  
  
###  <a name="BKMK_JS_Exception_behavior"></a> Ausnahmeverhalten  
 Wenn ein Ausnahmefehler auftritt in:  
  
-   **MyCode** oder **LibraryCode** Code, unterbricht der Debugger immer.  
  
-   **UnrelatedCode** Code und **MyCode** oder **LibraryCode** Code befindet sich in der Aufrufliste befindet, unterbricht der Debugger.  
  
 Wenn Ausnahmen der ersten Chance für die Ausnahme im Dialogfeld "Ausnahmen" aktiviert sind, und die Ausnahme, in ausgelöst wird **LibraryCode** oder **UnrelatedCode** Code:  
  
-   Wenn die Ausnahme behandelt wird, unterbrochen nicht der Debugger.  
  
-   Wenn die Ausnahme nicht behandelt wird, unterbricht der Debugger.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Nur mein Code anpassen  
 Um Benutzer- und Nichtbenutzercode für ein einzelnes Visual Studio-Projekt zu kategorisieren, fügen Sie dem Stammordner des Projekts eine JSON-Datei mit dem Namen `mycode.json` hinzu.  
  
 Klassifizierungen werden in dieser Reihenfolge ausgeführt:  
  
1.  Standardklassifizierungen  
  
2.  Klassifizierungen in der `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Datei  
  
3.  Klassifizierungen in der Datei `mycode. json` des aktuellen Projekts  
  
 Jeder Klassifizierungsschritt überschreibt die vorherigen Schritte. Eine JSON-Datei muss nicht alle Schlüsselwertpaare auflisten und die **MyCode**, **Bibliotheken**, und **Unrelated** Werte können leere Arrays sein.  
  
 JSON-Dateien für eigenen Code verwenden folgende Syntax:  
  
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
  
 Die **Eval**, **Funktion**, und **"scriptblock"** Schlüssel-/Wertpaaren bestimmen, wie dynamisch erzeugter Code klassifiziert wird.  
  
|||  
|-|-|  
|**Eval**|Skript, das ausgeführt wird, indem eine Zeichenfolge an die vom Host bereitgestellte `eval`-Funktion übergeben wird. Eval-Skript wird standardmäßig als klassifiziert **MyCode**.|  
|**Function**|Skript, das ausgeführt wird, indem eine Zeichenfolge an den `Function`-Konstruktor übergeben wird. Function-Skript wird standardmäßig als klassifiziert **LibraryCode**.|  
|**"Scriptblock"**|Skript, das ausgeführt wird, indem eine Zeichenfolge an die Funktionen `setTimeout`, `setImmediate` oder `setInterval` übergeben wird. ScriptBlock-Skript wird standardmäßig als klassifiziert **UnrelatedCode**.|  
  
 Sie können den Wert auf eines dieser Schlüsselwörter ändern:  
  
-   `MyCode`  klassifiziert das Skript als **MyCode**.  
  
-   `Library`  klassifiziert das Skript als **LibraryCode**.  
  
-   `Unrelated`  klassifiziert das Skript als **UnrelatedCode**.  
  
 **MyCode, Libraries und Unrelated**  
  
 Die **MyCode**, **Bibliotheken**, und **Unrelated** Schlüssel-Wert-Paare angeben, die Urls oder Dateien, die Sie in eine Klassifikation einschließen möchten:  
  
|||  
|-|-|  
|**MyCode**|Ein Array von Urls oder Dateien, die als klassifiziert werden **MyCode**.|  
|**Bibliotheken**|Ein Array von Urls oder Dateien, die als klassifiziert werden **LibraryCode**.|  
|**Unabhängig vom stagingstatus**|Ein Array von Urls oder Dateien, die als klassifiziert werden **UnrelatedCode**.|  
  
 Die URL-Zeichenfolge oder Dateizeichenfolge kann eine oder mehrere `*`-Zeichen enthalten, die mit null oder mehr Zeichen übereinstimmen. `*` entspricht dem regulären Ausdruck `.*`.
