---
title: IDebugDocumentPositionOffset2::GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd305b6506471a40de90fbd954e54461d2a139d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731624"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Ruft den Bereich für die aktuelle Dokumentposition ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Parameter
`pdwBegOffset`\
[in, out] Offset für die Startposition des Bereichs. Legen Sie diesen Parameter auf einen NULL-Wert fest, wenn diese Informationen nicht benötigt werden.

`pdwEndOffset`\
[in, out] Offset für die Endposition des Bereichs. Legen Sie diesen Parameter auf einen NULL-Wert fest, wenn diese Informationen nicht benötigt werden.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der in einer Dokumentposition für einen Positionshaltepunkt angegebene Bereich wird von der Debug-Engine (DE) verwendet, um im Voraus nach einer Anweisung zu suchen, die tatsächlich Code beisteuert. Beachten Sie z. B. folgenden Code:

```
Line 5: // comment
Line 6: x = 1;
```

 Zeile 5 trägt keinen Code zum zu debuggenden Programm bei. Wenn der Debugger, der den Haltepunkt in Zeile 5 festlegt, möchte, dass die DE einen bestimmten Betrag für die erste Zeile, die Code beisteuert, vorwärts sucht, gibt der Debugger einen Bereich an, der zusätzliche Kandidatenzeilen enthält, in denen ein Haltepunkt möglicherweise korrekt platziert wird. Die DE durchsuchte dann diese Zeilen, bis sie eine Linie fand, die einen Haltepunkt akzeptieren konnte.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
