---
title: Anpassen der Elementerstellung und-Verschiebung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
ms.assetid: cbd28f15-dfd7-46bd-ab79-5430e3ed83c8
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ccf761521d43e3f5ff9d12a4af7fbae4addcddc9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100520"
---
# <a name="customizing-element-creation-and-movement"></a>Anpassen der Elementerstellung und -verschiebung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können zulassen, dass ein Element auf eine andere gezogen werden, aus der Toolbox oder in einem einfügen bzw. Verschiebevorgang ab. Sie haben die verschobenen Elemente, die auf die Zielelemente verknüpft mit den Beziehungen, die Sie angeben.  
  
 Eine Direktive für elementzusammenführungen (EMD) gibt an, was geschieht, wenn ein Modellelement *zusammengeführte* in ein anderes Modellelement. Dies geschieht, wenn:  
  
- Der Benutzer zieht aus der Toolbox auf das Diagramm oder eine Form.  
  
- Der Benutzer erstellt ein Element über ein Menü "hinzufügen" im Explorer oder in eine Depot-Form.  
  
- Der Benutzer verschiebt ein Element von einem Verantwortlichkeitsbereich in einen anderen.  
  
- Der Benutzer fügt ein Element.  
  
- Der Code Ruft die elementmerge-Anweisung.  
  
  Auch die Vorgänge zur Erstellung scheint sich von der Kopiervorgänge unterscheiden, arbeiten sie tatsächlich auf die gleiche Weise. Wenn ein Element hinzugefügt wird, wird z. B. aus der Toolbox ein Prototyp des repliziert. Der Prototyp wird in das Modell auf die gleiche Weise wie Elemente zusammengeführt, die von einem anderen Teil des Modells kopiert wurden.  
  
  Die Verantwortung für eine EMD besteht darin zu entscheiden, wie ein Objekt oder eine Gruppe von Objekten in einem bestimmten Speicherort im Modell zusammengeführt werden sollen. Insbesondere können sie entscheidet, welche Beziehungen instanziiert werden sollten, um die zusammengeführte Gruppe in das Modell zu verknüpfen. Sie können auch zum Festlegen von Eigenschaften und zum Erstellen zusätzlicher Objekte anpassen.  
  
  ![DSL&#45;EMD&#95;Merge](../modeling/media/dsl-emd-merge.png "DSL-EMD_Merge")  
  Die Rolle des eine Direktive für Elementzusammenführungen  
  
  Eine EMD wird automatisch generiert, wenn Sie eine einbettende Beziehung definieren. Diese Standardeinstellung EMD erstellt eine Instanz der Beziehung aus, wenn Benutzer neue Instanzen der untergeordneten zum übergeordneten Element hinzufügen. Sie können diese Standardeinstellung EMDs, z. B. Hinzufügen von benutzerdefiniertem Code ändern.  
  
  Sie können auch Ihre eigenen EMDs hinzufügen, in der DSL-Definition, damit Benutzer durch Ziehen oder verschiedene Kombinationen von zusammengeführten und empfangenden Klassen einfügen.  
  
## <a name="defining-an-element-merge-directive"></a>Definieren eine Direktive für Elementzusammenführungen  
 Sie können die elementmerge-Anweisungen um Domänenklassen, domänenbeziehungen, Formen, Konnektoren und Diagrammen hinzufügen. Sie können hinzugefügt oder finden sie im DSL-Explorer unter der empfangende Domänenklasse. Die empfangende Klasse ist die Domänenklasse des Elements, das bereits im Modell, und klicken Sie auf dem das neue oder kopierte Element zusammengeführt werden.  
  
 ![DSL&#45;EMD&#95;Details](../modeling/media/dsl-emd-details.png "DSL-EMD_Details")  
  
 Die **Indizierung Klasse** ist die Domänenklasse von Elementen, die Mitglieder der erhaltenen Klasse zusammengeführt werden können. Instanzen von Unterklassen der Klasse Indizierung werden auch zusammengeführt werden, indem diese EMD, es sei denn, Sie **gilt für Unterklassen** auf "false".  
  
 Es gibt zwei Arten von elementmerge-Anweisung aus:  
  
- Ein **Prozess Merge** -Direktive gibt an, die Beziehungen, die mit dem das neue Element in der Struktur verknüpft werden soll.  
  
- Ein **vorwärts Merge** Richtlinie leitet das neue Element zu einem anderen Element empfangen, in der Regel ein übergeordnetes Element.  
  
  Sie können benutzerdefinierten Code zum Zusammenführen von Anweisungen hinzufügen:  
  
- Legen Sie **verwendet benutzerdefiniertes akzeptieren** , fügen Ihren eigenen Code, um festzustellen, ob eine bestimmte Instanz des volltextindizierungs-Elements in das Zielelement zusammengeführt werden sollen. Wenn der Benutzer aus der Toolbox gezogen wird, zeigt der Zeiger "Ungültige", wenn Ihr Code die Zusammenführung nicht zulässt.  
  
   Beispielsweise können Sie die Zusammenführung ermöglichen, nur, wenn das empfangende Element in einem bestimmten Zustand ist.  
  
- Legen Sie **verwendet benutzerdefinierte Merge** hinzuzufügende Geben Sie eigenen Code, um die Änderungen zu definieren, die für das Modell vorgenommen werden, wenn die Zusammenführung ausgeführt wird.  
  
   Sie können beispielsweise Eigenschaften im zusammengeführten-Element festlegen, mit Daten aus die neue Position in das Modell.  
  
> [!NOTE]
>  Wenn Sie benutzerdefinierte Zusammenführung von Code schreiben, wirkt sich dies nur Zusammenführungen, die mit diesem EMD ausgeführt werden. Wenn andere EMDs, die die gleiche Art von Objekt zusammenführen, oder bei anderen benutzerdefinierter Code, der diese Objekte erstellt werden, ohne die EMD wird dann sie nicht von Ihrem benutzerdefinierten Merge Code betroffen sind.  
>   
>  Wenn Sie sicherstellen, dass ein neues Element oder eine neue Beziehung immer von Ihrem benutzerdefinierten Code verarbeitet wird, können Sie definieren eine `AddRule` in der einbettenden Beziehung und eine `DeleteRule` für das Element die Domänenklasse. Weitere Informationen finden Sie unter [Regeln weitergegeben werden Änderungen in das Modell](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="example-defining-an-emd-without-custom-code"></a>Beispiel: Definieren eine EMD ohne benutzerdefinierten code  
 Im folgende Beispiel ermöglicht Benutzern, die ein Element und einen Connector zur gleichen Zeit zu erstellen, indem Sie Sie aus der Toolbox auf eine vorhandene Form ziehen. Im Beispiel wird eine EMD der DSL-Definition hinzugefügt. Vor dieser Änderung ist können die Benutzer Tools auf das Diagramm, jedoch nicht auf vorhandene Formen ziehen.  
  
 Benutzer können auch Elemente in andere Elemente einfügen.  
  
#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Damit können Benutzer zur selben Zeit ein Element und einen Connector erstellen  
  
1. Erstellen Sie eine neue DSL mithilfe der **minimale Sprache** Projektmappe (Vorlage).  
  
    Wenn Sie diese DSL ausführen, können sie Formen und Konnektoren zwischen den Formen zu erstellen. Sie können keine ziehen, eine neue **ExampleElement** Form aus der Toolbox auf eine vorhandene Form.  
  
2. Zusammenführen von Elementen am Benutzer informieren, `ExampleElement` Formen, erstellen Sie eine neue EMD in die `ExampleElement` Domänenklasse:  
  
   1. In **DSL-Explorer**, erweitern Sie **Domänenklassen**. Mit der rechten Maustaste `ExampleElement` , und klicken Sie dann auf **Hinzufügen neuer Elementmerge-Anweisung**.  
  
   2. Stellen Sie sicher, dass die **DSL-Details** Fenster geöffnet ist, sodass Sie die Details der neuen EMD sehen können. (Im Menü: **Anzeigen von**, **andere Windows**, **DSL-Details**.)  
  
3. Legen Sie die **indizierende Klasse** im DSL-Details-Fenster, zu definieren, welche Klasse von Elementen auf zusammengeführt werden kann `ExampleElement` Objekte.  
  
    Wählen Sie für dieses Beispiel `ExampleElements`, sodass der Benutzer neue Elemente auf vorhandenen Elementen ziehen kann.  
  
    Beachten Sie, dass die Indizierung-Klasse den Namen der EMD im DSL-Explorer wird.  
  
4. Klicken Sie unter **Prozess Merge durch Erstellen von Verknüpfungen**, fügen Sie zwei Pfade hinzu:  
  
   1. Ein Pfad verknüpft das neue Element, das übergeordnete Modell. Der Path-Ausdruck, den Sie benötigen, geben navigiert von das vorhandene Element, um über die einbettungsbeziehung auf das übergeordnete Modell. Schließlich gibt es die Rolle im neuen Link, den das neue Element zugewiesen werden soll. Der Pfad lautet wie folgt aus:  
  
       `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`  
  
   2. Der andere Pfad verknüpft das neue Element, auf das vorhandene Element. Der Path-Ausdruck gibt an, die verweisbeziehung und der Rolle, die das neue Element zugewiesen werden soll. Dieser Pfad lautet wie folgt aus:  
  
       `ExampleElementReferencesTargets.Sources`  
  
      Sie können die Pfad-Navigation-Tool verwenden, um jeden Pfad zu erstellen:  
  
   3. Klicken Sie unter **Prozess Merge durch Erstellen von Links in Pfaden**, klicken Sie auf  **\<Pfad hinzufügen >**.  
  
   4. Klicken Sie auf den Dropdown-Pfeil rechts neben dem Listenelement. Es wird eine Strukturansicht angezeigt.  
  
   5. Erweitern Sie die Knoten in der Struktur zu einem Pfad kombiniert, den Sie angeben möchten.  
  
5. Testen Sie die DSL an:  
  
   1. Drücken Sie F5, um neu zu erstellen, und führen Sie die Projektmappe aus.  
  
        Neuerstellung dauert länger als üblich, da der generierte Code aus Textvorlagen, um die neue DSL-Definition entsprechen aktualisiert wird.  
  
   2. Wenn die experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wurde gestartet, öffnen Sie eine Modelldatei Ihrer DSL. Erstellen Sie eine Beispiel-Elemente.  
  
   3. Ziehen Sie aus der **Beispielelement** Tool auf einer vorhandenen Form.  
  
        Eine neue Form angezeigt wird, und sie mit der vorhandenen Form mit einem Connector verknüpft ist.  
  
   4. Kopieren einer vorhandenen Form an. Wählen Sie eine andere Form, und fügen Sie ein.  
  
        Eine Kopie der ersten Form wird erstellt.  Es hat es sich um einen neuen Namen, und sie mit der zweiten Form mit einem Connector verknüpft ist.  
  
   Beachten Sie die folgenden Punkte in diesem Verfahren aus:  
  
- Erstellen Sie die Elementmerge-Anweisungen, können Sie jede Klasse des Elements, akzeptieren Sie alle anderen zulassen. Die EMD wird in der empfangenden Domänenklasse erstellt, und die akzeptierte Domäne-Klasse wird angegeben, der **Index-Klasse** Feld.  
  
- Durch Definieren von Pfaden, können Sie festlegen, welche Links sollte verwendet werden, um das neue Element mit dem vorhandenen Modell herzustellen.  
  
     Die Links, die Sie angeben, sollte einer einbettende Beziehung enthalten.  
  
- Die EMD wirkt sich sowohl die Erstellung aus der Toolbox, und auch einfügen.  
  
     Wenn Sie benutzerdefinierten Code, die neuen Elemente erstellt schreiben, können Sie die EMD explizit aufrufen, indem Sie mit der `ElementOperations.Merge` Methode. Dadurch wird sichergestellt, dass Ihr Code neue Elemente in das Modell in die gleiche Weise wie andere Vorgänge verknüpft. Weitere Informationen finden Sie unter [Anpassen des Verhaltens beim Kopieren](../modeling/customizing-copy-behavior.md).  
  
## <a name="example-adding-custom-accept-code-to-an-emd"></a>Beispiel: Eine EMD akzeptieren Sie die benutzerdefinierten Code hinzufügen  
 Eine EMD benutzerdefinierten Code hinzufügen, können Sie komplexere Zusammenführungsverhalten definieren. In diesem einfache Beispiel wird verhindert, dass der Benutzer mehr als eine feste Anzahl von Elementen zum Diagramm hinzufügen. Im Beispiel wird der Standardwert EMD, die mit einer einbettenden Beziehung geändert.  
  
#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Zum Schreiben von Code benutzerdefiniertes akzeptieren, um einzuschränken, was der Benutzer hinzufügen können  
  
1. Erstellen Sie eine DSL mithilfe der **minimale Sprache** Projektmappe (Vorlage). Öffnen Sie im DSL-Definitionsdiagramm.  
  
2. Erweitern Sie im DSL-Explorer **Domänenklassen**, `ExampleModel`, **Elementmerge-Anweisungen**. Wählen Sie die elementmerge-Anweisung mit dem Namen `ExampleElement`.  
  
     Diese EMD steuert, wie der Benutzer neu erstellen kann `ExampleElement` Objekte im Modell, indem Sie beispielsweise aus der Toolbox ziehen.  
  
3. In der **DSL-Details** wählen Sie im Fenster **verwendet benutzerdefiniertes akzeptieren**.  
  
4. Generieren Sie die Projektmappe neu. Dies dauert länger als üblich, da es sich bei der generierte Code aus dem Modell aktualisiert wird.  
  
     Ein Buildfehler werden gemeldet, ähnlich: "Company.ElementMergeSample.ExampleElement enthält eine Definition für CanMergeExampleElement keine..."  
  
     Sie müssen die Methode implementieren `CanMergeExampleElement`.  
  
5. Erstellen Sie eine neue Codedatei, in der **Dsl** Projekt. Ersetzen Sie deren Inhalt durch den folgenden Code ein, und ändern Sie den Namespace auf den Namespace des Projekts.  
  
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
  
     In diesem einfache Beispiel schränkt die Anzahl der Elemente, die das übergeordnete Modell zusammengeführt werden können. Weitere interessante Bedingungen kann die Methode eine der Eigenschaften und Links, der das empfangende Objekt überprüfen. Es kann auch überprüfen, das Zusammenführen von Elementen, die übertragen werden die Eigenschaften einer <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Weitere Informationen zu `ElementGroupPrototypes`, finden Sie unter [Anpassen des Verhaltens beim Kopieren](../modeling/customizing-copy-behavior.md). Weitere Informationen dazu, wie Sie Code schreiben, der ein Modell liest, finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
6. Testen Sie die DSL an:  
  
    1. Drücken Sie F5, um die Projektmappe erneut erstellen. Wenn die experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] geöffnet wird, öffnen Sie eine Instanz Ihrer DSL.  
  
    2. Erstellen Sie neue Elemente auf verschiedene Weise:  
  
        1. Ziehen Sie aus der **Beispielelement** Werkzeug in das Diagramm.  
  
        2. In der **Beispiel-Modell-Explorer**mit der rechten Maustaste auf den Stammknoten, und klicken Sie dann auf **fügen neue Beispielelement**.  
  
        3. Kopieren Sie ein Element im Diagramm.  
  
    3. Stellen Sie sicher, dass Sie keine dieser Methoden zum Hinzufügen von mehr als vier Elemente für das Modell verwenden können. Dies ist, da sie alle der Elementmerge-Anweisung verwenden.  
  
## <a name="example-adding-custom-merge-code-to-an-emd"></a>Beispiel: Eine EMD Zusammenführen von benutzerdefinierten Code hinzufügen  
 In benutzerdefinierten Zusammenführung von Code können Sie definieren, was geschieht, wenn der Benutzer ein Tool zieht oder auf ein Element eingefügt. Es gibt zwei Möglichkeiten, eine benutzerdefinierte Zusammenführung zu definieren:  
  
1. Legen Sie **verwendet benutzerdefinierte Merge** , und geben Sie den erforderlichen Code. Ihr Code ersetzt die generierten Zusammenführung von Code. Verwenden Sie diese Option, wenn Sie vollständig neu definieren, was bewirkt, dass die Zusammenführung möchten.  
  
2. Überschreiben der `MergeRelate` -Methode, und optional die `MergeDisconnect` Methode. Zu diesem Zweck müssen Sie festlegen der **generiert doppelte Ableitungen** Eigenschaft der Domänenklasse. Ihr Code kann die generierte Zusammenführung von Code in der Basisklasse aufrufen. Verwenden Sie diese Option, sollten Sie weitere Vorgänge ausführen, nachdem die Zusammenführung durchgeführt wurde.  
  
   Diese Ansätze wirken sich nur Zusammenführungen, die mit diesem EMD ausgeführt werden. Sollten Sie alle Möglichkeiten zu beeinflussen, in dem das zusammengeführte Element erstellt werden kann, ist eine Alternative zum Definieren einer `AddRule` in der einbettenden Beziehung und eine `DeleteRule` in der zusammengeführten Domänenklasse. Weitere Informationen finden Sie unter [Regeln weitergegeben werden Änderungen in das Modell](../modeling/rules-propagate-changes-within-the-model.md).  
  
#### <a name="to-override-mergerelate"></a>MergeRelate überschreiben  
  
1. Stellen Sie sicher, dass Sie die EMD definiert haben, zu dem Sie Code hinzufügen möchten, in der DSL-Definition. Wenn Sie möchten, können Sie diese Pfade hinzufügen und definieren benutzerdefinierte Code akzeptiert, wie in den vorherigen Abschnitten beschrieben.  
  
2. Wählen Sie im Diagramm DslDefinition erhaltenen Klasse der Zusammenführung aus. In der Regel wird die Klasse am Quellenende einer einbettenden Beziehung.  
  
     Wählen Sie in einer DSL, die von der Lösung für die minimale Sprache generiert wird, z. B. `ExampleModel`.  
  
3. In der **Eigenschaften** legen **generiert doppelte Ableitungen** zu **"true"**.  
  
4. Generieren Sie die Projektmappe neu.  
  
5. Überprüfen Sie den Inhalt des **Dsl\Generated Files\DomainClasses.cs**. Suche nach Methoden, die mit dem Namen `MergeRelate` und deren Inhalt untersuchen. Dadurch können Sie Ihre eigenen Versionen zu schreiben.  
  
6. Klicken Sie in eine neue Codedatei, eine partielle Klasse für den empfangenden Klasse schreiben, und überschreiben die `MergeRelate` Methode. Denken Sie daran, die Basismethode aufrufen. Zum Beispiel:  
  
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
  
1. In **Dsl\Generated Code\DomainClasses.cs**, überprüfen Sie die Methoden, die mit dem Namen `MergeRelate`. Diese Methoden erstellen Verknüpfungen zwischen ein neues Element und das vorhandene Modell an.  
  
    Überprüfen Sie darüber hinaus Methoden, die mit dem Namen `MergeDisconnect`. Diese Methoden Aufheben der Verknüpfung eines Elements aus dem Modell bei, die gelöscht werden.  
  
2. In **DSL-Explorer**wählen oder erstellen Sie die Elementmerge-Anweisung, die Sie anpassen möchten. In der **DSL-Details** legen **verwendet benutzerdefinierte Merge**.  
  
    Beim Festlegen dieser Option die **Prozess Merge** und **vorwärts Merge** Optionen werden ignoriert. Ihr Code wird stattdessen verwendet.  
  
3. Generieren Sie die Projektmappe neu. Es dauert länger als üblich, da es sich bei die generierten Codedateien aus dem Modell aktualisiert werden.  
  
    Es werden Fehlermeldungen angezeigt. Doppelklicken Sie auf die zu den Anweisungen im generierten Code finden in Fehlermeldungen. Stellen Sie diese Anweisungen aufgefordert, zwei Methoden, `MergeRelate` *YourDomainClass* und `MergeDisconnect` *YourDomainClass*  
  
4. Schreiben Sie die Methoden in einer partiellen Klassendefinition in einer separaten Codedatei gespeichert. Die Beispiele, die Sie zuvor untersucht werden sollten, benötigen Sie empfohlen.  
  
   Benutzerdefinierte Zusammenführung von Code wirkt sich nicht auf Code, der Objekte und Beziehungen direkt erstellt, und es hat keine Auswirkungen auf andere EMDs. Um sicherzustellen, dass die zusätzlichen Änderungen implementiert werden, unabhängig davon, wie das Element erstellt wird, sollten Sie auf das Schreiben einer `AddRule` und `DeleteRule` stattdessen. Weitere Informationen finden Sie unter [Regeln weitergegeben werden Änderungen in das Modell](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="redirecting-a-merge-operation"></a>Einen Merge-Vorgang umleiten  
 Eine Vorwärts-elementmerge-Anweisung leitet das Ziel eines Mergevorgangs. Normalerweise ist das neue Ziel der übergeordneten einbettungselement, der das ursprüngliche Ziel.  
  
 In einer DSL, die mit der Komponente Diagramm-Vorlage erstellt wurde, sind z. B. die Ports in Komponenten eingebettet. Ports werden als kleine Formen am Rand einer Komponentenform angezeigt. Der Benutzer erstellt Ports durch Ziehen die Port-Tool auf eine Komponentenform. Aber in manchen Fällen der Benutzer zieht das Tool Port versehentlich auf einen vorhandenen Port, anstatt die Komponente, und der Vorgang fehlschlägt. Dies ist einer einfachen Fehler, wenn mehrere vorhandene Ports vorhanden sind. Damit werden den Benutzer, der dieses Sicherheitsrisiko zu vermeiden, können Sie die Ports, um auf einen vorhandenen Port gezogen werden, jedoch die Aktion, die an die übergeordnete Komponente weitergeleitet. Der Vorgang kann, als wäre das Zielelement der Komponente.  
  
 Sie können eine forward elementmerge-Anweisung in der Component Model-Lösung erstellen. Wenn Sie kompilieren und der ursprüngliche Lösung ausführen, sollten Sie sehen, dass Benutzer, eine beliebige Anzahl von ziehen können **Eingangsport** oder **Ausgabeport** Elemente aus der **Toolbox** zu einem **Komponente** Element. Sie können einen Port jedoch können nicht auf einen vorhandenen Port ziehen. Der Zeiger nicht verfügbar warnt sie, dass der Verschiebevorgang nicht aktiviert ist. Allerdings können Sie eine forward elementmerge-Anweisung erstellen, sodass ein Port ist, die versehentlich gelöscht, die auf einem vorhandenen **Eingangsport** an weitergeleitet der **Komponente** Element.  
  
#### <a name="to-create-a-forward-merge-directive"></a>Eine Vorwärts-elementmerge-Anweisung zu erstellen  
  
1. Erstellen Sie eine [!INCLUDE[dsl](../includes/dsl-md.md)] Lösung, mit der Component Model-Vorlage.  
  
2. Anzeigen der **DSL-Explorer** "DslDefinition.DSL" zu öffnen.  
  
3. In der **DSL-Explorer**, erweitern Sie **Domänenklassen**.  
  
4. Die **ComponentPort** abstrakte Domänenklasse ist die Basisklasse sowohl **InPort** und **OutPort**. Mit der rechten Maustaste **ComponentPort** , und klicken Sie dann auf **Hinzufügen neuer Elementmerge-Anweisung**.  
  
     Ein neues **Elementmerge-Anweisung** Knoten befindet sich unter dem **Elementmerge-Anweisungen** Knoten.  
  
5. Wählen Sie die **Elementmerge-Anweisung** Knoten, und öffnen Sie die **DSL-Details** Fenster.  
  
6. Wählen Sie in der Liste der Indizierung, **ComponentPort**.  
  
7. Wählen Sie **Merge an eine andere Domänenklasse weiterleiten**.  
  
8. Erweitern Sie in der Auswahlliste Pfad **ComponentPort**, erweitern Sie **ComponentHasPorts**, und wählen Sie dann **Komponente**.  
  
     Der neue Pfad sollte dieser ähneln:  
  
     **ComponentHasPorts.Component/!Component**  
  
9. Speichern Sie die Projektmappe, und klicken Sie dann die Vorlagen transformieren, indem Sie auf die Schaltfläche ganz rechts auf der **Projektmappen-Explorer** Symbolleiste.  
  
10. Erstellen Sie die Projektmappe, und führen Sie sie aus. Eine neue Instanz der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] angezeigt wird.  
  
11. In **Projektmappen-Explorer**, Sample.mydsl zu öffnen. Das Diagramm und die **ComponentLanguage Toolbox** angezeigt werden.  
  
12. Ziehen Sie ein **Eingangsport** aus der **Toolbox** in ein anderes **Eingangsport.** Ziehen Sie jetzt eine **"outputport"** auf eine **InputPort** , und klicken Sie dann an einen anderen **"outputport"**.  
  
     Daraufhin sollte nicht den Zeiger nicht verfügbar, und Sie sollten so löschen Sie die neue **Eingangsport** auf vorhandener basieren. Wählen Sie die neue **Eingangsport** und ziehen Sie es zu einem anderen Punkt auf der **Komponente**.  
  
## <a name="see-also"></a>Siehe auch  
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Anpassen der Tools und der Toolbox](../modeling/customizing-tools-and-the-toolbox.md)   
 [Circuit Diagrams Sample DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
