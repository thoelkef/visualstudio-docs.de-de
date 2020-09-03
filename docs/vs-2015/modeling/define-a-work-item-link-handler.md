---
title: Definieren eines Link Handlers für Arbeitselemente | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 380aaa5bed1e30c549334bc004ea38e3f0bdb762
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669935"
---
# <a name="define-a-work-item-link-handler"></a>Definieren eines Linkhandlers für Arbeitselemente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Visual Studio Integration Extension erstellen, die auf das Erstellen oder Löschen eines Links zwischen einem UML-Modellelement und ein Arbeitselement durch den Benutzer reagiert. Wenn Benutzer ein neues Arbeitselement mit einem Modellelement verknüpfen, können beispielsweise im Code die Felder des Arbeitselements aus Werten im Modell initialisiert werden.

## <a name="set-up-a-uml-extension-solution"></a>Einrichten einer UML-Erweiterungsprojektmappe
 Auf diese Weise können Sie Handler entwickeln und dann an andere Benutzer verteilen. Sie müssen zwei Visual Studio-Projekte einrichten:

- Ein Klassenbibliotheksprojekt, das den Code für den Linkhandler enthält.

- Ein VSIX-Projekt, das als Container zum Installieren des Befehls fungiert. Gegebenenfalls können Sie in dasselbe VSIX auch weitere Komponenten einschließen.

#### <a name="to-set-up-the-visual-studio-solution"></a>So richten Sie die Visual Studio-Projektmappe ein

1. Erstellen Sie ein Klassenbibliotheksprojekt. Sie können dieses entweder zu einer vorhandenen VSIX-Projektmappe hinzufügen, oder Sie können eine neue Projektmappe erstellen.

    1. Wählen Sie im Menü **Datei** die Befehle **Neu** und **Projekt** aus.

    2. Erweitern Sie unter **installierte Vorlagen**den Eintrag **Visual c#** oder **Visual Basic**, und klicken Sie dann in der mittleren Spalte auf **Klassenbibliothek**.

    3. Legen Sie **Projektmappe** fest, um anzugeben, ob eine neue Projektmappe erstellt oder einer bereits geöffneten VSIX-Projektmappe eine Komponente hinzugefügt werden soll.

    4. Legen Sie Name und Speicherort für das Projekt fest, und klicken Sie auf OK.

2. Erstellen Sie ein VSIX-Projekt, sofern die Projektmappe noch kein VSIX-Projekt enthält.

    1. Wählen Sie in **Projektmappen-Explorer**im Kontextmenü der Projekt Mappe die Option **Hinzufügen**und dann **Neues Projekt**aus.

    2. Erweitern Sie unter **Installierte Vorlagen**den Knoten **Visual C#** oder **Visual Basic**, und wählen Sie anschließend **Erweiterungen**aus. Wählen Sie in der mittleren Spalte **VSIX Project**.

3. Legen Sie das VSIX-Projekt als Startprojekt der Projektmappe fest.

    - Wählen Sie in Projektmappen-Explorer im Kontextmenü des VSIX-Projekts die Option **als Startprojekt festlegen**aus.

4. Fügen Sie in **Source. Extension. vsixmanifest**unter **Inhalt**das Klassen Bibliotheksprojekt als MEF-Komponente hinzu.

    1. Legen Sie auf der Registerkarte **MetaData** einen Namen für VSIX fest.

    2. Legen Sie auf der Registerkarte **Ziele installieren** die Visual Studio-Versionen als Ziele fest.

    3. Wählen Sie auf der Registerkarte **Objekte** die Option **Neu**und wählen Sie im Dialogfeld:

         **Typ**  =  **MEF-Komponente**

         **Quelle**  =  **Ein Projekt in der aktuellen Projekt** Mappe.

         **Projekt**  =  *Ihr Klassen Bibliotheksprojekt*

## <a name="defining-the-work-item-link-handler"></a>Definieren des Arbeitsaufgaben-Linkhandlers
 Führen Sie alle folgenden Aufgaben im Klassenbibliotheksprojekt aus.

### <a name="project-references"></a>Projektverweise
 Fügen Sie den Projektverweisen die folgenden [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]-Assemblys hinzu:

 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`

 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`

 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

 `Microsoft.VisualStudio.Uml.Interfaces`

 `System.ComponentModel.Composition`

 `System.Drawing` -verwendet durch den Beispielcode

 Wenn Sie einen dieser Verweise nicht auf der Registerkarte **.net** des Dialog Felds **Verweis hinzufügen** finden können, verwenden Sie die Registerkarte Durchsuchen, um Sie in \Programme\Microsoft Visual Studio [Version] \common7\ide\privateassemblys zu suchen \\ .

