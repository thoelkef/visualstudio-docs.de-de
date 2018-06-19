---
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7efc14b3d2bad9111e12328c29960ef991e8a4f9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107620"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Bestimmt, ob ein benutzerdefiniertes Attribut für dieses Feld vorhanden ist und, falls vorhanden, gibt die Attributinformationen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Symbol-Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das implementiert [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) um benutzerdefinierte Attribute zu unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwendung [QueryInterface](/cpp/atl/queryinterface) beim Abrufen dieser Schnittstelle aus dem [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der **IDebugCustomAttributeQuery** Schnittstelle.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Bestimmt, ob ein benutzerdefiniertes Attribut anhand des Namens vorhanden ist.|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Ruft die Informationen über Bildattribute für den angegebenen benutzerdefinierten Attributs ab.|  
  
 Zusätzlich zu den **IDebugCustomAttributeQuery** Methoden `IDebugCustomAttributeQuery2` implementiert die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Ruft einen Enumerator für alle benutzerdefinierten Attribute, die mit diesem Feld verbunden.|  
  
## <a name="remarks"></a>Hinweise  
 Die [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) Methode kann einen Enumerator für alle für dieses Feld definierten benutzerdefinierten Attribute zurück.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbol-Anbieter-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)