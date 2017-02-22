---
title: "SDK-Hilfsprogramme f&#252;r das Debuggen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dbgmetric.lib"
  - "Debugging-SDK-Registrierung"
  - "Debuggen-SDK, Registrierung"
  - "dbgmetric.h"
  - "Metriken [SDK-Debuggen]"
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# SDK-Hilfsprogramme f&#252;r das Debuggen
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Funktionen und Deklarationen sind globale Hilfsfunktionen zum Implementieren von Debuggen von Modulen, Ausdrucksauswertern und Symbol anbietern in C\+\+.  
  
> [!NOTE]
>  Es gibt keine verwalteten Versionen dieser Funktionen und \- Deklarationen zur Zeit.  
  
## Übersicht  
 Für Module, Debugsymbolinformationen für Symbole und Ausdrucksauswertung von Visual Studio verwendet werden können, müssen sie registriert werden.  Dies geschieht, indem Registrierungsunterschlüssel und Einträge festlegt, andernfalls wird auch als „Einstellungen“. metrik Die folgenden globalen Funktionen sind für den Prozess der Aktualisierung dieser Metriken zu erleichtern.  Weitere Informationen finden Sie im Abschnitt über Registrierungs\-Speicherorten, um das Lay\-out der einzelnen Registrierungsunterschlüssels herausfinden, der von dieser Funktionen aktualisiert wird.  
  
## Allgemeine metrische Funktionen  
 Dies sind die allgemeinen Funktionen, die von Debugsymbolinformationen auf Module verwendet werden.  Spezialisierte Features für die Ausdrucksauswertung Anbieter Symbol und höher werden einzeln aufgelistet.  
  
### GetMetric\-Methode  
 Ruft einen metrischen Werts aus der Registrierung ab.  
  
```cpp#  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|pszMachine|\[in\]  möglicherweise Name eines Remotecomputers, dessen Register geschrieben wird, bedeutet`NULL` \(lokaler Computer\).|  
|pszType|\[in\]  Einer der metrischen Typen.|  
|guidSection|\[in\]  GUID eines bestimmten Moduls, mit einem Auswertungsdelegaten, der Ausnahmen usw.  Dies gibt einen Unterabschnitt eines metrischen Typ für ein bestimmtes Element an.|  
|pszMetric|\[in\]  Die Metriken abgerufen werden soll.  Dies entspricht einem bestimmten Namen des Werts.|  
|pdwValue|\[in\]  Der Speicherort des Werts der Metriken.  Es gibt verschiedene Typen von GetMetric, die ein DWORD \(wie in diesem Beispiel\), ein BSTR, eine GUID oder ein Array von GUIDs zurückgeben können.|  
|pszAltRoot|\[in\]  Ein alternativer zu verwendende Registrierungsstamm.  Auf `NULL` , wenn der Standardwert verwendet werden soll.|  
  
### SetMetric\-Methode  
 Legt den bereitgestellten metrischen Wert in der Registrierung festgelegt.  
  
```cpp#  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|pszType|\[in\]  Einer der metrischen Typen.|  
|guidSection|\[in\]  GUID eines bestimmten Moduls, mit einem Auswertungsdelegaten, der Ausnahmen usw.  Dies gibt einen Unterabschnitt eines metrischen Typ für ein bestimmtes Element an.|  
|pszMetric|\[in\]  Die Metriken abgerufen werden soll.  Dies entspricht einem bestimmten Namen des Werts.|  
|dwValue|\[in\]  Der Speicherort des Werts in der Metriken.  Es gibt verschiedene Typen von SetMetric, die ein DWORD \(in diesem Beispiel\), ein BSTR, eine GUID oder ein Array von GUIDs speichern können.|  
|fUserSpecific|\[in\]  TRUE, wenn die Metrik ist und ob sie sich auf Hiven des Benutzers anstelle der Hive des lokalen Computers geschrieben werden soll.|  
|pszAltRoot|\[in\]  Ein alternativer zu verwendende Registrierungsstamm.  Auf `NULL` , wenn der Standardwert verwendet werden soll.|  
  
