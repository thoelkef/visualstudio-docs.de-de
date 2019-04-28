---
title: IDebugAsyncOperationCallBack::onComplete | Microsoft-Dokumentation
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
ms.openlocfilehash: f9e5532a55901d8e29addfee58594645440991f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821871"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Signalisiert, dass ein Ergebnis eines asynchronen Debugvorgangs verfügbar ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode akzeptiert keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode signalisiert, dass ein Ergebnis verfügbar ist ein `IDebugAsyncOperation` Objekt. Das Ereignis wird im Debuggerthread ausgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugAsyncOperationCallBack-Schnittstelle](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [IDebugAsyncOperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)