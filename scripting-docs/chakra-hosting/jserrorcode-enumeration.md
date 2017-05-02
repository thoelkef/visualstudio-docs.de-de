---
title: "JsErrorCode-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsErrorCode"
helpviewer_keywords: 
  - "JsErrorCode-Enumeration"
ms.assetid: 4902f3f3-47a5-4e74-9c29-f96eeecbcda9
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsErrorCode-Enumeration
Ein Fehlercode, der von einer Chakra\-Hosting\-API zurückgegeben wird.  
  
## Syntax  
  
```  
enum JsErrorCode : unsigned int;  
```  
  
## Mitglieder  
  
### Werte  
  
|Name|Beschreibung|  
|----------|------------------|  
|`JsErrorAlreadyDebuggingContext`|Der Kontext kann nicht in einen Debuggingzustand versetzt werden, da er diesen bereits aufweist.|  
|`JsErrorAlreadyProfilingContext`|Der Kontext kann die Profilerstellung nicht beginnen, da er sie bereits ausführt.|  
|`JsErrorArgumentNotObject`|Eine Hosting\-API, die für Objektwerte gilt, wurde nicht mit einem Objektwert aufgerufen.|  
|`JsErrorBadSerializedScript`|Ein ungültiges serialisiertes Skript wurde verwendet, oder das serialisierte Skript wurde von einer anderen Version der Chakra\-Engine serialisiert.|  
|`JsErrorCannotDisableExecution`|Die Laufzeit unterstützt keine zuverlässige Skriptunterbrechung.|  
|`JsErrorCannotSerializeDebugScript`|Skripts können nicht in Debuggingkontexten serialisiert werden.|  
|`JsErrorCategoryEngine`|Kategorie von Fehlern, die sich auf Fehler in der Engine selbst bezieht.|  
|`JsErrorCategoryFatal`|Kategorie von Fehlern, die schwerwiegend sind und auf einen Fehler in der Engine hinweisen.|  
|`JsErrorCategoryScript`|Kategorie von Fehlern, die sich auf Fehler in einem Skript bezieht.|  
|`JsErrorCategoryUsage`|Kategorie von Fehlern, die sich auf die falsche Verwendung der API selbst beziehen.|  
|`JsErrorFatal`|Ein schwerwiegender Fehler ist in der Engine aufgetreten.|  
|`JsErrorHeapEnumInProgress`|Eine Heapenumeration wird gerade im Skriptkontext ausgeführt.|  
|`JsErrorIdleNotEnabled`|Eine Benachrichtigung über Leerlauf wird ausgegeben, wenn der Host die Leerlaufverarbeitung nicht aktiviert hat.|  
|`JsErrorInDisabledState`|Die Laufzeit ist in einem deaktivierten Zustand.|  
|`JsErrorInExceptionState`|Das Modul ist in einem Ausnahmezustand, und es können keine APIs aufgerufen werden, bis die Ausnahme gelöscht wurde.|  
|`JsErrorInObjectBeforeCollectCallback`|Der Vorgang wird in einem Objekt vor dem Erfassen des Rückrufs nicht unterstützt.<br /><br /> Dieser Enumerationswert wird nur im Edge\-Modus unterstützt.|  
|`JsErrorInProfileCallback`|Ein Skriptkontext befindet sich gerade in einem Profilrückruf.|  
|`JsErrorInThreadServiceCallback`|Ein Threaddienstrückruf wird gerade ausgeführt.|  
|`JsErrorInvalidArgument`|Ein Argument für eine Hosting\-API war ungültig.|  
|`JsErrorNoCurrentContext`|Die Hosting\-API erfordert, dass ein Kontext aktuell ist, aber es gibt keinen aktuellen Kontext.|  
|`JsErrorNotImplemented`|Eine Hosting\-API ist noch nicht implementiert.|  
|`JsErrorNullArgument`|Ein Argument für eine Hosting\-API war in einem Kontext NULL, obwohl NULL\-Werte nicht zulässig sind.|  
|`JsErrorObjectNotInspectable`|Objekt kann nicht in einen `IInspectable`\-Zeiger entpackt werden.<br /><br /> Dieser Enumerationswert wird nur im Edge\-Modus unterstützt.|  
|`JsErrorOutOfMemory`|Die Chakra\-Engine hat nicht mehr genügend Arbeitsspeicher.|  
|`JsErrorPropertyNotSymbol`|Eine Hosting\-API, die für Symboleigenschafts\-IDs ausgeführt werden kann, jedoch von einer Nicht\-Symboleigenschafts\-ID aufgerufen wurde. Der Fehlercode wird von `JsGetSymbolFromPropertyId` zurückgegeben, wenn die Funktion mit einer Nicht\-Symboleigenschafts\-ID aufgerufen wird.<br /><br /> Dieser Enumerationswert wird nur im Edge\-Modus unterstützt.|  
|`JsErrorPropertyNotString`|Eine Hosting\-API, die für Zeichenfolgeneigenschafts\-IDs ausgeführt werden kann, jedoch von einer Nicht\-Zeichenfolgeneigenschafts\-ID aufgerufen wurde. Der Fehlercode wird von `JsGetPropertyNamefromId` zurückgegeben, wenn die Funktion mit einer Nicht\-Zeichenfolgeneigenschafts\-ID aufgerufen wird.<br /><br /> Dieser Enumerationswert wird nur im Edge\-Modus unterstützt.|  
|`JsErrorRuntimeInUse`|Eine Laufzeit, die noch verwendet wird, kann nicht verworfen werden.|  
|`JsErrorScriptCompile`|Fehler bei JavaScript\-Kompilierung.|  
|`JsErrorScriptEvalDisabled`|Ein Skript wurde beendet, da es versucht hat, `eval` oder `function` zu verwenden, und "eval" deaktiviert wurde.|  
|`JsErrorScriptException`|Eine JavaScript\-Ausnahme ist beim Ausführen eines Skripts aufgetreten.|  
|`JsErrorScriptTerminated`|Ein Skript wurde aufgrund einer Anforderung zum Anhalten einer Laufzeit beendet.|  
|`JsErrorWrongRuntime`|Eine Hosting\-API wurde mit einem auf einer anderen JavaScript\-Laufzeit erstellten Objekt aufgerufen.|  
|`JsErrorWrongThread`|Eine Hosting\-API wurde im falschen Thread aufgerufen.|  
|`JsNoError`|Code für erfolgreiche Ausführung.|  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)