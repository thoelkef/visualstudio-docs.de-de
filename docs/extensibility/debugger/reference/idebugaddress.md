---
title: IDebugAddress | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress
helpviewer_keywords: IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ea03ec205a4bc28f025b8539bc0abf3abc59ceaa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugaddress"></a>IDebugAddress
Diese Schnittstelle stellt die Adresse eines Elements dar. Es wird von der Symbol-Handler zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Symbol-Anbieter implementiert diese Schnittstelle, um eine Adresse eines Objekts darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Viele Methoden auf viele Schnittstellen geben diese Schnittstelle zurück.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Diese Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Ruft eine [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur, die beschreibt ein Objekt und dessen Speicherort.|  
  
## <a name="remarks"></a>Hinweise  
 Die Symbol-Anbieter gibt diese Schnittstelle, um ein Objekt und dessen Speicherort innerhalb eines bestimmten Bereichs (z. B. Funktion, Methode oder Klasse) darstellen. Diese Schnittstelle wird von zurückgegeben und auf verschiedenen-Methoden der Symbol-Anbieter und der Ausdruck übergeben bei der ausdrucksauswertung. Die Symbol-Anbieter ist in der Regel wird die einzige Entität, die zum Interpretieren des Inhalts dieser Schnittstelle muss.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbol-Anbieter-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)