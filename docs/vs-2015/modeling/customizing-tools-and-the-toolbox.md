---
title: Customizing Tools and the Toolbox | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
ms.assetid: 2a0d03d7-ebc6-4458-b9f4-d2cb8418a62d
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a5e2a46a2326c123d6b7b4e85fa29908ede9fc9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299326"
---
# <a name="customizing-tools-and-the-toolbox"></a>Anpassen der Tools und der Toolbox
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie müssen Toolboxelemente für die Elemente definieren, die die Benutzer ihren Modellen hinzufügen dürfen. Es gibt zwei Arten von Tools: Elementtools und Verbindungstools. Im generierten Designer kann ein Benutzer ein Elementtool auswählen, um Formen auf das Diagramm zu ziehen. Dann kann der Benutzer ein Verbindungstool auswählen, um die Verbindungen zwischen den Formen zu zeichnen. Im Allgemeinen können Benutzer mit Elementtools ihren Modellen Instanzen von Domänenklassen hinzufügen, und mit Verbindungstools können sie Instanzen von Domänenbeziehungen hinzufügen.

 In diesem Thema:

- [How the Toolbox is Defined](#ToolboxDef)

- [Anpassen von Elementtools](#customizing)

- [Creating Groups of Elements from a Tool](#groups)

- [Customizing Connection Tools](#connections)

## <a name="ToolboxDef"></a> How the toolbox is defined
 Erweitern Sie im DSL-Explorer den Knoten "Editor" und die darunter liegenden Knoten. Normalerweise wird eine Hierarchie wie die folgende angezeigt:

```

Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool

```

 In diesem Teil des DSL-Explorers können Sie folgende Aufgaben ausführen:

- Neue Registerkarten erstellen. Mit Registerkarten werden die Abschnittsüberschriften in der Toolbox definiert.

- Neue Tools erstellen.

- Kopieren Sie Tools, und fügen Sie sie ein.

- Tools in der Liste nach oben oder unten verschieben.

- Registerkarten und Tools löschen.

> [!IMPORTANT]
> Sie können in einem DSL-Explorer Elemente hinzufügen oder einfügen, indem Sie mit der rechten Maustaste auf die zweite übergeordnete Ebene klicken. For example, to add a tool, right-click the tab, and not the **Tools** node. To add a tab, right-click the **Editor** node.

 The **Toolbox Icon** property of every tool references a 16x16 bitmap file. These files are usually kept in the **Dsl\Resources** folder.

 The **Class** property of an element tool refers to a concrete domain class. Standardmäßig erstellt das Tool Instanzen dieser Klasse. Sie können jedoch Code schreiben, damit das Tool Gruppen von Elementen oder Elemente unterschiedlicher Typen erstellt.

 The **Connection Builder** property of a connection tool refers to a connection builder, which defines what types of elements the tool can connect, and what relationships it creates between them. Verbindungs-Generatoren werden im DSL-Explorer als Knoten definiert. Verbindungs-Generatoren werden automatisch erstellt, wenn Sie Domänenbeziehungen definieren, aber Sie können sie über Code anpassen.

#### <a name="to-add-a-tool-to-the-toolbox"></a>So fügen Sie der Toolbox ein Tool hinzu

1. Normalerweise erstellen Sie ein Elementtool, nachdem Sie eine Formklasse erstellt und einer Domänenklasse zugeordnet haben.

     Normalerweise erstellen Sie ein Konnektortool, nachdem Sie eine Konnektorklasse erstellt und einer Verweisbeziehung zugeordnet haben.

2. In DSL Explorer, expand the **Editor** node and the **Toolbox Tabs** node.

     Right-click a toolbox tab node, and then click **Add New Element Tool** or **Add New Connection Tool**.

3. Set the **Toolbox Icon** property to refer to a 16x16 bitmap.

     If you want to define a new icon, create a bitmap file in Solution Explorer in the **Dsl\Resources** folder. The file should have the following property values: **Build Action** = **Content**; **Copy to Output Directory** = **Do not copy**.

4. **For an element tool:** Set the **Class** property of the tool to refer to a concrete domain class that is mapped to a shape.

     **For a connector tool:** Set the **Connection Builder** property of the tool to one of the items that are offered in the drop-down list. Verbindungs-Generatoren werden automatisch erstellt, wenn Sie einen Konnektor einer Domänenbeziehung zuordnen. Wenn Sie gerade einen Konnektor erstellt haben, würden Sie normalerweise den zugehörigen Verbindungs-Generator auswählen.

5. Drücken Sie zum Testen der DSL F5 oder STRG+F5, und öffnen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eine Beispielmodelldatei. Das neue Tool sollte in der Toolbox aufgeführt sein. Ziehen Sie es auf das Diagramm, um zu überprüfen, ob es ein neues Element erstellt.

     Wenn das Tool nicht angezeigt wird, beenden Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In the Windows **Start** menu, run **Reset the Microsoft Visual Studio 2010 Experimental Instance**. On the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**Build** menu, click **Rebuild Solution**. Wiederholen Sie dann den DSL-Test.

## <a name="customizing"></a> Customizing Element Tools
 Standardmäßig erstellt das Tool eine Instanz der angegebenen Klasse. Sie haben jedoch zwei Optionen, dies zu ändern:

- Definieren Sie Direktiven für Elementzusammenführungen für andere Klassen, sodass sie neue Instanzen dieser Klasse akzeptieren und weitere Links erstellen können, wenn ein neues Element erstellt wird. Sie können beispielsweise zulassen, dass ein Benutzer einem anderen Element einen Kommentar hinzufügt und auf diese Weise einen Verweislink zwischen beiden erstellt.

     Diese Anpassungen haben auch Auswirkungen darauf, was geschieht, wenn der Benutzer ein Element einfügt oder per Drag &amp; Drop ergänzt.

     For more information, see [Customizing Element Creation and Movement](../modeling/customizing-element-creation-and-movement.md).

- Schreiben Sie Code, um das Tool so anzupassen, dass es Gruppen von Elementen erstellen kann. Das Tool wird von Methoden in "ToolboxHelper.cs" initialisiert, die Sie überschreiben können. For more information, see [Creating Groups of Elements from a Tool](#groups).

## <a name="groups"></a> Creating Groups of Elements from a Tool
 Jedes Elementtool enthält einen Prototyp der Elemente, die es erstellen soll. Standardmäßig erstellt jedes Elementtool ein Element. Es ist jedoch auch möglich, eine Gruppe verknüpfter Objekte mit einem Tool zu erstellen. Dazu initialisieren Sie das Tool mit einem <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>, der verknüpfte Elemente enthält.

 Das folgende Beispiel stammt aus DSL und enthält einen Typ "Transistor". Jeder Transistor weist drei benannte Terminals auf. Das Elementtool für Transistoren speichert einen Prototyp, der vier Modellelemente und drei Beziehungslinks enthält. Wenn der Benutzer das Tool auf das Diagramm zieht, wird der Prototyp instanziiert und mit dem Modellstamm verknüpft.

 This code overrides a method that is defined in **Dsl\GeneratedCode\ToolboxHelper.cs**.

 For more information about customizing the model by using program code, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }

```

## <a name="connections"></a> Customizing Connection Tools
 Üblicherweise erstellen Sie ein Elementtool, wenn Sie eine neue Konnektorklasse erstellen. Alternativ können Sie ein Tool überladen, indem Sie den Beziehungstyp durch die Typen an den beiden Enden bestimmen lassen. Beispielsweise könnten Sie ein Verbindungstool erstellen, das Person-Person- und Person-Stadt-Beziehungen erstellen kann.

 Verbindungstools rufen Verbindungs-Generatoren auf. Verwenden Sie Verbindungs-Generatoren, um anzugeben, wie Benutzer Elemente im generierten Designer verknüpfen können. Mit Verbindungs-Generatoren werden die Elemente angegeben, die verknüpft werden können. Zudem wird die Art von Link bestimmt, der zwischen den Elementen erstellt werden kann.

 Wenn Sie eine Verweisbeziehung zwischen Domänenklassen erstellen, wird automatisch ein Verbindungs-Generator erstellt. Sie können diesen Verbindungs-Generator verwenden, wenn Sie ein Verbindungstool zuordnen. For more information about how to create connection tools, see [Configuring the Toolbox](../modeling/customizing-tools-and-the-toolbox.md).

 Sie können den standardmäßigen Verbindungs-Generator so ändern, dass er mit einem anderen Bereich von Quell- und Zieltypen verwendet werden kann und unterschiedliche Typen von Beziehungen erstellen kann.

 Darüber hinaus können Sie benutzerdefinierten Code für Verbindungs-Generatoren schreiben, um die Quell- und Zielklassen für die Verbindung anzugeben, den Typ der herzustellenden Verbindung zu definieren und Aktionen im Zusammenhang mit der Verbindungserstellung auszuführen.

### <a name="the-structure-of-connection-builders"></a>Struktur der Verbindungs-Generatoren
 Verbindungs-Generatoren enthalten mindestens eine Direktive für Linkverbindungen, um die Domänenbeziehung sowie die Quell- und Zielelemente anzugeben. For example, in the Task Flow solution template, you can see the **CommentReferencesSubjectsBuilder** in the **DSL Explorer**. This connection builder contains one link connect directive named **CommentReferencesSubjects**, which is mapped to the domain relationship **CommentReferencesSubjects**. Diese Direktive für Linkverbindungen enthält eine Direktive für die Quellrolle, die auf die `Comment`-Domänenklasse verweist, und eine Direktive für die Zielrolle, die auf die `FlowElement`-Domänenklasse verweist.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Verwenden von Verbindungs-Generatoren zum Beschränken von Quell- und Zielrollen
 Sie können mit Verbindungs-Generatoren das Auftreten bestimmter Klassen in der Quell- oder Zielrolle einer angegebenen Domänenbeziehung beschränken. Beispiel: Sie verfügen über eine Basisdomänenklasse, die eine Domänenbeziehung mit einer anderen Domänenklasse aufweist, Sie möchten jedoch nicht, dass alle abgeleiteten Klassen der Basisklasse in dieser Beziehung die gleiche Rolle haben. In the Task Flow solution, there are four concrete domain classes (**StartPoint**, **EndPoint**, **MergeBranch**, and **Synchronization**) that inherit directly from the abstract domain class **FlowElement**, and two concrete domain classes (**Task** and **ObjectInState**) that inherit indirectly from it. There is also a **Flow** reference relationship that takes **FlowElement** domain classes in both its source role and target role. However, an instance of an **EndPoint** domain class should not be the source of an instance of a **Flow** relationship, nor should an instance of a **StartPoint** class be the target of an instance of a **Flow** relationship. The **FlowBuilder** connection builder has a link connect directive named **Flow** that specifies which domain classes can play the source role (**Task**, **MergeBranch**, **StartPoint**, and **Synchronization**) and which can play the target role(**MergeBranch**, **Endpoint**, and **Synchronization**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Verbindungs-Generatoren mit mehreren Direktiven für Linkverbindungen
 Sie können einem Verbindungs-Generator mehr als eine Direktive für Linkverbindungen hinzufügen. This can help you hide some of the complexities of the domain model from users and keep the **Toolbox** from getting too cluttered. Sie können in einem Verbindungs-Generator für mehrere verschiedene Domänenbeziehungen Direktiven für Linkverbindungen hinzufügen. Sie sollten Domänenbeziehungen jedoch kombinieren, wenn sie annähernd die gleiche Funktion ausführen.

 In the Task Flow solution, the **Flow** connection tool is used to draw instances of both the **Flow** and the **ObjectFlow** domain relationships. The **FlowBuilder** connection builder has, in addition to the **Flow** link connect directive described earlier, two link connect directives named **ObjectFlow**. These directives specify that an instance of an **ObjectFlow** relationship may be drawn between instances of the **ObjectInState** domain class, or from an instance of an **ObjectInState** to an instance of a **Task**, but not between two instances of a **Task**, or from an instance of a **Task** to an instance of an **ObjectInState**. However, an instance of a **Flow** relationship may be drawn between two instances of a **Task**. If you compile and run the Task Flow solution, you can see that drawing a **Flow** from an instance of an **ObjectInState** to an instance of a **Task** creates an instance of an **ObjectFlow**, but drawing a **Flow** between two instances of a **Task** creates an instance of a **Flow**.

### <a name="custom-code-for-connection-builders"></a>Benutzerdefinierter Code für Verbindungs-Generatoren
 Es gibt vier Kontrollkästchen auf der Benutzeroberfläche, mit denen die unterschiedlichen Typen von Anpassungen der Verbindungs-Generatoren definiert werden:

- the **Custom accept** check box on a source or target role directive

- the **Custom connect** check box on a source or target role directive

- the **Uses custom connect** check box on a connect directive

- the **Is Custom** property of the connection builder

  Für diese Anpassungen müssen Sie Programmcode angeben. Sie können herausfinden, welcher Code erforderlich ist, indem Sie eines dieser Kontrollkästchen aktivieren, auf "Alle Vorlagen transformieren" klicken und dann die Projektmappe erstellen. Ein Fehlerbericht wird erstellt. Doppelklicken Sie auf den Fehlerbericht, um einen Kommentar zu lesen, der den hinzuzufügenden Code erläutert.

> [!NOTE]
> Erstellen Sie zum Hinzufügen von benutzerdefiniertem Code eine partielle Klassendefinition in einer Codedatei, die nicht zu den Codedateien in den Ordnern "GeneratedCode" gehört. Damit Ihre Arbeit nicht verloren geht, sollten Sie die generierten Codedateien nicht bearbeiten. For more information, see [Overriding and Extending the Generated Classes](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Erstellen von benutzerdefiniertem Verbindungscode
 In each link connect directive, the **Source role directives** tab defines from what types you can drag. Similarly, the **Target role directives** tab defines to what types you can drag. For each type, you can further specify whether to allow the connection (for that link connect directive) by setting the **Custom Accept** flag and then supplying the extra code.

 Darüber hinaus können Sie anpassen, was geschieht, wenn die Verbindung hergestellt wird. Sie können beispielsweise nur den Fall anpassen, wenn das Ziehen in eine oder aus einer bestimmten Klasse erfolgt. Sie können aber auch alle Fälle, für die eine Direktive für Linkverbindungen gilt, oder den gesamten FlowBuilder-Verbindungs-Generator anpassen. Für jede dieser Optionen können Sie benutzerdefinierte Flags auf der entsprechenden Ebene festlegen. Wenn Sie alle Vorlagen transformieren und die Projektmappe erstellen, weisen Sie Fehlermeldungen auf Kommentare im generierten Code hin. In diesen Kommentaren werden die erforderlichen Angaben identifiziert.

 Im Komponentendiagrammbeispiel wurde der Verbindungs-Generator für die Domänenbeziehung "Verbindung" angepasst, um die zwischen Ports möglichen Verbindungen zu beschränken. Die folgende Abbildung zeigt, dass Sie nur Verbindungen von `OutPort`-Elementen mit `InPort`-Elementen herstellen können. Zudem können Sie Komponenten ineinander schachteln.

 **Connection Coming in to an OutPort from a Nested Component**

 ![Connection Builder](../modeling/media/connectionbuilder-3.png "ConnectionBuilder_3")

 Daher könnten Sie angeben, dass eine Verbindung aus einer geschachtelten Komponente mit "OutPort" zulässig ist. To specify such a connection, you set **Uses Custom Accept** on the **InPort** type as source role and the **OutPort** type as target role in the **DSL Details** window as shown in the following illustrations:

 **Link Connect Directive in DSL Explorer**

 ![Connection builder image](../modeling/media/connectionbuilder-4a.png "ConnectionBuilder_4a")

 **Link Connect Directive in DSL Details Window**

 ![](../modeling/media/connectionbuilder-4b.png "ConnectionBuilder_4b")

 Dann müssen Sie die Methoden in der ConnectionBuilder-Klasse angeben:

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts…
```

 For more information about customizing the model by using program code, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Sie können ähnlichen Code verwenden, um beispielsweise zu verhindern, dass die Benutzer Schleifen mit Links zwischen übergeordneten und untergeordneten Elementen erstellen. Diese Beschränkungen gelten als fest, da sie von den Benutzern zu keinem Zeitpunkt verletzt werden können. Sie können auch "weiche" Überprüfungen einrichten, die die Benutzer vorübergehend mit ungültigen Konfigurationen, die nicht gespeichert werden, umgehen können.

### <a name="good-practice-in-defining-connection-builders"></a>Empfehlungen für die Definition von Verbindungs-Generatoren
 Sie sollten einen Verbindungs-Generator definieren, um unterschiedliche Typen von Beziehungen zu erstellen, wenn sie konzeptionell verwandt sind. Im Beispiel des Aufgabenablaufs verwenden Sie einen Generator, um die Abläufe zwischen Aufgaben und zwischen Aufgaben und Objekten zu erstellen. Es kann jedoch verwirrend sein, den gleichen Generator für Beziehungen zwischen Kommentaren und Aufgaben zu verwenden.

 Wenn Sie einen Verbindungs-Generator für mehrere Typen von Beziehungen erstellen, sollten Sie sicherstellen, dass er nicht zu mehr als einem Typ eines Paars von Quell- und Zielobjekten passt. Andernfalls können sich unerwartete Ergebnisse ergeben.

 Sie verwenden benutzerdefinierten Code, um feste Beschränkungen anzuwenden. Sie sollten aber überlegen, ob die Benutzer vorübergehend ungültige Verbindungen erstellen dürfen. In dem Fall können Sie die Beschränkungen so ändern, dass die Verbindungen erst überprüft werden, wenn die Benutzer die Änderungen speichern möchten.

## <a name="see-also"></a>Siehe auch
 [Customizing Element Creation and Movement](../modeling/customizing-element-creation-and-movement.md) [Customizing Copy Behavior](../modeling/customizing-copy-behavior.md) [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md) [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md)
