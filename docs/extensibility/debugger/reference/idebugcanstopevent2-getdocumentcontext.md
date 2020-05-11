---
title: IDebugCanStopEvent2::GetDocumentContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3dc5e4bd7144db7fa94425371488bfd8c0e57ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734555"
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
Ruft den Dokumentkontext ab, der den Speicherort dieses Ereignisses beschreibt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocCxt
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocCxt
);
```

## <a name="parameters"></a>Parameter
`ppDocCxt`\
[out] Gibt die [IDebugDocumentContext2-Schnittstelle](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) zurück, die eine Position in einem Quelldateidokument darstellt, die dem aktuellen Codespeicherort entspricht.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Im Allgemeinen kann der Dokumentkontext als Position in einer Quelldatei betrachtet werden.

 Um den Codekontext abzurufen, der auf Codeanweisungen ausgerichtet ist, rufen Sie die [GetCodeContext-Methode](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
