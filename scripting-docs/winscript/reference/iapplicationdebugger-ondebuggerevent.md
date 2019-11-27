---
title: 'Iapplicationdebugger:: ondebuggerevent | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebuggerEvent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8edb2a3c39d639b5b6722707d7b6c0b57a5c19
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577868"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Behandelt ein benutzerdefiniertes Anwendungs Ereignis.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `riid`  
 in Der Schnittstellen Bezeichner für das-Objekt.  
  
 `punk`  
 in Das Ereignis Objekt, das die durch `riid`definierte-Schnittstelle implementiert.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die-Methode ist zurzeit nicht implementiert.|  
  
## <a name="remarks"></a>Hinweise  
 Die Semantik des `IUnknown` ist vollständig von Anwendung/Debugger definiert.  
  
 Diese Methode ermöglicht benutzerdefinierte Erweiterungen des Debugger-Modells. Es ist zurzeit nicht implementiert.  
  
 Diese Methode wird aufgerufen, wenn `IDebugApplication::FireDebuggerEvent` aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Iapplicationdebugger-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)