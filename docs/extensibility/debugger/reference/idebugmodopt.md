---
title: IDebugModOpt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7585a303c8f4a37567d64b0a27f7a8560c3135f3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851536"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Stellt einen Debug-Optionaler Modifizierer.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugModOpt : IUnknown  
```  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Abgerufen aus einem [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, das eine Klasse oder Methode darstellt.  
  
## <a name="methods"></a>Methoden  
 Diese Schnittstelle implementiert die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Ruft eine Liste optionaler Modifizierer.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll