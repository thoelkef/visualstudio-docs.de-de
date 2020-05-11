---
title: SDK-Hilfsprogramme zum Debuggen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edb7c508fdea6736a71c0f70c0d2ff305d4a399
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713647"
---
# <a name="sdk-helpers-for-debugging"></a>SDK-Hilfsprogramme für das Debuggen
Diese Funktionen und Deklarationen sind globale Hilfsfunktionen zum Implementieren von Debugmodulen, Ausdrucksauswertungen und Symbolanbietern in C++.

> [!NOTE]
> Es sind derzeit keine verwalteten Versionen dieser Funktionen und Deklarationen vorhanden.

## <a name="overview"></a>Übersicht
 Damit Debugmodule, Ausdrucksauswertungen und Symbolanbieter von Visual Studio verwendet werden können, müssen sie registriert werden. Dies geschieht durch Festlegen von Registrierungsunterschlüsseln und Einträgen, die auch als "Festlegen von Metriken" bezeichnet werden. Die folgenden globalen Funktionen wurden entwickelt, um die Aktualisierung dieser Metriken zu vereinfachen. Im Abschnitt "Registrierungsspeicherorte" finden Sie informationen zum Layout der einzelnen Registrierungsunterschlüssel, die durch diese Funktionen aktualisiert werden.

## <a name="general-metric-functions"></a>Allgemeine metrische Funktionen
 Dies sind allgemeine Funktionen, die von Debug-Engines verwendet werden. Spezielle Funktionen für Ausdrucksevaluatoren und Symbolanbieter werden später detailliert beschrieben.

### <a name="getmetric-method"></a>GetMetric-Methode
 Ruft einen Metrikwert aus der Registrierung ab.

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

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|pszMachine|[in] Name eines möglicherweise entfernten Computers,`NULL` dessen Register geschrieben wird (d. h. lokaler Computer).|
|pszType|[in] Einer der Metriktypen.|
|guidAbschnitt|[in] GUID eines bestimmten Motors, Evaluators, Ausnahme usw. Dadurch wird ein Unterabschnitt unter einem Metriktyp für ein bestimmtes Element angegeben.|
|pszMetric|[in] Die zu erhaltende Metrik. Dies entspricht einem bestimmten Wertnamen.|
|pdwValue|[in] Der Speicherort des Werts aus der Metrik. Es gibt mehrere Varianten von GetMetric, die ein DWORD (wie in diesem Beispiel), eine BSTR, eine GUID oder ein Array von GUIDs zurückgeben können.|
|pszAltRoot|[in] Ein alternativer Registrierungsstamm, der verwendet werden soll. Legen `NULL` Sie fest, dass die Standardeinstellung verwendet wird.|

### <a name="setmetric-method"></a>SetMetric-Methode
 Legt den angegebenen Metrikwert in der Registrierung fest.

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

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|pszType|[in] Einer der Metriktypen.|
|guidAbschnitt|[in] GUID eines bestimmten Motors, Evaluators, Ausnahme usw. Dadurch wird ein Unterabschnitt unter einem Metriktyp für ein bestimmtes Element angegeben.|
|pszMetric|[in] Die zu erhaltende Metrik. Dies entspricht einem bestimmten Wertnamen.|
|dwValue|[in] Der Speicherort des Werts in der Metrik. Es gibt mehrere Varianten von SetMetric, die ein DWORD (in diesem Beispiel), eine BSTR, eine GUID oder ein Array von GUIDs speichern können.|
|fUserSpecific|[in] TRUE, wenn die Metrik benutzerspezifisch ist und in die Struktur des Benutzers anstelle der lokalen Computerstruktur geschrieben werden soll.|
|pszAltRoot|[in] Ein alternativer Registrierungsstamm, der verwendet werden soll. Legen `NULL` Sie fest, dass die Standardeinstellung verwendet wird.|

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

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|pszType|[in] Einer der Metriktypen.|
|guidAbschnitt|[in] GUID eines bestimmten Motors, Evaluators, Ausnahme usw. Dadurch wird ein Unterabschnitt unter einem Metriktyp für ein bestimmtes Element angegeben.|
|pszMetric|[in] Die zu entfernende Metrik. Dies entspricht einem bestimmten Wertnamen.|
|pszAltRoot|[in] Ein alternativer Registrierungsstamm, der verwendet werden soll. Legen `NULL` Sie fest, dass die Standardeinstellung verwendet wird.|

