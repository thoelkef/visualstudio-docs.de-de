---
title: 'UML-Komponenten Diagramme: Richtlinien | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99f2b67d264edcaab5272d0224d4450ee2e8a6f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297162"
---
# <a name="uml-component-diagrams-guidelines"></a>UML-Komponentendiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie ein *Komponenten Diagramm* zeichnen, um die Struktur eines Software Systems anzuzeigen. Eine videodemo finden Sie unter [Entwerfen der physischen Struktur mithilfe von Komponenten Diagrammen](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure).

 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Klicken Sie zum Erstellen eines UML-Komponenten Diagramms im Menü **Architektur** auf **neues UML-oder ebenendiagramm**.

 Eine Komponente ist eine modulare Einheit, die innerhalb ihrer Umgebung austauschbar ist. Die internale sind ausgeblendet, aber Sie verfügen über eine oder mehrere klar definierte *Schnittstellen* , über die auf ihre Funktionen zugegriffen werden kann. Eine Komponente kann auch über *erforderliche Schnittstellen*verfügen. Eine erforderliche Schnittstelle definiert, welche Funktionen oder Dienste von anderen Komponenten benötigt werden. Indem die angebotenen und erforderlichen Schnittstellen mehrerer Komponenten verknüpft werden, kann eine größere Komponente erstellt werden. Ein vollständiges Softwaresystem kann auch als Komponente verstanden werden.

 Das Zeichnen von Komponentendiagrammen hat mehrere Vorteile:

- Wenn sich das Entwicklungsteam auf die Hauptblöcke eines Entwurfs konzentriert, kann es ein besseres Verständnis des vorhandenen Entwurfs entwickeln und einen entsprechenden neuen Entwurf erstellen.

- Indem Sie sich Ihr System als Auflistung von Komponenten mit klar definierten angebotenen und erforderlichen Schnittstellen vorstellen, optimieren Sie die Abgrenzung zwischen den Komponenten. Dadurch ist der Entwurf einfacher zu verstehen, und der Entwurf kann bei sich ändernden Anforderungen auch einfacher angepasst werden.

  Sie können ein Komponentendiagramm verwenden, um den Entwurf unabhängig von der verwendeten Sprache oder Plattform darzustellen.

## <a name="relationship-to-other-diagrams"></a><a name="OtherDiagrams"></a> Beziehung zu anderen Diagrammen
 Sie können ein Komponentendiagramm in Verbindung mit anderen Diagrammen verwenden.

|Anderes Diagramm|Unterstützt Sie beim Diskutieren und Kommunizieren dieser Aspekte des Entwurfs.|
|-------------------|--------------------------------------------------------------------|
|UML-Sequenzdiagramm|-Interaktionen zwischen den Komponenten eines Systems<br />-Interaktionen und zwischen den Teilen innerhalb einer Komponente.<br /><br /> Weitere Informationen finden Sie unter [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).|
|UML-Klassendiagramm|: Die Schnittstellen einer Komponente. Mit dem Klassendiagramm können Sie die Methoden der Schnittstelle detailliert angeben.<br />: Die Daten, die in Parametern über die Schnittstellen der Komponenten gesendet werden.<br /><br /> Weitere Informationen finden Sie unter [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md).|
|Aktivitätsdiagramme|: Die interne Verarbeitung, die von einer Komponente als Reaktion auf eingehende Nachrichten ausgeführt wird.<br /><br /> Weitere Informationen finden Sie unter [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).|
|Ebenendiagramme|-Logische Architektur Ebenen für Ihre Komponenten.<br /><br /> Weitere Informationen finden Sie unter [ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md).|

## <a name="basic-steps-for-drawing-component-diagrams"></a><a name="Basics"></a> Grundlegende Schritte zum Zeichnen von Komponenten Diagrammen
 Referenzinformationen zu den Elementen in Komponenten Diagrammen finden Sie unter [UML-Komponenten Diagramme: Referenz](../modeling/uml-component-diagrams-reference.md).

 Weitere Informationen zur Verwendung von Komponenten Diagrammen während des Entwurfsprozesses finden Sie unter Modellieren der [Architektur Ihrer APP](../modeling/model-your-app-s-architecture.md).

> [!NOTE]
> Ausführliche Schritte zum Erstellen von Modellierungs Diagrammen werden unter [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)beschrieben.

