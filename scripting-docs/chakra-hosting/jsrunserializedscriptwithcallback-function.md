---
title: "JsRunSerializedScriptWithCallback-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0608d778-f65b-4dc5-a745-364aac57ef59
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsRunSerializedScriptWithCallback-Funktion
Führt ein serialisiertes Skript aus. Ermöglicht das verzögerte Laden \(Lazy Loading\) der Skriptquelle im Bedarfsfall.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_opt_ JsValueRef *result  
);  
  
```  
  
#### Parameter  
 `scriptLoadCallback`  
 Ein Rückruf, der aufgerufen wird, wenn der Quellcode des Skripts geladen werden muss.  
  
 `scriptUnloadCallback`  
 Ein Rückruf, der aufgerufen wird, wenn das serialisierte Skript und der Quellcode nicht mehr benötigt werden.  
  
 `buffer`  
 Das serialisierte Skript.  
  
 `sourceContext`  
 Ein Cookie, das das Skript identifiziert, das von debugfähigen Skriptkontexten verwendet werden kann. Dieser Kontext wird an scriptLoadCallback und scriptUnloadCallback übergeben.  
  
 `sourceUrl`  
 Der Speicherort, aus dem das Skript stammt.  
  
 `result`  
 Das Ergebnis der Skriptausführung, falls vorhanden. Dieser Parameter kann NULL sein.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
  
> [!NOTE]
>  Diese API ist noch nicht für Store\-Apps verfügbar.  
  
 Erfordert einen Active Script\-Kontext.  
  
 Die Laufzeit hält an den Pufferdaten fest, bis alle Instanzen der vom Puffer erstellten Funktionen durch die Garbage Collection bereinigt wurden.  Anschließend wird scriptUnloadCallback aufgerufen, um den Aufrufer darüber zu informieren, dass die Freigabe sicher ist.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)