---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 603bd08c1ec3832bf732e0b33101076738d009e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702253"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Dies ist eine Rückruffunktion, die in einem Aufruf `SCC_OPT_NAMECHANGEPFN`der [SccSetOption](../extensibility/sccsetoption-function.md) angegeben wird (verwendungsoption ) und wird verwendet, um Namensänderungen, die vom Quellcodeverwaltungs-Plug-In vorgenommen wurden, an die IDE zurückzugeben.

## <a name="signature"></a>Signatur

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parameter
 pvCallerData

[in] Benutzerwert, der in einem vorherigen Aufruf der `SCC_OPT_USERDATA` [SccSetOption](../extensibility/sccsetoption-function.md) angegeben wurde (Verwendungsoption ).

 pszOldName

[in] Der ursprüngliche Name der Datei.

 pszNewName

[in] Der Name, in den die Datei umbenannt wurde.

## <a name="return-value"></a>Rückgabewert
 Keine.

## <a name="remarks"></a>Bemerkungen
 Wenn eine Datei während eines Quellcodeverwaltungsvorgangs umbenannt wird, kann das Quellcodeverwaltungs-Plug-In die IDE über die Namensänderung durch diesen Rückruf benachrichtigen.

 Wenn die IDE diesen Rückruf nicht unterstützt, ruft sie die [SccSetOption](../extensibility/sccsetoption-function.md) nicht auf, um sie anzugeben. Wenn das Plug-In diesen Rückruf nicht unterstützt, `SccSetOption` wird es von der Funktion zurückgegeben, `SCC_E_OPNOTSUPPORTED` wenn die IDE versucht, den Rückruf festzulegen.

## <a name="see-also"></a>Weitere Informationen
- [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
