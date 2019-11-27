---
title: 'Idebugapplication:: firedebug-Ereignis | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00d895ed484e37f0ba38636a409876156ed97287
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574997"
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Löst ein generisches Ereignis für die `IApplicationDebugger`-Schnittstelle des Debuggers aus.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `riid`  
 in Eine GUID für das-Objekt.  
  
 `punk`  
 in Ein Ereignis Objekt, das an den Debugger übergeben werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die-Methode ist zurzeit nicht implementiert.|  
  
## <a name="remarks"></a>Hinweise  
 Die Semantik der GUID und der `IUnknown` sind vollständig Anwendungen/Debugger definiert.  
  
 Diese Methode ermöglicht benutzerdefinierte Erweiterungen des Debugger-Modells. Es ist zurzeit nicht implementiert.  
  
 Diese Methode bewirkt, dass `IApplicationDebugger::onDebuggerEvent` aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)