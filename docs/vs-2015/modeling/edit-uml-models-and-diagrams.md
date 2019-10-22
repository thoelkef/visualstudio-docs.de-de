---
title: Bearbeiten von UML-Modellen und-Diagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6585fbfa7c16e710633e81841b4c8eb380f9f564
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669724"
---
# <a name="edit-uml-models-and-diagrams"></a>Bearbeiten von UML-Modellen und -Diagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können ein UML-Modell über die durch die verschiedenen Diagrammtypen bereitgestellten Ansichten erstellen und bearbeiten. Durch Bereitstellen von unterschiedlichen Perspektiven auf Ihrem System helfen Ihnen diese Diagramme dabei, verschiedene Aspekte des Degins und Anforderungen zu verstehen. Visual Studio stellt Vorlagen für fünf der am häufigsten verwendeten UML-Diagrammtypen bereit:

 Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Dieses Thema beschreibt Verfahren zum Bearbeiten des Modells, das bei den verschiedenen Diagrammtypen gleich ist. Weitere Informationen, die spezifisch für bestimmte Diagrammtypen sind, finden [Sie unter Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md).

## <a name="in-this-topic"></a>In diesem Thema

- [UML-Diagramme sind Ansichten eines UML-Modells.](#Views)

- [Erstellen von UML-Modellierungs Diagrammen](#Creating)

- [Zeichnen von UML-Modellierungs Diagrammen](#Drawing)

- [Bearbeiten von Formen und Connectors](#Editing)

- [Übernehmen von Änderungen am Modell](#Undo)

- [Freigeben von Elementen zwischen Diagrammen](#Sharing)

- [Kopieren von Elementen und Gruppen verwandter Elemente](#Copying)

- [Löschen eines Modell Elements oder seiner Sichten](#Deleting)

- [Suchen von Text in einem Diagramm](#Searching)

- [Vorbereiten eines Diagramms für die Präsentation](#presentation)

- [Erweitern von UML-Designern](#extensions)

## <a name="Views"></a>UML-Diagramme sind Ansichten eines UML-Modells.
 Sie können UML-Diagramme nur in Modellierungsprojekten erstellen und verwenden. Weitere Informationen zum Erstellen von Diagrammen und Projekten finden Sie unter [Erstellen von UML-Modellierungs Projekten und-Diagrammen](../modeling/create-uml-modeling-projects-and-diagrams.md).

- Ein Modellierungsprojekt enthält ein einzelnes UML-Modell. Jedes UML-Diagramm im Projekt ist eine Ansicht des UML-Modells.

- Das Modell wird im UML- **Modell-Explorer**angezeigt. Zeigen Sie im Menü **Architektur** auf **Fenster**, und klicken Sie dann auf UML- **Modell-Explorer**.

- Jede Form in einem Diagramm ist eine Ansicht eines Elements im Modell. Wenn Sie eine neue Form in einem Diagramm platzieren, erstellen Sie ein neues Element im Modell.

- Wenn Sie ein Diagramm speichern, speichert Visual Studio das gesamte Modell, alle zugehörigen Diagramme und die Modellierungsprojekt Datei.

## <a name="Creating"></a>Erstellen von UML-Modellierungs Diagrammen

1. Klicken Sie in Visual Studio im Menü **Architektur** auf **neues UML-oder ebenendiagramm**.

2. Wählen Sie Ihr Diagramm aus, und benennen Sie es.

3. Wählen Sie unter **zu Modellierungsprojekt hinzufügen**ein vorhandenes Modellierungsprojekt aus, oder wählen Sie **Neues Modellierungsprojekt erstellen**aus.

   > [!NOTE]
   > Im Modellierungsprojekt muss ein Modellierungsdiagramm vorhanden sein.

   Sie können auch im Projektmappen-Explorer einem vorhandenen Modellierungsprojekt ein Diagramm hinzufügen. Klicken Sie mit der rechten Maustaste auf das Modellierungsprojekt, zeigen Sie auf **Hinzufügen**, und klicken Sie auf **Neues Element**.

#### <a name="to-create-an-empty-uml-modeling-project"></a>Erstellen eines leeren UML-Modellierungsprojekts

- Zeigen Sie im Menü **Datei** auf **neu**, klicken Sie auf **Projekt**, und doppelklicken Sie im Dialogfeld **Neues Projekt** auf **Modellierungs Projekte**.

  Weitere Informationen zum Verwalten von Modellierungs Projekten finden Sie unter [Erstellen von UML-Modellierungs Projekten und-Diagrammen](../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="Drawing"></a>Zeichnen von UML-Modellierungs Diagrammen
 Ein Modellierungsdiagramm zeigt eine Auflistung von Modellelementen, die durch Beziehungen verknüpft sind. Jedes Element wird als Form, und jede Beziehung als Konnektor zwischen zwei Formen angezeigt.

 Es gibt zwei Arten von Tools, eines für Elemente und eines für Beziehungen. In der UML-Klassendiagramm-Toolbox ist **Class** beispielsweise ein Element Tool, und **Association** ist ein Beziehungs Tool.

> [!NOTE]
> Informationen zu bestimmten Diagrammtypen finden Sie unter [Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md).

#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Erstellen von Elementen und Beziehungen in einem UML-Modellierungsdiagramm

1. Um ein Modellelement zu erstellen, klicken Sie auf ein Element in der Toolbox, und klicken Sie dann auf das Diagramm, in dem es angezeigt werden soll. Nachdem Sie das Element erstellt haben, passen Sie die Größe und Form durch Ziehen der Ziehpunkte an.

    In einigen Fällen können Sie ein neues Element in einem anderen Element platzieren. Beispielsweise können Sie eine Klasse in einem Paket in einem UML-Klassendiagramm platzieren.

   > [!NOTE]
   > Wenn die Toolbox nicht angezeigt wird, klicken Sie im Menü **Ansicht** auf **Toolbox** .

2. Um eine Beziehung zu erstellen, klicken Sie auf ein Beziehungstool, klicken Sie auf das Element, in dem die Beziehung gestartet werden soll und klicken Sie dann auf das Element, in dem sie enden soll.

    Verschiedene Typen von Beziehungen können bei verschiedene Arten von Elementen beginnen oder enden. Beispielsweise kann eine Zuordnungsbeziehung in einem UML-Klassendiagramm nicht bei einem Kommentarelement beginnen oder enden.

   > [!NOTE]
   > Um das gleiche Tool mehrmals zu verwenden, doppelklicken Sie auf das Tool. Wenn Sie fertig sind, klicken Sie auf das **Zeiger** Tool.

   Bei einigen Arten von Diagrammen können Sie auch einfache Formen zeichnen. Diese Formen sind nicht Teil des Modells, Sie können sie jedoch verwenden, um Teile des Diagramms hervorzuheben oder in verschiedene Bereiche zu unterteilen.

## <a name="Editing"></a>Bearbeiten von Formen und Connectors
 Beim Ändern der Größe oder Farbe einer Form oder dem erneuten Erstellen eines Konnektors gibt es keine Auswirkungen auf das zugrunde liegende Modell. Wenn Sie eine Form im Diagramm oder im UML-Modell-Explorer umbenennen, wird das entsprechende Element im UML-Modell-Explorer und allen anderen Diagrammen, die dieses Element darstellen, umbenannt.

> [!NOTE]
> Es ist eine einfache Möglichkeit, neue Toolboxelemente zu erzeugen, aus denen Sie Gruppen von Elementen oder Elemente mit Eigenschaften Ihrer Wahl erstellen können. Weitere Informationen finden Sie unter [Definieren eines benutzerdefinierten Modellierungs Toolbox Elements](../modeling/define-a-custom-modeling-toolbox-item.md).

 Die folgende Abbildung zeigt, wie Sie die Größe einer Form oder ihren Namen ändern.

 ![Anpassen eines Modell Elements](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")

> [!TIP]
> Die integrierten Befehle enthalten keinen Befehl zum übersichtlichen Ausrichten von Formen. Sie können jedoch problemlos einen eigenen Ausrichtungs Befehl erstellen, indem Sie den Code im Beispiel in [Anzeigen eines UML-Modells in Diagrammen](../modeling/display-a-uml-model-on-diagrams.md)kopieren.

 Die folgende Abbildung zeigt, wie die Route und Position eines Konnektors oder seiner Bezeichnungen angepasst werden.

 ![Anpassen eines Connector](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")

#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>So verschieben Sie ein Ende der Verbindung zu einer anderen Form

1. Führen Sie einen der folgenden Schritte aus:

   - Drücken Sie **STRG** , und verschieben Sie das Ende.

     \- oder -

   - Klicken Sie mit der rechten Maustaste auf den Connector und dann auf **Verbindung wiederherstellen**.

2. Klicken Sie auf das Ende des Konnektors, das Sie verschieben möchten.

3. Klicken Sie auf die Form, zu der Sie den Konnektor verschieben möchten.

#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Ändern der Farbe oder anderer Eigenschaften eines Elements, einer Beziehung oder eines Diagramms

- Klicken Sie auf das Element, und legen Sie die Felder im Fenster **Eigenschaften** fest.

     Wenn das **Eigenschaften** Fenster nicht angezeigt wird, klicken Sie mit der rechten Maustaste auf das Element, und klicken Sie dann auf **Eigenschaften.**

#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Vergrößern und Verkleinern in einem Modellierungsdiagramm

- Halten Sie die **STRG** -Taste gedrückt, während Sie das Mausrad drehen.

     \- oder -

- Halten Sie **STRG + UMSCHALT**gedrückt, und klicken Sie dann auf die linke oder Rechte Maustaste.

     \- oder -

- Klicken Sie auf der Symbolleiste **Architektur-Designer** auf das Pluszeichen ( **+** ) oder Minuszeichen ( **-** ), oder wählen Sie eine Zoomstufe aus.

## <a name="Searching"></a>Suchen in einem Diagramm
 Die Schnellsuche-Funktion sucht nach Elementen in einem Diagramm. Sie müssen **Suchen in:** **Aktuelles Dokument**festlegen.

#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Suchen nach Text in einem Modellierungsdiagramm

1. Drücken Sie **STRG + F**.

     \- oder -

     Zeigen Sie im Menü **Bearbeiten** auf **Suchen und ersetzen**, und klicken Sie dann auf **Schnellsuche**.

    > [!NOTE]
    > Im Dialogfeld Suchen **und ersetzen** muss das Feld **Suchen in** auf **Aktuelles Dokument**festgelegt bleiben. Die anderen Optionen werden nicht unterstützt.

2. Geben Sie den Text ein, den Sie suchen möchten, und klicken Sie dann auf **weiter suchen**.

    > [!NOTE]
    > Wenn der gesuchte Text in einer reduzierten Form enthalten ist, wird die Form hervorgehoben. Erweitern Sie die Form, und klicken Sie dann erneut auf **weiter suchen** .

## <a name="Undo"></a>Übernehmen von Änderungen am Modell
 Mithilfe der Befehle **Rückgängig** und wieder **holen** im Menü **Bearbeiten** können Sie Änderungen rückgängig machen und wiederholen, die Sie am Modell und in den Diagrammen vorgenommen haben.

 **Jedes Modellierungsprojekt verfügt über einen einzigen Stapel von Änderungen.** Alle Änderungen, die Sie am Modell und den Diagrammen vornehmen, werden in diesem Stapel gespeichert. Der Stapel enthält außerdem Änderungen am Fokus zwischen Diagrammen. Durch den Befehl „Rückgängig“ werden die Änderungen in diesem Stapel rückgängig gemacht.

 Nehmen wir beispielsweise an, dass Sie diese Operationen ausführen: Ändern von Diagramm1; Ändern Sie den Fokus in Diagramm 2. Ändern Sie Diagram2. Wenn Sie Änderungen rückgängig machen, wird die letzte Änderung durch das erste Rückgängig machen rückgängig gemacht; duch das nächste Rückgängig machen wird der Fokus wieder auf Diagramm 1 gelegt; und durch das dritte Rückgängig machen wird die Änderung an Diagramm 1 rückgänig gemacht.

 **Durch das Schließen eines Diagramms wird der Stapel von Änderungen abgeschnitten.** Wenn Sie ein Diagramm schließen, können Sie die an dem Diagramm vorgenommene Änderungen nicht rückgängig machen, außerdem können Sie zuvor am Modell oder dazugehörigen Diagrammen vorgenommene Änderungen nicht rückgängig machen.

 **Sie können während der Bearbeitung einer Eigenschaft nicht rückgängig machen.** Während der Bearbeitung einer Eigenschaft im Eigenschaftenfenster oder in einer Bezeichnung in einem Diagramm können Sie nur Änderungen rückgängig machen, die Sie in dieser Eigenschaft vorgenommen haben. Schließen Sie Ihre Änderung in der Eigenschaft ab, indem Sie die EINGABETASTE drücken, oder brechen Sie den Vorgang ab, indem Sie ESC drücken. Anschließend können Sie Änderungen im Modell und den Diagrammen rückgängig machen.

 **Das Schließen eines Diagramms ohne Speichern weist möglicherweise nicht die erwarteten Auswirkungen auf.** Wenn Sie Änderungen vornehmen und dann ein Diagramm schließen, ohne es zu speichern, werden die Änderungen im Modell weiterhin beibehalten. Es wird empfohlen, das gesamte Modell zu schließen, wenn Sie dies machen möchten, ohne es zu speichern.

## <a name="Sharing"></a>Freigeben von Elementen zwischen Diagrammen
 Sie können eine spezielle Instanz eines Modellelements mehrmals in den Diagrammen angezeigen. Dies gilt für Klassen, Schnittstellen, Komponenten, Anwendungsfälle und Akteure.

 Dies ist hilfreich, wenn Sie unterschiedliche Gruppen von Beziehungen in unterschiedlichen Diagrammen anzeigen möchten. In einem Diagramm können Sie z. B. die Zuordnungen zwischen Customer- und Address-Klassen anzeigen. In einem anderen Diagramm können Sie die Address-Klasse mit der Zuordnung zum Postal-Bereich erneut anzeigen.

 Sie können die Eigenschaften eines Modellelements, wie z. B. den Namen ändern, indem Sie seine Ansichten in einem beliebigen Diagramm auswählen oder indem Sie sie im UML-Modell-Explorer auswählen.

 Jede Art von Diagramm kann nur einige Arten von Modellelementen anzeigen. Sie können beispielsweise keinen Anwendungsfall in einem Komponentendiagramm anzeigen. Daher funktionieren die folgenden Verfahren nur für einige Kombinationen von Modellelement und Diagramm.

#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>So fügen Sie eine neue Ansicht eines Modellelements mithilfe des UML-Modell-Explorers hinzu

1. Um den **UML-Modell-Explorer**zu öffnen, zeigen Sie im Menü **Architektur** auf **Fenster**, und klicken Sie dann auf UML- **Modell-Explorer**.

2. Ziehen Sie das Modellelement aus dem **UML-Modell-Explorer** in ein kompatibles Diagramm im selben Projekt.

     Es wird eine Form angezeigt, die eine Ansicht des Modellelements bereitstellt, die zusätzlich zu Ansichten in anderen Diagrammen oder dem gleichen Diagramm angezeigt werden können.

    > [!NOTE]
    > Der Effekt unterscheidet sich, wenn Sie eine Klasse oder eine Komponente in ein Sequenzdiagramm ziehen. In diesem Fall wird eine neue Lebenslinie erstellt, deren Typ diese Klasse oder eine Komponente ist. Weitere Informationen finden Sie unter [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).

#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>So fügen Sie eine neue Ansicht eines Modellelements mithilfe der Funktion „Verweis einfügen“

1. Klicken Sie mit der rechten Maustaste auf ein vorhandenes Element, und klicken Sie auf **Kopieren**.

    - Sie können mehrere Elemente gleichzeitig kopieren. Halten Sie die STRG-Taste gedrückt, während Sie auf die einzelnen Elemente klicken, klicken Sie mit der rechten Maustaste darauf, und klicken Sie dann auf **Kopieren**.

2. Klicken Sie mit der rechten Maustaste auf einen leeren Teil eines kompatiblen Diagramms, und klicken Sie dann auf **Verweis einfügen**.

     Es wird eine andere Ansicht des gleichen Elements angezeigt.

    > [!NOTE]
    > Dies unterscheidet sich vom **Einfüge** Befehl, der ein neues Element im Modell erstellt. Weitere Informationen finden Sie unter [Kopieren von Elementen und Gruppen verwandter Elemente](#Copying).

> [!NOTE]
> Wenn Sie Diagrammansichten von zwei Modellelementen hinzufügen, die bereits durch eine Beziehung verbunden sind, wird eine Ansicht der Beziehung auch im Diagramm angezeigt. Sie können diese Ansicht nur eines der Elemente aus dem Diagramm entfernen oder Löschen der Beziehung aus dem Modell löschen.

## <a name="Copying"></a>Kopieren von Elementen und Gruppen verwandter Elemente
 Sie können Modellelemente und Elementgruppen zusammen mit den Beziehungen zwischen ihnen kopieren und einfügen.

> [!NOTE]
> Die Befehle zum **Einfügen** und **Einfügen von verweisen** haben unterschiedliche Auswirkungen. Beim **Einfügen** werden neue Elemente erstellt, deren Eigenschaften denen der kopierten Elemente ähneln. Durch **Einfügen eines Verweises** werden neue Sichten derselben Elemente erstellt.

#### <a name="to-copy-elements-and-their-relationships"></a>Kopieren von Elementen und Beziehungen

1. Wählen Sie ein oder mehrere Elemente im Diagramm mit den Elementen, die Sie kopieren möchten.

    > [!NOTE]
    > Sie können Beziehungen nur als Teil einer Gruppe von Elementen kopieren.

2. Klicken Sie im Menü **Bearbeiten** auf **Kopieren**.

3. Wenn Sie die Elemente in ein anderes Diagramm kopieren möchten, erstellen Sie das neue Diagramm, oder öffnen Sie das vorhandene Diagramm.

4. Klicken Sie im Menü **Bearbeiten** auf **Einfügen**.

    - Kopien der Elemente werden zusammen mit Kopien von Beziehungen zueinander angezeigt.

    - Bei jedem neuen Element wird automatisch ein neuer Name generiert.

5. Passen Sie die Positionen, Namen und andere Eigenschaften der neuen Elemente und Beziehungen an.

> [!NOTE]
> Sie können kein Modellelement aus einem Modell in ein anderes Modell kopieren, z. B. wenn Sie zwei Modelle in der gleichen Projektmappe haben. Sie können jedoch Elemente aus einem Diagramm in ein anderes kopieren.

#### <a name="to-copy-an-entire-diagram"></a>Kopieren eines gesamten Diagramms

1. Erstellen Sie ein neues Diagramm.

2. Wählen Sie alle Elemente in einem vorhandenen Diagramm, kopieren Sie sie, und fügen Sie sie in die neue Zeile ein.

   Sie können ein Diagramm nicht durch Kopieren und Einfügen im Projektmappen-Explorer replizieren.

## <a name="Deleting"></a>Löschen eines Modell Elements oder seiner Sichten
 Einige Elementarten, insbesondere Klassifizierer, können aus einem Diagramm gelöscht werden, ohne sie aus dem Modell zu löschen. Klassifizierer sind die Hauptelemente, die in Klassendiagrammen, Komponentendiagrammen und Anwendungsfalldiagrammen angezeigt werden. Sie können in mehr als einem Diagramm angezeigt werden. Für diese Elementtypen gibt es zwei separate Befehle: aus dem **Diagramm entfernen** und **aus Modell löschen**.

 Im Gegensatz dazu wird beim Löschen einer Beziehung aus einem Diagramm die Beziehung immer auch aus dem Modell gelöscht.

> [!NOTE]
> Bestimmte Arten von Elementen in einem UML-Diagramm besitzen Bezeichnungen. Wenn Sie solche Elemente auswählen, indem Sie ein Rechteck darum zeichnen, können Bezeichnungen ausgewählt werden, jedoch nicht die dazugehörigen Elemente. Das Löschen einer Teilmenge von Elementen, die auf diese Weise ausgewählt werden, wird nicht unterstützt. Wenn Sie eine Teilmenge dieser Elemente auswählen möchten, halten Sie die **STRG** -Taste gedrückt, während Sie auf die einzelnen Elemente klicken.

#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>So entfernen Sie eine Klassifizierungsansicht aus einem Diagramm

- Klicken Sie mit der rechten Maustaste auf das Element im Diagramm, und klicken Sie dann auf **aus Diagramm entfernen**.

  \- oder -

- Klicken Sie auf das Element im Diagramm, und drücken Sie dann die ENTF **-Taste.**

  - Diese Ansicht des Elements wird ausgeblendet. Das-Element verbleibt jedoch im Modell, und Sie können es weiterhin im **UML-Modell-Explorer**finden. Andere Ansichten des gleichen Elements werden ebenfalls beibehalten.

  - Jeder Konnektor, der an dieser Form endet, wird aus dem Diagramm entfernt, die Beziehung bleibt jedoch im Modell. Die Beziehung können Sie im **UML-Modell-Explorer** unter **Beziehungen**unter jedem Element sehen, das eine Verbindung herstellt.

#### <a name="to-delete-an-element-from-the-model"></a>Löschen eines Elements aus dem Modell

- Klicken Sie im UML-Modell- **Explorer** oder in einem Diagramm mit der rechten Maustaste auf das Element, und klicken Sie dann auf **aus Modell löschen**.

  - Das Element wird aus jedem Diagramm gelöscht, in dem es angezeigt wird.

  - Jede Beziehung, die an diesem Element endet, wird ebenfalls aus dem Modell gelöscht.

#### <a name="to-delete-a-relationship-from-the-model"></a>So löschen Sie eine Beziehung aus dem Modell

- Klicken Sie mit der rechten Maustaste auf die Beziehung in einem Diagramm oder im **UML-Modell-Explorer**, und klicken Sie dann auf **aus Modell löschen**.

    > [!CAUTION]
    > Sie können keine Beziehung aus einem Diagramm entfernen, ohne sie aus dem Modell entfernen.

     Die Beziehung wird aus dem Modell gelöscht und aus jedem Diagramm, in dem sie angezeigt wird.

## <a name="presentation"></a>Vorbereiten eines Diagramms für die Präsentation
 Mithilfe der folgenden Funktionen können Sie bestimmte Teile des Diagramms hervorheben, Erläuterungen hinzufügen oder ein Diagramm in unterschiedliche relevante Bereiche unterteilen.

- Sie können einen beliebigen Teil eines Diagramms in ein Word-, PowerPoint- oder anderes Dokument kopieren. Wählen Sie die gewünschten Formen und Connectors aus, klicken Sie mit der rechten Maustaste, und klicken Sie dann auf **Kopieren**.

- Die Farbe der Formen und Konnectoren kann geändert werden. Wählen Sie mindestens eine Form aus, und ändern Sie die **Color** -Eigenschaft. Wenn Sie das Fenster **Eigenschaften** nicht sehen, drücken Sie **F4**.

- In Diagrammen einiger Arten können Sie Linien, Rechtecke und Ellipsen aus dem Abschnitt **einfache Formen** der Toolbox zeichnen. Diese Formen bilden keinen Teil des UML-Modells.

- Wenn Sie einen Bereich bezeichnen möchten, können Sie einen Kommentar aus der Toolbox ziehen und seine **transparente** Eigenschaft auf **true**festlegen. Genau wie einfache Formen sind Kommentare kein Bestandteil des UML-Modells und werden nicht im UML-Modell-Explorer angezeigt.

- Um Hinweise und Erläuterungen zu Modellelementen hinzuzufügen, können Sie Kommentare erstellen und diese dann mit den Elementen verknüpfen.

- Um eine Spalte oder Zeilenformen im Diagramm sauber auszurichten, können Sie den Befehl „Formen ausrichten“ installieren. Dies ist als Beispiel für eine UML-Erweiterung verfügbar: [UML: Command zum Ausrichten von Formen](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7) .

### <a name="to-export-a-diagram-as-an-image"></a>Exportieren eines Diagramms als Bild
 Weitere Informationen finden Sie unter [Exportieren von Diagrammen als Bilder](../modeling/export-diagrams-as-images.md).

## <a name="extensions"></a>Erweitern von UML-Designern
 Sie können neue Funktionalität zu den UML-Tools hinzufügen und die Diagramm-Notation an Ihre eigenen Anforderungen anpassen. Weitere Informationen finden Sie unter [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md).

 Es sind mehrere Beispielerweiterungen verfügbar. Sie können sie entweder einfach installieren und verwenden oder Sie können ihren Quellcode als Grundlage für eigene Erweiterungen verwenden. Die Beispiele enthalten:

|||
|-|-|
|[Formen ausrichten](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)|Menübefehl, der Ihnen hilft, ein Diagramm zu bereinigen.|
|[Link zu docs](http://code.msdn.microsoft.com/Link-UML-elements-to-0adbf5a8)|Verknüpfen Sie ein UML-Element mit Word-Überschriften, PowerPoint-Folien, Dateien eines beliebigen Typs, UML-Diagrammen oder anderen UML-Elementen. Die Verknüpfung kann einfach durch Ziehen erstellt werden. Später können Sie auf das Element doppelklicken, um das verknüpfte Element anzuzeigen. Beispielsweise können Sie die Anwendungsfälle zu Word-Spezifikationen oder ausführlichen Aktivitätsdiagrammen und Aktionen mit Storyboard-Folien verknüpfen.|
|[Schneller Einstieg](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)|Erstellen Sie mithilfe von Texteingabe schnell ein Modell. Nützlich zum Erfassen von Ideen in Besprechungen.|
|[Farbe nach Stereotype](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Farben-Klassen nach Stereotyp. Sie können den Code für Ihre eigenen Stereotype leicht erweitern.|
|[Domänen Modellierung](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4)|Praktische Standardwerte für Geschäftsmodelle. Zuordnungen werden standardmäßig ohne Pfeile angezeigt, und Vorgänge werden nicht in Klassen angezeigt.|

## <a name="see-also"></a>Siehe auch
 [Erstellen von UML-Modellierungs Projekten und-Diagrammen](../modeling/create-uml-modeling-projects-and-diagrams.md) [analysieren und modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md) [Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md)
