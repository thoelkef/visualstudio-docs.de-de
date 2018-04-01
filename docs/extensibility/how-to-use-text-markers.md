---
title: 'Vorgehensweise: Verwenden von Text Marker | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f5c5c2686bee9850da72c00e044952b15bed9c58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-text-markers"></a>Vorgehensweise: Verwenden von Text-Marker
Text-Marker können angewendet werden, um Sie bearbeiten ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Objekt.  
  
## <a name="procedures"></a>Verfahren  
  
#### <a name="to-apply-text-markers"></a>Text-Marker anwenden  
  
1.  Rufen Sie eine Instanz von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> Klasse.  
  
    > [!NOTE]
    >  Der Editor Core gilt automatisch Standardtext Marker für jedes Dokument, das bearbeitet wird, und es sollte nicht erforderlich sein, explizites übernehmen von standard-Text-Marker.  
  
2.  Erhalten Sie eine Marker-Typ-ID des Markers, durch Aufrufen interessiert sind der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> Methode mit der `GUID` des Markers Text Sie arbeiten möchten.  
  
    > [!NOTE]
    >  Verwenden Sie nicht die `GUID` des VSPackage oder der Dienst, den Text Marker bereitstellt.  
  
3.  Verwenden die Marker-Typ-ID abgerufen wird, durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> Methode als Parameter aufrufen, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> Methode oder die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> Methode, um einen Text-Marker in einer bestimmten Region des Texts anzuwenden.  
  
#### <a name="to-add-features-to-text-markers"></a>Text-Marker Funktionen hinzufügen  
  
1.  Es möglicherweise wünschenswert, ein Marker Text z. B. QuickInfos, eine spezielle Kontextmenü oder der Handler bei besonderen Umständen zusätzliche Funktionen hinzugefügt. Dazu:  
  
2.  Erstellen Sie ein Objekt, durch die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle.  
  
3.  Implementieren Sie ggf. zusätzliche Funktionen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>, und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> Schnittstellen für das gleiche Objekt, das implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle.  
  
4.  Übergeben der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle, die Sie, die dem Aufruf Erstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> Methode oder die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> Methode verwendet, um den Marker für Text in einer bestimmten Region des Texts anzuwenden.  
  
5.  Beim Hinzufügen von kontextunterstützung-Menü zu einer Markierung Textbereich ist es erforderlich, klicken Sie im Menü erstellen.  
  
     Weitere Informationen zum Erstellen einer Kontext Menü finden Sie unter [Kontextmenüs](../extensibility/context-menus.md).  
  
6.  Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung Aufrufe der Methoden der bereitgestellten Schnittstellen, z. B. die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> -Methode oder die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> Methode nach Bedarf.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Text Marker mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Vorgehensweise: Hinzufügen von Standard-Text-Marker](../extensibility/how-to-add-standard-text-markers.md)   
 [Vorgehensweise: Erstellen von benutzerdefinierten Text-Marker](../extensibility/how-to-create-custom-text-markers.md)   
 [Vorgehensweise: Implementieren von Fehler Marker](../extensibility/how-to-implement-error-markers.md)