### <a name="enummetricsections-method"></a>EnumMetricSections-Methode
 Zählt die verschiedenen Metrikabschnitte in der Registrierung auf.

```cpp
HRESULT EnumMetricSections(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   GUID *  rgguidSections,
   DWORD * pdwSize,
   LPCWSTR pszAltRoot
);
```

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|pszMachine|[in] Name eines möglicherweise entfernten Computers,`NULL` dessen Register geschrieben wird (d. h. lokaler Computer).|
|pszType|[in] Einer der Metriktypen.|
|rgguidSections|[in, out] Vorab zugewiesenes Array von GUIDs, die ausgefüllt werden sollen.|
|pdwSize|[in] Die maximale Anzahl von GUIDs, `rgguidSections` die im Array gespeichert werden können.|
|pszAltRoot|[in] Ein alternativer Registrierungsstamm, der verwendet werden soll. Legen `NULL` Sie fest, dass die Standardeinstellung verwendet wird.|

## <a name="expression-evaluator-functions"></a>Expression Evaluator-Funktionen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|GetEEMetric|Ruft einen Metrikwert aus der Registrierung ab.|
|SetEEMetric|Legt den angegebenen Metrikwert in der Registrierung fest.|
|RemoveEEMetric|Entfernt die angegebene Metrik aus der Registrierung.|
|GetEEMetricFile|Ruft einen Dateinamen aus der angegebenen Metrik ab und lädt ihn, wodurch der Dateiinhalt als Zeichenfolge zurückgegeben wird.|

## <a name="exception-functions"></a>Ausnahmefunktionen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|GetExceptionMetric|Ruft einen Metrikwert aus der Registrierung ab.|
|SetExceptionMetric|Legt den angegebenen Metrikwert in der Registrierung fest.|
|RemoveExceptionMetric|Entfernt die angegebene Metrik aus der Registrierung.|
|RemoveAllExceptionMetrics|Entfernt alle Ausnahmemetriken aus der Registrierung.|

## <a name="symbol-provider-functions"></a>Symbolanbieterfunktionen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|GetSPMetric|Ruft einen Metrikwert aus der Registrierung ab.|
|SetSPMetric|Legt den angegebenen Metrikwert in der Registrierung fest.|
|RemoveSPMetric|Entfernt die angegebene Metrik aus der Registrierung.|

## <a name="enumeration-functions"></a>Enumerationsfunktionen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|EnumMetricSections|Zählt alle Metriken für einen angegebenen Metriktyp auf.|
|EnumDebugEngine|Zählt die registrierten Debugmodule auf.|
|EnumEEs|Zählt die Auswertungen des registrierten Ausdrucks auf.|
|EnumExceptionMetrics|Zählt alle Ausnahmemetriken auf.|

## <a name="metric-definitions"></a>Metrikdefinitionen
 Diese Definitionen können für vordefinierte Metriknamen verwendet werden. Die Namen entsprechen verschiedenen Registrierungsschlüsseln und Wertnamen und sind alle `extern LPCWSTR metrictypeEngine`als Breitzeichenzeichenfolgen definiert: z. B. .

|Vordefinierte Metriktypen|Beschreibung: Der Basisschlüssel für....|
|-----------------------------|---------------------------------------|
|metrictypeEngine|Alle Debugmodulmetriken.|
|metrictypePortSupplier|Alle Portlieferantenmetriken.|
|metrictypeException|Alle Ausnahmemetriken.|
|metricttypeEEExtension|Alle Ausdrucksauswertungserweiterungen.|

