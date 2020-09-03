---
title: 'IDebugDocumentPosition2:: ispositionindocument | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7950f091d34d03222044455be671e15f5297a747
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200281"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, ob die Dokument Position im angegebenen Dokument enthalten ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Das [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Objekt, das den enthaltenden Dokument Kandidaten darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird hauptsächlich beim Festlegen von Breakpoints in [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Schnittstellen verwendet. Beim Laden von Dokumenten wird die Haltepunkt Position aufgerufen, um zu bestimmen, ob das Dokument diese Position enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
