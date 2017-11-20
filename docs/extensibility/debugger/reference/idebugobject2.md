---
title: IDebugObject2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2
helpviewer_keywords: IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6072d88bf6e065c7f9f72b5e6d1ffab0dcc46d03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle bietet zusätzliche Informationen zu einem Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung implementiert diese Schnittstelle, um Unterstützung für Aliase und den Zugriff auf Informationen über das Objekt zu bieten.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle kann mithilfe dieser Schnittstelle abrufen [QueryInterface](/cpp/atl/queryinterface). Darüber hinaus [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) gibt diese Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle, die `IDebugObject2` Schnittstelle implementiert die folgenden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Ruft das Feld oder eine Variable (sofern vorhanden), die von diesem Objekt dargestellte Eigenschaft sichern.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Ruft das verwaltetem Code-Objekt, das den Wert dieses Objekts darstellt.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Erstellt eine eindeutige ID für dieses Objekt fest oder gibt einen vorhandenen Alias.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Ruft den Alias, der diesem Objekt zugeordneten ab, sofern vorhanden.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Ruft den Typ dieses Objekts ab.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Bestimmt, ob dieses Objekt Benutzerdaten darstellt.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Bestimmt, ob der Status bearbeiten und Fortfahren nicht mehr gültig ist.<br /><br /> Eine benutzerdefinierte ausdrucksauswertung diese Methode nicht implementiert (es sollten stets `E_NOTIMPL`).|  
  
## <a name="remarks"></a>Hinweise  
 Finden Sie unter [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) eine Diskussion zur Aliase.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdruck Auswertung Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)