---
title: IEnumDebugCodeContexts2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75765f714bd52d7e7b01eca15e451152ceba54a7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980583"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Diese Schnittstelle Listet die Codekontexte auf, mit der Debugsitzung oder einem bestimmten Programm oder Dokument zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um eine Liste von Kontexten, Code für eine Position im bestimmten Text in einem Programm oder eine Liste von Kontexten, Code für ein bestimmtes Dokumentkontext darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) beim Abrufen der diese Schnittstelle, die eine Liste von Kontexten, Code für eine bestimmte Textposition im Quelldokument eines Programms darstellt.  
  
 Rufen Sie [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) beim Abrufen der diese Schnittstelle, die eine Liste mit allen Code-Kontexten in einem bestimmten Quelldokument darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugCodeContexts2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Ruft eine angegebene Anzahl von Kontexten, Code in einer Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Überspringt eine angegebene Anzahl von Kontexten, Code in einer Enumerationsfolge.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Ruft die Anzahl von Kontexten, Code in einen Enumerator ab.|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio-Aufrufe [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) zum Auffüllen einer Liste von Kontexten, Code wahlweise kann der Benutzer aus, wenn die nächste Anweisung festlegen oder die Disassemblierung für eine Quelldatei angezeigt. Mehrere Codekontexte können beispielsweise auftreten, wenn mehrere Instanzen einer Vorlage im C++-Stil vorhanden sind.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)