---
title: "Gewusst wie: Hinzuf&#252;gen von Standard-Text-Marker | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - standard-Text-Marker"
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Hinzuf&#252;gen von Standard-Text-Marker
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Führen Sie die folgenden Schritte aus, um einen der Standardtext marker Typen zu erstellen, die mit dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kern des Editors bereitgestellt werden.  
  
### So erstellen Sie eine Textmarkierung  
  
1.  Je nachdem, ob Sie das oder ein zweidimensionales Koordinatensystem verwenden, rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>\-Methode oder die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>\-Methode auf, um eine neue Textmarkierung zu erstellen.  
  
     In diesem Methodenaufruf geben Sie einen Marker Typ der einen Textbereich auf, um die Markierung durch erstellen und eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>\-Schnittstelle.  Diese Methode gibt einen Zeiger auf die neu erstellten Textmarkierung zurück.  Marker Typen werden von der <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE>\-Enumeration bestimmt.  Geben Sie eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>\-Schnittstelle an, wenn Sie zur Markierung von Ereignissen informiert werden möchten.  
  
    > [!NOTE]
    >  Bereitstellen von Textmarkierungen nur auf dem primären UI\-Thread.  Der Kern des Editors basiert auf dem Inhalt des Textpuffers, um Textmarkierungen zu erstellen und den Textpuffer ist nicht threadsicher.  
  
## Hinzufügen eines benutzerdefinierten Befehl  
 Das Implementieren der Schnittstelle `IVsTextMarkerClient` sowie zum Bereitstellen eines Zeigers auf sie von einem Marker erhöht sich das Verhalten von Markern auf verschiedene Weise.  Erstens können Sie Tipps für den Marker bereitzustellen und Befehle auszuführen.  Dies können Sie auch Ereignisbenachrichtigungen für einzelne Marker zu empfangen und ein benutzerdefiniertes Kontextmenü über den Marker zu erstellen.  Führen Sie die folgenden Schritte aus, um einen benutzerdefinierten Befehl im Kontextmenü Markierung hinzuzufügen.  
  
#### So erstellen Sie einen benutzerdefinierten Befehl im Kontextmenü auf Hinzufügen  
  
1.  Bevor das Kontextmenü angezeigt wird, ruft die Umgebung die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A>\-Methode auf und übergibt ein Zeiger auf die betroffenen Textmarkierung und die Nummer des Befehls Elements im Kontextmenü.  
  
     Zum Beispiel sind die spezifischen Befehle im Kontextmenü auf Haltepunkt **Haltepunkt entfernen** von **Neuer Haltepunkt**, wie in der folgenden Bildschirmabbildung angezeigt.  
  
     ![Marker&#45;Kontextmenü](../extensibility/media/vsmarkercontextmenu.png "vsMarkercontextmenu")  
  
2.  Führen Sie einen kurzen Text, der den Namen des benutzerdefinierten Befehl identifiziert.  Zum Beispiel könnte **Haltepunkt entfernen** ein benutzerdefinierter Befehl auf, wenn die Umgebung nicht bereits ihn geliefert hat.  Führen Sie auch den Hintergrund unterstützt wird, ob der Befehl zur Verfügung und ermöglicht und\/oder eine Umschaltfläche Ein\-Aus.  Die Umgebung verwendet diese Informationen, um den benutzerdefinierten Befehl im Kontextmenü auf die richtige Weise anzuzeigen.  
  
3.  Um den Befehl ruft die Umgebung, die Sie ausführen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>\-Methode einen Zeiger auf die Textmarkierung und die Nummer des Befehls im Kontextmenü ausgewählt sind.  
  
     Verwenden Sie diese Informationen von diesem Aufruf, der ausgeführt werden soll, welche Aktionen der Textmarkierung der benutzerdefinierten Befehl vorschreibt.  
  
## Siehe auch  
 [Verwenden von Text Marker mit der Legacy\-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Gewusst wie: Implementieren von Fehler Marker](../extensibility/how-to-implement-error-markers.md)   
 [Gewusst wie: Erstellen von benutzerdefinierten Text Marken](../extensibility/how-to-create-custom-text-markers.md)   
 [Gewusst wie: Verwenden von Text\-Marker](../extensibility/how-to-use-text-markers.md)