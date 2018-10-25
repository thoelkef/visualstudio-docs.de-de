---
title: SDK-Hilfsprogramme für das Debuggen | Microsoft-Dokumentation
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
ms.openlocfilehash: d352e22b95540cfc1901eb214c2d5180b6024f27
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821525"
---
# <a name="sdk-helpers-for-debugging"></a>SDK-Hilfsprogramme für das Debuggen
Diese Funktionen und Deklarationen sind globale Hilfsfunktionen für die Implementierung von Debug-Engines, ausdrucksauswertung und Symbol-Anbieter in C++.  
  
> [!NOTE]
>  Es gibt keine verwalteten Versionen dieser Funktionen und-Deklarationen zu diesem Zeitpunkt.  
  
## <a name="overview"></a>Übersicht  
 In der Reihenfolge für die Debug-Engines, ausdrucksauswertung und Symbol-Anbieter von Visual Studio verwendet werden müssen sie registriert werden. Dies erfolgt durch Festlegen von Registrierungsunterschlüsseln und Einträge, auch bekannt als "Einstellung Metriken". Die folgenden globalen Funktionen dienen, den Prozess der Aktualisierung dieser Metriken zu vereinfachen. Finden Sie im Abschnitt Registrierungspfaden das Layout der einzelnen Registrierungsunterschlüssel finden, die von diesen Funktionen aktualisiert wird.  
  
## <a name="general-metric-functions"></a>Allgemeine Metrik Funktionen  
 Hierbei handelt es sich um allgemeine Funktionen, die von der Debug-Engines verwendet. Die spezialisierte Funktionen für die ausdrucksauswertung und Symbol-Anbieter werden weiter unten beschrieben.  
  
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
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|pszMachine|[in] Name eines möglicherweise Remotecomputers, deren Registrierung geschrieben (`NULL` bedeutet lokalen Computer).|  
|pszType|[in] Einer der Typen metrischen.|  
|guidSection|[in] GUID des einer bestimmten-Engine, die ausdrucksauswertung, die Ausnahme, die usw. Gibt einen Unterabschnitt einer Metrik Typs für ein bestimmtes Element an.|  
|pszMetric|[in] Die Metrik abgerufen werden sollen. Dies entspricht einem bestimmten Wertnamen.|  
|pdwValue|[in] Der Speicherort des Werts aus der Metrik. Es gibt verschiedene Arten von GetMetric, die einen DWORD-Wert (wie in diesem Beispiel), einen BSTR-Wert, eine GUID oder ein Array von GUIDs zurückgeben kann.|  
|pszAltRoot|[in] Eine alternative Registrierungsstamm verwendet wird. Legen Sie auf `NULL` , wenn der Standardwert verwendet.|  
  
### <a name="setmetric-method"></a>SetMetric-Methode  
 Den angegebenen Wert für die Metrik festgelegt in der Registrierung.  
  
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
|pszType|[in] Einer der Typen metrischen.|  
|guidSection|[in] GUID des einer bestimmten-Engine, die ausdrucksauswertung, die Ausnahme, die usw. Gibt einen Unterabschnitt einer Metrik Typs für ein bestimmtes Element an.|  
|pszMetric|[in] Die Metrik abgerufen werden sollen. Dies entspricht einem bestimmten Wertnamen.|  
|dwValue|[in] Der Speicherort des Werts in der Metrik. Es gibt verschiedene Arten von SetMetric, die einen DWORD-Wert (in diesem Beispiel), einen BSTR-Wert, eine GUID oder ein Array von GUIDs speichern können.|  
|fUserSpecific|[in] "True", wenn die Metrik spezifisch sind und es in die Struktur des Benutzers anstelle der Struktur des lokalen Computers geschrieben werden soll.|  
|pszAltRoot|[in] Eine alternative Registrierungsstamm verwendet wird. Legen Sie auf `NULL` , wenn der Standardwert verwendet.|  
  
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
|pszType|[in] Einer der Typen metrischen.|  
|guidSection|[in] GUID des einer bestimmten-Engine, die ausdrucksauswertung, die Ausnahme, die usw. Gibt einen Unterabschnitt einer Metrik Typs für ein bestimmtes Element an.|  
|pszMetric|[in] Die Metrik, die entfernt werden. Dies entspricht einem bestimmten Wertnamen.|  
|pszAltRoot|[in] Eine alternative Registrierungsstamm verwendet wird. Legen Sie auf `NULL` , wenn der Standardwert verwendet.|  
  
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
|pszMachine|[in] Name eines möglicherweise Remotecomputers, deren Registrierung geschrieben (`NULL` bedeutet lokalen Computer).|  
|pszType|[in] Einer der Typen metrischen.|  
|rgguidSections|[in, out] Vorab zugeordnete Array von GUIDs gefüllt werden soll.|  
|pdwSize|[in] Die maximale Anzahl von GUIDs, die in gespeichert werden, können die `rgguidSections` Array.|  
|pszAltRoot|[in] Eine alternative Registrierungsstamm verwendet wird. Legen Sie auf `NULL` , wenn der Standardwert verwendet.|  
  
