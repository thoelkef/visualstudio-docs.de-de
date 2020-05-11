---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 333535a727d88f66346ba4c94cb08b4917b8acfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722739"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Schreibt ein Dump in eine Datei.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>Parameter
`DumpType`\
[in] Ein Wert [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) aus der DUMPTYPE-Enumeration, der den Typ des Dumps angibt, z. B. kurz oder lang.

`pszDumpUrl`\
[in] Die URL, in die das Dump geschrieben werden soll. In der Regel ist `file://c:\path\filename.ext`dies in Form von , aber kann eine gültige URL sein.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Programmabbild würde in der Regel den aktuellen Stapelrahmen, den Stapel selbst, eine Liste der im Programm ausgeführten Threads und möglicherweise jeden Speicher enthalten, den das Programm besitzt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
