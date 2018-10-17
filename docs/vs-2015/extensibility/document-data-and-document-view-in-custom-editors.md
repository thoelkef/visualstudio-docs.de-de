---
title: Dokumentdaten und Dokument anzeigen, in benutzerdefinierten Editoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 258718a99e774b7098ff29dd66efc51a57062475
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206907"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein benutzerdefinierter Editor besteht aus zwei Teilen: ein dokumentdatenobjekt und eine dokumentenansichtsobjekt. Wie die Namen schon sagen, das dokumentendatenobjekt darstellt, die Textdaten, die angezeigt werden, und die dokumentenansichtsobjekt (oder "View") stellt ein oder mehrere Fenster, in dem das dokumentendatenobjekt angezeigt.  
  
## <a name="document-data-object"></a>Dokumentendatenobjekt  
 Ein dokumentdatenobjekt ist eine Darstellung des Texts im Textpuffer. Es ist ein COM-Objekt, das speichert Dokumenttext und andere Informationen, behandelt der Dokument-Persistenz und ermöglicht mehrere Ansichten der Daten. Weitere Informationen finden Sie unter  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> und [dokumentieren Windows](../extensibility/internals/document-windows.md).  
  
 Benutzerdefinierter Editoren und Designer können gewünschtenfalls verwenden die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt oder ihre eigenen benutzerdefinierten Puffer. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> folgt den vereinfachte Modell für worteinbettungen für einen standard-Editor, mehrere Ansichten unterstützt und bietet Event-Schnittstellen, die zum Verwalten von mehreren Ansichten verwendet werden.  
  
## <a name="document-view-object"></a>Dokumentenansichtsobjekt  
 Ein Fenster, Code und anderer Text angezeigt, wird als ein Dokument bezeichnet Ansicht "oder". Wenn Sie einen Editor erstellen, können Sie entweder auf einer zentralen Ansicht, in der Text in einem einzelnen Fenster angezeigt wird oder auf eine Ansicht für mehrere, in der Text in mehr als einem Fenster angezeigt wird. Die Auswahl hängt von Ihrer Anwendung ab. Wenn Sie die Seite-an-Seite bearbeiten benötigen, würden Sie beispielsweise mehrere Ansichten auswählen. Jede Ansicht, die einen Eintrag in der integrierten Entwicklungsumgebung des (IDE) mit der Document-Tabelle (RDT) zugeordnet ist. In den anzeigefenstern gehören zu einem Projekt oder eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt.  
  
 Wenn Ihr Editor mehrere Ansichten für ein dokumentdatenobjekt unterstützt, müssen Ihre Dokumentdaten und dokumentenansichtsobjekten getrennt werden. Andernfalls können sie gruppiert werden. Weitere Informationen finden Sie unter [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
 Die IDE benachrichtigt Ansichten über Ereignisse (z. B., wenn eine Projektmappe mit einem Dokument geschlossen wird) durch entsprechende eine Element-ID (Element-ID) für jeden Eintrag in der aktiven Dokumenttabelle. Weitere Informationen hierzu finden Sie unter [Running Document Table](../extensibility/internals/running-document-table.md).  
  
 Es gibt zwei Optionen zum Erstellen einer Ansicht für einen benutzerdefinierten Editor. Eine ist die direkte Aktivierungsmodell, in dem die Ansicht in einem Fenster mit einem ActiveX-Steuerelement oder ein dokumentdatenobjekt gehostet wird. Die zweite ist die vereinfachte einbetten Modell, in dem die Ansicht von gehostet wird [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> wird implementiert, um die Befehle im Fenster zu behandeln. Weitere Informationen über das Modell für die direkte Aktivierung finden Sie unter [direkte Aktivierung](../misc/in-place-activation.md). Weitere Informationen zu den vereinfachten Modell für worteinbettungen, finden Sie unter [vereinfachtes einbetten](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützen mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)   
 [Zum Vereinfachen des Einbettens](../extensibility/simplified-embedding.md)   
 [Vorgehensweise: Anfügen von Ansichten zu Dokumentdaten](../extensibility/how-to-attach-views-to-document-data.md)   
 [Verwaltung von Dokumentsperren](../extensibility/document-lock-holder-management.md)   
 [Einer und mehreren Registerkarten-Ansichten](../extensibility/single-and-multi-tab-views.md)   
 [Speichern eines Standarddokuments](../extensibility/internals/saving-a-standard-document.md)   
 [Persistenz und die aktive Dokumenttabelle](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Bestimmen daraufhin-Editor eine Datei in einem Projekt](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Editorfactorys](../extensibility/editor-factories.md)

