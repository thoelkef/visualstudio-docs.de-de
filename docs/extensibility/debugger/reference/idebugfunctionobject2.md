---
title: IDebugFunctionObject2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47ad3e889568b260d63ca0a38be58994f6966384
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035457"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt eine Funktion dar, und verbessert die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Eine ausdrucksauswertung (EE) implementiert diese Schnittstelle, um die Funktion dar.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Methoden dieser Schnittstelle zu verzögern, denen der **IDebugFunctionObject** auf folgende Weise:  
  
-   Die **IDebugEvaluate** Methode akzeptiert die Kennzeichen.  
  
-   Die **CreateObject** Methode akzeptiert die Kennzeichen und ein Timeout.  
  
-   Die **CreateStringObjectWithLength** Methode akzeptiert eine Länge.  
  
## <a name="methods"></a>Methoden  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Erstellt ein Objekt, das einen Konstruktor, der angegebenen Einstellungen für die Evaluierung und einen Timeoutwert verwendet.|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Erstellt ein String-Objekt, das die angegebene Länge aufweist.|  
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Ruft die Funktion und der resultierende Wert als Objekt zurückgegeben.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: EE.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll