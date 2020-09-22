---
title: 'Gewusst wie: Verwenden von Text Markern | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841004"
---
# <a name="how-to-use-text-markers"></a>Vorgehensweise: Verwenden von Textmarkierungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Text Marker können angewendet werden, um ein-Objekt zu bearbeiten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
## <a name="procedures"></a>Prozeduren  
  
#### <a name="to-apply-text-markers"></a>So wenden Sie Textmarker an  
  
1. Rufen Sie eine Instanz der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> Klasse ab.  
  
    > [!NOTE]
    > Der Kern-Editor wendet automatisch Standardtext Marker auf jedes Dokument an, das bearbeitet wird, und es sollte nicht notwendig sein, Standardtext Marker explizit anzuwenden.  
  
2. Rufen Sie eine Markertyp-ID des Markers ab, an dem Sie interessiert sind, indem Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> Methode mit der `GUID` des Text Markers aufrufen, mit dem Sie arbeiten möchten.  
  
    > [!NOTE]
    > Verwenden Sie nicht die `GUID` des VSPackages oder des Dienstanbieter, der den Textmarker bereitstellt.  
  
3. Verwenden Sie die Markertyp-ID, die Sie erhalten haben, indem Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> Methode als Parameter aufrufen, um die-Methode aufzurufen, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> oder die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> Methode, um einen Textmarker auf einen angegebenen Text  
  
#### <a name="to-add-features-to-text-markers"></a>So fügen Sie Funktionen zu Text Markern hinzu  
  
1. Es kann wünschenswert sein, einem Textmarker zusätzliche Funktionen hinzuzufügen, z. b. Quick Infos, ein spezielles Kontextmenü oder einen Handler für besondere Umstände. Gehen Sie folgendermaßen vor:  
  
2. Erstellen Sie ein Objekt, das die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle implementiert.  
  
3. Wenn zusätzliche Funktionalität gewünscht ist, implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> -Schnittstelle und die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> Schnittstelle für das gleiche Objekt, das die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle implementiert.  
  
4. Übergeben Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle, die Sie erstellen, an den-Befehl der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> Methode oder die-Methode, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> verwendet wird, um den Textmarker auf einen bestimmten Textbereich anzuwenden.  
  
5. Beim Hinzufügen von Kontextmenü Unterstützung zu einem Text Markierungs Bereich muss das Menü erstellt werden.  
  
     Weitere Informationen zum Erstellen eines Kontextmenüs finden Sie unter [Kontextmenüs](../extensibility/context-menus.md).  
  
6. Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Umgebung Ruft die Methoden der angegebenen Schnittstellen auf, z. b. die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> Methode oder die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> Methode nach Bedarf.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Text Markern mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Vorgehensweise: Hinzufügen von Standard Text Markern](../extensibility/how-to-add-standard-text-markers.md)   
 [Gewusst wie: Erstellen von benutzerdefinierten Text Markern](../extensibility/how-to-create-custom-text-markers.md)   
 [Vorgehensweise: Implementieren von Fehlermarkierungen](../extensibility/how-to-implement-error-markers.md)
