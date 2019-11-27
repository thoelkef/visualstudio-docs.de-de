---
title: 'Icanlenker Exception:: canlenker Exception | Microsoft-Dokumentation'
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
ms.openlocfilehash: c536d35dcb9f0faca8b033ecd39aec520a2e260a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575722"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Bestimmt, ob der Aufrufer der Skript-Engine eine angegebene Ausnahme behandeln kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pExcepInfo`  
 in Ein Zeiger auf eine `EXCEPINFO` Struktur, die die Informationen enthält, die gemeldet werden, wenn kein Ausnahmehandler gefunden wird.  
  
 `pvar`  
 in Ein Wert, der der Ausnahme zugeordnet ist, z. b. der von einer `throw` Anweisung ausgelöste Wert. Dieser Parameter kann `NULL` sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Der Aufrufer kann die Ausnahme behandeln.|  
|`E_FAIL`|Der Aufrufer kann die Ausnahme nicht verarbeiten.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Aufruf von `IDispatchEx::InvokeEx`oder einer ähnlichen Methode zu einer Ausnahme führt, sucht die Skript-Engine nach einem Aufrufer in der Aufruf Kette des Skripts, der die `ICanHandleException` Schnittstelle unterstützt und zeigt an, dass die Ausnahme behandelt werden kann. Wenn kein Aufrufer die Ausnahme behandeln kann, wird die Skript-Engine angehalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Icanlenker Exception-Schnittstelle](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)