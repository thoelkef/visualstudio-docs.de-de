---
title: Definieren ein linkhandlers für Arbeitsaufgaben | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd50f4c80e5e67f6fb7582dc2bc22963151b42fe
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433118"
---
# <a name="define-a-work-item-link-handler"></a>Definieren eines Linkhandlers für Arbeitselemente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Visual Studio Integration Extension erstellen, die auf das Erstellen oder Löschen eines Links zwischen einem UML-Modellelement und einem Arbeitselement durch den Benutzer reagiert. Wenn Benutzer eine neue Arbeitsaufgabe mit einem Modellelement verknüpfen, können beispielsweise im Code die Felder der Arbeitsaufgabe aus Werten im Modell initialisiert werden.  
  
## <a name="set-up-a-uml-extension-solution"></a>Einrichten einer UML-Erweiterungsprojektmappe  
 Auf diese Weise können Sie Handler entwickeln und dann an andere Benutzer verteilen. Sie müssen zwei Visual Studio-Projekte einrichten:  
  
- Ein Klassenbibliotheksprojekt, das den Code für den Linkhandler enthält.  
  
- Ein VSIX-Projekt, das als Container zum Installieren des Befehls fungiert. Gegebenenfalls können Sie in dasselbe VSIX auch weitere Komponenten einschließen.  
  
#### <a name="to-set-up-the-visual-studio-solution"></a>So richten Sie die Visual Studio-Projektmappe ein  
  
1. Erstellen Sie ein Klassenbibliotheksprojekt. Sie können dieses entweder zu einer vorhandenen VSIX-Projektmappe hinzufügen, oder Sie können eine neue Projektmappe erstellen.  
  
    1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu**, **Projekt**aus.  
  
    2. Klicken Sie unter **installierte Vorlagen**, erweitern Sie **Visual C#-** oder **Visual Basic**, klicken Sie dann in der mittleren Spalte auf **Klassenbibliothek**.  
  
    3. Legen Sie **Projektmappe** fest, um anzugeben, ob eine neue Projektmappe erstellt oder einer bereits geöffneten VSIX-Projektmappe eine Komponente hinzugefügt werden soll.  
  
    4. Legen Sie Name und Speicherort für das Projekt fest, und klicken Sie auf OK.  
  
2. Erstellen Sie ein VSIX-Projekt, sofern die Projektmappe noch kein VSIX-Projekt enthält.  
  
    1. Wählen Sie im **Projektmappen-Explorer**im Kontextmenü der Projektmappe die Option **Hinzufügen**und dann **Neues Projekt**aus.  
  
    2. Erweitern Sie unter **Installierte Vorlagen**den Knoten **Visual C#** oder **Visual Basic**, und wählen Sie anschließend **Erweiterungen**aus. Wählen Sie in der mittleren Spalte **VSIX Project**.  
  
3. Legen Sie das VSIX-Projekt als Startprojekt der Projektmappe fest.  
  
    - Wählen Sie im Projektmappen-Explorer im Kontextmenü des VSIX-Projekts die Option **Als Startprojekt festlegen**aus.  
  
4. In **"Source.Extension.vsixmanifest"** unter **Content**, fügen Sie das Klassenbibliotheksprojekt als MEF-Komponente hinzu.  
  
    1. Legen Sie auf der Registerkarte **MetaData** einen Namen für VSIX fest.  
  
    2. Legen Sie auf der Registerkarte **Ziele installieren** die Visual Studio-Versionen als Ziele fest.  
  
    3. Wählen Sie auf der Registerkarte **Objekte** die Option **Neu**und wählen Sie im Dialogfeld:  
  
         **Typ** = **MEF-Komponente**  
  
         **Quelle** = **Ein Projekt in der aktuellen Projektmappe**  
  
         **Projekt** = *Ihr Klassenbibliotheksprojekt*  
  
## <a name="defining-the-work-item-link-handler"></a>Definieren des Arbeitselement-Linkhandlers  
 Führen Sie alle folgenden Aufgaben im Klassenbibliotheksprojekt aus.  
  
