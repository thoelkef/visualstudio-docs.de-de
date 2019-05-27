---
title: IDebugDocumentPosition2::IsPositionInDocument | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb62493170cf393a3a46b14586f6dcdc4f762d76
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210051"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Bestimmt, ob die Dokumentposition in das angegebene Dokument enthalten ist.

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

## <a name="parameters"></a>Parameter
`pDoc`\
[in] Die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Objekt, das die Candidate-Version mit Dokument darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird verwendet, in erster Linie in das Festlegen von Breakpoints in [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Schnittstellen. Während Dokumente geladen werden, wird die Position des Haltepunkts aufgerufen, um festzustellen, ob das Dokument dieser Position enthält.

## <a name="see-also"></a>Siehe auch
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)