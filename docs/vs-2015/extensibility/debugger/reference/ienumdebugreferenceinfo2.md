---
title: IEnumDebugReferenceInfo2 | Microsoft-Dokumentation
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
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 891022c12d3fe463c165653b5bf0b054efa751d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514730"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IEnumDebugReferenceInfo2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugreferenceinfo2).  
  
Diese Schnittstelle listet [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle als Teil der Unterstützung für Verweise auf Objekte im Arbeitsspeicher. Diese Schnittstelle muss implementiert werden, nur dann, wenn Verweise unterstützt werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Visual Studio-Aufrufe [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) dieser Schnittstelle abgerufen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugReferenceInfo2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Ruft eine angegebene Anzahl von [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen in einer Enumerationsfolge.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Überspringt eine angegebene Anzahl von [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen in der Enumerationsfolge.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Ruft die Anzahl der [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen in einem Enumerator.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Verweis ist im Wesentlichen ein Typ und eine Adresse, während eine Eigenschaft einen Namen, den Typ und die Adresse ist. Ein Verweis beibehalten, bis das Objekt bezeichnet, im Arbeitsspeicher vorhanden sind. Finden Sie unter [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Weitere Details.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)

