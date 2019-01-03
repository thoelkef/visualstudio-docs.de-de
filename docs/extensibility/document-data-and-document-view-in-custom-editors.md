---
title: Dokumentdaten und Dokument anzeigen, in benutzerdefinierten Editoren | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2af41600ed809259cd7512a7fc0a146047a37ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53818874"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren
Ein benutzerdefinierter Editor besteht aus zwei Teilen: ein dokumentdatenobjekt und eine dokumentenansichtsobjekt. Wie die Namen schon sagen, stellt das dokumentendatenobjekt die Textdaten, die angezeigt werden. Auf ähnliche Weise stellt das dokumentenansichtsobjekt (oder "View") ein oder mehrere Fenster, in dem das dokumentendatenobjekt angezeigt.  
  
## <a name="document-data-object"></a>Dokumentendatenobjekt  
 Ein dokumentdatenobjekt ist eine Darstellung des Texts im Textpuffer. Es ist ein COM-Objekt, in dem Dokumenttext und andere Informationen gespeichert. Das dokumentendatenobjekt außerdem Dokument Persistenz behandelt und kann von mehreren Ansichten der Daten. Weitere Informationen finden Sie unter  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> und [dokumentieren Windows](../extensibility/internals/document-windows.md).  
  
 Benutzerdefinierter Editoren und Designer können gewünschtenfalls verwenden die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt oder ihre eigenen benutzerdefinierten Puffer. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> folgt den vereinfachte Modell für worteinbettungen für einen standard-Editor, mehrere Ansichten unterstützt und bietet Event-Schnittstellen, die zum Verwalten von mehreren Ansichten verwendet werden.  
  
## <a name="document-view-object"></a>Dokumentenansichtsobjekt  
 Ein Fenster, Code und anderer Text angezeigt, wird als ein Dokument bezeichnet Ansicht "oder". Wenn Sie einen Editor erstellen, können Sie entweder eine einzelne Ansicht auswählen, in der Text in einem einzelnen Fenster angezeigt wird. Oder Sie können eine Ansicht für mehrere, in der Text in mehr als einem Fenster angezeigt wird. Die Auswahl hängt von Ihrer Anwendung ab. Wenn Sie die Seite-an-Seite bearbeiten benötigen, würden Sie beispielsweise mehrere Ansichten auswählen. Jede Ansicht, die einen Eintrag in der integrierten Entwicklungsumgebung des (IDE) mit der Document-Tabelle (RDT) zugeordnet ist. In den anzeigefenstern gehören zu einem Projekt oder eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt.  
  
 Wenn Ihr Editor mehrere Ansichten für ein dokumentdatenobjekt unterstützt, müssen Ihre Dokumentdaten und dokumentenansichtsobjekten getrennt werden. Andernfalls können sie gruppiert werden. Weitere Informationen finden Sie unter [unterstützen mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md).  
  
 Die IDE benachrichtigt Ansichten über Ereignisse (z. B., wenn eine Projektmappe mit einem Dokument geschlossen wird) durch entsprechende eine Element-ID (Element-ID) für jeden Eintrag in der aktiven Dokumenttabelle. Weitere Informationen hierzu finden Sie unter [Document-Tabelle mit](../extensibility/internals/running-document-table.md).  
  
 Es gibt zwei Optionen zum Erstellen einer Ansicht für einen benutzerdefinierten Editor. Eine ist die direkte Aktivierungsmodell, in dem die Ansicht in einem Fenster mit einem ActiveX-Steuerelement oder ein dokumentdatenobjekt gehostet wird. Die zweite ist die vereinfachte einbetten Modell, in dem die Ansicht von gehostet wird [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> wird implementiert, um die Befehle im Fenster zu behandeln. Weitere Informationen über das Modell für die direkte Aktivierung finden Sie unter [direkte Aktivierung](../extensibility/in-place-activation.md). Weitere Informationen zu den vereinfachten Modell für worteinbettungen, finden Sie unter [zum Vereinfachen des Einbettens](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützen Sie mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)   
 [Zum Vereinfachen des Einbettens](../extensibility/simplified-embedding.md)   
 [Vorgehensweise: Anfügen von Ansichten zu Dokumentdaten](../extensibility/how-to-attach-views-to-document-data.md)   
 [Verwaltung von Dokumentsperren](../extensibility/document-lock-holder-management.md)   
 [Einer und mehreren Registerkarten-Ansichten](../extensibility/single-and-multi-tab-views.md)   
 [Speichern eines Standarddokuments](../extensibility/internals/saving-a-standard-document.md)   
 [Persistenz und der ausgeführten Dokumententabelle](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Bestimmen Sie, welcher Editor eine Datei in einem Projekt öffnet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Editorfactorys](../extensibility/editor-factories.md)