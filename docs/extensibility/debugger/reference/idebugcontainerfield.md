---
title: IDebugContainerField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c93113f89c11e787a23cc57dfbebcce882125091
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922285"
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