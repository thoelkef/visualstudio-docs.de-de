---
title: "Gewusst wie: Implementieren von geschachtelten Projekte | Microsoft Docs"
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
  - "Implementieren von geschachtelten-Projekten"
  - "Projekte [Visual Studio SDK] schachteln"
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Implementieren von geschachtelten Projekte
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn Sie einen geschachtelten Projekttyp erstellen, gibt es einige zusätzliche Schritte, die implementiert werden müssen.  Ein übergeordnetes Projekt übernimmt ein einiger der gleichen Projektmappe, die die Verantwortung für die geschachtelten \(untergeordnete\) Projekte aufweist.  Das Projekt ist ein Container für Elemente, die Projekte in einer Projektmappe ähneln.  Insbesondere gibt es einige Ereignisse, die von der Projektmappe enthaltenen Projekte und von den Elementen ausgelöst werden müssen, die Hierarchie geschachtelter Projekten zu erstellen.  Diese Ereignisse werden im folgenden Verfahren zum Erstellen von geschachtelten Projekten beschrieben.  
  
### Um geschachtelte Projekte erstellen  
  
1.  Die integrierte Entwicklungsumgebung \(IDE\) lädt die Elemente und Projektdatei\- Informationen zum Starten des Projekts, indem sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>\-Schnittstelle aufruft.  Das übergeordnete Projekt der Projektmappe wird erstellt und dem Projektmappen\-Explorer hinzugefügt.  
  
    > [!NOTE]
    >  An diesem Punkt ist es zu einem frühen Zeitpunkt im Prozess, dessen Elemente das Projekt geschachtelte Projekt erstellt, da das übergeordnete Projekt erstellt werden muss, bevor die untergeordneten Projekte erstellt werden können.  Nach dieser Sequenz kann das übergeordnete Projekt Einstellungen auf untergeordnete Projekte anwenden und die untergeordneten Projekte können Informationen aus den Elementen Projekten nach Bedarf abrufen.  Diese Sequenz ist, wenn sie von Clients wie die Quellcodeverwaltung \(SCC\) und der Projektmappen\-Explorer nicht erforderlich ist.  
  
     Das übergeordnete Projekt muss von der IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>\-Methode aufgerufen werden, auf die gewartet werden soll, bevor sein, geschachtelte \(untergeordnete\) Projekt oder Projekte erstellen kann.  
  
2.  Die IDE ruft `QueryInterface` des übergeordneten Projekts für <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>an.  Wenn dieser Aufruf erfolgreich ausgeführt wird, wird die IDE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A>\-Methode des übergeordneten Elements an, um alle geschachtelten Projekte für das übergeordnete Projekt zu öffnen.  
  
3.  Das übergeordnete Projekt wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A>\-Methode auf, um einen Listener zu benachrichtigen, dass geschachtelte Projekte im Begriff sind erstellt werden.  SCC auf diese Ereignisse überwacht, z. B. zu wissen, wenn die Schritte im Projektmappen\- und des Builds Projekt in der Reihenfolge auftreten.  Wenn die Testschritte gestört auftreten, wird die Projektmappe nicht mit Quellcodeverwaltung ordnungsgemäß registriert werden.  
  
4.  Das übergeordnete Projekt wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A>\-Methode oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A>\-Methode für jeden seiner untergeordneten Projekte an.  
  
     Führen Sie zur <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS>`AddVirtualProject`\-Methode usw. anzugeben, dass das virtuelle \(geschachtelte\) Projekt im Fenster Projekt hinzugefügt werden soll, vom Build ausgeschlossen wurde der Quellcodeverwaltung hinzugefügt.  `VSADDVPFLAGS` können Sie die Sichtbarkeit des geschachtelten Projekts gesteuert und angeben, welche Funktionen zugeordnet ist.  
  
     Wenn Sie ein bereits vorhandener untergeordnetes Projekt erneut laden, das eine Projekt\-GUID verfügt, die in der übergeordneten Projektdatei des Projekts gespeichert wird, ruft das übergeordnete Projekt `AddVirtualProjectEx`an.  Der einzige Unterschied zwischen `AddVirtualProject` und `AddVirtualProjectEX` besteht darin, dass `AddVirtualProjectEX` einen Parameter verfügt, sodass die übergeordneten Projekts zu ermöglichen, eine pro Instanz `guidProjectID` anzugeben, dass das untergeordnete Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> aktiviert, um ordnungsgemäß zu funktionieren.  
  
     Wenn kein GUID gibt an, wie verfügbar, wenn Sie ein neues geschachteltes Projekt hinzufügen, erstellt das Projekt für die Projektmappe ein, wenn sie zum übergeordneten Element hinzugefügt wird.  Es liegt in der Verantwortung des übergeordneten Projekts, diese Projekt\-GUID in der Projektdatei beizubehalten.  Wenn Sie ein geschachteltes Projekt löschen, kann die GUID für dieses Projekt auch gelöscht werden.  
  
