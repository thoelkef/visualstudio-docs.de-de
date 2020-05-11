---
title: IDebugCanStopEvent2::GetCodeContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94c129d7d50bc747291d8a178d73c06655e65414
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734561"
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
Ruft den Codekontext ab, der den Speicherort dieses Ereignisses beschreibt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCodeContext( 
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parameter
`ppCodeContext`\
[out] Gibt das [IDebugCodeContext2-Objekt](../../../extensibility/debugger/reference/idebugcodecontext2.md) zurück, das den aktuellen Codespeicherort darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Für die meisten Laufzeitarchitekturen kann ein Codekontext als Adresse im Ausführungsstream eines Programms betrachtet werden, die auf eine bestimmte Anweisung verweist.

 Um den Dokumentkontext abzurufen, der auf Quellcodezeilen ausgerichtet ist, rufen Sie die [GetDocumentContext-Methode](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
