---
title: 'IDebugDisassemblyStream2:: getcodelta-ID | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32be70e11776177a0e68f09689c2262497703ab1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732254"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Gibt einen Bezeichner für den Code Speicherort für einen bestimmten Code Kontext zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>Parameter
`pCodeContext`\
in Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das in einen Bezeichner konvertiert werden soll.

`puCodeLocationId` vorgenommen Gibt den Bezeichner des Code Speicher Orts zurück. Siehe Hinweise.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück, `E_CODE_CONTEXT_OUT_OF_SCOPE` Wenn der Code Kontext gültig, aber außerhalb des Bereichs ist.

## <a name="remarks"></a>Bemerkungen
 Der Bezeichner für den Code Speicherort ist für die Debug-Engine (de) spezifisch, die die Disassembly unterstützt Dieser Speicherort Bezeichner wird intern von der de verwendet, um Positionen im Code zu verfolgen, und ist in der Regel eine Adresse oder ein Offset. Die einzige Voraussetzung ist, dass der Code Kontext eines Speicher Orts, der kleiner als der Code Kontext einer anderen Position ist, auch kleiner als der Bezeichner für den Code Speicherort des zweiten Code Kontexts sein muss.

 Um den Code Kontext eines Code Speicherort Bezeichners abzurufen, rufen Sie die [getcodecontext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) -Methode auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
