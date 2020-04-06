---
title: IDebugDocumentContext2::Vergleichen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0e46f765c8e4c0e12c3bb9447e0713919fae7b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731892"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Vergleicht diesen Dokumentkontext mit einem bestimmten Array von Dokumentkontexten.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>Parameter
`compare`\
[in] Ein Wert [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) aus der DOCCONTEXT_COMPARE-Enumeration, der den Typ des Vergleichs angibt.

`rgpDocContextSet`\
[in] Ein Array von [IDebugDocumentContext2-Objekten,](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) die die Dokumentkontexte darstellen, mit denen verglichen wird.

`dwDocContextSetLen`\
[in] Die Länge des zu vergleichenden Arrays von Dokumentkontexten.

`pdwDocContext`\
[out] Gibt den Index `rgpDocContextSet` in das Array des ersten Dokumentkontexts zurück, der den Vergleich erfüllt.

## <a name="return-value"></a>Rückgabewert
 Gibt `S_OK` zurück, wenn eine Übereinstimmung gefunden wurde. Gibt `S_FALSE` zurück, wenn keine Übereinstimmung gefunden wurde. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die [IDebugDocumentContext2-Objekte,](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) die im Array übergeben werden, müssen von `IDebugDocumentContext2` demselben Debugmodul implementiert werden, das das aufgerufene Objekt implementiert. Andernfalls ist der Vergleich ungültig.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
