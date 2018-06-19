---
title: IDebugDocumentContext2::GetSourceRange | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: f003ba3f97f053c4617408bfc9334da057bb98ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107224"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Ruft der Code Quellbereich dieses Kontexts Dokument ab.  
  
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
 [in, out] Ein [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) -Struktur, die mit der Startposition ausgefüllt ist. Legen Sie dieses Argument auf einen null-Wert, wenn diese Informationen nicht benötigt wird.  
  
 `pEndPosition`  
 [in, out] Ein [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) -Struktur, die mit der Endposition ausgefüllt ist. Legen Sie dieses Argument auf einen null-Wert, wenn diese Informationen nicht benötigt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Quellbereich wird der gesamte Bereich des Quellcodes von der aktuellen Anweisung zurück, nach der vorherigen Anweisung einfach, die Code beigetragen haben. Der Quellbereich wird normalerweise verwendet, für die quellanweisungen, einschließlich der Kommentare mit Code im Disassemblyfenster mischen.  
  
 Rufen Sie zum Abrufen des Bereichs für nur den codeanweisungen, die in diesem Dokumentenkontext enthalten die [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)