### RemoveMetric\-Methode  
 Entfernt die angegebene Metrik aus der Registrierung.  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|pszType|\[in\]  Einer der metrischen Typen.|  
|guidSection|\[in\]  GUID eines bestimmten Moduls, mit einem Auswertungsdelegaten, der Ausnahmen usw.  Dies gibt einen Unterabschnitt eines metrischen Typ für ein bestimmtes Element an.|  
|pszMetric|\[in\]  Die zu entfernende Metriken.  Dies entspricht einem bestimmten Namen des Werts.|  
|pszAltRoot|\[in\]  Ein alternativer zu verwendende Registrierungsstamm.  Auf `NULL` , wenn der Standardwert verwendet werden soll.|  
  
### EnumMetricSections\-Methode  
 Listet die verschiedenen metrischen Abschnitte in der Registrierung auf.  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|pszMachine|\[in\]  möglicherweise Name eines Remotecomputers, dessen Register geschrieben wird, bedeutet`NULL` \(lokaler Computer\).|  
|pszType|\[in\]  Einer der metrischen Typen.|  
|rgguidSections|\[in, out\]  Zugeteiltes Array von GUIDs ausgefüllt werden soll, oder legt diese fest.|  
|pdwSize|\[in\]  Die maximale Anzahl von GUIDs, die im `rgguidSections` Array gespeichert werden kann.|  
|pszAltRoot|\[in\]  Ein alternativer zu verwendende Registrierungsstamm.  Auf `NULL` , wenn der Standardwert verwendet werden soll.|  
  
## Ausdrucksauswerter\-Funktionen  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|GetEEMetric|Ruft einen metrischen Werts aus der Registrierung ab.|  
|SetEEMetric|Legt den bereitgestellten metrischen Wert in der Registrierung festgelegt.|  
|RemoveEEMetric|Entfernt die angegebene Metrik aus der Registrierung.|  
|GetEEMetricFile|Ruft einen Dateinamen aus der angegebenen Metrik ab und lädt den Inhalt der Datei und gibt ihn als Zeichenfolge zurück.|  
  
## Ausnahme\-Funktionen  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|GetExceptionMetric|Ruft einen metrischen Werts aus der Registrierung ab.|  
|SetExceptionMetric|Legt den bereitgestellten metrischen Wert in der Registrierung festgelegt.|  
|RemoveExceptionMetric|Entfernt die angegebene Metrik aus der Registrierung.|  
|RemoveAllExceptionMetrics|Entfernt alle Ausnahme metrik aus der Registrierung.|  
  
## Symbol\-Anbieter\-Funktionen  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|GetSPMetric|Ruft einen metrischen Werts aus der Registrierung ab.|  
|SetSPMetric|Legt den bereitgestellten metrischen Wert in der Registrierung festgelegt.|  
|RemoveSPMetric|Entfernt die angegebene Metrik aus der Registrierung.|  
  
## Enumerations\-Funktionen  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|EnumMetricSections|Listet alle Metriken für einen bereitgestellten metrischen Typ auf.|  
|EnumDebugEngine|Listet die registrierten Debugmodule auf.|  
|EnumEEs|Listet die registrierten Ausdrucksauswertung auf.|  
|EnumExceptionMetrics|Listet alle Ausnahmemetrik auf.|  
  
## Metrische Definitionen  
 Diese Definitionen können für vordefinierte metrische Namen verwendet werden.  Alle Namen entsprechen den verschiedenen Registrierungsschlüsseln und \- Werts sind, und die als Zeichenfolgen mit Breitzeichen definiert sind: Beispielsweise `extern LPCWSTR metrictypeEngine`.  
  