## <a name="expression-evaluator-functions"></a>Expression Evaluator-Funktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|GetEEMetric|Ruft einen Metrikwert aus der Registrierung ab.|  
|SetEEMetric|Den angegebenen Wert für die Metrik festgelegt in der Registrierung.|  
|RemoveEEMetric|Entfernt die angegebene Metrik aus der Registrierung.|  
|GetEEMetricFile|Ruft einen Dateinamen aus die angegebene Metrik und geladen, den Inhalt der Datei als Zeichenfolge zurückgegeben.|  
  
## <a name="exception-functions"></a>Ausnahme-Funktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|GetExceptionMetric|Ruft einen Metrikwert aus der Registrierung ab.|  
|SetExceptionMetric|Den angegebenen Wert für die Metrik festgelegt in der Registrierung.|  
|RemoveExceptionMetric|Entfernt die angegebene Metrik aus der Registrierung.|  
|RemoveAllExceptionMetrics|Entfernt alle Ausnahme Metriken aus der Registrierung.|  
  
## <a name="symbol-provider-functions"></a>Symbol-Anbieter-Funktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|GetSPMetric|Ruft einen Metrikwert aus der Registrierung ab.|  
|SetSPMetric|Den angegebenen Wert für die Metrik festgelegt in der Registrierung.|  
|RemoveSPMetric|Entfernt die angegebene Metrik aus der Registrierung.|  
  
## <a name="enumeration-functions"></a>Enumerationsfunktionen  
  
|Funktion|Beschreibung|  
|--------------|-----------------|  
|EnumMetricSections|Listet alle Metriken für einen angegebenen Metrik.|  
|EnumDebugEngine|Listet die registrierten Debug-Engines.|  
|EnumEEs|Listet die registrierten ausdrucksauswertungen.|  
|EnumExceptionMetrics|Listet alle Metriken der Ausnahme an.|  
  
## <a name="metric-definitions"></a>Metrikdefinitionen  
 Diese Definitionen können für Namen von vordefinierten Metriken verwendet werden. Die Namen entsprechen, verschiedene Registrierungsschlüssel, Wertnamen und werden als Breitzeichen-Zeichenfolgen definiert: z. B. `extern LPCWSTR metrictypeEngine`.  
  
|Vordefinierte Metriktypen|Beschreibung: Der CodeBase-Schlüssel für...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Alle debug-Engine-Metriken.|  
|metrictypePortSupplier|Alle Metriken für die Port-Lieferanten.|  
|metrictypeException|Alle Metriken für Ausnahme.|  
|metricttypeEEExtension|Alle Expression Evaluator-Erweiterungen.|  
  
