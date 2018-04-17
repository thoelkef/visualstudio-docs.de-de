---
title: 'Vorgehensweise: Hinzufügen von Standard-Text-Marker | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2fc5bf34c9b4200d8d7fef2d9f4a878ca604f886
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-standard-text-markers"></a>Vorgehensweise: Hinzufügen von Standard-Text-Marker
Gehen Sie zum Erstellen der Standardeinstellung Text Markertypen bereitgestellt, mit der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editor.  
  
### <a name="to-create-a-text-marker"></a>So erstellen einen Text-marker  
  
1.  Abhängig davon, ob Sie eine oder zwei - dimensionalen Koordinatensystem, rufen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> Methode oder die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> Methode, um einen neuen Text Marker zu erstellen.  
  
     In diesem Methodenaufruf, geben Sie einen Markertyp einen Textbereich erstellen Sie die Markierung über, und ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle. Diese Methode gibt dann einen Zeiger auf den neu erstellten Text-Marker. Markertypen stammen aus den <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> Enumeration. Geben Sie eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle, wenn Sie über methodenmarkerereignisse informiert werden möchten.  
  
    > [!NOTE]
    >  Erstellen Sie auf dem Hauptbenutzeroberflächen-Thread nur Text Marker. Die Core-Editor beruht auf dem Inhalt des Textpuffers Text Marker erstellen, und der Textpuffer ist nicht threadsicher.  
  
## <a name="adding-a-custom-command"></a>Hinzufügen eines benutzerdefinierten Befehls  
 Implementieren der `IVsTextMarkerClient` Schnittstelle und einen Zeiger darauf bereitstellen, von einem Marker verbessert die Marker Verhalten auf unterschiedliche Weise. Erstens können Sie diese Tipps für die Marker generieren und Ausführen von Befehlen. Dadurch können Sie ereignisbenachrichtigungen für die einzelnen Marker erhalten und erstellen Sie ein benutzerdefiniertes Kontextmenü über die Markierung. Verwenden Sie das folgende Verfahren, Marker-Kontextmenü einen benutzerdefinierten Befehl hinzu.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Im Kontextmenü den Befehl einen benutzerdefinierten Befehl hinzu  
  
1.  Bevor Sie das Kontextmenü angezeigt wird, ruft die Umgebung die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> -Methode und übergeben Sie einen Zeiger auf den Text Marker betroffen und die Anzahl der im Kontextmenü den Befehlselement.  
  
     Die Breakpoint-spezifischen Befehle im Kontextmenü zählen beispielsweise **Haltepunkt entfernen** über **Neuer Haltepunkt**, wie im folgenden Screenshot angezeigt.  
  
     ![Marker-Kontextmenü](../extensibility/media/vsmarkercontextmenu.gif "VsMarkercontextmenu")  
  
2.  Geben Sie etwas Text identifiziert den Namen des benutzerdefinierten Befehls zurück. Beispielsweise **Haltepunkt entfernen** möglicherweise ein benutzerdefinierter Befehl aus, wenn die Umgebung nicht bereits sie bereitgestellt wurden. Sie auch übergeben zurück, ob der Befehl unterstützt, verfügbar und aktiviert ist, und/oder eine-off ein-/ausschalten. Die Umgebung verwendet diese Informationen, um den benutzerdefinierten Befehl im Kontextmenü in korrekter Weise anzuzeigen.  
  
3.  Beim Ausführen des Befehls, der die Umgebung Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> Methode, die Übergabe eines Zeigers auf den Marker für Text und die Anzahl des Befehls aus dem Kontextmenü ausgewählt.  
  
     Verwenden Sie diese Informationen aus diesen Aufruf bestimmt die Aktionen des Markers aus Text, einen Befehl ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Text Marker mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Vorgehensweise: Implementieren von Fehler Marker](../extensibility/how-to-implement-error-markers.md)   
 [Vorgehensweise: Erstellen von benutzerdefinierten Text-Marker](../extensibility/how-to-create-custom-text-markers.md)   
 [Vorgehensweise: Verwenden von Text-Marker](../extensibility/how-to-use-text-markers.md)