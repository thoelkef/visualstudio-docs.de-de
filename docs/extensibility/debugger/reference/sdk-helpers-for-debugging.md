---
title: SDK-Hilfsprogramme für das Debuggen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e80344b8cec1bc013e044be39638879b049c8d0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135921"
---
# <a name="sdk-helpers-for-debugging"></a>SDK-Hilfsprogramme für das Debuggen
Diese Funktionen und Deklarationen sind globale Hilfsfunktionen zum Implementieren von Debugmodule, ausdruckauswertung und Symbol-Anbieter in C++.  
  
> [!NOTE]
>  Es gibt keine verwalteten Versionen dieser Funktionen und Deklarationen zu diesem Zeitpunkt.  
  
## <a name="overview"></a>Übersicht  
 Damit Debugmodule, ausdruckauswertung und Symbol-Anbieter von Visual Studio verwendet werden kann müssen sie registriert werden. Dies erfolgt durch Festlegen der Registrierungsunterschlüssel und-Einträge, bekannt als "Einstellung Metriken". Die folgenden globalen Funktionen dienen, aktualisiert diese Metriken zu vereinfachen. Finden Sie im Abschnitt für Registrierungsspeicherorte so ermitteln Sie das Layout der einzelnen Registrierungsunterschlüssel, die von diesen Funktionen aktualisiert wird.  
  
## <a name="general-metric-functions"></a>Allgemeine Metrik-Funktionen  
 Hierbei handelt es sich um allgemeine Funktionen, die von Debugmodule verwendet. Spezielle Funktionen für ausdruckauswertung und Symbol-Anbieter werden später beschrieben.  
  
### <a name="getmetric-method"></a>GetMetric-Methode  
 Ruft einen metrischen Wert aus der Registrierung ab.  
  
```cpp  
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
|---------------|-----------------|  
|pszMachine|[in] Name eines möglicherweise Remotecomputers, deren Registrierung geschrieben werden (`NULL` bedeutet lokalen Computer).|  
|pszType|[in] Einer der Metriken Typen.|  
|guidSection|[in] GUID, der einem bestimmten Modul, bei der ausdrucksauswertung, Ausnahme usw. Dies gibt einen Unterabschnitt unter einen metrischen Typ für ein bestimmtes Element an.|  
|pszMetric|[in] Die Metrik abgerufen werden soll. Dies entspricht einem bestimmten Wertnamen.|  
|pdwValue|[in] Der Speicherort des Werts aus der Metrik. Es gibt verschiedene Arten von GetMetric, die einen DWORD-Wert (wie in diesem Beispiel), einen BSTR, eine GUID oder ein Array von GUIDs zurückgeben können.|  
|pszAltRoot|[in] Eine alternative Registrierungsstamm verwenden. Legen Sie auf `NULL` verwenden.|  
  
### <a name="setmetric-method"></a>SetMetric-Methode  
 Den angegebenen Wert für die Metriken festgelegt in der Registrierung.  
  
```cpp  
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
|---------------|-----------------|  
|pszType|[in] Einer der Metriken Typen.|  
|guidSection|[in] GUID, der einem bestimmten Modul, bei der ausdrucksauswertung, Ausnahme usw. Dies gibt einen Unterabschnitt unter einen metrischen Typ für ein bestimmtes Element an.|  
|pszMetric|[in] Die Metrik abgerufen werden soll. Dies entspricht einem bestimmten Wertnamen.|  
|dwValue|[in] Der Speicherort des Werts in der Metrik. Es gibt verschiedene Arten von SetMetric, die einen DWORD-Wert (in diesem Beispiel), einen BSTR, eine GUID oder ein Array von GUIDs speichern können.|  
|fUserSpecific|[in] "True", wenn die Metrik benutzerspezifische ist und es in die Struktur des Benutzers anstelle der lokalen Struktur geschrieben werden soll.|  
|pszAltRoot|[in] Eine alternative Registrierungsstamm verwenden. Legen Sie auf `NULL` verwenden.|  
  
### <a name="removemetric-method"></a>RemoveMetric-Methode  
 Entfernt die angegebene Metrik aus der Registrierung.  
  
