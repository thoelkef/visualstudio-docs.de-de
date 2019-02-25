---
title: Erstellen von benutzerdefinierten Editoren und Designern | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c29b5c5e80f8a0381a2c42704d14a8ea9fc3cae5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721068"
---
# <a name="create-custom-editors-and-designers"></a>Erstellen von benutzerdefinierten Editoren und Designern
Die integrierte Entwicklungsumgebung (IDE) von Visual Studio kann auf verschiedene Arten von Editor hosten:

- Die Visual Studio-Kern-editor

- Benutzerdefinierte Editoren

- Externe Editoren

- Designer

  Die folgende Informationen können Sie den Typ des Editors auswählen, die Sie benötigen.

## <a name="types-of-editor"></a>Typen des Editors
 Weitere Informationen zu den Visual Studio-Kern-Editor, finden Sie unter [Erweiterung der Dienste, Editoren und Sprachen](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Benutzerdefinierte Editoren
 Ein benutzerdefinierter Editor ist eine, die entwickelt wurde, in speziellen Umständen funktioniert. Z. B. können Sie einen Editor erstellen, deren Funktion zum Lesen und Schreiben von Daten in ein bestimmtes Repository wie z. B. Microsoft Exchange-Server ist. Wählen Sie einen benutzerdefinierten Editor, wenn Sie einen Editor, der mit der Art Ihres Projekts funktioniert oder ggf. einen Editor, die nur einige spezifische Befehle hat. Beachten Sie jedoch, dass Benutzer nicht um einen benutzerdefinierten Editor zu verwenden, um Standard bearbeiten können [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekte.

 Ein benutzerdefinierter Editor kann eine Editorfactory verwenden und Informationen zum Editor zur Registrierung hinzuzufügen. Allerdings kann der Projekttyp, der den benutzerdefinierten Editor zugeordnet, den benutzerdefinierten Editor auf andere Weise instanziieren.

 Ein benutzerdefinierter Editor können direkte Aktivierung oder vereinfachtes einbetten Sie um eine Ansicht zu implementieren.

### <a name="external-editors"></a>Externe Editoren
 Externe Editoren sind-Editoren, die nicht in Visual Studio, z. B. Microsoft Word oder Microsoft FrontPage, integriert werden. Sie können einen-Editor aufrufen, wenn, z. B. Sie Text, aus einem VSPackage übergeben werden. Externe Editoren registrieren sich selbst und außerhalb von Visual Studio verwendet werden können. Wenn Sie einen externen Editor aufrufen und es in ein Hostfenster eingebettet werden kann, wird es in einem Fenster in der IDE. Wenn dies nicht der Fall ist, klicken Sie dann die IDE erstellt ein separates Fenster für sie.

 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Methode legt die Priorität des Dokuments mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration. Wenn die `DP_External` Wert angegeben wird, die Datei kann von einem externen Editor geöffnet werden.

## <a name="editor-design-decisions"></a>Editor-entwurfsentscheidungen
 Die folgenden Entwurfsfragen helfen Ihnen, wählen Sie den Typ des Editors, die beste für Ihre Anwendung geeignet sind:

- Wird Ihre Anwendung die Daten in Dateien oder nicht speichern? Wenn sie die Daten in Dateien gespeichert werden, werden sie in einem benutzerdefinierten oder standardmäßigen Format?

   Wenn Sie ein standard-Dateiformat verwenden, werden andere Projekttypen zusätzlich zu Ihrem Projekt zu öffnen und Daten für sie Lese-/Schreibberechtigung. Wenn Sie ein benutzerdefiniertes Dateiformat verwenden, jedoch werden nur die Art Ihres Projekts zu öffnen und Daten für sie Lese-/Schreibberechtigung.

   Wenn Ihr Projekt Dateien verwendet, sollten Sie in der standard-Editor anpassen. Wenn Ihr Projekt keine Dateien verwendet, aber stattdessen Elemente in einer Datenbank oder anderen Repository verwendet, sollten Sie einen benutzerdefinierten Editor erstellen.

- Muss Ihr Editor für ActiveX-Steuerelemente hosten?

   Wenn Ihr Editor für ActiveX-Steuerelemente hostet, dann implementieren einen direkten Aktivierung-Editor, wie unter [direkte Aktivierung](../extensibility/in-place-activation.md). Wenn es kein ActiveX-Steuerelemente gehostet wird, klicken Sie dann entweder einen vereinfachten einbetten Editor verwenden oder Anpassen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Standard-Editor.

- Wird als Editor verwenden, die mehrere Ansichten unterstützt? Wenn Ansichten des Editors zur gleichen Zeit wie der Standard-Editor angezeigt werden soll, müssen Sie auch mehrere Ansichten unterstützen.

   Wenn Ihr Editor mehrere Ansichten zu unterstützen muss, müssen die Dokumentdaten und dokumentenansichtsobjekten für den Editor separate Objekte sein. Weitere Informationen finden Sie unter [unterstützen mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md).

   Wenn Ihr Editor mehrere Ansichten unterstützt, möchten Sie verwenden die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] core-Anmerkung des Text-Puffer-Implementierung (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt) für Ihre dokumentendatenobjekt? D.h., möchten Sie Ihre-Editor-Ansicht Seite-an-Seite mit Unterstützung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Kern-Editor? Die Möglichkeit hierzu ist die Grundlage für das Forms-Designer...

- Wenn Sie einen externen Editor hosten müssen, kann der Editor eingebettet werden in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?

   Wenn sie eingebettet werden kann, erstellen Sie ein Hostfenster für den externen Editor, und rufen Sie dann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Methode, und legen die <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumerationswert zu `DP_External`. Wenn der Editor kann nicht eingebettet werden, wird die IDE automatisch ein separates Fenster dafür erstellt.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefiniertes Editors](../extensibility/walkthrough-creating-a-custom-editor.md) wird erläutert, wie Sie einen benutzerdefinierten Editor erstellen.

- [Exemplarische Vorgehensweise: Hinzufügen von Funktionen zu einer benutzerdefinierten Editor](../extensibility/walkthrough-adding-features-to-a-custom-editor.md) wird erläutert, wie Sie einen benutzerdefinierten Editor Features hinzu.

- [Designer-Initialisierung und Metadaten Konfiguration](../extensibility/designer-initialization-and-metadata-configuration.md) wird erläutert, wie ein Designer initialisiert.

- [Geben Sie die Rückgängig-Unterstützung für Designer](../extensibility/supplying-undo-support-to-designers.md) wird erläutert, wie zum Bereitstellen von Rückgängig-Unterstützung für Designer.

- [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md) erläutert den Unterschied zwischen Syntaxfarben, die in der Kern-Editor und in benutzerdefinierten Editoren.

- [Dokumentieren Sie die Daten und das Dokument anzeigen, in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md) wird erläutert, wie Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren implementieren.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Legacy-Schnittstellen im Editor](../extensibility/legacy-interfaces-in-the-editor.md) wird erläutert, wie der Kern-Editor mithilfe der legacy-API zugreifen.

- [Entwickeln eines Datendiensts legacysprache](../extensibility/internals/developing-a-legacy-language-service.md) wird erläutert, wie einen Sprachdienst zu implementieren.

- [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md) wird erläutert, wie Elemente der Benutzeroberfläche zu erstellen, die den Rest der entsprechen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>