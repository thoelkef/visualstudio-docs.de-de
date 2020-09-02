---
title: Idebugdynamicfieldcomplus | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 823057303655da59494680ce9f591b252e28f792
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731227"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
Stellt ein dynamisches Feld für ein [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Objekt dar.

## <a name="syntax"></a>Syntax

```
IDebugDynamicFieldCOMPlus : IDebugDynamicField
```

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die [idebugdynamicfield](../../../extensibility/debugger/reference/idebugdynamicfield.md) -Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Ruft einen Typ ab, der den primitiven Typ erhält.|
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Ruft einen Typ ab, der sein Token erhält.|

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
