---
title: SEEK_START | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca1c38027123ca5147a6a7ab1fa6a3f92966409a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713592"
---
# <a name="seek_start"></a>SEEK_START
Gibt die Position an, von der aus in einem Demontagestrom gesucht werden soll.

## <a name="syntax"></a>Syntax

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Felder
 `SEEK_START_BEGIN`\
 Beginnt mit der Suche am Anfang des aktuellen Dokuments.

 `SEEK_START_END`\
 Beginnt mit der Suche am Ende des aktuellen Dokuments.

 `SEEK_START_CURRENT`\
 Beginnt mit der Suche an der aktuellen Position des aktuellen Dokuments.

 `SEEK_START_CODECONTEXT`\
 Beginnt mit der Suche im angegebenen Codekontext des aktuellen Dokuments.

 `SEEK_START_CODELOCID`\
 Beginnt mit der Suche an der angegebenen Codepositionskennung. Codepositionsbezeichner werden durch Aufrufen von [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)abgerufen.

## <a name="remarks"></a>Bemerkungen
 Übergeben als Argument [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) an die Seek-Methode.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
