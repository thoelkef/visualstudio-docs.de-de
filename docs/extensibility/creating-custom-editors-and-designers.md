---
title: Erstellen von benutzerdefinierten Editoren und Designern | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: "31"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 149870d9c9a0a281cb0bba167496cc4c37d6f83a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="creating-custom-editors-and-designers"></a>Erstellen von benutzerdefinierten Editoren und Designern
Die integrierte Entwicklungsumgebung (IDE) von Visual Studio kann verschiedene Typen von Editor hosten:  
  
-   Der Visual Studio Core-editor  
  
-   Benutzerdefinierte Editoren  
  
-   Externe Editoren  
  
-   Designer  
  
 Die folgende Informationen können Sie den Typ des Editors auswählen, die Sie benötigen.  
  
## <a name="types-of-editor"></a>Typen des Editors  
 Informationen über die Visual Studio-Core-Editor finden Sie unter [Erweiterung des Editors und des Sprachdienste](../extensibility/extending-the-editor-and-language-services.md).  
  
##### <a name="custom-editors"></a>Benutzerdefinierte Editoren  
 Ein benutzerdefinierter Editor ist in speziellen Fällen verwendet. Z. B. möglicherweise einen Editor erstellen, deren Funktion wird zum Lesen und Schreiben von Daten in einem bestimmten-Repository, z. B. einem Microsoft Exchange-Server. Wählen Sie einen benutzerdefinierten Editor, wenn Sie einen Editor, der mit Ihrem Projekttyp nur arbeitet oder gegebenenfalls einen Editor, die nur einige bestimmte Befehle hat. Beachten Sie jedoch, dass Benutzer nicht um einen benutzerdefinierten Editor zu verwenden, um Standard bearbeiten können [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekte.  
  
 Ein benutzerdefinierter Editor kann verwenden Sie eine Editorfactory und Informationen zum Editor zur Registrierung hinzuzufügen. Allerdings kann den benutzerdefinierten Editor auf andere Weise der Projekttyp, der den benutzerdefinierten Editor zugeordnet instanziiert werden.  
  
 Ein benutzerdefinierter Editor können direkte Aktivierung oder vereinfachte einbetten Sie eine Sicht implementieren.  
  
##### <a name="external-editors"></a>Externe Editoren  
 Externe Editoren sind Editoren, die nicht in Visual Studio, z. B. Microsoft Word, Editor oder Microsoft FrontPage integriert werden. Sie möglicherweise einen-Editor aufrufen, wenn z. B. Sie Text, aus Ihrem VSPackage übergeben werden. Externe Editoren registrieren sich und außerhalb von Visual Studio verwendet werden können. Wenn Sie einen externen Editor aufrufen und es in einem Hostfenster eingebettet werden kann, wird er in einem Fenster in der IDE. Wenn dies nicht der Fall ist, klicken Sie dann die IDE erstellt ein separates Fenster dafür.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Methode legt die Priorität des Dokuments mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration. Wenn die `DP_External` -Wert angegeben wird, die durch einen externen Editor geöffnet werden können.  
  
## <a name="editor-design-decisions"></a>Entwurfsentscheidungen-Editor  
 Die folgenden Entwurfsfragen unterstützt Sie beim Auswählen des besten Editor-Typs für Ihre Anwendung geeignet:  
  
-   Wird die Anwendung die Daten in Dateien oder nicht speichern? Wenn sie die Daten in Dateien gespeichert werden, werden sie in einem benutzerdefinierten oder standardmäßigen Format?  
  
     Wenn Sie einen standard-Dateiformat verwenden, werden andere Projekttypen zusätzlich zu Ihrem Projekt zu öffnen und Daten für diese Lese-/Schreibberechtigung. Wenn Sie eine benutzerdefinierte Dateiformat verwenden, sind jedoch nur vom Projekttyp Lage zu öffnen und Daten für diese Lese-/Schreibberechtigung.  
  
     Wenn das Projekt Dateien verwendet, sollten Sie die standard-Editors anpassen. Wenn Ihr Projekt keine Dateien verwendet, aber stattdessen Elemente in einer Datenbank oder anderen Repository verwendet, sollten Sie einen benutzerdefinierten Editor erstellen.  
  
-   Ist in der Editor zum Hosten von ActiveX-Steuerelemente erforderlich?  
  
     Wenn der Editor ActiveX-Steuerelemente hostet, implementieren einen Editor, das direkte Aktivierung klicken Sie dann im [direkte Aktivierung](../extensibility/in-place-activation.md). Wenn sie kein ActiveX-Steuerelemente gehostet wird, klicken Sie dann einen vereinfachten einbetten-Editor verwenden oder Anpassen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Standard-Editor.  
  
-   Wird für der Editor mehrere Ansichten unterstützt? Sie müssen mehrere Ansichten unterstützen, wenn Ansichten des Editors gleichzeitig als Standard-Editor angezeigt werden soll.  
  
     Wenn der Editor mehrere Ansichten zu unterstützen muss, müssen der Dokumentdaten und Ansicht-Dokumentobjekte für den Editor separate Objekte sein. Weitere Informationen finden Sie unter [unterstützen mehrere Dokumentansichten](../extensibility/supporting-multiple-document-views.md).  
  
     Wenn der Editor über mehrere Ansichten unterstützt, möchten Sie verwenden die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Haupt-Editor Text-Puffer-Implementierung (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt) für Ihre dokumentdatenobjekt? D. h., möchten Sie Ihre Editor Ansicht Seite-an-Seite mit Unterstützung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editor? Die Möglichkeit hierfür bildet die Grundlage der Forms-Designer...  
  
-   Wenn Sie einen externen Editor hosten müssen, kann der Editor eingebettet werden in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     Wenn sie eingebettet werden kann, sollten Sie ein Hostfenster für den externen Editor erstellen und rufen dann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> -Methode, und legen die <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumerationswert, auf `DP_External`. Wenn der Editor nicht eingebettet werden kann, wird die IDE automatisch ein separates Fenster dafür erstellen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Erläutert das Erstellen eines benutzerdefinierten Editors.  
  
 [Exemplarische Vorgehensweise: Hinzufügen von Funktionen zu einem benutzerdefinierten Editor](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Erläutert das Hinzufügen von Funktionen zu einer benutzerdefinierten Editor.  
  
 [Designer-Initialisierung und Metadatenkonfiguration](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Erläutert, wie einen Designer initialisiert werden.  
  
 [Bereitstellen von Rückgängig-Unterstützung für Designer](../extensibility/supplying-undo-support-to-designers.md)  
 Erläutert, wie Designer Rückgängig-Unterstützung bereit.  
  
 [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)  
 Erläutert den Unterschied zwischen Syntaxfarben Core im Editor und in benutzerdefinierten Editoren.  
  
 [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Erläutert die Dokumentdaten und Dokumentansichten in benutzerdefinierten Editoren implementieren.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Legacy-Schnittstellen im Editor](../extensibility/legacy-interfaces-in-the-editor.md)  
 Erläutert die Core-Editor über die legacy-API zugreifen.  
  
 [Entwickeln eines Legacysprachdiensts](../extensibility/internals/developing-a-legacy-language-service.md)  
 Implementieren Sie einen Sprachdienst erläutert.  
  
 [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert, wie Sie Elemente der Benutzeroberfläche zu erstellen, die restliche entspricht [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>