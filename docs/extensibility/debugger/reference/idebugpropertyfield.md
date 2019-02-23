---
title: IDebugPropertyField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c3376a6b8d6d269cac1f376e3f7f3f6f8a036f0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709628"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Diese Schnittstelle bietet die Funktionen, die es ermöglichen, abrufen und Festlegen einer Eigenschaft an.

## <a name="syntax"></a>Syntax

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein symbolanbieter implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Diese Schnittstelle ist eine Spezialisierung, die das Konzept der Eigenschaften einer Klasse unterstützt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwenden [QueryInterface](/cpp/atl/queryinterface) dieser Schnittstelle vom Abrufen der [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstelle, wenn die [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) Methodenrückgabe `FIELD_KIND_PROP`.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden für die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) und [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstellen, die diese Schnittstelle implementiert die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Ruft die Methode ab, die die Eigenschaft abruft.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Ruft die Methode ab, die die Eigenschaft festlegt.|

## <a name="remarks"></a>Hinweise
 Eine Eigenschaft ist ein Konzept von verwaltetem Code und stellt eine Methode, die als Variable behandelt wird. Eigenschaften sind in nicht verwaltetem C++ nicht vorhanden.

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)