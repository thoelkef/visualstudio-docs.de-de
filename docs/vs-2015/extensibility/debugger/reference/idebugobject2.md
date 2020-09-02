---
title: IDebugObject2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 979ede5601f1f31ca972bb9067b626954b1296f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695200"
---
# <a name="idebugobject2"></a>IDebugObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt zusätzliche Informationen zu einem Objekt bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Ausdrucks Auswertung implementiert diese Schnittstelle, um Aliase und Zugriff auf Informationen über das Objekt zu unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Eine [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle kann diese Schnittstelle mithilfe von [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)abrufen. Außerdem gibt [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) diese Schnittstelle zurück.  
  
## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle implementiert die- `IDebugObject2` Schnittstelle Folgendes:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Ruft das Feld oder die Variable (sofern vorhanden) ab, die möglicherweise die von diesem-Objekt dargestellte Eigenschaft unterstützt.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Ruft das verwaltete Code Objekt ab, das den Wert dieses-Objekts darstellt.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Erstellt eine eindeutige ID für dieses Objekt oder gibt einen vorhandenen Alias zurück.|  
|[Getalias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Ruft den Alias ab, der diesem-Objekt zugeordnet ist, sofern vorhanden.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Ruft den Typ dieses-Objekts ab.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Bestimmt, ob dieses-Objekt Benutzerdaten darstellt.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Bestimmt, ob der Zustand "Bearbeiten und Fortfahren" nicht mehr gültig ist.<br /><br /> Diese Methode wird von einer benutzerdefinierten Ausdrucks Auswertung nicht implementiert (Sie sollte immer zurückgeben `E_NOTIMPL` ).|  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Erläuterung zu Aliasen finden Sie unter [idebugalias](../../../extensibility/debugger/reference/idebugalias.md) .  
  
## <a name="requirements"></a>Anforderungen  
 Header: EE. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucks Bewertungs Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md)   
 [Idebugalias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
