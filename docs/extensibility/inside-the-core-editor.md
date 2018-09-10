---
title: In der Kern-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 37c62ebad5b5f119c9acf5b62b14db6743949c19
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500448"
---
# <a name="inside-the-core-editor"></a>In der Kern-editor
Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Kern-Editor ist ein Satz von mehreren Komponenten, mit denen Sie ändern und Abfragen von Textinformationen. Wenn Sie die Kern-Editor mit der legacy-API angepasst haben, können Sie weiterhin diesen Anpassungen verwenden, die über den Editor für Adapter weitergeleitet werden. Es wird jedoch empfohlen, dass Sie Ihre Anpassungen an den neuen Editor API anpassen.  
  
 Die folgenden Bereiche sind einige wichtige Aspekte bei der die Kern-Editor:  
  
-   Textpuffer  
  
-   Textansicht  
  
-   Codefenster  
  
-   Textmarkierungen  
  
-   Text-manager  
  
-   Integration mit Sprachdienste  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Instanziieren Sie die Kern-Editor, indem Sie die legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Enthält schrittweise Anleitungen zur Verwendung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> So erstellen eine Instanz von der Kern-Editor.  
  
 [Zugriff auf den Textpuffer mithilfe der legacy-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Erläutert den Textpuffer-Rolle in der Kern-Editor, wird erläutert, die zugehörigen Systeme, die werden verwendet, um Zugriff auf den Puffer und enthält eine Liste der von den TextBuffer-Objekt, implementierten Schnittstellen <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Text-Puffer-Ereignisse in der legacy-API](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Enthält eine Liste der Schnittstellen, die für die Benachrichtigung über Ereignisse für Text-Puffer verwendet werden.  
  
 [Gewusst wie: Registrieren Sie sich für Text-Puffer-Ereignisse mit der legacy-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Beschreibt, wie Text Puffern von Ereignissen zu empfehlen.  
  
 [Verwenden Sie den TextManager zum Überwachen von globaler Einstellungen](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Erläutert, wie TextManager verwendet wird, für die Editor-Kernkomponenten globale Einstellung Informationen freigeben und Empfangen von Benachrichtigungen über Text-Manager-Ereignisse.  
  
 [Access TheText-Ansicht mit der legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Beschreibt die Textansicht-Rolle in der Kern-Editor, und listet die von implementierten Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.  
  
 [Anpassen von Fenstern des Code mit der legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Enthält Informationen wie ein Code-Fenster wird verwendet, um die Textansicht zu schließen, wird erläutert, wie der Codefenster-Manager verwendet ist, Ergänzungen zum Code-Fenster zu und ermöglicht die Benachrichtigung über neue Ansichten.  
  
 [Ändern der ansichtseinstellungen mithilfe der legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Enthält schrittweise Anleitungen zum Erzwingen der Einstellungen und erzwungene Einstellungen zu entfernen.  
  
 [Sprachdienste und die Kern-editor](../extensibility/language-services-and-the-core-editor.md)  
 Beschreibt die Instanziierung von einem Sprachdienst, Ergänzungen der Steuerelement-Code.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Exemplarische Vorgehensweise: Erstellen einer Kern-Editor und registrieren einen Dateityp-Editor-](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Enthält schrittweise Anweisungen zum Starten der Kern-Editor von verwaltetem Code.  
  
 [Dropdownleiste](../extensibility/drop-down-bar.md)  
 Beschreibt, wie die Dropdownleiste wird verwendet, im Code-Fenster, und beschreibt die Schnittstellen, die verwendet werden, wenn Sie eine Dropdownleiste implementieren.  
  
 [Verwenden von Textmarkierungen mit der legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Erklärt das Konzept von Textmarkierungen und wie sie in der Kern-Editor verwendet werden, und listet die Schnittstellen, die zum Zugreifen auf und Verwalten von Textmarkierungen verwendet werden.  
  
 [Gewusst wie: Hinzufügen von standard-Text-Marker](../extensibility/how-to-add-standard-text-markers.md)  
 Enthält schrittweise Anleitungen zum Erstellen ein textmarkers und So fügen Sie einen benutzerdefinierten Befehl in einem Kontextmenü Menüelemente hinzu.  
  
 [Gewusst wie: Erstellen von benutzerdefinierten Textmarkierungen](../extensibility/how-to-create-custom-text-markers.md)  
 Enthält schrittweise Anleitungen zum Erstellen ein benutzerdefinierten textmarkers und den Typ des Markers als Dienst bereitstellen.