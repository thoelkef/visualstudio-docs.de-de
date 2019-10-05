---
title: IDebugActivateDocumentEvent2::GetDocumentContext | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2::GetDocumentContext
helpviewer_keywords:
- GetDocumentContext method
- IDebugActivateDocumentEvent2::GetDocumentContext method
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 855ff83786a02632304ed397ab8d2844c186bded
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160119"
---
# <a name="idebugactivatedocumentevent2getdocumentcontext"></a>IDebugActivateDocumentEvent2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft ab, der Dokumentenkontext, der die Position im Dokument wird beschrieben, die durch das debugpaket ausgeführt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppDocContext`  
 [out] Gibt eine [idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Objekt, das eine Position in einem Quelldokument für die Datei darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Position kann verwendet werden, um die Einfügemarke, z. B. anzuzeigen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
