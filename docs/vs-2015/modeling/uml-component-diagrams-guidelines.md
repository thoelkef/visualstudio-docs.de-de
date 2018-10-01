---
title: 'UML-Komponentendiagramme: Richtlinien | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2a01e81b54f5ee4a581cff4705d3751dd370bc0e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509988"
---
# <a name="uml-component-diagrams-guidelines"></a>UML-Komponentendiagramme: Richtlinien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [UML-Komponentendiagramme: Richtlinien](https://docs.microsoft.com/visualstudio/modeling/uml-component-diagrams-guidelines).  
  
Sie können in Visual Studio zeichnen eine *Komponentendiagramm* um die Struktur ein Softwaresystems darzustellen. Eine Videodemo finden Sie unter [Entwerfen der physischen Struktur mithilfe von Komponentendiagrammen](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/).  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Zum Erstellen eines UML-Komponentendiagramms, auf die **Architektur** Menü klicken Sie auf **neues UML- oder Ebenendiagramm**.  
  
 Eine Komponente ist eine modulare Einheit, die innerhalb ihrer Umgebung austauschbar ist. Interne Daten sind ausgeblendet, aber sie verfügt über einen oder mehrere klar definierte *bereitgestellte Schnittstellen* über die zugehörigen Funktionen zugegriffen werden können. Eine Komponente kann auch verfügen *erforderlichen Schnittstellen*. Eine erforderliche Schnittstelle definiert, welche Funktionen oder Dienste von anderen Komponenten benötigt werden. Indem die angebotenen und erforderlichen Schnittstellen mehrerer Komponenten verknüpft werden, kann eine größere Komponente erstellt werden. Ein vollständiges Softwaresystem kann auch als Komponente verstanden werden.  
  
 Das Zeichnen von Komponentendiagrammen hat mehrere Vorteile:  
  
-   Wenn sich das Entwicklungsteam auf die Hauptblöcke eines Entwurfs konzentriert, kann es ein besseres Verständnis des vorhandenen Entwurfs entwickeln und einen entsprechenden neuen Entwurf erstellen.  
  
-   Indem Sie sich Ihr System als Auflistung von Komponenten mit klar definierten angebotenen und erforderlichen Schnittstellen vorstellen, optimieren Sie die Abgrenzung zwischen den Komponenten. Dadurch ist der Entwurf einfacher zu verstehen, und der Entwurf kann bei sich ändernden Anforderungen auch einfacher angepasst werden.  
  
 Sie können ein Komponentendiagramm verwenden, um den Entwurf unabhängig von der verwendeten Sprache oder Plattform darzustellen.  
  
##  <a name="OtherDiagrams"></a> Beziehung zu anderen Diagrammen  
 Sie können ein Komponentendiagramm in Verbindung mit anderen Diagrammen verwenden.  
  
|Anderes Diagramm|Unterstützt Sie beim Diskutieren und Kommunizieren dieser Aspekte des Entwurfs.|  
|-------------------|--------------------------------------------------------------------|  
|UML-Sequenzdiagramm|-Interaktionen zwischen den Komponenten eines Systems<br />-Interaktionen zwischen den Teilen innerhalb einer Komponente.<br /><br /> Weitere Informationen finden Sie unter [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).|  
|UML-Klassendiagramm|– Die Schnittstellen einer Komponente. Mit dem Klassendiagramm können Sie die Methoden der Schnittstelle detailliert angeben.<br />-Die Daten, die in Parametern über die Schnittstellen der Komponenten gesendet wird.<br /><br /> Weitere Informationen finden Sie unter [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md).|  
|Aktivitätsdiagramme|-Die interne Verarbeitung, die von einer Komponente als Reaktion auf eingehende Nachrichten ausgeführt wird.<br /><br /> Weitere Informationen finden Sie unter [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).|  
|Ebenendiagramme|-Logische Architekturebenen für Ihre Komponenten.<br /><br /> Weitere Informationen finden Sie unter [Ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md).|  
  
##  <a name="Basics"></a> Grundlegende Schritte zum Zeichnen von Komponentendiagrammen  
 Referenzinformationen zu den Elementen in Komponentendiagrammen finden Sie unter [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md).  
  
 Weitere Informationen zur Verwendung von Komponentendiagrammen während des Entwurfsprozesses finden Sie unter [Modellieren der Architektur Ihrer app](../modeling/model-your-app-s-architecture.md).  
  
