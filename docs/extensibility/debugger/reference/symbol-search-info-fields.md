---
title: SYMBOL_SEARCH_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SYMBOL_SEARCH_INFO_FIELDS
helpviewer_keywords:
- SYMBOL_SEARCH_INFO_FIELDS enumeration
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf8a1ad8a5dabc663ef29f5f2c36fdf0fbd8b786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713476"
---
# <a name="symbol_search_info_fields"></a>SYMBOL_SEARCH_INFO_FIELDS
Gibt die Art der abzurufenden Symbolinformationen an.

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

## <a name="fields"></a>Felder
 `SSIF_NONE`\
 Zeigt keine Flags an

 `SSIF_VERBOSE_SEARCH_INFO`\
 Gibt alle Suchpfade zurück, die zum Suchen von Symbolen verwendet werden

## <a name="remarks"></a>Bemerkungen
 Diese Flags werden als Parameter an die [GetSymbolInfo-Methode](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) übergeben, um die Menge der zurückgegebenen Informationen zu bestimmen.

> [!NOTE]
> Derzeit wird `SSIF_VERBOSE_SEARCH_INFO` nur unterstützt, und es `dwFlags` muss `IDebugModule3::GetSymbolInfo`als Parameter für angegeben werden. Alle anderen Werte geben einen Fehler zurück.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