```cpp  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|pszType|[in] Einer der Metriken Typen.|  
|guidSection|[in] GUID, der einem bestimmten Modul, bei der ausdrucksauswertung, Ausnahme usw. Dies gibt einen Unterabschnitt unter einen metrischen Typ für ein bestimmtes Element an.|  
|pszMetric|[in] Die Metrik entfernt werden soll. Dies entspricht einem bestimmten Wertnamen.|  
|pszAltRoot|[in] Eine alternative Registrierungsstamm verwenden. Legen Sie auf `NULL` verwenden.|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections-Methode  
 Listet die verschiedenen Metrik Abschnitte in der Registrierung.  
  
```cpp  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|pszMachine|[in] Name eines möglicherweise Remotecomputers, deren Registrierung geschrieben werden (`NULL` bedeutet lokalen Computer).|  
|pszType|[in] Einer der Metriken Typen.|  
|rgguidSections|[in, out] Vorab zugeordnete Array von GUIDs, das ausgefüllt wird.|  
|pdwSize|[in] Die maximale Anzahl von GUIDs, die in gespeichert werden, können die `rgguidSections` Array.|  
|pszAltRoot|[in] Eine alternative Registrierungsstamm verwenden. Legen Sie auf `NULL` verwenden.|  
  
## <a name="expression-evaluator-functions"></a>Ausdrucksauswertungsfehler Ausdrucksfunktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|GetEEMetric|Ruft einen metrischen Wert aus der Registrierung ab.|  
|SetEEMetric|Den angegebenen Wert für die Metriken festgelegt in der Registrierung.|  
|RemoveEEMetric|Entfernt die angegebene Metrik aus der Registrierung.|  
|GetEEMetricFile|Ruft einen Dateinamen aus der angegebenen Metrik und geladen, den Inhalt der Datei als Zeichenfolge zurückgegeben.|  
  
## <a name="exception-functions"></a>Ausnahme-Funktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|GetExceptionMetric|Ruft einen metrischen Wert aus der Registrierung ab.|  
|SetExceptionMetric|Den angegebenen Wert für die Metriken festgelegt in der Registrierung.|  
|RemoveExceptionMetric|Entfernt die angegebene Metrik aus der Registrierung.|  
|RemoveAllExceptionMetrics|Entfernt alle Ausnahme Metriken aus der Registrierung.|  
  
## <a name="symbol-provider-functions"></a>Symbol-Anbieter-Funktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|GetSPMetric|Ruft einen metrischen Wert aus der Registrierung ab.|  
|SetSPMetric|Den angegebenen Wert für die Metriken festgelegt in der Registrierung.|  
|RemoveSPMetric|Entfernt die angegebene Metrik aus der Registrierung.|  
  
## <a name="enumeration-functions"></a>Änderungsenumerationsfunktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|EnumMetricSections|Listet alle Metriken für einen angegebenen Metrik an.|  
|EnumDebugEngine|Listet die registrierten Debugmodule an.|  
|EnumEEs|Listet die registrierten ausdruckauswertung an.|  
|EnumExceptionMetrics|Listet alle Ausnahme Metriken an.|  
  
## <a name="metric-definitions"></a>Metrikdefinitionen  
 Diese Definitionen können für vordefinierte metriknamen verwendet werden. Die Namen entsprechen, um verschiedene Registrierungsschlüssel, Wertnamen und sind definiert als Breitzeichen-Zeichenfolgen: z. B. `extern LPCWSTR metrictypeEngine`.  
  
|Vordefinierte Metrik Typen|Beschreibung: Der base-Schlüssel für...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Alle für das Debuggen des Datenbankmoduls Metriken.|  
|metrictypePortSupplier|Alle Metriken für die Port-Lieferanten.|  
|metrictypeException|Alle Ausnahme Metriken.|  
|metricttypeEEExtension|Alle Expression Evaluator-Erweiterungen.|  
  
