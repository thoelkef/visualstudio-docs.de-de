---
title: IDebugArrayObject2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc101fa7e0f339a599bd48f1954c0f6ed165f47f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102407"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt ein verwaltetes Array-Objekt dar und ermöglicht eine ausdrucksauswertung (EE), um zu bestimmen, den Basisindex (Untergrenze) für das Array.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugArrayObject2 : IDebugArrayObject  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Dies wird von der verwalteten Debugging-Modul (DE) implementiert.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden für die [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) diese Schnittstelle implementiert, die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Ruft den Basis-Indizes (Untergrenze) für jeden Index, der die Anzahl der Dimensionen im Array angegebenen ab.|  
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Bestimmt, ob das Array Basis Indizes (Untergrenze) definiert wurde.|  
  
## <a name="remarks"></a>Hinweise  
 Eine ausdrucksauswertung verwendet diese Schnittstelle, um verwaltete Arrays in einer Analysestruktur darzustellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll