---
title: "In der Core-Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Core-editor"
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# In der Core-Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kern des Editors ist ein Satz von mehreren Komponenten, die Textinformationen ändern und abfragen können.  Wenn Sie den Kern des Editors angepasst haben, indem Sie das Legacy APIs verwenden, fahren Sie möglicherweise weiterhin diese Anpassungen zu verwenden, die von Editor Netzwerkkarten weitergeleitet werden.  Es wird jedoch empfohlen, dass Sie die Anpassungen dem neuen Editor API anpassen.  
  
 Die folgenden Bereiche sind einige wichtige Aspekte des zentralen editors:  
  
-   Textpuffer  
  
-   Textansicht  
  
-   Codefenster  
  
-   Textmarkierungen  
  
-   Text Manager  
  
-   Integration mit Sprachendiensten  
  
## In diesem Abschnitt  
 [Instanziieren die Core\-Editor mithilfe der Legacy\-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Enthält schrittweise Anweisungen zum Bereitstellen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> verwendet wird, um eine Instanz des zentralen editors zu erstellen.  
  
 [Zugriff auf den Textpuffer mit der Legacy\-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Erläutert die Rolle des Textpuffers im Kern des Editors, werden die entsprechenden Systeme, die verwendet werden, um den Puffer zuzugreifen und stellt eine Liste von Schnittstellen bereit, die im Textpuffer, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>implementiert werden.  
  
 [Text\-Puffer\-Ereignisse in der Legacy\-API](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Stellt eine Liste der Schnittstellen bereit, die für eine Benachrichtigung über Textpuffer Ereignissen verwendet werden.  
  
 [Gewusst wie: Registrieren für Ereignisse Puffer mit der Legacy\-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Beschreibt, wie Ereignisse Textpuffer Logs.  
  
 [Verwenden die Text\-Manager zum Überwachen von globaler Einstellungen](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Erläutert, wie der Text Manager verwendet wird, um globale Einstellungen von Informationen mit den Kern des Editors nutzen, und wie die Benachrichtigung von Ereignissen empfängt Manager Text.  
  
 [Zugreifen auf Dietext Ansicht mithilfe der Legacy\-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Beschreibt die Rolle der Textansicht im Kern des Editors und führt die Schnittstellen aufgeführt, die vom <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>\-Objekt implementiert werden.  
  
 [Anpassen von Code Windows mit der Legacy\-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Enthält Informationen darüber, wie ein Codefenster verwendet wird, um die Textansicht einzuschließen, erläutert, wie der Code fenster\-manager verwendet wird, um Dekorationen für das Codefenster bereitzustellen, Benachrichtigungen bereitstellt und neuer Ansichten bereit.  
  
 [Ändern die Ansicht mit der Legacy\-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Enthält schrittweise Anweisungen zum Bereitstellen von Einstellungen anzeigen und erzwingt die Verwendung erzwungene Einstellungen entfernt.  
  
 [Language Services und die Core\-Editor](../extensibility/language-services-and-the-core-editor.md)  
 Beschreibt die Instanziierung des Sprachdiensts den Steuerungscode dekorationen.  
  
## Verwandte Abschnitte  
 [Exemplarische Vorgehensweise: Erstellen eines Kern\-Editors, und registrieren einen Dateityp\-Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Enthält schrittweise Anweisungen zum Bereitstellen von den Kern des Editors aus verwaltetem Code beginnt.  
  
 [Dropdown\-Leiste](../extensibility/drop-down-bar.md)  
 Erläutert, wie die Dropdownliste Anzeige im Codefenster verwendet wird, und beschreibt die Schnittstellen, die verwendet werden, wenn Sie eine Dropdownliste Leiste implementieren.  
  
 [Verwenden von Text Marker mit der Legacy\-API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Erklärt das Konzept von Textmarkierungen und wie sie im Kern des Editors verwendet werden, und führt die Schnittstellen aufgeführt, die verwendet werden, um Textmarkierungen zuzugreifen und zu verwalten.  
  
 [Gewusst wie: Hinzufügen von Standard\-Text\-Marker](../extensibility/how-to-add-standard-text-markers.md)  
 Stellt schrittweise Anweisungen zum Erstellen einer Textmarkierung erstellt wird und wie ein benutzerdefinierter Befehl in einem Kontextmenü hinzugefügt wird.  
  
 [Gewusst wie: Erstellen von benutzerdefinierten Text Marken](../extensibility/how-to-create-custom-text-markers.md)  
 Stellt schrittweise Anweisungen zum Erstellen einer benutzerdefinierten Textmarkierung erstellt wird und wie der Markierung des Arrays als Dienst bereitstellt.