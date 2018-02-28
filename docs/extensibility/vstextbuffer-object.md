---
title: VSTextBuffer Objekt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 643bd434e058a24cc17936d9ab2f333489b8aa5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="vstextbuffer-object"></a>VSTextBuffer-Objekt
Die TextBuffer-Objekt stellt einen Stream von Unicode-Text, der in der Regel von einer Datei zugeordnet ist. Ein <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt außerhalb des Kontexts des Editors Core im Falle eines Assistenten verwendet werden kann.  
  
 Die folgende Tabelle enthält die Schnittstellen der `VSTextBuffer`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Standard-OLE-Schnittstelle. Hauptsächlich verwendet für Rückgängigmachen/Wiederholen-Behandlung im Puffer.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Standard-OLE-Schnittstelle.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von Aktionen für zusammengesetzte Wörter (d. h., Aktionen, die in einer einzelnen Rückgängig/Wiederholen-Einheit gruppiert werden).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Aktiviert die Persistenz der Dokumentdaten, die von den Textpuffer verwaltet werden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Stellt grundlegende Dienste; von vielen Clients verwendet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Verwendet, um einen Puffer zu suchen.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Bietet Lese- / Funktionen, die mit einem zweidimensionalen Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Bietet Lese- / Funktionen, die über eindimensionale Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Bietet schnelle streamorientiertes, sequenziellen Zugriff auf den Text im Puffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Bietet Zugriff auf eine generische Auflistung von Eigenschaften. Die wichtigste Eigenschaft ist der Name oder der Moniker des Puffers. Sie können Ihren eigenen zufälligen Daten in den Puffer mit dieser Schnittstelle speichern, indem eine GUID erstellen und verwenden es als Schlüssel.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Unterstützt die Verbindungspunkte für Ereignisse.|  
  
## <a name="remarks"></a>Hinweise  
 Die `VSTextBuffer` befindet sich in der Regel durch einen `QueryInterface` Aufrufen auf `IVsTextBuffer`. Weitere Informationen finden Sie unter [Textpuffer](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Bearbeiten von Zahlen](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)