---
title: "Debug-Konstanten | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Debug-Konstanten
Debugkonstanten geben konstante Werte zurück, die Eigenschaften des `Debug`\-Objekts sind.  
  
## Konstanten des Debugobjekts  
 In der folgenden Tabelle sind konstante Werte aufgelistet, bei denen es sich um Eigenschaften des [Debugobjekts](../../javascript/reference/debug-object-javascript.md) handelt.  
  
|Konstante|Beschreibung|Wert|  
|---------------|------------------|----------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|Die synchrone Arbeitsaufgabe wies einen Rückruf oder eine Fortsetzung zu, die von einem asynchronen Vorgang ausgeführt wird.|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|Die synchrone Arbeitsaufgabe erfüllt einen Teil eines asynchronen Join\-Vorgangs.|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|Die synchrone Arbeitsaufgabe erfüllt einen asynchronen Auswahlvorgang.|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|Die synchrone Arbeitsaufgabe wurde storniert.|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|Die synchrone Arbeitsaufgabe hat einen Fehler in einem asynchronen Vorgang verursacht.|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|Der asynchrone Vorgang war erfolgreich.|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|Der asynchrone Vorgang wurde abgebrochen.|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|Der asynchrone Vorgang verursachte einen Fehler.|3|  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Siehe auch  
 [Debug.msTraceAsyncOperationCompleted\-Funktion](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Debug.msUpdateAsyncCallbackRelation\-Funktion](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)