---
title: IDebugDocumentContext2::GetSourceRange | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73600b81c71a1337470a1975902c40292ab4dcef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515999"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugDocumentContext2::GetSourceRange](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange).  
  
Ruft die Quelle des Bereichs dieses Kontexts Dokument ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