#### <a name="to-create-a-component-diagram"></a>So erstellen Sie ein Komponentendiagramm

1. Klicken Sie im Menü **Architektur** auf **neues UML-oder ebenendiagramm**.

2. Klicken Sie unter **Vorlagen**auf **UML-Komponenten Diagramm**.

3. Benennen Sie das Diagramm.

4. Wählen Sie unter **zu Modellierungsprojekt hinzufügen**ein vorhandenes Modellierungsprojekt in der Projekt Mappe aus, oder **Erstellen Sie ein neues Modellierungsprojekt**, und klicken Sie dann auf **OK**.

     Ein neues Komponenten Diagramm wird mit der UML- **komponentendiagrammtoolbox** angezeigt. Die Toolbox enthält die erforderlichen Elemente und Beziehungen.

### <a name="drawing-components"></a>Zeichnen von Komponenten
 ![Komponenten mit Schnittstellen](../modeling/media/uml-compdrawing.png "UML_CompDrawing")

 Erstellen Sie eine *Komponente* (1) für jede wesentliche Funktionseinheit in Ihrem System oder Ihrer Anwendung.

 Beispiele hierfür sind eine Anwendung, ein Hardwaregerät, ein Webdienst, eine .NET-Assembly, eine Programmklasse oder eine Gruppe von Klassen oder ein beliebiges anderes Hauptsegment eines Programms.

##### <a name="to-create-components"></a>So erstellen Sie Komponenten

1. Klicken Sie in der Toolbox auf **Komponente** und dann auf einen leeren Teil des Diagramms.

     \- oder -

     Kopieren Sie eine vorhandene Komponente, und fügen Sie diese ein.

    1. Suchen Sie eine vorhandene Komponente in einem Diagramm oder im **UML-Modell-Explorer**.

    2. Klicken Sie mit der rechten Maustaste auf die Komponente und dann auf **Kopieren**.

    3. Öffnen Sie das Diagramm, in dem die kopierte Komponente angezeigt werden soll.

    4. Klicken Sie mit der rechten Maustaste auf einen leeren Bereich im Diagramm, und klicken Sie dann auf **Einfügen**.

         Eine Kopie der Komponente wird unter einem neuen Namen angezeigt.

2. Klicken Sie auf den Namen der Komponente, um ihn zu ändern.

3. Klicken Sie auf das Chevron (5), wenn Sie nur den Header der Komponente anzeigen möchten.

### <a name="showing-the-ports-of-a-component"></a>Anzeigen der Ports einer Komponente
 Ein *Port* (2, 3) stellt eine Gruppe von Nachrichten oder Vorgangs aufrufen dar, die entweder in eine oder aus einer Komponente übergeben werden. Die Gruppe wird von einer Schnittstelle beschrieben, die den Typ des Ports definiert. Ein Port kann entweder eine Schnittstelle anbieten oder eine Schnittstelle erfordern.

 Ein Port mit einer *bereitgestellten Schnittstelle* (2) stellt Vorgänge bereit, die von der Komponente implementiert werden und die von anderen Komponenten verwendet werden können.

 Beispiele sind eine Benutzeroberfläche, ein Webdienst, eine .NET-Schnittstelle oder eine Auflistung von Funktionen in einer beliebigen Programmiersprache.

 Ein Port mit einer *erforderlichen Schnittstelle* (3) stellt die Anforderung einer Komponente für eine Gruppe von Vorgängen oder Diensten dar, die von anderen Komponenten oder externen Systemen bereitgestellt werden soll.

 Ein Webbrowser erfordert z. B. Webserver, und ein Anwendungs-Add-In erfordert die Dienste einer Anwendung.

 Eine Komponente kann über eine beliebige Anzahl von Ports verfügen.

##### <a name="to-add-ports-to-a-component"></a>So fügen Sie einer Komponente Ports hinzu

1. Klicken Sie in der Toolbox auf **bereitgestellte Schnittstelle** oder **erforderliche Schnittstelle**.

2. Klicken Sie auf die Komponente, der Sie Ports hinzufügen möchten.

    Ein Port wird an der Begrenzung der Komponente angezeigt.

    Eine neue Schnittstelle wird als Typ des Ports erstellt. Diese Schnittstelle wird im **UML-Modell-Explorer**angezeigt.

3. Ziehen Sie den Port mit der Maus entlang der Komponentenbegrenzung, um ihn wie gewünscht zu platzieren.

