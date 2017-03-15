---
title: "IDebugDocumentTextEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents2-Schnittstelle"
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird verwendet, um Visual Studio über Änderungen im Quelldokument zu benachrichtigen, die durch das Debugmodul angegeben werden.  
  
## Syntax  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, um das Vornehmen von Änderungen am Quellcode zu unterstützen.  Diese Schnittstelle wird normalerweise im selben Objekt implementiert, das die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\-Schnittstelle implementiert.  
  
## Hinweise für Aufrufer  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] erhält diese Schnittstelle durch einen Aufruf der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>\-Methode.  Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>\-Schnittstelle wird von einem Aufruf der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>\-Methode abgerufen.  Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>\-Schnittstelle wird abgerufen, indem die [QueryInterface](/visual-cpp/atl/queryinterface)\-Methode für eine [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\-Schnittstelle aufruft.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugDocumentTextEvents2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Gibt an, dass das gesamte Dokument zerstört wurde.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Benachrichtigt das Debuggen Paket, das Text in das Dokument eingefügt wurde.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Benachrichtigt das Debuggen Paket, das Text aus dem Dokument entfernt wurde.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Benachrichtigt das Debuggen Paket, das Text im Dokument ersetzt wurde.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Benachrichtigt das Paket debuggen, das Attribute wurden aktualisiert simsen im Dokument.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Benachrichtigt Empfänger auf das Ereignis, dass die Attribute aktualisiert wurden.|  
  
## Hinweise  
 Debuggen Sie nur Module, die ihre eigenen Dokumente verarbeiten würden die `IDebugDocumentTextEvent2`\-Schnittstelle bereitstellen.  Ein Beispiel hierfür ist eine Debug\- Modul der Skripterstellung sein.  Bei dem Interpretieren von Skripts kann neuer Quellcode generiert werden, der in keiner Datei auf einem Datenträger vorhanden ist und nur auf DE bekannt ist.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)