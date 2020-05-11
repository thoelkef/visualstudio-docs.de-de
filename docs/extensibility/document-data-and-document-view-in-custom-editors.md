---
title: Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e89194ff09bc273294246cc25718c999daf70f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712134"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren
Ein benutzerdefinierter Editor besteht aus zwei Teilen: einem Dokumentdatenobjekt und einem Dokumentansichtsobjekt. Wie die Namen vermuten lassen, stellt das Dokumentdatenobjekt die anzuzeigenden Textdaten dar. Ebenso stellt das Dokumentansichtsobjekt (oder "Ansicht") ein oder mehrere Fenster dar, in denen das Dokumentdatenobjekt angezeigt werden soll.

## <a name="document-data-object"></a>Dokumentdatenobjekt
 Ein Dokumentdatenobjekt ist eine Datendarstellung von Text im Textpuffer. Es ist ein COM-Objekt, das Dokumenttext und andere Informationen speichert. Das Dokumentdatenobjekt verarbeitet auch die Dokumentpersistenz und ermöglicht mehrere Ansichten seiner Daten. Weitere Informationen finden Sie unter

 <xref:EnvDTE80.Window2.DocumentData%2A>und [Document Windows](../extensibility/internals/document-windows.md).

 Benutzerdefinierte Editoren und Designer <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> können das Objekt oder ihren eigenen benutzerdefinierten Puffer verwenden. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>folgt dem vereinfachten Einbettungsmodell für einen Standard-Editor, unterstützt mehrere Ansichten und stellt Ereignisschnittstellen bereit, die zum Verwalten mehrerer Ansichten verwendet werden.

## <a name="document-view-object"></a>Dokumentansichtsobjekt
 Ein Fenster, in dem Code und anderer Text angezeigt werden, wird als Dokumentansicht oder -ansicht bezeichnet. Wenn Sie einen Editor erstellen, können Sie entweder eine einzelne Ansicht auswählen, in der Text in einem einzelnen Fenster angezeigt wird. Sie können auch eine Mehrfachansicht auswählen, in der Text in mehr als einem Fenster angezeigt wird. Ihre Wahl hängt von Ihrer Anwendung ab. Wenn Sie z. B. eine Seite-an-Seite-Bearbeitung benötigen, wählen Sie mehrere Ansichten aus. Jede Ansicht ist einem Eintrag in der IDE-Laufdokumenttabelle (IDE) der integrierten Entwicklungsumgebung zugeordnet. Ansichtsfenster gehören zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> einem Projekt oder Objekt.

 Wenn der Editor mehrere Ansichten eines Dokumentdatenobjekts unterstützt, müssen die Dokumentdaten- und Dokumentansichtsobjekte getrennt sein. Andernfalls können sie gruppiert werden. Weitere Informationen finden Sie unter [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md).

 Die IDE benachrichtigt Ansichten über Ereignisse (z. B. wenn eine Projektmappe, die ein Dokument schließt) durch Abgleich eines Elementbezeichners (ItemID) für jeden Eintrag in der laufenden Dokumenttabelle. Weitere Informationen hierzu finden Sie unter Ausführen der [Dokumenttabelle](../extensibility/internals/running-document-table.md).

 Es gibt zwei Optionen zum Erstellen einer Ansicht für einen benutzerdefinierten Editor. Eines davon ist das ortsspezifische Aktivierungsmodell, bei dem die Ansicht in einem Fenster mit einem ActiveX-Steuerelement oder einem Dokumentdatenobjekt gehostet wird. Das zweite ist das vereinfachte Einbettungsmodell, bei dem die Ansicht von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gehostet wird und <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> implementiert wird, um Fensterbefehle zu verarbeiten. Informationen zum in-place-Aktivierungsmodell finden Sie unter [In-Place-Aktivierung](/visualstudio/misc/in-place-activation?view=vs-2015). Informationen zum vereinfachten Einbettungsmodell finden Sie unter [Vereinfachtes Einbetten](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Weitere Informationen

- [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)
- [Vereinfachte Einbettung](../extensibility/simplified-embedding.md)
- [Gewusst wie: Anfügen von Ansichten zu Dokumentdaten](../extensibility/how-to-attach-views-to-document-data.md)
- [Verwaltung von Dokumentenschlosshaltern](../extensibility/document-lock-holder-management.md)
- [Einzel- und Multi-Tab-Ansichten](../extensibility/single-and-multi-tab-views.md)
- [Speichern eines Standarddokuments](../extensibility/internals/saving-a-standard-document.md)
- [Persistenz und die laufende Dokumenttabelle](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Bestimmen, welcher Editor eine Datei in einem Projekt öffnet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