|Vordefinierte metrische Typen|Beschreibung: Die Taste für….|  
|-----------------------------------|-----------------------------------|  
|metrictypeEngine|Alle metrik Modul debuggen.|  
|metrictypePortSupplier|Alle Anschlusslieferantenmetrik.|  
|metrictypeException|Alle Ausnahmemetrik.|  
|metricttypeEEExtension|Alle Erweiterungen der Ausdrucksauswertung.|  
  
|Debuggen von Modul\-Eigenschaften|Beschreibung|  
|---------------------------------------|------------------|  
|metricAddressBP|Wird als ungleich 0, um die Unterstützung Adressen Haltepunkte festzulegen.|  
|metricAlwaysLoadLocal|Wird als ungleich 0 für das Debugmodul immer lokal laden.|  
|metricLoadInDebuggeeSession|NOT VERWENDETE|  
|metricLoadedByDebuggee|Auf dem Wert ungleich 0 \(null\), um anzugeben, dass das Debugmodul immer geladen wird oder durch das Programm, das gedebuggt wird.|  
|metricAttach|Wird als ungleich 0, um die Unterstützung Anlage zu vorhandenen Programmen anzugeben.|  
|metricCallStackBP|Wird als ungleich 0, um die Unterstützung Aufruflisten von Haltepunkten anzugeben.|  
|metricConditionalBP|Wird als ungleich 0, um die Unterstützung der Einstellung von bedingten Haltepunkten anzugeben.|  
|metricDataBP|Auf dem Wert ungleich 0 \(null\), wenn die Unterstützung für das Festlegen von Haltepunkten für Änderungen an den Daten anzugeben.|  
|metricDisassembly|Auf dem Wert ungleich 0 \(null\), wenn die Unterstützung für die Produktion Disassemblys listet anzugeben.|  
|metricDumpWriting|Wird als ungleich 0, um die Unterstützung von Arbeitsspeicher zu schreiben \(Dumps einem Ausgabegerät speichern\) anzugeben.|  
|metricENC|Wird als ungleich 0, um die Unterstützung von Bearbeiten und Fortfahren. **Note:**  Ein benutzerdefiniertes Modul sollte dies nie Debuggen festlegen und sollte immer auf 0 festlegen.|  
|metricExceptions|Auf dem Wert ungleich 0 \(null\), wenn die Unterstützung für Ausnahmen anzugeben.|  
|metricFunctionBP|Auf dem Wert ungleich 0 \(null\), wenn die Unterstützung für benannte Haltepunkte Haltepunkte \(verursachen, wenn ein bestimmter Funktionsnamens aufgerufen wird\) anzugeben.|  
|metricHitCountBP|Wird als ungleich 0, um die Unterstützung der Einstellung von „Treffer das Popup“ \(Haltepunkte Haltepunkte, die erst nach gestartet werden, wobei einige Male\) erreicht wird.|  
|metricJITDebug|Wird als ungleich 0, um die Unterstützung Just\-In\-Time\-Debuggen \(der Debugger wird ausgelöst, wenn eine Ausnahme in einem laufenden Prozess ausgeführt wird\).|  
|metricMemory|NOT VERWENDETE|  
|metricPortSupplier|Legen Sie dies auf die CLSID des Anschlusslieferanten ab, sofern implementiert wird.|  
|metricRegisters|NOT VERWENDETE|  
|metricSetNextStatement|Auf dem Wert ungleich 0 \(null\), wenn die Unterstützung für das Festlegen der nächsten Anweisung zwischen der Ausführung anzugeben \(durch die Anweisungen überspringt\).|  
|metricSuspendThread|Auf dem Wert ungleich 0 \(null\), wenn die Unterstützung für das Unterbrechen der Ausführung des Threads anzugeben.|  
|metricWarnIfNoSymbols|Auf dem Wert ungleich 0 \(null\), um anzugeben, dass der Benutzer benachrichtigt werden soll, wenn keine Symbole vorhanden ist.|  
|metricProgramProvider|Legen Sie dies auf die CLSID des Anbieters Programm fest.|  
|metricAlwaysLoadProgramProviderLocal|Legen Sie dies auf den Wert ungleich 0 \(null\) fest, um anzugeben, dass der Anbieter Programm immer lokal geladen werden soll.|  
|metricEngineCanWatchProcess|Legen Sie dies auf den Wert ungleich 0 \(null\) fest, um anzugeben, dass das Debugmodul für Prozess wird anstelle des Anbieters Programm überwacht.|  
|metricRemoteDebugging|Legen Sie dies auf den Wert ungleich 0 \(null\) fest, um Unterstützung für das Remotedebuggen anzugeben.|  
|metricEncUseNativeBuilder|Legen Sie dies auf den Wert ungleich 0 \(null\) fest, um anzugeben, dass die Bearbeiten und Fortfahren Manager sollte das Debuggen encbuild.dll des Moduls verwenden, um zum Bearbeiten und Fortfahren zu erstellen. **Note:**  Ein benutzerdefiniertes Modul sollte dies nie Debuggen festlegen und sollte immer auf 0 festlegen.|  
|metricLoadUnderWOW64|Legen Sie dies auf den Wert ungleich 0 \(null\) fest, um anzugeben, dass das Debugmodul im zu debuggenden Prozess unter wow geladen werden soll, wenn Sie einen 64\-Bit\-Prozess debuggten. Andernfalls wird das Debugmodul in Visual Studio\-Prozess unter WOW64 ausgeführt \(Laden\).|  
|metricLoadProgramProviderUnderWOW64|Legen Sie dies auf den Wert ungleich 0 \(null\) fest, um anzugeben, dass der Anbieter Programm im zu debuggenden Prozess geladen werden soll, falls ein 64\-Bit\-Prozess unter wow gedebuggt. Andernfalls wird er in Visual Studio\-Prozess geladen.|  
|metricStopOnExceptionCrossingManagedBoundary|Legen Sie dies auf den Wert ungleich 0 \(null\) fest, um anzugeben, dass der Prozess beendet werden soll, wenn ein Ausnahmefehler zu den verwalteten und nicht verwalteten Code hinweg ausgelöst wird.|  
|metricAutoSelectPriority|Legen Sie dies auf eine Priorität für die automatische Auswahl des Debugmoduls fest \(höhere Werte entspricht höhere Priorität\).|  
|metricAutoSelectIncompatibleList|Registrierungsschlüssel, der Einträge enthält, die GUIDs angeben, sodass Debugsymbolinformationen auf Module in der automatischen Auswahl ignoriert werden können.  Diese Einträge sind eine Zahl \(0, 1, 2 usw.\) mit einer GUID, die als Zeichenfolge ausgedrückt wird.|  
|metricIncompatibleList|Registrierungsschlüssel, der Einträge enthält, die GUIDs für die Debug\- Module angeben, die diesem Modul Debuggen nicht kompatibel sind.|  
|metricDisableJITOptimization|Legen Sie dies auf den Wert ungleich 0 \(null\) fest, um anzugeben, dass die Optimierung \(für verwalteten Code\) während des Debuggens deaktiviert werden sollen.|  
  
