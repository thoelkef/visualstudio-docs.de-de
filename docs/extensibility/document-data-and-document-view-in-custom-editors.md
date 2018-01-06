---
title: Dokumentdaten und Document in benutzerdefinierte Editoren anzeigen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7c7e24ed2db4538ab0fd38dbb85930452611f0ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dokumentdaten und Dokumentenansicht in benutzerdefinierten Editoren
Ein benutzerdefinierter Editor besteht aus zwei Teilen: ein dokumentdatenobjekt und ein Document-Objekt. Wie die Namen erkennen lassen, das dokumentdatenobjekt stellt die Textdaten, die angezeigt werden, und die dokumentansichtsobjekts (oder "View") stellt ein oder mehrere Fenster, in dem das dokumentdatenobjekt angezeigt.  
  
## <a name="document-data-object"></a>Dokumentdatenobjekt  
 Ein dokumentdatenobjekt ist eine Darstellung der Daten des Texts in den Textpuffer. Es ist ein COM-Objekt, das speichert Dokumenttext und andere Informationen, Dokument Persistenz behandelt und mehrere Ansichten für seine Daten ermöglicht. Weitere Informationen finden Sie unter  
  
 <xref:EnvDTE80.Window2.DocumentData%2A>und [Dokumentfenster](../extensibility/internals/document-windows.md).  
  
 Benutzerdefinierte Editoren und Designern können wahlweise verwenden die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt oder ihre eigenen benutzerdefinierten Puffer. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>folgt das Einbetten von vereinfachte Modell für eine standard-Editor unterstützt mehrere Ansichten und bietet Ereignisschnittstellen, die verwendet werden, um mehrere Ansichten zu verwalten.  
  
## <a name="document-view-object"></a>Dokumentansichtsobjekts  
 Ein Fenster, in dem Code und anderer Text angezeigt wird bezeichnet als ein Dokument oder der Ansicht. Wenn Sie einen Editor erstellen, können Sie auswählen, einer einzelnen Ansicht, in der Text in einem einzelnen Fenster angezeigt wird oder eine mehrere Ansichten, in dem Text in mehr als ein Fenster angezeigt wird. Ihre Wahl hängt von der Anwendung ab. Wenn die gewünschte Seite-an-Seite zu bearbeiten, würden Sie z. B. mehrere Ansichten auswählen. Jede Ansicht ist ein Eintrag in der integrierten Entwicklungsumgebung des (IDE) ausgeführt wird (RDT) der Document-Tabelle zugeordnet. Fenster gehören zu einem Projekt oder einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt.  
  
 Wenn Ihrem-Editor mehrere Ansichten für ein dokumentdatenobjekt unterstützt, müssen die Dokumentdaten und Ansicht-Dokumentobjekte getrennt sein. Andernfalls können sie gruppiert werden. Weitere Informationen finden Sie unter [unterstützen mehrere Dokumentansichten](../extensibility/supporting-multiple-document-views.md).  
  
 Die IDE benachrichtigt Ansichten über Ereignisse (z. B., wenn eine Projektmappe mit einem Dokument geschlossen ist) durch den Abgleich eine Element-ID (ItemID) für jeden Eintrag in der Dokumenttabelle der ausgeführten. Weitere Informationen dazu finden Sie unter [Document-Tabelle ausgeführt](../extensibility/internals/running-document-table.md).  
  
 Es gibt zwei Optionen zum Erstellen einer Ansicht für einen benutzerdefinierten Editor. Eine ist des Modells für die direkte Aktivierung, wo die Ansicht in einem Fenster mit einem ActiveX-Steuerelement oder ein dokumentdatenobjekt gehostet wird. Das zweite ist die vereinfachte Einbetten von Modell, in dem die Sicht von gehostet wird [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> wird implementiert, um die Befehle "Fenster" zu behandeln. Informationen über das Modell für die direkte Aktivierung finden Sie unter [direkte Aktivierung](../extensibility/in-place-activation.md). Informationen über das vereinfachte Einbetten von Modell finden Sie unter [vereinfachte einbetten](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)   
 [Einbetten von vereinfacht](../extensibility/simplified-embedding.md)   
 [Vorgehensweise: Anfügen von Ansichten, um Daten zu dokumentieren.](../extensibility/how-to-attach-views-to-document-data.md)   
 [Inhaber von Dokumentverwaltung-Sperre](../extensibility/document-lock-holder-management.md)   
 [Ansichten für einzelne und Registerkarte "Multi"](../extensibility/single-and-multi-tab-views.md)   
 [Speichern eines Dokuments Standard](../extensibility/internals/saving-a-standard-document.md)   
 [Persistenz und die Ausführung Document-Tabelle](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Bestimmen daraufhin-Editor eine Datei in einem Projekt](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Editor-Factorys](../extensibility/editor-factories.md)