---
title: IDebugDocumentContext2::Compare | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06fe3b1c2acffa47f7c47f5f9426fb1d07bbf288
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937833"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Vergleicht diese Dokumentkontext in ein angegebenes Array von Dokument-Kontexten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `compare`  
 [in] Ein Wert aus der [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) Enumeration, die den Typ des Vergleichs angibt.  
  
 `rgpDocContextSet`  
 [in] Ein Array von [idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Objekte, die darstellen, die dokumentenkontexte, die mit dem verglichen wird.  
  
 `dwDocContextSetLen`  
 [in] Die Länge des Arrays von dokumentenkontexte, verglichen werden soll.  
  
 `pdwDocContext`  
 [out] Gibt den Index in die `rgpDocContextSet` Array mit den ersten Dokumentenkontext, die den Vergleich zu erfüllen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` , wenn eine Übereinstimmung gefunden wurde. Gibt `S_FALSE` , wenn keine Übereinstimmung gefunden wurde. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Objekte, die im Array übergeben werden müssen implementiert werden, indem Sie die gleichen Debug-Engine, die implementiert die `IDebugDocumentContext2` Objekt aufgerufen wird, andernfalls der Vergleich ist ungültig.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)