---
title: 'Gewusst wie: Implementieren von verschachtelten Projekten | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d9dfe567db0b8788b93b13aeb760d45f4c05b57
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707986"
---
# <a name="how-to-implement-nested-projects"></a>Gewusst wie: Implementieren verschachtelter Projekte

Wenn Sie einen geschachtelten Projekttyp erstellen, müssen mehrere zusätzliche Schritte implementiert werden. Ein übergeordnetes Projekt übernimmt einige der gleichen Aufgaben wie die Projektmappe für ihre verschachtelten (untergeordneten) Projekte. Das übergeordnete Projekt ist ein Container von Projekten, die einer Projektmappe ähneln. Insbesondere gibt es mehrere Ereignisse, die von der Projektmappe und von den übergeordneten Projekten ausgelöst werden müssen, um die Hierarchie der verschachtelten Projekte zu erstellen. Diese Ereignisse werden im folgenden Prozess zum Erstellen verschachtelter Projekte beschrieben.

## <a name="create-nested-projects"></a>Erstellen verschachtelter Projekte

1. Die integrierte Entwicklungsumgebung (IDE) lädt die Projektdatei und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> Startinformationen des übergeordneten Projekts, indem die Schnittstelle aufgerufen wird. Das übergeordnete Projekt wird erstellt und der Projektmappe hinzugefügt.

    > [!NOTE]
    > Zu diesem Zeitpunkt ist es für das übergeordnete Projekt zu früh, das verschachtelte Projekt zu erstellen, da das übergeordnete Projekt erstellt werden muss, bevor die untergeordneten Projekte erstellt werden können. Nach dieser Reihenfolge kann das übergeordnete Projekt Einstellungen auf die untergeordneten Projekte anwenden, und die untergeordneten Projekte können bei Bedarf Informationen aus den übergeordneten Projekten abrufen. Diese Sequenz wird von Clients wie Quellcodeverwaltung (SCC) und **Projektmappen-Explorer**benötigt.

     Das übergeordnete Projekt muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> warten, bis die Methode von der IDE aufgerufen wird, bevor es sein verschachteltes (untergeordnetes) Projekt oder seine Projekte erstellen kann.

2. Die IDE `QueryInterface` ruft das <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>übergeordnete Projekt für auf. Wenn dieser Aufruf erfolgreich ist, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> ruft die IDE die Methode des übergeordneten Elements auf, um alle verschachtelten Projekte für das übergeordnete Projekt zu öffnen.

3. Das übergeordnete Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> ruft die Methode auf, listener zu benachrichtigen, dass verschachtelte Projekte erstellt werden sollen. SCC hört sich beispielsweise diese Ereignisse an, um zu erfahren, ob die Schritte im Projektmappen- und Projekterstellungsprozess in der Reihenfolge erfolgen. Wenn die Schritte nicht in Ordnung sind, wird die Lösung möglicherweise nicht ordnungsgemäß bei der Quellcodeverwaltung registriert.

4. Das übergeordnete <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> Projekt ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> die Methode oder die Methode für jedes untergeordnete Projekt auf.

     Sie <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> übergeben `AddVirtualProject` die Methode, um anzugeben, dass das virtuelle (verschachtelte) Projekt dem Projektfenster hinzugefügt, vom Build ausgeschlossen, der Quellcodeverwaltung hinzugefügt werden soll usw. `VSADDVPFLAGS`können Sie die Sichtbarkeit des verschachtelten Projekts steuern und angeben, welche Funktionalität damit verknüpft ist.

     Wenn Sie ein zuvor vorhandenes untergeordnetes Projekt erneut laden, in dem eine Projekt-GUID in der Projektdatei des übergeordneten Projekts gespeichert ist, ruft das übergeordnete Projekt auf. `AddVirtualProjectEx` Der einzige `AddVirtualProject` Unterschied `AddVirtualProjectEX` zwischen `AddVirtualProjectEX` und ist, dass ein Parameter, `guidProjectID` der es dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> übergeordneten Projekt ermöglicht, eine pro Instanz für das untergeordnete Projekt anzugeben, um es zu aktivieren und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> ordnungsgemäß zu funktionieren.

     Wenn keine GUID verfügbar ist, z. B. wenn Sie ein neues verschachteltes Projekt hinzufügen, erstellt die Projektmappe eine für das Projekt zum Zeitpunkt der Bereitstellung zum übergeordneten Projekt. Es liegt in der Verantwortung des übergeordneten Projekts, diese Projekt-GUID in seiner Projektdatei beizubehalten. Wenn Sie ein verschachteltes Projekt löschen, kann auch die GUID für dieses Projekt gelöscht werden.

