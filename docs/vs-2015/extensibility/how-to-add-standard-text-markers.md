---
title: 'Vorgehensweise: Hinzufügen von Standard-Text-Marker | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3bd7b31a609117a59a5110cdb4460e5c36395ede
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089210"
---
# <a name="how-to-add-standard-text-markers"></a>Vorgehensweise: Standard-Text-Marker hinzufügen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden Sie das folgende Verfahren zum Erstellen der standardmäßigen Text Markertypen im Lieferumfang der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Kern-Editor.  
  
### <a name="to-create-a-text-marker"></a>Erstellen ein textmarkers  
  
1. Je nachdem, ob Sie eine oder zwei - dimensionalen Koordinatensystem, Aufruf verwenden, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> Methode oder der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> Methode, um eine neue textmarkierung zu erstellen.  
  
     Geben Sie in diesem Methodenaufruf einen Markertyp, einen Textbereich, den Marker aus, zu erstellen und ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle. Diese Methode gibt dann einen Zeiger auf die neu erstellte textmarkierung. Markertypen stammen aus der <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> Enumeration. Geben Sie eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle, wenn Sie über Markerereignissen informiert werden möchten.  
  
    > [!NOTE]
    >  Erstellen Sie auf dem Hauptbenutzeroberflächen-Thread nur Textmarkierungen. Der Kern-Editor basiert auf dem Inhalt des Textpuffers Textmarkierungen zu erstellen und der Textpuffer ist nicht threadsicher.  
  
## <a name="adding-a-custom-command"></a>Hinzufügen eines benutzerdefinierten Befehls  
 Implementieren der `IVsTextMarkerClient` Schnittstelle und Angeben eines Zeigers, von einem Marker verbessert die markerverhalten auf verschiedene Weise. Erstens können Sie die Tipps für Ihre Marke zu generieren und Ausführen von Befehlen. Dadurch können Sie ereignisbenachrichtigungen für die einzelnen Marker erhalten und erstellen ein benutzerdefiniertes Kontextmenü über die Markierung. Verwenden Sie das folgende Verfahren, das Marker-Kontextmenü einen benutzerdefinierten Befehl hinzu.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Hinzufügen ein benutzerdefiniertes Befehls zum Kontextmenü  
  
1. Bevor das Kontextmenü angezeigt wird, wird die Umgebung Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> -Methode und übergeben Sie einen Zeiger auf die textmarkierung betroffen und die Anzahl der Befehl im Kontextmenü des Elements.  
  
     Die Haltepunkt-spezifische Befehle im Kontextmenü kann beispielsweise **Haltepunkt entfernen** über **Neuer Haltepunkt**, wie im folgenden Screenshot angezeigt.  
  
     ![Marker-Kontextmenü](../extensibility/media/vsmarkercontextmenu.gif "VsMarkercontextmenu")  
  
2. Geben Sie Text identifiziert den Namen des benutzerdefinierten Befehls zurück. Z. B. **Haltepunkt entfernen** möglicherweise ein benutzerdefinierter Befehl aus, wenn die Umgebung nicht bereits er angegeben wurde. Sie auch übergeben zurück, ob der Befehl unterstützt, verfügbar und aktiviert ist, bzw. eine Umschaltfläche aktivieren / deaktivieren. Die Umgebung verwendet diese Informationen, um den benutzerdefinierten Befehl im Kontextmenü in korrekter Weise anzuzeigen.  
  
3. Zum Ausführen des Befehls, der die Umgebung Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> Methode und übergeben Sie einen Zeiger auf die textmarkierung und die Anzahl des Befehls aus dem Kontextmenü ausgewählt.  
  
     Verwenden Sie diese Informationen aus diesen Aufruf zum Ausführen der Aktionen der textmarkierung des benutzerdefinierten Befehls bestimmt.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Textmarkierungen mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Vorgehensweise: Implementieren von Fehlermarker](../extensibility/how-to-implement-error-markers.md)   
 [Vorgehensweise: Erstellen von benutzerdefinierten Textmarkierungen](../extensibility/how-to-create-custom-text-markers.md)   
 [Vorgehensweise: Verwenden von Textmarkierungen](../extensibility/how-to-use-text-markers.md)
