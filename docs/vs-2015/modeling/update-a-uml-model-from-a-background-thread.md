---
title: Aktualisieren eines UML-Modells aus einem Hintergrundthread | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7faef9f085f21db4d4f819746acf52c119189f6d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940995"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Aktualisieren eines UML-Modells aus einem Hintergrundthread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gelegentlich kann es nützlich sein, Änderungen an einem Modell in einem Hintergrundthread vorzunehmen. Wenn Sie z. B. Informationen aus einer langsamen externen Ressource laden, können Sie die Updates mithilfe eines Hintergrundthreads überwachen. Dies ermöglicht es dem Benutzer, die einzelnen Updates zu sehen, sobald diese ausgeführt wurden.  
  
 Dabei ist jedoch zu beachten, dass der UML-Speicher nicht threadsicher ist. Die folgenden Vorsichtsmaßnahmen sind zu beachten:  
  
-   Jedes Update eines Modells oder Diagramm muss im UI-Thread (Benutzeroberflächenthread) ausgeführt werden. Der Hintergrundthread muss <xref:System.Windows.Forms.Control.Invoke%2A> oder `Dispatcher.`<xref:System.Windows.Threading.Dispatcher.Invoke%2A> verwenden, damit der UI-Thread die tatsächlichen Updates ausführt.  
  
-   Wenn Sie eine Reihe von Änderungen in einer einzigen Transaktion zusammenfassen, sollten Sie verhindern, dass der Benutzer das Modell bearbeitet, während die Transaktion ausgeführt wird. Andernfalls werden vom Benutzer vorgenommene Änderungen zum Teil dieser Transaktion. Sie können verhindern, dass Benutzer Änderungen vornehmen, indem Sie ein modales Dialogfeld anzeigen. Sie können ggf. eine Schaltfläche Abbrechen im Dialogfeld bereitstellen. Die Änderungen werden für den Benutzer in Echtzeit angezeigt.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel werden mit einem Hintergrundthread mehrere Änderungen an einem Modell vorgenommen. Mithilfe eines Dialogfelds werden Bearbeitungen durch den Benutzer verhindert, während der Thread ausgeführt wird. In diesem einfachen Beispiel wird keine Schaltfläche Abbrechen im Dialogfeld bereitgestellt. Diese Funktion kann jedoch auf einfache Weise hinzugefügt werden.  
  
#### <a name="to-run-the-example"></a>So führen Sie das Beispiel aus  
  
1. Erstellen Sie einen Befehlshandler in einem C#-Projekt, wie im [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
2. Stellen Sie sicher, dass das Projekt Verweise auf die folgenden Assemblys enthält:  
  
   -   Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.[version]  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]  
  
   -   Microsoft.VisualStudio.Uml.Interfaces  
  
   -   System.ComponentModel.Composition  
  
   -   System.Windows.Forms  
  
3. Fügen Sie dem Projekt ein Windows-Formular mit dem Namen **ProgressForm hinzu**. Dieses muss eine Meldung anzeigen, mit der angegeben wird, dass die Updates ausgeführt werden. Weitere Steuerelemente müssen nicht enthalten sein.  
  
4. Fügen Sie eine C#-Datei hinzu, die den nach Schritt 7 angezeigten Code enthält.  
  
5. Erstellen Sie das Projekt, und führen Sie es aus.  
  
    Eine neue Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird im Testmodus gestartet.  
  
6. Erstellen oder öffnen Sie ein UML-Klassendiagramm in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7. Mit der rechten Maustaste an einer beliebigen Stelle im UML-Klassendiagramm, und klicken Sie dann auf **Add Several UML Classes**.  
  
   Mehrere neue Klassenfelder werden im Diagramm angezeigt, die in Intervallen von jeweils einer halben Sekunde aufeinander folgen.  
  
```csharp  
using System;  
using System.ComponentModel;  
using System.ComponentModel.Composition;  
using System.Threading;  
using System.Windows.Forms;  
  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.Uml.Classes;  
  
namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class UmlClassAdderCommand : ICommandExtension  
  {  
  
    [Import]  
    IDiagramContext context { get; set; }  
  
    [Import]  
    ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called when the user runs the command.  
    public void Execute(IMenuCommand command)  
    {  
      // The form that will exclude the user.  
      ProgressForm form = new ProgressForm();  
  
      // System.ComponentModel.BackgroundWorker is a  
      // convenient way to run a background thread.  
      BackgroundWorker worker = new BackgroundWorker();  
      worker.WorkerSupportsCancellation = true;  
  
      worker.DoWork += delegate(object sender, DoWorkEventArgs args)  
      {  
        // This block will be executed in a background thread.  
  
        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;  
        IModelStore store = diagram.ModelStore;  
        const int CLASSES_TO_CREATE = 15;  
  
        // Group all the changes together.  
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))  
        {  
          for (int i = 1; i < CLASSES_TO_CREATE; i++)  
          {  
            if (worker.CancellationPending)   
               return; // No commit - undo all.  
  
            // Create model elements using the UI thread by using  
            // the Invoke method on the progress form. Always   
            // modify the model and diagrams from a UI thread.  
            form.Invoke((MethodInvoker)(delegate  
            {  
              IClass newClass = store.Root.CreateClass();  
              newClass.Name = string.Format("NewClass{0}", i);  
              diagram.Display(newClass);  
            }));  
  
            // Sleep briefly so that we can watch the updates.  
            Thread.Sleep(500);  
          }  
  
          // Commit the transaction or it will be rolled back.  
          transaction.Commit();  
        }  
      };  
  
      // Close the form when the thread completes.  
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)  
      {  
        form.Close();  
      };  
  
      // Start the thread before showing the modal progress dialog.  
      worker.RunWorkerAsync();  
  
      // Show the form modally, parented on VS.  
      // Prevents the user from making changes while in progress.  
      form.ShowDialog();  
    }  
  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
  
    public string Text  
    {  
      get { return "Add several classes"; }  
    }  
  }  
}  
```  
  
#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>So lassen Sie zu, dass Benutzer den Thread im Beispiel abbrechen  
  
1.  Fügen Sie dem Statusdialogfeld eine Schaltfläche zum Abbrechen hinzu.  
  
2.  Fügen Sie dem Statusdialogfeld den folgenden Code hinzu:  
  
     `public event MethodInvoker Cancel;`  
  
     `private void CancelButton_Click(object sender, EventArgs e)`  
  
     `{`  
  
     `Cancel();`  
  
     `}`  
  
3.  Fügen Sie in der Execute()-Methode nach der Formularkonstruktion die folgende Zeile ein:  
  
     `form.Cancel += delegate() { worker.CancelAsync(); };`  
  
### <a name="other-methods-of-accessing-the-ui-thread"></a>Weitere Methoden zum Zugreifen auf den UI-Thread  
 Wenn Sie kein Dialogfeld erstellen möchten, können Sie auf das Steuerelement zugreifen, von dem das Diagramm angezeigt wird:  
  
 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`  
  
 Mithilfe von `uiThreadHolder.Invoke()` können Sie Vorgänge im UI-Thread ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definieren eines Gestenhandlers in einem Modellierungsdiagramm](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)



