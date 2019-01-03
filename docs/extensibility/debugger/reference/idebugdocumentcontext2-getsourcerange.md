---
title: IDebugDocumentContext2::GetSourceRange | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe2ad435b4b70f2314822414c0cc0eb429c2478e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841554"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Ruft die Quelle des Bereichs dieses Kontexts Dokument ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pBegPosition`  
 [in, out] Ein [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) -Struktur, die mit die Position gefüllt wird. Legen Sie dieses Argument auf einen null-Wert, wenn diese Informationen nicht benötigt wird.  
  
 `pEndPosition`  
 [in, out] Ein [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) -Struktur, die mit der Endposition gefüllt wird. Legen Sie dieses Argument auf einen null-Wert, wenn diese Informationen nicht benötigt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Quellbereich wird der gesamte Bereich der Quellcode, aus der aktuellen Anweisung zurück, nachdem die vorherige Anweisung einfach, die Code beigetragen haben. Der Quellbereich wird normalerweise verwendet, für das Kombinieren von quellanweisungen, einschließlich der Kommentare, durch Code im Disassemblyfenster.  
  
 Um den Bereich nur Code enthaltenen Anweisungen in diesem Dokumentenkontext abzurufen, rufen die [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)