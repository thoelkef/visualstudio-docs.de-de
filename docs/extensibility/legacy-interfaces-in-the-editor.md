---
title: "Legacy-Schnittstellen im Editor | Microsoft Docs"
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
  - "ältere Editoren [Visual Studio SDK]"
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Legacy-Schnittstellen im Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können den Visual Studio\-Editor von legacy\-Schnittstellen zugreifen. Das Visual Studio SDK enthält Adapter genannt *Shims*, die diese Schnittstellen für die Interaktion mit dem neuen Editor ermöglichen. Dennoch wird empfohlen, dass Sie Ihren Legacycode, um den neuen Editor API aktualisieren. Code bieten eine bessere Leistung, und Sie können neue Technologien wie Windows Presentation Foundation \(WPF\) und das Managed Extensibility Framework \(MEF\) verwenden.  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Anpassen von Legacycode in den Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Erläutert, wie den Code den neuen Editor anpassen.|  
|[Neue oder geänderte Verhalten mit Editor\-Adaptern](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Erläutert, wie das Verhalten der Editor\-Adapter von früheren Versionen des Editors unterscheidet.|  
|[In der Core\-Editor](../extensibility/inside-the-core-editor.md)|Beschreibt die verschiedenen Komponenten von früheren Versionen des Editors an.|  
|[Instanziieren die Core\-Editor mithilfe der Legacy\-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Erläutert die legacy\-API verwenden, um die Core\-Editor zu instanziieren.|  
|[Editor\-Factorys](../extensibility/editor-factories.md)|Erläutert das editorfactorys mit legacy\-API verwenden.|  
|[Gewusst wie: Registrieren von Dateitypen\-Editor](../extensibility/how-to-register-editor-file-types.md)|Erläutert die Erweiterung zum Editor verknüpfen.|  
|[Exemplarische Vorgehensweise: Erstellen eines Kern\-Editors, und registrieren einen Dateityp\-Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Erläutert, wie einen Kern\-Editor erstellen und verknüpfen eine Erweiterung zu.|  
|[Gewusst wie: Bereitstellen von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md)|Erläutert, wie um einen Kontext für den Editor anzugeben.|  
|[Language Services und die Core\-Editor](../extensibility/language-services-and-the-core-editor.md)|Erläutert die Interaktionen zwischen einer Sprachdienst und einem Editor.|  
|[Zugriff auf den Textpuffer mit der Legacy\-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Erläutert, wie auf den Textpuffer mithilfe der legacy\-API.|  
|[Zugreifen auf Dietext Ansicht mithilfe der Legacy\-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Erläutert, wie die Ansicht für den Zugriff auf mithilfe der legacy\-API.|  
|[Anpassen von Code Windows mit der Legacy\-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Erläutert das Code\-Fenster anpassen, indem Sie mit der legacy\-API.|  
|[Zugreifen auf Textebenen mithilfe der Legacy\-API](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Erläutert die verschiedene Ebenen von Text mithilfe von legacy\-API zugreifen.|  
|[Verwenden von Text Marker mit der Legacy\-API](../extensibility/using-text-markers-with-the-legacy-api.md)|Erläutert, wie Text Marker mit legacy\-API hinzufügen.|  
|[Anpassen von Editor\-Steuerelemente und Menüs mit der Legacy\-API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Erläutert das Editor\-Steuerelemente mithilfe von legacy\-API anpassen.|  
|[Verwalten von Rückgängigmachen und wiederholen, mit der Legacy\-API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Erläutert, wie verwalten rückgängig und wiederherstellen, indem Sie mit der legacy\-API.|  
|[Gewusst wie: Implementieren Sie suchen und Ersetzen Sie Mechanismus](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Erläutert das Verwalten von Suchen und Ersetzen Sie durch die legacy\-API.|  
|[Gewusst wie: Unterdrücken von Dateiänderungsbenachrichtigungen](../extensibility/how-to-suppress-file-change-notifications.md)|Erläutert das Unterdrücken von dateiänderungsbenachrichtigungen über die legacy\-API.|  
|[Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)|Erläutert das Erstellen von benutzerdefinierten Editoren und Designern.|  
|[Entwickeln einer Sprache](../extensibility/internals/developing-a-legacy-language-service.md)|Enthält Links zu Dokumenten über Funktionen, mit denen Funktionen zur Anpassung an die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core\-Editor durch Hinzufügen von Unterstützung für eine Sprachdienst.|  
|[Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md)|Erläutert, wie Schriftarten und Farben mit legacy\-Schnittstellen.|