4. Ziehen Sie die Bezeichnung des Ports, um die Position anzupassen.

5. Klicken Sie auf die Bezeichnung, um sie zu ändern. Die Bezeichnung zeigt den Namen der Schnittstelle an. Wenn Sie diesen ändern, ändern Sie den Namen der Schnittstelle.

   Wenn Sie die Attribute und Vorgänge der Schnittstelle aufführen möchten, fügen Sie sie der Schnittstelle im UML-Modell-Explorer hinzu. Alternativ können Sie die Schnittstelle aus dem UML-Modell-Explorer in ein Klassendiagramm ziehen und dort die Vorgänge und Attribute hinzufügen.

### <a name="linking-between-components"></a>Erstellen von Verknüpfungen zwischen Komponenten
 Verwenden Sie eine Abhängigkeit (4), um anzuzeigen, dass die Anforderung einer Komponente von den Vorgängen oder Diensten erfüllt werden kann, die von einer anderen Komponente bereitgestellt werden.

##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>So zeigen Sie an, dass eine angebotene Schnittstelle die Anforderungen einer erforderlichen Schnittstelle erfüllen kann

1. Klicken Sie in der Toolbox auf **Abhängigkeit**.

2. Klicken Sie in einer Komponente auf den Port mit der erforderlichen Schnittstelle und dann in einer anderen Komponente auf den Port mit der angebotenen Schnittstelle.

   Sie sollten es vermeiden, Abhängigkeitsschleifen zu entwerfen, bei denen alle Komponenten einer Gruppe von allen anderen Komponenten abhängig sind.

##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>So fügen Sie einer Komponente einen Port für eine vorhandene Schnittstelle hinzu

- Suchen Sie im **UML-Modell-Explorer** die-Schnittstelle, und ziehen Sie Sie von dort auf die-Komponente.

     - oder -

- Kopieren Sie einen Verweis auf eine Schnittstelle aus einem Diagramm, und fügen Sie ihn ein.

    1. Klicken Sie in einem Klassendiagramm oder einem Komponenten Diagramm mit der rechten Maustaste auf die Schnittstelle, und klicken Sie dann auf **Kopieren**.

    2. Klicken Sie im Komponenten Diagramm mit der rechten Maustaste auf die Komponente, und klicken Sie dann auf **Verweis einfügen**.

         Eine angebotene Schnittstelle wird auf der Komponente angezeigt. Daneben wird ein Aktionstag angezeigt.

        > [!NOTE]
        > Wenn Sie anstelle von einfügenden **Verweis** **Einfügen** verwenden, wird eine neue Schnittstelle mit einem neuen Namen erstellt.

    3. Wenn Sie eine erforderliche Schnittstelle erstellen möchten, klicken Sie auf das Aktions-Tag, und klicken Sie dann **auf in erforderliche Schnittstelle konvertieren**.

## <a name="showing-the-internal-parts-of-a-component"></a><a name="Parts"></a> Die internen Teile einer Komponente werden angezeigt.
 ![Komponentendiagramm mit internen Teilen](../modeling/media/uml-compshowing.png "UML_CompShowing")

 Sie können Teile (3) in einer Komponente (1) platzieren, um anzuzeigen, wie diese aus kleineren Komponenten zusammengesetzt ist, die miteinander interagieren.

 Das Diagramm in der Abbildung gibt an, dass jede Instanz vom Typ "Dinner Now Web Service" eine Instanz von "Customer Server" und eine Instanz von "Kitchen Server" enthält.

 Ein Teil ist eine Eigenschaft seiner übergeordneten Komponente, so wie ein Attribut einer normalen Klasse angehört. Ein Teil hat seinen eigenen Typ, der normalerweise auch eine Komponente ist. Die Bezeichnung des Teils hat die gleiche Form wie ein normales Attribut:

 `+ partName : TypeName`

 In der übergeordneten Komponente zeigt jeder Teil die angebotenen und erforderlichen Schnittstellen an, die für seinen Typ (4, 5) definiert sind. Die Vorgänge und Dienste, die für einen Teil erforderlich sind, können von einem anderen Teil bereitgestellt werden. Sie können teilassemblyconnectors verwenden, um anzuzeigen, wie Teile miteinander verbunden sind (6). **Part Assembly**

 Sie können auch anzeigen, dass eine Schnittstelle der übergeordneten Komponente von einem ihrer Teile angeboten wird oder dafür erforderlich ist. Sie können einen Port des übergeordneten Elements mit einem Port eines internen Teils verbinden, indem Sie eine **Delegierungs** Beziehung (9) verwenden. Die zwei Ports müssen vom gleichen Typ sein (angeboten oder erforderlich), und ihre Schnittstellentypen müssen kompatibel sein.

 Sie können einen neuen Teil entweder mit einem neuen Typ oder aus einem vorhandenen Typ erstellen.

