---
title: 'Vorgehensweise: Implementieren von geschachtelten Projekten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3892d02e39eb29039f815df5ff9174ce39415a81
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173575"
---
# <a name="how-to-implement-nested-projects"></a>Vorgehensweise: Implementieren von geschachtelten Projekten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bei der Erstellung ein geschachtelten Projekts-Typs vorhanden sind eine zusätzliche Schritte, die implementiert werden müssen. Ein übergeordnetes Projekt nimmt Teil die gleichen Aufgaben, die die Lösung für die geschachtelten (untergeordnet) Projekte. Das übergeordnete Projekt ist ein Container für Projekte, die ähnlich wie eine Lösung. Insbesondere stehen mehrere Ereignisse, die von der Lösung und von der übergeordneten zu erstellenden Projekte an die Hierarchie von geschachtelten Projekten ausgelöst werden müssen. Diese Ereignisse werden in den folgenden Prozess zum Erstellen von geschachtelten Projekten beschrieben.  
  
### <a name="to-create-nested-projects"></a>Zum Erstellen von geschachtelten Projekten  
  
1.  Die integrierte Entwicklungsumgebung (IDE) lädt des übergeordneten Projekts Project-Datei und Start-Informationen durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> Schnittstelle. Das übergeordnete Projekt wird erstellt und zur Projektmappe hinzugefügt.  
  
    > [!NOTE]
    >  An diesem Punkt ist es zu früh im Prozess für das übergeordnete Projekt, das geschachtelte Projekt erstellt werden, da das übergeordnete Projekt erstellt werden muss, bevor die untergeordneten Projekte erstellt werden können. Das übergeordnete Projekt Einstellungen für die untergeordneten Projekte anwenden und untergeordneten Projekte können Informationen aus der übergeordneten Projekten abrufen, bei Bedarf, nach der Sequenz. Diese Sequenz ist, wenn es von Clients wie z.B. quellcodeverwaltung (SCC) und der Projektmappen-Explorer auf benötigt wird.  
  
     Das übergeordnete Projekt warten muss, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> Methode, um die von der IDE aufgerufen werden, bevor sie die geschachtelten (untergeordnet) Projekte erstellen kann.  
  
2.  Die IDE-Aufrufe `QueryInterface` auf das übergeordnete Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Wenn dieser Aufruf erfolgreich ist, die IDE-Aufrufe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> -Methode der das übergeordnete Element, um alle geschachtelten Projekte für das übergeordnete Projekt zu öffnen.  
  
3.  Das übergeordnete projektaufrufe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> Methode, um Listener zu benachrichtigen, die Projekte geschachtelt sind im Begriff, die erstellt werden. SCC, z. B. überwacht für diese Ereignisse zu wissen, ob die Schritte im Prozess Projektmappen- und Projektdateien in der Reihenfolge auftreten. Wenn Sie die Schritte werden außerhalb der Reihenfolge ausgeführt, kann die Lösung nicht mit quellcodeverwaltung ordnungsgemäß registriert werden.  
  
4.  Das übergeordnete projektaufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> Methode oder der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> -Methode für jedes der zugehörigen untergeordneten Projekte.  
  
     Übergeben Sie <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> auf die `AddVirtualProject` Methode, um anzugeben, dass das Projektfenster, aus dem Build ausgeschlossen (geschachtelte) virtuelle Projekt hinzugefügt werden soll, quellcodeverwaltung usw. hinzugefügt. `VSADDVPFLAGS` ermöglicht Ihnen das Steuern der Sichtbarkeit des geschachtelten Projekts, und geben Sie an, welche Funktion zugeordnet ist.  
  
     Wenn Sie ein bereits vorhandene untergeordnete Projekt erneut laden, die ein Projekt in der Projektdatei die Aufrufe der übergeordneten Projekt des übergeordneten Projekts gespeicherte GUID hat `AddVirtualProjectEx`. Der einzige Unterschied zwischen `AddVirtualProject` und `AddVirtualProjectEX` ist, die `AddVirtualProjectEX` verfügt über einen Parameter So aktivieren Sie das übergeordnete Projekt an einen pro Instanz `guidProjectID` für das untergeordnete Projekt aktivieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> -Funktion richtig.  
  
     Wenn keine GUID vorhanden verfügbar, ist z. B. Wenn Sie ein neues geschachtelte Projekt hinzufügen, erstellt die Lösung für das Projekt zum Zeitpunkt ist es das übergeordnete Element hinzugefügt. Es ist die Verantwortung für das übergeordnete Projekt, Projekt-GUID in der Projektdatei beibehalten werden. Wenn Sie eine geschachtelte Projekt löschen, kann auch die GUID für das Projekt gelöscht werden.  
  
