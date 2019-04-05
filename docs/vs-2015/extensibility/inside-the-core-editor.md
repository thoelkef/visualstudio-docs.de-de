---
title: In der Kern-Editor | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 61484c9d01022b9f3b860f0c7b78dd3aedc045f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961016"
---
# <a name="inside-the-core-editor"></a>In der Kern-Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Kern-Editor ist ein Satz von mehreren Komponenten, mit denen Sie ändern und Abfragen von Textinformationen. Wenn Sie die Kern-Editor mit der legacy-API angepasst haben, können Sie weiterhin diesen Anpassungen verwenden, die über den Editor für Adapter weitergeleitet werden. Es wird jedoch empfohlen, dass Sie Ihre Anpassungen an den neuen Editor API anpassen.  
  
 Die folgenden Bereiche sind einige wichtige Aspekte bei der die Kern-Editor:  
  
-   Textpuffer  
  
-   Textansicht  
  
-   Codefenster  
  
-   Textmarkierungen  
  
-   Text-manager  
  
-   Integration mit Sprachdienste  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Instanziieren des Core-Editors mit der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Enthält schrittweise Anleitungen zur Verwendung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> So erstellen eine Instanz von der Kern-Editor.  
  
 [Zugriff auf den Textpuffer mit der Legacy-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Erläutert den Textpuffer-Rolle in der Kern-Editor, wird erläutert, die zugehörigen Systeme, die werden verwendet, um Zugriff auf den Puffer und enthält eine Liste der von den TextBuffer-Objekt, implementierten Schnittstellen <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Textpufferereignisse in der Legacy-API](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Enthält eine Liste der Schnittstellen, die für die Benachrichtigung über Ereignisse für Text-Puffer verwendet werden.  
  
 [Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der Legacy-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Beschreibt, wie Text Puffern von Ereignissen zu empfehlen.  
  
 [Überwachen der globalen Einstellungen mit dem Text-Manager](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Erläutert, wie TextManager verwendet wird, für die Editor-Kernkomponenten globale Einstellung Informationen freigeben und Empfangen von Benachrichtigungen über Text-Manager-Ereignisse.  
  
 [Zugriff auf die Textansicht mit der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Beschreibt die Textansicht-Rolle in der Kern-Editor, und listet die von implementierten Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.  
  
 [Anpassen von Codefenstern mit der Legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Enthält Informationen wie ein Code-Fenster wird verwendet, um die Textansicht zu schließen, wird erläutert, wie der Codefenster-Manager verwendet ist, Ergänzungen zum Code-Fenster zu und ermöglicht die Benachrichtigung über neue Ansichten.  
  
 [Ändern der Ansichtseinstellungen mit der Legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Enthält schrittweise Anleitungen zum Erzwingen der Einstellungen und erzwungene Einstellungen zu entfernen.  
  
 [Sprachdienste und der Core-Editor](../extensibility/language-services-and-the-core-editor.md)  
 Beschreibt die Instanziierung von einem Sprachdienst, Ergänzungen der Steuerelement-Code.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Exemplarische Vorgehensweise: Erstellen einen Kern-Editor, und registrieren einen Dateityp-Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Enthält schrittweise Anweisungen zum Starten der Kern-Editor von verwaltetem Code.  
  
 [Dropdownleiste](../extensibility/drop-down-bar.md)  
 Beschreibt, wie die Dropdownleiste wird verwendet, im Code-Fenster, und beschreibt die Schnittstellen, die verwendet werden, wenn Sie eine Dropdownleiste implementieren.  
  
 [Verwenden von Textmarkierungen mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Erklärt das Konzept von Textmarkierungen und wie sie in der Kern-Editor verwendet werden, und listet die Schnittstellen, die zum Zugreifen auf und Verwalten von Textmarkierungen verwendet werden.  
  
 [Vorgehensweise: Standard-Text-Marker hinzufügen](../extensibility/how-to-add-standard-text-markers.md)  
 Enthält schrittweise Anleitungen zum Erstellen ein textmarkers und So fügen Sie einen benutzerdefinierten Befehl in einem Kontextmenü Menüelemente hinzu.  
  
 [Vorgehensweise: Erstellen von benutzerdefinierten Textmarkierungen](../extensibility/how-to-create-custom-text-markers.md)  
 Enthält schrittweise Anleitungen zum Erstellen ein benutzerdefinierten textmarkers und den Typ des Markers als Dienst bereitstellen.
