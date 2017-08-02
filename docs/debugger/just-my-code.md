---
title: "Nur mein Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Nur mein Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Entwickler, die .NET Framework\-Sprachen verwenden, sind mit der Debuggerfunktion "Nur eigenen Code" vertraut, die System\-, Framework\- und andere Nichtbenutzeraufrufe überspringt und diese Aufrufe in den Aufruflistenfenstern reduziert.  „Nur eigener Code“ wurde die C\+\+\- und JavaScript\-Sprachen erweitert.  In diesem Thema werden die Einzelheiten der Verwendung von "Nur eigenen Code" in .NET Framework\-, in systemeigenen C\+\+\- und in JavaScript\-Projekten beschrieben.  
  
##  <a name="BKMK_Contents"></a> Inhalt  
 [Aktivieren oder Deaktivieren von "Nur eigenen Code"](#BKMK_Enable_or_disable_Just_My_Code)  
  
 ["Nur eigenen Code" in .NET Framework](#BKMK__NET_Framework_Just_My_Code)  
  
 ["Nur eigenen Code" in C++](#BKMK_C___Just_My_Code)  
  
 ["Nur eigenen Code" in JavaScript](#BKMK_JavaScript_Just_My_Code)  
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Aktivieren oder Deaktivieren von "Nur eigenen Code"  
 Zum Aktivieren oder Deaktivieren von "Nur eigenen Code" wählen Sie im Menü **Optionen und Einstellungen** die Option **Debuggen** aus.  Aktivieren oder deaktivieren Sie im Knoten **Debugging**\/**Allgemein** das Kontrollkästchen **Nur meinen Code aktivieren**.  
  
 ![Option zum Aktivieren nur des eigenen Codes im Dialogfeld "Optionen"](../debugger/media/dbg_justmycode_options.png "DBG\_JustMyCode\_Options")  
  
> [!NOTE]
>  Die Einstellung **Nur meinen Code aktivieren** ist eine globale Einstellung, die auf alle Visual Studio\-Projekte in allen Sprachen angewendet wird.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> Überschreiben der Aufruflistenfilterung  
 In den Aufruflistenanzeigen wie den Fenstern "Aufrufliste" und "Aufgaben" reduziert "Nur eigenen Code" den Nichtbenutzercode in einen mit Anmerkungen versehenen Frame mit der Bezeichnung `[External Code]`.  Um die reduzierten Frames anzuzeigen, wählen Sie im Kontextmenü der Aufruflistenanzeige **Externen Code anzeigen** aus.  
  
> [!NOTE]
>  Die Einstellung **Externen Code anzeigen** wird im Profiler des aktuellen Benutzers gespeichert.  Sie wird auf alle Projekte in allen Sprachen angewendet, die von dem Benutzer geöffnet werden.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> "Nur eigenen Code" in .NET Framework  
 [Benutzer- und Nichtbenutzercode](#BKMK_NET_User_and_non_user_code) **&#124;** [Schrittverhalten](#BKMK_NET_Stepping_behavior) **&#124;** [Haltepunktverhalten](#BKMK_NET_Breakpoint_behavior) **&#124;** [Ausnahmeverhalten](#BKMK_NET_Exception_behavior)  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> Benutzer\- und Nichtbenutzercode  
 Die Option "Nur eigenen Code" untersucht offene Projekte, Symboldateien \(PDB\-Dateien\) und Programmoptimierungen, um Benutzercode von Nichtbenutzercode zu unterscheiden.  
  
1.  Wenn eine Binärdatei aus einem geöffneten Visual Studio\-Projekt erstellt wurde, wird sie immer als Benutzercode angesehen.  
  
2.  Der Debugger behandelt Code als Nichtbenutzercode, wenn die Binärdatei optimiert oder die PDB\-Datei nicht verfügbar ist.  
  
 Drei Attribute beeinflussen außerdem, was der Debugger als eigenen Code ansieht:  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> teilt dem Debugger mit, dass der Code, auf den er angewendet wird, kein eigener Code ist.  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> blendet den Code für den Debugger aus, auch wenn Nur mein Code deaktiviert wird.  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute> veranlasst den Debugger, den vorliegenden Code nicht in Einzelschritten, sondern in Prozedurschritten zu durchlaufen.  
  
 Der übrige Code wird als Benutzercode angesehen.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in .NET Framework](#BKMK__NET_Framework_Just_My_Code)  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> Schrittverhalten  
 Wenn Sie **Einzelschritt** \(Tastenkombination: F11\) auf Nichtbenutzercode anwenden, überspringt der Debugger den Code bis zur nächsten Benutzeranweisung.  Wenn Sie **Ausführen bis Rücksprung** \(Tastenkombination: UMSCHALT\+F11\) verwenden, wird der Debugger bis zur nächsten Zeile des Benutzercodes ausgeführt.  Wenn kein Benutzercode gefunden wird, läuft die Ausführung weiter, bis die App beendet wird, ein Haltepunkt erreicht wird oder eine Ausnahme auftritt.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in .NET Framework](#BKMK__NET_Framework_Just_My_Code)  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> Haltepunktverhalten  
 Wenn "Nur eigenen Code" aktiviert ist, können Sie **Alle unterbrechen** \(Tastenkombination: STRG\+Alt\+UNTBR\) auswählen und die Ausführung an einer Stelle anhalten, an der kein Benutzercode vorhanden ist.  Wenn dies geschieht, wird das Fenster "Kein Quellcode" angezeigt.  Wenn Sie anschließend einen Schrittbefehl auswählen, wechselt der Debugger zur nächsten Zeile von Benutzercode.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in .NET Framework](#BKMK__NET_Framework_Just_My_Code)  
  
###  <a name="BKMK_NET_Exception_behavior"></a> Ausnahmeverhalten  
 Wenn ein Ausnahmefehler im Nichtbenutzercode auftritt, unterbricht der Debugger an der Zeile im Benutzercode, in der die Ausnahme generiert wurde.  
  
 Wenn Ausnahmen \(erste Chance\) für die Ausnahme aktiviert sind, wird die Benutzercodezeile grün hervorgehoben.  Die Aufrufliste zeigt einen mit Anmerkungen versehenen Frame mit der Bezeichnung **\[Externer Code\]** an.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in .NET Framework](#BKMK__NET_Framework_Just_My_Code)  
  
##  <a name="BKMK_C___Just_My_Code"></a> "Nur eigenen Code" in C\+\+  
 [Benutzer- und Nichtbenutzercode](#BKMK_CPP_User_and_non_user_code) **&#124;** [Schrittverhalten](#BKMK_CPP_Stepping_behavior) **&#124;** [Ausnahmeverhalten](#BKMK_CPP_Exception_behavior) **&#124;** [Anpassen des Schrittverhaltens](#BKMK_CPP_Customize_stepping_behavior) **&#124;** [Anpassen des Aufruflistenverhaltens](#BKMK_CPP_Customize_call_stack_behavior)  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> Benutzer\- und Nichtbenutzercode  
 "Nur eigenen Code" in C\+\+ ist anders als "Nur eigenen Code" in .NET Framework und JavaScript, da das Schrittverhalten vom Aufruflistenverhalten unabhängig ist.  
  
 **Aufruflisten**  
  
 Standardmäßig behandelt der Debugger diese Funktionen als Nichtbenutzercode in Aufruflistenfenstern:  
  
-   Funktionen mit entfernten Quellinformationen in ihrer Symboldatei.  
  
-   Funktionen, bei denen die Symboldateien angeben, dass keine Quelldatei vorhanden ist, die dem Stapelrahmen entspricht.  
  
-   Die Funktionen sind in den `*.natjmc`\-Dateien im Ordner `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` definiert.  
  
 **Schrittweises Ausführen**  
  
 Standardmäßig werden nur Funktionen, die in `*.natstepfilter`\-Dateien im `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`\-Ordner festgelegt sind, als Nichhtbenutzercode angesehen.  
  
 Sie können Ihre eigenen `.natstepfilter` und `.natjmc` erstellen, um das Schrittverhalten und das Verhalten der Aufruflistenfenster in `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` anzupassen.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in C++](#BKMK_C___Just_My_Code)  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> Schrittverhalten  
 Wenn Sie **Einzelschritt** \(Tastenkombination: F11\-\) für Nichtbenutzercode aus Benutzercode verwenden, überspringt der Debugger den Code bis zur nächsten Benutzercodezeile.  Wenn Sie **Ausführen bis Rücksprung** \(Tastenkombination: UMSCHALT\+F11\) verwenden, wird der Debugger bis zur nächsten Zeile des Benutzercodes ausgeführt.  Wenn kein Benutzercode gefunden wird, läuft die Ausführung weiter, bis die App beendet wird, ein Haltepunkt erreicht wird oder eine Ausnahme auftritt.  
  
 Wenn der Debugger beim Nichtbenutzercode unterbricht \(zum Beispiel, wenn ein Befehl "Alle unterbrechen" in Nichtbenutzercode anhält\), wird die schrittweise Ausführung im Nichtbenutzercode weitergeführt.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in C++](#BKMK_C___Just_My_Code)  
  
###  <a name="BKMK_CPP_Exception_behavior"></a> Ausnahmeverhalten  
 Wenn der Debugger auf eine Ausnahme trifft, hält er bei der Ausnahme an, unabhängig davon, ob sie im Benutzer\- oder Nichtbenutzercode auftritt.  Die Optionen **Vom Benutzercode unbehandelt** im Dialogfeld **Ausnahmen** werden ignoriert.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in C++](#BKMK_C___Just_My_Code)  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Anpassen des Schrittverhaltens  
 Sie können Funktionen angeben, die zu überspringen sind, indem Sie sie als Nichtbenutzercode in `*.natstepfilter`\-Dateien auflisten.  
  
-   Um Nichtbenutzercode für alle Benutzer des Visual Studio\-Computers anzugeben, fügen Sie die  Natstepfilter\-Datei dem `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers`\-Ordner hinzu.  
  
-   Um Nichtbenutzercode für einen einzelnen Benutzer anzugeben, fügen die  Natstepfilter\-Datei dem `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`\-Ordner hinzu.  
  
 .  Natsetepfilter\-Dateien sind XML\-Dateien mit folgender Syntax:  
  
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
|-------------|------------------|  
|Funktion|Erforderlich.  Gibt eine oder mehreren Funktionen als Nichtbenutzerfunktionen an.|  
|`Name`|Erforderlich.  Ein ECMA\-262\-formatierter regulärer Ausdruck, der den vollständigen Funktionsnamen angibt, der übereinstimmen muss.  Zum Beispiel:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> teilt dem Debugger mit, dass alle Methoden in `MyNS::MyClass` als Nichtbenutzercode behandelt werden sollen.  Bei der Übereinstimmung muss die Groß\-\/Kleinschreibung beachtet werden.|  
|`Module`|Dies ist optional.  Ein ECMA\-262\-formatierter regulärer Ausdruck, der den vollständigen Pfad zu dem Modul angibt, das die Funktion enthält.  Die Groß\- und Kleinschreibung wird bei der Übereinstimmung nicht berücksichtigt.|  
|`Action`|Erforderlich.  Einer dieser Werte, bei denen die Groß\-\/Kleinschreibung beachtet werden muss.<br /><br /> -   `NoStepInto` : Weist den Debugger an, die übereinstimmende Funktion zu überspringen.<br />-   `StepInto` : Weist den Debugger an, die übereinstimmenden Funktionen schrittweise auszuführen, wobei alle anderen `NoStepInto` für die übereinstimmenden Funktionen überschrieben werden.|  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in C++](#BKMK_C___Just_My_Code)  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Anpassen des Aufruflistenverhaltens  
 Sie können Module, Quelldateien und Funktionen angeben, die als Nichtbenutzercode in Aufruflisten behandelt werden, indem sie in `*.natjmc`\-Dateien angegeben werden.  
  
-   Um Nichtbenutzercode für alle Benutzer des Visual Studio\-Computers anzugeben, fügen Sie die  NATJMC\-Datei in den `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` Ordner.  
  
-   Um Nichtbenutzercode für einen einzelnen Benutzer anzugeben, fügen die  NATJMC\-Datei in den `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` Ordner.  
  
 .  NATJMC\-Dateien sind XML\-Dateien mit folgender Syntax:  
  
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
|--------------|------------------|  
|`Name`|Erforderlich.  Der vollständige Pfad des Moduls oder der Module.  Sie können die Windows\-Platzhalterzeichen `?` \(null oder ein Zeichen\) und `*` \(null oder mehr Zeichen\) verwenden.  Beispiel:<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> weist den Debugger an, alle Module in `\3rdParty\UtilLibs` auf einem Laufwerk als externen Code zu behandeln.|  
|`Company`|Dies ist optional.  Der Name des Unternehmens, das das Modul veröffentlicht, das in die ausführbare Datei eingebettet ist.  Sie können dieses Attribut verwenden, um die Module zu unterscheiden.|  
  
 **Dateielementattribute**  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Name`|Erforderlich.  Der vollständige Pfad der Quelldatei oder \-dateien, die als externer Code behandelt werden sollen.  Sie können die Windows\-Platzhalterzeichen `?` und `*` verwenden, wenn Sie den Pfad angeben.|  
  
 **Funktionselementattribute**  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Name`|Erforderlich.  Der vollqualifizierte Name der Funktion, die als externer Code behandelt werden soll.|  
|`Module`|Dies ist optional.  Der Name oder der vollständige Pfad zu dem Modul, das die Funktion enthält.  Sie können dieses Attribut verwenden, um Funktionen mit demselben Namen zu unterscheiden.|  
|`ExceptionImplementation`|Bei Festlegung auf `true` zeigt die Aufrufliste die Funktion an, die die Ausnahme und nicht diese Funktion ausgelöst hat.|  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in C++](#BKMK_C___Just_My_Code)  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> "Nur eigenen Code" in JavaScript  
 [Benutzer- und Nichtbenutzercode](#BKMK_JS_User_and_non_user_code) **&#124;** [Schrittverhalten](#BKMK_JS_Stepping_behavior) **&#124;** [Haltepunktverhalten](#BKMK_JS_Breakpoint_behavior) **&#124;** [Ausnahmeverhalten](#BKMK_JS_Exception_behavior) **&#124;** [Anpassen von "Nur eigenen Code"](#BKMK_JS_Customize_Just_My_Code)  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> Benutzer\- und Nichtbenutzercode  
 **Codeklassifizierungen**  
  
 "Nur eigenen Code" in JavaScript steuert die schrittweise Ausführung und die Aufruflistenanzeige durch Kategorisieren von Code in einer dieser Klassifizierungen:  
  
|||  
|-|-|  
|**MyCode**|Benutzercode, den Sie besitzen und steuern.|  
|**LibraryCode**|Nichtbenutzercode aus Bibliotheken, den Sie regelmäßig verwenden und die für das ordnungsgemäße Funktionieren Ihrer Anwendung erforderlich sind \(z. B. WinJS oder jQuery\).|  
|**UnrelatedCode**|Nichtbenutzercode, der in Ihrer Anwendung ausgeführt werden könnte, den Sie jedoch nicht besitzen und der für das ordnungsgemäße Funktionieren Ihrer Anwendung nicht direkt erforderlich ist \(z. B. ein Werbungs\-SDK, das Anzeigen anzeigt\).  In Windows Store\-Projekten gilt jeder Code, der von einem HTTP\- oder HTTPS\-URI in Ihre App geladen wird, als UnrelatedCode.|  
  
 Der JavaScript\-Debugger klassifiziert automatisch diese Codetypen:  
  
-   Skript, das ausgeführt wird, indem eine Zeichenfolge an die vom Host bereitgestellte `eval`\-Funktion übergeben wird, wird als **MyCode** klassifiziert.  
  
-   Skript, das ausgeführt wird, indem eine Zeichenfolge an den `Function`\-Konstruktor übergeben wird, wird als **LibraryCode** klassifiziert.  
  
-   Skript, das in einem Frameworkverweis, wie etwa WinJS oder dem Azure\-SDK, enthalten ist, wird als **LibraryCode** klassifiziert.  
  
-   Skript, das ausgeführt wird, indem eine Zeichenfolge an die Funktionen `setTimeout`, `setImmediate` oder `setInterval` übergeben wird, wird als **UnrelatedCode** klassifiziert.  
  
-   `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` legt anderen Benutzer\- und Nichtbenutzercode für alle Visual Studio\-JavaScript\-Projekte fest.  
  
 Sie können die Standardklassifizierungen ändern und bestimmte Dateien und URLs klassifizieren, indem Sie dem Stammordner eines Projekts eine JSON\-Datei mit dem Namen `mycode.json` hinzufügen.  
  
 Der restliche Code wird als **MyCode** klassifiziert.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in JavaScript](#BKMK_JavaScript_Just_My_Code)  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> Schrittverhalten  
  
-   Wenn eine Funktion nicht Benutzercode \(**MyCode**\) ist, verhält sich **Einzelschritt** \(Tastenkombination: F11\) wie **Prozedurschritt** \(Tastenkombination: F10\).  
  
-   Wenn ein Schritt im Nichtbenutzercode \(**LibraryCode** oder **UnrelatedCode**\) beginnt, dann verhält sich die schrittweise Ausführung kurzfristig so, als wäre "Nur eigenen Code" nicht aktiviert.  Sobald Sie zurück zum Benutzercode wechseln, wird die schrittweise Ausführung für "Nur eigenen Code" erneut aktiviert.  
  
-   Wenn ein Schritt im Benutzercode dazu führt, dass der aktuelle Ausführungskontext \(wie etwa das Durchführen eines Schritts in der letzten Zeile eines Ereignishandlers\) verlassen wird, hält der Debugger bei der nächsten ausgeführten Benutzercodezeile an.  Wenn beispielsweise ein Rückruf in **LibraryCode**\-Code ausgeführt wird, fährt der Debugger fort, bis die nächste Zeile des Benutzercodes ausgeführt wird.  
  
-   **Ausführen bis Rücksprung** \(Tastenkombination: UMSCHALT\+F11\) hält in der nächsten Zeile des Benutzercodes an.  Wenn kein Benutzercode gefunden wird, läuft die Ausführung weiter, bis die App beendet wird, ein Haltepunkt erreicht wird oder eine Ausnahme auftritt.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in JavaScript](#BKMK_JavaScript_Just_My_Code)  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> Haltepunktverhalten  
  
-   Haltepunkte, die im Code festgelegt wurden, werden immer erreicht, unabhängig von der Klassifizierung dieses Codes.  
  
-   Wenn das `debugger`\-Schlüsselwort gefunden wird in:  
  
    -   **LibraryCode**\-Code, unterbricht der Debugger immer.  
  
    -   **UnrelatedCode**\-Code, beendet der Debugger die Aktion nicht.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in JavaScript](#BKMK_JavaScript_Just_My_Code)  
  
###  <a name="BKMK_JS_Exception_behavior"></a> Ausnahmeverhalten  
 Wenn ein Ausnahmefehler auftritt in:  
  
-   **MyCode**\- oder **LibraryCode**\-Code, unterbricht der Debugger immer.  
  
-   **UnrelatedCode**\-Code, und **MyCode**\- oder **LibraryCode**\-Code sich in der Aufrufliste befindet, unterbricht der Debugger.  
  
 Wenn Ausnahmen \(erste Chance\) für die Ausnahme im Dialogfeld "Ausnahmen" aktiviert sind und die Ausnahme in **LibraryCode**\- oder **UnrelatedCode**\-Code ausgelöst wird:  
  
-   Wenn die Ausnahme behandelt wird, unterbricht der Debugger nicht.  
  
-   Wenn die Ausnahme nicht behandelt wird, unterbricht der Debugger.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in JavaScript](#BKMK_JavaScript_Just_My_Code)  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Anpassen von "Nur eigenen Code"  
 Um Benutzer\- und Nichtbenutzercode für ein einzelnes Visual Studio\-Projekt zu kategorisieren, fügen Sie dem Stammordner des Projekts eine JSON\-Datei mit dem Namen `mycode.json` hinzu.  
  
 Klassifizierungen werden in dieser Reihenfolge ausgeführt:  
  
1.  Standardklassifizierungen  
  
2.  Klassifizierungen in der `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Datei  
  
3.  Klassifizierungen in der Datei `mycode. json` des aktuellen Projekts  
  
 Jeder Klassifizierungsschritt überschreibt die vorherigen Schritte.  Eine JSON\-Datei muss nicht alle Schlüsselwertpaare auflisten, und die Werte **MyCode**, **Libraries** und **Unrelated** können leere Arrays sein.  
  
 JSON\-Dateien für eigenen Code verwenden folgende Syntax:  
  
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
  
 Die Schlüsselwertpaare **Eval**, **Function** und **ScriptBlock** bestimmen, wie dynamisch erzeugter Code klassifiziert wird.  
  
|||  
|-|-|  
|**Eval**|Skript, das ausgeführt wird, indem eine Zeichenfolge an die vom Host bereitgestellte `eval`\-Funktion übergeben wird.  Standardmäßig wird ein Eval\-Skript als **MyCode** klassifiziert.|  
|**Funktion**|Skript, das ausgeführt wird, indem eine Zeichenfolge an den `Function`\-Konstruktor übergeben wird.  Standardmäßig wird ein Function\-Skript als **LibraryCode** klassifiziert.|  
|**ScriptBlock**|Skript, das ausgeführt wird, indem eine Zeichenfolge an die Funktionen `setTimeout`, `setImmediate` oder `setInterval` übergeben wird.  Standardmäßig wird ein ScriptBlock\-Skript als **UnrelatedCode** klassifiziert.|  
  
 Sie können den Wert auf eines dieser Schlüsselwörter ändern:  
  
-   `MyCode`  klassifiziert das Skript als **MyCode**.  
  
-   `Library`  klassifiziert das Skript als **LibraryCode**.  
  
-   `Unrelated`  klassifiziert das Skript als **UnrelatedCode**.  
  
 **MyCode, Libraries und Unrelated**  
  
 Die Schlüsselwertpaare **MyCode**, **Libraries** und **Unrelated** geben die URLs oder Dateien an, die Sie in eine Klassifikation einschließen möchten:  
  
|||  
|-|-|  
|**MyCode**|Ein Array von URLs oder Dateien, die als **MyCode** klassifiziert werden.|  
|**Bibliothekar**|Ein Array von URLs oder Dateien, die als **LibraryCode** klassifiziert werden.|  
|**Unrelated**|Ein Array von URLs oder Dateien, die als **UnrelatedCode** klassifiziert werden.|  
  
 Die URL\-Zeichenfolge oder Dateizeichenfolge kann eine oder mehrere `*`\-Zeichen enthalten, die mit null oder mehr Zeichen übereinstimmen.  `*` entspricht dem regulären Ausdruck `.*`.  
  
 ![Zurück nach oben](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents) **&#124;** ["Nur eigenen Code" in JavaScript](#BKMK_JavaScript_Just_My_Code)