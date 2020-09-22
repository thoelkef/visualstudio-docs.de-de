---
title: Ienumdebugobjects | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d01e6340be0cb710d9173850e66fc18d543347d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841200"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt eine Auflistung von-Objekten dar, die die [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle implementieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Ausdrucks Auswertung implementiert diese Schnittstelle, um Sätze von Objekten bereitzustellen, die die [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle implementieren. Beachten Sie, dass es sich hierbei nicht um eine com-Standard Enumeration handelt, da die [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) -Methode vorhanden ist.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) gibt diese Schnittstelle zurück.  
  
## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge  
 Diese Schnittstelle implementiert die folgenden Methoden.  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Ruft den nächsten Satz von [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekten aus der-Enumeration ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Überspringt eine angegebene Anzahl von Einträgen.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Setzt die Enumeration auf den ersten Eintrag zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Ruft eine Kopie der aktuellen Enumeration ab.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Ruft die Anzahl der Einträge in der-Enumeration ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle ermöglicht es einer Debug-Engine, eine Gruppe von Objekten in einem Array aufzulisten.  
  
## <a name="requirements"></a>Anforderungen  
 Header: EE. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
