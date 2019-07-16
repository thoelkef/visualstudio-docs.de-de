---
title: IDebugDynamicField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58a4838afc0d52ab60ae0a11de419393d68dfc06
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351342"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Diese Schnittstelle stellt einen Typ einer Variablen dar.

## <a name="syntax"></a>Syntax

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird als Basisklasse für jeden Typ von Symbol-Anbieter implementiert, die zur Laufzeit bestimmt werden kann. Dies ist nur für verwalteten Code.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle stellt eine Basisklasse, die von der spezialisiertere Schnittstellen abgeleitet werden können.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle stellt keine Methoden außer den von geerbten `IDebugField`.

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)