|Debugmoduleigenschaften|BESCHREIBUNG|
|-----------------------------|-----------------|
|metricAddressBP|Legen Sie auf ungleich Null fest, um die Unterstützung für Adresshaltepunkte anzugeben.|
|metricAlwaysLoadLocal|Legen Sie einen Wert ungleich Null fest, um das Debugmodul immer lokal zu laden.|
|metricLoadInDebuggeeSession|NICHT VERWENDET|
|metricLoadedByDebuggee|Legen Sie einen Wert ungleich Null fest, um anzugeben, dass das Debugmodul immer mit oder vom zu debuggenden Programm geladen wird.|
|metricAttach|Legen Sie einen Wert ungleich Null fest, um die Unterstützung für die Anlage zu vorhandenen Programmen anzugeben.|
|metricCallStackBP|Legen Sie auf ungleich Null fest, um die Unterstützung für Call-Stack-Haltepunkte anzugeben.|
|metricConditionalBP|Legen Sie einen Wert ungleich Null fest, um die Unterstützung für die Einstellung bedingter Haltepunkte anzugeben.|
|metricDataBP|Legen Sie einen Wert ungleich Null fest, um die Unterstützung für die Einstellung von Haltepunkten für Datenänderungen anzugeben.|
|metricDisassembly|Legen Sie wert auf ungleich Null fest, um die Unterstützung für die Erstellung einer Demontageliste anzugeben.|
|metricDumpWriting|Legen Sie auf ungleich Null fest, um die Unterstützung für das Dump-Schreiben anzuzeigen (das Abladen von Speicher auf ein Ausgabegerät).|
|metricENC|Legen Sie einen Wert ungleich Null fest, um die Unterstützung für Bearbeiten und Fortfahren anzuzeigen. **Hinweis:**  Ein benutzerdefiniertes Debugmodul sollte dies niemals festlegen oder immer auf 0 setzen.|
|metricAusnahmen|Legen Sie auf ungleich Null fest, um die Unterstützung für Ausnahmen anzugeben.|
|metricFunctionBP|Legen Sie einen Wert ungleich Null fest, um die Unterstützung für benannte Haltepunkte anzuzeigen (Haltepunkte, die beim Aufruf eines bestimmten Funktionsnamens umbrechen).|
|metricHitCountBP|Legen Sie einen Wert ungleich Null fest, um die Unterstützung für die Einstellung von "Trefferpunkt"-Haltepunkten anzugeben (Haltepunkte, die erst ausgelöst werden, nachdem sie eine bestimmte Anzahl von Malen getroffen wurden).|
|metricJITDebug|Legen Sie einen Wert ungleich Null fest, um die Unterstützung für Just-in-Time-Debugging anzuzeigen (der Debugger wird gestartet, wenn eine Ausnahme in einem laufenden Prozess auftritt).|
|metricMemory|NICHT VERWENDET|
|metricPortSupplier|Legen Sie diese einstellung auf die CLSID des Portlieferanten fest, wenn eine implementiert ist.|
|metricRegister|NICHT VERWENDET|
|metricSetNextStatement|Legen Sie einen Wert ungleich Null fest, um die Unterstützung für das Festlegen der nächsten Anweisung anzugeben (die die Ausführung von Zwischenanweisungen überspringt).|
|metricSuspendThread|Legen Sie einen Wert ungleich Null fest, um die Unterstützung für das Anhalten der Threadausführung anzugeben.|
|metricWarnIfNoSymbols|Legen Sie einen Wert ungleich Null fest, um anzugeben, dass der Benutzer benachrichtigt werden soll, wenn keine Symbole vorhanden sind.|
|metricProgramProvider|Legen Sie dies auf die CLSID des Programmanbieters fest.|
|metricAlwaysLoadProgramProviderLocal|Legen Sie diesen Wert auf ungleich Null fest, um anzugeben, dass der Programmanbieter immer lokal geladen werden soll.|
|metricEngineCanWatchProcess|Legen Sie diesen Wert auf ungleich Null fest, um anzugeben, dass das Debugmodul prozessereignisse anstelle des Programmanbieters beobachtet.|
|metricRemoteDebugging|Legen Sie diesen Wert auf ungleich Null fest, um die Unterstützung für Remote-Debugging anzuzeigen.|
|metricEncUseNativeBuilder|Legen Sie diesen Wert auf ungleich Null fest, um anzugeben, dass der Bearbeitungs- und Weiter-Manager die encbuild.dll des Debugmoduls verwenden soll, um für Bearbeiten und Fortfahren zu erstellen. **Hinweis:**  Ein benutzerdefiniertes Debugmodul sollte dies niemals festlegen oder immer auf 0 setzen.|
|metricLoadUnderWOW64|Legen Sie diesen Wert auf ungleich Null fest, um anzugeben, dass das Debugmodul beim Debuggen eines 64-Bit-Prozesses im Debuggee-Prozess unter WOW geladen werden soll. Andernfalls wird das Debugmodul in den Visual Studio-Prozess geladen (der unter WOW64 ausgeführt wird).|
|metricLoadProgramProviderUnderWOW64|Legen Sie diesen Wert auf ungleich Null fest, um anzugeben, dass der Programmanbieter beim Debuggen eines 64-Bit-Prozesses unter WOW in den Debuggee-Prozess geladen werden soll. Andernfalls wird es in den Visual Studio-Prozess geladen.|
|metricStopOnExceptionCrossingManagedBoundary|Legen Sie diesen Wert auf ungleich Null fest, um anzugeben, dass der Prozess beendet werden soll, wenn eine nicht behandelte Ausnahme über verwaltete/nicht verwaltete Codegrenzen hinweg ausgelöst wird.|
|metricAutoSelectPriorität|Legen Sie dies auf eine Priorität für die automatische Auswahl des Debugmoduls fest (höhere Werte entsprechen höherer Priorität).|
|metricAutoSelectIncompatibleListe|Registrierungsschlüssel, der Einträge enthält, die GUIDs für Debugmodule angeben, die bei der automatischen Auswahl ignoriert werden sollen. Bei diesen Einträgen handelt es sich um eine Zahl (0, 1, 2 usw.) mit einer GUID, die als Zeichenfolge ausgedrückt wird.|
|metricIncompatibleListe|Registrierungsschlüssel, der Einträge enthält, die GUIDs für Debugmodule angeben, die mit diesem Debugmodul nicht kompatibel sind.|
|metricDisableJITOptimization|Legen Sie diesen Wert auf ungleich Null fest, um anzugeben, dass Just-in-Time-Optimierungen (für verwalteten Code) während des Debuggens deaktiviert werden sollen.|