5.  Die IDE ruft die `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren`\-Methode für jedes untergeordnete Projekt des übergeordneten Projekts an.  
  
     Das übergeordnete Projekt muss `IVsParentProject` implementieren, wenn Sie Projekte schachteln möchten.  Aber das übergeordnete Projekt wird nie `QueryInterface` für `IVsParentProject` an, auch wenn diese Elemente Projekte darunter verfügt.  Die Projektmappe behandelt den Aufruf von `IVsParentProject` und bei der Implementierung ruft `OpenChildren` auf, um die geschachtelten Projekte zu erstellen.  `AddVirtualProjectEX` wird immer vom `OpenChildren`aufgerufen.  Es sollte nie durch das übergeordnete Projekt aufgerufen werden, die Hierarchien von Builds in der Reihenfolge beizubehalten.  
  
6.  Die IDE ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>\-Methode für das untergeordnete Projekt an.  
  
7.  Das übergeordnete Projekt wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A>\-Methode auf, um einen Listener zu benachrichtigen, dass die untergeordneten Projekte für das übergeordnete Element erstellt wurden.  
  
8.  Die IDE ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A>\-Methode auf dem übergeordneten Projekts, nachdem alle an das untergeordnete Projekte geöffnet wurden.  
  
     Wenn sie nicht bereits vorhanden ist, erstellt das übergeordnete Projekt eine GUID für jedes geschachtelte Projekt, indem `CoCreateGuid`aufruft.  
  
    > [!NOTE]
    >  `CoCreateGuid` ist mit der Bezeichnung COM\-APIs, wenn eine GUID erstellt werden soll.  Weitere Informationen finden Sie unter `CoCreateGuid` und GUID in der MSDN Library.  
  
     Das Elemente in seiner GUID dieses speichert Projekt das nächste Mal abgerufen werden sollen, die Projektdatei im IDE geöffnet ist.  Siehe Schritt 4 für weitere Informationen bezüglich der Aufruf von `AddVirtualProjectEX` , um `guidProjectID` für das untergeordnete Projekt abzurufen.  
  
9. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>\-Methode wird dann für das übergeordnete ItemID aufgerufen, das vereinbarungsgemäß Sie dem geschachtelten Projekt delegieren.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> ruft die Eigenschaften des Knotens ab, der ein Projekt schachtelt, in dem Sie delegieren möchten, wenn es sich um dem übergeordneten Element aufgerufen wird.  
  
     Da übergeordnete und untergeordnete Projekte programmgesteuert instanziiert werden, können Sie Eigenschaften für geschachtelte Projekten an diesem Punkt festlegen.  
  
    > [!NOTE]
    >  Rufen Sie nicht nur die Kontextinformationen vom geschachtelten Projekt. Sie können jedoch auch fragen, ob das übergeordnete Projekt einen Kontext für dieses Element verfügt, indem <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>überprüft.  Auf diese Weise können Sie zusätzliche Menüoptionen und die dynamische Hilfe Attribute hinzufügen, die geschachtelten einzelnen Projekte spezifisch sind.  
  
10. Die Hierarchie wird für die Anzeige im Projektmappen\-Explorer mit einem Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>\-Methode erstellt.  
  
     Sie führen die Hierarchie der Umgebung von `GetNestedHierarchy` , um die Hierarchie für die Anzeige im Projektmappen\-Explorer zu erstellen.  Auf diese Weise wird die Lösung, weiß, dass das Projekt zum Erstellen der Build\-Manager vorhanden und verwaltet werden kann, oder es kann Dateien des Projekts ermöglichen, unter Quellcodeverwaltung gestellt werden.  
  
11. Wenn alle geschachtelten Project1 für Projekte erstellt wurden, wird die Steuerung wieder an die Projektmappe übergeben, und der Prozess wird für Project2 wiederholt.  
  
     Dieser gleichen Prozess zum Erstellen von geschachtelten Projekten tritt für ein untergeordnetes Projekt, das ein untergeordnetes Element verfügt.  In diesem Fall wenn BuildProject1, das ein untergeordnetes Element von Project1 ist, untergeordnete Projekte hatte, werden sie vor und nach BuildProject1 Project2 erstellt.  Der Prozess ist rekursiv und die Hierarchie wird von oben nach unten erstellt.  
  
     Wenn ein geschachteltes Projekt geschlossen wird, da der Benutzer die Projektmappe oder das bestimmtes Projekt selbst wurde, wird die andere Methode für `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, aufgerufen.  Die Elemente umbruchs Projekt zur <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A>\-Methode mit dem von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> und den <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A>\-Methode, um Projektmappen Listener Ereignisse zu benachrichtigen, dass die geschachtelten Projekte geschlossen werden.  
  
 Im folgenden Thema abkommen mit einigen anderen Konzepten, geschachtelte beachten sollten, wenn Sie Projekte ausführen:  
  
 [Hinweise für entfernen und erneutes Laden geschachtelten Projekte](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [Unterstützung für geschachtelte Projekte\-Assistenten](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [Implementieren der Befehl für die geschachtelte Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [Das Dialogfeld AddItem Filtern für geschachtelte Projekte](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## Siehe auch  
 [Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrieren von Projekt\- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Prüfliste: Erstellen von neuen Typen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Kontextparameter](../../extensibility/internals/context-parameters.md)   
 [Assistenten \(. VSZ\)\-Datei](../../extensibility/internals/wizard-dot-vsz-file.md)