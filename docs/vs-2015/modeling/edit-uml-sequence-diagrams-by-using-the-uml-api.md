---
title: Bearbeiten von UML-Sequenzdiagrammen mit der UML-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c619ae6efd1de48319bf9c0398ee8ab4e3cd57ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442958"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>Bearbeiten von UML-Sequenzdiagrammen mit der UML-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Interaktion ist eine Sequenz von Meldungen zwischen einem Satz von Lebenslinien. Eine Interaktion wird in einem UML-Sequenzdiagramm angezeigt.  
  
 Detaillierte Informationen zur API finden Sie unter <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>.  
  
 Eine allgemeine Einführung in das Schreiben von Befehls- und gestenhandlern für UML-Diagramme, finden Sie unter [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="basic-code"></a>Basic-Code  
  
### <a name="namespace-imports"></a>Namespaceimporte  
 Sie müssen die folgenden `using`-Anweisungen einschließen:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
   // for basic UML types such as IPackage  
using Microsoft.VisualStudio.Uml.Interactions;  
   // for interaction types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // to create elements and use additional functions  
```  
  
 Wenn Sie Menübefehle und Gestenhandler erstellen, müssen Sie außerdem:  
  
```  
using System.ComponentModel.Composition;   
   // for Import and Export  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   // for ICommandExtension  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   // for diagrams and context  
```  
  
 Weitere Informationen finden Sie unter [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="getting-the-context"></a>Abrufen von Kontext  
 Wenn Sie eine Interaktion als Teil eines Befehls oder eines Gestenhandlers in einem Diagramm bearbeiten, können Sie einen Verweis auf den Kontext abrufen. Zum Beispiel:  
  
```  
[SequenceDesignerExtension]  
[Export(typeof(ICommandExtension))]    
public class MySequenceDiagramCommand : ICommandExtension  
{  
    [Import]  
    public IDiagramContext Context { get; set; }  
    public void QueryStatus (IMenuCommand command)  
    {  
      ISequenceDiagram sequenceDiagram =   
          Context.CurrentDiagram as ISequenceDiagram;  
         ...  
```  
  
### <a name="generated-and-uml-sequence-diagrams"></a>Generierte und UML-Sequenzdiagramme  
 Es gibt zwei Arten von Sequenzdiagrammen: manuell in einem UML-Modellierungsprojekt erstellte, und solche, die aus Programmcode generiert wurden. Verwenden Sie die `UmlMode` -Eigenschaft, um zu ermitteln, welches Sequenzdiagramm Sie haben.  
  
> [!NOTE]
> Diese Eigenschaft false nur bei Sequenzdiagrammen zurück, die aus Code mit Visual Studio 2013 und früheren Versionen generiert wurden. Dies schließt code-generierte Sequenzdiagramme ein, die von 2013 und früheren Versionen migriert wurden. Diese Version von Visual Studio unterstützt nicht das Generieren von neuen Sequenzdiagrammen.  
  
 Wenn Sie beispielsweise einen Menübefehl erstellen möchten, der nur in UML-Sequenzdiagrammen sichtbar ist, kann die `QueryStatus()` -Methode die folgende Anweisung enthalten:  
  
```  
command.Enabled = command.Visible =   
      sequenceDiagram != null && sequenceDiagram.UmlMode;  
```  
  
 Generierte Sequenzdiagramme, Lebenslinien, Meldungen und andere Elemente entsprechen größtenteils denen im UML-Sequenzdiagramm. In einem UML-Modell hat der Modellspeicher eine Stammzertifizierungsstelle, das Modell, das alle anderen Elemente besitzt. Es gibt jedoch eine generierte Interaktion im eigenen Modellspeicher, der einen NULL-Stamm aufweist:  
  
```  
IModel rootModel = sequenceDiagram.ModelStore.Root;  
    // !sequenceDiagram.UmlMode == (rootModel == null)  
```  
  
## <a name="to-create-and-display-an-interaction"></a>Erstellen und Anzeigen einer Interaktion  
 Erstellen Sie die Interaktion als untergeordnetes Element eines Pakets oder Modells.  
  
 Wenn Sie beispielsweise einen Befehl entwickeln, der auf ein leeres Sequenzdiagramm ausgeführt werden kann, sollten Sie immer zuerst überprüfen, ob die Interaktion vorhanden ist.  
  
```  
public void Execute (IMenuCommand command)  
{  
    ISequenceDiagram sequenceDiagram =   
         Context.CurrentDiagram as ISequenceDiagram;  
    if (sequenceDiagram == null) return;  
    // Get the diagram's interaction:  
    IInteraction interaction = sequenceDiagram.Interaction;  
    // A new sequence diagram might have no interaction:  
    if (interaction == null)  
    {  
       // Get the home package or model of the diagram:  
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();  
       interaction = parentPackage.CreateInteraction();  
       // Display the interaction on the sequence diagram:  
       sequenceDiagram.Bind(interaction);  
    }   
```  
  
## <a name="updating-an-interaction-and-its-layout"></a>Aktualisieren einer Interaktion und des Layouts  
 Bei der Aktualisierung einer Interaktion beenden Sie den Vorgang immer durch Aktualisieren des Layouts mit einer der folgenden Methoden:  
  
- `ISequenceDiagram.UpdateShapePositions()` Passt die Positionen von kürzlich eingefügten oder verschobenen Formen und der benachbarten Formen an.  
  
- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` zeichnet das gesamte Diagramm neu. Sie können den Parameter verwenden, um die Neupositionierung von Lebenslinien, Meldungen oder beides anzugeben.  
  
  Dies ist besonders wichtig, wenn Sie neue Elemente einfügen oder vorhandene Elemente verschieben. Sie befinden sich dann erst an den korrekten Positionen im Diagramm, wenn Sie eine dieser Operationen ausgeführt haben. Sie müssen nur eine dieser Operationen am Ende einer Reihe von Änderungen aufrufen.  
  
  Um den Benutzer nicht zu vewirren, der nach Ihrem Befehl eine Aktion zum Rückgängig machen ausführt, verwenden Sie eine `ILinkedUndoTransaction`, um die Änderungen einzuschließen, und die endgültige `Layout()`- oder `UpdateShapePositions()`-Operation. Zum Beispiel:  
  
```  
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))  
{  
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);  
  Diagram.UpdateShapePositions();  
  transaction.Commit();  
}  
```  
  
 Zum Verwenden einer `ILinkedUndoTransaction` müssen Sie diese Deklaration in der Klasse vornehmen:  
  
```  
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }  
```  
  
 Weitere Informationen finden Sie unter [Link UML-modellaktualisierungen mithilfe von Transaktionen](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
## <a name="building-an-interaction"></a>Erstellen einer Interaktion  
  
### <a name="to-create-lifelines"></a>So erstellen Sie Lebenslinien  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
```  
  
 Eine Lebenslinie stellt ein verbindungsfähiges Element dar, d. h. eine Instanz eines Typs dar. Wenn die Interaktion beispielsweise dazu verwendet wird, anzuzeigen, wie eine Komponente eingehende Meldungen an die internen Bestandteile delegiert, können die Lebenslinien Anschlüsse und Bestandteile der Komponente darstellen:  
  
```  
foreach (IConnectableElement part in   
            component.Parts  
           .Concat<IConnectableElement>(component.OwnedPorts))  
{  
   ILifeline lifeline = interaction.CreateLifeline();  
   lifeline.Represents = part;  
}  
```  
  
 Auch wenn die Interaktion einen beliebigen Satz von Objekten anzeigt, können Sie eine Eigenschaft oder ein anderes `IConnectableElement` in der Interaktion selbst erstellen:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
IProperty property1 = interaction.CreateProperty();  
property1.Type = model.CreateInterface();  
property1.Type.Name = "Type 1";  
lifeline.Represents = property1;  
```  
  
 Als weitere Alternative können Sie den Namen und Typ einer Lebenslinie ohne Verknüpfung mit einem verbindungsfähigen Element festlegen:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
lifeline.Name = "c1";  
lifeline.SetInstanceType("Customer");  
System.Diagnostics.Debug.Assert(  
           lifeline.GetDisplayName() == "c1:Customer"  );  
```  
  
### <a name="to-create-messages"></a>So erstellen Sie Meldungen  
 Um eine Meldung zu erstellen, müssen Sie zu den Quell- und Ziel-Lebenslinien Einfügemarken festlegen. Zum Beispiel:  
  
```  
interaction.CreateMessage( sourceInsertionPoint,   
                           targetInsertionPoint,   
                           MessageKind.Complete,   
                           MessageSort.ASynchCall)  
```  
  
 So erstellen Sie eine Meldung, die eine nicht definierte Quelle oder ein nicht definiertes Ziel besitzt:  
  
```  
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);  
```  
  
 Es gibt verschiedene Meldungen, mit denen Sie Einfügemarken an allen wichtigen Punkten einer Lebenslinie festlegen können:  
  
|Methode zur Lebenslinie|Verwenden Sie sie, um sie an diesem Punkt einzufügen.|  
|-------------------------|------------------------------------|  
|`FindInsertionPointAtTop()`|Das obere Ende der Lebenslinie.|  
|`FindInsertionPointAtBottom()`|Das untere Ende der Lebenslinie.|  
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Ein Punkt unmittelbar nach der angegebenen Meldung.|  
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|Der Punkt kann sich auf der Lebenslinie oder auf einem übergeordneten Ausführungsspezifikationsblock befinden.|  
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Ein Punkt, der auf eine Interaktionsverwendung folgt.|  
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Ein Punkt, der auf ein kombiniertes Fragment folgt.|  
|`FindInsertionPoint(IExecutionSpecification block)`|Das obere Ende eines Ausführungsblocks.|  
|`FindInsertionPoint(IInteractionOperand fragment)`|Das obere Ende eines Operanden eines kombinierten Fragments.|  
  
 Achten Sie bei der Erstellung von Meldungen darauf, eine Definition einer Meldung zu vermeiden,  die sich mit einer anderen Meldung überschneidet.  
  
### <a name="to-create-combined-fragments-and-interaction-uses"></a>Erstellen von kombinierten Fragmenten und Interaktionsverwendungen  
 Sie können kombinierte Fragmente und Interaktionsverwendungen erstellen, indem Sie auf jeder Lebenslinie eine Einfügemarke angeben, die vom Element abgedeckt werden muss. Achten Sie darauf, das Angeben von Punktgruppen zu vermeiden, die sich mit einer vorhandenen Meldung oder einem vorhandenen Fragment überschneiden.  
  
```  
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,   
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
Interaction.CreateInteractionUse(  
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
```  
  
 Sie können auch ein kombiniertes Fragment erstellen, das einen vorhandenen Satz von Meldungen abdeckt. Die Meldungen müssen alle aus der gleichen Lebenslinie oder dem gleichen Ausführungsblock stammen.  
  
```  
ICombinedFragment cf = Interaction.CreateCombinedFragment(  
  InteractionOperatorKind.Loop,  
  Interaction.Lifelines.First().GetAllOutgoingMessages());  
```  
  
 Ein kombiniertes Fragment wird immer mit nur einem Operanden erstellt. Um einen neuen Operanden zu erstellen, müssen Sie den vorhandenen Operanden angeben, den Sie davor oder danach einfügen möchten, und ob Sie etwas dahinter oder davor eingefügt möchten:  
  
```  
// Create an additional operand before the first  
cf.CreateInteractionOperand(cf.Operands.First(), false);  
// Create an additional operand after the last:  
cf.CreateInteractionOperand(cf.Operands.Last(), true);  
```  
  
## <a name="troubleshooting"></a>Problembehandlung  
 Formen werden an falschen Positionen angezeigt, wenn Änderungen nicht mit einer `UpdateShapePositions()`- oder `Layout()`-Operation abgeschlossen werden.  
  
 Die meisten anderen Probleme entstehen durch falsch ausgerichtete Einfügemarken, sodass sich neue Meldungen oder Fragmente mit anderen überschneiden müssten. Symptome hierfür sind, dass keine Änderung ausgeführt oder eine Ausnahme ausgelöst wird. Die Ausnahme kann nicht ausgelöst werden, bis die `UpdateShapePositions()`- oder `Layout()`-Operation ausgeführt wird.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>   
 [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)   
 [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Definieren von validierungseinschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md)   
 [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md)
