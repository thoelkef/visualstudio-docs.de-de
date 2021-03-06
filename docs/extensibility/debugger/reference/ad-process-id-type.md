---
title: AD_PROCESS_ID_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a88fbe97cede8d343f1a96bc1917a69b8905b02b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738191"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Gibt an, wie eine Prozess-ID in der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur interpretiert werden soll.

## <a name="syntax"></a>Syntax

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>Felder
`AD_PROCESS_ID_SYSTEM`\
Die Prozess-ID ist ein System Bezeichner. Verwenden Sie das- `ProcessId.dwProcessId` Feld der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur.

`AD_PROCESS_ID_GUID`\
Die Prozess-ID ist eine GUID. Verwenden Sie das- `ProcessId.guidProcessId` Feld der- `AD_PROCESS_ID` Struktur.

## <a name="remarks"></a>Bemerkungen
Wird für den `ProcessIdType` Member der [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur verwendet, um den Typ der Prozess-ID zu identifizieren, der in der Struktur enthalten ist. Bestimmt, wie die `ProcessId` Union in der-Struktur interpretiert wird.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
