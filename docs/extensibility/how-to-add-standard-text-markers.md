---
title: 'Vorgehensweise: Hinzufügen von Standard-Text-Marker | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80c32827a991a87b582f31ceefd2bfd6dbcc7a8f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922349"
---
# <a name="how-to-add-standard-text-markers"></a>Vorgehensweise: Standard-Text-Marker hinzufügen
Verwenden Sie das folgende Verfahren zum Erstellen der standardmäßigen Text Markertypen im Lieferumfang der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Kern-Editor.  
  
## <a name="to-create-a-text-marker"></a>Erstellen ein textmarkers  
  
1.  Je nachdem, ob Sie einem ein- oder zweidimensionalen Koordinatensystem verwenden, rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> Methode oder der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> Methode, um eine neue textmarkierung zu erstellen.  
  
     Geben Sie in diesem Methodenaufruf einen Markertyp, einen Textbereich, den Marker aus, zu erstellen und ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle. Diese Methode gibt dann einen Zeiger auf die neu erstellte textmarkierung. Markertypen stammen aus der <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> Enumeration. Geben Sie eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle, wenn Sie über Markerereignissen informiert werden möchten.  
  
    > [!NOTE]
    >  Erstellen Sie auf dem Hauptbenutzeroberflächen-Thread nur Textmarkierungen. Der Kern-Editor basiert auf dem Inhalt des Textpuffers Textmarkierungen zu erstellen und der Textpuffer ist nicht threadsicher.  
  
## <a name="add-a-custom-command"></a>Fügen Sie einen benutzerdefinierten Befehl hinzu  
 Implementieren der `IVsTextMarkerClient` Schnittstelle und Angeben eines Zeigers, von einem Marker verbessert die markerverhalten auf verschiedene Weise. Erstens können Sie die Tipps für Ihre Marke zu generieren und Ausführen von Befehlen. Dadurch können Sie ereignisbenachrichtigungen für die einzelnen Marker erhalten und erstellen ein benutzerdefiniertes Kontextmenü über die Markierung. Verwenden Sie das folgende Verfahren, das Marker-Kontextmenü einen benutzerdefinierten Befehl hinzu.  
  
### <a name="to-add-a-custom-command-to-the-context-menu"></a>Hinzufügen ein benutzerdefiniertes Befehls zum Kontextmenü  
  
1.  Bevor das Kontextmenü angezeigt wird, wird die Umgebung Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> -Methode und übergeben Sie einen Zeiger auf die textmarkierung betroffen und die Anzahl der Befehl im Kontextmenü des Elements.  
  
     Die Haltepunkt-spezifische Befehle im Kontextmenü kann beispielsweise **Haltepunkt entfernen** über **Neuer Haltepunkt**, wie im folgenden Screenshot angezeigt.  
  
     ![Marker-Kontextmenü](../extensibility/media/vsmarkercontextmenu.gif "VsMarkercontextmenu")  
  
2.  Geben Sie Text identifiziert den Namen des benutzerdefinierten Befehls zurück. Z. B. **Haltepunkt entfernen** möglicherweise ein benutzerdefinierter Befehl aus, wenn die Umgebung nicht bereits er angegeben wurde. Sie auch übergeben zurück, ob der Befehl unterstützt, verfügbar und aktiviert ist, bzw. eine Umschaltfläche aktivieren / deaktivieren. Die Umgebung verwendet diese Informationen, um den benutzerdefinierten Befehl im Kontextmenü in korrekter Weise anzuzeigen.  
  
3.  Zum Ausführen des Befehls, der die Umgebung Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> Methode und übergeben Sie einen Zeiger auf die textmarkierung und die Anzahl des Befehls aus dem Kontextmenü ausgewählt.  
  
     Verwenden Sie diese Informationen aus diesen Aufruf zum Ausführen der Aktionen der textmarkierung des benutzerdefinierten Befehls bestimmt.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Textmarkierungen mit der legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Vorgehensweise: Implementieren von fehlermarker](../extensibility/how-to-implement-error-markers.md)   
 [Vorgehensweise: Erstellen von benutzerdefinierten Textmarkierungen](../extensibility/how-to-create-custom-text-markers.md)   
 [Vorgehensweise: Verwenden von Textmarkierungen](../extensibility/how-to-use-text-markers.md)