|Debuggen Sie die Eigenschaften des Datenbankmoduls|Beschreibung|  
|-----------------------------|-----------------|  
|metricAddressBP|Legen Sie auf ungleich NULL, um Unterstützung für Adresshaltepunkte anzugeben.|  
|metricAlwaysLoadLocal|Legen Sie auf ungleich NULL, um immer lokal die Debugging-Modul zu laden.|  
|metricLoadInDebuggeeSession|NICHT VERWENDET|  
|metricLoadedByDebuggee|Legen Sie auf ungleich NULL, um anzugeben, dass die Debugging-Modul wird immer mit oder durch das derzeit debuggte Programm geladen werden.|  
|metricAttach|Legen Sie auf ungleich NULL, um Unterstützung für das Anfügen an eine vorhandene Programme anzugeben.|  
|metricCallStackBP|Legen Sie auf ungleich NULL, um Unterstützung für Call Stack Haltepunkte anzugeben.|  
|metricConditionalBP|Legen Sie auf ungleich NULL, um Unterstützung für die Einstellung bedingte Haltepunkte anzugeben.|  
|metricDataBP|Legen Sie auf ungleich NULL, um Unterstützung für die Einstellung von Haltepunkten auf Änderungen in Daten anzugeben.|  
|metricDisassembly|Legen Sie zu ungleich NULL, um Unterstützung für die Erzeugung einer Auflistung an Disassembly anzugeben.|  
|metricDumpWriting|Legen Sie auf ungleich NULL, um Unterstützung für Dump schreiben (die Sicherung der Arbeitsspeicher, um ein Ausgabegerät) anzugeben.|  
|metricENC|Legen Sie zu ungleich NULL, um Unterstützung für bearbeiten und Fortfahren anzugeben. **Hinweis:** benutzerdefinierten Debugmodul Dies darf nicht festgelegt oder sollte immer auf 0 festgelegt.|  
|metricExceptions|Legen Sie auf ungleich NULL, um Unterstützung für Ausnahmen anzugeben.|  
|metricFunctionBP|Legen Sie auf ungleich NULL, um anzugeben, Unterstützung für benannte Haltepunkte (Breakpoints, die zu unterbrechen, wenn der Name einer bestimmten Funktion aufgerufen wird).|  
|metricHitCountBP|Legen Sie auf ungleich NULL an, dass die Unterstützung für die Einstellung von Haltepunkten "Punkt erreicht" (Haltepunkte, die ausgelöst werden, nachdem eine bestimmte Anzahl von Malen wird erreicht).|  
|metricJITDebug|Legen Sie zu ungleich NULL, um Unterstützung für Just-in-Time-Debuggen (der Debugger wird gestartet, wenn eine Ausnahme in einen laufenden Prozess auftritt) anzugeben.|  
|metricMemory|NICHT VERWENDET|  
|metricPortSupplier|Legen Sie diese auf die CLSID des Lieferanten Port, wenn eine implementiert wird.|  
|metricRegisters|NICHT VERWENDET|  
|metricSetNextStatement|Legen Sie auf ungleich NULL, um Unterstützung für das Festlegen der nächsten Anweisung (die Ausführung von Anweisungen intermediate überspringt) anzugeben.|  
|metricSuspendThread|Legen Sie auf ungleich NULL, um Unterstützung für das Anhalten der Threadausführung anzugeben.|  
|metricWarnIfNoSymbols|Legen Sie auf ungleich NULL, um anzugeben, dass der Benutzer benachrichtigt werden sollen, wenn keine Symbole vorhanden sind.|  
|metricProgramProvider|Legen Sie diese Option, um die CLSID des Programm-Anbieters.|  
|metricAlwaysLoadProgramProviderLocal|Legen Sie diese zu ungleich NULL, um anzugeben, dass der Anbieter Programm immer lokal geladen werden soll.|  
|metricEngineCanWatchProcess|Legen Sie ungleich NULL, um anzugeben, dass die Debugging-Modul für die Verarbeitung von Ereignissen anstelle des Anbieters Programm überwacht werden.|  
|metricRemoteDebugging|Legen Sie ungleich NULL, um Unterstützung für das Remotedebuggen anzugeben.|  
|metricEncUseNativeBuilder|Legen Sie diese zu ungleich NULL, um anzugeben, dass das Debugmodul encbuild.dll den bearbeiten und Fortfahren-Manager zum Erstellen für bearbeiten und Fortfahren verwenden werden soll. **Hinweis:** benutzerdefinierten Debugmodul Dies darf nicht festgelegt oder sollte immer auf 0 festgelegt.|  
|metricLoadUnderWOW64|Legen Sie den Wert ungleich NULL, um anzugeben, dass die Debugging-Modul im zu debuggenden Prozess unter WOW soll, beim Debuggen eines 64-Bit-Prozess geladen werden; Andernfalls wird Debugging-Modul in der Visual Studio-Prozess geladen werden (die unter WOW64 ausgeführt wird).|  
|metricLoadProgramProviderUnderWOW64|Legen Sie den Wert ungleich NULL, um anzugeben, dass der Anbieter der Anwendung im zu debuggenden Prozess geladen, beim Debuggen eines 64-Bit-Prozess unter WOW werden soll; Andernfalls wird in der Visual Studio-Prozess geladen werden.|  
|metricStopOnExceptionCrossingManagedBoundary|Legen Sie ungleich NULL, um anzugeben, dass der Prozess beendet wird, wenn eine nicht behandelte Ausnahme, verwalteten und unverwalteten Code hinweg ausgelöst wird.|  
|metricAutoSelectPriority|Legen Sie eine Priorität für die automatische Auswahl von Debugging-Modul (höher Werte gleich höhere Priorität).|  
|metricAutoSelectIncompatibleList|Der Registrierungsschlüssel enthält Einträge, die GUIDs für Debugmodule ignoriert werden soll, in der automatischen Auswahl angeben. Diese Einträge sind eine Zahl (0, 1, 2 und So weiter) mit einer GUID als Zeichenfolge ausgedrückt.|  
|metricIncompatibleList|Der Registrierungsschlüssel enthält Einträge, die GUIDs für die Debugmodule angeben, die mit diesem Debugging-Modul nicht kompatibel sind.|  
|metricDisableJITOptimization|Legen Sie ungleich NULL, um anzugeben, dass während des Debuggens Just-in-Time-Optimierungen (für verwalteten Code) deaktiviert werden soll.|  
  
