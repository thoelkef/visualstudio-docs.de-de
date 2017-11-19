---
title: IDebugAlias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias
helpviewer_keywords: IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 128dc9001faba06b1c95c5ebc364f319891ce409
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt einen numerische Alias für eine Variable dar. Ein Alias ist einfach einen anderen Namen für eine Variable.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung (EE) implementiert diese Schnittstelle, um numerische Aliase für Variablen zu unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) einen Alias für ein bestimmtes Objekt erstellt. Verwenden Sie zum Suchen von Aliasen [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) oder [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgenden Methoden definiert werden, dem `IDebugAlias` Schnittstelle.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Ruft das Objekt, das auf den dieser Alias verweist.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Ruft den Aliasnamen ab.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Ruft eine `ICorDebugValue` -Schnittstelle, die Zugriff auf verwaltete Code-Informationen zu diesem Objekt (nur verwalteter Code).|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Kennzeichnet dieses alias als nicht mehr verwendet wird.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Alias ist eine Dezimalzahl in Form einer Zeichenfolge gefolgt vom #-Zeichen, z. B. 1001#.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdruck Auswertung Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)