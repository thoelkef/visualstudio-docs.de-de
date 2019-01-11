---
title: IDebugMethodField::EnumAllLocals | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f03a285a390e244babe99b2cc0ae2db5bf9e67f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846281"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Erstellt einen Enumerator für alle lokalen Variablen der Methode enthält, beispielsweise solche, die intern vom Compiler generiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 [in] Ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Objekt, das eine debugadresse innerhalb der Methode, die auf einem bestimmten Bereich oder Kontext darstellt.  
  
 `ppLocals`  
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der alle lokalen Variablen im angegebenen Bereich darstellt, andernfalls einen null-Wert, der angibt, kein lokal.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn kein lokal vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Nur die Variablen, die innerhalb des Blocks mit der angegebenen Adresse definiert werden aufgelistet. Diese Methode enthält alle vom Compiler generierter "lokal". Wenn lediglich die lokalen Variablen, die explizit im Aufruf der Quelle definiert sind die [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) Methode.  
  
 Eine Methode kann mehrere Bereichsdefinition Kontexte oder Blöcke enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)