|Ausdrucksauswerter\-Eigenschaften|Beschreibung|  
|---------------------------------------|------------------|  
|metricEngine|Dadurch wird die Anzahl der Module Debuggen auf, die den angegebenen Ausdrucksauswertung unterstützt werden.|  
|metricPreloadModules|Legen Sie dies auf den Wert ungleich 0 \(null\) fest, um anzugeben, dass Module vorab geladen werden sollen, wenn ein Ausdrucksauswertung für ein Programm gestartet wird.|  
|metricThisObjectName|Legen Sie dies auf den Objektnamen „this“ fest.|  
  
|Ausdrucksauswerter\-Erweiterungs\-Eigenschaften|Beschreibung|  
|-----------------------------------------------------|------------------|  
|metricExtensionDll|Name der DLL, die von dieser Erweiterung unterstützt.|  
|metricExtensionRegistersSupported|Liste von Registern unterstützt.|  
|metricExtensionRegistersEntryPoint|Einstiegspunkt zum Aufrufen von Registern.|  
|metricExtensionTypesSupported|Liste der Typen unterstützt.|  
|metricExtensionTypesEntryPoint|Einstiegspunkt für den Zugriff auf Typen.|  
  
|Anschluss\-Lieferanten\-Eigenschaften|Beschreibung|  
|-------------------------------------------|------------------|  
|metricPortPickerCLSID|Die CLSID der Anschluss\-Auswahl \(ein Dialogfeld, über das der Benutzer verwenden kann, um Ports ausgewählt und Ports zum Debuggen verwenden hinzuzufügen.\)|  
|metricDisallowUserEnteredPorts|Ungleich 0 \(null\), wenn die vom Benutzer eingegebene Ports nicht auf den Anschlusslieferanten \(dieser Port stellt das Dialogfeld Auswahl im Wesentlichen schreibgeschützt\) hinzugefügt werden können.|  
|metricPidBase|Die Prozess\-ID Verwendung des Anschlusslieferanten, wenn Prozesse\-ID zugeordnet sind.|  
  
