---
title: ICanHandleException::CanHandleException | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 406787d5ee6811b80f9e6831e5a67cab8367e7d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991395"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Bestimmt, ob der Aufrufer von der Skript-Engine eine angegebene Ausnahme verarbeiten kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pExcepInfo`  
 [in] Zeiger auf ein `EXCEPINFO` Struktur, die mit den Informationen, die gemeldet werden, wenn kein Ausnahmehandler gefunden wird.  
  
 `pvar`  
 [in] Ein Wert mit der Ausnahme, z. B. den Wert, der ausgelöst wird, indem eine `throw` Anweisung. Dieser Parameter kann `NULL` sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Der Aufrufer kann die Ausnahme behandelt.|  
|`E_FAIL`|Der Aufrufer kann die Ausnahme nicht verarbeiten.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Aufruf von `IDispatchEx::InvokeEx`, oder eine ähnliche Methode löst eine Ausnahme, die Skript-Engine-Überprüfungen von einem Aufrufer in Kette der Aufrufer des Skripts, die unterstützt die `ICanHandleException` -Schnittstelle und gibt an, dass sie die Ausnahme verarbeiten kann. Wenn keine Aufrufer die Ausnahme behandeln kann, hält die Skript-Engine.  
  
## <a name="see-also"></a>Siehe auch  
 [ICanHandleException-Schnittstelle](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)