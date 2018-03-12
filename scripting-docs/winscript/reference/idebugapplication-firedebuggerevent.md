---
title: IDebugApplication::FireDebuggerEvent | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4cb02390602b6b93b8c233f245ede395833d67e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Löst ein Ereignis aus, die im Debuggers generische `IApplicationDebugger` Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `riid`  
 [in] Eine GUID für das Objekt.  
  
 `punk`  
 [in] Ein Ereignisobjekt für die Übergabe an den Debugger.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die Methode wird derzeit nicht implementiert.|  
  
## <a name="remarks"></a>Hinweise  
 Die Semantik der GUID und die `IUnknown` vollständig Anwendung/Debugger definiert sind.  
  
 Diese Methode ermöglicht für benutzerdefinierte Erweiterungen des Modells Debugger; Es ist derzeit nicht implementiert.  
  
 Diese Methode bewirkt, dass `IApplicationDebugger::onDebuggerEvent` aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)