### <a name="import-the-work-item-namespace"></a>Importieren des Namespaces für Arbeitsaufgaben
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Fügen Sie in den Projekt **verweisen**Verweise auf die folgenden Assemblys hinzu:

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll

  Importieren Sie im Programmcode die folgenden Namespaces:

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;
```

### <a name="define-the-linked-work-item-event-handler"></a>Definieren des Ereignishandlers für verknüpfte Arbeitsaufgaben
 Fügen Sie dem Klassenbibliotheksprojekt eine Klassendatei hinzu, und legen Sie deren Inhalt wie folgt fest. Ändern Sie die Namespace- und Klassennamen entsprechend den jeweiligen Anforderungen.

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;

namespace WorkItems
{
  [Export(typeof(ILinkedWorkItemExtension))]
  public class MyWorkItemExtension : ILinkedWorkItemExtension
  {
    // Called before a new work item is edited by the user.
    // Use this to initialize work item fields from the model element.
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)
    {
      INamedElement namedElement =
            elementsToBeLinked.First() as INamedElement;
      if (namedElement != null)
        workItemDocument.Item.Title = namedElement.Name;

    }

    // Called when any work item is linked to a model element.
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)
    {
      foreach (IElement element in elements)
        foreach (IShape shape in element.Shapes())
          shape.Color = System.Drawing.Color.Red;
    }

    // Called when a work item is unlinked from a model element.
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)
    {
      foreach (IShape shape in element.Shapes())
        shape.Color = System.Drawing.Color.White;
    }
  }
}
```

## <a name="testing-the-link-handler"></a>Testen des Linkhandlers
 Führen Sie den Linkhandler zu Testzwecken im Debugmodus aus.

> [!WARNING]
> Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um ein Arbeitselement zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, ein Arbeitselement zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.

#### <a name="to-test-the-link-handler"></a>So testen Sie den Linkhandler

1. Drücken Sie **F5**oder wählen Sie im Menü **Debug** die Option **Debugging starten**.

     Eine experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird gestartet.

     **Problem**Behandlung: Wenn ein neuer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nicht gestartet wird, stellen Sie sicher, dass das VSIX-Projekt als Startprojekt der Projekt Mappe festgelegt ist.

2. Öffnen oder erstellen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ein Modellierungsprojekt, und öffnen oder erstellen Sie ein Modellierungsdiagramm.

3. Erstellen Sie ein Modellelement (z. B. eine UML-Klasse), und legen Sie dessen Namen fest.

4. Klicken Sie mit der rechten Maustaste auf das Element, und klicken Sie auf **Arbeitsaufgabe erstellen**.

    - Wenn im Untermenü die Option **Team Foundation Server Verbindung öffnen**angezeigt wird, müssen Sie das Projekt schließen, eine Verbindung mit dem entsprechenden TFS herstellen und dieses Verfahren neu starten.

    - Wenn im Untermenü eine Liste von Arbeitselementetypen angezeigt wird, klicken Sie auf einen Arbeitselementetyp.

         Ein neues Arbeitselementformular wird geöffnet.

5. Vergewissern Sie sich, dass der Titel des Arbeitselementes dem des Modellelements entspricht, wenn Sie den Beispielcode aus dem vorherigen Abschnitt verwendet haben. Dadurch wird nachgewiesen, dass `OnWorkItemCreated()` erfolgreich ausgeführt wurde.

6. Füllen Sie das Formular aus. Speichern und schließen Sie anschließend das Arbeitselement.

7. Überprüfen Sie, ob das Arbeitselement jetzt rot gefärbt ist. Dies wird von `OnWorkItemLinked()` im Beispielcode veranschaulicht.

     **Problem**Behandlung: Wenn die Handlermethoden nicht ausgeführt wurden, überprüfen Sie Folgendes:

    - Das Klassen Bibliotheksprojekt wird in der **Inhalts** Liste in **Source. Extensions. Manifest** im VSIX-Projekt als MEF-Komponente aufgeführt.

    - An die Handlerklasse ist das richtige `Export`-Attribut angefügt, und von der Klasse wird `ILinkedWorkItemExtension` implementiert.

    - Die Parameter aller `Import`-Attribute und `Export`-Attribute sind gültig.

## <a name="about-the-work-item-handler-code"></a>Informationen zum Arbeitselement-Handlercode

