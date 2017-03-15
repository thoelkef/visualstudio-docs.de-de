---
title: "Erstellen von benutzerdefinierten Editoren und Designern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Designer [Visual Studio SDK]"
  - "Benutzerdefinierte Editoren [Visual Studio SDK]"
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 31
---
# Erstellen von benutzerdefinierten Editoren und Designern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die integrierte Entwicklungsumgebung \(IDE\) von Visual Studio kann verschiedene Arten von Editor gehostet werden:  
  
-   Der Visual Studio Core\-editor  
  
-   Benutzerdefinierte Editoren  
  
-   Externe Editoren  
  
-   Designer  
  
 Die folgende Informationen können Sie den Typ des Editors auswählen, die Sie benötigen.  
  
## Typen von Editor  
 Informationen zu den wichtigsten Visual Studio\-Editor finden Sie unter [Erweitern der\-Editor und Sprachdienste](../extensibility/extending-the-editor-and-language-services.md).  
  
##### Benutzerdefinierte Editoren  
 Ein benutzerdefinierter Editor ist in speziellen Fällen funktioniert. Z. B. möglicherweise einen Editor erstellen, dessen Funktion zum Lesen und Schreiben von Daten in einem bestimmten Repository, z. B. Microsoft Exchange\-Server ist. Wählen Sie einen benutzerdefinierten Editor, wenn Sie einen Editor, der mit dem Projekttyp nur arbeitet oder gegebenenfalls einen Editor, bei dem nur einige spezifische Befehle. Beachten Sie jedoch, dass Benutzer nicht mithilfe ein benutzerdefiniertes Editors Standard bearbeiten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekte.  
  
 Ein benutzerdefinierter Editor kann mithilfe eine Editorfactory und fügen Informationen zum Editor in der Registrierung. Allerdings kann der Projekttyp, den benutzerdefinierten Editor zugeordnet, den benutzerdefinierten Editor auf andere Weise instanziieren.  
  
 Ein benutzerdefinierter Editor können\-Ort\-Aktivierung oder vereinfachte einbetten Sie eine Ansicht implementieren.  
  
##### Externe Editoren  
 Externe Editoren werden Editoren, die nicht in Visual Studio, z. B. Microsoft Word, Editor oder Microsoft FrontPage integriert sind. Sie können einen\-Editor aufrufen, wenn z. B. Sie Text aus Ihrer VSPackage übergibt sind. Externe Editoren registrieren sich selbst und außerhalb von Visual Studio verwendet werden können. Wenn Sie einen externen Editor aufrufen und es in einem Hostfenster eingebettet werden kann, wird sie in einem Fenster in der IDE. Wenn dies nicht der Fall ist, dann erstellt die IDE ein separates Fenster für sie.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Methode legt die Priorität des Dokuments mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration. Wenn die `DP_External` \-Wert angegeben wird, die durch einen externen Editor geöffnet werden können.  
  
## Designentscheidungen\-Editor  
 Die folgenden Entwurfsfragen helfen Ihnen, wählen Sie den Typ des Editors, die beste für Ihre Anwendung geeignet:  
  
-   Wird die Anwendung die Daten in Dateien oder nicht speichern? Wenn die Daten in Dateien gespeichert werden, werden sie in einem benutzerdefinierten oder standardmäßigen Format?  
  
     Wenn Sie eine standard\-Dateiformat verwenden, werden andere Projekttypen zusätzlich zu Ihrem Projekt zu öffnen und Daten für diese Lese\-\/Schreibberechtigung. Wenn Sie ein benutzerdefiniertes Format verwenden, jedoch werden nur der Projekttyp zu öffnen und Daten für diese Lese\-\/Schreibberechtigung.  
  
     Wenn Ihr Projekt Dateien verwendet, sollten Sie den standard\-Editor anpassen. Wenn das Projekt keine Dateien verwendet, aber stattdessen Elemente in einer Datenbank oder einer anderen Repository verwendet, sollten Sie einen benutzerdefinierten Editor erstellen.  
  
-   Muss als Editor ActiveX\-Steuerelemente zu hosten?  
  
     Wenn Editor ActiveX\-Steuerelemente hostet, dann implementieren einen Editor direkte Aktivierung gemäß [Direkte Aktivierung](../misc/in-place-activation.md). Wenn es kein ActiveX\-Steuerelemente gehostet wird, dann verwenden Sie einen vereinfachten Einbetten von Editor oder Anpassen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Standard\-Editor.  
  
-   Unterstützt der Editor mehrere Ansichten? Wenn Sie Ansichten des Editors gleichzeitig als Standard\-Editor angezeigt werden soll, müssen Sie mehrere Ansichten unterstützen.  
  
     Der Editor muss mehrere Ansichten zu unterstützen, müssen die Dokumentdaten und Document\-Objekte für den Editor separate Objekte sein. Weitere Informationen finden Sie unter [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md).  
  
     Wenn Editor mehrere Ansichten unterstützt, möchten Sie verwenden die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kern des Editors Text Puffer Implementierung \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt\) für Ihr Dokument Datenobjekt? D. h. möchten Sie Ihre\-Editor\-Ansicht\-parallelem mit Unterstützung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core\-Editor? Die Möglichkeit dazu ist die Grundlage für die Forms\-Designer...  
  
-   Wenn Sie einen externen Editor hosten müssen, kann der Editor eingebettet werden in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     Wenn sie eingebettet werden kann, erstellen Sie ein Hostfenster für den externen Editor und rufen Sie dann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Methode, und legen die <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> \-Enumerationswert auf `DP_External`. Wenn der Editor nicht eingebettet werden kann, erstellt die IDE automatisch ein separates Fenster dafür.  
  
## In diesem Abschnitt  
 [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Erstellen ein benutzerdefiniertes Editors erläutert.  
  
 [Exemplarische Vorgehensweise: Hinzufügen eines benutzerdefinierten Editors von Funktionen](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Erläutert das Hinzufügen von Funktionen zu einem benutzerdefinierten Editor.  
  
 [Designer\-Initialisierung und Metadatenkonfiguration](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Erläutert, wie einen Designer initialisiert werden.  
  
 [Bereitstellen von Rückgängig\-Unterstützung für Designer](../extensibility/supplying-undo-support-to-designers.md)  
 Erläutert die Rückgängig\-Unterstützung für Designer bereitgestellt werden.  
  
 [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)  
 Erläutert den Unterschied zwischen Syntaxfarben in der Core\-Editor und benutzerdefinierte Editoren.  
  
 [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Erläutert die Dokumentdaten und Dokumentansichten in benutzerdefinierten Editoren implementieren.  
  
## Verwandte Abschnitte  
 [Legacy\-Schnittstellen im Editor](../extensibility/legacy-interfaces-in-the-editor.md)  
 Erläutert die Core\-Editor die legacy\-API zugreifen.  
  
 [Entwickeln einer Sprache](../extensibility/internals/developing-a-legacy-language-service.md)  
 Erläutert, wie einen Language\-Dienst implementiert.  
  
 [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert die Elemente der Benutzeroberfläche erstellen, die den restlichen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>