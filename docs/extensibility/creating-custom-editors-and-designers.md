---
title: Erstellen von benutzerdefinierten Editoren und Designern | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08d9ee33d49985fed8e8c0180fa652aed39b25d9
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186809"
---
# <a name="create-custom-editors-and-designers"></a>Erstellen von benutzerdefinierten Editoren und Designern

Die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio kann unterschiedliche Arten von Editor hosten:

- Der Visual Studio-Kern-Editor

- Benutzerdefinierte Editoren

- Externe Editoren

- Designer

Die folgenden Informationen helfen Ihnen bei der Auswahl des benötigten Editors.

## <a name="types-of-editor"></a>Editor Typen

Weitere Informationen zum Visual Studio-Kern-Editor finden Sie unter [Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Benutzerdefinierte Editoren
 Ein benutzerdefinierter Editor ist ein benutzerdefinierter Editor, der in speziellen Situationen funktionieren soll. Beispielsweise können Sie einen Editor erstellen, dessen Funktion das Lesen und Schreiben von Daten in ein bestimmtes Repository, z. b. ein Microsoft Exchange-Server, ist. Wählen Sie einen benutzerdefinierten Editor aus, wenn Sie einen Editor benötigen, der nur mit dem Projekttyp funktioniert, oder wenn Sie einen Editor benötigen, der nur über einige bestimmte Befehle verfügt. Beachten Sie jedoch, dass Benutzer einen benutzerdefinierten Editor nicht verwenden können, um Standard [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekte zu bearbeiten.

 Ein benutzerdefinierter Editor kann eine Editorfactory verwenden und der Registrierung Informationen über den Editor hinzufügen. Der mit dem benutzerdefinierten Editor verknüpfte Projekttyp kann den benutzerdefinierten Editor jedoch auf andere Weise instanziieren.

 Ein benutzerdefinierter Editor kann entweder eine direkte Aktivierung oder eine vereinfachte Einbettung verwenden, um eine Ansicht zu implementieren.

### <a name="external-editors"></a>Externe Editoren
 Externe Editoren sind Editoren, die nicht in Visual Studio integriert sind, z. b. Microsoft Word, Notepad oder Microsoft FrontPage. Sie könnten beispielsweise einen solchen Editor aufzurufen, wenn Sie z. b. Text aus Ihrem VSPackage an ihn übergeben. Externe Editoren registrieren sich selbst und können außerhalb von Visual Studio verwendet werden. Wenn Sie einen externen Editor aufzurufen und in ein Host Fenster eingebettet werden können, wird dieser in einem Fenster in der IDE angezeigt. Wenn dies nicht der Fall ist, erstellt die IDE ein separates Fenster dafür.

 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>-Methode legt die Dokument Priorität mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>-Enumeration fest. Wenn der `DP_External`-Wert angegeben wird, kann die Datei von einem externen Editor geöffnet werden.

## <a name="editor-design-decisions"></a>Entwurfsentscheidungen im Editor
 Die folgenden Entwurfs Fragen helfen Ihnen, den Typ des Editors auszuwählen, der für Ihre Anwendung am besten geeignet ist:

- Speichert Ihre Anwendung Ihre Daten in Dateien? Wenn die Daten in Dateien gespeichert werden, befinden Sie sich in einem benutzerdefinierten oder Standardformat?

   Wenn Sie ein Standarddatei Format verwenden, können andere Projekttypen zusätzlich zu Ihrem Projektdaten öffnen und in diese schreiben/schreiben. Wenn Sie jedoch ein benutzerdefiniertes Dateiformat verwenden, kann nur Ihr Projekttyp Daten öffnen und in diese schreiben/schreiben.

   Wenn das Projektdateien verwendet, sollten Sie den Standard-Editor anpassen. Wenn das Projekt keine Dateien verwendet, sondern stattdessen Elemente in einer Datenbank oder einem anderen Repository verwendet, sollten Sie einen benutzerdefinierten Editor erstellen.

- Muss der Editor ActiveX-Steuerelemente hosten?

   Wenn Ihr Editor ActiveX-Steuerelemente hostet, implementieren Sie einen direkten Aktivierungs-Editor, wie unter direkte [Aktivierung](../extensibility/in-place-activation.md)beschrieben. Wenn keine ActiveX-Steuerelemente gehostet werden, verwenden Sie entweder einen vereinfachten Einbettungs-Editor, oder passen Sie den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Standard-Editor an.

- Unterstützt der Editor mehrere Ansichten? Sie müssen mehrere Sichten unterstützen, wenn Sie möchten, dass Ansichten des Editors zur gleichen Zeit wie der Standard-Editor sichtbar sind.

   Wenn Ihr Editor mehrere Ansichten unterstützen muss, müssen die Dokument Daten-und Dokument Ansichts Objekte für den Editor getrennte Objekte sein. Weitere Informationen finden Sie [unter Unterstützung mehrerer Dokument Ansichten](../extensibility/supporting-multiple-document-views.md).

   Wenn der Editor mehrere Ansichten unterstützt, planen Sie die Verwendung der Text Puffer Implementierung des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editors (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>-Objekts) für das Dokument Datenobjekt? Das heißt, möchten Sie die Editor-Ansicht parallel mit dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editor unterstützen? Die Möglichkeit, dies zu erreichen, ist die Basis des Forms-Designers.

- Wenn Sie einen externen Editor hosten müssen, kann der Editor in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]eingebettet werden?

   Wenn Sie eingebettet werden kann, sollten Sie ein Host Fenster für den externen Editor erstellen und dann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>-Methode aufzurufen und den <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumerationswert auf `DP_External`festlegen. Wenn der Editor nicht eingebettet werden kann, wird von der IDE automatisch ein separates Fenster erstellt.

## <a name="in-this-section"></a>In diesem Abschnitt

Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md)\
Erläutert das Erstellen eines benutzerdefinierten Editors.

Exemplarische Vorgehensweise [: Hinzufügen von Funktionen zu einem benutzerdefinierten Editor](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Erläutert das Hinzufügen von Funktionen zu einem benutzerdefinierten Editor.

[Initialisierungs-und metadatenkonfigurations-](../extensibility/designer-initialization-and-metadata-configuration.md)\ des Designers
Erläutert, wie ein Designer initialisiert wird.

[Unterstützung für die Bereitstellung an Designer](../extensibility/supplying-undo-support-to-designers.md)\
Erläutert die Bereitstellung von Rückgängig-Unterstützung für-Designer.

[Syntax Farbgebung in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)\
Erläutert den Unterschied zwischen der Syntax Farbgebung im Kern-Editor und in benutzerdefinierten Editoren.

[Dokument Daten und Dokument Ansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Erläutert, wie Dokument Daten und Dokument Sichten in benutzerdefinierten Editoren implementiert werden.

## <a name="related-sections"></a>Verwandte Abschnitte

[Legacy Schnittstellen im Editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
Erläutert, wie Sie mithilfe der Legacy-API auf den Kern-Editor zugreifen können.

[Entwickeln eines Legacy sprach Dienstanbieter](../extensibility/internals/developing-a-legacy-language-service.md)\
Erläutert, wie ein Sprachdienst implementiert wird.

[Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Erläutert das Erstellen von UI-Elementen, die dem Rest [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]entsprechen.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>