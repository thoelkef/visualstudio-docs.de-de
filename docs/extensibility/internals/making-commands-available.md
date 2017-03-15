---
title: "Befehle stellen zur Verf&#252;gung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Menüs [Visual Studio SDK] Befehle"
  - "Bewährte Methoden, die Menü-und Symbolleistenbefehle"
  - "Bewährte Methoden für Symbolleisten [Visual Studio]"
  - "Menübefehle, bewährte Methoden"
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 35
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 35
---
# Befehle stellen zur Verf&#252;gung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn mehrere VSPackages zu Visual Studio hinzugefügt werden, kann die Benutzeroberfläche \(UI\) mit den Befehlen Akzente werden. Sie können das Paket, um dieses Problem wie folgt zu verringern Programmieren:  
  
-   Die Anwendung das Paket, damit sie geladen wird, nur, wenn ein Benutzer ist erforderlich.  
  
-   Programmieren Sie das Paket, damit die Befehle werden nur angezeigt, wenn diese im Kontext des aktuellen Zustands der integrierten Entwicklungsumgebung \(IDE\) werden möglicherweise benötigt.  
  
## Verzögertes Laden  
 Das übliche Verfahren zum Aktivieren ist des VSPackage so entwerfen, dass die Befehle in der Benutzeroberfläche angezeigt werden, aber das Paket selbst nicht geladen wird, bis ein Benutzer einen der Befehle das verzögerte Laden. Erstellen Sie dazu in der VSCT\-Datei Befehlen, die keine Befehlsflags verfügen.  
  
 Das folgende Beispiel zeigt die Definition eines Menübefehls aus einer VSCT\-Datei. Dies ist der Befehl, der von der Visual Studio\-Paket\-Vorlage generiert bei der **Menübefehl** in der Vorlage ausgewählt ist.  
  
 [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
 Im Beispiel wenn die übergeordnete Gruppe `MyMenuGroup`, ist ein untergeordnetes Element des ein Menü der obersten Ebene, wie z. B. der **Tools** im Menü der Befehl wird auf das Menü angezeigt werden, aber das Paket, das der Befehl ausgeführt wird, werden erst dann geladen von einem Benutzer mit dem Befehl geklickt wird. Jedoch durch die Programmierung des Befehls zum Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> \-Schnittstelle, damit Sie das Paket geladen werden, wenn das Menü, das den Befehl enthält zunächst erweitert wird.  
  
 Beachten Sie, dass verzögertes Laden auch verlangsamten verbessern kann.  
  
## Aktuellen Kontext und die Sichtbarkeit von Befehlen  
 Sie können Programmieren VSPackage\-Befehle werden ein\- oder ausgeblendet, je nach den aktuellen Zustand des VSPackage Daten oder die Aktionen, die derzeit relevant sind. Sie können das VSPackage zum Festlegen des Status der darin enthaltenen Befehle in der Regel mithilfe einer Implementierung von der <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> Methode aus der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> \-Schnittstelle, aber dies erfordert das VSPackage geladen werden, bevor der Code ausgeführt werden kann. Stattdessen empfehlen wir, die IDE, um die Sichtbarkeit der Befehle zu verwalten, ohne das Laden des Pakets zu aktivieren. Ordnen Sie dazu in der VSCT\-Datei ein oder mehrere spezielle Benutzeroberfläche Kontexte Befehle. Diese Benutzeroberflächen\-Kontexte werden durch eine GUID als bekannt identifiziert eine *Befehlskontext GUID*.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] überwacht die Änderungen, die durch Benutzeraktionen, wie z. B. ein Projekt geladen oder Erstellen von bearbeiten möchten. Wenn Änderungen auftreten, wird die Darstellung der IDE automatisch geändert. Die folgende Tabelle zeigt die vier wichtigsten Kontexte der IDE ändern, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] überwacht.  
  