|Debug-Engine-Eigenschaften|Beschreibung|  
|-----------------------------|-----------------|  
|metricAddressBP|Um die Unterstützung für Adressenhaltepunkte ungleich NULL festgelegt.|  
|metricAlwaysLoadLocal|Legen Sie auf ungleich NULL, um immer die Debug-Engine lokal zu laden.|  
|metricLoadInDebuggeeSession|NICHT VERWENDET|  
|metricLoadedByDebuggee|Legen Sie auf ungleich NULL, um anzugeben, dass die Debug-Engine immer mit oder durch das derzeit debuggte Programm geladen wird.|  
|metricAttach|Legen Sie auf ungleich NULL, um die Unterstützung für die Anlage auf vorhandene Programme.|  
|metricCallStackBP|Legen Sie auf ungleich NULL, um die Unterstützung für Call Stack Haltepunkte.|  
|metricConditionalBP|Legen Sie auf ungleich NULL, um die Unterstützung für die Einstellung von bedingter Haltepunkte.|  
|metricDataBP|Um die Unterstützung für die Einstellung von Haltepunkten auf Änderungen an Daten ungleich NULL festgelegt.|  
|metricDisassembly|Legen Sie zu ungleich NULL, um die Unterstützung für die Herstellung einer Disassembly-Auflistung.|  
|metricDumpWriting|Legen Sie auf ungleich NULL, um die Unterstützung für Dump schreiben (die Sicherung der Arbeitsspeicher, um ein Ausgabegerät).|  
|metricENC|Legen Sie zu ungleich NULL, um die Unterstützung für bearbeiten und fortfahren. **Hinweis:** eine benutzerdefinierten Debug-Engine nie legen Sie hier, oder muss immer auf 0 festgelegt.|  
|metricExceptions|Um die Unterstützung für Ausnahmen, die ungleich NULL festgelegt.|  
|metricFunctionBP|Legen Sie auf ungleich NULL, Unterstützung für benannte Haltepunkte (Breakpoints, die unterbrochen, wenn Namen in einer bestimmten Funktion aufgerufen wird).|  
|metricHitCountBP|Legen Sie auf ungleich NULL, Unterstützung für die Einstellung "Triff Punkt" Haltepunkte (Breakpoints, die ausgelöst werden, nachdem eine bestimmte Anzahl von Malen wird erreicht).|  
|metricJITDebug|Legen Sie zu ungleich NULL, um Unterstützung für die just-in-Time-Debuggen (der Debugger wird gestartet, tritt eine Ausnahme in einem laufenden Prozess) anzugeben.|  
|metricMemory|NICHT VERWENDET|  
|metricPortSupplier|Legen Sie diese auf die CLSID des portbereitstellers, wenn eine implementiert wird.|  
|metricRegisters|NICHT VERWENDET|  
|metricSetNextStatement|Legen Sie auf ungleich NULL, Unterstützung für das Festlegen der nächsten Anweisung (die Ausführung von intermediate-Anweisungen wird übersprungen) angeben.|  
|metricSuspendThread|Legen Sie auf ungleich NULL, um die Unterstützung zum Anhalten der Ausführung des Threads.|  
|metricWarnIfNoSymbols|Legen Sie auf ungleich NULL, um anzugeben, dass der Benutzer benachrichtigt werden soll, wenn keine Symbole vorhanden sind.|  
|metricProgramProvider|Legen Sie diese auf die CLSID des Programm-Anbieters.|  
|metricAlwaysLoadProgramProviderLocal|Legen Sie diese Einstellung zu ungleich NULL, um anzugeben, dass der Anbieter für die Anwendung immer lokal geladen werden soll.|  
|metricEngineCanWatchProcess|Legen Sie den ungleich NULL, um anzugeben, dass die Debug-Engine für die Verarbeitung von Ereignissen anstelle des Anbieters der Anwendung überwacht.|  
|metricRemoteDebugging|Legen Sie diese um die Unterstützung für das Remotedebuggen ungleich NULL.|  
|metricEncUseNativeBuilder|Legen Sie diese Einstellung zu ungleich NULL, um anzugeben, dass die Debug-Engine encbuild.dll den bearbeiten und Fortfahren-Manager zum Erstellen für bearbeiten und Fortfahren verwenden werden soll. **Hinweis:** eine benutzerdefinierten Debug-Engine nie legen Sie hier, oder muss immer auf 0 festgelegt.|  
|metricLoadUnderWOW64|Legen Sie den Wert ungleich NULL, um anzugeben, dass die Debug-Engine an, die im zu debuggenden Prozess unter WOW soll, beim Debuggen von 64-Bit-Prozess geladen werden; Andernfalls wird die Debug-Engine in Visual Studio-Prozesses geladen werden (der unter WOW64 ausgeführt wird).|  
|metricLoadProgramProviderUnderWOW64|Legen Sie diese Einstellung um anzugeben, dass der Anbieter der Anwendung im zu debuggenden Prozess geladen, beim Debuggen von 64-Bit-Prozess unter WOW werden soll ungleich null; Andernfalls wird es in Visual Studio-Prozesses geladen.|  
|metricStopOnExceptionCrossingManagedBoundary|Legen Sie diese um anzugeben, dass der Prozess beendet werden soll, wenn eine nicht behandelte Ausnahme, über die Grenzen von verwaltetem/nicht verwaltetem Code ausgelöst wird ungleich NULL.|  
|metricAutoSelectPriority|Legen Sie diese Option, um eine Priorität für die automatische Auswahl des Debug-Engine (höhere Werte gleich höhere Priorität).|  
|metricAutoSelectIncompatibleList|Der Registrierungsschlüssel mit Einträgen, die GUIDs für Debug-Engines, ignoriert werden sollen in die automatische Auswahl angeben. Diese Einträge sind eine Zahl (0, 1, 2 und So weiter) mit einer GUID als Zeichenfolge ausgedrückt.|  
|metricIncompatibleList|Der Registrierungsschlüssel, der Einträge, die GUIDs für die Debug-Engines angeben, die mit diesem Debug-Engine nicht kompatibel sind.|  
|metricDisableJITOptimization|Legen Sie den ungleich NULL, um anzugeben, dass die just-in-Time-Optimierungen (bei verwaltetem Code) beim Debuggen deaktiviert werden soll.|  
  
