---
title: IDebugDocumentPosition2::isPositionInDocument | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4d92dddda8fd9831f5d66b602cd48fdbbc3dbcf1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731656"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
Bestimmt, ob die Dokumentposition im angegebenen Dokument enthalten ist.

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
[in] Das [IDebugDocument2-Objekt,](../../../extensibility/debugger/reference/idebugdocument2.md) das den enthaltenden Dokumentkandidaten darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird hauptsächlich beim Festlegen von Haltepunkten in [IDebugDocument2-Schnittstellen](../../../extensibility/debugger/reference/idebugdocument2.md) verwendet. Beim Laden von Dokumenten wird die Haltepunktposition aufgerufen, um zu bestimmen, ob das Dokument diese Position enthält.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