|Typ des Kontexts|Beschreibung|  
|----------------------|------------------|  
|Aktive Projekttyp|Bei den meisten Projekttypen dies `GUID` Wert ist identisch mit der GUID des VSPackage, das das Projekt implementiert. Allerdings [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte verwenden den Projekttyp `GUID` als Wert.|  
|Aktives Fenster|In der Regel ist dies die letzte aktive Fenster, das den aktuellen Kontext der Benutzeroberfläche für Tastenbelegungen herstellt. Allerdings auch ein Toolfenster ist möglicherweise mit einer Tastenkombination\-Tabelle, die den internen Webbrowser ähnelt. Für Registerkarten Dokumentfenster wie der HTML\-Editor, jede Registerkarte verfügt über einen anderen Befehlskontext `GUID`.|  
|Aktive Sprachdienst|Die Language\-Dienst, der der Datei zugeordnet ist, die derzeit in einem Text\-Editor angezeigt wird.|  
|Aktives Toolfenster|Ein Fenster, das geöffnet ist und den Fokus hat.|  
  
 Eine fünfte wichtigen Kontextbereich ist der Zustand der Benutzeroberfläche der IDE. Benutzeroberflächen\-Kontexte werden vom aktiven Befehlskontext identifiziert `GUID`s, wie folgt:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Dragging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_FullScreenMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_DesignMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_NoSolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_CodeWindow>  
  
 Diese GUIDs werden als aktiv oder inaktiv ist, je nach den aktuellen Zustand der IDE markiert. Mehrere UI\-Kontexte können gleichzeitig aktiv sein.  
  
### Ausblenden und Anzeigen von Befehlen, die anhand des Kontexts  
 Sie können ein\- oder Ausblenden von einem Paket\-Befehl in der IDE ohne das Laden des Pakets selbst. Definieren Sie hierzu den Befehl in der VSCT\-Datei des Pakets die `DefaultDisabled`, `DefaultInvisible`, und `DynamicVisibility` Befehl Flags und Hinzufügen von einem oder mehreren [VisibilityItem](../../extensibility/visibilityitem-element.md) Elemente, die die [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) Abschnitt. Wenn eine angegebene Kontext `GUID` wird aktiv ist, wird der Befehl ohne Laden des Pakets angezeigt.  
  
### Benutzerdefinierten Kontext\-GUIDs  
 Wenn einen entsprechenden Befehl\-Kontext, den GUID noch nicht definiert ist, können Sie in Ihr VSPackage definieren und dann auf aktiv oder inaktiv nach Bedarf, um die Sichtbarkeit der Befehle zu steuern. Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Service:  
  
-   Registrieren Sie die Kontext\-GUIDs \(durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> Methode\).  
  
-   Abrufen des Status eines Kontexts `GUID` \(durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode\).  
  
-   Aktivieren von Kontext `GUID`s ein\- und ausschalten \(durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> Methode\).  
  
    > [!CAUTION]
    >  Stellen Sie sicher, dass Ihr VSPackage den Status der alle vorhandenen Kontext GUID nicht beeinträchtigt, da andere VSPackages abhängen kann.  
  
## Beispiel  
 Das folgende Beispiel für einen VSPackage\-Befehl zeigt die dynamische Sichtbarkeit eines Befehls, der vom Befehl Kontexte verwaltet wird, ohne dass das VSPackage geladen.  
  
 Der Befehl wird festgelegt, aktiviert und angezeigt, wenn eine Projektmappe vorhanden ist. d. h. jedes Mal, wenn eine der folgenden Befehlskontext GUIDs aktiv ist:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 Im Beispiel beachten Sie, dass jede Befehlsflag eine Separate [Befehlsflag](../../extensibility/command-flag-element.md) Element.  
  
 [!CODE [DynamicVisibility#01](DynamicVisibility#01)]  
  
 Beachten Sie auch, mit dem alle UI\-Kontext in einer separaten muss `VisibilityItem` \-Element wie folgt.  
  
 [!CODE [DynamicVisibility#02](DynamicVisibility#02)]  
  
## Siehe auch  
 [MenuCommand\- und OleMenuCommand\-Objekte](../../misc/menucommands-vs-olemenucommands.md)   
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Dynamisches Hinzufügen von Menüelementen](../../extensibility/dynamically-adding-menu-items.md)