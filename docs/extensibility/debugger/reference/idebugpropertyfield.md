---
title: IDebugPropertyField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a3f3c2dca16cd2c28c9d1727e4ac145c91c482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720700"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Diese Schnittstelle stellt die Funktionen bereit, die das Abrufen und Festlegen einer Eigenschaft ermöglichen.

## <a name="syntax"></a>Syntax

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbolanbieter implementiert diese Schnittstelle für dasselbe Objekt, das das [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)implementiert. Diese Schnittstelle ist eine Spezialisierung, die das Konzept der Eigenschaften für eine Klasse unterstützt.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Verwenden Sie [QueryInterface,](/cpp/atl/queryinterface) um diese Schnittstelle von der [IDebugContainerField-Schnittstelle](../../../extensibility/debugger/reference/idebugcontainerfield.md) abzuholen, wenn die [GetKind-Methode](../../../extensibility/debugger/reference/idebugfield-getkind.md) zurückgibt. `FIELD_KIND_PROP`

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden auf den [Schnittstellen IDebugField](../../../extensibility/debugger/reference/idebugfield.md) und [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Ruft die Methode ab, die die Eigenschaft abruft.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Ruft die Methode ab, die die Eigenschaft festlegt.|

## <a name="remarks"></a>Bemerkungen
 Eine Eigenschaft ist ein verwaltetes Codekonzept und stellt eine Methode dar, die als Variable behandelt wird. Eigenschaften sind in nicht verwaltetem C++ nicht vorhanden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
