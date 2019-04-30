---
title: SYMBOL_SEARCH_INFO_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SYMBOL_SEARCH_INFO_FIELDS
helpviewer_keywords:
- SYMBOL_SEARCH_INFO_FIELDS enumeration
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2621b88622e99ac95533e388197e483f2925f897
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420836"
---
# <a name="symbolsearchinfofields"></a>SYMBOL_SEARCH_INFO_FIELDS
Gibt die Art von symbolischen Informationen abrufen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;
```

```csharp
public enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};

```

## <a name="members"></a>Member
 SSIF_NONE gibt keine Flags an.

 SSIF_VERBOSE_SEARCH_INFO gibt zurück, die alle Pfade verwendet werden, für die Suche nach Symbolen suchen

## <a name="remarks"></a>Hinweise
 Diese Flags werden übergeben, als Parameter an die ["getsymbolinfo"](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) Methode, um zu bestimmen, die Menge an Informationen zurückgegeben.

> [!NOTE]
> Derzeit nur `SSIF_VERBOSE_SEARCH_INFO` wird unterstützt, und es muss angegeben werden, als die `dwFlags` Parameter `IDebugModule3::GetSymbolInfo`. Alle anderen Werte wird ein Fehler zurückgegeben.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)