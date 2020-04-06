---
title: IDebugProcessQueryEigenschaften | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08abf401b4e8f0e7a33d882e8178d77e6f248318
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723278"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Diese Schnittstelle ist eine Erweiterungsschnittstelle, die von [IDebugProcess2-Implementierern](../../../extensibility/debugger/reference/idebugprocess2.md) implementiert wird. Es ermöglicht dem Implementierer, Informationen über die Debugprozessumgebung abzubekommen.

## <a name="syntax"></a>Syntax

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Implementieren Sie diese Schnittstelle, um Informationen über die Ausführungsumgebung eines Debugvorgangs abzubekommen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugProcessQueryProperties`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Abfragen für einen Eigenschaftswert.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Abfragen für Eigenschaftswerte.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird selten implementiert.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
