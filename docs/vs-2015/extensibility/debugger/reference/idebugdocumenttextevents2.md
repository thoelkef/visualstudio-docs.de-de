---
title: IDebugDocumentTextEvents2 | Microsoft-Dokumentation
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
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d7fb3c64c1cdbd0e52753b6cd7ec4da197d22f4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797285"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle wird verwendet, um Visual Studio zu Änderungen bei Quelldokument zu benachrichtigen, die von der Debug-Engine bereitgestellt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um Änderungen an den Quellcode zu unterstützen. Diese Schnittstelle wird in der Regel implementiert, für das gleiche Objekt, das implementiert die [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Ruft diese Schnittstelle durch einen Aufruf der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> Methode. Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle wird von einem Aufruf von Abrufen der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> Methode. Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle wird abrufen durch Aufrufen der [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) Methode für ein [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugDocumentTextEvents2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Gibt an, dass das gesamte Dokument zerstört wurde.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Benachrichtigt dem debugpaket an, dass Text in das Dokument eingefügt wurde.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Benachrichtigt dem debugpaket an, dass Text aus dem Dokument entfernt wurde.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Benachrichtigt dem debugpaket, dass im Dokument Text ersetzt wurde.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Benachrichtigt dem debugpaket, Text-Attribute im Dokument aktualisiert wurden.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Benachrichtigt Empfänger des Ereignisses, dass die Attribute des Dokuments aktualisiert wurden.|  
  
## <a name="remarks"></a>Hinweise  
 Nur Debug-Engines, die ihre eigenen Dokumente angeben nutzen würden die `IDebugDocumentTextEvent2` Schnittstelle. Ein Beispiel hierfür wäre eine Skript DebugEngine. Beim Interpretieren von Skripts, kann neue Quellcode generiert werden, die nicht in jeder Datenträgerdatei vorhanden ist, und wird nur für das DE bezeichnet.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

