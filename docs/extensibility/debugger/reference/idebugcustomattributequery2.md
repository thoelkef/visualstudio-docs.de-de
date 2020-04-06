---
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe3969002c64ab361de76012c432e2bb5c61b5c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732490"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Bestimmt das Vorhandensein eines benutzerdefinierten Attributs für dieses Feld und gibt, falls vorhanden, die Attributinformationen zurück.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbolanbieter implementiert diese Schnittstelle für dasselbe Objekt, das [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) implementiert, um benutzerdefinierte Attribute zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Verwenden Sie [QueryInterface,](/cpp/atl/queryinterface) um diese Schnittstelle von der [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) abzufragen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der **IDebugCustomAttributeQuery-Schnittstelle.**

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Bestimmt, ob ein benutzerdefiniertes Attribut nach Namen vorhanden ist.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Ruft die Attributinformationen für das angegebene benutzerdefinierte Attribut ab.|

 Zusätzlich zu den **IDebugCustomAttributeQuery-Methoden** `IDebugCustomAttributeQuery2` implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Ruft einen Enumerator für alle benutzerdefinierten Attribute ab, die diesem Feld zugeordnet sind.|

## <a name="remarks"></a>Bemerkungen
 Die [IEnumDebugCustomAttributes-Methode](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) kann einen Enumerator für alle benutzerdefinierten Attribute zurückgeben, die für dieses Feld definiert sind.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