|Vordefinierte SP\-Speicher\-Typen|Beschreibung|  
|---------------------------------------|------------------|  
|storetypeFile|Die Symbole werden in einer separaten Datei gespeichert.|  
|storetypeMetadata|Die Symbole werden als Metadaten in einer Assembly gespeichert.|  
  
|Verschiedene Eigenschaften|Beschreibung|  
|--------------------------------|------------------|  
|metricShowNonUserCode|Legen Sie dies auf den Wert ungleich 0 \(null\) fest, um Nicht\-Benutzer Code anzuzeigen.|  
|metricJustMyCodeStepping|Legen Sie dies auf den Wert ungleich 0 \(null\) fest, um anzugeben, dass das tretendes kann nur im Benutzercode auftreten.|  
|metricCLSID|CLSID für ein Objekt eines bestimmten Typs metrischen.|  
|metricName|Benutzerfreundlicher Name für ein Objekt eines bestimmten Typs metrischen.|  
|metricLanguage|Sprachenname.|  
  
## Registrierungs\-Speicherorte  
 Die Metriken wird von gelesen und geschrieben in die Registrierung, insbesondere im `VisualStudio` Unterschlüssel.  
  
> [!NOTE]
>  Meistens wird die Metrik für die HKEY\_LOCAL\_MACHINE\-Taste geschrieben.  Manchmal ist die den Schlüssel HKEY\_CURRENT\_USER Ziel.  Dbgmetric.lib behandelt beide Schlüssel.  Wenn eine Metrik abruft, sucht er zuerst HKEY\_CURRENT\_USER, HKEY\_LOCAL\_MACHINE.  Wenn eine Metrik festlegt, gibt ein Parameter an, der die zu verwendende Schlüssel der obersten Ebene.  
  
 *\[Registrierungsschlüssel\]*\\  
  
 `Software`\\  
  
 `Microsoft`\\  
  
 `VisualStudio`\\  
  
 *\[Release Registrierungsstamm\]*\\  
  
 *\[metrischer Stamm\]*\\  
  
 *\[metrischer Typ\]*\\  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
