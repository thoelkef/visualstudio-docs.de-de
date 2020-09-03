---
title: Im Kern-Editor | Microsoft-Dokumentation
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
ms.openlocfilehash: cf9bc42aec3aac5acc996487f99c7e1f29ca252c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203953"
---
# <a name="inside-the-core-editor"></a>Im Core-Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kern-Editor ist eine Reihe von verschiedenen Komponenten, mit denen Sie Textinformationen ändern und Abfragen können. Wenn Sie den Kern-Editor mithilfe der Legacy-API angepasst haben, können Sie diese Anpassungen weiterhin verwenden, die über Editor Adapter weitergeleitet werden. Es wird jedoch empfohlen, dass Sie Ihre Anpassungen an die neue Editor-API anpassen.  
  
 Die folgenden Bereiche sind einige wichtige Aspekte des Kern-Editors:  
  
- Text Puffer  
  
- Text Ansicht  
  
- Codefenster  
  
- Text Marker  
  
- Text-Manager  
  
- Integration in Sprachdienste  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Instanziieren des Core-Editors mit der Legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Enthält Schritt-für-Schritt-Anleitungen zum <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Erstellen einer Instanz des Core-Editors.  
  
 [Zugriff auf den Textpuffer mit der Legacy-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Erläutert die Rolle des Text Puffers im Kern-Editor, erläutert die zugeordneten Systeme, die für den Zugriff auf den Puffer verwendet werden, und stellt eine Liste der Schnittstellen bereit, die vom Text Puffer Objekt implementiert werden <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 [Textpufferereignisse in der Legacy-API](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Stellt eine Liste der Schnittstellen bereit, die für die Benachrichtigung von Text Puffer Ereignissen verwendet werden.  
  
 [Vorgehensweise: Registrieren für Textpufferereignisse mit der Legacy-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Beschreibt, wie Text Puffer Ereignisse zu empfehlen sind.  
  
 [Überwachen der globalen Einstellungen mit dem Text-Manager](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Erläutert, wie der Text-Manager verwendet wird, um globale Einstellungs Informationen mit den Kern-Editor-Komponenten gemeinsam zu nutzen und um Benachrichtigungen von Text-Manager-Ereignissen zu empfangen.  
  
 [Zugriff auf die Textansicht mit der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Beschreibt die Rolle der Textansicht im Kern-Editor und listet die Schnittstellen auf, die vom-Objekt implementiert werden <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 [Anpassen von Codefenstern mit der Legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Stellt Informationen dazu bereit, wie ein Code Fenster zum Einschließen der Textansicht verwendet wird, erläutert, wie der Code Fenster-Manager verwendet wird, um Dekorationen für das Code Fenster bereitzustellen, und stellt Benachrichtigungen zu neuen Ansichten bereit.  
  
 [Ändern der Ansichtseinstellungen mit der Legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Enthält Schritt-für-Schritt-Anleitungen zum Erzwingen von Ansichts Einstellungen und zum Entfernen erzwungener Einstellungen.  
  
 [Sprachdienste und der Core-Editor](../extensibility/language-services-and-the-core-editor.md)  
 Beschreibt die Instanziierung eines sprach Dienstanbieter zum Steuern von Code Dekorationen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Exemplarische Vorgehensweise: Erstellen eines Core-Editors und Registrieren eines Editordateityps](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Enthält Schritt-für-Schritt-Anweisungen zum Starten des Kern-Editors aus verwaltetem Code.  
  
 [Dropdownleiste](../extensibility/drop-down-bar.md)  
 Erläutert, wie die Dropdown Leiste im Code Fenster verwendet wird, und beschreibt die Schnittstellen, die beim Implementieren einer Dropdown Leiste verwendet werden.  
  
 [Verwenden von Textmarkierungen mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Erläutert das Konzept von Text Markern und deren Verwendung im Kern-Editor und listet die Schnittstellen auf, die für den Zugriff auf und die Verwaltung von Text Markern verwendet werden.  
  
 [Vorgehensweise: Hinzufügen von Standardtextmarkierungen](../extensibility/how-to-add-standard-text-markers.md)  
 Enthält Schritt-für-Schritt-Anleitungen zum Erstellen eines Text Markers und zum Hinzufügen eines benutzerdefinierten Befehls zu einem Kontextmenü.  
  
 [Vorgehensweise: Erstellen von benutzerdefinierten Diagrammen](../extensibility/how-to-create-custom-text-markers.md)  
 Enthält Schritt-für-Schritt-Anleitungen zum Erstellen eines benutzerdefinierten Text Markers und zum Bereitstellen des Markertyps als Dienst.