#### <a name="to-add-parts-to-a-component"></a>So fügen Sie einer Komponente Teile hinzu

1. Erstellen Sie einen Teil für jede Hauptfunktionseinheit, die Bestandteil der übergeordneten Komponente ist.

    1. Klicken Sie in der Toolbox auf **Komponente** , und klicken Sie dann in die übergeordnete Komponente (1).

         Ein neuer Teil (3) wird in der übergeordneten Komponente angezeigt.

         Im **UML-Modell-Explorer**wird eine neue-Komponente erstellt. Dies ist der Typ des neuen Teils.

         \- oder -

         Ziehen Sie eine vorhandene Komponente aus dem UML-Modell-Explorer auf die übergeordnete Komponente.

         Ein neuer Teil (3) wird in der übergeordneten Komponente angezeigt. Der Typ ist die Komponente, die Sie aus dem UML-Modell-Explorer gezogen haben.

         \- oder -

         Klicken Sie mit der rechten Maustaste auf eine Komponente, entweder in einem Diagramm oder im UML-Modell-Explorer, und klicken Sie dann auf **Kopieren**.

         Klicken Sie mit der rechten Maustaste auf die übergeordnete Komponente, und klicken Sie dann auf **Verweis einfügen**.

         Ein neuer Teil (3) wird in der übergeordneten Komponente angezeigt. Sein Typ ist die Komponente, die Sie kopiert haben.

    2. Klicken Sie auf den Namen des neuen Teils, um ihn zu ändern. Seinen Typ können Sie nicht ändern.

    3. Sie können dem neuen Teil angebotene und erforderliche Schnittstellen (4, 5) hinzufügen. Klicken Sie auf die **bereitgestellte Schnittstelle** oder das **erforderliche Schnittstellen** Tool, und klicken Sie dann auf den Teil.

         \- oder -

         Ziehen Sie eine vorhandene Schnittstelle aus dem **UML-Modell-Explorer** auf den Teil.

         Die Schnittstellen werden dem Typ des Teils hinzugefügt und auf dem Teil selbst angezeigt. Die übergeordnete Komponente passt bei Bedarf die Größe an.

2. Verbinden Sie die Teile miteinander.

    - Verwenden Sie das **Abhängigkeits** Tool, um die Ports verschiedener Teile (6) zu verbinden.

3. Verbinden Sie die Teile mit den Ports der übergeordneten Komponente:

    1. Erstellen Sie auf der übergeordneten Komponente einen oder mehrere Ports (7). Klicken Sie in der Toolbox auf **erforderliche Schnittstelle** oder **angegebene Schnittstelle** , und klicken Sie dann auf die übergeordnete Komponente.

    2. Delegieren (9) Sie den Port an einen oder mehrere Teile. Klicken Sie auf das **Delegierungs** Tool und dann auf einen Port auf der übergeordneten Komponente und dann auf einen Anschluss an einem Teil. Sie können Ports, die Schnittstellen entweder anbieten oder erfordern, auf dieselbe Weise verbinden.

### <a name="showing-the-parts-of-a-part"></a>Anzeigen der Teile eines Teils
 Nachdem Sie eine Komponente in ihre Teile zerlegt haben, können Sie jeden Teiltyp in seine eigenen internen Bestandteile zerlegen.

 Es ist am einfachsten, jede Ebene der Zerlegung in einem separaten Komponentendiagramm durchzuführen. Sie müssen zuerst den Typ des Teils ermitteln. In der Abbildung hat einer der Teile z. B. den Namen `DNCustomerServer`, und der Typ ist eine Komponente mit dem Namen `CustomerServer`. Sie finden diesen Typ im UML-Modell-Explorer und können ihn in ein anderes Diagramm einfügen. Dann können Sie seine eigenen internen Teile erstellen.

