---
title: IDebugMemoryContext2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f5a0533e2f7ce50dce7ccdf1285e4ab28a4b7a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146359"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt eine Position im Adressraum des Computers dar, auf dem das gedestete Programm ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (de) implementiert diese Schnittstelle, um eine Adresse im Arbeitsspeicher darzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird von einem [getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) -oder [getmemorycontext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) -Befehl zurückgegeben. Außerdem geben Aufrufe zum [addieren](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) und [subtrahieren](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) neue Kopien dieser Schnittstelle zurück, nachdem die entsprechende arithmetische Operation angewendet wurde.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugMemoryContext2` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Ruft den vom Benutzer anzeigbaren Namen für diesen Kontext ab.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Ruft Informationen ab, die diesen Kontext beschreiben.|  
|[Add (Hinzufügen)](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Fügt der Adresse des aktuellen Kontexts einen angegebenen Wert hinzu, um einen neuen Kontext zu erstellen.|  
|[Subtrahieren](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Subtrahiert einen angegebenen Wert von der Adresse des aktuellen Kontexts, um einen neuen Kontext zu erstellen.|  
|[Vergleichen](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Vergleicht zwei Kontexte in der durch Compare-Flags gekennzeichneten Weise.|  
  
## <a name="remarks"></a>Bemerkungen  
 Das Fenster Arbeits **Speicher** von Visual Studio ruft [getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) auf, um die `IDebugMemoryContext2` Schnittstelle abzurufen, die den ausgewerteten Ausdruck für die Speicheradresse enthält. Dieser Kontext wird dann an " [leseat](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) " und "Write" weitergegeben, um die zu lesende oder zu Schreib [Ende](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) Adresse anzugeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Getmemorycontext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [Getmemorycontext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt '](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
