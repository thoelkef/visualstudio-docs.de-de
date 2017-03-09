---
title: "Optionsseite, Eigenschaften des Knotens „Debuggen“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 7f9daff5a0f196a4cebdd41a91f67bd37815b121
ms.lasthandoff: 02/22/2017

---
# <a name="options-page-debugging-node-properties"></a>Optionsseite, Eigenschaften des Knotens 'Debuggen'
In den folgenden Tabellen werden die Seiten (bzw. Eigenschaftenauflistungen) beschrieben, die der Kategorie **Debugging** `DTE.Properties("Debugging", <Property Page>)` im Dialogfeld **Optionen** zugeordnet sind.  
  
## <a name="general"></a>Allgemein  
 `DTE.Properties("Debugging", "General")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|PromptOnBreakpointDelete|Get/Set (boolesch)|Bestimmt, ob der Debugger vor dem Löschen aller Haltepunkte in einem Projekt zur Bestätigung auffordert.|  
|BreakAllProcesses|Get/Set (boolesch)|Bestimmt, ob der Debugger alle Prozesse unterbricht, sobald ein einzelner Prozess unterbrochen wird.|  
|BreakAtBoundaries|Get/Set (boolesch)|Bestimmt, ob der Debugger die Ausführung unterbricht, wenn eine Ausnahme eine Grenze zwischen AppDomains oder zwischen verwaltetem und systemeigenem Code überschreitet.|  
|EnableAddressLevelDebugging|Get/Set (boolesch)|Bestimmt, ob Debugfeatures auf Adressebene aktiviert werden.|  
|ShowDisassemblyIfNoSource|Get/Set (boolesch)|Bestimmt, ob der Debugger Disassemblycode anzeigt, wenn Quellcode nicht verfügbar ist.|  
|EnableBreakpointFilters|Get/Set (boolesch)|Bestimmt, ob die Haltepunktfilterung aktiviert ist.|  
|EnableExceptionAssistant|Get/Set (boolesch)|Bestimmt, ob der Ausnahmen-Assistent für verwaltete Ausnahmen verwendet wird.|  
|UnwindCallstack|Get/Set (boolesch)|Bestimmt, ob der Debugger die Aufrufliste für eine nicht behandelte Ausnahme entlädt.|  
|EnableJustMyCode|Get/Set (boolesch)|Bestimmt, ob "Nur mein Code" für C#- und Visual Basic-Code aktiviert ist.|  
|ShowAllMembers|Get/Set (boolesch)|Bestimmt für Nichtbenutzerobjekte, ob der Debugger alle Objektmember in den Variablenfenstern anzeigt. Diese Option ist nur wirksam, wenn "Nur mein Code" aktiviert ist.|  
|WarnIfNoUserCode|Get/Set (boolesch)|Bestimmt, ob der Debugger eine Warnung ausgibt, wenn der Benutzer eine Verbindung mit einem Prozess herzustellen versucht, der keinen Benutzercode enthält. Diese Option ist nur wirksam, wenn "Nur mein Code" aktiviert ist.|  
|EnablePropertyEvaluation|Get/Set (boolesch)|Bestimmt, ob der Debugger Eigenschaften und implizite Funktionsaufrufe in verwaltetem Code automatisch auswertet.|  
|CallStringConversion|Get/Set (boolesch)|Bestimmt, ob der Debugger in den Variablenfenstern eine Zeichenfolgenkonvertierungsfunktion für Objekte implizit aufruft. Diese Option gilt nur für C#- und JScript-Code.|  
|EnableSourceServer|Get/Set (boolesch)|Bestimmt, ob der Debugger auf Code von einem Quellserver zugreifen kann.|  
|PrintSourceServerDiagnostics|Get/Set (boolesch)|Bestimmt, ob das Ausgabefenster Diagnosemeldungen über den Quellserver anzeigt. Diese Option nur wirksam, wenn der Zugriff auf den Quellserver aktiviert ist.|  
|HighlightEntireLine|Get/Set (boolesch)|Bestimmt, ob der Debugger eine ganze Zeile für Haltepunkte und die aktuelle Anweisung hervorhebt.|  
|RequireSourceToMatch|Get/Set (boolesch)|Bestimmt, ob der Debugger verlangt, dass Quelldateien genau mit der Originalversion übereinstimmen müssen, wenn Sie Dateien zum Debuggen öffnen.|  
|RedirectOutputToImmediate|Get/Set (boolesch)|Bestimmt, ob die Ausgabe des Ausgabefensters zum Direktfenster umgeleitet wird.|  
|ShowRawVariableStructure|Get/Set (boolesch)|Bestimmt, ob Objekte in den Variablenfenstern in unformatierter Form angezeigt werden.|  
|SuppressJitOptimization|Get/Set (boolesch)|Bestimmt bei verwaltetem Code, ob Just-In-Time-Optimierung vom Debugger unterdrückt wird.|  
|WarnIfNoSymbols|Get/Set (boolesch)|Bestimmt, ob der Debugger eine Warnung anzeigt, wenn beim Starten eines Prozesses keine Debugsymbole verfügbar sind.|  
|WarnIfScriptDisabled|Get/Set (boolesch)|Bestimmt, ob der Debugger eine Warnung anzeigt, wenn beim Starten eines Prozesses das Skriptdebuggen nicht aktiviert ist.|  
|ShowMarkersForAllThreads|Get/Set (boolesch)|Bestimmt, ob der Debugger Threadmarker anzeigt.|  
|StepOverPropertiesAndOperators|Get/Set (boolesch)|Gibt an, ob Eigenschaften und Operatoren übersprungen werden (nur in verwaltetem Code).|  
  
## <a name="edit-and-continue"></a>Bearbeiten und Fortfahren  
 `DTE.Properties("Debugging", "EditAndContinue")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|EnableEditAndContinue|Get/Set (boolesch)|Bestimmt, ob Bearbeiten und Fortfahren aktiviert ist. Diese Option gilt für alle Sprachen, die Bearbeiten und Fortfahren unterstützen.|  