|Ausdrucksauswertungsfehler Ausdruckseigenschaften|Beschreibung|  
|-------------------------------------|-----------------|  
|metricEngine|Dies enthält die Anzahl der Debug-Engines, die die angegebenen ausdrucksauswertung unterstützt.|  
|metricPreloadModules|Legen Sie den ungleich NULL, um anzugeben, dass Module geladen werden sollen, wenn eine ausdrucksauswertung, die für ein Programm gestartet wird.|  
|metricThisObjectName|Legen Sie diese Option, die "this" Objektnamens.|  
  
|Expression Evaluator-Erweiterungseigenschaften|Beschreibung|  
| - |-----------------|  
|metricExtensionDll|Der Name der Dll, die diese Erweiterung unterstützt.|  
|metricExtensionRegistersSupported|Die Liste der Register unterstützt.|  
|metricExtensionRegistersEntryPoint|Der Einstiegspunkt für den Zugriff auf registriert.|  
|metricExtensionTypesSupported|Die Liste der unterstützten Typen.|  
|metricExtensionTypesEntryPoint|Der Einstiegspunkt für den Zugriff auf Typen.|  
  
|Eigenschaften für Lieferanten|Beschreibung|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|Die CLSID des der Port-Auswahl (ein Dialogfeld, das der Benutzer kann zum Auswählen von Ports und Hinzufügen von Ports für die Verwendung für das Debuggen verwenden).|  
|metricDisallowUserEnteredPorts|Ungleich NULL, wenn die Ports der freien Eingabe an den Lieferanten Port hinzugefügt werden können (Dadurch wird das Dialogfeld für Port-Auswahl im Wesentlichen schreibgeschützt).|  
|metricPidBase|Die Basis-Prozess-ID, die vom Lieferanten Port verwendet wird, wenn die Prozess-IDs zuordnen.|  
  
|Vordefinierte SP-Store-Typen|Beschreibung|  
|-------------------------------|-----------------|  
|storetypeFile|Die Symbole werden in einer separaten Datei gespeichert.|  
|storetypeMetadata|Die Symbole werden als Metadaten in einer Assembly gespeichert.|  
  
|Verschiedene sonstige Eigenschaften|Beschreibung|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Legen Sie den anzuzeigenden Nonuser Code ungleich NULL.|  
|metricJustMyCodeStepping|Legen Sie den ungleich NULL, um anzugeben, dass die schrittweise Ausführung nur im Benutzercode auftreten kann.|  
|metricCLSID|Die CLSID für ein Objekt eines bestimmten Typs für die Metrik.|  
|"Metricname"|Benutzerfreundlicher Name für ein Objekt eines bestimmten Typs für die Metrik.|  
|metricLanguage|Name der Sprache.|  
  
## <a name="registry-locations"></a>Registrierung  
 Die Metriken aus gelesen und geschrieben, um die Registrierung in der `VisualStudio` Unterschlüssel.  
  
