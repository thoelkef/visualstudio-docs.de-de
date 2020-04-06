---
title: IDebugDocumentContext2::GetSourceRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 782cf230c38af77da09b49f69c093e2e95bf7199
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731802"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Ruft den Quellcodebereich dieses Dokumentkontexts ab.

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

## <a name="parameters"></a>Parameter
`pBegPosition`\
[in, out] Eine [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die mit der Startposition ausgefüllt wird. Legen Sie dieses Argument auf einen NULL-Wert fest, wenn diese Informationen nicht benötigt werden.

`pEndPosition`\
[in, out] Eine [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die mit der Endposition ausgefüllt wird. Legen Sie dieses Argument auf einen NULL-Wert fest, wenn diese Informationen nicht benötigt werden.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Quellbereich ist der gesamte Bereich des Quellcodes, von der aktuellen Anweisung zurück bis zur vorherigen Anweisung, die Code beigesteuert hat. Der Quellbereich wird in der Regel zum Mischen von Quellanweisungen, einschließlich Kommentaren, mit Code im Demontagefenster verwendet.

 Um den Bereich für nur die Codeanweisungen abzurufen, die in diesem Dokumentkontext enthalten sind, rufen Sie die [GetStatementRange-Methode](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