|Expression Evaluator Eigenschaften|BESCHREIBUNG|
|-------------------------------------|-----------------|
|metricEngine|Dies enthält die Anzahl der Debugmodule, die den angegebenen Ausdrucksevaluator unterstützen.|
|metricPreloadModules|Legen Sie diesen Wert auf ungleich Null fest, um anzugeben, dass Module vorinstalliert werden sollen, wenn ein Ausdrucksauswertungswert für ein Programm gestartet wird.|
|metricThisObjectName|Legen Sie diesen auf den Objektnamen "this" fest.|

|Expression Evaluator-Erweiterungseigenschaften|BESCHREIBUNG|
| - |-----------------|
|metricExtensionDll|Name der DLL, die diese Erweiterung unterstützt.|
|metricExtensionRegistersUnterstützt|Liste der unterstützten Register.|
|metricExtensionRegistersEntryPoint|Einstiegspunkt für den Zugriff auf Register.|
|metricExtensionTypesUnterstützt|Liste der unterstützten Typen.|
|metricExtensionTypesEntryPoint|Einstiegspunkt für den Zugriff auf Typen.|

|Port Supplier Eigenschaften|BESCHREIBUNG|
|------------------------------|-----------------|
|metricPortPickerCLSID|Die CLSID der Portauswahl (ein Dialogfeld, das der Benutzer verwenden kann, um Ports auszuwählen und Ports hinzuzufügen, die zum Debuggen verwendet werden).|
|metricDisallowUserEnteredPorts|Ein Wert ungleich Null, wenn die vom Benutzer eingegebenen Ports dem Portlieferanten nicht hinzugefügt werden können (dadurch ist das Dialogfeld Portauswahl im Wesentlichen schreibgeschützt).|
|metricPidBase|Die Basisprozess-ID, die vom Portlieferanten beim Zuweisen von Prozess-IDs verwendet wird.|

|Vordefinierte SP-Speichertypen|BESCHREIBUNG|
|-------------------------------|-----------------|
|storetypeFile|Die Symbole werden in einer separaten Datei gespeichert.|
|storetypeMetadata|Die Symbole werden als Metadaten in einer Assembly gespeichert.|

|Verschiedene Eigenschaften|BESCHREIBUNG|
|------------------------------|-----------------|
|metricShowNonUserCode|Legen Sie diesen Wert auf ungleich Null fest, um Nichtbenutzercode anzuzeigen.|
|metricJustMyCodeStepping|Legen Sie diesen Wert auf ungleich Null fest, um anzugeben, dass schrittweise Schritte nur im Benutzercode auftreten können.|
|metricCLSID|CLSID für ein Objekt eines bestimmten Metriktyps.|
|metricName|Benutzerfreundlicher Name für ein Objekt eines bestimmten Metriktyps.|
|metricSprache|Sprachname.|

## <a name="registry-locations"></a>Registrierungsspeicherorte
 Die Metriken werden aus der Registrierung gelesen und `VisualStudio` in die Registrierung geschrieben, insbesondere im Unterschlüssel.

