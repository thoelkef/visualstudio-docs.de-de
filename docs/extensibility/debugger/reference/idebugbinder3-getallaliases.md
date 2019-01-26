---
title: IDebugBinder3::GetAllAliases | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e64df5e58f396462ebc9309302a7bbb7a42febcf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006293"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Diese Methode ruft eine Liste der Aliase ab, aus dem Programm.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `uRequest`  
 [in] Die maximale Anzahl von Aliasen zu zurückgeben (gibt die Länge des übergebenen Arrays `ppAliases`).  
  
 `ppAliases`  
 [in, out] Mit Aliasen auszufüllende Array (ist dies ein null-Wert und `uRequest` gleich 0 ist, wird die Anzahl der Aliase, die zurückgegeben werden können, zurückgegeben werden, indem `puFetched`).  
  
 `puFetched`  
 [out] Gibt die Anzahl von Aliasen abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)