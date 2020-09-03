---
title: PENDING_BP_STATE_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_FLAGS
helpviewer_keywords:
- PENDING_BP_STATE_FLAGS enumeration
ms.assetid: 85522449-3fd8-4da5-b0fe-a43160e0c33b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6da1a956ac958a95dd0c433283a71af0a9b29d1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714092"
---
# <a name="pending_bp_state_flags"></a>PENDING_BP_STATE_FLAGS
Gibt die ausstehenden breakpointstatusflags an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
typedef DWORD PENDING_BP_STATE_FLAGS;
```

```csharp
public enum enum_PENDING_BP_STATE_FLAGS { 
   PBPSF_NONE        = 0x0000,
   PBPSF_VIRTUALIZED = 0x0001
};
```

## <a name="fields"></a>Felder
 `PBPSF_NONE` Platzhalter.

 `PBPSF_VIRTUALIZED` Gibt einen virtualisierten ausstehenden Haltepunkt an, der jedes Mal gebunden werden soll, wenn neuer Code geladen wird.

## <a name="remarks"></a>Bemerkungen
 Wird für den `flags` Member der [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) -Struktur verwendet.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
