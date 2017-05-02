---
title: "Debug.msUpdateAsyncCallbackRelation-Funktion | Microsoft Docs"
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
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Debug.msUpdateAsyncCallbackRelation-Funktion
Aktualisiert den Beziehungsstatus zwischen einer synchronen Arbeitsaufgabe und dem zugeordneten asynchronen Vorgang.  
  
## Syntax  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### Parameter  
 `relatedAsyncOperationId`  
 Erforderlich.  Die dem asynchronen Vorgang zugeordnete ID.  
  
 `relationType`  
 Dies ist optional.  Der Wert, der den Beziehungsstatus angibt.  
  
## Hinweise  
 Die synchronen Arbeitsaufgabe ist in der Regel die Rückruffunktion für den asynchronen Vorgang.  Diese Funktion kann aufgerufen werden, wenn ein asynchroner Vorgang abgebrochen oder ein Join\-Vorgang verwenden wird, oder auch in anderen Szenarien.  
  
 Zu den möglichen Werten für `relationType` zählen:  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 Weitere Informationen hierzu finden Sie unter [Debugkonstanten](../../javascript/reference/debug-constants.md).  
  
> [!NOTE]
>  Einige Debugtools zeigen nicht die Informationen an, die über diese Funktion an den Debugger gesendet werden.  
  
## Anforderungen  
 [!INCLUDE[jsv11](../../includes/jsv11-md.md)]