|Platzhalter|Beschreibung|  
|-----------------|------------------|  
|*\[Registrierungsschlüssel\]*|`HKEY_CURRENT_USER` oder `HKEY_LOCAL_MACHINE`.|  
|*\[Release Registrierungsstamm\]*|Die Version von Visual Studio \(z. B. `7.0`, `7.1`oder `8.0`\).  Allerdings kann dieser Schalter**\/rootsuffix** mit dem Stamm an **devenv.exe**ebenfalls geändert werden.  Bei dieser Modifizierer ist Partner in der Regel Exp, daher ist der Stamm Version z. B. 8.0Exp sein.|  
|*\[metrischer Stamm\]*|Dies ist entweder `AD7Metrics` oder `AD7Metrics(Debug)`, je nachdem, ob die Debugversion von dbgmetric.lib verwendet wird. **Note:**  Ob dbgmetric.lib verwendet wird, sollte dieser Namenskonvention gehaftet werden, wenn Sie Unterschiede zwischen Debugem und Releaseversionen haben, die in der Registrierung angegeben werden müssen.|  
|*\[metrischer Typ\]*|Der Typ der zu schreibenden Metriken: `Engine`, `ExpressionEvaluator`, `SymbolProvider`usw.  Alle diese werden wie in dbgmetric.h als definiert, in dem der bestimmte Typname ist.|  
|*\[Metriken\]*|Der Name eines Eintrags, der ein Wert zugewiesen werden soll, um die Metrik festlegen.  Die tatsächliche Organisation der Metrik ist von metrischen Typ ab.|  
|*\[metrischer Wert\]*|Der Wert der Metriken.  Der Typ, in den der Wert zugewiesen werden soll \(String, Nummer usw.\) richtet der Metriken.|  
  
