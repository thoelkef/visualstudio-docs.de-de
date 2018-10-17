---
title: 'Abhängigkeitsdiagramme: Richtlinien'
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 262dfd7860c5bd16c210e7305599eeb1003372fe
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860068"
---
# <a name="dependency-diagrams-guidelines"></a>Abhängigkeitsdiagramme: Richtlinien

Beschreiben Sie die Architektur Ihrer app auf einer hohen Ebene erstellen *Abhängigkeitsdiagramme* in Visual Studio. Stellen Sie sicher, dass Ihr Code und Entwurf konsistent bleiben, indem Sie überprüfen Ihres Codes mit einem Abhängigkeitsdiagramm. Sie können auch eine Ebenenvalidierung im Buildprozess einschließen. Finden Sie unter [Channel 9-Video: Entwerfen und Überprüfen der Architektur, die mithilfe von Abhängigkeitsdiagrammen](http://go.microsoft.com/fwlink/?LinkID=252073).

Welche Editionen von Visual Studio dieses Feature unterstützen, finden Sie unter [Edition-Unterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Abhängigkeitsdiagramme werden für .NET Core-Projekte in Visual Studio 2017 nicht unterstützt.

## <a name="what-is-a-dependency-diagram"></a>Was ist ein Abhängigkeitsdiagramm?

Wie einem herkömmlichen Architekturdiagramm identifiziert ein Abhängigkeitsdiagramm, die wichtigsten Komponenten oder Funktionseinheiten des Entwurfs sowie ihre Abhängigkeiten. Jeder Knoten im Diagramm mit der Bezeichnung eine *Ebene*, stellt eine logische Gruppe von Namespaces, Projekte oder andere Artefakte. Sie können die Abhängigkeiten zeichnen, die im Entwurf vorhanden sein sollen. Anders als bei einem herkömmlichen Architekturdiagramm können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Quellcode den gewünschten Abhängigkeiten entsprechen, die Sie angegeben haben. Indem Sie die Validierung zu einem Bestandteil eines regulären Buildvorgangs in [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] machen, stellen Sie sicher, dass der Programmcode auch in zukünftigen Änderungen mit der Architektur des Systems übereinstimmt. Finden Sie unter [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>So entwerfen oder aktualisieren Sie Ihre app mit Abhängigkeitsdiagrammen

Die folgenden Schritte bieten einen Überblick zu Abhängigkeitsdiagrammen im Entwicklungsprozess verwenden. In späteren Abschnitten dieses Themas werden die einzelnen Schritte ausführlicher beschrieben. Wenn Sie einen neuen Entwurf entwickeln, lassen Sie die Schritte aus, die sich auf vorhandenen Code beziehen.

> [!NOTE]
> Die Schritte entsprechen ungefähr der tatsächlichen Reihenfolge. Wahrscheinlich werden Sie die Aufgaben überlappend ausführen, die Reihenfolge Ihrer eigenen Situation anpassen und am Anfang jeder Iteration im Projekt nochmals auf die Beschreibung der Schritte zurückkommen.

1.  [Erstellen Sie ein Abhängigkeitsdiagramm](#Create) für die gesamte Anwendung oder für eine Ebene in der Anwendung.

2.  [Ebenen definieren, um die wichtigsten Funktionsbereiche oder Komponenten darzustellen](#CreateLayers) Ihrer Anwendung. Benennen Sie diese Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". Wenn Sie Visual Studio-Projektmappe haben, können Sie eine Auflistung von einzelnen Ebenen zuordnen *Artefakte*, z. B. Projekte, Namespaces, Dateien und So weiter.

3.  [Ermitteln Sie die vorhandenen Abhängigkeiten](#Generate) zwischen Ebenen.

4.  [Bearbeiten Sie die Ebenen und Abhängigkeiten](#EditArchitecture) anzuzeigenden der aktualisierten Entwurf, der den Code entsprechend angezeigt werden soll.

5.  [Entwerfen Sie neue Bereiche der Anwendung](#NewAreas) Ebenen erstellen, um die wichtigsten architekturblöcke oder-Komponenten darzustellen, und Definieren von Abhängigkeiten, um anzuzeigen, wie jede Ebene die anderen verwendet.

6.  [Bearbeiten Sie das Layout und die Darstellung des Diagramms](#EditLayout) können Sie es mit Kollegen erörtern.

7.  [Überprüfen Sie den Code anhand des Diagramms Abhängigkeit](#Validate) um die Konflikte zwischen dem Code und die Architektur, die Sie benötigen.

8.  [Aktualisieren Sie den Code der neuen Architektur entspricht](#UpdateCode). Führen Sie die Entwicklung und Umgestaltung von Code in Iterationen durch, bis bei der Validierung keine Konflikte auftreten.

9. [Schließen Sie ebenenvalidierung im Buildprozess](#BuildValidation) , stellen Sie sicher, dass der Code weiterhin dem Entwurf entspricht.

## <a name="Create"></a> Erstellen Sie ein Abhängigkeitsdiagramm

Ein Abhängigkeitsdiagramm muss in einem Modellierungsprojekt erstellt werden. Sie können einem vorhandenen Modellierungsprojekt ein neues Abhängigkeitsdiagramm hinzugefügt, erstellen ein neues Modellierungsprojekt für das Abhängigkeitsdiagramm oder kopieren Sie ein vorhandene Abhängigkeitsdiagramm im gleichen Modellierungsprojekt.

> [!IMPORTANT]
> DO nicht hinzuzufügen Sie, ziehen Sie oder kopieren Sie ein vorhandenes Abhängigkeitsdiagramm von einem Modellierungsprojekt in ein anderes Modellierungsprojekt oder an einen anderen Speicherort in der Projektmappe. Ein Abhängigkeitsdiagramm, die auf diese Weise kopiert werden, müssen die gleichen Verweise wie das ursprüngliche Diagramm, auch wenn Sie das Diagramm ändern. Dies verhindert das ordnungsgemäße Funktionieren der Ebenenvalidierung und verursacht möglicherweise andere Probleme, z. B. fehlende Elemente oder andere Fehler beim Versuch, das Diagramm zu öffnen.

Finden Sie unter [Erstellen von Abhängigkeitsdiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a> Definieren Sie Ebenen, um Funktionsbereiche oder Komponenten darzustellen

Ebenen stellen logische Gruppen von dar *Artefakte*, z. B. Projekte, Codedateien, Namespaces, Klassen und Methoden. Sie können Ebenen aus Artefakten aus Visual c# und Visual Basic-Projekte erstellen, oder Sie können Spezifikationen oder Plänen zu einer Ebene anfügen, durch das Verknüpfen von Dokumenten, z. B. Word-Dateien oder PowerPoint-Präsentationen. Jede Ebene wird im Diagramm als Rechteck angezeigt und gibt Aufschluss über die Anzahl der mit ihr verknüpften Artefakte. Eine Ebene kann geschachtelte Ebenen enthalten, um spezielle Aufgaben zu beschreiben.

Benennen Sie als allgemeine Richtlinie Ebenen nach ihrer Funktion, z. B. "Präsentation" oder "Dienste". Fügen Sie Artefakte in der gleichen Ebene ein, wenn zwischen ihnen eine enge Abhängigkeit besteht. Wenn die Artefakte getrennt voneinander aktualisiert oder in separaten Anwendungen verwendet werden können, sollten sie auf unterschiedlichen Ebenen eingefügt werden. Informationen zu Ebenenmuster finden Sie auf der Patterns & Practices-Website unter [ http://go.microsoft.com/fwlink/?LinkId=145794 ](http://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> Es gibt bestimmte Arten von Artefakten, die Sie mit Ebenen verknüpfen können, die Überprüfung anhand des Diagramms für die Abhängigkeit nicht unterstützen. Öffnen Sie zum Anzeigen, ob das Artefakt die Validierung unterstützt **Ebenen-Explorer** Untersuchen der **unterstützt die Validierung** Eigenschaft des Artefaktlinks. Finden Sie unter [vorhandene Abhängigkeiten zwischen Ebenen ermitteln](#Generate).

Bei der Aktualisierung einer nicht vertrauten Anwendung können Sie auch Codezuordnungen erstellen. Diese Diagramme können Ihnen helfen, Muster und Abhängigkeiten zu ermitteln, während Sie den Code untersuchen. Mithilfe des Projektmappen-Explorers können Namespaces und Klassen untersucht werden, die häufig den vorhandenen Ebenen entsprechen. Weisen Sie diese Codeartefakte Ebenen, indem Sie sie im Projektmappen-Explorer zu Abhängigkeitsdiagrammen ziehen. Sie können Abhängigkeitsdiagramme dann verwenden, können Sie den Code aktualisieren, und bewahren Sie sie mit dem Entwurf konsistent.

Thema

-   [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)

-   [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)

-   [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a> Vorhandene Abhängigkeiten zwischen Ebenen ermitteln

Eine Abhängigkeit ist überall dort vorhanden, wo ein Artefakt, das einer Ebene zugeordnet ist, einen Verweis auf ein Artefakt enthält, das einer anderen Ebene zugeordnet ist. Beispiel: Eine Klasse in einer Ebene deklariert eine Variable, deren Klasse sich auf einer anderen Ebene befindet. Vorhandene Abhängigkeiten können mittels Reverse Engineering (Zurückentwicklung) ermittelt werden.

> [!NOTE]
> Bei bestimmten Arten von Artefakten ist kein Reverse Engineering der Abhängigkeiten möglich. So kann beispielsweise bei einer Ebene, die mit einer Textdatei verknüpft ist, keinerlei Rückentwicklung der Abhängigkeiten vorgenommen werden. Um anzuzeigen, welche Elemente über Abhängigkeiten verfügen, können Sie die Reverse-Engineering, mit der rechten Maustaste in eine oder mehrere Ebenen aus, und klicken Sie dann auf **Links anzeigen**. In **Ebenen-Explorer**, überprüfen Sie die **unterstützt die Validierung** Spalte. Abhängigkeiten werden nicht für Elemente, die für die in dieser Spalte wird Reverse Engineering **"false"**.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>So entwickeln Sie vorhandene Abhängigkeiten zwischen Ebenen zurück

Wählen Sie eine Ebene oder mehrere Ebenen, mit der rechten Maustaste in der ausgewählten Ebene, und klicken Sie dann auf **Abhängigkeiten generieren**.

In der Regel sind einige unerwünschte Abhängigkeiten vorhanden. Diese Abhängigkeiten können bearbeitet werden, um sie mit dem geplanten Entwurf in Einklang zu bringen.

## <a name="EditArchitecture"></a> Bearbeiten von Ebenen und Abhängigkeiten auf den vorgesehenen Entwurf anzeigen

Beschreibung die Änderungen, die Sie an Ihrem System oder der vorgesehenen Architektur vornehmen möchten, verwenden Sie die folgenden Schritte aus, um das Abhängigkeitsdiagramm zu bearbeiten. Sie können vor dem Erweitern des Codes ggf. auch einige Refactoringänderungen vornehmen, um die Codestruktur zu verbessern. Finden Sie unter [Verbessern der Struktur des Codes](#Improving).

|**Aktion**|**Führen Sie diese Schritte aus**|
|------------|-----------------------------|
|Löschen einer unerwünschten Abhängigkeit|Klicken Sie auf die Abhängigkeit, und drücken Sie dann die **löschen**.|
|Ändern oder Einschränken der Richtung einer Abhängigkeit|Legen Sie dessen **Richtung** Eigenschaft.|
|Erstellen von neuen Abhängigkeiten|Verwenden der **Abhängigkeit** und **bidirektionale Abhängigkeit** Tools.<br /><br /> Doppelklicken Sie zum Zeichnen mehrerer Abhängigkeiten auf das Tool. Wenn Sie fertig sind, klicken Sie auf die **Zeiger** Tool, oder drücken Sie die **ESC** Schlüssel.|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht von den angegebenen Namespaces abhängen dürfen|Geben Sie die Namespaces in der Ebene des **verboten Namespace Dependencies** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|
|Angeben, dass einer Ebene zugeordnete Artefakte nicht zu den angegebenen Namespaces gehören dürfen|Geben Sie die Namespaces in der Ebene des **Unzulässige Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|
|Angeben, dass einer Ebene zugeordnete Artefakte zu einem der angegebenen Namespaces gehören müssen|Geben Sie den Namespace in der Ebene des **erforderliche Namespaces** Eigenschaft. Verwenden Sie ein Semikolon (**;**) trennen Sie die Namespaces.|

### <a name="Improving"></a> Verbessern der Struktur des Codes

Refactoringänderungen sind Verbesserungen, die das Verhalten der Anwendung nicht ändern, jedoch zukünftige Änderungen und Erweiterungen des Codes erleichtern. Gut strukturierter Code verfügt über ein Design, das ist einfach, um ein Abhängigkeitsdiagramm zu abstrahieren.

Wenn Sie z. B. eine Ebene für jeden Namespace im Code erstellen und die Abhängigkeiten dann zurück entwickeln, sollte die Anzahl unidirektionaler Abhängigkeiten zwischen den Ebenen minimal sein. Wenn Sie ein detailliertes Diagramm mit Klassen oder Methoden als Ebenen zeichnen, sollte das Ergebnis dieselben Merkmale aufweisen.

Wenn dies nicht der Fall ist, wird der Code so ändern Sie während seiner Lebensdauer schwieriger und für die Validierung mithilfe von Abhängigkeitsdiagrammen weniger geeignet sein.

## <a name="NewAreas"></a> Entwerfen Sie neue Bereiche der Anwendung

Wenn Sie mit der Entwicklung eines neuen Projekts oder eines neuen Bereichs in einem neuen Projekt beginnen, können Sie Ebenen und Abhängigkeiten zeichnen, um die Hauptkomponenten zu identifizieren, bevor Sie mit dem Entwickeln des Codes beginnen.

-   **Zeigen Sie identifizierbare architektonische Muster** in Ihre Abhängigkeitsdiagramme, falls möglich. Beispielsweise kann ein Abhängigkeitsdiagramm, das eine Desktopanwendung beschreibt Ebenen wie Präsentation, Domänenlogik und Data Store enthalten. Ein Abhängigkeitsdiagramm, das eine einzelne Funktion in einer Anwendung umfasst möglicherweise Ebenen, wie z. B. Modell, Ansicht und Controller. Weitere Informationen zu solchen Mustern finden Sie unter [Patterns & Practices: Application Architecture](http://go.microsoft.com/fwlink/?LinkId=145794).

-   **Erstellen Sie ein Codeartefakt für jede Ebene** wie z. B. einen Namespace, Klasse oder Komponente. Dies vereinfacht das Verfolgen des Codes und das Verknüpfen der Codeartefakte mit den Ebenen. Verknüpfen Sie jedes Artefakt mit der entsprechenden Ebene, sobald Sie das Artefakt erstellen.

-   **Sie müssen nicht die meisten Klassen und andere Artefakte mit Ebenen verknüpfen** , da sie zu größeren Artefakten z. B. Namespaces liegen, den Sie bereits mit Ebenen verknüpft haben.

-   **Erstellen Sie ein neues Diagramm für ein neues Feature**. In der Regel werden ein oder mehrere Abhängigkeitsdiagramme, die die gesamte Anwendung beschreibt. Wenn Sie eine neue Funktion in der Anwendung entwerfen, ändern Sie nicht die vorhandenen Diagramme, und fügen Sie ihnen keine Elemente hinzu. Erstellen Sie stattdessen ein eigenes Diagramm, das die neuen Teile des Codes wiedergibt. Das neue Diagramm kann beispielsweise Ebenen für die Präsentation, Domänenlogik und Datenbank der neuen Funktion enthalten.

     Wenn Sie die Anwendung erstellen, wird der Code sowohl anhand des allgemeinen Diagramms als auch anhand des ausführlicheren Funktionsdiagramms überprüft.

## <a name="EditLayout"></a> Das Layout für die Präsentation und Diskussion bearbeiten

Bearbeiten Sie Darstellung und Layout des Diagramms, um die Suche nach Ebenen und Abhängigkeiten sowie Diskussionen mit Teammitgliedern zu vereinfachen. Führen Sie hierzu die folgenden Schritte aus:

-   Ändern der Größe, Formen und Positionen von Ebenen

-   Ändern der Farben von Ebenen und Abhängigkeiten

    -   Wählen Sie eine oder mehrere Ebenen oder Abhängigkeiten, mit der rechten Maustaste und klicken Sie dann auf **Eigenschaften**. In der **Eigenschaften** Fenster Bearbeiten der **Farbe** Eigenschaft.

## <a name="Validate"></a> Überprüfen Sie den Code anhand des Diagramms

Wenn Sie das Diagramm bearbeitet haben, können Sie es mit dem Code jederzeit manuell oder automatisch jedes Mal überprüfen, die Sie erstellen.

Thema

-   [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md)

-   [Schließen Sie Ebenenvalidierung im Buildprozess](#BuildValidation)

## <a name="UpdateCode"></a> Aktualisieren Sie den Code, um ihn an die neue Architektur anzupassen

In der Regel treten Fehler beim ersten, Code für ein aktualisiertes Abhängigkeitsdiagramm zu überprüfen. Diese Fehler können mehrere Ursachen haben:

-   Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.

-   Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.

Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Dies ist normalerweise ein iterativer Vorgang. Weitere Informationen zu diesen Fehlern finden Sie unter [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Beim Entwickeln oder des Codes Umgestalten, Sie möglicherweise neue Artefakte mit dem Abhängigkeitsdiagramm zu verknüpfen. Dies ist jedoch möglicherweise nicht erforderlich, wenn Ebenen z. B. vorhandene Namespaces darstellen und diesen Namespaces mit dem neuen Code lediglich weitere Elemente hinzugefügt werden.

Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie Fehler unterdrücken, ist es sich bewährt, melden Sie sich eine Arbeitsaufgabe in Team Foundation. Um diese Aufgabe ausführen zu können, finden Sie unter [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a> Schließen Sie ebenenvalidierung im Buildprozess

Schließen Sie ebenenvalidierung zum standardmäßigen Buildprozess der Projektmappe, um sicherzustellen dass zukünftige Änderungen im Code den Abhängigkeitsdiagrammen entsprechen. Wenn andere Teammitglieder die Projektmappe zu erstellen, werden alle Unterschiede zwischen den Abhängigkeiten im Code und das Dependency-Diagramm als Buildfehler gemeldet. Weitere Informationen zum Einschließen von ebenenvalidierung im Buildprozess finden Sie unter [Überprüfen von Code mit Abhängigkeitsdiagrammen](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Siehe auch

- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)
- [Erstellen von Abhängigkeitsdiagrammen aus dem Code](../modeling/create-layer-diagrams-from-your-code.md)