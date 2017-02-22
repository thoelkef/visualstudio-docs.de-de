---
title: "Befehl-Verf&#252;gbarkeit | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehle, Kontext"
  - "Menüelemente, die Sichtbarkeit Kontexte"
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 34
caps.handback.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
---
# Befehl-Verf&#252;gbarkeit
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Visual Studio\-Kontext wird bestimmt, welche Befehle verfügbar sind. Der Kontext kann je nach dem aktuellen Projekt, den aktuellen Editor, die VSPackages, die geladen werden und andere Aspekte der integrierten Entwicklungsumgebung \(IDE\) ändern.  
  
## Befehl Kontexte  
 Der folgende Befehl Kontexte sind die am häufigsten verwendeten.  
  
-   **IDE** Befehle von der IDE immer verfügbar sind.  
  
-   **VSPackage** VSPackages können definieren, wenn Befehle angezeigt oder ausgeblendet werden.  
  
-   **Projekt** Befehle werden nur für das aktuell ausgewählte Projekt angezeigt.  
  
-   **Editor** nur einen Editor gleichzeitig aktiv sein kann. Befehle im aktiven\-Editor zur Verfügung. Ein Editor arbeitet eng mit einem Language\-Dienst. Der Sprachdienst muss die Befehle im Kontext des zugehörigen Editors verarbeiten.  
  
-   **Dateityp** Redakteur kann mehr als eine Art von Datei laden. Die verfügbaren Befehle können je nach den Dateityp ändern.  
  
-   **Aktive Fenster** die letzte aktive Fenster wird den Benutzerkontext für die Benutzeroberfläche \(UI\) für Tastenkombinationen. Ein Fenster mit einer Schlüssel\-Binding\-Tabelle, die den internen Webbrowser ähnelt jedoch festlegen auch den Benutzeroberflächenkontext. Für Registerkarten Dokumentfenster wie der HTML\-Editor hat jeder Registerkarte einen anderen Befehl GUID. Nachdem ein Toolfenster registriert wurde, kann jederzeit auf die **Ansicht** Menü.  
  
-   **Benutzeroberflächenkontext** Benutzeroberflächen\-Kontexte werden identifiziert, indem die Werte der <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> Klasse, zum Beispiel <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding> wenn die Projektmappe erstellt wird, oder <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging> Wenn der Debugger aktiv ist. Mehrere UI\-Kontexte können gleichzeitig aktiv sein.  
  
## Definieren von benutzerdefinierten Kontext\-GUIDs  
 Wenn einen entsprechenden Befehl\-Kontext, den GUID noch nicht definiert ist, können Sie in Ihr VSPackage definieren und dann auf aktiv oder inaktiv nach Bedarf, um die Sichtbarkeit der Befehle zu steuern.  
  
1.  Registrieren Sie die Kontext\-GUIDs durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> Methode.  
  
2.  Erhalten Sie den Status eines Kontexts GUID durch einen Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode.  
  
3.  Aktivieren und deaktivieren Kontext\-GUIDs, durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> Methode.  
  
    > [!CAUTION]
    >  Stellen Sie sicher, dass Ihr VSPackage alle vorhandenen Kontext GUIDs nicht beeinträchtigt, da andere VSPackages abhängen kann.  
  
## Siehe auch  
 [Auswahl Kontextobjekte](../../extensibility/internals/selection-context-objects.md)   
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)