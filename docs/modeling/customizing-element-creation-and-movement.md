---
title: Anpassen der Elementerstellung und -verschiebung
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8f4563756e42b5c0bdc1a56e938ca6326e04b104
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748658"
---
# <a name="customizing-element-creation-and-movement"></a>Anpassen der Elementerstellung und -verschiebung
Sie können ein Element auf eine andere gezogen werden, aus der Toolbox oder in einem einfügen bzw. Verschiebevorgang ab. Können die verschobenen Elemente, die mit der Zielelemente verknüpft mit den Beziehungen, die Sie angeben.

 Eine Element-Merge-Anweisung (EMD) gibt an, was geschieht, wenn ein Modellelement wird *zusammengeführte* in ein anderes Modellelement. Dies geschieht, wenn:

-   Der Benutzer zieht aus der Toolbox auf das Diagramm oder eine Form ".

-   Der Benutzer erstellt ein Element mit einem Menü "hinzufügen" in den Explorer oder einem Depot-Form.

-   Der Benutzer verschiebt ein Element aus einem Verantwortlichkeitsbereich.

-   Der Benutzer fügt ein Element.

-   Programmcode Ruft die Element-Direktive zusammenführen.

 Obwohl die Vorgänge zur Erstellung erscheinen, können von den Kopiervorgänge unterscheiden, arbeiten sie tatsächlich auf die gleiche Weise. Wenn ein Element hinzugefügt wird, wird z. B. aus der Toolbox ein Prototyp davon repliziert. Der Prototyp wird in das Modell auf die gleiche Weise wie Elemente zusammengeführt, die von einem anderen Teil des Modells kopiert wurden.

 Die Zuständigkeit für ein EMD besteht darin, entscheiden, wie ein Objekt oder eine Gruppe von Objekten in einer bestimmten Stelle im Modell zusammengeführt werden sollen. Insbesondere können sie entscheidet, welche Beziehungen instanziiert werden sollte, um der Gruppe "zusammengeführte" in das Modell zu verknüpfen. Sie können auch zum Festlegen von Eigenschaften und zum Erstellen zusätzlicher Objekte anpassen.

 ![DSL&#45;EMD&#95;Merge](../modeling/media/dsl-emd_merge.png) die Rolle des eine Merge-Element-Direktive

 Ein EMD wird automatisch generiert, wenn Sie eine Einbetten von Beziehung definieren. Diese Standardeinstellung EMD erstellt eine Instanz der Beziehung an, wenn Benutzer neue Instanzen der untergeordneten zum übergeordneten Element hinzufügen. Sie können diese Standardeinstellung EMDs z. B. durch Hinzufügen von benutzerdefiniertem Code ändern.

 Sie können auch eigene EMDs hinzufügen, in der DSL-Definition, damit Benutzer ziehen, oder fügen Sie verschiedene Kombinationen von zusammengeführten und Empfangen von Klassen.

## <a name="defining-an-element-merge-directive"></a>Definieren eine Element-Merge-Anweisung
 Sie können Element Merge Direktiven Domänenklassen, domänenbeziehungen, Formen, Connectors und Diagrammen hinzufügen. Sie können finden sie unter der empfangenden Domänenklasse im Explorer für DSL oder hinzufügen. Die empfangende Klasse ist die Domänenklasse des Elements, das bereits im Modell, und klicken Sie auf dem das neue oder kopierte Element zusammengeführt werden.

 ![DSL&#45;EMD&#95;Details](../modeling/media/dsl-emd_details.png)

 Die **Indizierung Klasse** ist die Domänenklasse von Elementen, die Mitglieder der empfangenden Klasse zusammengeführt werden können. Instanzen einer Unterklasse von der Indizierung-Klasse werden auch von diesem EMD zusammengeführt werden, es sei denn, Sie legen **gilt für Unterklassen** auf "false".

 Es gibt zwei Arten von Merge-Anweisung aus:

-   Ein **Prozess Merge** -Direktive angibt, die Beziehungen mit dem das neue Element in der Struktur verknüpft werden soll.

-   Ein **vorwärts Merge** Richtlinie leitet das neue Element zu einem anderen Element empfangen, in der Regel ein übergeordnetes Element.

 Sie können benutzerdefinierten Code zum Zusammenführen von Direktiven hinzufügen:

-   Legen Sie **verwendet benutzerdefinierte akzeptieren** Hinzufügen Ihrer eigenen Code aus, um zu bestimmen, ob eine bestimmte Instanz des Elements Indizierung in das Zielelement zusammengeführt werden sollen. Wenn der Benutzer aus der Toolbox gezogen wird, zeigt "Ungültige" Zeiger auf, wenn Ihr Code die Zusammenführung lässt.

     Sie können z. B. die Zusammenführung ermöglichen, nur, wenn die empfangende Element in einem bestimmten Status ist.

-   Legen Sie **verwendet benutzerdefinierte Merge** hinzuzufügende bieten Sie eigenen Code, um die Änderungen zu definieren, die für das Modell vorgenommen werden, wenn die Zusammenführung ausgeführt wird.

     Sie können z. B. Eigenschaften in der zusammengeführten Elements festlegen, mit Daten aus seiner neuen Position im Modell.

> [!NOTE]
>  Wenn Sie benutzerdefinierten Code schreiben, wirkt sich dieser nur Zusammenführungen, die mithilfe dieser EMD ausgeführt werden. Wenn andere EMDs, die den gleichen Typ des Objekts zusammenführen, oder wenn anderen benutzerdefinierten Code, der diese Objekte erstellt, ohne die EMD vorhanden ist, klicken Sie dann diese nicht von Ihrem benutzerdefinierten Code betroffen davon.
>
>  Wenn Sie möchten sicherstellen, dass ein neues Element oder eine neue Beziehung immer der benutzerdefinierte Code verarbeitet wird, sollten Sie eventuell definieren ein `AddRule` Einbetten von Beziehung und eine `DeleteRule` auf das Element Domänenklasse. Weitere Informationen finden Sie unter [weitergeben Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="example-defining-an-emd-without-custom-code"></a>Beispiel: Definieren einer EMD ohne benutzerdefinierten code
 Das folgende Beispiel ermöglicht Benutzern, die ein Element und eine Verbindung zur gleichen Zeit zu erstellen, indem Sie aus der Toolbox auf eine vorhandene Form ziehen. Im Beispiel wird ein EMD der DSL-Definition hinzugefügt. Vor dieser Änderung können Benutzer auf das Diagramm, jedoch nicht auf vorhandene Shapes Tools ziehen.

 Benutzer können auch Elemente auf andere Elemente einfügen.

#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Können Benutzer, die zur selben Zeit ein Element und einen Connector erstellen

1.  Erstellen Sie eine neue DSL mit der **minimale Sprache** Projektmappenvorlage.

     Wenn Sie diese DSL ausführen, können Sie die Formen und Verbindern zwischen den Formen erstellen. Sie können kein neues ziehen **ExampleElement** Form aus der Toolbox auf eine vorhandene Form.

2.  Können Benutzer Elemente auf merge `ExampleElement` Formen, erstellen Sie eine neue EMD in die `ExampleElement` Domänenklasse:

    1.  In **Explorer für DSL**, erweitern Sie **Domänenklassen**. Mit der rechten Maustaste `ExampleElement` , und klicken Sie dann auf **fügen neue Element Merge-Direktive**.

    2.  Stellen Sie sicher, dass die **DSL-Detailfenster** Fenster geöffnet ist, sodass Sie die Details des neuen EMD sehen können. (Menü: **Ansicht**, **anderen Fenstern**, **DSL-Detailfenster**.)

3.  Legen Sie die **Indizierung Klasse** in DSL-Detailfenster definieren, welche Klasse von Elementen auf zusammengeführt werden kann `ExampleElement` Objekte.

     Wählen Sie für dieses Beispiel `ExampleElements`, sodass neue Elemente in der Benutzer in vorhandenen Elemente gezogen werden kann.

     Beachten Sie, dass die Indizierung-Klasse den Namen des der EMD im Explorer für DSL wird.

4.  Klicken Sie unter **Prozess Merge durch Erstellen von Verknüpfungen**, fügen Sie zwei Pfade hinzu:

    1.  Ein Pfad verknüpft das neue Element, das übergeordnete Modell. Der Path-Ausdruck, den Sie benötigen, geben navigiert von das vorhandene Element sich durch das Einbetten von Beziehung für das übergeordnete Modell. Schließlich gibt die Rolle an, in den neuen Link, den das neue Element zugewiesen werden soll. Der Pfad lautet wie folgt:

         `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

    2.  Der andere Pfad verknüpft das neue Element auf das vorhandene Element. Der Path-Ausdruck gibt die verweisbeziehung und die Rolle, die das neue Element zugewiesen werden soll. Dieser Pfad lautet wie folgt:

         `ExampleElementReferencesTargets.Sources`

     Der Pfad Navigationstool können jeder Pfad erstellen:

    1.  Klicken Sie unter **Prozess Merge durch Erstellen von Verknüpfungen Pfade**, klicken Sie auf  **\<Pfad hinzufügen >**.

    2.  Klicken Sie auf den Dropdownpfeil rechts neben dem Listenelement. Es wird eine Strukturansicht angezeigt.

    3.  Erweitern Sie die Knoten in der Struktur zu einem Pfad kombiniert, den Sie angeben möchten.

5.  Testen der DSL:

    1.  Drücken Sie F5, um erneut zu erstellen und führen Sie die Projektmappe aus.

         Neuerstellung dauert länger als üblich, da der generierte Code über Textvorlagen entsprechen, die neue DSL-Definition aktualisiert werden.

    2.  Wenn der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wurde gestartet, öffnen Sie eine Modelldatei von der DSL. Erstellen Sie einige Beispiel-Elemente.

    3.  Ziehen Sie aus der **Beispielelement** Tool eine vorhandene Shape.

         Neue Form angezeigt wird, und sie mit der vorhandenen Form mit einer Verbindung verknüpft ist.

    4.  Kopieren einer vorhandenen Form an. Wählen Sie eine andere Form, und fügen Sie.

         Eine Kopie der ersten Form wird erstellt.  Er besitzt einen neuen Namen ein, und sie mit der zweiten Form mit einer Verbindung verknüpft ist.

 Beachten Sie die folgenden Punkte von dieser Prozedur aus:

-   Durch das Erstellen von Element Merge-Anweisungen, können Sie jede Klasse des Elements auf alle anderen akzeptieren erlauben. Die EMD wird in der empfangenden Domänenklasse erstellt, und die akzeptierte Domäne-Klasse wird angegeben, der **Index-Klasse** Feld.

-   Durch Definieren von Pfaden, können Sie angeben, welche Links sollte verwendet werden, um das neue Element mit dem vorhandenen Modell herzustellen.

     Die Links, die Sie angeben, sollte eine Einbetten von Beziehung enthalten.

-   Die EMD wirkt sich auf beide Erstellung aus der Toolbox und auch die Einfügevorgänge.

     Wenn Sie benutzerdefinierten Code, die neuen Elemente erstellt schreiben, können Sie die EMD explizit aufrufen, mit der `ElementOperations.Merge` Methode. Dadurch wird sichergestellt, dass Ihr Code neue Elemente in das Modell in die gleiche Weise wie andere Vorgänge verknüpft. Weitere Informationen finden Sie unter [Kopierverhalten anpassen](../modeling/customizing-copy-behavior.md).

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Beispiel: Ein EMD akzeptieren benutzerdefinierten Code hinzufügen
 Ein EMD benutzerdefinierten Code hinzufügen, können Sie komplexeres Merge Verhalten definieren. In diesem einfachen Beispiel wird verhindert, dass den Benutzer in das Diagramm mehr als eine feste Anzahl von Elementen hinzufügen. Im Beispiel wird die Standardeinstellung EMD, die mit einer Beziehung auf Einbetten von geändert.

#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Zum Schreiben von Code zum einschränken, was der Benutzer hinzufügen, kann benutzerdefinierte akzeptieren

1.  Erstellen Sie eine DSL mit der **minimale Sprache** Projektmappenvorlage. DSL-Definitionsdiagramm zu öffnen.

2.  Erweitern Sie im Explorer für DSL, **Domänenklassen**, `ExampleModel`, **Element Merge Direktiven**. Wählen Sie die Element-Merge-Direktive mit dem Namen `ExampleElement`.

     Diese EMD steuert, wie der Benutzer neu erstellen kann `ExampleElement` Objekte im Modell, indem Sie beispielsweise aus der Toolbox ziehen.

3.  In der **DSL-Detailfenster** wählen **verwendet benutzerdefinierte akzeptieren**.

4.  Generieren Sie die Projektmappe neu. Dieser Vorgang dauert länger als üblich, da der generierte Code aus dem Modell aktualisiert werden.

     Ein Buildfehler wird gemeldet, die sehr ähnlich: "Company.ElementMergeSample.ExampleElement enthält keine Definition für CanMergeExampleElement..."

     Sie müssen die Methode implementieren `CanMergeExampleElement`.

5.  Erstellen Sie eine neue Codedatei, in der **Dsl** Projekt. Ersetzen Sie den Inhalt durch den folgenden Code aus, und ändern Sie den Namespace dem Namespace des Projekts.

    ```csharp
    using Microsoft.VisualStudio.Modeling;

    namespace Company.ElementMergeSample // EDIT.
    {
      partial class ExampleModel
      {
        /// <summary>
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.
        /// This happens when the user pastes an ExampleElement
        /// or drags from the toolbox.
        /// Determines whether the merge is allowed.
        /// </summary>
        /// <param name="rootElement">The root element in the merging EGP.</param>
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>
        /// <returns>True if the merge is allowed</returns>
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)
        {
          // Allow no more than 4 elements to be added:
          return this.Elements.Count < 4;
        }
      }
    }

    ```

     Dieses einfache Beispiel schränkt die Anzahl der Elemente, die das übergeordnete Modell zusammengeführt werden können. Die Methode kann keine der Eigenschaften und Links, der das empfangende Objekt überprüfen und weitere interessante Bedingungen. Sie können auch die Eigenschaften der Zusammenführen von Elemente, die in ausgeführt werden Überprüfen einer <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Weitere Informationen zu `ElementGroupPrototypes`, finden Sie unter [Kopierverhalten anpassen](../modeling/customizing-copy-behavior.md). Weitere Informationen dazu, wie Sie Code schreiben, der ein Modell liest, finden Sie unter [Navigieren in und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).

6.  Testen der DSL:

    1.  Drücken Sie F5, um die Projektmappe neu erstellen. Wenn der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] geöffnet wird, öffnen Sie eine Instanz von der DSL.

    2.  Erstellen Sie neue Elemente auf verschiedene Arten:

        1.  Ziehen Sie aus der **Beispielelement** Tool auf das Diagramm.

        2.  In der **Beispiel-Modell-Explorer**mit der rechten Maustaste auf den Stammknoten, und klicken Sie dann auf **neue Beispielelement hinzufügen**.

        3.  Kopieren Sie ein Element im Diagramm.

    3.  Stellen Sie sicher, dass Sie eine der folgenden Möglichkeiten zum Hinzufügen von mehr als vier Elemente für das Modell verwenden können. Dies ist, da sie alle die Element-Direktive Zusammenführen verwenden.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Beispiel: Ein EMD Merge benutzerdefinierten Code hinzufügen
 In benutzerdefinierten Merge Code können Sie definieren, was geschieht, wenn der Benutzer ein Tool zieht oder auf einem Element eingefügt. Es gibt zwei Möglichkeiten, eine benutzerdefinierte Zusammenführung zu definieren:

1.  Legen Sie **verwendet benutzerdefinierte Merge** , und geben Sie den erforderlichen Code. Die generierten Merge-Code wird Code ersetzt. Verwenden Sie diese Option, wenn Sie vollständig neu definieren, was bewirkt, dass die Zusammenführung möchten.

2.  Überschreiben Sie die `MergeRelate` -Methode, und optional die `MergeDisconnect` Methode. Zu diesem Zweck legen Sie die **generiert doppelte abgeleitet** Eigenschaft der Domänenklasse. Ihr Code kann den generierten Merge Code in der Basisklasse aufrufen. Verwenden Sie diese Option, wenn Sie möchten zusätzliche Vorgänge ausführen, nachdem die Zusammenführung durchgeführt wurde.

 Diese Ansätze wirken sich nur auf Zusammenführungen, die mithilfe dieser EMD ausgeführt werden. Wenn Sie möchten alle Möglichkeiten zu beeinflussen, in dem das zusammengeführte Element erstellt werden kann, ist eine Alternative zum definieren eine `AddRule` Einbetten von Beziehung und eine `DeleteRule` in der verbundene-Domänenklasse. Weitere Informationen finden Sie unter [weitergeben Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

#### <a name="to-override-mergerelate"></a>MergeRelate überschreiben

1.  Stellen Sie in der DSL-Definition sicher, dass Sie die EMD definiert haben, zu dem Sie Code hinzufügen möchten. Wenn Sie möchten, können Sie Pfade hinzufügen und definieren benutzerdefinierte Code akzeptieren, wie in den vorherigen Abschnitten beschrieben.

2.  Wählen Sie im Diagramm DslDefinition die empfangende Klasse der Zusammenführung aus. In der Regel wird die Klasse am Quellende des ein Einbetten von Beziehung.

     Wählen Sie in eine DSL generiert aus der Projektmappe minimale Sprache, z. B. `ExampleModel`.

3.  In der **Eigenschaften** legen **generiert doppelte abgeleitete** auf **"true"**.

4.  Generieren Sie die Projektmappe neu.

5.  Überprüfen Sie den Inhalt des **Dsl\Generated Files\DomainClasses.cs**. Suche nach Methoden, die mit dem Namen `MergeRelate` und deren Inhalt untersuchen. Dies hilft Ihnen Ihre eigenen Versionen zu schreiben.

6.  In eine neue Codedatei schreiben eine partielle Klasse für die empfangende-Klasse, und überschreiben die `MergeRelate` Methode. Denken Sie daran, zum Aufrufen der Basismethode. Zum Beispiel:

    ```csharp
    partial class ExampleModel
    {
      /// <summary>
      /// Called when the user drags or pastes an ExampleElement onto the diagram.
      /// Sets the time of day as the name.
      /// </summary>
      /// <param name="sourceElement">Element to be added</param>
      /// <param name="elementGroup">Elements to be merged</param>
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)
      {
        // Connect the element according to the EMD:
        base.MergeRelate(sourceElement, elementGroup);

        // Custom actions:
        ExampleElement mergingElement = sourceElement as ExampleElement;
        if (mergingElement != null)
        {
          mergingElement.Name = DateTime.Now.ToLongTimeString();
        }
      }
    }

    ```

#### <a name="to-write-custom-merge-code"></a>Zusammenführen von benutzerdefinierten Code schreiben

1.  In **Dsl\Generated Code\DomainClasses.cs**, überprüfen Sie die Methoden, die mit dem Namen `MergeRelate`. Diese Methoden werden Links zwischen ein neues Element und das vorhandene Modell erstellt.

     Überprüfen Sie darüber hinaus Methoden, die mit dem Namen `MergeDisconnect`. Diese Methoden Aufheben der Verknüpfung eines Elements aus dem Modell gelöscht wird.

2.  In **Explorer für DSL**Auswahl, oder erstellen Sie das Element Merge-Direktive, die Sie anpassen möchten. In der **DSL-Detailfenster** legen **verwendet benutzerdefinierte Merge**.

     Bei Festlegung dieser Option die **Prozess Merge** und **vorwärts Merge** Optionen werden ignoriert. Der Code wird stattdessen verwendet.

3.  Generieren Sie die Projektmappe neu. Es dauert länger als üblich, da es sich bei die generierten Codedateien aus dem Modell aktualisiert werden.

     Es werden Fehlermeldungen angezeigt. Doppelklicken Sie auf die Fehlermeldungen, die Anweisungen im generierten Code finden Sie unter. Diese Anweisungen Sie werden aufgefordert, zwei Methoden geben `MergeRelate` *YourDomainClass* und `MergeDisconnect` *YourDomainClass*

4.  Schreiben Sie die Methoden in einer partiellen Klassendefinition in einer separaten Codedatei. Die Beispiele, die Sie zuvor betrachtete sollte gesuchte vorgeschlagen.

 Benutzerdefinierte Merge Code wirkt sich nicht auf Code, der Objekte und Beziehungen direkt erstellt, und andere EMDs sind davon nicht betroffen. Um sicherzustellen, dass die zusätzlichen Änderungen implementiert werden, unabhängig davon, wie das Element erstellt wird, sollten Sie das Schreiben einer `AddRule` und ein `DeleteRule` stattdessen. Weitere Informationen finden Sie unter [weitergeben Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="redirecting-a-merge-operation"></a>Umleiten eines Merge-Vorgangs
 Eine forward-Merge-Richtlinie leitet das Ziel einer Merge-Vorgang. In der Regel ist das neue Ziel das Einbetten von übergeordnet das erste Ziel.

 Ports werden z. B. in eine DSL, die mit der Komponente Diagrammvorlage erstellt wurde, in den Komponenten eingebettet. Ports werden als kleine Formen auf den Rand einer Form "Komponente" angezeigt. Der Benutzer erstellt Ports durch Ziehen die Port-Tool auf eine Form "Komponente". Aber in manchen Fällen versehentlich bewegt die Port-Tool auf einen vorhandenen Port, anstatt die Komponente und der Vorgang fehlschlägt. Dies ist eine einfache Fehler, wenn mehrere vorhandene Ports sind. Um dem Benutzer zur Vermeidung dieses Sicherheitsrisiko zu helfen, können Sie zulassen, Ports, um auf einen vorhandenen Port gezogen werden, jedoch die Aktion an die übergeordnete Komponente umgeleitet. Der Vorgang funktioniert, als wäre das Zielelement der Komponente.

 Sie können eine forward-Merge-Anweisung in der Komponentenmodell-Lösung erstellen. Wenn Sie kompilieren und die ursprüngliche Projektmappe ausführen, sollten Sie sehen, dass Benutzer, eine beliebige Anzahl von ziehen können **Eingabe Port** oder **Ausgabeport** Elemente aus der **Toolbox** auf eine **Komponente** Element. Sie können keine jedoch einen Port an einen vorhandenen Port ziehen. Der Zeiger nicht verfügbar warnt sie, dass diese Entscheidung nicht aktiviert ist. Allerdings können Sie eine forward-Merge-Anweisung erstellen, sodass ein Port sein, die versehentlich gelöscht, die auf einer vorhandenen **Eingabe Port** an weitergeleitet wird die **Komponente** Element.

#### <a name="to-create-a-forward-merge-directive"></a>So erstellen eine forward-Merge-Anweisung

1.  Erstellen einer [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Lösung mithilfe der Komponentenmodell-Vorlage.

2.  Anzeigen der **Explorer für DSL** DslDefinition.dsl öffnen.

3.  In der **Explorer für DSL**, erweitern Sie **Domänenklassen**.

4.  Die **ComponentPort** abstrakte Domänenklasse ist die Basisklasse beider **InPort** und **OutPort**. Mit der rechten Maustaste **ComponentPort** , und klicken Sie dann auf **fügen neue Element Merge-Direktive**.

     Ein neues **Merge Element-Direktive** Knoten befindet sich unter der **Element Merge Direktiven** Knoten.

5.  Wählen Sie die **Merge Element-Direktive** Knoten, und öffnen Sie die **DSL-Detailfenster** Fenster.

6.  Wählen Sie in der Liste der Indizierung Klasse **ComponentPort**.

7.  Wählen Sie **Weiterleiten der Zusammenführung zu einer anderen Domänenklasse**.

8.  Erweitern Sie in der Auswahlliste Pfad **ComponentPort**, erweitern Sie **ComponentHasPorts**, und wählen Sie dann **Komponente**.

     Der neue Pfad sollte diesem ähneln:

     **ComponentHasPorts.Component/!Component**

9. Speichern Sie die Projektmappe, und klicken Sie dann die Vorlagen zu transformieren, durch Klicken auf die Schaltfläche ganz rechts auf der **Projektmappen-Explorer** Symbolleiste.

10. Erstellen Sie die Projektmappe, und führen Sie sie aus. Eine neue Instanz der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt wird.

11. In **Projektmappen-Explorer**, Sample.mydsl zu öffnen. Das Diagramm und die **ComponentLanguage Toolbox** angezeigt werden.

12. Ziehen Sie ein **Eingabe Port** aus der **Toolbox** in eine andere **Eingabe Port.** Ziehen Sie anschließend eine **OutputPort** auf eine **InputPort** , und klicken Sie dann zu einem anderen **OutputPort**.

     Sie sollte nicht den Zeiger nicht verfügbar, und Sie sollten so löschen Sie die neue möglich **Eingabe Port** auf vorhandener basieren. Wählen Sie die neue **Eingabe Port** und ziehen Sie es auf einem anderen Punkt der **Komponente**.

## <a name="see-also"></a>Siehe auch

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Anpassen der Tools und der Toolbox](../modeling/customizing-tools-and-the-toolbox.md)
- [Circuit Diagramme Beispiel DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)