---
title: "Gewusst wie: Verwenden von Text-Marker | Microsoft Docs"
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
  - "legacy - Text-Marken mit Editoren [Visual Studio SDK]"
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Verwenden von Text-Marker
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Textmarkierungen können angewendet werden, um ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>\-Objekt zu bearbeiten.  
  
## Arbeitsschritte  
  
#### So wenden Textmarkierungen  
  
1.  Rufen Sie eine Instanz der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>\-Klasse.  
  
    > [!NOTE]
    >  Der Kern des Editors wird automatisch Standardwert textmarkierungen jedem Dokument, dass er bearbeitet, und es sollte nicht notwendig sein Standardwert textmarkierungen explizit zu übernehmen.  
  
2.  Ruft eine Markierung des ID des Markers, den Sie interessiert sind, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>\-Methode mit `GUID` der Textmarkierung aufrufen Sie bearbeiten möchten.  
  
    > [!NOTE]
    >  Verwenden Sie keine `GUID` VSPackages oder des Diensts, der die Textmarkierung bereitstellt.  
  
3.  Verwenden Sie den Marker, die ID, den Typ anhand der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>\-Methode als Parameter aufgerufen hat, um die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>\-Methode oder die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>\-Methode aufrufen, um eine Textmarkierung zu einem angegebenen Textbereich anzuwenden.  
  
#### So fügen Sie Funktionen hinzu Textmarkierungen  
  
1.  Es ist möglicherweise wünschenswert, zusätzliche Features einer Textmarkierung, z. B. QuickInfos, einem besonderen Kontextmenü oder Handler für besondere Umstände hinzuzufügen.  So erstellen Sie so vorgehen:  
  
2.  Erstellen Sie ein Objekt, das die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>\-Schnittstelle implementiert.  
  
3.  Wenn zusätzliche Funktionen erwünscht ist, implementieren Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>\-Schnittstellen auf demselben Objekt, das die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>\-Schnittstelle implementiert.  
  
4.  Führen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>\-Schnittstelle, die Sie erstellen, um Aufruf der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>\-Methode oder die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>\-Methode, die verwendet werden, um die Textmarkierung zu einem angegebenen Textbereich anzuwenden.  
  
5.  Wenn die Unterstützung von einem Bereich Textmarkierungs Kontextmenü hinzugefügt wird, ist es notwendig, das Menü zu erstellen.  
  
     Weitere Informationen zum Erstellen eines Kontextmenüs finden Sie unter [Kontextmenüs](../extensibility/context-menus.md)erstellt.  
  
6.  Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung ruft die Methoden der angegebenen Schnittstellen, wie der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A>\-Methode oder die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>\-Methode bei Bedarf an.  
  
## Siehe auch  
 [Verwenden von Text Marker mit der Legacy\-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Gewusst wie: Hinzufügen von Standard\-Text\-Marker](../extensibility/how-to-add-standard-text-markers.md)   
 [Gewusst wie: Erstellen von benutzerdefinierten Text Marken](../extensibility/how-to-create-custom-text-markers.md)   
 [Gewusst wie: Implementieren von Fehler Marker](../extensibility/how-to-implement-error-markers.md)