### <a name="project-references"></a>Projektverweise  
 Fügen Sie den Projektverweisen die folgenden [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]-Assemblys hinzu:  
  
 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`  
  
 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
 `Microsoft.VisualStudio.Uml.Interfaces`  
  
 `System.ComponentModel.Composition`  
  
 `System.Drawing` -vom Beispielcode verwendet  
  
 Wenn Sie einen dieser Verweise unter nicht finden die **.Net** Registerkarte die **Verweis hinzufügen** Dialogfeld, verwenden Sie die Registerkarte "Durchsuchen", um diese Datei unter \Programme\Microsoft Visual Studio [Version] \Common7\IDE\ finden "Privateassemblies"\\.  
  
### <a name="import-the-work-item-namespace"></a>Importieren des Namespaces für Arbeitselemente  
 In Ihrer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projekt **Verweise**, fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
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
  
     **Problembehandlung bei**: Wenn ein neuer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nicht gestartet wird, stellen Sie sicher, dass das VSIX-Projekt als Startprojekt der Projektmappe festgelegt ist.  
  
2. Öffnen oder erstellen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ein Modellierungsprojekt, und öffnen oder erstellen Sie ein Modellierungsdiagramm.  
  
3. Erstellen Sie ein Modellelement (z. B. eine UML-Klasse), und legen Sie dessen Namen fest.  
  
4. Mit der rechten Maustaste in des Elements, und klicken Sie dann auf **Arbeitselement erstellen**.  
  
    - Wenn im Untermenü **Team Foundation Server-Verbindung öffnen**, Sie benötigen, schließen Sie das Projekt, eine Verbindung mit dem richtigen TFS herstellen und Vorgang erneut starten.  
  
    - Wenn im Untermenü eine Liste von Arbeitselementtypen angezeigt wird, klicken Sie auf einen Arbeitselementtyp.  
  
         Ein neues Arbeitsaufgabenformular wird geöffnet.  
  
5. Vergewissern Sie sich, dass der Titel der Arbeitsaufgabe dem des Modellelements entspricht, wenn Sie den Beispielcode aus dem vorherigen Abschnitt verwendet haben. Dadurch wird nachgewiesen, dass `OnWorkItemCreated()` erfolgreich ausgeführt wurde.  
  
6. Füllen Sie das Formular aus. Speichern und schließen Sie anschließend die Arbeitsaufgabe.  
  
7. Überprüfen Sie, ob die Arbeitsaufgabe jetzt rot gefärbt ist. Dies wird von `OnWorkItemLinked()` im Beispielcode veranschaulicht.  
  
     **Problembehandlung bei**: Wenn die Handlermethoden nicht ausgeführt haben, überprüfen Sie Folgendes aus:  
  
    - Das Klassenbibliotheksprojekt als MEF-Komponente auf aufgeführt ist die **Content** Liste **source.extensions.manifest** im VSIX-Projekt.  
  
    - An die Handlerklasse ist das richtige `Export`-Attribut angefügt, und von der Klasse wird `ILinkedWorkItemExtension` implementiert.  
  
    - Die Parameter aller `Import`-Attribute und `Export`-Attribute sind gültig.  
  
## <a name="about-the-work-item-handler-code"></a>Informationen zum Arbeitsaufgaben-Handlercode  
  
### <a name="listening-for-new-work-items"></a>Lauschen auf neue Arbeitsaufgaben  
 `OnWorkItemCreated` wird aufgerufen, wenn Benutzer eine neue Arbeitsaufgabe erstellen, die mit den Modellelementen verknüpft werden soll. Die Arbeitsaufgabenfelder können im Code initialisiert werden. Anschließend wird die Arbeitsaufgabe angezeigt, und Benutzer können die Felder aktualisieren und die Arbeitsaufgabe speichern. Der Link zu einem Modellelement wird erst erstellt, wenn die Arbeitsaufgabe erfolgreich gespeichert wurde.  
  
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
 `OnWorkItemLinked` wird unmittelbar nach dem Erstellen eines Links aufgerufen. Dabei spielt es keine Rolle, ob die Verknüpfung mit einer neuen oder einer bestehenden Arbeitsaufgabe hergestellt wurde. Der Aufruf erfolgt einmal für jede Arbeitsaufgabe.  
  
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
 `OnWorkItemRemoved` wird einmal unmittelbar vor dem Entfernen des Arbeitsaufgabenlinks aufgerufen. Wenn ein Modellelement gelöscht wird, werden alle Links entfernt.  
  
```  
public void OnWorkItemRemoved  
         (IElement element, string serverUri, int workItemId)  
{...}  
```  
  
## <a name="updating-a-work-item"></a>Aktualisieren einer Arbeitsaufgabe  
 Sie können Arbeitsaufgaben mithilfe der Team Foundation-Namespaces bearbeiten.  
  
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
  
## <a name="accessing-the-work-item-reference-links"></a>Zugreifen auf die Verweislinks für Arbeitsaufgaben  
 Sie können wie folgt auf die Links zugreifen:  
  
```  
//Get:  
string linkString = element.GetReference(ReferenceConstants.WorkItem);  
// Set:  
element.AddReference(ReferenceConstants.WorkItem, linkString, true);  
  
```  
  
 Das Format von `linkString` lautet wie folgt:  
  
 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`  
  
 Dabei gilt:  
  
- Der URI für den Server lautet dann:  
  
   `http://tfServer:8080/tfs/projectCollection`  
  
   In `projectCollection` wird die Groß- und Kleinschreibung beachtet.  
  
- `RepositoryGuid` kann von der TFS-Verbindung abgerufen werden:  
  
  ```csharp  
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;  
  RepositoryGuid= tpc.InstanceId;  
  
  ```  
  
  Weitere Informationen über Verweise finden Sie unter [Anfügen von Referenzzeichenfolgen an UML-Modellelemente](../modeling/attach-reference-strings-to-uml-model-elements.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore?displayProperty=fullName>   
 [Verknüpfen von Modellelementen und Arbeitsaufgaben](../modeling/link-model-elements-and-work-items.md)   
 [Anfügen von Referenzzeichenfolgen an UML-Modellelemente](../modeling/attach-reference-strings-to-uml-model-elements.md)   
 [Definieren und Installieren einer modellierungserweiterung](../modeling/define-and-install-a-modeling-extension.md)   
 [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md)