|InvokedByCommands|Get/Set (boolesch)|Bestimmt, ob beim Bearbeiten und Fortfahren Codeänderungen automatisch angewendet werden, wenn der Benutzer einen Debugbefehl wie **Schritt** oder **Fortfahren** auswählt. Diese Option gilt nur für nativen Code.|  
|InvokedByCommandsAskFirst|Get/Set (boolesch)|Bestimmt, ob der Benutzer beim Bearbeiten und Fortfahren zur Bestätigung von Codeänderungen aufgefordert wird, wenn der Benutzer einen Debugbefehl wie **Schritt** oder **Fortfahren** auswählt. Diese Option gilt nur für nativen Code.|  
|WarnAboutStaleCode|Get/Set (boolesch)|Bestimmt, ob der Debugger eine Warnung ausgibt, wenn das Bearbeiten und Fortfahren zur Ausführung von veraltetem Code führen würde. Diese Option gilt nur für systemeigenen Code.|  
|RelinkChangesOnStop|Get/Set (kurzer Name)|Bestimmt, ob Visual Studio Codeänderungen, die mit Bearbeiten und Fortfahren angewendet wurden, erneut bindet, wenn die Ausführung der Anwendung unterbrochen wird. Diese Option gilt nur für systemeigenen Code.|  
|AllowPrecompiling|Get/Set (kurzer Name)|Bestimmt, ob beim Bearbeiten und Fortfahren vorkompilierte Header im Hintergrund geladen werden können. Diese Option gilt nur für systemeigenen Code.|  
  
## <a name="just-in-time"></a>Just-In-Time  
 `DTE.Properties("Debugging", "JustInTime")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|JitManaged|Get/Set (boolesch)|Bestimmt, ob Just-In-Time-Debuggen für verwalteten Code aktiviert ist.|  
|JitNative|Get/Set (boolesch)|Bestimmt, ob Just-In-Time-Debuggen für systemeigenen Code aktiviert ist.|  
|JitScript|Get/Set (boolesch)|Bestimmt, ob Just-In-Time-Debuggen für Skriptcode aktiviert ist.|  
  
## <a name="native"></a>Systemeigen  
 `DTE.Properties("Debugging", "Native")`  
  
|Eigenschaftenelementname|Wert|Beschreibung|  
|------------------------|-----------|-----------------|  
|LoadDllExports|Get/Set (boolesch)|Bestimmt, ob der Debugger DLL-Exporttabellen lädt.|  
|EnableRPC|Get/Set (boolesch)|Bestimmt, ob der Debugger COM-Remoteprozeduraufrufe schrittweise ausführen kann.|  
  
## <a name="see-also"></a>Siehe auch  
 [Steuern der Einstellungen im Dialogfeld „Optionen“ (Menü „Extras“)](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Bestimmen der Namen von Eigenschaftenelementen auf Optionsseiten](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Optionsseite, Eigenschaften des Knotens „Schriftarten und Farben“](../../ide/reference/options-page-fonts-and-colors-node-properties.md)   
 [Optionsseite, Eigenschaften des Knotens „Text-Editor“](../../ide/reference/options-page-text-editor-node-properties.md)   
 [Allgemein, Debuggen, Dialogfeld „Optionen“](../../debugger/general-debugging-options-dialog-box.md)   
 [Bearbeiten und Fortfahren, Debuggen, Dialogfeld „Optionen“](http://msdn.microsoft.com/Library/009d225f-ef65-463f-a146-e4c518f86103)   
 [Just-In-Time, Debuggen, Dialogfeld "Optionen"](../../debugger/just-in-time-debugging-options-dialog-box.md)