> [!NOTE]
>  In den meisten Fällen, werden die Metriken auf dem Schlüssel HKEY_LOCAL_MACHINE geschrieben. In einigen Fällen allerdings wird HKEY_CURRENT_USER der Ziel-Schlüssel sein. Dbgmetric.lib behandelt beide Schlüssel. Wenn eine Metrik zu erhalten, sucht es HKEY_CURRENT_USER zuerst, dann HKEY_LOCAL_MACHINE. Wenn sie eine Metrik festlegen, ist, wird ein Parameter der obersten Ebene Schlüssels zu.  
  
 *[Registrierungsschlüssel]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[Version Root]*\  
  
 *[Metrik Root]*\  
  
 *[Metriktyp]*\  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Registrierungsschlüssel]*|`HKEY_CURRENT_USER` oder `HKEY_LOCAL_MACHINE`.|  
|*[Version Root]*|Die Version von Visual Studio (z. B. `7.0`, `7.1`, oder `8.0`). Jedoch diesem Stamm kann auch geändert werden mithilfe der **/rootsuffix** wechseln Sie zur **devenv.exe**. Für VSIP, dieser Modifizierer ist in der Regel **"exp"**, sodass das Stammverzeichnis für die Version, z. B. 8.0Exp wäre.|  
|*[Metrik Root]*|Dies ist entweder `AD7Metrics` oder `AD7Metrics(Debug)`, abhängig davon, ob die Debugversion von dbgmetric.lib verwendet wird. **Hinweis:** , und zwar unabhängig davon, ob dbgmetric.lib verwendet wird, diese Namenskonvention sollte eingehalten werden, wenn Sie die Unterschiede zwischen Debug- und Releaseversionen haben-Versionen, die in der Registrierung berücksichtigt werden müssen.|  
|*[Metriktyp]*|Der Typ des zu schreibenden Metrik: `Engine`, `ExpressionEvaluator`, `SymbolProvider`usw. Diese sind alle definiert, wie dbgmetric.h als `metricTypeXXXX`, wobei `XXXX` ist der Name der spezifischen Typ.|  
|*[Metrik]*|Der Name eines Eintrags, der ein Wert zugewiesen werden, um die Metrik festlegen. Die tatsächlichen Organisation der Metriken, hängt von den Metriktyp ab.|  
|*[Metrikwert]*|Der Wert, der die Metrik zugewiesen wird. Der Typ, der den Wert (Zeichenfolge, Zahl, usw.) haben soll, hängt von der Metrik ab.|  
  
