---
title: IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6b3864528ee90c22a1e7122eeaf1969f613cc8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732286"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
Gibt ein Codekontextobjekt zurück, das einem angegebenen Codepositionsbezeichner entspricht.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCodeContext( 
   UINT64               uCodeLocationId,
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   ulong                  uCodeLocationId,
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parameter
`uCodeLocationId`\
[in] Gibt den Codepositionsbezeichner an. Eine Beschreibung eines Codepositionsbezeichners finden Sie im Abschnitt "Hinweise" für die [GetCodeLocationId-Methode.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)

`ppCodeContext`\
[out] Gibt ein [IDebugCodeContext2-Objekt](../../../extensibility/debugger/reference/idebugcodecontext2.md) zurück, das den zugeordneten Codekontext darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Codepositionsbezeichner kann von einem Aufruf an die [GetCurrentLocation-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) zurückgegeben und in der [DisassemblyData-Struktur](../../../extensibility/debugger/reference/disassemblydata.md) angezeigt werden.

 Um einen Codekontext in einen Codepositionsbezeichner zu konvertieren, rufen Sie die [GetCodeLocationId-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
