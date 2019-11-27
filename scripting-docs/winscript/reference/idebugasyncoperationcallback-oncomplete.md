---
title: 'Idebugasyncoperationcallback:: OnComplete | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperationCallBack.onComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugAsyncOperationCallBack::onComplete
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a15ae57d64d2b1e7be867c20e9683e4aaa415974
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573230"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Signalisiert, dass ein Ergebnis von einem asynchronen Debugvorgang verfügbar ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode signalisiert, dass ein Ergebnis aus einem `IDebugAsyncOperation`-Objekt verfügbar ist. Das Ereignis wird im Debugger-Thread ausgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugasyncoperationcallback-Schnittstelle](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [IDebugAsyncOperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)