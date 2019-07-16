---
title: IDebugModule2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b621ae3b1408bc4af371243a1c34909117d40576
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323933"
---
# <a name="idebugmodule2"></a>IDebugModule2
Diese Schnittstelle stellt ein Modul dar, d. h. eine ausführbare Einheit eines Programms, wie z. B. eine DLL-Datei.

## <a name="syntax"></a>Syntax

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um ein Modul und den Zugriff auf Informationen zu diesem Modul ermöglichen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufruf von [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) dieser Schnittstelle zurück. Der DE sendet die [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) Schnittstelle für die Sitzung Debug-Manager (SDM) mithilfe der [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Methode.

 Diese Schnittstelle auch zurückgegeben werden kann, einem [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Struktur (das durch einen Aufruf zurückgegeben [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [Nächste](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) gibt auch diese Schnittstelle zurück ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) gibt die [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) Schnittstelle).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugModule2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ruft die [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) , der dieses Modul beschreibt.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|VERALTET. VERWENDEN SIE NICHT. Lädt die Symbole für dieses Modul erneut.|

## <a name="remarks"></a>Hinweise
 Modulinformationen kann angezeigt werden, der **Module** Fenster der IDE.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)