##### <a name="to-place-a-parts-type-on-a-diagram"></a>So platzieren Sie den Typ eines Teils in einem Diagramm

1. Ermitteln Sie den vollqualifizierten Namen für den Typ des Teils.

     Klicken Sie mit der rechten Maustaste auf den Teil und dann auf **Eigenschaften**.

     Der Typname wird im **Type** -Feld des Eigenschaftenfenster angezeigt.

2. Suchen Sie im **UML-Modell-Explorer**nach dem Typ des Teils.

     Klicken Sie auf **Ansicht**, zeigen Sie auf **Weitere Fenster**, und klicken Sie dann auf **UML-Modell-Explorer**.

     Erweitern Sie das Projekt und bei Bedarf alle Pakete, zu denen der Typ gehört.

     Der Typ wird als **Komponente**aufgeführt.

     Sie können seinen Namen hier ändern, wenn Sie dies möchten.

3. Öffnen oder erstellen Sie ein weiteres Komponentendiagramm.

4. Führen Sie mit der Maus eine Ziehbewegung aus dem Typ im UML-Modell-Explorer auf das Diagramm durch.

     Eine Ansicht des Typs wird als Komponente im Diagramm angezeigt.

     Sie verfügt über die gleichen Schnittstellen, die Sie für den Teil definiert haben.

     Sie können darin jetzt Teile hinzufügen.

## <a name="designing-the-component"></a><a name="Designing"></a> Entwerfen der Komponente

### <a name="describing-how-the-parts-collaborate"></a>Beschreiben der Zusammenarbeit der Teile
 Sie können ein Sequenzdiagramm zeichnen, um darzustellen, wie die Teile als Reaktion auf eine Meldung zusammenarbeiten, die bei der übergeordneten Komponente eingeht.

 Sie können diese Diagramme verwenden, um eine vorhandene Komponente zu erläutern und um eine neue Komponente zu entwerfen.

 Wenn Sie den Entwurf der Komponente noch nicht abgeschlossen haben, können Sie Sequenzdiagramme zeichnen, bevor Sie sich entschieden haben, welche Teile darin enthalten sein sollen. Sie können Sequenzdiagramme auch verwenden, um mit verschiedenen Teilen, erforderlichen Schnittstellen und Meldungssequenzen zu experimentieren. Zeichnen Sie Sequenzdiagramme für die häufigsten und wichtigsten eingehenden Meldungen. Sie können in der Komponente dann Teile erstellen, die den Lebenslinien entsprechen, für die Sie sich entschieden haben.

 Verwenden Sie die Sequenzdiagramme, um zu bewerten, wie die Arbeitsschritte des Systems auf die verschiedenen Komponenten verteilt sind.

- Wenn ein Teil zu viele Schritte ausführen muss, ist die Anwendung möglicherweise schwieriger zu aktualisieren, als wenn die Arbeitsschritte gleichmäßig verteilt werden.

- Falls die Arbeitsschritte sehr stark verteilt sind und viele Interaktionen stattfinden, kann dies die Leistung und die Verständlichkeit des Systems beeinträchtigen.

  ![Sequenzdiagramm mit zusammenarbeitenden Teilen](../modeling/media/uml-compdescparts.png "UML_CompDescParts")

##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>So zeichnen Sie ein Sequenzdiagramm, das die Zusammenarbeit zwischen Teilen veranschaulicht

1. Erstellen Sie ein neues Sequenzdiagramm.

     Weitere Informationen finden Sie unter [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).

2. Erstellen Sie eine Lebenslinie für eine externe Komponente, einen Benutzer, ein Gerät oder einen anderen Akteur (1), der Meldungen an diese Komponente sendet.

     Sie können die **Actor** -Eigenschaft dieser Lebenslinie auf "true" festlegen, um anzugeben, dass Sie außerhalb der zu berücksichtigenden Komponente steht. Über der Lebenslinie wird ein Strichmännchen angezeigt.

3. Erstellen Sie eine Lebenslinie für die angebotene Schnittstelle (2) dieser Komponente, an die der ausgewählte Akteur Meldungen sendet.

4. Erstellen Sie eine Lebenslinie für jeden Teil (3) der Komponente.

5. Erstellen Sie eine Lebenslinie für jede erforderliche Schnittstelle (4) der Komponente.

