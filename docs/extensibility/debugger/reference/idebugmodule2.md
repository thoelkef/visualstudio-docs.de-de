---
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbbea1b52133de41dd26f437aeba31a0eff5a50a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726907"
---
# <a name="idebugmodule2"></a>IDebugModule2
Diese Schnittstelle stellt ein Modul dar, d. h. eine ausführbare Einheit eines Programms, z. B. eine DLL.

## <a name="syntax"></a>Syntax

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um ein Modul darzustellen und den Zugriff auf Informationen zu diesem Modul zu ermöglichen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) gibt diese Schnittstelle zurück. Die DE sendet die [IDebugModuleLoadEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) mithilfe der [Ereignismethode](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) an den Session Debug Manager (SDM).

 Diese Schnittstelle kann auch in einer [FRAMEINFO-Struktur](../../../extensibility/debugger/reference/frameinfo.md) zurückgegeben werden (die durch einen Aufruf von [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)zurückgegeben wird).

- [Als nächstes](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) gibt auch diese Schnittstelle zurück ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) gibt die [IEnumDebugModules2-Schnittstelle](../../../extensibility/debugger/reference/ienumdebugmodules2.md) zurück).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugModule2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ruft die [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) ab, die dieses Modul beschreibt.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|VERALTET. NICHT VERWENDEN. Lädt die Symbole für dieses Modul neu.|

## <a name="remarks"></a>Bemerkungen
 Modulinformationen können im **Modulfenster** der IDE angezeigt werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [Getmodule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
