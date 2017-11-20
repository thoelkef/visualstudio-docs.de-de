---
title: 'Vorgehensweise: Implementieren von geschachtelten Projekte | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 26456122d8b2cb0e89cfcda929cf68306959a31e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-nested-projects"></a>Vorgehensweise: Implementieren von geschachtelten Projekte
Bei der Erstellung ein geschachtelten Projekts vorhanden sind eine einige zusätzliche Schritte erforderlich, die implementiert werden müssen. Ein übergeordnetes Projekt werden einige der gleichen Aufgaben, die die Lösung für die geschachtelte (untergeordnete) Projekte hinzugefügt. Übergeordnetes Projekt ist ein Container für Projekte einer Projektmappe ähnelt. Es gibt insbesondere mehrere Ereignisse, die von der Lösung und von den übergeordneten Projekten zum Erstellen der Hierarchie von geschachtelten Projekten potenziert werden müssen. Diese Ereignisse werden in der folgende Vorgang zum Erstellen von geschachtelten Projekten beschrieben.  
  
### <a name="to-create-nested-projects"></a>Zum Erstellen von geschachtelten Projekten  
  
1.  Die integrierte Entwicklungsumgebung (IDE) lädt die Datei und der Starttyp Projektinformationen des übergeordneten Projekts durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> Schnittstelle. Das übergeordnete-Projekt wird erstellt und zur Projektmappe hinzugefügt.  
  
    > [!NOTE]
    >  An diesem Punkt ist es zu früh im Prozess für das übergeordnete Projekt des geschachtelten Projekts erstellt werden, da das übergeordnete Projekt erstellt werden muss, bevor untergeordneten Projekte erstellt werden können. Nach dieser Sequenz übergeordneten Projekts kann Einstellungen auf untergeordneten Projekte anwenden und untergeordneten Projekte können Informationen aus der übergeordneten Projekte abrufen, bei Bedarf. Diese Sequenz erfolgt, wenn er auf Clients, z. B. Quellcodeverwaltungssystem (SCC) und Projektmappen-Explorer erforderlich ist.  
  
     Übergeordnetes Projekt warten muss, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> Methode, um die von der IDE aufgerufen werden, bevor er seine geschachtelte (untergeordnete) oder Projekte erstellen kann.  
  
2.  Ruft die IDE `QueryInterface` auf dem übergeordneten Projekt für <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Wenn dieser Aufruf erfolgreich ist, ruft die IDE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> Methode des übergeordneten Elements, um alle geschachtelten Projekte für das übergeordnete-Projekt zu öffnen.  
  
3.  Die Aufrufe der übergeordneten Projekt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> Methode, um den Listener zu benachrichtigen, die Projekte geschachtelt sind im Begriff, die erstellt werden. SCC, lauscht z. B. mit diesen Ereignissen wissen, ob die Schritte bei der Erstellung von Projektmappen- und Projektdateien in der Reihenfolge ausgeführt werden. Wenn Sie die Schritte werden nicht in der richtigen Reihenfolge ausgeführt, kann die Projektmappe nicht mit quellcodeverwaltung ordnungsgemäß registriert werden.  
  
4.  Die Aufrufe der übergeordneten Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> Methode oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> -Methode für jede der untergeordneten Projekte.  
  
     Sie übergeben <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> auf die `AddVirtualProject` Methode, um anzugeben, dass der virtuelle (geschachtelte)-Projekt Projektfenster, aus dem Build ausgeschlossen hinzugefügt werden soll, quellcodeverwaltung, usw. hinzugefügt. `VSADDVPFLAGS`ermöglicht das Steuern der Sichtbarkeit des geschachtelten Projekts, und geben Sie an, welche Funktionen zugeordnet sind.  
  
     Wenn Sie ein bereits vorhandene untergeordnete Projekt erneut laden, die ein Projekt in der übergeordneten Projekts-Projektdatei, die Aufrufe der übergeordneten Projekt gespeicherte GUID hat `AddVirtualProjectEx`. Der einzige Unterschied zwischen `AddVirtualProject` und `AddVirtualProjectEX` handelt, `AddVirtualProjectEX` weist einen Parameter So aktivieren Sie das übergeordnete Projekt angeben einer pro Instanz `guidProjectID` für das untergeordnete Projekt aktivieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> -Funktion ordnungsgemäß.  
  
     Wenn keine GUID vorhanden verfügbar, ist z. B. Wenn Sie ein neues Projekt für die geschachtelte hinzufügen, die Projektmappe für das Projekt zum Zeitpunkt erstellt ist es an das übergeordnete Element hinzugefügt. Es liegt die Verantwortung des übergeordneten Projekts, Projekt-GUID in der Projektdatei beibehalten werden. Wenn Sie eine geschachtelte Projekt löschen, kann auch die GUID für das betreffende Projekt gelöscht werden.  
  
