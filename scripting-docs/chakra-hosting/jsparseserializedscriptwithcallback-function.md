---
title: "JsParseSerializedScriptWithCallback-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a93ecfb-4b82-4a85-b24c-6816db2332ea
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsParseSerializedScriptWithCallback-Funktion
Analysiert ein serialisiertes Skript und gibt eine Funktion zurück, die das Skript darstellt. Ermöglicht das verzögerte Laden \(Lazy Loading\) der Skriptquelle im Bedarfsfall.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsParseSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_ JsValueRef * result  
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
 Eine Funktion, die den Skriptcode darstellt.  
  
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