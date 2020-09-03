---
title: IDebugCustomAttributeQuery2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4bc592ff0198d4cc93d500c39167e214e63f032
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702586"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, ob ein benutzerdefiniertes Attribut für dieses Feld vorhanden ist, und gibt, sofern vorhanden, die Attributinformationen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) implementiert, um benutzerdefinierte Attribute zu unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) , um diese Schnittstelle von der [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle abzurufen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle werden die Methoden der **idebugcustomattributequery** -Schnittstelle angezeigt.  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Bestimmt, ob ein benutzerdefiniertes Attribut anhand des Namens vorhanden ist.|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Ruft die Attributinformationen für das angegebene benutzerdefinierte Attribut ab.|  
  
 Zusätzlich zu den **idebugcustomattributequery** -Methoden `IDebugCustomAttributeQuery2` implementiert die folgende Methode:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Ruft einen Enumerator für alle benutzerdefinierten Attribute ab, die an dieses Feld angefügt sind.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die [ienumdebugcustomattribute](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) -Methode kann einen Enumerator für alle für dieses Feld definierten benutzerdefinierten Attribute zurückgeben.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Symbol Anbieter Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
