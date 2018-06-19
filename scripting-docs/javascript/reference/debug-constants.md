---
title: Debug-Konstanten | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2c50181dc9f40d8665d6caca407232231682d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636150"
---
# <a name="debug-constants"></a>Debug-Konstanten
Debugkonstanten geben konstante Werte zurück, die Eigenschaften des `Debug`-Objekts sind.  
  
## <a name="debug-object-constants"></a>Konstanten des Debugobjekts  
 Die folgende Tabelle enthält konstante Werte, die Eigenschaften sind die [Debugobjekt](../../javascript/reference/debug-object-javascript.md).  
  
|Konstante|Beschreibung|Wert|  
|--------------|-----------------|-----------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|Die synchrone Arbeitsaufgabe wies einen Rückruf oder eine Fortsetzung zu, die von einem asynchronen Vorgang ausgeführt wird.|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|Das synchrone Arbeitselement erfüllt einen Teil eines asynchronen Join-Vorgangs.|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|Die synchrone Arbeitsaufgabe erfüllt einen asynchronen Auswahlvorgang.|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|Die synchrone Arbeitsaufgabe wurde storniert.|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|Die synchrone Arbeitsaufgabe hat einen Fehler in einem asynchronen Vorgang verursacht.|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|Der asynchrone Vorgang war erfolgreich.|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|Der asynchrone Vorgang wurde abgebrochen.|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|Der asynchrone Vorgang verursachte einen Fehler.|3|  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Debug.msTraceAsyncOperationCompleted-Funktion](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Debug.msUpdateAsyncCallbackRelation-Funktion](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)