> [!NOTE]
>  Alle GUID ist im Format `{GUID}`gespeichert.  Beispielsweise `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### Debuggen von Modulen  
 Im Folgenden sind die Organisation der metrik Modul Debuggen in der Registrierung.  `Engine` metrische ist der Typname für eine Debug\- und Modul entspricht *\[metrischer Typ\]* Registrierungsdaten in der obigen teilstruktur.  
  
 `Engine`\\  
  
 *\[Modul guid\]*\\  
  
 `CLSID` \= *\[Klasse guid\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 `PortSupplier`\\  
  
 `0` \= *\[Port\] lieferant guid*  
  
 `1` \= *\[Port\] lieferant guid*  
  
|Platzhalter|Beschreibung|  
|-----------------|------------------|  
|*\[Modul guid\]*|Die GUID des Debugmoduls.|  
|*\[Klasse guid\]*|Die GUID der Klasse, die dieses Debugmodul implementiert.|  
|*\[Port\] lieferant guid*|Die GUID des Anschlusslieferanten, sofern vorhanden.  Viele Debugmodule verwenden den Anschlusslieferanten und daher nicht ihren eigenen Lieferanten an.  In diesem Fall ist der Unterschlüssel nicht vorhanden `PortSupplier` .|  
  
### Anschluss\-Lieferanten  
 Im Folgenden sind die Organisation der Anschlusslieferanten metrik in der Registrierung.  `PortSupplier` metrische ist der Typname für den Anschlusslieferanten entsprechend *\[metrischer Typ\]*.  
  
 `PortSupplier`\\  
  
 *\[Port\] lieferant guid*\\  
  
 `CLSID` \= *\[Klasse guid\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
|Platzhalter|Beschreibung|  
|-----------------|------------------|  
|*\[Port\] lieferant guid*|Die GUID des Anschlusslieferanten|  
|*\[Klasse guid\]*|Die GUID der Klasse, die den Anschlusslieferanten implementiert|  
  
### Symbol\-Anbieter  
 Im Folgenden sind die Organisation der Symbol lieferanten metrik in der Registrierung.  `SymbolProvider` ist der metrische Typname für den Symbol und entspricht *\[metrischer Typ\]*.  
  
 `SymbolProvider`\\  
  
 *\[Symbol für guid\]*\\  
  
 `file`\\  
  
 `CLSID` \= *\[Klasse guid\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 `metadata`\\  
  
 `CLSID` \= *\[Klasse guid\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
|Platzhalter|Beschreibung|  
|-----------------|------------------|  
|*\[Symbol für guid\]*|Die GUID des Anbieters Symbol|  
|*\[Klasse guid\]*|Die GUID der Klasse, in der dieser Anbieter implementiert Symbol|  
  
### Ausdrucksauswerter  
 Im Folgenden sind die Organisation der Ausdrucksauswertung metrik in der Registrierung.  `ExpressionEvaluator` metrische ist der Typname für die Ausdrucksauswertung entspricht und *\[metrischer Typ\]*.  
  
> [!NOTE]
>  Der metrische Typ für `ExpressionEvaluator` wird nicht in dbgmetric.h definiert, da davon ausgegangen wird, dass alle metrischen Änderungen für die Ausdrucksauswertung die metrischen Funktionen des entsprechenden Ausdrucksauswerters durchlaufen werden \(das Lay\-out des Unterschlüssels `ExpressionEvaluator` ist etwas kompliziert. Daher werden die Details in dbgmetric.lib Hidden\).  
  
 `ExpressionEvaluator`\\  
  
 *\[Sprache guid\]*\\  
  
 *\[Anbieter guid\]*\\  
  
 `CLSID` \= *\[Klasse guid\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 `Engine`\\  
  
 `0` \= *\[Debuggen Modul guid\]*  
  
 `1` \= *\[Debuggen Modul guid\]*  
  
|Platzhalter|Beschreibung|  
|-----------------|------------------|  
|*\[Sprache guid\]*|Die GUID einer Sprache|  
|*\[Anbieter guid\]*|Die GUID eines Anbieters|  
|*\[Klasse guid\]*|Die GUID der Klasse, in der dieser Ausdrucksauswertung implementiert|  
|*\[Debuggen Modul guid\]*|Die GUID eines Debugmoduls, dem dieser Funktion mit der Ausdrucksauswertung|  
  
### Ausdrucksauswerter\-Erweiterungen  
 Im Folgenden sind die Organisation der Ausdrucksauswertung für metrik in der Registrierung.  `EEExtensions` metrische ist der Typname für die Ausdrucksauswertung entspricht und Verbesserungen *\[metrischer Typ\]*.  
  
 `EEExtensions`\\  
  
 *\[Erweiterung guid\]*\\  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
|Platzhalter|Beschreibung|  
|-----------------|------------------|  
|*\[Erweiterung guid\]*|Die GUID der Ausdrucksauswertung Namespaceerweiterung|  
  
### Ausnahmen  
 Im Folgenden sind die Organisation der Ausnahme metrik in der Registrierung.  `Exception` metrische ist der Typname für die Ausnahmen und entspricht *\[metrischer Typ\]*.  
  
 `Exception`\\  
  
 *\[Debuggen Modul guid\]*\\  
  
 *\[Ausnahmetypen\]*\\  
  
 *\[Ausnahme\]*\\  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Ausnahme\]*\\  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
 *\[Metriken\] \= \[metrischer Wert\]*  
  
|Platzhalter|Beschreibung|  
|-----------------|------------------|  
|*\[Debuggen Modul guid\]*|Die GUID eines Debugmoduls, die Ausnahmen unterstützt.|  
|*\[Ausnahmetypen\]*|Ein allgemeiner Name für den Unterschlüssel, der die Klasse angibt, die von Ausnahmen behandelt werden können.  Typische Namen sind **C\+\+ Exceptions**, **Win32 Exceptions**, **Common Language Runtime Exceptions**und **Native Run\-Time Checks**.  Diese Namen werden auch verwendet, um eine bestimmte Klasse Ausnahme an den Benutzer zu identifizieren.|  
|*\[Ausnahme\]*|Ein Name für eine Ausnahme: **\_com\_error** z. B. **Control\-Break**oder legt diese fest.  Diese Namen werden auch verwendet, um eine bestimmte Ausnahme an den Benutzer zu identifizieren.|  
  
## Anforderungen  
 Diese Dateien befinden sich im Installationsverzeichnis [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK \(standardmäßig *\[Laufwerk\]*\\ Programme \\ Microsoft Visual Studio 2010 SDK \\\).  
  
 Header: dbgmetric.h \\ Includes  
  
 Bibliothek: Bibliotheken \\ \\ dbgmetric.lib Bibliotheken, ad2de.lib  
  
## Siehe auch  
 [API\-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)