---
title: IDebugDynamicField | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 41cf0e397834f337863baa46abb4e6bbccee98ad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198513"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Typ einer Variablen dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird als Basisklasse für jeden Typ von Symbol-Anbieter implementiert, die zur Laufzeit bestimmt werden kann. Dies ist nur für verwalteten Code.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle stellt eine Basisklasse, die von der spezialisiertere Schnittstellen abgeleitet werden können.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Diese Schnittstelle stellt keine Methoden außer den von geerbten `IDebugField`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