5.  Die IDE-Aufrufe der `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` Methode für jedes untergeordnete Projekt des übergeordneten Projekts.  
  
     Das übergeordnete Projekt implementieren muss `IVsParentProject` Wenn Projekte geschachtelt werden sollen. Aber das übergeordnete Element, das niemals Aufrufe Projekt `QueryInterface` für `IVsParentProject` auch wenn es sich um übergeordnete Projekte darunter hat. In der Lösung wird den Aufruf von `IVsParentProject` und, wenn sie implementiert ist, ruft `OpenChildren` um geschachtelte Projekte zu erstellen. `AddVirtualProjectEX` wird immer aufgerufen, von `OpenChildren`. Es sollte nie durch das übergeordnete Projekt zu der Hierarchie Ereignisse der diensterstellung in der Reihenfolge aufgerufen werden.  
  
6.  Die IDE-Aufrufe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> Methode für das untergeordnete Projekt.  
  
7.  Das übergeordnete projektaufrufe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> Methode, um Listener zu benachrichtigen, dass die untergeordneten Projekte für das übergeordnete Element erstellt wurden.  
  
8.  Die IDE-Aufrufe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> Methode für das übergeordnete Projekt, nachdem alle untergeordneten Projekte geöffnet wurden.  
  
     Wenn es nicht bereits vorhanden ist, erstellt das übergeordnete Projekt eine GUID für jede geschachtelte Projekt durch den Aufruf `CoCreateGuid`.  
  
    > [!NOTE]
    >  `CoCreateGuid` eine COM-API wird aufgerufen werden, wenn eine GUID ist, erstellt werden. Weitere Informationen finden Sie unter `CoCreateGuid` und GUIDs in der MSDN Library.  
  
     Das übergeordnete Projekt speichert diese GUID in der Projektdatei das nächste Mal abgerufen werden soll, das sie in der IDE geöffnet ist. Finden Sie unter Schritt 4 für Weitere Informationen über das Aufrufen der `AddVirtualProjectEX` zum Abrufen der `guidProjectID` für das untergeordnete Projekt.  
  
9. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Methode wird dann aufgerufen, für das übergeordnete Element-ID die gemäß der Konvention in dem geschachtelte Projekt delegieren. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Ruft die Eigenschaften des Knotens, der ein Projekt schachtelt die zu delegieren, wenn sie auf dem übergeordneten Element aufgerufen wird.  
  
     Da über- und untergeordneten Projekte programmgesteuert instanziiert werden, können Sie die Eigenschaften für geschachtelte Projekte an diesem Punkt festlegen.  
  
    > [!NOTE]
    >  Nicht nur erhalten Sie die Kontextinformationen aus dem geschachtelten Projekt, sondern können auch gefragt, ob das übergeordnete Projekt einen beliebigen Kontext für dieses Element durch die Überprüfung hat <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>. Auf diese Weise können Sie zusätzliche Attribute der dynamischen Hilfe und Menüoptionen, die bestimmten einzelnen geschachtelten Projekten hinzufügen.  
  
10. Die Hierarchie wird erstellt, für die Anzeige im Projektmappen-Explorer mit einem Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> Methode.  
  
     Übergeben Sie die Hierarchie, an die Umgebung über `GetNestedHierarchy` die Hierarchie für die Anzeige im Projektmappen-Explorer zu erstellen. Auf diese Weise weiß die Lösung an, das Projekt vorhanden ist und für die Erstellung von der Build-Manager verwaltet werden kann, oder Dateien im Projekt unter quellcodeverwaltung versetzt werden können.  
  
11. Wenn alle geschachtelten Projekte für Projekt1 erstellt wurden, erhält die Kontrolle wieder an die Lösung, und der Vorgang wird wiederholt, für die "Projekt2".  
  
     Dieser Prozess zum Erstellen von geschachtelten Projekten tritt ein, für ein untergeordnetes Projekt, das ein untergeordnetes Element verfügt. In diesem Fall wenn BuildProject1, das ein untergeordnetes Element des Projekt1 ist, untergeordnete Projekte enthält, würden sie nach dem BuildProject1 und vor "Projekt2" erstellt werden. Der Vorgang ist rekursiv, und die Hierarchie wird von oben nach unten erstellt.  
  
     Wenn ein geschachtelten Projekts geschlossen ist, da der Benutzer die Projektmappe geschlossen hat oder das entsprechende Projekt selbst, die andere Methode auf `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, aufgerufen wird. Das übergeordnete Projekt umschließt Aufrufe an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> -Methode mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> Methoden, um Listener zu Projektmappenereignissen benachrichtigen Sie, dass die geschachtelten Projekte geschlossen werden.  
  
 In den folgenden Themen behandeln verschiedene andere Konzepte beim Implementieren von geschachtelter Projekten zu berücksichtigen:  
  
 [Überlegungen für das Entladen und Neuladen von geschachtelten Projekten](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [Assistentenunterstützung für geschachtelte Projekte](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [Implementieren der Befehlsbehandlung für geschachtelte Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [Filtern des AddItem-Dialogfelds für geschachtelte Projekte](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Elementen, das Hinzufügen neuer Elemente in Dialogfeldern](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Kontextparameter](../../extensibility/internals/context-parameters.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)