|Expression Evaluator-Eigenschaften|Beschreibung|  
|-------------------------------------|-----------------|  
|metricEngine|Dies ist die Anzahl der Debugmodule, die die angegebenen ausdrucksauswertung zu unterstützen.|  
|metricPreloadModules|Legen Sie ungleich NULL, um anzugeben, dass Module geladen werden sollen, wenn eine ausdrucksauswertung für ein Programm gestartet wird.|  
|metricThisObjectName|Legen Sie den "this" Objektnamen.|  
  
|Expression Evaluator-Erweiterungseigenschaften|Beschreibung|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Der Name der Dll, die diese Erweiterung unterstützt.|  
|metricExtensionRegistersSupported|Liste der Register unterstützt.|  
|metricExtensionRegistersEntryPoint|Der Einstiegspunkt für den Zugriff auf registriert.|  
|metricExtensionTypesSupported|Die Liste der unterstützten Typen.|  
|metricExtensionTypesEntryPoint|Der Einstiegspunkt für den Zugriff auf Typen.|  
  
|Eigenschaften für Lieferanten|Beschreibung|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|Die CLSID der Port-Auswahl (der Benutzer das Dialogfeld können Sie Ports auswählen und Hinzufügen von Ports zum Debuggen verwendet).|  
|metricDisallowUserEnteredPorts|Ungleich NULL, wenn der Benutzer eingegeben Ports an den Lieferanten Port hinzugefügt werden können (Dadurch wird der Port Farbauswahl-Dialogfeld im Wesentlichen schreibgeschützt).|  
|metricPidBase|Die Basis-Prozess-ID, die vom Lieferanten Port verwendet wird, wenn Sie die Prozess-IDs zuordnen.|  
  
|Vordefinierte SP Speichertypen|Beschreibung|  
|-------------------------------|-----------------|  
|storetypeFile|Die Symbole werden in einer separaten Datei gespeichert.|  
|storetypeMetadata|Die Symbole werden als Metadaten in einer Assembly gespeichert.|  
  
|Verschiedene sonstige Eigenschaften|Beschreibung|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Legen Sie den anzuzeigenden Nonuser Code ungleich NULL.|  
|metricJustMyCodeStepping|Legen Sie ungleich NULL, um anzugeben, dass die schrittweise Ausführung im Benutzercode nur auftreten kann.|  
|metricCLSID|Die CLSID für ein Objekt eines bestimmten Typs Metrik.|  
|MetricName|Benutzerfreundlicher Name für ein Objekt eines bestimmten Typs Metrik.|  
|metricLanguage|Der Name der Sprache.|  
  
## <a name="registry-locations"></a>Registrierungspfad  
 Die Metriken aus liest und schreibt Sie in der Registrierung, insbesondere in den `VisualStudio` Unterschlüssel.  
  