5. Die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> ruft die Methode für jedes untergeordnete Projekt des übergeordneten Projekts auf.

     Das übergeordnete Projekt `IVsParentProject` muss implementiert werden, wenn Sie Projekte verschachteln möchten. Aber das Übergeordnete `QueryInterface` Projekt `IVsParentProject` verlangt nie, auch wenn es Übergeordnete Projekte darunter hat. Die Projektmappe verarbeitet `IVsParentProject` den Aufruf von und, falls sie implementiert ist, Aufrufe, `OpenChildren` um die verschachtelten Projekte zu erstellen. `AddVirtualProjectEX`wird immer `OpenChildren`von aufgerufen. Es sollte nie vom übergeordneten Projekt aufgerufen werden, um die Hierarchieerstellungsereignisse in Ordnung zu halten.

6. Die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> ruft die Methode für das untergeordnete Projekt auf.

7. Das übergeordnete Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> ruft die Methode auf, Listener darüber zu informieren, dass die untergeordneten Projekte für das übergeordnete Element erstellt wurden.

8. Die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> ruft die Methode für das übergeordnete Projekt auf, nachdem alle untergeordneten Projekte geöffnet wurden.

     Wenn es noch nicht vorhanden ist, erstellt das übergeordnete Projekt `CoCreateGuid`eine GUID für jedes geschachtelte Projekt, indem es aufruft.

    > [!NOTE]
    > `CoCreateGuid`ist eine COM-API, die aufgerufen wird, wenn eine GUID erstellt werden soll. Weitere Informationen finden `CoCreateGuid` Sie unter und GUIDs in der MSDN-Bibliothek.

     Das übergeordnete Projekt speichert diese GUID in ihrer Projektdatei, die beim nächsten Öffnen in der IDE abgerufen werden soll. Weitere Informationen zum Aufruf von zum `AddVirtualProjectEX` Abrufen `guidProjectID` des für das untergeordnete Projekt finden Sie in Schritt 4.

9. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Methode wird dann für die übergeordnete ItemID aufgerufen, die Sie durch Konvention an das geschachtelte Projekt delegieren. Der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> ruft die Eigenschaften des Knotens ab, der ein Projekt verschachtelt, an das Sie delegieren möchten, wenn es für das übergeordnete Element aufgerufen wird.

     Da übergeordnete und untergeordnete Projekte programmgesteuert instanziiert werden, können Sie an dieser Stelle Eigenschaften für verschachtelte Projekte festlegen.

    > [!NOTE]
    > Sie erhalten nicht nur die Kontextinformationen aus dem verschachtelten Projekt, sondern Sie können auch fragen, ob das übergeordnete Projekt einen Kontext für dieses Element hat, indem Sie [__VSHPROPID überprüfen. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). Auf diese Weise können Sie zusätzliche dynamische Hilfeattribute und Menüoptionen hinzufügen, die für einzelne verschachtelte Projekte spezifisch sind.

10. Die Hierarchie wird für die Anzeige im <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> **Projektmappen-Explorer** mit einem Aufruf der Methode erstellt.

     Sie übergeben die Hierarchie `GetNestedHierarchy` an die Umgebung, um die Hierarchie für die Anzeige im Projektmappen-Explorer zu erstellen. Auf diese Weise weiß die Projektmappe, dass das Projekt vorhanden ist und vom Build-Manager für die Erstellung verwaltet werden kann, oder sie kann zulassen, dass Dateien im Projekt unter Quellcodeverwaltung gestellt werden.

11. Wenn alle verschachtelten Projekte für Project1 erstellt wurden, wird die Steuerung an die Projektmappe zurückübergaben, und der Prozess wird für Project2 wiederholt.

     Derselbe Prozess zum Erstellen verschachtelter Projekte tritt für ein untergeordnetes Projekt auf, das über ein untergeordnetes Projekt verfügt. Wenn in diesem Fall BuildProject1, das ein untergeordnetes Element von Project1 ist, untergeordnete Projekte hatte, würden sie nach BuildProject1 und vor Project2 erstellt. Der Prozess ist rekursiv, und die Hierarchie wird von oben nach unten erstellt.

     Wenn ein geschachteltes Projekt geschlossen wird, weil der Benutzer die `IVsParentProject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>Projektmappe oder das spezifische Projekt selbst geschlossen hat, wird die andere Methode für , aufgerufen. Das übergeordnete Projekt umschließt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> Aufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> Methode mit der und den Methoden, um Listener zu Projektmappenereignissen zu benachrichtigen, dass die verschachtelten Projekte geschlossen werden.

In den folgenden Themen werden mehrere andere Konzepte behandelt, die beim Implementieren verschachtelter Projekte zu berücksichtigen sind:

- [Überlegungen zum Entladen und Nachladen verschachtelter Projekte](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Assistentenunterstützung für verschachtelte Projekte](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementieren der Befehlsbehandlung für verschachtelte Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtern des Dialogfelds AddItem nach verschachtelten Projekten](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen von Elementen zum Dialogfeld Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Checkliste: Neue Projekttypen erstellen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Kontextparameter](../../extensibility/internals/context-parameters.md)
- [Wizarddatei (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