### <a name="listening-for-new-work-items"></a>Lauschen auf neue Arbeitsaufgaben
 `OnWorkItemCreated` wird aufgerufen, wenn der Benutzer ein neues Arbeits Element erstellt, das mit den Modellelementen verknüpft werden soll. Die Arbeitselementfelder können im Code initialisiert werden. Anschließend wird das Arbeitselement angezeigt, und Benutzer können die Felder aktualisieren und das Arbeitselement speichern. Der Link zu einem Modellelement wird erst erstellt, wenn das Arbeitselement erfolgreich gespeichert wurde.

```
public void OnWorkItemCreated(
    IEnumerable<IElement> elementsToBeLinked,
    IWorkItemDocument workItem)
{
  INamedElement namedElement =
         elementsToBeLinked.First() as INamedElement;
  if (namedElement != null)
      workItem.Item.Title = namedElement.Name;
}
```

### <a name="listening-for-link-creation"></a>Lauschen auf Linkerstellung
 `OnWorkItemLinked` wird unmittelbar nach dem Erstellen eines Links aufgerufen. Dabei spielt es keine Rolle, ob die Verknüpfung mit einer neuen oder ein bestehenden Arbeitselement hergestellt wurde. Der Aufruf erfolgt einmal für jedes Arbeitselement.

```
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  foreach (IElement element in elements)
    foreach (IShape shape in element.Shapes())
         shape.Color = System.Drawing.Color.Red;
}
```

> [!NOTE]
> Damit dieses Beispiel funktioniert, müssen Sie einen Projektverweis auf `System.Drawing.dll` hinzufügen und den `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation`-Namespace importieren. Diese Hinzufügungen sind für andere Implementierungen von `OnWorkItemLinked` jedoch nicht erforderlich.

### <a name="listening-for-link-removal"></a>Lauschen auf Linkentfernung
 `OnWorkItemRemoved` wird einmal unmittelbar vor jedem gelöschten Arbeits Element Link aufgerufen. Wenn ein Modellelement gelöscht wird, werden alle Links entfernt.

```
public void OnWorkItemRemoved
         (IElement element, string serverUri, int workItemId)
{...}
```

## <a name="updating-a-work-item"></a>Aktualisieren ein Arbeitselement
 Sie können Arbeitselemente mithilfe der Team Foundation-Namespaces bearbeiten.

 Fügen Sie den Verweisen des Projekts die folgenden .NET-Assemblys hinzu, um das folgende Beispiel zu verwenden:

- Microsoft.TeamFoundation.Client.dll

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

```

using Microsoft.TeamFoundation.Client;
using Microsoft.TeamFoundation.WorkItemTracking.Client;
...
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  TfsTeamProjectCollection tfs =
        TfsTeamProjectCollectionFactory
            .GetTeamProjectCollection(new Uri(serverUri));
  WorkItemStore workItemStore = new WorkItemStore(tfs);
  WorkItem item = workItemStore.GetWorkItem(workItemId);
  item.Open();
  item.Title = "something";
  item.Save();
} 
```

## <a name="accessing-the-work-item-reference-links"></a>Zugreifen auf die Verweislinks für Arbeitselemente
 Sie können wie folgt auf die Links zugreifen:

```
//Get:
string linkString = element.GetReference(ReferenceConstants.WorkItem);
// Set:
element.AddReference(ReferenceConstants.WorkItem, linkString, true);

```

 Das Format von `linkString` lautet wie folgt:

 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`

 Dabei gilt Folgendes:

- Der URI für den Server lautet dann:

   `http://tfServer:8080/tfs/projectCollection`

   In `projectCollection` wird die Groß- und Kleinschreibung beachtet.

- `RepositoryGuid` kann von der TFS-Verbindung abgerufen werden:

  ```csharp
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;
  RepositoryGuid= tpc.InstanceId;

  ```

  Weitere Informationen zu verweisen finden Sie unter [Anfügen von Verweis Zeichenfolgen an UML-Modellelemente](../modeling/attach-reference-strings-to-uml-model-elements.md).

## <a name="see-also"></a>Siehe auch

- [Microsoft. TeamFoundation. WorkItemTracking. Client. WorkItemStore](/previous-versions/visualstudio/visual-studio-2013/bb179850(v=vs.120))
- [Verknüpfen von Modellelementen und Arbeitselementen](../modeling/link-model-elements-and-work-items.md)
- [Anfügen von Referenzzeichenfolgen an UML-Modellelemente](../modeling/attach-reference-strings-to-uml-model-elements.md)
- [Definieren und Installieren einer Modellierungserweiterung](../modeling/define-and-install-a-modeling-extension.md)
- [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md)
