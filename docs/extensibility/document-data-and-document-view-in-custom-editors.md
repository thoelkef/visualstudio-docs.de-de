---
title: "Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren | Microsoft Docs"
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
  - "Editoren [Visual Studio SDK] benutzerdefinierte - Dokumentdaten und Dokumentansicht"
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein benutzerdefinierter Editor besteht aus zwei Teilen: einem Datenobjekt Dokument und ein Document\-Objekt. Wie die Namen andeuten, das Dokument\-Datenobjekt darstellt, die Text\-Daten angezeigt werden und das Document\-Objekt \(oder "View"\) stellt ein oder mehrere Fenster zum Anzeigen des Datenobjekts Dokument.  
  
## Dokument\-Datenobjekt  
 Ein Datenobjekt Dokument ist eine Darstellung des Texts im Textpuffer. Es ist ein COM\-Objekt speichert Dokumenttext und andere Informationen, die Persistenz Dokument behandelt und kann mehrere Ansichten der Daten. Weitere Informationen finden Sie unter  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> und [Dokumentfenster](../extensibility/internals/document-windows.md).  
  
 Benutzerdefinierte Editoren und Designern können wahlweise verwenden die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt oder ihre eigenen benutzerdefinierten Puffer.<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> folgt das Einbetten von vereinfachte Modell für einen standard\-Editor unterstützt mehrere Ansichten, und enthält Ereignisschnittstellen, die zum Verwalten von mehreren Ansichten verwendet werden.  
  
## Document\-Objekt  
 Ein Fenster mit Code und anderen Text fungiert als ein Dokument oder der Ansicht. Wenn Sie einen Editor erstellen, können Sie einer einzelnen Ansicht, in der Text in einem einzigen Fenster angezeigt wird oder eine Ansicht für mehrere, in der Text in mehr als ein Fenster angezeigt wird. Ihre Wahl hängt von Ihrer Anwendung ab. Wenn Side\-by\-Side bearbeitet werden sollen, würden Sie z. B. mehrere Ansicht auswählen. Jede Ansicht ist ein Eintrag in der IDE \(IDE\) ausgeführt Dokumenttabelle \(RDT\) zugeordnet. Fenster gehören zu einem Projekt oder einem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt.  
  
 Wenn Editor mehrere Ansichten eines Dokuments\-Objekts unterstützt, müssen die Dokumentdaten und Document\-Objekte getrennt werden. Andernfalls können sie gruppiert werden. Weitere Informationen finden Sie unter [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md).  
  
 Die IDE benachrichtigt Ansichten über Ereignisse \(z. B., wenn eine Projektmappe mit einem Dokument geschlossen wird\) durch entsprechende eine Element\-ID \(ItemID\) für jeden Eintrag in der Dokumenttabelle der aktiven. Weitere Informationen hierzu finden Sie unter [Dokumenttabelle der ausgeführten](../extensibility/internals/running-document-table.md).  
  
 Es gibt zwei Optionen zum Erstellen einer Ansicht für einen benutzerdefinierten Editor. Eine ist das direkte Aktivierungsmodell, die Ansicht in einem Fenster mit ActiveX\-Steuerelement oder ein Dokumentobjekt gehostet wird. Das zweite ist das vereinfachte einbetten Modell, in dem die Ansicht von gehostet wird [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> wird implementiert, um das Fenster Befehle zu verarbeiten. Informationen über das Modell für die direkte Aktivierung finden Sie unter [Direkte Aktivierung](../misc/in-place-activation.md). Informationen zum Einbetten von vereinfachte Modell finden Sie unter [Vereinfachen des Einbettens](../extensibility/simplified-embedding.md).  
  
## Siehe auch  
 [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)   
 [Vereinfachen des Einbettens](../extensibility/simplified-embedding.md)   
 [Gewusst wie: Anfügen von Ansichten, um Daten](../extensibility/how-to-attach-views-to-document-data.md)   
 [Verwaltung der Inhaber Dokument](../extensibility/document-lock-holder-management.md)   
 [Einzelne und mehrere Registerkarte Ansichten](../extensibility/single-and-multi-tab-views.md)   
 [Ein standardisiertes Dokument speichern](../extensibility/internals/saving-a-standard-document.md)   
 [Persistenz und der Document\-Tabelle ausgeführt wird](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Bestimmen daraufhin\-Editor eine Datei in einem Projekt](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Editor\-Factorys](../extensibility/editor-factories.md)