> [!NOTE]
> Meistens werden die Metriken in den HKEY_LOCAL_MACHINE-Schlüssel geschrieben. Manchmal ist jedoch HKEY_CURRENT_USER der Zielschlüssel. Dbgmetric.lib behandelt beide Schlüssel. Wenn eine Metrik abruft, wird zuerst HKEY_CURRENT_USER gesucht, dann HKEY_LOCAL_MACHINE. Wenn eine Metrik festgelegt wird, gibt ein Parameter an, welcher Schlüssel der obersten Ebene verwendet werden soll.

 *[Registrierungsschlüssel]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[Versionsstamm]*\

 *[Metrikstamm]*\

 *[Metriktyp]*\

 *[metrisch] = [Metrikwert]*

 *[metrisch] = [Metrikwert]*

 *[metrisch] = [Metrikwert]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Registrierungsschlüssel]*|`HKEY_CURRENT_USER` oder `HKEY_LOCAL_MACHINE`|
|*[Versionsstamm]*|Die Version von Visual Studio `7.0` `7.1`(z. B. , , oder `8.0`). Dieser Stamm kann jedoch auch mit dem **Schalter /rootsuffix** zu **devenv.exe**geändert werden. Für VSIP ist dieser Modifikator in der Regel **Exp**, so dass der Versionsstamm z. B. 8.0Exp wäre.|
|*[Metrikstamm]*|Dies `AD7Metrics` ist `AD7Metrics(Debug)`entweder oder , je nachdem, ob die Debugversion von dbgmetric.lib verwendet wird. **Hinweis:**  Unabhängig davon, ob dbgmetric.lib verwendet wird, sollte diese Namenskonvention eingehalten werden, wenn Sie Unterschiede zwischen Debug- und Releaseversionen haben, die in der Registrierung widergespiegelt werden müssen.|
|*[Metriktyp]*|Der Typ der zu `Engine`schreibenden Metrik: , `ExpressionEvaluator`, `SymbolProvider`, usw. Diese sind alle wie in dbgmetric.h als `metricTypeXXXX`definiert, wobei `XXXX` der spezifische Typname ist.|
|*[metrisch]*|Der Name eines Eintrags, dem ein Wert zugewiesen werden soll, um die Metrik festzulegen. Die tatsächliche Organisation der Metriken hängt vom Metriktyp ab.|
|*[Metrikwert]*|Der der Metrik zugewiesene Wert. Der Typ, den der Wert haben soll (Zeichenfolge, Zahl usw.), hängt von der Metrik ab.|

