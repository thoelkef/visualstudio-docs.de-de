---
title: IDebugContainerField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d633b7e42f8c7f64a818539694837b954ea31e72
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332513"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Diese Schnittstelle stellt ein Symbol oder ein Typ, der ein Container für andere Symbole oder Typen ist.

## <a name="syntax"></a>Syntax

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein symbolanbieter implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle. Diese Schnittstelle ist auch die Basisklasse für alle Schnittstellen, die Container darstellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Viele Methoden für viele Schnittstellen zurückgeben dieser Schnittstelle. Da es sich um eine Basisklasse für alle Container handelt, spezialisiertere Schnittstellen erhalten Sie von dieser Schnittstelle mit [QueryInterface](/cpp/atl/queryinterface). Diese Schnittstellen umfassen [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), und [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden für die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle, die diese Schnittstelle implementiert, die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Erstellt einen Enumerator für die Felder des Containers.|

## <a name="remarks"></a>Hinweise
 Arrays (Container für Variablen), (Container für Methoden und Variablen)-Klassen und Methoden (der Container für Parameter und lokalen Variablen) sind Beispiele für Container.

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)