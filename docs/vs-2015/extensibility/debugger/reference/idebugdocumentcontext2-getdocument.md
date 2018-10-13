---
title: IDebugDocumentContext2::GetDocument | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::GetDocument
helpviewer_keywords:
- IDebugDocumentContext2::GetDocument
ms.assetid: c6d46c5d-ade8-4dc8-9862-8fc7876658c4
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5e250ba149df7915e05775810a95ab246817902
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302587"
---
# <a name="idebugdocumentcontext2getdocument"></a>IDebugDocumentContext2::GetDocument
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft das Dokument, das Dokumentenkontext dieses enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetDocument(   
   IDebugDocument2** ppDocument  
);  
```  
  
```csharp  
int GetDocument(   
   out IDebugDocument2 ppDocument  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppDocument`  
 [out] Gibt eine [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Objekt, das Dokument darstellt, das Dokumentenkontext dieses enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist für die Debug-Engines, die Dokumente direkt in der IDE bereitstellen. Andernfalls sollte diese Methode zurückgegeben `E_NOTIMPL`.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

