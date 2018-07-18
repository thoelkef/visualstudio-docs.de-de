---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a7c7dbc966c6c2747de4c969975ef8455cf6b0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116857"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Diese Schnittstelle stellt Bytes an Arbeitsspeicher.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Debugging-Modul (DE) implementiert diese Schnittstelle, um die Bytes im Speicher darzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) gibt diese Schnittstelle für den Zugriff auf den Systemarbeitsspeicher. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) und [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) diese Schnittstelle für den Zugriff auf ein Objekt Bytes zurück.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugMemoryBytes2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Liest eine Folge von Bytes, beginnend an einer angegebenen Position.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Schreibt `dwCount` Bytes, beginnend bei `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Ruft die Größe in Bytes des Speichers, der von dieser Schnittstelle dargestellt.|  
  
## <a name="remarks"></a>Hinweise  
 Für Eigenschaften ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, die ein Array darstellt bietet ein `IDebugMemoryBytes2` Schnittstelle, um den Zugriff auf die Werte in diesem Array zurück.  
  
 Visual Studio **Arbeitsspeicher Ansicht** Aufrufe [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) zum Abrufen einer `IDebugMemoryBytes2` Schnittstelle für den Zugriff auf den Systemarbeitsspeicher. Die Adresse zugegriffen werden abgerufen wird durch Analysieren des Ausdrucks als eine Adresse eingegeben werden, in die Speicher-Sicht und der anschließenden auswertungen der analysierten Ausdrucks mit [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) zum Abrufen einer `IDebugProperty2` Schnittstelle. Ein Aufruf von [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) gibt die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , beschreibt die Speicheradresse. Dieser Speicherkontext übergeben, [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) und [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)