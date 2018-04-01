---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: cd6ead902a65a9f3e5e392b1b9dbeed135f326b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Diese Schnittstelle Listet die Code-Kontexte, die Debugsitzung, oder mit einem bestimmten Programm oder Dokument zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle, um eine Liste der Code Kontexten für einen bestimmten Textposition in einem Programm oder eine Liste von Code Kontexten für ein bestimmtes Dokumentenkontext darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) beim Abrufen dieser Schnittstelle, die eine Liste der Code Kontexten für eine Position bestimmten Text in einem Programm-Quelldokument darstellt.  
  
 Rufen Sie [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) beim Abrufen dieser Schnittstelle, die eine Liste aller Kontexte von Code in einem bestimmten Quelldokument darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugCodeContexts2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Ruft eine angegebene Anzahl von Kontexten ein Enumerationsfolge Code ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Überspringt eine angegebene Anzahl von Kontexten ein Enumerationsfolge Code an.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Setzt ein Enumerationsfolge auf den Anfang zurück.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumeration Status als der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Ruft die Anzahl von Kontexten Code in einen Enumerator ab.|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio-Aufrufe [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) der Benutzer kann wahlweise zum Auffüllen einer Liste von Kontexten Code aus, wenn die nächste Anweisung festlegen oder das Anzeigen der Disassembly für eine Quelldatei. Mehrere Kontexte von Code können z. B. auftreten, wenn mehrere Instanzen einer Vorlage im C++-Format vorliegen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)