5.  Ruft die IDE die `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` -Methode für jedes Projekt untergeordnetes Element des übergeordneten Projekts.  
  
     Übergeordnetes Projekt implementieren muss `IVsParentProject` , wenn Sie Projekte schachteln wollen. Aber das übergeordnete Element nie Aufrufe Projekt `QueryInterface` für `IVsParentProject` auch wenn es sich um übergeordnete Projekte darunter hat. Die Lösung verarbeitet den Aufruf von `IVsParentProject` und, wenn er implementiert wurde, ruft `OpenChildren` geschachtelte Projekte erstellen. `AddVirtualProjectEX`wird immer aufgerufen, von `OpenChildren`. Es sollte nie vom übergeordneten Projekt auf die Hierarchie Erstellungsereignisse in Reihenfolge zu behalten aufgerufen werden.  
  
6.  Ruft die IDE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Methode für das untergeordnete Projekt.  
  
7.  Die Aufrufe der übergeordneten Projekt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> Methode, um den Listener zu benachrichtigen, dass die untergeordneten Projekte für das übergeordnete Element erstellt wurden.  
  
8.  Ruft die IDE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> Methode auf dem übergeordneten Projekt aus, nachdem alle untergeordneten Projekte geöffnet worden sein.  
  
     Wenn es nicht bereits vorhanden ist, erstellt der übergeordneten Projekt eine GUID für jeden geschachtelten Projekts durch Aufrufen `CoCreateGuid`.  
  
    > [!NOTE]
    >  `CoCreateGuid`eine COM-API, die aufgerufen wird, wenn eine GUID ist, erstellt werden. Weitere Informationen finden Sie unter `CoCreateGuid` und GUIDs in der MSDN Library.  
  
     Übergeordnetes Projekt speichert diese GUID in der Projektdatei das nächste Mal abgerufen werden soll, das sie in der IDE geöffnet ist. Finden Sie unter Schritt 4 für Weitere Informationen im Zusammenhang mit dem Aufruf der `AddVirtualProjectEX` zum Abrufen der `guidProjectID` für das untergeordnete Projekt.  
  
9. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Methode wird dann aufgerufen, für das übergeordnete Element-ID, die gemäß der Konvention in dem geschachtelte Projekt zu delegieren. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Ruft die Eigenschaften des Knotens, der ein Projekt schachtelt die gewünschten delegieren, wenn sie auf das übergeordnete Element aufgerufen wird.  
  
     Da über- und untergeordneten Projekte programmgesteuert instanziiert werden, können Sie Eigenschaften für geschachtelte Projekte zu diesem Zeitpunkt festlegen.  
  
    > [!NOTE]
    >  Nicht nur erhalten Sie die Kontextinformationen aus dem geschachtelten Projekt, aber Sie können auch Anfragen, verfügt das übergeordnete Projekt jeglichen Kontext für dieses Element durch Überprüfen <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>. Auf diese Weise können Sie zusätzliche dynamische Hilfe Attribute und bestimmte Optionen für einzelne geschachtelte Projekte hinzufügen.  
  
10. Die Hierarchie wird erstellt, für die Anzeige im Projektmappen-Explorer mit einem Aufruf von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> Methode.  
  
     Übergeben Sie die Hierarchie an der Umgebung über `GetNestedHierarchy` die Hierarchie für die Anzeige im Projektmappen-Explorer zu erstellen. Auf diese Weise weiß die Projektmappe an, dass das Projekt vorhanden ist und für die Erstellung von dem Build-Manager verwaltet werden kann oder Dateien in das Projekt unter quellcodeverwaltung eingesetzt werden können.  
  
11. Wenn alle geschachtelten Projekte für Projekt1 erstellt wurden, erhält die Kontrolle an die Lösung, und der Vorgang wird wiederholt für Projekt2.  
  
     Der gleiche Vorgang geschachtelte Projekte erstellen, tritt für ein untergeordnetes Projekt, das ein untergeordnetes Element verfügt. In diesem Fall BuildProject1, d. h. ein untergeordnetes Element des Projekt1, untergeordnete Projekte haben, würden sie nach BuildProject1 und vor Projekt2 erstellt werden. Der Prozess ist rekursiv und die Hierarchie von oben nach unten erstellt wird.  
  
     Wenn eine geschachtelte Projekt geschlossen, da die Lösung durch den Benutzer geschlossen oder das entsprechende Projekt selbst, die andere Methode auf `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, aufgerufen wird. Übergeordnetes Projekt dient als Wrapper für Aufrufe an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> Methode mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> Methoden Listener zur Lösung Ereignisse benachrichtigt, dass die geschachtelte Projekte geschlossen werden.  
  
 In den folgenden Themen behandeln mehrere andere Konzepte, die bei der Implementierung von geschachtelten Projekte berücksichtigen:  
  
 [Überlegungen für das Entladen und Neuladen von geschachtelten Projekten](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [Assistentenunterstützung für geschachtelte Projekte](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [Implementieren der Befehlsbehandlung für geschachtelte Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [Filtern des AddItem-Dialogfelds für geschachtelte Projekte](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Prüfliste: Erstellen neuen Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Kontextparameter](../../extensibility/internals/context-parameters.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)