> [!NOTE]
>  Ausführliche Schritte zum Erstellen der Modellierungsdiagramme beschrieben sind [Bearbeiten von UML-Modellen und Diagrammen](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-component-diagram"></a>So erstellen Sie ein Komponentendiagramm  
  
1.  Auf der **Architektur** Menü klicken Sie auf **neues UML- oder Ebenendiagramm**.  
  
2.  Klicken Sie unter **Vorlagen**, klicken Sie auf **UML-Komponentendiagramm**.  
  
3.  Benennen Sie das Diagramm.  
  
4.  In **zu Modellierungsprojekt hinzufügen**, wählen Sie ein vorhandenes Modellierungsprojekt aus, in der Projektmappe oder **Neues Modellierungsprojekt erstellen**, und klicken Sie dann auf **OK**...  
  
     Ein neues Komponentendiagramm angezeigt wird, mit der UML- **Komponentendiagramm** Toolbox. Die Toolbox enthält die erforderlichen Elemente und Beziehungen.  
  
### <a name="drawing-components"></a>Zeichnen von Komponenten  
 ![Komponenten mit Schnittstellen](../modeling/media/uml-compdrawing.png "UML_CompDrawing")  
  
 Erstellen Sie eine *Komponente* (1) für jede Hauptfunktionseinheit im System oder Anwendung.  
  
 Beispiele hierfür sind eine Anwendung, ein Hardwaregerät, ein Webdienst, eine .NET-Assembly, eine Programmklasse oder eine Gruppe von Klassen oder ein beliebiges anderes Hauptsegment eines Programms.  
  
##### <a name="to-create-components"></a>So erstellen Sie Komponenten  
  
1.  Klicken Sie auf **Komponente** in der Toolbox, und klicken Sie dann auf einen leeren Bereich des Diagramms.  
  
     \- oder –  
  
     Kopieren Sie eine vorhandene Komponente, und fügen Sie diese ein.  
  
    1.  Suchen Sie eine vorhandene Komponente in einem Diagramm oder im **UML-Modell-Explorer**.  
  
    2.  Mit der rechten Maustaste in der Komponente, und klicken Sie dann auf **Kopie**.  
  
    3.  Öffnen Sie das Diagramm, in dem die kopierte Komponente angezeigt werden soll.  
  
    4.  Mit der rechten Maustaste in eines leeren Bereich des Diagramms, und klicken Sie dann auf **einfügen**.  
  
         Eine Kopie der Komponente wird unter einem neuen Namen angezeigt.  
  
2.  Klicken Sie auf den Namen der Komponente, um ihn zu ändern.  
  
3.  Klicken Sie auf das Chevron (5), wenn Sie nur den Header der Komponente anzeigen möchten.  
  
### <a name="showing-the-ports-of-a-component"></a>Anzeigen der Ports einer Komponente  
 Ein *Port* (2, 3) steht für eine Gruppe von Meldungen oder Vorgangsaufrufen, die entweder in oder aus einer Komponente zu übergeben. Die Gruppe wird von einer Schnittstelle beschrieben, die den Typ des Ports definiert. Ein Port kann entweder eine Schnittstelle anbieten oder eine Schnittstelle erfordern.  
  
 Ein Port mit einem *bereitgestellte Schnittstelle* (2) stellt Vorgänge, die von der Komponente implementiert werden und, die von anderen Komponenten verwendet werden kann.  
  
 Beispiele sind eine Benutzeroberfläche, ein Webdienst, eine .NET-Schnittstelle oder eine Auflistung von Funktionen in einer beliebigen Programmiersprache.  
  
 Ein Port mit einem *erforderliche Schnittstelle* (3) stellt die Anforderung einer Komponente für eine Gruppe von Vorgängen oder Diensten von anderen Komponenten oder externen Systemen bereitgestellt werden.  
  
 Ein Webbrowser erfordert z. B. Webserver, und ein Anwendungs-Add-In erfordert die Dienste einer Anwendung.  
  
 Eine Komponente kann über eine beliebige Anzahl von Ports verfügen.  
  
##### <a name="to-add-ports-to-a-component"></a>So fügen Sie einer Komponente Ports hinzu  
  
1.  Klicken Sie in der Toolbox auf **angebotene Schnittstelle** oder **erforderliche Schnittstelle**.  
  
2.  Klicken Sie auf die Komponente, der Sie Ports hinzufügen möchten.  
  
     Ein Port wird an der Begrenzung der Komponente angezeigt.  
  
     Eine neue Schnittstelle wird als Typ des Ports erstellt. Diese Schnittstelle wird angezeigt, **UML-Modell-Explorer**.  
  
3.  Ziehen Sie den Port mit der Maus entlang der Komponentenbegrenzung, um ihn wie gewünscht zu platzieren.  
  
4.  Ziehen Sie die Bezeichnung des Ports, um die Position anzupassen.  
  
5.  Klicken Sie auf die Bezeichnung, um sie zu ändern. Die Bezeichnung zeigt den Namen der Schnittstelle an. Wenn Sie diesen ändern, ändern Sie den Namen der Schnittstelle.  
  
 Wenn Sie die Attribute und Vorgänge der Schnittstelle aufführen möchten, fügen Sie sie der Schnittstelle im UML-Modell-Explorer hinzu. Alternativ können Sie die Schnittstelle aus dem UML-Modell-Explorer in ein Klassendiagramm ziehen und dort die Vorgänge und Attribute hinzufügen.  
  
### <a name="linking-between-components"></a>Erstellen von Verknüpfungen zwischen Komponenten  
 Verwenden Sie eine Abhängigkeit (4), um anzuzeigen, dass die Anforderung einer Komponente von den Vorgängen oder Diensten erfüllt werden kann, die von einer anderen Komponente bereitgestellt werden.  
  
##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>So zeigen Sie an, dass eine angebotene Schnittstelle die Anforderungen einer erforderlichen Schnittstelle erfüllen kann  
  
1.  Klicken Sie in der Toolbox auf **Abhängigkeit**.  
  
2.  Klicken Sie in einer Komponente auf den Port mit der erforderlichen Schnittstelle und dann in einer anderen Komponente auf den Port mit der angebotenen Schnittstelle.  
  
 Sie sollten es vermeiden, Abhängigkeitsschleifen zu entwerfen, bei denen alle Komponenten einer Gruppe von allen anderen Komponenten abhängig sind.  
  
##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>So fügen Sie einer Komponente einen Port für eine vorhandene Schnittstelle hinzu  
  
-   Suchen Sie die Schnittstelle in **UML-Modell-Explorer** und ziehen Sie es von dort auf die Komponente aus.  
  
     - oder -   
  
-   Kopieren Sie einen Verweis auf eine Schnittstelle aus einem Diagramm, und fügen Sie ihn ein.  
  
    1.  Klicken Sie auf ein Klassendiagramm oder Komponentendiagramm eine Komponente, mit der rechten Maustaste in der Schnittstelle, und klicken Sie dann auf **Kopie**.  
  
    2.  Klicken Sie auf dem Komponentendiagramm mit der rechten Maustaste in der Komponente, und klicken Sie dann auf **Verweis einfügen**.  
  
         Eine angebotene Schnittstelle wird auf der Komponente angezeigt. Daneben wird ein Aktionstag angezeigt.  
  
        > [!NOTE]
        >  Bei Verwendung von **einfügen** anstelle von **Verweis einfügen**, eine neue Schnittstelle mit einem neuen Namen erstellt werden.  
  
    3.  Wenn Sie eine erforderliche Schnittstelle erstellen möchten, klicken Sie auf das Aktionstag, und klicken Sie dann auf **in erforderliche Schnittstelle konvertieren**.  
  
##  <a name="Parts"></a> Anzeigen der internen Teile einer Komponente  
 ![Komponentendiagramm mit internen Teilen](../modeling/media/uml-compshowing.png "UML_CompShowing")  
  
 Sie können Teile (3) in einer Komponente (1) platzieren, um anzuzeigen, wie diese aus kleineren Komponenten zusammengesetzt ist, die miteinander interagieren.  
  
 Das Diagramm in der Abbildung gibt an, dass jede Instanz vom Typ "Dinner Now Web Service" eine Instanz von "Customer Server" und eine Instanz von "Kitchen Server" enthält.  
  
 Ein Teil ist eine Eigenschaft seiner übergeordneten Komponente, so wie ein Attribut einer normalen Klasse angehört. Ein Teil hat seinen eigenen Typ, der normalerweise auch eine Komponente ist. Die Bezeichnung des Teils hat die gleiche Form wie ein normales Attribut:  
  
 `+ partName : TypeName`  
  
 In der übergeordneten Komponente zeigt jeder Teil die angebotenen und erforderlichen Schnittstellen an, die für seinen Typ (4, 5) definiert sind. Die Vorgänge und Dienste, die für einen Teil erforderlich sind, können von einem anderen Teil bereitgestellt werden. Sie können **Teilassembly** Connectors zu zeigen, wie Teile miteinander (6) verbunden sind.  
  
 Sie können auch anzeigen, dass eine Schnittstelle der übergeordneten Komponente von einem ihrer Teile angeboten wird oder dafür erforderlich ist. Sie können einen Port des übergeordneten Elements eine Verbindung herstellen, an einen Port eines internen Teils mithilfe einer **Delegierung** Beziehung (9). Die zwei Ports müssen vom gleichen Typ sein (angeboten oder erforderlich), und ihre Schnittstellentypen müssen kompatibel sein.  
  
 Sie können einen neuen Teil entweder mit einem neuen Typ oder aus einem vorhandenen Typ erstellen.  
  
#### <a name="to-add-parts-to-a-component"></a>So fügen Sie einer Komponente Teile hinzu  
  
1.  Erstellen Sie einen Teil für jede Hauptfunktionseinheit, die Bestandteil der übergeordneten Komponente ist.  
  
    1.  Klicken Sie auf **Komponente** in der Toolbox, und klicken Sie dann innerhalb der übergeordneten Komponente (1).  
  
         Ein neuer Teil (3) wird in der übergeordneten Komponente angezeigt.  
  
         Erstellt eine neue Komponente **UML-Modell-Explorer**. Dies ist der Typ des neuen Teils.  
  
         \- oder –  
  
         Ziehen Sie eine vorhandene Komponente aus dem UML-Modell-Explorer auf die übergeordnete Komponente.  
  
         Ein neuer Teil (3) wird in der übergeordneten Komponente angezeigt. Der Typ ist die Komponente, die Sie aus dem UML-Modell-Explorer gezogen haben.  
  
         \- oder –  
  
         Mit der rechten Maustaste einer Komponente, die in einem Diagramm oder im UML-Modell-Explorer, und klicken Sie dann auf **Kopie**.  
  
         Mit der rechten Maustaste auf die übergeordnete Komponente, und klicken Sie dann auf **Verweis einfügen**.  
  
         Ein neuer Teil (3) wird in der übergeordneten Komponente angezeigt. Sein Typ ist die Komponente, die Sie kopiert haben.  
  
    2.  Klicken Sie auf den Namen des neuen Teils, um ihn zu ändern. Seinen Typ können Sie nicht ändern.  
  
    3.  Sie können dem neuen Teil angebotene und erforderliche Schnittstellen (4, 5) hinzufügen. Klicken Sie auf die **angebotene Schnittstelle** oder **erforderliche Schnittstelle** tool, und klicken Sie dann im Bereich auf.  
  
         \- oder –  
  
         Ziehen Sie eine vorhandene Schnittstelle aus **UML-Modell-Explorer** auf den Teil.  
  
         Die Schnittstellen werden dem Typ des Teils hinzugefügt und auf dem Teil selbst angezeigt. Die übergeordnete Komponente passt bei Bedarf die Größe an.  
  
2.  Verbinden Sie die Teile miteinander.  
  
    -   Verwenden der **Abhängigkeit** Tool, um die Ports verschiedener Teile (6) verbinden.  
  
3.  Verbinden Sie die Teile mit den Ports der übergeordneten Komponente:  
  
    1.  Erstellen Sie auf der übergeordneten Komponente einen oder mehrere Ports (7). Klicken Sie auf **erforderliche Schnittstelle** oder **angebotene Schnittstelle** in der Toolbox, und klicken Sie dann auf die übergeordnete Komponente.  
  
    2.  Delegieren (9) Sie den Port an einen oder mehrere Teile. Klicken Sie auf die **Delegierung** -Tool, und klicken Sie dann einen Port der übergeordneten Komponente und klicken Sie dann einen Port eines Teils. Sie können Ports, die Schnittstellen entweder anbieten oder erfordern, auf dieselbe Weise verbinden.  
  
### <a name="showing-the-parts-of-a-part"></a>Anzeigen der Teile eines Teils  
 Nachdem Sie eine Komponente in ihre Teile zerlegt haben, können Sie jeden Teiltyp in seine eigenen internen Bestandteile zerlegen.  
  
 Es ist am einfachsten, jede Ebene der Zerlegung in einem separaten Komponentendiagramm durchzuführen. Sie müssen zuerst den Typ des Teils ermitteln. In der Abbildung hat einer der Teile z. B. den Namen `DNCustomerServer`, und der Typ ist eine Komponente mit dem Namen `CustomerServer`. Sie finden diesen Typ im UML-Modell-Explorer und können ihn in ein anderes Diagramm einfügen. Dann können Sie seine eigenen internen Teile erstellen.  
  
##### <a name="to-place-a-parts-type-on-a-diagram"></a>So platzieren Sie den Typ eines Teils in einem Diagramm  
  
1.  Ermitteln Sie den vollqualifizierten Namen für den Typ des Teils.  
  
     Mit der rechten Maustaste des Teils, und klicken Sie dann auf **Eigenschaften**.  
  
     Der Typname wird der **Typ** Feld des Eigenschaftenfensters angezeigt.  
  
2.  Suchen Sie den Typ des Teils in **UML-Modell-Explorer**.  
  
     Klicken Sie auf **Ansicht**, zeigen Sie auf **Other Windows**, und klicken Sie dann auf **UML-Modell-Explorer**.  
  
     Erweitern Sie das Projekt und bei Bedarf alle Pakete, zu denen der Typ gehört.  
  
     Der Typ wird er als ein **Komponente**.  
  
     Sie können seinen Namen hier ändern, wenn Sie dies möchten.  
  
3.  Öffnen oder erstellen Sie ein weiteres Komponentendiagramm.  
  
4.  Führen Sie mit der Maus eine Ziehbewegung aus dem Typ im UML-Modell-Explorer auf das Diagramm durch.  
  
     Eine Ansicht des Typs wird als Komponente im Diagramm angezeigt.  
  
     Sie verfügt über die gleichen Schnittstellen, die Sie für den Teil definiert haben.  
  
     Sie können darin jetzt Teile hinzufügen.  
  
##  <a name="Designing"></a> Entwerfen der Komponente  
  
### <a name="describing-how-the-parts-collaborate"></a>Beschreiben der Zusammenarbeit der Teile  
 Sie können ein Sequenzdiagramm zeichnen, um darzustellen, wie die Teile als Reaktion auf eine Meldung zusammenarbeiten, die bei der übergeordneten Komponente eingeht.  
  
 Sie können diese Diagramme verwenden, um eine vorhandene Komponente zu erläutern und um eine neue Komponente zu entwerfen.  
  
 Wenn Sie den Entwurf der Komponente noch nicht abgeschlossen haben, können Sie Sequenzdiagramme zeichnen, bevor Sie sich entschieden haben, welche Teile darin enthalten sein sollen. Sie können Sequenzdiagramme auch verwenden, um mit verschiedenen Teilen, erforderlichen Schnittstellen und Meldungssequenzen zu experimentieren. Zeichnen Sie Sequenzdiagramme für die häufigsten und wichtigsten eingehenden Meldungen. Sie können in der Komponente dann Teile erstellen, die den Lebenslinien entsprechen, für die Sie sich entschieden haben.  
  
 Verwenden Sie die Sequenzdiagramme, um zu bewerten, wie die Arbeitsschritte des Systems auf die verschiedenen Komponenten verteilt sind.  
  
-   Wenn ein Teil zu viele Schritte ausführen muss, ist die Anwendung möglicherweise schwieriger zu aktualisieren, als wenn die Arbeitsschritte gleichmäßig verteilt werden.  
  
-   Falls die Arbeitsschritte sehr stark verteilt sind und viele Interaktionen stattfinden, kann dies die Leistung und die Verständlichkeit des Systems beeinträchtigen.  
  
 ![Sequenzieren Komponentendiagramm mit zusammenarbeitenden teilen](../modeling/media/uml-compdescparts.png "UML_CompDescParts")  
  
##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>So zeichnen Sie ein Sequenzdiagramm, das die Zusammenarbeit zwischen Teilen veranschaulicht  
  
1.  Erstellen Sie ein neues Sequenzdiagramm.  
  
     Weitere Informationen finden Sie unter [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).  
  
2.  Erstellen Sie eine Lebenslinie für eine externe Komponente, einen Benutzer, ein Gerät oder einen anderen Akteur (1), der Meldungen an diese Komponente sendet.  
  
     Sie können festlegen, die **Actor** Eigenschaft dieser Lebenslinie auf "true", um anzugeben, dass sie außerhalb der jeweiligen Komponente. Über der Lebenslinie wird ein Strichmännchen angezeigt.  
  
3.  Erstellen Sie eine Lebenslinie für die angebotene Schnittstelle (2) dieser Komponente, an die der ausgewählte Akteur Meldungen sendet.  
  
4.  Erstellen Sie eine Lebenslinie für jeden Teil (3) der Komponente.  
  
5.  Erstellen Sie eine Lebenslinie für jede erforderliche Schnittstelle (4) der Komponente.  
  
6.  Ziehen Sie Meldungen aus dem externen Akteur (5). Veranschaulichen Sie, wie die Meldung an die Teile übergeben wird und wie diese zusammenarbeiten, um auf die Meldung zu reagieren.  
  
7.  Zeigen Sie an eine erforderliche Schnittstelle (6) gesendete Meldungen an, wo dies notwendig ist. Zeigen Sie keine Details der Ausführung der Meldung an.  
  
### <a name="is-the-component-more-than-its-parts"></a>Ist die Komponente mehr als die Summe ihrer Teile?  
 In einigen Fällen ist eine Komponente lediglich ein Name für eine Auflistung von Teilen. Die gesamte Arbeit wird von den Teilen erledigt, und zur Laufzeit gibt es keinen Code oder anderes Artefakt, das die Komponente darstellt.  
  
 Sie können dies im Modell angeben, durch Festlegen der **Is Indirectly Instantiated** -Eigenschaft der Komponente. In diesem Fall sollten sich alle Schnittstellen der Komponente auf Ports befinden und über Delegierungen zu internen Teilen verfügen.  
  
### <a name="describing-the-process-inside-each-part"></a>Beschreiben des Prozesses in den einzelnen Teilen  
 Mithilfe von Aktivitätsdiagrammen können Sie anzeigen, wie eine Komponente die einzelnen eingehenden Meldungen verarbeitet. Weitere Informationen finden Sie unter [UML-Aktivitätsdiagramme: Richtlinien](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Aktivitätsdiagramm mit Datenpuffer](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")  
  
 Verwenden Sie "Ereignisaktion akzeptieren" (1), um anzuzeigen, dass eine eingehende Meldung einen neuen Thread startet.  
  
 Verwenden Sie Objektknoten und Eingabe-/Ausgabepins, um den Informationsfluss und die Speicherorte der Informationen anzuzeigen. Im Beispiel wird ein Objektknoten (2) verwendet, um Elemente anzuzeigen, die zwischen zwei Threads gepuffert werden.  
  
### <a name="defining-data-and-classes"></a>Definieren von Daten und Klassen  
 Mit einem UML-Klassendiagramm können Sie den ausführlichen Inhalt von folgenden Elementen beschreiben:  
  
-   Schnittstellen der Komponenten Wenn Sie eine erforderliche Komponente hinzufügen oder einen Port für eine Komponente bereitstellen, wird eine Schnittstelle im UML-Modell-Explorer angezeigt. Sie können dieses in ein UML-Klassendiagramm ziehen oder kopieren, um die Attribute und Vorgänge sowie die Beziehungen zu anderen Schnittstellen anzuzeigen.  
  
-   In den Schnittstellen über Vorgangsparameter übergebene Daten  
  
-   In den Komponenten gespeicherte Daten, wie z. B. in den Objektflüssen von Aktivitätsdiagrammen dargestellt  
  
### <a name="general-dependencies-between-components"></a>Allgemeine Abhängigkeiten zwischen Komponenten  
 Mit einem Komponentendiagramm können Sie auch nur die Hauptbestandteile des Entwurfs und deren Abhängigkeiten anzeigen.  
  
 ![Eine Abhängigkeit zwischen Komponenten](../modeling/media/uml-compdepend.png "UML_CompDepend")  
  
 Verwenden der **Abhängigkeit** Tool, um eine Abhängigkeit zu zeichnen. Dies gibt an, dass der Entwurf einer Komponente von einer anderen Komponente abhängt.  
  
 Es gibt folgende typische Arten von Abhängigkeit:  
  
-   Eine Komponente ruft Code in einer anderen Komponente auf.  
  
-   Eine Komponente instanziiert eine Klasse, die innerhalb einer anderen Klasse definiert ist.  
  
-   Eine Komponente verwendet Informationen, die von einer anderen Komponente erstellt wurden.  
  
 Sie können den Namen des Abhängigkeitspfeils verwenden, um eine bestimmte Art der Verwendung anzugeben. Um den Namen festzulegen, mit der rechten Maustaste des Pfeils, und klicken Sie dann **Eigenschaften**, und legen Sie die **Namen** Feld im Eigenschaftenfenster.  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)   
 [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)   
 [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)   
 [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)   
 [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)   
 [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)   
 [Video: Entwerfen der physischen Struktur mithilfe von Komponentendiagrammen](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/)