> [!NOTE]
>  In den meisten Fällen, werden die Metriken für den Schlüssel HKEY_LOCAL_MACHINE geschrieben. Allerdings wird manchmal HKEY_CURRENT_USER das Ziel ist. Dbgmetric.lib verarbeitet beide Schlüssel. Beim Abrufen einer Metrik HKEY_CURRENT_USER durchsucht zuerst, dann HKEY_LOCAL_MACHINE. Wenn sie eine Metrik festlegen ist, gibt einen Parameter welche Schlüssel auf oberster Ebene verwendet.  
  
 *[Registrierungsschlüssel]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[Version Root]*\  
  
 *[Metrik Root]*\  
  
 *[Metrik Type]*\  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Registrierungsschlüssel]*|`HKEY_CURRENT_USER` oder `HKEY_LOCAL_MACHINE`.|  
|*[Version Root]*|Die Version von Visual Studio (z. B. `7.0`, `7.1`, oder `8.0`). Diese Stamm kann jedoch auch geändert werden mithilfe der **/rootsuffix** wechseln Sie zur **devenv.exe**. Für VSIP, this-Modifizierer ist in der Regel **Exp**, deshalb ist der Stamm der Version, z. B. 8.0Exp.|  
|*[Metrik Root]*|Dies liegt entweder an `AD7Metrics` oder `AD7Metrics(Debug)`, je nachdem, ob die Debugversion von dbgmetric.lib verwendet wird. **Hinweis:** , und zwar unabhängig davon, ob dbgmetric.lib verwendet wird, diese Benennungskonvention befolgen sollten eingehalten werden, wenn Sie Unterschiede zwischen Debug- und haben Versionen, die in der Registrierung berücksichtigt werden müssen.|  
|*[Metrik Type]*|Der Typ des zu schreibenden Metrik: `Engine`, `ExpressionEvaluator`, `SymbolProvider`usw. Diese sind alle definiert, wie in dbgmetric.h als `metricTypeXXXX`, wobei `XXXX` ist der Name der spezifischen Typ.|  
|*[Metrik]*|Der Name der Eintrag ein Wert zugewiesen werden, um die Metrik festzulegen. Die tatsächliche Organisation der Metriken hängt von der Metrik Typ ab.|  
|*[Metrikwert]*|Der Wert, der an der Metrik zugewiesen wird. Der Typ, der den Wert (Zeichenfolge, Zahl, usw.) aufweisen sollte hängt die Metrik aus.|  
  
