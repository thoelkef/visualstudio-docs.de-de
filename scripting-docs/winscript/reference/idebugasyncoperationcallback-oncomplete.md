---
title: IDebugAsyncOperationCallBack::onComplete | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperationCallBack.onComplete
apilocation: jscript.dll
helpviewer_keywords: IDebugAsyncOperationCallBack::onComplete
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc55918c25da695f9eab470bf39fc648910ddc97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Signalisiert, dass ein Ergebnis aus einem asynchronen Debugvorgang verfügbar ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode signalisiert, ein Ergebnis von verfügbar ist ein `IDebugAsyncOperation` Objekt. Dieses Ereignis wird im Debuggerthread ausgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAsyncOperationCallBack-Schnittstelle](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [IDebugAsyncOperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)