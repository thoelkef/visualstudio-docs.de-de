---
title: IDebugMethodField | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b42f37e0418ec354b522da102adaff3653cfc6a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Diese Schnittstelle wird eine Methode beschrieben.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Symbol-Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstelle. Diese Schnittstelle ist eine Spezialisierung, in dem eine Methode dargestellt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwendung [QueryInterface](/cpp/atl/queryinterface) beim Abrufen dieser Schnittstelle aus der [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstelle, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) gibt `FIELD_TYPE_METHOD`. Darüber hinaus die Methoden [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), und [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), alle return die `IDebugMethodField` Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) und [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstellen, die diese Schnittstelle implementiert, die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Erstellt einen Enumerator für die Parameter der Methode.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Ruft die Zeiger "this" des Objekts mit der Methode ab.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Erstellt einen Enumerator für alle lokalen Variablen der Methode.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Erstellt einen Enumerator für die ausgewählten lokalen Variablen der Methode.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Bestimmt, ob ein bestimmtes benutzerdefiniertes Attribut definiert wurde.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Erstellt einen Enumerator für statische lokale Variablen der Methode.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Ruft den globalen Container der Methode ab.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Erstellt einen Enumerator für den Typ jedes Arguments erforderlich, um die Methode aufzurufen.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Methode kann es sich um Parameter als auch für lokale Variablen enthalten.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbol-Anbieter-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)