> [!NOTE]
>  Alle GUIDs werden gespeichert, in das Format der `{GUID}`. Beispielsweise `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Debug-Engines  
 Im folgenden finden die Organisation der Debug-Engines Metriken in der Registrierung. `Engine` Um der metrischen Typnamen für eine Debug-Engine und entspricht *[Metriktyp]* in der Registrierungsteilstruktur der oben genannten.  
  
 `Engine`\  
  
 *[-Engine-Guid]*\  
  
 `CLSID` = *[Klassen-Guid]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 `PortSupplier`\  
  
 `0` = *[Port Lieferanten Guid]*  
  
 `1` = *[Port Lieferanten Guid]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[-Engine-Guid]*|Die GUID der Debug-Engine.|  
|*[Klassen-Guid]*|Die GUID der Klasse, die diese Debug-Engine implementiert.|  
|*[Port Lieferanten Guid]*|Die GUID des portbereitstellers, sofern vorhanden. Viele Debug-Engines verwenden den Standard-Anschlusslieferanten und aus diesem Grund sollten Sie keinen eigenen Lieferanten. In diesem Fall ist der Unterschlüssel `PortSupplier` ist nicht vorhanden.|  
  
### <a name="port-suppliers"></a>Portanbieter  
 Im folgenden finden die Organisation der Port Lieferanten Metriken in der Registrierung. `PortSupplier` der Metrik Name eines portanbieters ist und Sie entspricht *[Metriktyp]*.  
  
 `PortSupplier`\  
  
 *[Port Lieferanten Guid]*\  
  
 `CLSID` = *[Klassen-Guid]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Port Lieferanten Guid]*|Die GUID des portbereitstellers|  
|*[Klassen-Guid]*|Die GUID der Klasse, die diesem Port Lieferanten implementiert|  
  
### <a name="symbol-providers"></a>Symbol-Anbieter  
 Im folgenden finden die Organisation der Metriken Lieferanten Symbol in der Registrierung. `SymbolProvider` Um der Metriktyp Namen für die symbolanbieter und entspricht *[Metriktyp]*.  
  
 `SymbolProvider`\  
  
 *[Symbol-Anbieter-Guid]*\  
  
 `file`\  
  
 `CLSID` = *[Klassen-Guid]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 `metadata`\  
  
 `CLSID` = *[Klassen-Guid]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Symbol-Anbieter-Guid]*|Die GUID des Anbieters symbol|  
|*[Klassen-Guid]*|Die GUID der Klasse, die diesem symbolanbieter implementiert.|  
  
### <a name="expression-evaluators"></a>Ausdrucksauswertungen  
 Im folgenden finden die Organisation der Expression Evaluator Metriken in der Registrierung. `ExpressionEvaluator` Um der Metriktyp-Namen für die ausdrucksauswertung und entspricht *[Metriktyp]*.  
  
> [!NOTE]
>  Den Metriktyp für `ExpressionEvaluator` ist in dbgmetric.h, nicht definiert, da davon ausgegangen wird, dass die entsprechenden Ausdruck Ausdrucksauswertungsfehler Metrik Funktionen alle metrikänderungen für ausdrucksauswertungen durchlaufen werden (das Layout der `ExpressionEvaluator` Unterschlüssel ist ein wenig kompliziert, damit die Details in dbgmetric.lib ausgeblendet sind).  
  
 `ExpressionEvaluator`\  
  
 *[Guid der Sprache]*\  
  
 *[Anbieter-Guid]*\  
  
 `CLSID` = *[Klassen-Guid]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 `Engine`\  
  
 `0` = *[Debug-Engine-Guid]*  
  
 `1` = *[Debug-Engine-Guid]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Guid der Sprache]*|Die GUID einer Sprache|  
|*[Anbieter-Guid]*|Die GUID eines Anbieters|  
|*[Klassen-Guid]*|Die GUID der Klasse, die diese ausdrucksauswertung implementiert.|  
|*[Debug-Engine-Guid]*|Die GUID einer Debug-Engine, der mit diesem ausdrucksauswertung funktioniert|  
  
### <a name="expression-evaluator-extensions"></a>Expression Evaluator-Erweiterungen  
 Im folgenden finden die Organisation der Expression Evaluator-Erweiterung Metriken in der Registrierung. `EEExtensions` Um der Metriktyp Namen für den Ausdruck Evaluator-Erweiterungen und entspricht *[Metriktyp]*.  
  
 `EEExtensions`\  
  
 *[Erweiterung Guid]*\  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Erweiterung Guid]*|Die GUID einer Expression Evaluator-Erweiterung|  
  
### <a name="exceptions"></a>Ausnahmen  
 Im folgenden finden die Organisation der Metriken Ausnahmen in der Registrierung. `Exception` Um der Metriktyp Namen für die Ausnahmen und entspricht *[Metriktyp]*.  
  
 `Exception`\  
  
 *[Debug-Engine-Guid]*\  
  
 *[Ausnahmetypen]*\  
  
 *[Exception]*\  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Exception]*\  
  
 *[Metrik] = [Metrikwert]*  
  
 *[Metrik] = [Metrikwert]*  
  
|Platzhalter|Beschreibung|  
|-----------------|-----------------|  
|*[Debug-Engine-Guid]*|Die GUID einer Debug-Engine, die Ausnahmen unterstützt.|  
|*[Ausnahmetypen]*|Ein allgemeiner Titel für den Unterschlüssel, identifiziert die Klasse von Ausnahmen, die verarbeitet werden können. Typische Namen sind **C++-Ausnahmen**, **Win32-Ausnahmen**, **Common Language Runtime-Ausnahmen**, und **systemeigene Laufzeitüberprüfungen**. Diese Namen werden auch verwendet, um eine bestimmte Klasse der Ausnahme, die dem Benutzer zu identifizieren.|  
|*[Exception]*|Einen Namen für eine Ausnahme: z. B. **_com_error** oder **STRG + UNTBR**. Diese Namen werden auch verwendet, um eine bestimmte Ausnahme an den Benutzer zu identifizieren.|  
  
## <a name="requirements"></a>Anforderungen  
 Diese Dateien befinden sich der [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK-Installationsverzeichnis (standardmäßig *[Laufwerk]* \Programme\Microsoft Visual Studio 2010 SDK\\).  
  
 Header: includes\dbgmetric.h  
  
 -Bibliothek: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Siehe auch  
 [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)