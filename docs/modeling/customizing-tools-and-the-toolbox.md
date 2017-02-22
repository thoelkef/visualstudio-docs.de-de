---
title: "Anpassen der Tools und der Toolbox | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.selectiondialog"
  - "vs.dsltools.dsldesigner.selecticondialog"
  - "vs.dsltools.dsldesigner.selectcursordialog"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Toolbox"
ms.assetid: 2a0d03d7-ebc6-4458-b9f4-d2cb8418a62d
caps.latest.revision: 26
caps.handback.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Anpassen der Tools und der Toolbox
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie müssen Toolboxelemente für die Elemente definieren, die die Benutzer ihren Modellen hinzufügen dürfen. Es gibt zwei Arten von Tools: Elementtools und Verbindungstools. Im generierten Designer kann ein Benutzer ein Elementtool auswählen, um Formen auf das Diagramm zu ziehen. Dann kann der Benutzer ein Verbindungstool auswählen, um die Verbindungen zwischen den Formen zu zeichnen. Im Allgemeinen können Benutzer mit Elementtools ihren Modellen Instanzen von Domänenklassen hinzufügen, und mit Verbindungstools können sie Instanzen von Domänenbeziehungen hinzufügen.  
  
 In diesem Thema:  
  
-   [Definition der Toolbox](#ToolboxDef)  
  
-   [Anpassen von Elementtools](#customizing)  
  
-   [Erstellen von Gruppen von Elementen über ein Tool](#groups)  
  
-   [Anpassen von Verbindungstools](#connections)  
  
##  <a name="ToolboxDef"></a> Definition der Toolbox  
 Erweitern Sie im DSL\-Explorer den Knoten "Editor" und die darunter liegenden Knoten. Normalerweise wird eine Hierarchie wie die folgende angezeigt:  
  
```  
  
Editor  
     Toobox Tabs  
        MyDsl          //a tab  
           Tools  
               ExampleElement      // an element tool  
               ExampleRelationship // a connection tool  
  
```  
  
 In diesem Teil des DSL\-Explorers können Sie folgende Aufgaben ausführen:  
  
-   Neue Registerkarten erstellen. Mit Registerkarten werden die Abschnittsüberschriften in der Toolbox definiert.  
  
-   Neue Tools erstellen.  
  
-   Kopieren Sie Tools, und fügen Sie sie ein.  
  
-   Tools in der Liste nach oben oder unten verschieben.  
  
-   Registerkarten und Tools löschen.  
  
> [!IMPORTANT]
>  Sie können in einem DSL\-Explorer Elemente hinzufügen oder einfügen, indem Sie mit der rechten Maustaste auf die zweite übergeordnete Ebene klicken. Klicken Sie beispielsweise zum Hinzufügen eines Tools mit der rechten Maustaste auf die Registerkarte und nicht auf den Knoten **Tools**. Klicken Sie zum Hinzufügen einer Registerkarte mit der rechten Maustaste auf den Knoten **Editor**.  
  
 Die Eigenschaft **Toolboxsymbol** eines Tools verweist auf eine 16x16\-Bitmapdatei. Diese Dateien befinden sich normalerweise im Ordner **Dsl\\Resources**.  
  
 Die Eigenschaft **Klasse** eines Elementtools verweist auf eine konkrete Domänenklasse. Standardmäßig erstellt das Tool Instanzen dieser Klasse. Sie können jedoch Code schreiben, damit das Tool Gruppen von Elementen oder Elemente unterschiedlicher Typen erstellt.  
  
 Die Eigenschaft **Verbindungs\-Generator** eines Verbindungstools verweist auf einen Verbindungs\-Generator, mit dem definiert wird, welche Typen von Elementen das Tool verbinden kann und welche Beziehungen zwischen den Elementen erstellt werden. Verbindungs\-Generatoren werden im DSL\-Explorer als Knoten definiert. Verbindungs\-Generatoren werden automatisch erstellt, wenn Sie Domänenbeziehungen definieren, aber Sie können sie über Code anpassen.  
  
#### So fügen Sie der Toolbox ein Tool hinzu  
  
1.  Normalerweise erstellen Sie ein Elementtool, nachdem Sie eine Formklasse erstellt und einer Domänenklasse zugeordnet haben.  
  
     Normalerweise erstellen Sie ein Konnektortool, nachdem Sie eine Konnektorklasse erstellt und einer Verweisbeziehung zugeordnet haben.  
  
2.  Erweitern Sie im DSL\-Explorer den Knoten **Editor** und den Knoten **Toolboxregisterkarten**.  
  
     Klicken Sie mit der rechten Maustaste auf einen Toolboxregisterkarten\-Knoten, und klicken Sie dann auf **Neues Elementtool hinzufügen** oder **Neues Verbindungstool hinzufügen**.  
  
3.  Legen Sie für die Eigenschaft **Toolboxsymbol** fest, dass sie auf eine 16x16\-Bitmapdatei verweist.  
  
     Wenn Sie ein neues Symbol definieren möchten, erstellen Sie im Projektmappen\-Explorer im Ordner **Dsl\\Resources** eine neue Bitmapdatei. Die Datei sollte die folgenden Eigenschaftenwerte aufweisen: **Buildvorgang** \= **Inhalt**, **In Ausgabeverzeichnis kopieren** \= **Nicht kopieren**.  
  
4.  **Für ein Elementtool:** Legen Sie die Eigenschaft **Klasse** des Tools so fest, dass sie auf eine konkrete Domänenklasse verweist, die einer Form zugeordnet ist.  
  
     **Für ein Konnektortool:** Legen Sie die Eigenschaft **Verbindungs\-Generator** des Tools auf eines der Elemente aus der Dropdownliste fest. Verbindungs\-Generatoren werden automatisch erstellt, wenn Sie einen Konnektor einer Domänenbeziehung zuordnen. Wenn Sie gerade einen Konnektor erstellt haben, würden Sie normalerweise den zugehörigen Verbindungs\-Generator auswählen.  
  
5.  Drücken Sie zum Testen der DSL F5 oder STRG\+F5, und öffnen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eine Beispielmodelldatei. Das neue Tool sollte in der Toolbox aufgeführt sein. Ziehen Sie es auf das Diagramm, um zu überprüfen, ob es ein neues Element erstellt.  
  
     Wenn das Tool nicht angezeigt wird, beenden Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Führen Sie im Windows\-Menü **Start** den Befehl **Experimentelle Instanz von Microsoft Visual Studio 2010 zurücksetzen** aus. Klicken Sie im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Menü **Erstellen** auf **Projektmappe neu erstellen**. Wiederholen Sie dann den DSL\-Test.  
  
##  <a name="customizing"></a> Anpassen von Elementtools  
 Standardmäßig erstellt das Tool eine Instanz der angegebenen Klasse. Sie haben jedoch zwei Optionen, dies zu ändern:  
  
-   Definieren Sie Direktiven für Elementzusammenführungen für andere Klassen, sodass sie neue Instanzen dieser Klasse akzeptieren und weitere Links erstellen können, wenn ein neues Element erstellt wird. Sie können beispielsweise zulassen, dass ein Benutzer einem anderen Element einen Kommentar hinzufügt und auf diese Weise einen Verweislink zwischen beiden erstellt.  
  
     Diese Anpassungen haben auch Auswirkungen darauf, was geschieht, wenn der Benutzer ein Element einfügt oder per Drag & Drop ergänzt.  
  
     Weitere Informationen finden Sie unter [Anpassen der Elementerstellung und \-verschiebung](../modeling/customizing-element-creation-and-movement.md).  
  
-   Schreiben Sie Code, um das Tool so anzupassen, dass es Gruppen von Elementen erstellen kann. Das Tool wird von Methoden in "ToolboxHelper.cs" initialisiert, die Sie überschreiben können. Weitere Informationen finden Sie unter [Erstellen von Gruppen von Elementen über ein Tool](#groups).  
  
##  <a name="groups"></a> Erstellen von Gruppen von Elementen über ein Tool  
 Jedes Elementtool enthält einen Prototyp der Elemente, die es erstellen soll. Standardmäßig erstellt jedes Elementtool ein Element. Es ist jedoch auch möglich, eine Gruppe verknüpfter Objekte mit einem Tool zu erstellen. Dazu initialisieren Sie das Tool mit einem <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>, der verknüpfte Elemente enthält.  
  
 Das folgende Beispiel stammt aus DSL und enthält einen Typ "Transistor". Jeder Transistor weist drei benannte Terminals auf. Das Elementtool für Transistoren speichert einen Prototyp, der vier Modellelemente und drei Beziehungslinks enthält. Wenn der Benutzer das Tool auf das Diagramm zieht, wird der Prototyp instanziiert und mit dem Modellstamm verknüpft.  
  
 Dieser Code überschreibt eine Methode, die in **Dsl\\GeneratedCode\\ToolboxHelper.cs** definiert ist.  
  
 Weitere Informationen zum Anpassen des Modells mit Programmcode finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
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
  
##  <a name="connections"></a> Anpassen von Verbindungstools  
 Üblicherweise erstellen Sie ein Elementtool, wenn Sie eine neue Konnektorklasse erstellen. Alternativ können Sie ein Tool überladen, indem Sie den Beziehungstyp durch die Typen an den beiden Enden bestimmen lassen. Beispielsweise könnten Sie ein Verbindungstool erstellen, das Person\-Person\- und Person\-Stadt\-Beziehungen erstellen kann.  
  
 Verbindungstools rufen Verbindungs\-Generatoren auf. Verwenden Sie Verbindungs\-Generatoren, um anzugeben, wie Benutzer Elemente im generierten Designer verknüpfen können. Mit Verbindungs\-Generatoren werden die Elemente angegeben, die verknüpft werden können. Zudem wird die Art von Link bestimmt, der zwischen den Elementen erstellt werden kann.  
  
 Wenn Sie eine Verweisbeziehung zwischen Domänenklassen erstellen, wird automatisch ein Verbindungs\-Generator erstellt. Sie können diesen Verbindungs\-Generator verwenden, wenn Sie ein Verbindungstool zuordnen. Weitere Informationen zum Erstellen von Verbindungstools finden Sie unter [Configuring the Toolbox](../modeling/customizing-tools-and-the-toolbox.md).  
  
 Sie können den standardmäßigen Verbindungs\-Generator so ändern, dass er mit einem anderen Bereich von Quell\- und Zieltypen verwendet werden kann und unterschiedliche Typen von Beziehungen erstellen kann.  
  
 Darüber hinaus können Sie benutzerdefinierten Code für Verbindungs\-Generatoren schreiben, um die Quell\- und Zielklassen für die Verbindung anzugeben, den Typ der herzustellenden Verbindung zu definieren und Aktionen im Zusammenhang mit der Verbindungserstellung auszuführen.  
  
### Struktur der Verbindungs\-Generatoren  
 Verbindungs\-Generatoren enthalten mindestens eine Direktive für Linkverbindungen, um die Domänenbeziehung sowie die Quell\- und Zielelemente anzugeben. Beispielsweise sehen Sie in der Projektmappenvorlage "Aufgabenablauf" im **DSL\-Explorer** "CommentReferencesSubjectsBuilder". Dieser Verbindungs\-Generator enthält eine Direktive für Linkverbindungen namens **CommentReferencesSubjects**, die der Domänenbeziehung "CommentReferencesSubjects" zugeordnet ist. Diese Direktive für Linkverbindungen enthält eine Direktive für die Quellrolle, die auf die `Comment`\-Domänenklasse verweist, und eine Direktive für die Zielrolle, die auf die `FlowElement`\-Domänenklasse verweist.  
  
### Verwenden von Verbindungs\-Generatoren zum Beschränken von Quell\- und Zielrollen  
 Sie können mit Verbindungs\-Generatoren das Auftreten bestimmter Klassen in der Quell\- oder Zielrolle einer angegebenen Domänenbeziehung beschränken. Beispiel: Sie verfügen über eine Basisdomänenklasse, die eine Domänenbeziehung mit einer anderen Domänenklasse aufweist, Sie möchten jedoch nicht, dass alle abgeleiteten Klassen der Basisklasse in dieser Beziehung die gleiche Rolle haben. In der Projektmappe "Aufgabenablauf" gibt es vier konkrete Domänenklassen \("StartPoint", "EndPoint", "MergeBranch" und "Synchronization"\), die direkt von der abstrakten FlowElement\-Domänenklasse erben, sowie zwei konkrete Domänenklassen \("Task" und "ObjectInState"\), die indirekt davon erben. Außerdem gibt es eine Flow\-Verweisbeziehung, die in der Quell\- und Zielrolle FlowElement\-Domänenklassen akzeptiert. Jedoch sollte eine Instanz einer EndPoint\-Domänenklasse nicht die Quelle einer Instanz einer Flow\-Beziehung sein. Auch sollte eine Instanz der StartPoint\-Klasse nicht das Ziel einer Instanz einer Flow\-Beziehung sein. Der FlowBuilder\-Verbindungs\-Generator weist eine Direktive für Linkverbindungen mit dem Namen "Flow" auf, die angibt, welche Domänenklassen die Quellrolle übernehmen können \("Task", "MergeBranch", "StartPoint" und "Synchronization"\) und welche die Zielrolle übernehmen können \("MergeBranch", "Endpoint" und "Synchronization"\).  
  
### Verbindungs\-Generatoren mit mehreren Direktiven für Linkverbindungen  
 Sie können einem Verbindungs\-Generator mehr als eine Direktive für Linkverbindungen hinzufügen. Dadurch gestalten Sie für die Benutzer das Domänenmodell und die **Toolbox** übersichtlicher. Sie können in einem Verbindungs\-Generator für mehrere verschiedene Domänenbeziehungen Direktiven für Linkverbindungen hinzufügen. Sie sollten Domänenbeziehungen jedoch kombinieren, wenn sie annähernd die gleiche Funktion ausführen.  
  
 In der Projektmappe "Aufgabenablauf" wird das Flow\-Verbindungstool verwendet, um Instanzen der Flow\- und ObjectFlow\-Domänenbeziehungen zu zeichnen. Der FlowBuilder\-Verbindungs\-Generator weist zusätzlich zur bereits erläuterten Direktive für Linkverbindungen namens "Flow" zwei Direktiven für Linkverbindungen namens "ObjectFlow" auf. Mit diesen Direktiven wird angegeben, dass eine Instanz einer ObjectFlow\-Beziehung zwischen Instanzen der ObjectInState\-Domänenklasse oder von einer ObjectInState\-Instanz zu einer Task\-Instanz gezeichnet werden kann, nicht aber zwischen zwei Task\-Instanzen oder von einer Task\-Instanz zu einer ObjectInState\-Instanz. Allerdings kann eine Instanz einer Flow\-Beziehung zwischen zwei Task\-Instanzen gezeichnet werden. Wenn Sie die Projektmappe "Aufgabenablauf" kompilieren und ausführen, erkennen Sie, dass das Zeichnen einer Flow\-Instanz von einer ObjectInState\- zu einer Task\-Instanz eine ObjectFlow\-Instanz erzeugt. Mit einer Flow\-Instanz zwischen zwei Task\-Instanzen wird dagegen eine Flow\-Instanz erstellt.  
  
### Benutzerdefinierter Code für Verbindungs\-Generatoren  
 Es gibt vier Kontrollkästchen auf der Benutzeroberfläche, mit denen die unterschiedlichen Typen von Anpassungen der Verbindungs\-Generatoren definiert werden:  
  
-   Kontrollkästchen **Benutzerdefiniert Akzeptieren** für die Direktive der Quell\- und Zielrolle  
  
-   Kontrollkästchen **Benutzerdefiniert Verbinden** für die Direktive der Quell\- und Zielrolle  
  
-   Kontrollkästchen **Verwendet benutzerdefiniertes Verbinden** für eine Verbindungsdirektive  
  
-   Eigenschaft **Ist benutzerdefiniert** des Verbindungs\-Generators  
  
 Für diese Anpassungen müssen Sie Programmcode angeben. Sie können herausfinden, welcher Code erforderlich ist, indem Sie eines dieser Kontrollkästchen aktivieren, auf "Alle Vorlagen transformieren" klicken und dann die Projektmappe erstellen. Ein Fehlerbericht wird erstellt. Doppelklicken Sie auf den Fehlerbericht, um einen Kommentar zu lesen, der den hinzuzufügenden Code erläutert.  
  
> [!NOTE]
>  Erstellen Sie zum Hinzufügen von benutzerdefiniertem Code eine partielle Klassendefinition in einer Codedatei, die nicht zu den Codedateien in den Ordnern "GeneratedCode" gehört. Damit Ihre Arbeit nicht verloren geht, sollten Sie die generierten Codedateien nicht bearbeiten. Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).  
  
#### Erstellen von benutzerdefiniertem Verbindungscode  
 In jeder Direktive für Linkverbindungen definiert die Registerkarte **Direktiven für die Quellrollen** welche Typen Sie verwenden können. Die Registerkarte **Direktiven für die Zielrollen** definiert ebenfalls, welche Typen Sie verwenden können. Für jeden Typ können Sie zudem angeben, ob die Verbindung \(für diese Direktive für Linkverbindungen\) zugelassen werden soll, indem Sie das Flag **Benutzerdefiniert Akzeptieren** festlegen und dann zusätzlichen Code angeben.  
  
 Darüber hinaus können Sie anpassen, was geschieht, wenn die Verbindung hergestellt wird. Sie können beispielsweise nur den Fall anpassen, wenn das Ziehen in eine oder aus einer bestimmten Klasse erfolgt. Sie können aber auch alle Fälle, für die eine Direktive für Linkverbindungen gilt, oder den gesamten FlowBuilder\-Verbindungs\-Generator anpassen. Für jede dieser Optionen können Sie benutzerdefinierte Flags auf der entsprechenden Ebene festlegen. Wenn Sie alle Vorlagen transformieren und die Projektmappe erstellen, weisen Sie Fehlermeldungen auf Kommentare im generierten Code hin. In diesen Kommentaren werden die erforderlichen Angaben identifiziert.  
  
 Im Komponentendiagrammbeispiel wurde der Verbindungs\-Generator für die Domänenbeziehung "Verbindung" angepasst, um die zwischen Ports möglichen Verbindungen zu beschränken. Die folgende Abbildung zeigt, dass Sie nur Verbindungen von `OutPort`\-Elementen mit `InPort`\-Elementen herstellen können. Zudem können Sie Komponenten ineinander schachteln.  
  
 **Eingehende Verbindung für "OutPort" aus einer geschachtelten Komponente**  
  
 ![Verbindungsgenerator](../modeling/media/connectionbuilder_3.png "ConnectionBuilder\_3")  
  
 Daher könnten Sie angeben, dass eine Verbindung aus einer geschachtelten Komponente mit "OutPort" zulässig ist. Zur Angabe einer solchen Verbindung legen Sie im Fenster **DSL\-Details** die Option **Verwendet benutzerdefiniertes Akzeptieren** für den Typ **InPort** als Quellrolle und den Typ **OutPort** als Zielrolle fest, wie in den folgenden Abbildungen veranschaulicht:  
  
 **Direktive für Linkverbindungen im DSL\-Explorer**  
  
 ![Verbindungsgenerator&#45;Abbild](../modeling/media/connectionbuilder_4a.png "ConnectionBuilder\_4a")  
  
 **Direktive für Linkverbindungen im Fenster "DSL\-Details"**  
  
 ![](../modeling/media/connectionbuilder_4b.png "ConnectionBuilder\_4b")  
  
 Dann müssen Sie die Methoden in der ConnectionBuilder\-Klasse angeben:  
  
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
  
 Weitere Informationen zum Anpassen des Modells mit Programmcode finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Sie können ähnlichen Code verwenden, um beispielsweise zu verhindern, dass die Benutzer Schleifen mit Links zwischen übergeordneten und untergeordneten Elementen erstellen. Diese Beschränkungen gelten als fest, da sie von den Benutzern zu keinem Zeitpunkt verletzt werden können. Sie können auch "weiche" Überprüfungen einrichten, die die Benutzer vorübergehend mit ungültigen Konfigurationen, die nicht gespeichert werden, umgehen können.  
  
### Empfehlungen für die Definition von Verbindungs\-Generatoren  
 Sie sollten einen Verbindungs\-Generator definieren, um unterschiedliche Typen von Beziehungen zu erstellen, wenn sie konzeptionell verwandt sind. Im Beispiel des Aufgabenablaufs verwenden Sie einen Generator, um die Abläufe zwischen Aufgaben und zwischen Aufgaben und Objekten zu erstellen. Es kann jedoch verwirrend sein, den gleichen Generator für Beziehungen zwischen Kommentaren und Aufgaben zu verwenden.  
  
 Wenn Sie einen Verbindungs\-Generator für mehrere Typen von Beziehungen erstellen, sollten Sie sicherstellen, dass er nicht zu mehr als einem Typ eines Paars von Quell\- und Zielobjekten passt. Andernfalls können sich unerwartete Ergebnisse ergeben.  
  
 Sie verwenden benutzerdefinierten Code, um feste Beschränkungen anzuwenden. Sie sollten aber überlegen, ob die Benutzer vorübergehend ungültige Verbindungen erstellen dürfen. In dem Fall können Sie die Beschränkungen so ändern, dass die Verbindungen erst überprüft werden, wenn die Benutzer die Änderungen speichern möchten.  
  
## Siehe auch  
 [Anpassen der Elementerstellung und \-verschiebung](../modeling/customizing-element-creation-and-movement.md)   
 [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md)   
 [Gewusst wie: Hinzufügen eines Drag & Drop\-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Circuit Diagrams sample DSL \(Schaltplanbeispiel in DSL, in englischer Sprache\)](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)