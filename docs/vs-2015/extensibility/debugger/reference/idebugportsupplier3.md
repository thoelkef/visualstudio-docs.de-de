---
title: IDebugPortSupplier3 | Microsoft-Dokumentation
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
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14a4e9f704cc5a863030ae6041f3d93276ecf18e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522047"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugPortSupplier3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplier3).  
  
Diese Schnittstelle ermöglicht es einen Aufrufer, die bestimmen, ob ein portanbieters beizubehalten, die Ports (auf Datenträger schreiben) zwischen den Aufrufen des Debuggers und Sie anschließend eine Liste mit diesen beibehaltenen Ports rufen kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle zum beibehalten oder Speichern von Informationen auf dem Datenträger unterstützt. Diese Schnittstelle muss implementiert werden, auf das gleiche Objekt wie die [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf die `IDebugPortSupplier2` Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden der [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) Schnittstelle, die diese Schnittstelle unterstützt die folgenden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Gibt zurück, ob die anschlusslieferant Ports gespeichert werden kann (indem sie auf den Datenträger geschrieben werden müssen) zwischen den Aufrufen des Debuggers.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Gibt ein Objekt, das verwendet werden kann zum Aufzählen über alle Ports, die auf den Datenträger geschrieben wurden, von diesem anschlusslieferant zurück.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein portanbieters Ports über Aufrufe hinweg beibehalten kann, sollten sie diese Schnittstelle implementieren. Ports sollte geladen werden, wenn Anschlusslieferanten instanziiert ist, und wenn Anschlusslieferanten zerstört wird auf den Datenträger geschrieben.  
  
 Eine Debug-Engine ist in der Regel interagiert nicht mit eines portanbieters und hat keine Verwendung für diese Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)

