---
title: IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b49f55d4391e8d002a01236bb411373316dba36f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Bestimmt, ob der Dokumentposition in dem angegebenen Dokument enthalten ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```csharp  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pDoc`  
 [in] Die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Objekt, das der enthaltenden Dokument Kandidat darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode dient in erster Linie hinsichtlich Festlegen von Haltepunkten in [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Schnittstellen. Wie Dokumente geladen werden, wird die Position des Haltepunkts aufgerufen, um festzustellen, ob das Dokument dieser Position enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)