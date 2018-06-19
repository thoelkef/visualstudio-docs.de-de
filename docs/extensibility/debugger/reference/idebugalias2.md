---
title: IDebugAlias2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15fbf639c15e62b19e112ad140517f096d49f9d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103213"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt einen numerische Alias für eine Variable dar und ermöglicht eine ausdrucksauswertung (EE), um die Anwendungsdomäne für den Alias zu erhalten.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von der verwalteten Debugging-Modul (DE) implementiert.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden für die [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) diese Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Ruft den Bezeichner für die Anwendungsdomäne ab.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Alias ist eine Dezimalzahl in Form einer Zeichenfolge gefolgt vom #-Zeichen, z. B. 1001#.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll