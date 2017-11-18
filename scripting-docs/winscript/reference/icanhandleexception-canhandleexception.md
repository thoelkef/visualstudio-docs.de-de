---
title: ICanHandleException::CanHandleException | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15612330f160f694202bb2158f970e0633fe53bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Bestimmt, ob der Aufrufer des Skriptmoduls eine angegebene Ausnahme verarbeiten kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pExcepInfo`  
 [in] Zeiger auf eine `EXCEPINFO` Struktur mit den Informationen, die gemeldet werden, wenn keine Ausnahmehandler gefunden wurde.  
  
 `pvar`  
 [in] Ein Wert mit der Ausnahme, z. B. der Wert, der vom ausgelöst wird, eine `throw` Anweisung. Dieser Parameter kann `NULL` sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Der Aufrufer kann die Ausnahme behandelt.|  
|`E_FAIL`|Der Aufrufer kann nicht die Ausnahme zu behandeln.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Aufruf von `IDispatchEx::InvokeEx`, oder eine ähnliche Methode führt zu einer Ausnahme, die Überprüfungen der Skript-Modul ein Aufrufer in das Skript Aufrufer Kette, die unterstützt die `ICanHandleException` -Schnittstelle und gibt an, dass die Ausnahme zu behandeln. Wenn keine Aufrufer die Ausnahme behandeln kann, hält das Skriptmodul.  
  
## <a name="see-also"></a>Siehe auch  
 [ICanHandleException-Schnittstelle](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)