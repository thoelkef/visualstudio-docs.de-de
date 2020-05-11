---
title: BP_LOCATION_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e6bdc0dba8f6bcbdd55c45132dff02735786d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737939"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Gibt den Positionstyp des Haltepunkts für eine Haltepunktanforderung an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>Felder
`BPLT_NONE`\
Gibt keine Haltepunktposition an.

`BPLT_FILE_LINE`\
Gibt den Speicherorttyp des Haltepunkts als Dateizeile an.

`BPLT_FUNC_OFFSET`\
Gibt den Positionstyp des Haltepunkts als Funktionsversatz an.

`BPLT_CONTEXT`\
Gibt den Positionstyp des Haltepunkts als Kontext an.

`BPLT_STRING`\
Gibt den Positionstyp des Haltepunkts als Zeichenfolge an.

`BPLT_ADDRESS`\
Gibt den Positionstyp des Haltepunkts als Adresse an.

`BPLT_RESOLUTION`\
Gibt den Positionstyp des Haltepunkts als Auflösung an.

`BPLT_CODE_FILE_LINE`\
Gibt den Positionstyp des Haltepunkts als Quellcodezeile an.

`BPLT_CODE_FUNC_OFFSET`\
Gibt den Positionstyp des Haltepunkts als Codefunktionsversatz an.

`BPLT_CODE_CONTEXT`\
Gibt den Positionstyp des Haltepunkts als Codekontext an.

`BPLT_CODE_STRING`\
Gibt den Positionstyp des Haltepunkts als Codezeichenfolge an.

`BPLT_CODE_ADDRESS`\
Gibt den Positionstyp des Haltepunkts als Codeadresse an.

`BPLT_DATA_STRING`\
Gibt den Positionstyp des Haltepunkts als Datenzeichenfolge an.

`BPLT_TYPE_MASK`\
Gibt eine Bitmaske an, damit der Haltepunkttyp aus dem Wert extrahiert werden kann.

`BPLT_LOCATION_TYPE_MASK`\
Gibt eine Bitmaske an, damit der Haltepunktpositionstyp aus dem Wert extrahiert werden kann.

## <a name="remarks"></a>Bemerkungen
Wird als Parameter an die [GetLocationType-Methode](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) übergeben.

Ein Haltepunktpositionstyp besteht aus einem Haltepunkttyp und einem Positionstyp. Dies bedeutet, dass ein Haltepunktpositionstyp nie nur `BPT_CODE`ein Haltepunkttyp (z. `BPLT_FILE_LINE`B. ) oder ein Positionstyp (z. B. ) ist. Vordefinierte Konstanten für alle derzeit unterstützten Haltepunktpositionstypen sind`BPLT_CODE_FILE_LINE` `BPLT_DATA_STRING`in dieser Enumeration ( bis ) enthalten.

`BPT_CODE`und `BPT_DATA` sind Mitglieder der [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) Aufzählung.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
