---
title: IDebugExpressionEvaluator2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 840f9be067d591b27bda6a01b6469699524787d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841298"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt eine erweiterte Version einer Ausdrucks Auswertung (EE) dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird durch eine Ausdrucks Auswertung implementiert.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden für die [idebugexpressionevaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) -Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Ruft ein Dienst Objekt unter Berücksichtigung des eindeutigen Bezeichners ab.|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Lädt die vom angegebenen Symbol Anbieter bezeichneten Module vorab.|  
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Ermöglicht es der Ausdrucks Auswertung (EE), die Rückruf Schnittstelle anzugeben, die die Debugger-Engine (de) zum Lesen von Metrikeinstellungen verwendet.|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Legt den Pfad zu dem im Debugger geladenen Common Language Runtime (CLR) fest.|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Ermöglicht es einer Debug-Engine, während der Initialisierung einen Rückruf an die Ausdrucks Auswertung zu übergeben.|  
|[Terminate](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Beendet und bereinigt die Ausdrucks Auswertung.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: EE. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