6. Ziehen Sie Meldungen aus dem externen Akteur (5). Veranschaulichen Sie, wie die Meldung an die Teile übergeben wird und wie diese zusammenarbeiten, um auf die Meldung zu reagieren.

7. Zeigen Sie an eine erforderliche Schnittstelle (6) gesendete Meldungen an, wo dies notwendig ist. Zeigen Sie keine Details der Ausführung der Meldung an.

### <a name="is-the-component-more-than-its-parts"></a>Ist die Komponente mehr als die Summe ihrer Teile?
 In einigen Fällen ist eine Komponente lediglich ein Name für eine Auflistung von Teilen. Die gesamte Arbeit wird von den Teilen erledigt, und zur Laufzeit gibt es keinen Code oder anderes Artefakt, das die Komponente darstellt.

 Dies können Sie im Modell angeben, indem Sie die Eigenschaft **ist indirekt instanziiert** der Komponente festlegen. In diesem Fall sollten sich alle Schnittstellen der Komponente auf Ports befinden und über Delegierungen zu internen Teilen verfügen.

### <a name="describing-the-process-inside-each-part"></a>Beschreiben des Prozesses in den einzelnen Teilen
 Mithilfe von Aktivitätsdiagrammen können Sie anzeigen, wie eine Komponente die einzelnen eingehenden Meldungen verarbeitet. Weitere Informationen finden Sie unter [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).

 ![Aktivitätsdiagramm mit Datenpuffer](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")

 Verwenden Sie "Ereignisaktion akzeptieren" (1), um anzuzeigen, dass eine eingehende Meldung einen neuen Thread startet.

 Verwenden Sie Objektknoten und Eingabe-/Ausgabepins, um den Informationsfluss und die Speicherorte der Informationen anzuzeigen. Im Beispiel wird ein Objektknoten (2) verwendet, um Elemente anzuzeigen, die zwischen zwei Threads gepuffert werden.

### <a name="defining-data-and-classes"></a>Definieren von Daten und Klassen
 Mit einem UML-Klassendiagramm können Sie den ausführlichen Inhalt von folgenden Elementen beschreiben:

- Schnittstellen der Komponenten Wenn Sie eine erforderliche Komponente hinzufügen oder einen Port für eine Komponente bereitstellen, wird eine Schnittstelle im UML-Modell-Explorer angezeigt. Sie können dieses in ein UML-Klassendiagramm ziehen oder kopieren, um die Attribute und Vorgänge sowie die Beziehungen zu anderen Schnittstellen anzuzeigen.

- In den Schnittstellen über Vorgangsparameter übergebene Daten

- In den Komponenten gespeicherte Daten, wie z. B. in den Objektflüssen von Aktivitätsdiagrammen dargestellt

### <a name="general-dependencies-between-components"></a>Allgemeine Abhängigkeiten zwischen Komponenten
 Mit einem Komponentendiagramm können Sie auch nur die Hauptbestandteile des Entwurfs und deren Abhängigkeiten anzeigen.

 ![Abhängigkeit zwischen Komponenten](../modeling/media/uml-compdepend.png "UML_CompDepend")

 Verwenden Sie das **Abhängigkeits** Tool, um eine Abhängigkeit zu zeichnen. Dies gibt an, dass der Entwurf einer Komponente von einer anderen Komponente abhängt.

 Es gibt folgende typische Arten von Abhängigkeit:

- Eine Komponente ruft Code in einer anderen Komponente auf.

- Eine Komponente instanziiert eine Klasse, die innerhalb einer anderen Klasse definiert ist.

- Eine Komponente verwendet Informationen, die von einer anderen Komponente erstellt wurden.

  Sie können den Namen des Abhängigkeitspfeils verwenden, um eine bestimmte Art der Verwendung anzugeben. Um den Namen festzulegen, klicken Sie mit der rechten Maustaste auf den Pfeil, klicken Sie dann auf **Eigenschaften**, und legen Sie im Eigenschaften Fenster das Feld **Name** fest.

## <a name="see-also"></a>Weitere Informationen
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md) [UML-Komponenten Diagramme: Referenz](../modeling/uml-component-diagrams-reference.md) [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md) [UML-Anwendungsfall Diagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md) für [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md) [UML-Komponenten Diagramme: Referenz](../modeling/uml-component-diagrams-reference.md) [Video: Entwerfen der physischen Struktur mithilfe von Komponenten Diagrammen](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-6-designing-a-projects-physical-structure)
