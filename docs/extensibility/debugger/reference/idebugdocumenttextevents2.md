---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentTextEvents2
helpviewer_keywords: IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bb9e284435cdf8a5905e068b0044cd118a1621c9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Diese Schnittstelle wird verwendet, um Visual Studio zu Änderungen an das Quelldokument zu benachrichtigen, die durch die Debugging-Modul bereitgestellt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, um dadurch Änderungen auf den Quellcode zu unterstützen. Diese Schnittstelle wird in der Regel implementiert, auf das gleiche Objekt, implementiert die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Ruft diese Schnittstelle über einen Aufruf der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> Methode. Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle wird abgerufen, von einem Aufruf der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> Methode. Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle durch den Aufruf abgerufen wird die [QueryInterface](/cpp/atl/queryinterface) Methode auf eine [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugDocumentTextEvents2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Gibt an, dass das gesamte Dokument zerstört wurde.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Benachrichtigt dem debugpaket an, dass Text in das Dokument eingefügt wurde.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Benachrichtigt dem debugpaket an, dass Text aus dem Dokument entfernt wurde.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Benachrichtigt dem debugpaket über Text in das Dokument ersetzt wurde.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Benachrichtigt dem debugpaket an, dass Textattribute im Dokument aktualisiert wurden.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Benachrichtigt Empfänger des Ereignisses, dass das Dokumentattribute aktualisiert wurden.|  
  
## <a name="remarks"></a>Hinweise  
 Nur die Debugmodule, die ihre eigenen Dokumente liefern nutzen würde die `IDebugDocumentTextEvent2` Schnittstelle. Ein Beispiel hierfür wäre eine Debug-Skriptmodul. Beim Interpretieren von Skripts, kann neue Quellcode generiert werden, die nicht in jeder Datei vorhanden ist, und wird nur für das DE bezeichnet.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)