> [!NOTE]
> Alle GUIDs werden im `{GUID}`Format von gespeichert. Beispiel: `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Debug-Engines
 Im Folgenden finden Sie die Organisation der Debugmodule-Metriken in der Registrierung. `Engine`ist der Metriktypname für ein Debugmodul und entspricht *[Metriktyp]* in der obigen Registrierungsunterstruktur.

 `Engine`\

 *[Engine guid]*\

 `CLSID` = *[Klasse guid]*

 *[metrisch] = [Metrikwert]*

 *[metrisch] = [Metrikwert]*

 *[metrisch] = [Metrikwert]*

 `PortSupplier`\

 `0` = *[Hafenlieferant guid]*

 `1` = *[Hafenlieferant guid]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Engine guid]*|Die GUID des Debugmoduls.|
|*[Klasse guid]*|Die GUID der Klasse, die dieses Debugmodul implementiert.|
|*[Hafenlieferant guid]*|Die GUID des Portanbieters, falls vorhanden. Viele Debug-Engines verwenden den Standardportlieferanten und geben daher keinen eigenen Lieferanten an. In diesem Fall ist `PortSupplier` der Unterschlüssel nicht vorhanden.|

### <a name="port-suppliers"></a>Portanbieter
 Im Folgenden finden Sie die Organisation der Portlieferantenmetriken in der Registrierung. `PortSupplier`ist der Metriktypname für einen Portlieferanten und entspricht *[Metriktyp]*.

 `PortSupplier`\

 *[Hafenlieferant guid]*\

 `CLSID` = *[Klasse guid]*

 *[metrisch] = [Metrikwert]*

 *[metrisch] = [Metrikwert]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Hafenlieferant guid]*|Die GUID des Portlieferanten|
|*[Klasse guid]*|Die GUID der Klasse, die diesen Portanbieter implementiert|

### <a name="symbol-providers"></a>Symbolanbieter
 Im Folgenden finden Sie die Organisation der Symbollieferantenmetriken in der Registrierung. `SymbolProvider`ist der Metriktypname für den Symbolanbieter und entspricht *[Metriktyp]*.

 `SymbolProvider`\

 *[Symbolanbieter guid]*\

 `file`\

 `CLSID` = *[Klasse guid]*

 *[metrisch] = [Metrikwert]*

 *[metrisch] = [Metrikwert]*

 `metadata`\

 `CLSID` = *[Klasse guid]*

 *[metrisch] = [Metrikwert]*

 *[metrisch] = [Metrikwert]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Symbolanbieter guid]*|Die GUID des Symbolanbieters|
|*[Klasse guid]*|Die GUID der Klasse, die diesen Symbolanbieter implementiert|

### <a name="expression-evaluators"></a>Ausdrucksauswertungen
 Im Folgenden finden Sie die Organisation der Ausdrucksauswertungsmetriken in der Registrierung. `ExpressionEvaluator`ist der Metriktypname für den Ausdrucksevaluator und entspricht *[Metriktyp]*.

> [!NOTE]
> Der Metriktyp für `ExpressionEvaluator` ist in dbgmetric.h nicht definiert, da davon ausgegangen wird, dass alle Metrikänderungen für Ausdrucksauswertungen die entsprechenden Ausdrucksauswertungsmetrikfunktionen durchlaufen (das Layout des `ExpressionEvaluator` Unterschlüssels ist etwas kompliziert, sodass die Details in dbgmetric.lib verborgen sind).

 `ExpressionEvaluator`\

 *[Sprach-GUID]*\

 *[Kreditor guid]*\

 `CLSID` = *[Klasse guid]*

 *[metrisch] = [Metrikwert]*

 *[metrisch] = [Metrikwert]*

 `Engine`\

 `0` = *[Debug-Engine guid]*

 `1` = *[Debug-Engine guid]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Sprach-GUID]*|Die GUID einer Sprache|
|*[Kreditor guid]*|Die GUID eines Anbieters|
|*[Klasse guid]*|Die GUID der Klasse, die diesen Ausdrucksevaluator implementiert|
|*[Debug-Engine guid]*|Die GUID eines Debugmoduls, mit dem dieser Ausdrucksauswertungswert arbeitet|

### <a name="expression-evaluator-extensions"></a>Expression Evaluator-Erweiterungen
 Im Folgenden finden Sie die Organisation der Attributauswertungserweiterungsmetriken in der Registrierung. `EEExtensions`ist der Metriktypname für die Ausdrucksauswertungserweiterungen und entspricht *[Metriktyp]*.

 `EEExtensions`\

 *[Erweiterung guid]*\

 *[metrisch] = [Metrikwert]*

 *[metrisch] = [Metrikwert]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Erweiterung guid]*|Die GUID einer Ausdrucksauswertungserweiterung|

### <a name="exceptions"></a>Ausnahmen
 Im Folgenden finden Sie die Organisation der Ausnahmemetriken in der Registrierung. `Exception`ist der Metriktypname für die Ausnahmen und entspricht *[Metriktyp]*.

 `Exception`\

 *[Debug-Engine guid]*\

 *[Ausnahmetypen]*\

 *[Ausnahme]*\

 *[metrisch] = [Metrikwert]*

 *[metrisch] = [Metrikwert]*

 *[Ausnahme]*\

 *[metrisch] = [Metrikwert]*

 *[metrisch] = [Metrikwert]*

|Platzhalter|BESCHREIBUNG|
|-----------------|-----------------|
|*[Debug-Engine guid]*|Die GUID eines Debugmoduls, das Ausnahmen unterstützt.|
|*[Ausnahmetypen]*|Ein allgemeiner Titel für den Unterschlüssel, der die Klasse der Ausnahmen identifiziert, die behandelt werden können. Typische Namen sind **C++-Ausnahmen**, **Win32-Ausnahmen**, **Common Language Runtime-Ausnahmen**und **Native Run-Time Checks**. Diese Namen werden auch verwendet, um eine bestimmte Ausnahmeklasse für den Benutzer zu identifizieren.|
|*[Ausnahme]*|Ein Name für eine Ausnahme: z. B. **_com_error** oder **Control-Break**. Diese Namen werden auch verwendet, um eine bestimmte Ausnahme für den Benutzer zu identifizieren.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Diese Dateien befinden [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] sich im SDK-Installationsverzeichnis (standardmäßig *[Laufwerk]*, Programmdateien, Microsoft\\Visual Studio 2010 SDK ).

 Kopfzeile: enthält die Überschrift .dbgmetric.h

 Bibliothek: libs-ad2de.lib, libs-dbgmetric.lib

## <a name="see-also"></a>Weitere Informationen
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
