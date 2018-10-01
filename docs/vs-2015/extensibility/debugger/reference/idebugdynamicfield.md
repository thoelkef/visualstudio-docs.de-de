---
title: IDebugDynamicField | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e975940947b68fdce34bd7d1e2e289c85914c44
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523897"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugDynamicField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdynamicfield).  
  
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

