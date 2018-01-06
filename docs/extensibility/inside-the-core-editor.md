---
title: In der Core-Editor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e4612f5779d6177d58cef7f087ef6e11bbe4ebd9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="inside-the-core-editor"></a>In der Core-Editor
Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Core-Editor ist ein Satz von mehreren Komponenten, mit denen Sie ändern und Abfragen von Textinformationen. Wenn Sie die Core-Editor angepasst haben, über die legacy-API, können Sie weiterhin diesen Anpassungen zu verwenden, die Editor Adapter weitergeleitet wird. Es wird jedoch empfohlen, dass Sie Ihre Anpassungen an den neuen Editor API anpassen.  
  
 Die folgenden Bereiche sind einige wichtige Aspekte des Core-Editors:  
  
-   Textpuffer  
  
-   Textansicht  
  
-   Codefenster  
  
-   Text-Marker  
  
-   Text-manager  
  
-   Integration in Sprachdienste  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Instanziieren den Core-Editor mithilfe der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Enthält schrittweise Anleitungen zur Verwendung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> So erstellen eine Instanz des Kerns-Editor.  
  
 [Zugreifen auf den Textpuffer mithilfe der Legacy-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Erläutert den Textpuffer-Rolle in der Core-Editor, erläutert die zugeordneten Systeme, werden verwendet, um Zugriff auf den Puffer, und enthält eine Liste der von der TextBuffer-Objekt, implementierten Schnittstellen <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Text-Puffer-Ereignisse in die Legacy-API](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Enthält eine Liste der Schnittstellen, die für die Benachrichtigung von Text-Puffer-Ereignissen verwendet werden.  
  
 [Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der Legacy-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Beschreibt, wie Text-Puffer Ereignisse informiert.  
  
 [Verwenden die Text-Manager zum Überwachen von globaler Einstellungen](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Erläutert, wie der TextManager verwendet wird, die Editor-Kernkomponenten globale Einstellung Informationen freigeben und wie der Text-Manager-Ereignisse benachrichtigt werden soll.  
  
 [Zugreifen auf TheText Ansicht über die Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Eine Beschreibung der Textansicht-Rolle in der Core-Editor und den implementierten Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.  
  
 [Anpassen von Code-Fenster mit der Legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Enthält Informationen wie ein Codefenster wird verwendet, um das Schließen der Textansicht, erläutert, wie der Code-Fenster-Manager zum Bereitstellen von Ergänzungen, die in das Codefenster für und ermöglicht die Benachrichtigung über neue Ansichten.  
  
 [Ändern Einstellungen anzeigen, über die Legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Enthält schrittweise Anleitungen zum Anzeigen von Einstellungen zu erzwingen und erzwungene Einstellungen zu entfernen.  
  
 [Language-Dienste und die Core-Editor](../extensibility/language-services-and-the-core-editor.md)  
 Beschreibt die Instanziierung eines Diensts Sprache Steuerelement Code Ergänzungen an.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Exemplarische Vorgehensweise: Erstellen eines Kern-Editors, und registrieren einen Dateityp-Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Enthält schrittweise Anleitungen zum Starten des Core-Editors aus verwaltetem Code.  
  
 [Dropdown-Leiste](../extensibility/drop-down-bar.md)  
 Beschreibt, wie die Dropdownleiste im Codefenster verwendet wird, und beschreibt die Schnittstellen, die bei der Implementierung einer Dropdownleiste verwendet werden.  
  
 [Verwenden von Text Marker mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Erklärt das Konzept der Marker aus Text und deren Verwendung in der Core-Editor, und listet die Schnittstellen, die zum zugreifen und diese verwalten Text Marker verwendet werden.  
  
 [Vorgehensweise: Hinzufügen von Standard-Text-Marker](../extensibility/how-to-add-standard-text-markers.md)  
 Enthält schrittweise Anweisungen zur Vorgehensweise: Erstellen Sie einen Text-Marker und zum Hinzufügen eines benutzerdefinierten Befehls zu einem Kontextmenü.  
  
 [Vorgehensweise: Erstellen von benutzerdefinierten Text-Marker](../extensibility/how-to-create-custom-text-markers.md)  
 Enthält schrittweise Anweisungen zur Vorgehensweise: Erstellen Sie einen benutzerdefinierten Text Marker und wie Sie den Markertyp als Dienst bereitstellen.