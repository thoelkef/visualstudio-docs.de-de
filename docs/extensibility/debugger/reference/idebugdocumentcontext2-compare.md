---
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f41b0e5973af8e0cb65f093f51137059084c9792
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105486"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Vergleicht dieses Dokumentenkontext in ein angegebenes Array von Kontexten Dokument.  
  
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
 [in] Ein Wert aus der [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) -Enumeration, der den Typ des Vergleichs angibt.  
  
 `rgpDocContextSet`  
 [in] Ein Array von [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Objekte, die die Dokument-Kontexten wird im Vergleich zu darstellen.  
  
 `dwDocContextSetLen`  
 [in] Die Länge des Arrays mit Dokument Kontexte, verglichen werden soll.  
  
 `pdwDocContext`  
 [out] Gibt den Index in der `rgpDocContextSet` Array mit den ersten Dokumentenkontext, die den Vergleich zu erfüllen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` , wenn eine Übereinstimmung gefunden wurde. Gibt `S_FALSE` , wenn keine Übereinstimmung gefunden wurde. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Objekte, die im Array übergeben werden müssen implementiert werden, von der gleichen Debugging-Modul, das implementiert die `IDebugDocumentContext2` -Objekt aufgerufen werden, andernfalls ist der Vergleich nicht gültig.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)