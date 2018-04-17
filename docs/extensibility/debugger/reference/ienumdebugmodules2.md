---
title: IEnumDebugModules2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd3ca02776aae4a7b4cd22485eba9827f4731d5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Diese Schnittstelle Listet die Module.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle, um eine Liste der für ein Programm geladene Module darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Visual Studio-Aufrufe [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) beim Abrufen dieser Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugModules2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Ruft eine angegebene Anzahl von Modulen in einem Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Überspringt eine angegebene Anzahl von Modulen in einem Enumerationsfolge an.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Setzt ein Enumerationsfolge auf den Anfang zurück.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumeration Status als der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Ruft die Anzahl der Module ab.|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio verwendet diese Schnittstelle in erster Linie zum Aktualisieren der **Module** Fenster.  
  
 Für die Zwecke des Debuggens in Visual Studio können ein Programm ist eine logische Sequenz von Code-Anweisungen, die übertragen werden hinweg, daher kann die Notwendigkeit für eine Liste der Module für eine einzelne [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle. Das erste Modul in der Liste enthält in der Regel den ersten Einstiegspunkt für das zugeordnete Programm.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)