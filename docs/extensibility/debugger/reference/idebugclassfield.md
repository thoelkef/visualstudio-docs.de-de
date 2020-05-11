---
title: IDebugClassField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b0e4cd7c851e65edf299f45ec97273804c25d8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734286"
---
# <a name="idebugclassfield"></a>IDebugClassField
Diese Schnittstelle stellt eine Klasse als Typ dar.

## <a name="syntax"></a>Syntax

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbolanbieter implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugContainerField-Schnittstelle](../../../extensibility/debugger/reference/idebugcontainerfield.md) implementiert. Diese Schnittstelle ist eine Spezialisierung, die einen Klassentyp darstellt.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Eine Reihe von Schnittstellen verfügen über Methoden, die diese Schnittstelle zurückgeben können, einschließlich [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)und [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). Außerdem können Sie [QueryInterface](/cpp/atl/queryinterface) verwenden, um diese Schnittstelle von der [IDebugContainerField-Schnittstelle](../../../extensibility/debugger/reference/idebugcontainerfield.md) abzusondern, wenn die [GetKind-Methode](../../../extensibility/debugger/reference/idebugfield-getkind.md) das Flag `FIELD_TYPE_CLASS`zurückgibt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden auf den [Schnittstellen IDebugField](../../../extensibility/debugger/reference/idebugfield.md) und [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) implementiert diese Schnittstelle Folgendes:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Erstellt einen Enumerator für die Basisklassen dieser Klasse.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Bestimmt, ob eine bestimmte Schnittstelle in der Klasse definiert ist.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Erstellt einen Enumerator für die geschachtelten Klassen dieser Klasse.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Ruft die Klasse ab, die diese Klasse umschließt.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Erstellt einen Enumerator für die von dieser Klasse implementierten Schnittstellen.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Erstellt einen Enumerator für die Konstruktoren dieser Klasse.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Ruft den Namen des Standardindexers ab.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Erstellt einen Enumerator für die geschachtelten Enumeratoren dieser Klasse.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
