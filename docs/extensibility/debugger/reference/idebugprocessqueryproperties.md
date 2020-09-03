---
title: Idebugprocessqueryproperties | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723278"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Diese Schnittstelle ist eine von [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) Implementierern implementierte Erweiterungsschnittstelle. Sie ermöglicht es dem Implementierer, Informationen zur debugprozessumgebung zu erhalten.

## <a name="syntax"></a>Syntax

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Implementieren Sie diese Schnittstelle, um Informationen zur Ausführungsumgebung eines Debugprozesses zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProcessQueryProperties` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Fragt nach einem Eigenschafts Wert ab.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Fragt nach Eigenschafts Werten ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle ist selten implementiert.

## <a name="requirements"></a>Anforderungen
 Header: portpriv. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
