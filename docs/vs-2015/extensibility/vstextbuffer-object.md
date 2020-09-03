---
title: Vstextbuffer-Objekt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b68d443e542b6bd707aacc2b22d0efc1064152c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690646"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer-Objekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Text Puffer Objekt stellt einen Stream von Unicode-Text dar, der in der Regel mit einer Datei verknüpft ist. Ein- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt kann außerhalb des Kontexts des Kern Editors verwendet werden, wie im Fall eines Assistenten.  
  
 In der folgenden Tabelle werden die Schnittstellen von angezeigt `VSTextBuffer` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|Standard-OLE-Schnittstelle. Wird hauptsächlich für die rückgängig-/Wiederholungsbehandlung im Puffer verwendet.|  
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Standard-OLE-Schnittstelle.|  
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von zuordnungsaktionen (d. h. Aktionen, die in einer einzelnen Rückgängig/Wiederholen-Einheit gruppiert sind).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Ermöglicht die Persistenz von Dokument Daten, die vom Text Puffer verwaltet werden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Stellt grundlegende Dienste bereit. wird von vielen Clients verwendet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Wird zum Durchsuchen eines Puffers verwendet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Bietet Lese-und Schreibfunktionen mit zweidimensionalen Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Bietet Lese-und Schreibfunktionen mithilfe eindimensionaler Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Bietet schnellen, streamorientierten, sequenziellen Zugriff auf Text im Puffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Ermöglicht den Zugriff auf eine generische Auflistung von Eigenschaften. Die wichtigste Eigenschaft ist der Name oder Moniker des Puffers. Mit dieser Schnittstelle können Sie Ihre eigenen zufälligen Daten im Puffer speichern, indem Sie eine GUID erstellen und Sie als Schlüssel verwenden.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Unterstützt Verbindungspunkte für Ereignisse.|  
  
## <a name="remarks"></a>Bemerkungen  
 Der `VSTextBuffer` wird normalerweise durch einen- `QueryInterface` Aufrufwert gefunden `IVsTextBuffer` . Weitere Informationen finden Sie unter [Text Puffer](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Abbildungen bearbeiten](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
