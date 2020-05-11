---
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c81cda3a27cfe1ef0fecfefc9bbb790d4d5217
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723192"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity`wird von einem Portlieferanten implementiert, um den Benutzer zu warnen, dass das Anfügen an den Prozess unsicher ist.

## <a name="syntax"></a>Syntax

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugProcessSecurity`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Ruft den Benutzernamen vom Portlieferanten ab.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Warnt einen Benutzer, dass das Anfügen an den Debugvorgang unsicher ist.|

## <a name="remarks"></a>Bemerkungen
 Implementieren Sie diese Schnittstelle, um eine Warnung anzuzeigen, und ermöglichen Sie dem Benutzer, abzubrechen, wenn der Prozess, an den Sie anhängen, als unsicher betrachtet werden kann.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Ports](../../../extensibility/debugger/ports.md)
- [Portanbieter](../../../extensibility/debugger/port-suppliers.md)
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
