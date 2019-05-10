---
title: PROVIDER_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 838a7dc0024e69335bf5c49c664bd491a6949d08
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460919"
---
# <a name="providerfields"></a>PROVIDER_FIELDS
Gibt Eigenschaften, die mit einem Programm Anbieter verknüpft sind.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
typedef DWORD PROVIDER_FIELDS;
```

```csharp
public enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
```

## <a name="fields"></a>Felder
 `PFIELD_PROGRAM_NODES`\
 Die `ProgramNodes` Feld ist gültig.

 `PFIELD_IS_DEBUGGER_PRESENT`\
 Die `fIsDebuggerPresent` Feld ist gültig.

## <a name="remarks"></a>Hinweise
 Diese Werte werden zurückgegeben, der `Fields` Mitglied der [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Struktur, um anzugeben, welche Felder der Struktur explizit ausgefüllt wurden.

 Diese Werte können kombiniert werden, mit einer bitweisen `OR`.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)