---
title: "Debug.msTraceAsyncOperationStarting-Funktion | Microsoft Docs"
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
ms.assetid: c8458264-07e0-4cd6-8528-ff7cf009cf9e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Debug.msTraceAsyncOperationStarting-Funktion
Initiiert eine Ablaufverfolgung für einen asynchronen Vorgang.  
  
## Syntax  
  
```  
Debug.msTraceAsyncOperationStarting(operationName)  
```  
  
#### Parameter  
 `operationName`  
 Erforderlich.  Eine Zeichenfolge, die den asynchronen Vorgang bezeichnet.  Wenn `operationName` null oder nicht definiert ist, wird eine leere Zeichenfolge für den Vorgangsnamen verwendet.  
  
## Rückgabewert  
 Eine ganze Zahl, die die Vorgangs\-ID darstellt.  
  
## Hinweise  
 Rufen Sie diese Methode vor dem Starten des asynchronen Vorgangs auf.  
  
> [!NOTE]
>  Einige Debugtools zeigen nicht die Informationen an, die an den Debugger gesendet werden.  
  
## Beispiel  
 Der folgende Code enthält ein Beispiel für das Instrumentieren eines asynchronen Aufrufs für eine [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]\-App.  
  
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