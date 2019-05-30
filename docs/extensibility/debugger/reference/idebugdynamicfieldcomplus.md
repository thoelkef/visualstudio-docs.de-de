---
title: IDebugDynamicFieldCOMPlus | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 824498f3d7657bcc5984d31a1abaa4e97c4a9a7d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330199"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
Stellt ein dynamisches Feld für eine [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Objekt.

## <a name="syntax"></a>Syntax

```
IDebugDynamicFieldCOMPlus : IDebugDynamicField
```

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Ein Typ, der primitive Typ abgerufen.|
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Ruft einen Typ, dessen Token erhält.|

## <a name="requirements"></a>Anforderungen
 Header: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll