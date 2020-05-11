---
title: IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732254"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Gibt einen Codepositionsbezeichner für einen bestimmten Codekontext zurück.

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
[in] Ein [IDebugCodeContext2-Objekt,](../../../extensibility/debugger/reference/idebugcodecontext2.md) das in einen Bezeichner konvertiert werden soll.

`puCodeLocationId`[out] Gibt den Codepositionsbezeichner zurück. Siehe Hinweise.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt `E_CODE_CONTEXT_OUT_OF_SCOPE` zurück, wenn der Codekontext gültig, aber außerhalb des Bereichs ist.

## <a name="remarks"></a>Bemerkungen
 Die Codepositionskennung ist spezifisch für das Debugmodul (DE), das die Demontage unterstützt. Dieser Positionsbezeichner wird intern von der DE verwendet, um Positionen im Code nachzuverfolgen, und ist in der Regel eine Adresse oder ein Offset irgendeiner Art. Die einzige Voraussetzung ist, dass, wenn der Codekontext eines Speicherorts kleiner als der Codekontext eines anderen Speicherorts ist, der entsprechende Codespeicherortbezeichner des ersten Codekontexts auch kleiner sein muss als der Codespeicherortbezeichner des zweiten Codekontexts.

 Um den Codekontext eines Codepositionsbezeichners abzurufen, rufen Sie die [GetCodeContext-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
