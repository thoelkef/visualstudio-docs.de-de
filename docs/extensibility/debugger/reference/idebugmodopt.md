---
title: IDebugModOpt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e9a883c99bb41decbe0bbb53d2a4c484e021c07
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929295"
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