---
title: IDebugDocumentContext2::Seek | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ec88bb39a8319fba752b52023fdc4fb0b5a6c22a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Verschiebt den Dokumentenkontext durch eine angegebene Anzahl von Anweisungen oder Zeilen an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Seek(   
   int                      nCount,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```cpp  
int Seek(   
   int                        nCount,  
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `nCount`  
 [in] Die Anzahl der Anweisungen oder Zeilen, je nach Dokumentenkontext springen.  
  
 `ppDocContext`  
 [out] Gibt eine neue [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Objekt mit der die neue Position.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)