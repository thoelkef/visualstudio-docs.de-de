---
title: IDebugMethodField::EnumAllLocals | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::EnumAllLocals
helpviewer_keywords: IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4910f5b0daa5b474be4061d73c8600c388884451
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Erstellt einen Enumerator für alle lokalen Variablen der Methode, die von einem Compiler intern generierten einschließlich.  
  
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
 [in] Ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Objekt, das eine Debug-Adresse innerhalb der Methode, die auf einem bestimmten Bereich oder Kontext darstellt.  
  
 `ppLocals`  
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der alle "lokal" im angegebenen Bereich darstellt; andernfalls wird einen null-Wert, der angibt, der keine "lokal" zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei Erfolg S_OK zurückgibt, oder gibt "S_FALSE" zurück, wenn es keine "lokal sind". Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Es werden nur die Variablen, die innerhalb des Blocks mit der angegebenen Adresse definiert aufgelistet. Diese Methode schließt alle vom Compiler generierte "lokal". Wenn erforderlich ist, die explizit in der Quelle Aufruf definiert "lokal" werden die [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) Methode.  
  
 Eine Methode kann mehrere Bereichsdefinition Kontexten oder Blöcke enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)