> [!NOTE]
>  Alle GUIDs werden gespeichert, in das Format der `{GUID}`. Beispielsweise `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Debuggen von Modulen  
 Im folgenden finden die Organisation von der Debug-Module-Metriken in der Registrierung. `Engine` ist der Metrik Typname für ein Debugging-Modul und entspricht *[Metrik Type]* in der oben genannten Registrierungsteilstruktur.  
  
 `Engine`\  
  
 *[Datenbankmodul Guid]*\  
  
 `CLSID` = *[Klasse Guid]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 `PortSupplier`\  
  
 `0` = *[Port Lieferanten Guid]*  
  
 `1` = *[Port Lieferanten Guid]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Datenbankmodul Guid]*|Die GUID der Debugging-Modul.|  
|*[Klasse Guid]*|Die GUID der Klasse, die diese Debugmodul implementiert werden soll.|  
|*[Port Lieferanten Guid]*|Die GUID des Lieferanten Port, sofern vorhanden. Viele Debugmodule verwenden standardmäßig Port Lieferanten und geben Sie daher nicht ihre eigenen Lieferanten. In diesem Fall ist der Unterschlüssel `PortSupplier` abwesend sein wird.|  
  
### <a name="port-suppliers"></a>Port-Lieferanten  
 Im folgenden finden die Organisation der Port Lieferanten Metriken in der Registrierung. `PortSupplier` ist der Metrik Typname für einen Port Lieferanten und entspricht *[Metrik Type]*.  
  
 `PortSupplier`\  
  
 *[Port Lieferanten Guid]*\  
  
 `CLSID` = *[Klasse Guid]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Port Lieferanten Guid]*|Die GUID des Lieferanten port|  
|*[Klasse Guid]*|Die GUID der Klasse, die diesem Port Lieferanten implementiert|  
  
### <a name="symbol-providers"></a>Symbol-Anbieter  
 Im folgenden finden die Organisation der Metriken Lieferanten Symbol in der Registrierung. `SymbolProvider` ist der Metrik Typname für den Symbol-Anbieter und entspricht *[Metrik Type]*.  
  
 `SymbolProvider`\  
  
 *[Symbol-Anbieter-Guid]*\  
  
 `file`\  
  
 `CLSID` = *[Klasse Guid]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 `metadata`\  
  
 `CLSID` = *[Klasse Guid]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Symbol-Anbieter-Guid]*|Die GUID der Symbol-Anbieter|  
|*[Klasse Guid]*|Die GUID der Klasse, die diese Symbol-Anbieter implementiert.|  
  
### <a name="expression-evaluators"></a>Ausdrucksauswertungen  
 Im folgenden finden die Organisation der Expression Evaluator Metriken in der Registrierung. `ExpressionEvaluator` ist der Metrik Typname für die ausdrucksauswertung und entspricht *[Metrik Type]*.  
  
> [!NOTE]
>  Der Metrik-Typ für `ExpressionEvaluator` ist im dbgmetric.h, nicht definiert, da davon ausgegangen wird, dass die entsprechenden Ausdruck Ausdrucksauswertungsfehler Metrik Funktionen aller metrische Änderungen für ausdruckauswertung durchlaufen werden (das Layout von der `ExpressionEvaluator` Unterschlüssel ist in einem gewissen kompliziert sein muss, damit die Details in dbgmetric.lib ausgeblendet sind).  
  
 `ExpressionEvaluator`\  
  
 *[Sprache Guid]*\  
  
 *[Anbieter-Guid]*\  
  
 `CLSID` = *[Klasse Guid]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 `Engine`\  
  
 `0` = *[Debuggen Sie Modul-Guid]*  
  
 `1` = *[Debuggen Sie Modul-Guid]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Sprache Guid]*|Die GUID einer Sprache|  
|*[Anbieter-Guid]*|Die GUID des ein Hersteller|  
|*[Klasse Guid]*|Die GUID der Klasse, die diese ausdrucksauswertung implementiert.|  
|*[Debuggen Sie Modul-Guid]*|Die GUID des ein Debugmodul, das mit dieser Auswertung eines Ausdrucks verwendet werden kann|  
  
### <a name="expression-evaluator-extensions"></a>Expression Evaluator-Erweiterungen  
 Im folgenden finden die Organisation der Expression Evaluator Erweiterung Metriken in der Registrierung. `EEExtensions` ist der Metrik Typname für den Ausdruck Evaluator-Erweiterungen und entspricht *[Metrik Type]*.  
  
 `EEExtensions`\  
  
 *[Erweiterung Guid]*\  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Erweiterung Guid]*|Die GUID einer Expression Evaluator-Erweiterung|  
  
### <a name="exceptions"></a>Ausnahmen  
 Im folgenden finden die Organisation der Metriken Ausnahmen in der Registrierung. `Exception` ist der Metrik Typname für die Ausnahmen und entspricht *[Metrik Type]*.  
  
 `Exception`\  
  
 *[Debuggen Sie Modul-Guid]*\  
  
 *[Ausnahmetypen]*\  
  
 *[Exception]*\  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Exception]*\  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Debuggen Sie Modul-Guid]*|Die GUID des ein Debugging-Modul, die Ausnahmen unterstützt.|  
|*[Ausnahmetypen]*|Eine allgemeine Titel für den Unterschlüssel, identifiziert die Klasse von Ausnahmen, die verarbeitet werden kann. Typische Namen sind **C++-Ausnahmen**, **Win32-Ausnahmen**, **Common Language Runtime-Ausnahmen**, und **Native Run-Time Checks**. Diese Namen werden auch verwendet, um eine bestimmte Klasse der Ausnahme an den Benutzer zu identifizieren.|  
|*[Exception]*|Einen Namen für eine Ausnahme: z. B. **_com_error** oder **mit Gruppenwechsel**. Diese Namen werden auch verwendet, um eine bestimmte Ausnahme an den Benutzer zu identifizieren.|  
  
## <a name="requirements"></a>Anforderungen  
 Diese Dateien befinden sich der [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK-Installationsverzeichnis (standardmäßig *[Laufwerk]* \Programme\Microsoft Visual Studio 2010 SDK\\).  
  
 Header: includes\dbgmetric.h  
  
 Bibliothek: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Siehe auch  
 [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)