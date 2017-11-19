---
title: IDebugCodeContext2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCodeContext2
helpviewer_keywords: IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e9e003372e390d7e807f314555310c167bf011a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Diese Schnittstelle stellt die Anfangsposition des Code-Anweisung dar. Für die meisten-Laufzeit-Architekturen kann heute ein Codekontext als eine Adresse im Datenstrom der Ausführung des Programms betrachtet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Debugging-Modul implementiert diese Schnittstelle, um die Position der Anweisung Code an eine Dokumentposition beziehen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Methoden für viele Schnittstellen zurückgeben dieser Schnittstelle i. d. r. [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Sie dient auch umfassend mit der [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) Schnittstelle auch wie Haltepunktinformationen-Auflösung.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) diese Schnittstelle implementiert, die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Ruft den Dokumentenkontext, der den Kontext aktiven Code entspricht.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ruft die Sprachinformationen für diesen Codekontext ab.|  
  
## <a name="remarks"></a>Hinweise  
 Der Hauptunterschied zwischen einer `IDebugCodeContext2` Schnittstelle und eine [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Schnittstelle ist, die eine `IDebugCodeContext2` ist immer Anweisung ausgerichtet. Dies bedeutet, dass ein `IDebugCodeContext2` muss immer auf den Anfang einer Anweisung verweisen, wohingegen ein `IDebugMemoryContext2` können eventuell Hinweise auf jedes Byte des Arbeitsspeichers in der Laufzeit-Architektur. `IDebugCodeContext2`wird über die Anweisungen statt über die grundlegenden Speichergröße (in der Regel Byte) erhöht.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [Nächste Anweisung festlegen](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)