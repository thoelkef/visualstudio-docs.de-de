---
title: "Debug.msTraceAsyncCallbackStarting-Funktion | Microsoft Docs"
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
ms.assetid: 0e2ca7c4-103c-44f2-b76c-102fb1e42543
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Debug.msTraceAsyncCallbackStarting-Funktion
Ordnet die Rückrufliste einem zuvor angegebenen asynchronen Vorgang zu.  
  
## Syntax  
  
```  
Debug.msTraceAsyncCallbackStarting(asyncOperationId)  
```  
  
#### Parameter  
 `asyncOperationId`  
 Erforderlich.  Die dem asynchronen Vorgang zugeordnete ID.  
  
## Hinweise  
 Rufen Sie diese Funktion in der Rückruffunktion für den asynchronen Vorgang nach dem Aufruf von `Debug.msTraceAsyncOperationCompleted` auf.  
  
> [!NOTE]
>  Einige Debugtools zeigen nicht die Informationen an, die an den Debugger gesendet werden.  
  
 `asyncOperationId` muss dem Vorgangsnamen entsprechen, der zuvor von `Debug.msTraceAsyncOperationStarting` zurückgegeben wurde.  
  
## Beispiel  
 Der folgende Code enthält ein Beispiel für das Verfolgen eines asynchronen Aufrufs für eine [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-App.  
  
```javascript  
function asyncWrapperFunction() {  
    var opID = Debug.msTraceAsyncOperationStarting('async trace');  
    doSomethingAsync().then(function (result) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_SUCCESS);  
        Debug.msTraceAsyncCallbackStarting(opID);  
        // Process result of async operation.  
    }, function (error) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_ERROR);  
        Debug.msTraceAsyncCallbackStarting(opID);  
    });  
  
    Debug.msTraceAsyncCallbackCompleted();  
}  
  
function doSomethingAsync() {  
    return WinJS.Promise.as(true);  
}  
  
asyncWrapperFunction();  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]