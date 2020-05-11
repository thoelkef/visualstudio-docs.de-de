---
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75e4453cae63f484961cb2d0f3385a703709f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737232"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Gibt die Kriterien für den Vergleich von zwei Dokumentkontexten an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>Felder
`DOCCONTEXT_EQUAL`\
Suchen Sie den ersten Dokumentkontext in der Liste, der dem Zieldokumentkontext entspricht.

`DOCCONTEXT_LESS_THAN`\
Suchen Sie den ersten Dokumentkontext in der Liste, der kleiner als der Zieldokumentkontext ist.

`DOCCONTEXT_GREATER_THAN`\
Suchen Sie den ersten Dokumentkontext in der Liste, der größer als der Kontext des Zieldokuments ist.

`DOCCONTEXT_SAME_DOCUMENT`\
Suchen Sie den ersten Dokumentkontext in der Liste, der sich im selben Dokument wie der Zieldokumentkontext befindet.

## <a name="remarks"></a>Bemerkungen
Übergeben als Argument [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) an die Compare-Methode.

Diese Werte werden verwendet, um ein Vergleichskriterium für das Suchen des ersten Dokumentkontexts in einer Liste anzugeben. Einem Dokumentkontext wird eine Liste von Dokumentkontexten `IDebugDocumentContext2::Compare` gegeben, mit denen er sich durch die Methode vergleichen kann. Der erste Dokumentkontext in der Liste, `true` für den der Vergleichsoperator angezeigt wird, wird dann zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Vergleichen](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
