---
title: Erstellen von benutzerdefinierten Editoren und Designern | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9f56b82225e1e40782b6753bea03d3c1780f596
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739478"
---
# <a name="create-custom-editors-and-designers"></a>Erstellen benutzerdefinierter Editoren und Designer

Die integrierte Visual Studio-Entwicklungsumgebung (IDE) kann verschiedene Editortypen hosten:

- Der Visual Studio-Kerneditor

- Benutzerdefinierte Editoren

- Externe Redakteure

- Designer

Mit den folgenden Informationen können Sie den benötigten Editortyp auswählen.

## <a name="types-of-editor"></a>Editor-Typen

Informationen zum Visual Studio-Kerneditor finden Sie unter [Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Benutzerdefinierte Editoren
 Ein benutzerdefinierter Editor ist ein Editor, der unter speziellen Umständen arbeiten soll. Sie können z. B. einen Editor erstellen, dessen Funktion darin besteht, Daten in ein bestimmtes Repository, z. B. einen Microsoft Exchange-Server, zu lesen und zu schreiben. Wählen Sie einen benutzerdefinierten Editor aus, wenn Sie einen Editor wünschen, der nur mit Ihrem Projekttyp arbeitet, oder wenn Sie einen Editor mit nur wenigen bestimmten Befehlen benötigen. Beachten Sie jedoch, dass Benutzer keinen benutzerdefinierten Editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Bearbeiten von Standardprojekten verwenden können.

 Ein benutzerdefinierter Editor kann eine Editorfactory verwenden und der Registrierung Informationen über den Editor hinzufügen. Der dem benutzerdefinierten Editor zugeordnete Projekttyp kann den benutzerdefinierten Editor jedoch auf andere Weise instanziieren.

 Ein benutzerdefinierter Editor kann entweder die direkte Aktivierung oder die vereinfachte Einbettung verwenden, um eine Ansicht zu implementieren.

### <a name="external-editors"></a>Externe Editoren
 Externe Editoren sind Editoren, die nicht in Visual Studio integriert sind, z. B. Microsoft Word, Notepad oder Microsoft FrontPage. Sie können einen solchen Editor aufrufen, wenn Sie z. B. Text aus Ihrem VSPackage an ihn übergeben. Externe Editoren registrieren sich selbst und können außerhalb von Visual Studio verwendet werden. Wenn Sie einen externen Editor aufrufen und er in ein Hostfenster eingebettet werden kann, wird er in einem Fenster in der IDE angezeigt. Wenn dies nicht der Fall ist, erstellt die IDE ein separates Fenster dafür.

 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Methode legt die Dokumentpriorität mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration fest. Wenn `DP_External` der Wert angegeben ist, kann die Datei von einem externen Editor geöffnet werden.

## <a name="editor-design-decisions"></a>Editor-Design-Entscheidungen
 Die folgenden Entwurfsfragen helfen Ihnen bei der Auswahl des Für-Antrags-Typs geeigneten Editors:

- Wird Ihre Anwendung ihre Daten in Dateien speichern oder nicht? Wenn es seine Daten in Dateien speichern wird, werden sie in einem benutzerdefinierten oder Standardformat sein?

   Wenn Sie ein Standarddateiformat verwenden, können neben dem Projekt auch andere Projekttypen Daten öffnen und lesen/schreiben. Wenn Sie jedoch ein benutzerdefiniertes Dateiformat verwenden, kann nur der Projekttyp Daten öffnen und lesen/schreiben.

   Wenn Ihr Projekt Dateien verwendet, sollten Sie den Standard-Editor anpassen. Wenn Ihr Projekt keine Dateien verwendet, sondern Elemente in einer Datenbank oder einem anderen Repository verwendet, sollten Sie einen benutzerdefinierten Editor erstellen.

- Muss Ihr Editor ActiveX-Steuerelemente hosten?

   Wenn Ihr Editor ActiveX-Steuerelemente hostet, implementieren Sie einen in-Place-Aktivierungseditor, wie unter [An-Ort-Aktivierung](/visualstudio/misc/in-place-activation?view=vs-2015)beschrieben. Wenn ActiveX-Steuerelemente nicht hosten, verwenden Sie entweder einen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vereinfachten Einbettungseditor, oder passen Sie den Standard-Editor an.

- Unterstützt Ihr Editor mehrere Ansichten? Sie müssen mehrere Ansichten unterstützen, wenn Ansichten des Editors gleichzeitig mit dem Standardeditor sichtbar sein sollen.

   Wenn der Editor mehrere Ansichten unterstützen muss, müssen die Dokumentdaten- und Dokumentansichtsobjekte für den Editor separate Objekte sein. Weitere Informationen finden Sie unter [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md).

   Wenn Ihr Editor mehrere Ansichten unterstützt, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] planen Sie, die Textpufferimplementierung (Objekt)<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> des Kerneditors für Ihr Dokumentdatenobjekt zu verwenden? Das heißt, möchten Sie Ihre Editor-Ansicht Seite an [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Seite mit dem Kerneditor unterstützen? Die Fähigkeit, dies zu tun, ist die Grundlage des Formulardesigners.

- Wenn Sie einen externen Editor hosten müssen, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]kann der Editor eingebettet werden?

   Wenn es eingebettet werden kann, sollten Sie ein Hostfenster <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> für den <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> externen Editor erstellen `DP_External`und dann die Methode aufrufen und den Enumerationswert auf festlegen. Wenn der Editor nicht eingebettet werden kann, erstellt die IDE automatisch ein separates Fenster dafür.

## <a name="in-this-section"></a>In diesem Abschnitt

[Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md)\
Erläutert, wie ein benutzerdefinierter Editor erstellt wird.

[Exemplarische Vorgehensweise: Hinzufügen von Features zu einem benutzerdefinierten Editor](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Erläutert das Hinzufügen von Features zu einem benutzerdefinierten Editor.

[Designerinitialisierung und Metadatenkonfiguration](../extensibility/designer-initialization-and-metadata-configuration.md)\
Erläutert, wie ein Designer initialisiert wird.

[Bereitstellung von Undo-Unterstützung für Designer](../extensibility/supplying-undo-support-to-designers.md)\
Erläutert, wie Designer nützen.

[Syntaxfärbung in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)\
Erläutert den Unterschied zwischen der Syntaxfärbung im Kerneditor und in benutzerdefinierten Editoren.

[Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Erläutert das Implementieren von Dokumentdaten und Dokumentansichten in benutzerdefinierten Editoren.

## <a name="related-sections"></a>Verwandte Abschnitte

[Legacy-Schnittstellen im Editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
Erläutert, wie der Kerneditor über die Legacy-API auf den Kerneditor zugreifen kann.

[Entwickeln eines älteren Sprachdienstes](../extensibility/internals/developing-a-legacy-language-service.md)\
Erläutert, wie ein Sprachdienst implementiert wird.

[Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Erläutert, wie UI-Elemente erstellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]werden, die mit dem Rest von übereinstimmen.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
