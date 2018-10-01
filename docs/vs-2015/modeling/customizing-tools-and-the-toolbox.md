---
title: Anpassen der Tools und der Toolbox | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
ms.assetid: 2a0d03d7-ebc6-4458-b9f4-d2cb8418a62d
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 97682059e90bac38b0b8b00492ff9fd50a36ffab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510741"
---
# <a name="customizing-tools-and-the-toolbox"></a>Anpassen der Tools und der Toolbox
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Anpassen von Tools und der Toolbox](https://docs.microsoft.com/visualstudio/modeling/customizing-tools-and-the-toolbox).  
  
Sie müssen Toolboxelemente für die Elemente definieren, die die Benutzer ihren Modellen hinzufügen dürfen. Es gibt zwei Arten von Tools: Elementtools und Verbindungstools. Im generierten Designer kann ein Benutzer ein Elementtool auswählen, um Formen auf das Diagramm zu ziehen. Dann kann der Benutzer ein Verbindungstool auswählen, um die Verbindungen zwischen den Formen zu zeichnen. Im Allgemeinen können Benutzer mit Elementtools ihren Modellen Instanzen von Domänenklassen hinzufügen, und mit Verbindungstools können sie Instanzen von Domänenbeziehungen hinzufügen.  
  
 In diesem Thema:  
  
-   [Die Definition der Toolbox](#ToolboxDef)  
  
-   [Anpassen von Elementtools](#customizing)  
  
-   [Erstellen von Gruppen von Elementen in einem Tool](#groups)  
  
-   [Anpassen von Verbindungstools](#connections)  
  
##  <a name="ToolboxDef"></a> Die Definition der toolbox  
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
  
-   Neue Registerkarten erstellen. Mit Registerkarten werden die Abschnittsüberschriften in der Toolbox definiert.  
  
-   Neue Tools erstellen.  
  
-   Kopieren Sie Tools, und fügen Sie sie ein.  
  
-   Tools in der Liste nach oben oder unten verschieben.  
  
-   Registerkarten und Tools löschen.  
  
> [!IMPORTANT]
>  Sie können in einem DSL-Explorer Elemente hinzufügen oder einfügen, indem Sie mit der rechten Maustaste auf die zweite übergeordnete Ebene klicken. Z. B. um ein Tool hinzuzufügen, mit der rechten Maustaste der Registerkarte ", und nicht die **Tools** Knoten. Zum Hinzufügen einer Registerkarte, Maustaste den **Editor** Knoten.  
  
 Die **Toolboxsymbol** Eigenschaft eines Tools verweist auf eine 16 x 16-Bitmap-Datei. Diese Dateien befinden sich normalerweise die **dsl\ressourcen** Ordner.  
  
 Die **Klasse** Eigenschaft eines Elementtools verweist auf eine konkrete Domänenklasse. Standardmäßig erstellt das Tool Instanzen dieser Klasse. Sie können jedoch Code schreiben, damit das Tool Gruppen von Elementen oder Elemente unterschiedlicher Typen erstellt.  
  
 Die **Verbindungsgenerator** Eigenschaft eines Verbindungstools verweist auf einen Verbindungs-Generator, der definiert, welche Arten von Elementen, die das Tool verbinden kann, und welche Beziehungen zwischen ihnen erstellt. Verbindungs-Generatoren werden im DSL-Explorer als Knoten definiert. Verbindungs-Generatoren werden automatisch erstellt, wenn Sie Domänenbeziehungen definieren, aber Sie können sie über Code anpassen.  
  
#### <a name="to-add-a-tool-to-the-toolbox"></a>So fügen Sie der Toolbox ein Tool hinzu  
  
1.  Normalerweise erstellen Sie ein Elementtool, nachdem Sie eine Formklasse erstellt und einer Domänenklasse zugeordnet haben.  
  
     Normalerweise erstellen Sie ein Konnektortool, nachdem Sie eine Konnektorklasse erstellt und einer Verweisbeziehung zugeordnet haben.  
  
2.  Erweitern Sie im DSL-Explorer die **Editor** Knoten und die **Toolboxregisterkarten** Knoten.  
  
     Mit der rechten Maustaste eines Toolboxregisterkarten-Knotens, und klicken Sie dann auf **neues Elementtool hinzufügen** oder **neues Verbindungswerkzeug hinzufügen**.  
  
3.  Legen Sie die **Toolboxsymbol** Eigenschaft zum Verweisen auf eine 16 x 16-Bitmap.  
  
     Wenn Sie ein neues Symbol definieren möchten, erstellen Sie eine Bitmapdatei im Projektmappen-Explorer die **dsl\ressourcen** Ordner. Die Datei sollte die folgenden Eigenschaftswerte enthalten: **Buildvorgang** = **Content**; **In Ausgabeverzeichnis kopieren** = **nicht kopieren**.  
  
4.  **Für ein Elementtool:** legen Sie die **Klasse** Eigenschaft des Tools für die auf eine konkrete Domänenklasse verweisen, die mit einer Form zugeordnet ist.  
  
     **Für ein konnektortool:** legen Sie die **Verbindungsgenerator** Eigenschaft des Tools auf eines der Elemente, die in der Dropdown Liste zur Verfügung stehen. Verbindungs-Generatoren werden automatisch erstellt, wenn Sie einen Konnektor einer Domänenbeziehung zuordnen. Wenn Sie gerade einen Konnektor erstellt haben, würden Sie normalerweise den zugehörigen Verbindungs-Generator auswählen.  
  
5.  Drücken Sie zum Testen der DSL F5 oder STRG+F5, und öffnen Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eine Beispielmodelldatei. Das neue Tool sollte in der Toolbox aufgeführt sein. Ziehen Sie es auf das Diagramm, um zu überprüfen, ob es ein neues Element erstellt.  
  
     Wenn das Tool nicht angezeigt wird, beenden Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In der Windows **starten** führen **Zurücksetzen der Microsoft Visual Studio 2010 experimentelle Instanz**. Auf der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **erstellen** Menü klicken Sie auf **Projektmappe neu erstellen**. Wiederholen Sie dann den DSL-Test.  
  
##  <a name="customizing"></a> Anpassen von Elementtools  
 Standardmäßig erstellt das Tool eine Instanz der angegebenen Klasse. Sie haben jedoch zwei Optionen, dies zu ändern:  
  
-   Definieren Sie Direktiven für Elementzusammenführungen für andere Klassen, sodass sie neue Instanzen dieser Klasse akzeptieren und weitere Links erstellen können, wenn ein neues Element erstellt wird. Sie können beispielsweise zulassen, dass ein Benutzer einem anderen Element einen Kommentar hinzufügt und auf diese Weise einen Verweislink zwischen beiden erstellt.  
  
     Diese Anpassungen haben auch Auswirkungen darauf, was geschieht, wenn der Benutzer ein Element einfügt oder per Drag & Drop ergänzt.  
  
     Weitere Informationen finden Sie unter [Anpassen der Elementerstellung und-Verschiebung](../modeling/customizing-element-creation-and-movement.md).  
  
-   Schreiben Sie Code, um das Tool so anzupassen, dass es Gruppen von Elementen erstellen kann. Das Tool wird von Methoden in "ToolboxHelper.cs" initialisiert, die Sie überschreiben können. Weitere Informationen finden Sie unter [Erstellen von Gruppen von Elementen in einem Tool](#groups).  
  
##  <a name="groups"></a> Erstellen von Gruppen von Elementen in einem Tool  
 Jedes Elementtool enthält einen Prototyp der Elemente, die es erstellen soll. Standardmäßig erstellt jedes Elementtool ein Element. Es ist jedoch auch möglich, eine Gruppe verknüpfter Objekte mit einem Tool zu erstellen. Dazu initialisieren Sie das Tool mit einem <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>, der verknüpfte Elemente enthält.  
  
 Das folgende Beispiel stammt aus DSL und enthält einen Typ "Transistor". Jeder Transistor weist drei benannte Terminals auf. Das Elementtool für Transistoren speichert einen Prototyp, der vier Modellelemente und drei Beziehungslinks enthält. Wenn der Benutzer das Tool auf das Diagramm zieht, wird der Prototyp instanziiert und mit dem Modellstamm verknüpft.  
  
 Dieser Code überschreibt eine Methode, die in definierten **Dsl\GeneratedCode\ToolboxHelper.cs**.  
  
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
 Üblicherweise erstellen Sie ein Elementtool, wenn Sie eine neue Konnektorklasse erstellen. Alternativ können Sie ein Tool überladen, indem Sie den Beziehungstyp durch die Typen an den beiden Enden bestimmen lassen. Beispielsweise könnten Sie ein Verbindungstool erstellen, das Person-Person- und Person-Stadt-Beziehungen erstellen kann.  
  
 Verbindungstools rufen Verbindungs-Generatoren auf. Verwenden Sie Verbindungs-Generatoren, um anzugeben, wie Benutzer Elemente im generierten Designer verknüpfen können. Mit Verbindungs-Generatoren werden die Elemente angegeben, die verknüpft werden können. Zudem wird die Art von Link bestimmt, der zwischen den Elementen erstellt werden kann.  
  
 Wenn Sie eine Verweisbeziehung zwischen Domänenklassen erstellen, wird automatisch ein Verbindungs-Generator erstellt. Sie können diesen Verbindungs-Generator verwenden, wenn Sie ein Verbindungstool zuordnen. Weitere Informationen über das Erstellen von Verbindungstools finden Sie unter [konfigurieren die Toolbox](../modeling/customizing-tools-and-the-toolbox.md).  
  
 Sie können den standardmäßigen Verbindungs-Generator so ändern, dass er mit einem anderen Bereich von Quell- und Zieltypen verwendet werden kann und unterschiedliche Typen von Beziehungen erstellen kann.  
  
 Darüber hinaus können Sie benutzerdefinierten Code für Verbindungs-Generatoren schreiben, um die Quell- und Zielklassen für die Verbindung anzugeben, den Typ der herzustellenden Verbindung zu definieren und Aktionen im Zusammenhang mit der Verbindungserstellung auszuführen.  
  
### <a name="the-structure-of-connection-builders"></a>Struktur der Verbindungs-Generatoren  
 Verbindungs-Generatoren enthalten mindestens eine Direktive für Linkverbindungen, um die Domänenbeziehung sowie die Quell- und Zielelemente anzugeben. Z. B. in der Projektmappenvorlage Aufgabenfluss können Sie sehen die **"commentreferencessubjectsbuilder"** in die **DSL-Explorer**. Dieser Verbindungs-Generator enthält eine Direktive für linkverbindungen namens **"commentreferencessubjects"**, die die domänenbeziehung zugeordnet **"commentreferencessubjects"**. Diese Direktive für Linkverbindungen enthält eine Direktive für die Quellrolle, die auf die `Comment`-Domänenklasse verweist, und eine Direktive für die Zielrolle, die auf die `FlowElement`-Domänenklasse verweist.  
  
### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Verwenden von Verbindungs-Generatoren zum Beschränken von Quell- und Zielrollen  
 Sie können mit Verbindungs-Generatoren das Auftreten bestimmter Klassen in der Quell- oder Zielrolle einer angegebenen Domänenbeziehung beschränken. Beispiel: Sie verfügen über eine Basisdomänenklasse, die eine Domänenbeziehung mit einer anderen Domänenklasse aufweist, Sie möchten jedoch nicht, dass alle abgeleiteten Klassen der Basisklasse in dieser Beziehung die gleiche Rolle haben. In der Projektmappe Aufgabenfluss, es gibt vier konkrete Domänenklassen (**"StartPoint"**, **Endpunkt**, **"mergebranch"**, und **Synchronisierung**), die direkt von der abstrakten Domänenklasse erben **FlowElement**, und zwei konkrete Domänenklassen (**Aufgabe** und **"objectinstate"**), erben Sie indirekt. Es gibt auch eine **Flow** verweisbeziehung, die akzeptiert **FlowElement** Domänenklassen in der Quell- und Zielrolle. Jedoch eine Instanz von ein **Endpunkt** Domänenklasse sollte sich nicht auf die Quelle einer Instanz von eine **Flow** Beziehung noch sollte eine Instanz von einer **"StartPoint"** -Klasse der Ziel einer Instanz von einem **Flow** Beziehung. Die **FlowBuilder** Verbindungs-Generator enthält einen Link, der mit dem Namen verbindungsdirektive **Flow** , der angibt, welche Domänenklassen die Quellrolle wiedergeben können (**Aufgabe**,  **"Mergebranch"**, **"StartPoint"**, und **Synchronisierung**) und können die Zielrolle wiedergeben (**"mergebranch"**,  **Endpunkt**, und **Synchronisierung**).  
  
### <a name="connection-builders-with-multiple-link-connect-directives"></a>Verbindungs-Generatoren mit mehreren Direktiven für Linkverbindungen  
 Sie können einem Verbindungs-Generator mehr als eine Direktive für Linkverbindungen hinzufügen. Damit können Sie einige der Komplexitäten der Benutzer das Domänenmodell ausgeblendet, und halten die **Toolbox** übersichtlicher. Sie können in einem Verbindungs-Generator für mehrere verschiedene Domänenbeziehungen Direktiven für Linkverbindungen hinzufügen. Sie sollten Domänenbeziehungen jedoch kombinieren, wenn sie annähernd die gleiche Funktion ausführen.  
  
 In der Projektmappe Aufgabenfluss der **Flow** Verbindungstool wird verwendet, um Instanzen der Zeichnen die **Flow** und **ObjectFlow** domänenbeziehungen. Die **FlowBuilder** Verbindungs-Generator verfügt zusätzlich zu den **Flow** weiter oben beschriebenen Direktive für linkverbindungen, zwei eine Direktive für linkverbindungen namens **ObjectFlow**. Diesen Direktiven wird angegeben, die eine Instanz von einer **ObjectFlow** Beziehung zwischen Instanzen von gezeichnet werden kann die **"objectinstate"** Domänenklasse oder von einer Instanz von einer **"objectinstate"**  mit einer Instanz von einer **Aufgabe**, jedoch nicht zwischen zwei Instanzen von eine **Aufgabe**, oder von einer Instanz von einer **Aufgabe** mit einer Instanz von einem **"Objectinstate"**. Jedoch eine Instanz von einem **Flow** Beziehung zwischen zwei Instanzen von gezeichnet werden kann eine **Aufgabe**. Wenn Sie kompilieren und führen Sie die Projektmappe Aufgabenfluss, sehen Sie diese Funktionen zum Zeichnen eine **Flow** von einer Instanz von ein **"objectinstate"** mit einer Instanz von eine **Aufgabe** erstellt eine Instanz der ein **ObjectFlow**, sondern zeichnen eine **Flow** zwischen zwei Instanzen von eine **Aufgabe** erstellt eine Instanz des eine **Flow**.  
  
### <a name="custom-code-for-connection-builders"></a>Benutzerdefinierter Code für Verbindungs-Generatoren  
 Es gibt vier Kontrollkästchen auf der Benutzeroberfläche, mit denen die unterschiedlichen Typen von Anpassungen der Verbindungs-Generatoren definiert werden:  
  
-   die **benutzerdefiniertes akzeptieren** Kontrollkästchen Direktive der Quell- oder Zieltabelle  
  
-   die **benutzerdefinierte Verbindung** Kontrollkästchen Direktive der Quell- oder Zieltabelle  
  
-   die **verwendet benutzerdefiniertes verbinden** das Kontrollkästchen für eine verbindungsdirektive  
  
-   die **ist Benutzerdefiniert** Eigenschaft des Verbindungs-Generators  
  
 Für diese Anpassungen müssen Sie Programmcode angeben. Sie können herausfinden, welcher Code erforderlich ist, indem Sie eines dieser Kontrollkästchen aktivieren, auf "Alle Vorlagen transformieren" klicken und dann die Projektmappe erstellen. Ein Fehlerbericht wird erstellt. Doppelklicken Sie auf den Fehlerbericht, um einen Kommentar zu lesen, der den hinzuzufügenden Code erläutert.  
  
> [!NOTE]
>  Erstellen Sie zum Hinzufügen von benutzerdefiniertem Code eine partielle Klassendefinition in einer Codedatei, die nicht zu den Codedateien in den Ordnern "GeneratedCode" gehört. Damit Ihre Arbeit nicht verloren geht, sollten Sie die generierten Codedateien nicht bearbeiten. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).  
  
#### <a name="creating-custom-connection-code"></a>Erstellen von benutzerdefiniertem Verbindungscode  
 In jeder Direktive für linkverbindungen der **rollendirektiven, die Quelle** definiert die Registerkarte welche Typen ziehen kann. Auf ähnliche Weise die **rollendirektiven, die als Ziel** Registerkarte definiert welche Typen ziehen kann. Für jeden Typ, Sie können zudem angeben, ob die Verbindung zulassen (für diese Direktive für linkverbindungen) durch Festlegen der **benutzerdefiniertes akzeptieren** kennzeichnen, und klicken Sie dann zusätzlichen Code angeben.  
  
 Darüber hinaus können Sie anpassen, was geschieht, wenn die Verbindung hergestellt wird. Sie können beispielsweise nur den Fall anpassen, wenn das Ziehen in eine oder aus einer bestimmten Klasse erfolgt. Sie können aber auch alle Fälle, für die eine Direktive für Linkverbindungen gilt, oder den gesamten FlowBuilder-Verbindungs-Generator anpassen. Für jede dieser Optionen können Sie benutzerdefinierte Flags auf der entsprechenden Ebene festlegen. Wenn Sie alle Vorlagen transformieren und die Projektmappe erstellen, weisen Sie Fehlermeldungen auf Kommentare im generierten Code hin. In diesen Kommentaren werden die erforderlichen Angaben identifiziert.  
  
 Im Komponentendiagrammbeispiel wurde der Verbindungs-Generator für die Domänenbeziehung "Verbindung" angepasst, um die zwischen Ports möglichen Verbindungen zu beschränken. Die folgende Abbildung zeigt, dass Sie nur Verbindungen von `OutPort`-Elementen mit `InPort`-Elementen herstellen können. Zudem können Sie Komponenten ineinander schachteln.  
  
 **Eingehende Verbindung für OutPort aus einer geschachtelten Komponente**  
  
 ![Verbindungs-Generator](../modeling/media/connectionbuilder-3.png "ConnectionBuilder_3")  
  
 Daher könnten Sie angeben, dass eine Verbindung aus einer geschachtelten Komponente mit "OutPort" zulässig ist. Um eine solche Verbindung anzugeben, legen Sie **verwendet benutzerdefiniertes akzeptieren** auf die **InPort** Typ als Quellrolle und den **OutPort** Typ als Zielrolle der **DSL-Details**  wie in den folgenden Abbildungen gezeigt:  
  
 **Linkverbindungsanweisung im DSL-Explorer**  
  
 ![Verbindungsgenerator-Abbild](../modeling/media/connectionbuilder-4a.png "ConnectionBuilder_4a")  
  
 **Linkverbindungsanweisung im Fenster "DSL-Details"**  
  
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
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)  
    {  
      return sourceInPort.Component == targetInPort.Component.Parent;  
    }  
// And similar for OutPorts…  
```  
  
 Weitere Informationen zum Anpassen des Modells mit Programmcode finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Sie können ähnlichen Code verwenden, um beispielsweise zu verhindern, dass die Benutzer Schleifen mit Links zwischen übergeordneten und untergeordneten Elementen erstellen. Diese Beschränkungen gelten als fest, da sie von den Benutzern zu keinem Zeitpunkt verletzt werden können. Sie können auch "weiche" Überprüfungen einrichten, die die Benutzer vorübergehend mit ungültigen Konfigurationen, die nicht gespeichert werden, umgehen können.  
  
### <a name="good-practice-in-defining-connection-builders"></a>Empfehlungen für die Definition von Verbindungs-Generatoren  
 Sie sollten einen Verbindungs-Generator definieren, um unterschiedliche Typen von Beziehungen zu erstellen, wenn sie konzeptionell verwandt sind. Im Beispiel des Aufgabenablaufs verwenden Sie einen Generator, um die Abläufe zwischen Aufgaben und zwischen Aufgaben und Objekten zu erstellen. Es kann jedoch verwirrend sein, den gleichen Generator für Beziehungen zwischen Kommentaren und Aufgaben zu verwenden.  
  
 Wenn Sie einen Verbindungs-Generator für mehrere Typen von Beziehungen erstellen, sollten Sie sicherstellen, dass er nicht zu mehr als einem Typ eines Paars von Quell- und Zielobjekten passt. Andernfalls können sich unerwartete Ergebnisse ergeben.  
  
 Sie verwenden benutzerdefinierten Code, um feste Beschränkungen anzuwenden. Sie sollten aber überlegen, ob die Benutzer vorübergehend ungültige Verbindungen erstellen dürfen. In dem Fall können Sie die Beschränkungen so ändern, dass die Verbindungen erst überprüft werden, wenn die Benutzer die Änderungen speichern möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Elementerstellung und-Verschiebung](../modeling/customizing-element-creation-and-movement.md)   
 [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md)   
 [Vorgehensweise: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Circuit Diagrams Sample DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)



