---
title: Idebugalias | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6c05b6987804681176abdde0e8c94a7463a9163c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840982"
---
# <a name="idebugalias"></a>IDebugAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt einen numerischen Alias für eine Variable dar. Ein Alias ist einfach ein anderer Name für eine Variable.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von der Ausdrucks Auswertung (EE) implementiert, um numerische Aliase für Variablen zu unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 " [Aliatealias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) " erstellt einen Alias für ein bestimmtes Objekt. Wenn Sie nach Aliasen suchen möchten, verwenden Sie [findalias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) oder [getallaliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgenden Methoden werden in der- `IDebugAlias` Schnittstelle definiert.  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Ruft das-Objekt ab, auf das dieser Alias verweist.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Ruft den Aliasnamen ab.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Ruft eine `ICorDebugValue` Schnittstelle ab, die Zugriff auf Informationen zu verwaltetem Code über dieses Objekt bietet (nur verwalteter Code).|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Markiert diesen Alias als nicht mehr verwendet.|  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Alias ist eine Dezimalzahl in Form von Zeichen folgen, gefolgt vom #-Zeichen, z. b. 1001 #.  
  
## <a name="requirements"></a>Anforderungen  
 Header: EE. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucks Bewertungs Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 ["Kreatealias"](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [Findalias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
