---
title: IDebugMemoryBytes2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80bf7aa4ad16fd2f213f2761779195b36e126b29
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180790"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt die Bytes im Arbeitsspeicher dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um die Bytes im Speicher darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) gibt diese Schnittstelle für den Zugriff auf den Systemspeicher. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) und [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) diese Schnittstelle für den Zugriff auf ein Objekt des Bytes zurück.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugMemoryBytes2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Liest eine Folge von Bytes, beginnend ab einem bestimmten Standort.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Schreibt `dwCount` Bytes, beginnend bei `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Ruft die Größe in Bytes des Arbeitsspeichers, die von dieser Schnittstelle dargestellt.|  
  
## <a name="remarks"></a>Hinweise  
 Informationen zu Eigenschaften eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle, ein Array darstellt, bietet ein `IDebugMemoryBytes2` Schnittstelle, um den Zugriff auf die Werte im Array.  
  
 Visual Studio **Speicheransicht** Aufrufe [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) zum Abrufen einer `IDebugMemoryBytes2` Schnittstelle für den Zugriff auf den Systemspeicher. Die Adresse zugegriffen werden kann, wird abgerufen durch Analysieren des Ausdrucks als eine Adresse eingegeben werden, in der Ansicht für Arbeitsspeicher und anschließende Evaluierung der analysierten Ausdruck mit [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) zum Abrufen einer `IDebugProperty2` Schnittstelle. Ein Aufruf von [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) gibt die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , beschreibt die Speicheradresse. Dieser Speicherkontext übergeben, [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) und [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

