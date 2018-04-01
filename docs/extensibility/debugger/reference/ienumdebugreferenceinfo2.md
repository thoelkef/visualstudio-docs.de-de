---
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9c7bcba4207e5caa14b9db27f2d9b243376c6d01
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Diese Schnittstelle listet [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle als Teil der Unterstützung für Verweise auf Objekte im Arbeitsspeicher. Diese Schnittstelle muss implementiert werden, nur dann, wenn Verweise unterstützt werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Visual Studio-Aufrufe [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) beim Abrufen dieser Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugReferenceInfo2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Ruft eine angegebene Anzahl von [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen in eine Enumerationsfolge.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Überspringt die angegebene Anzahl von [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen in die Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Setzt ein Enumerationsfolge auf den Anfang zurück.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumeration Status als der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Ruft die Anzahl der [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen in einen Enumerator.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Verweis ist im Wesentlichen ein Typ und eine Adresse, eine Eigenschaft ist ein Name, Typ und Adresse. Ein Verweis weiterhin besteht, solange das Objekt bezeichnet, im Arbeitsspeicher vorhanden ist. Finden Sie unter [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Weitere Details.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)