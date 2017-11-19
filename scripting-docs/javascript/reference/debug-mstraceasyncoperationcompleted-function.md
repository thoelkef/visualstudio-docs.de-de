---
title: Debug.msTraceAsyncOperationCompleted-Funktion | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 9b628b71-61f1-478a-857f-5e1f607db56c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41370257042a2de50d21eba51c299198a6bfb72a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="debugmstraceasyncoperationcompleted-function"></a>Debug.msTraceAsyncOperationCompleted-Funktion
Gibt an, dass ein asynchroner Vorgang abgeschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.msTraceAsyncOperationCompleted(asyncOperationId, status)  
```  
  
#### <a name="parameters"></a>Parameter  
 `asyncOperationId`  
 Erforderlich. Die einem asynchronen Vorgang zugeordnete ID.  
  
 `status`  
 Dies ist optional. Der Status des asynchronen Vorgangs. Wenn dieser nicht angegeben wurde, wird `Debug.MS_ASYNC_OP_STATUS_SUCCESS` verwendet.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie diese Funktion auf, wenn der asynchrone Vorgang abgeschlossen wird.  
  
 `asyncOperationId` muss der Vorgangs-ID entsprechen, die zuvor von `Debug.msTraceAsyncOperationStarting` zurückgegeben wurde.  
  
 Zu den möglichen Werten für `status` zählen:  
  
-   `Debug.MS_ASYNC_OP_STATUS_SUCCESS`  
  
-   `Debug.MS_ASYNC_OP_STATUS_CANCELED`  
  
-   `Debug.MS_ASYNC_OP_STATUS_ERROR`  
  
> [!NOTE]
>  Einige Debugtools zeigen nicht die Informationen an, die an den Debugger gesendet werden.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code enthält ein Beispiel für das Verfolgen eines asynchronen Aufrufs für eine [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]-App.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]