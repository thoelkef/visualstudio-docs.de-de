---
title: FIELD_INFO_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cab1d06c868f0236d1d24c186af705e9adab717e
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317470"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Gibt an, welche Informationen Sie zum Abrufen einer [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt.

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="members"></a>Member
FIF_FULLNAME  
Initialisieren und Verwenden der `bstrFullName` -Feld in der [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur.

FIF_NAME  
Initialisieren und Verwenden der `bstrName` -Feld in der `FIELD_INFO` Struktur.

FIF_TYPE  
Initialisieren und Verwenden der `bstrType` -Feld in der `FIELD_INFO` Struktur.

FIF_MODIFIERS  
Initialisieren und Verwenden der `bstrModifiers` -Feld in der `FIELD_INFO` Struktur.

## <a name="remarks"></a>Hinweise
Diese Werte werden auch als Argument übergeben die [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) Methode, um die Felder der anzugeben, die [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) sind, dass die Struktur initialisiert werden.

Diese Werte werden auch verwendet, der `dwFields` Mitglied der `FIELD_INFO` Struktur, um anzugeben, welche Felder verwendet und gültig sind.

Diese Flags können kombiniert werden, mit einer bitweisen `OR`.

## <a name="requirements"></a>Anforderungen
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)  
[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
