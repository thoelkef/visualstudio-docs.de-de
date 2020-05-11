---
title: IDebugContainerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72296517a64c6dcfcb8e347fb00588504aa75a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733216"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Diese Schnittstelle stellt ein Symbol oder einen Typ dar, der ein Container für andere Symbole oder Typen ist.

## <a name="syntax"></a>Syntax

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbolanbieter implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) implementiert. Diese Schnittstelle ist auch die Basisklasse für alle Schnittstellen, die Container darstellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Viele Methoden auf vielen Schnittstellen geben diese Schnittstelle zurück. Da es sich um eine Basisklasse für alle Container handelt, können mithilfe von [QueryInterface](/cpp/atl/queryinterface)speziellere Schnittstellen über diese Schnittstelle abgerufen werden. Zu diesen Schnittstellen gehören [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)und [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden auf der [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) implementiert diese Schnittstelle die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Erstellt einen Enumerator für die Felder des Containers.|

## <a name="remarks"></a>Bemerkungen
 Arrays (Container für Variablen), Klassen (Container für Methoden und Variablen) und Methoden (Container für Parameter und lokale Variablen) sind Beispiele für Container.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
