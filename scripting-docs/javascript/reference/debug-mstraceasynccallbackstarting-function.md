---
title: Debug.msTraceAsyncCallbackStarting-Funktion | Microsoft Docs
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
ms.assetid: 0e2ca7c4-103c-44f2-b76c-102fb1e42543
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49203cdf16e7cbd74493c882d9cf17b7629da79a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="debugmstraceasynccallbackstarting-function"></a>Debug.msTraceAsyncCallbackStarting-Funktion
Ordnet die Rückrufliste einem zuvor angegebenen asynchronen Vorgang zu.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.msTraceAsyncCallbackStarting(asyncOperationId)  
```  
  
#### <a name="parameters"></a>Parameter  
 `asyncOperationId`  
 Erforderlich. Die dem asynchronen Vorgang zugeordnete ID.  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie diese Funktion in der Rückruffunktion für den asynchronen Vorgang nach dem Aufruf von `Debug.msTraceAsyncOperationCompleted` auf.  
  
> [!NOTE]
>  Einige Debugtools zeigen nicht die Informationen an, die an den Debugger gesendet werden.  
  
 `asyncOperationId` muss dem Vorgangsnamen entsprechen, der zuvor von `Debug.msTraceAsyncOperationStarting` zurückgegeben wurde.  
  
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