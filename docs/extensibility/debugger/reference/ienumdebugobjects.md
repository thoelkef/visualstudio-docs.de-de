---
title: IEnumDebugObjects | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c8f62f4a153ac5c5966721578313245fc02f7d04
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt eine Auflistung von Objekten, die Implementierung der [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung implementiert diese Schnittstelle, um Gruppen von Objekten bereitstellen, die implementieren die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle. Beachten Sie, dass dies keiner standardmäßigen COM-Enumeration kann wegen des Vorhandenseins der [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) Methode.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) gibt diese Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Diese Schnittstelle implementiert die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Ruft den nächsten Satz von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekte aus der Enumeration.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Überspringt eine angegebene Anzahl von Einträgen.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Setzt die Enumeration an den ersten Eintrag zurück.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Ruft eine Kopie der aktuellen Enumeration.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Ruft die Anzahl der Einträge in der Enumeration ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ermöglicht es sich um ein Debugmodul an eine Gruppe von Objekten in einem Array aufgelistet werden sollen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)