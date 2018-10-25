---
title: Bearbeiten von UML-Modellen und-Diagrammen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: fafbccdae03c604e4d9b150b5745a75792833681
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834577"
---
# <a name="edit-uml-models-and-diagrams"></a>Bearbeiten von UML-Modellen und -Diagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können ein UML-Modell über die durch die verschiedenen Diagrammtypen bereitgestellten Ansichten erstellen und bearbeiten. Durch Bereitstellen von unterschiedlichen Perspektiven auf Ihrem System helfen Ihnen diese Diagramme dabei, verschiedene Aspekte des Degins und Anforderungen zu verstehen. Visual Studio stellt Vorlagen für fünf der am häufigsten verwendeten UML-Diagrammtypen bereit:  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Dieses Thema beschreibt Verfahren zum Bearbeiten des Modells, das bei den verschiedenen Diagrammtypen gleich ist. Weitere Informationen, die spezifisch für bestimmte Arten von Diagrammen finden Sie unter [Erstellen von Modellen für Ihre app](../modeling/create-models-for-your-app.md).  
  
## <a name="in-this-topic"></a>In diesem Thema  
  
-   [UML-Diagramme sind Ansichten eines UML-Modells](#Views)  
  
-   [Erstellen von UML-Modellierungsdiagrammen](#Creating)  
  
-   [Zeichnen von UML-Modellierungsdiagrammen](#Drawing)  
  
-   [Bearbeiten von Formen und Konnektoren](#Editing)  
  
-   [Rückgängigmachen von Änderungen das Modell](#Undo)  
  
-   [Freigeben von Elementen zwischen Diagrammen](#Sharing)  
  
-   [Kopieren von Elementen und Gruppen von verwandten Elementen](#Copying)  
  
-   [Löschen eines Modellelements oder seiner Ansichten](#Deleting)  
  
-   [Suchen von Text in einem Diagramm](#Searching)  
  
-   [Vorbereiten eines Diagramms für die Präsentation](#presentation)  
  
-   [Erweitern Sie die UML-Designern](#extensions)  
  
##  <a name="Views"></a> UML-Diagramme sind Ansichten eines UML-Modells  
 Sie können UML-Diagramme nur in Modellierungsprojekten erstellen und verwenden. Weitere Informationen zum Erstellen von Diagrammen und Projekten finden Sie unter [Erstellen von UML-Modellierungsprojekten und-Diagrammen](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
-   Ein Modellierungsprojekt enthält ein einzelnes UML-Modell. Jedes UML-Diagramm im Projekt ist eine Ansicht des UML-Modells.  
  
-   Sehen Sie das Modell im **UML-Modell-Explorer**. Auf der **Architektur** Startmenü **Windows**, und klicken Sie dann auf **UML-Modell-Explorer**.  
  
-   Jede Form in einem Diagramm ist eine Ansicht eines Elements im Modell. Wenn Sie eine neue Form in einem Diagramm platzieren, erstellen Sie ein neues Element im Modell.  
  
-   Wenn Sie ein Diagramm speichern, Visual Studio das gesamte Modell speichert, Projektdatei alle zugehörigen Diagramme sowie die Modellierungsprojektdatei.  
  
##  <a name="Creating"></a> Erstellen von UML-Modellierungsdiagrammen  
  
1. Auf der **Architektur** in Visual Studio, klicken Sie anschließend auf **neues UML- oder Ebenendiagramm**.  
  
2. Wählen Sie Ihr Diagramm aus, und benennen Sie es.  
  
3. In **fügen Sie dem Modellierungsprojekt**wählen Sie ein vorhandenes Modellierungsprojekt, oder **ein neues Modellierungsprojekt erstellen**.  
  
   > [!NOTE]
   >  Im Modellierungsprojekt muss ein Modellierungsdiagramm vorhanden sein.  
  
   Sie können auch im Projektmappen-Explorer einem vorhandenen Modellierungsprojekt ein Diagramm hinzufügen. Mit der rechten Maustaste in des Modellierungsprojekts, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Element**.  
  
#### <a name="to-create-an-empty-uml-modeling-project"></a>Erstellen eines leeren UML-Modellierungsprojekts  
  
- Auf der **Datei** , zeigen Sie auf **neu**, klicken Sie auf **Projekt**, und klicken Sie in der **neues Projekt** Dialogfeld Doppelklicken Sie auf **Modellierung Projekte**.  
  
  Weitere Informationen zum Verwalten von Modellierungsprojekten finden Sie unter [Erstellen von UML-Modellierungsprojekten und-Diagrammen](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
##  <a name="Drawing"></a> Zeichnen von UML-Modellierungsdiagrammen  
 Ein Modellierungsdiagramm zeigt eine Auflistung von Modellelementen, die durch Beziehungen verknüpft sind. Jedes Element wird als Form, und jede Beziehung als Konnektor zwischen zwei Formen angezeigt.  
  
 Es gibt zwei Arten von Tools, eines für Elemente und eines für Beziehungen. Z. B. in der UML-Klassendiagramm-Toolbox **Klasse** ist ein Elementtool, das und **Zuordnung** ein Beziehungstool.  
  
> [!NOTE]
>  Wenn Sie Informationen, die spezifisch für bestimmte Diagrammtypen sind wünschen, finden Sie unter [Erstellen von Modellen für Ihre app](../modeling/create-models-for-your-app.md).  
  
#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Erstellen von Elementen und Beziehungen in einem UML-Modellierungsdiagramm  
  
1. Um ein Modellelement zu erstellen, klicken Sie auf ein Element in der Toolbox, und klicken Sie dann auf das Diagramm, in dem es angezeigt werden soll. Nachdem Sie das Element erstellt haben, passen Sie die Größe und Form durch Ziehen der Ziehpunkte an.  
  
    In einigen Fällen können Sie ein neues Element in einem anderen Element platzieren. Beispielsweise können Sie eine Klasse in einem Paket in einem UML-Klassendiagramm platzieren.  
  
   > [!NOTE]
   >  Wenn die Toolbox nicht angezeigt wird, klicken Sie auf **Toolbox** auf die **Ansicht** Menü.  
  
2. Um eine Beziehung zu erstellen, klicken Sie auf ein Beziehungstool, klicken Sie auf das Element, in dem die Beziehung gestartet werden soll und klicken Sie dann auf das Element, in dem sie enden soll.  
  
    Verschiedene Typen von Beziehungen können bei verschiedene Arten von Elementen beginnen oder enden. Beispielsweise kann eine Zuordnungsbeziehung in einem UML-Klassendiagramm nicht bei einem Kommentarelement beginnen oder enden.  
  
   > [!NOTE]
   >  Um das gleiche Tool mehrmals zu verwenden, doppelklicken Sie auf das Tool. Wenn Sie fertig sind, klicken Sie auf die **Zeiger** Tool.  
  
   Bei einigen Arten von Diagrammen können Sie auch einfache Formen zeichnen. Diese Formen sind nicht Teil des Modells, Sie können sie jedoch verwenden, um Teile des Diagramms hervorzuheben oder in verschiedene Bereiche zu unterteilen.  
  
##  <a name="Editing"></a> Bearbeiten von Formen und Konnektoren  
 Beim Ändern der Größe oder Farbe einer Form oder dem erneuten Erstellen eines Konnektors gibt es keine Auswirkungen auf das zugrunde liegende Modell. Wenn Sie eine Form im Diagramm oder im UML-Modell-Explorer umbenennen, wird das entsprechende Element im UML-Modell-Explorer und allen anderen Diagrammen, die dieses Element darstellen, umbenannt.  
  
> [!NOTE]
>  Es ist eine einfache Möglichkeit, neue Toolboxelemente zu erzeugen, aus denen Sie Gruppen von Elementen oder Elemente mit Eigenschaften Ihrer Wahl erstellen können. Weitere Informationen finden Sie unter [Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
 Die folgende Abbildung zeigt, wie Sie die Größe einer Form oder ihren Namen ändern.  
  
 ![Modellelement anpassen](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")  
  
> [!TIP]
>  Die integrierten Befehle enthalten keinen Befehl zum übersichtlichen Ausrichten von Formen. Sie können einfach eigene Ausrichtungsbefehle erstellen, kopieren Sie den Code im Beispiel in [anzeigen ein UML-Modells in Diagrammen](../modeling/display-a-uml-model-on-diagrams.md).  
  
 Die folgende Abbildung zeigt, wie die Route und Position eines Konnektors oder seiner Bezeichnungen angepasst werden.  
  
 ![Connector anpassen](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")  
  
#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>So verschieben Sie ein Ende der Verbindung zu einer anderen Form  
  
1. Führen Sie einen der folgenden Schritte aus:  
  
   - Drücken Sie **STRG** und verschieben Sie das Ende.  
  
     \- oder –  
  
   - Mit der rechten Maustaste in des Connectors, und klicken Sie dann auf **Reconnect**.  
  
2. Klicken Sie auf das Ende des Konnektors, das Sie verschieben möchten.  
  
3. Klicken Sie auf die Form, zu der Sie den Konnektor verschieben möchten.  
  
#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Ändern der Farbe oder anderer Eigenschaften eines Elements, einer Beziehung oder eines Diagramms  
  
-   Klicken Sie auf das Element aus, und legen Sie die Felder der **Eigenschaften** Fenster.  
  
     Wenn Sie nicht angezeigt, die **Eigenschaften** rechten Maustaste auf das Element, und klicken Sie dann auf **Eigenschaften.**  
  
#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Vergrößern und Verkleinern in einem Modellierungsdiagramm  
  
-   Halten Sie die **STRG** gedrückt, während Sie das Mausrad drehen.  
  
     \- oder –  
  
-   Halten Sie **STRG + UMSCHALT**, und klicken Sie dann auf die linke oder rechte Maustaste gedrückt.  
  
     \- oder –  
  
-   Auf der **Architektur-Designer** -Symbolleiste klicken Sie auf das Pluszeichen (**+**) oder Minuszeichen (-) (**-**), oder wählen Sie eine Zoomstufe.  
  
##  <a name="Searching"></a> Suchen in einem Diagramm  
 Die Schnellsuche-Funktion sucht nach Elementen in einem Diagramm. Sie müssen festlegen, **Suchen in:** zu **Aktuelles Dokument**.  
  
#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Suchen nach Text in einem Modellierungsdiagramm  
  
1.  Drücken Sie **STRG + F**.  
  
     \- oder –  
  
     Auf der **bearbeiten** Startmenü **suchen und Ersetzen**, und klicken Sie dann auf **Schnellsuche**.  
  
    > [!NOTE]
    >  In der **suchen und Ersetzen** (Dialogfeld), müssen Sie lassen die **Suchen in** Feld festgelegt, um **Aktuelles Dokument**. Die anderen Optionen werden nicht unterstützt.  
  
2.  Geben Sie den Text, den Sie verwenden möchten, suchen, und klicken Sie dann auf **Weitersuchen**.  
  
    > [!NOTE]
    >  Wenn der gesuchte Text in einer reduzierten Form enthalten ist, wird die Form hervorgehoben. Erweitern Sie die Form, und klicken Sie dann auf **Weitersuchen** erneut aus.  
  
##  <a name="Undo"></a> Rückgängigmachen von Änderungen das Modell  
 Rückgängigmachen und wiederholen Sie die Änderungen, die Sie an Modellen und Diagrammen mit vorgenommen haben die **rückgängig machen** und **wiederholen** von Befehlen auf die **bearbeiten** Menü.  
  
 **Jedes Modellierungsprojekt verfügt über einen einzigen Stapel von Änderungen.** Alle Änderungen, die Sie am Modell und den Diagrammen vornehmen, werden in diesem Stapel gespeichert. Der Stapel enthält außerdem Änderungen am Fokus zwischen Diagrammen. Durch den Befehl „Rückgängig“ werden die Änderungen in diesem Stapel rückgängig gemacht.  
  
 Nehmen wir beispielsweise an, dass Sie diese Operationen ausführen: Ändern von Diagramm1; Ändern Sie den Fokus in Diagramm 2. Ändern Sie Diagram2. Wenn Sie Änderungen rückgängig machen, wird die letzte Änderung durch das erste Rückgängig machen rückgängig gemacht; duch das nächste Rückgängig machen wird der Fokus wieder auf Diagramm 1 gelegt; und durch das dritte Rückgängig machen wird die Änderung an Diagramm 1 rückgänig gemacht.  
  
 **Schließen eines Diagramms wird der Änderungsstapel Änderungen.** Wenn Sie ein Diagramm schließen, können Sie die an dem Diagramm vorgenommene Änderungen nicht rückgängig machen, außerdem können Sie zuvor am Modell oder dazugehörigen Diagrammen vorgenommene Änderungen nicht rückgängig machen.  
  
 **Sie können nicht rückgängig gemacht, während der Bearbeitung einer Eigenschaft.** Während der Bearbeitung einer Eigenschaft im Eigenschaftenfenster oder in einer Bezeichnung in einem Diagramm können Sie nur Änderungen rückgängig machen, die Sie in dieser Eigenschaft vorgenommen haben. Schließen Sie Ihre Änderung in der Eigenschaft ab, indem Sie die EINGABETASTE drücken, oder brechen Sie den Vorgang ab, indem Sie ESC drücken. Anschließend können Sie Änderungen im Modell und den Diagrammen rückgängig machen.  
  
 **Schließen eines Diagramms ohne Speichern möglicherweise nicht die Auswirkungen, die Sie erwarten.** Wenn Sie Änderungen vornehmen und dann ein Diagramm schließen, ohne es zu speichern, werden die Änderungen im Modell weiterhin beibehalten. Es wird empfohlen, das gesamte Modell zu schließen, wenn Sie dies machen möchten, ohne es zu speichern.  
  
##  <a name="Sharing"></a> Freigeben von Elementen zwischen Diagrammen  
 Sie können eine spezielle Instanz eines Modellelements mehrmals in den Diagrammen angezeigen. Dies gilt für Klassen, Schnittstellen, Komponenten, Anwendungsfälle und Akteure.  
  
 Dies ist hilfreich, wenn Sie unterschiedliche Gruppen von Beziehungen in unterschiedlichen Diagrammen anzeigen möchten. In einem Diagramm können Sie z. B. die Zuordnungen zwischen Customer- und Address-Klassen anzeigen. In einem anderen Diagramm können Sie die Address-Klasse mit der Zuordnung zum Postal-Bereich erneut anzeigen.  
  
 Sie können die Eigenschaften eines Modellelements, wie z. B. den Namen ändern, indem Sie seine Ansichten in einem beliebigen Diagramm auswählen oder indem Sie sie im UML-Modell-Explorer auswählen.  
  
 Jede Art von Diagramm kann nur einige Arten von Modellelementen anzeigen. Sie können beispielsweise keinen Anwendungsfall in einem Komponentendiagramm anzeigen. Daher funktionieren die folgenden Verfahren nur für einige Kombinationen von Modellelement und Diagramm.  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>So fügen Sie eine neue Ansicht eines Modellelements mithilfe des UML-Modell-Explorers hinzu  
  
1.  Zum Öffnen **UML-Modell-Explorer**auf die **Architektur** , zeigen Sie auf **Windows**, und klicken Sie dann auf **UML-Modell-Explorer**.  
  
2.  Ziehen Sie das Modellelement aus **UML-Modell-Explorer** in ein kompatibles Diagramm im gleichen Projekt.  
  
     Es wird eine Form angezeigt, die eine Ansicht des Modellelements bereitstellt, die zusätzlich zu Ansichten in anderen Diagrammen oder dem gleichen Diagramm angezeigt werden können.  
  
    > [!NOTE]
    >  Der Effekt unterscheidet sich, wenn Sie eine Klasse oder eine Komponente in ein Sequenzdiagramm ziehen. In diesem Fall wird eine neue Lebenslinie erstellt, deren Typ diese Klasse oder eine Komponente ist. Weitere Informationen finden Sie unter [UML-Sequenzdiagramme: Richtlinien](../modeling/uml-sequence-diagrams-guidelines.md).  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>So fügen Sie eine neue Ansicht eines Modellelements mithilfe der Funktion „Verweis einfügen“  
  
1.  Mit der rechten Maustaste in eines vorhandenen Elements aus, und klicken Sie dann auf **Kopie**.  
  
    -   Sie können mehrere Elemente gleichzeitig kopieren. Die STRG-Taste gedrückt, während Sie klicken Sie auf jedes Element, mit der rechten eine davon Maustaste, und klicken Sie dann auf **Kopie**.  
  
2.  Mit der rechten Maustaste in eines leeren Bereich eines kompatiblen Diagramms, und klicken Sie dann auf **Verweis einfügen**.  
  
     Es wird eine andere Ansicht des gleichen Elements angezeigt.  
  
    > [!NOTE]
    >  Dies unterscheidet sich von der **einfügen** Befehl, der ein neues Element im Modell erstellt. Weitere Informationen finden Sie unter [Kopieren von Elementen und Gruppen von verwandten Elementen](#Copying).  
  
> [!NOTE]
>  Wenn Sie Diagrammansichten von zwei Modellelementen hinzufügen, die bereits durch eine Beziehung verbunden sind, wird eine Ansicht der Beziehung auch im Diagramm angezeigt. Sie können diese Ansicht nur eines der Elemente aus dem Diagramm entfernen oder Löschen der Beziehung aus dem Modell löschen.  
  
##  <a name="Copying"></a> Kopieren von Elementen und Gruppen von verwandten Elementen  
 Sie können Modellelemente und Elementgruppen zusammen mit den Beziehungen zwischen ihnen kopieren und einfügen.  
  
> [!NOTE]
>  Die **einfügen** und **Verweis einfügen** Befehle haben unterschiedliche Auswirkungen. **Fügen Sie** erstellt neue Elemente, deren Eigenschaften vergleichbar mit denen der kopierten Elemente sind. **Verweis einfügen** werden neue Ansichten der gleichen Elemente erstellt.  
  
#### <a name="to-copy-elements-and-their-relationships"></a>Kopieren von Elementen und Beziehungen  
  
1.  Wählen Sie ein oder mehrere Elemente im Diagramm mit den Elementen, die Sie kopieren möchten.  
  
    > [!NOTE]
    >  Sie können Beziehungen nur als Teil einer Gruppe von Elementen kopieren.  
  
2.  Auf der **bearbeiten** Menü klicken Sie auf **Kopie**.  
  
3.  Wenn Sie die Elemente in ein anderes Diagramm kopieren möchten, erstellen Sie das neue Diagramm, oder öffnen Sie das vorhandene Diagramm.  
  
4.  Auf der **bearbeiten** Menü klicken Sie auf **einfügen**.  
  
    -   Kopien der Elemente werden zusammen mit Kopien von Beziehungen zueinander angezeigt.  
  
    -   Bei jedem neuen Element wird automatisch ein neuer Name generiert.  
  
5.  Passen Sie die Positionen, Namen und andere Eigenschaften der neuen Elemente und Beziehungen an.  
  
> [!NOTE]
>  Sie können kein Modellelement aus einem Modell in ein anderes Modell kopieren, z. B. wenn Sie zwei Modelle in der gleichen Projektmappe haben. Sie können jedoch Elemente aus einem Diagramm in ein anderes kopieren.  
  
#### <a name="to-copy-an-entire-diagram"></a>Kopieren eines gesamten Diagramms  
  
1. Erstellen Sie ein neues Diagramm.  
  
2. Wählen Sie alle Elemente in einem vorhandenen Diagramm, kopieren Sie sie, und fügen Sie sie in die neue Zeile ein.  
  
   Sie können ein Diagramm nicht durch Kopieren und Einfügen im Projektmappen-Explorer replizieren.  
  
##  <a name="Deleting"></a> Löschen eines Modellelements oder seiner Ansichten  
 Einige Elementarten, insbesondere Klassifizierer, können aus einem Diagramm gelöscht werden, ohne sie aus dem Modell zu löschen. Klassifizierer sind die Hauptelemente, die in Klassendiagrammen, Komponentendiagrammen und Anwendungsfalldiagrammen angezeigt werden. Sie können in mehr als einem Diagramm angezeigt werden. Für diese Typen von Elementen, es gibt zwei separate Befehlen: **aus Diagramm entfernen** und **aus Modell löschen**.  
  
 Im Gegensatz dazu wird beim Löschen einer Beziehung aus einem Diagramm die Beziehung immer auch aus dem Modell gelöscht.  
  
> [!NOTE]
>  Bestimmte Arten von Elementen in einem UML-Diagramm besitzen Bezeichnungen. Wenn Sie solche Elemente auswählen, indem Sie ein Rechteck darum zeichnen, können Bezeichnungen ausgewählt werden, jedoch nicht die dazugehörigen Elemente. Das Löschen einer Teilmenge von Elementen, die auf diese Weise ausgewählt werden, wird nicht unterstützt. Um eine Teilmenge dieser Elemente auszuwählen, halten Sie die **STRG** gedrückt, während Sie jedes Element klicken.  
  
#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>So entfernen Sie eine Klassifizierungsansicht aus einem Diagramm  
  
- Mit der rechten Maustaste in des Elements im Diagramm, und klicken Sie dann auf **aus Diagramm entfernen**.  
  
  \- oder –  
  
- Klicken Sie auf das Element im Diagramm, und drücken Sie dann die **löschen** Schlüssel.  
  
  -   Diese Ansicht des Elements wird ausgeblendet. Allerdings das Element bleibt im Modell, und Sie finden es weiterhin im **UML-Modell-Explorer**. Andere Ansichten des gleichen Elements werden ebenfalls beibehalten.  
  
  -   Jeder Konnektor, der an dieser Form endet, wird aus dem Diagramm entfernt, die Beziehung bleibt jedoch im Modell. Sehen Sie die Beziehung im **UML-Modell-Explorer** unter **Beziehungen**, in dem jedes Element, das eine Verbindung hergestellt.  
  
#### <a name="to-delete-an-element-from-the-model"></a>Löschen eines Elements aus dem Modell  
  
-   Mit der rechten Maustaste entweder auf des Elements im **UML-Modell-Explorer** oder auf ein Diagramm, und klicken Sie dann auf **aus Modell löschen**.  
  
    -   Das Element wird aus jedem Diagramm gelöscht, in dem es angezeigt wird.  
  
    -   Jede Beziehung, die an diesem Element endet, wird ebenfalls aus dem Modell gelöscht.  
  
#### <a name="to-delete-a-relationship-from-the-model"></a>So löschen Sie eine Beziehung aus dem Modell  
  
-   Mit der rechten Maustaste in der Beziehung in einem Diagramm oder im **UML-Modell-Explorer**, und klicken Sie dann auf **aus Modell löschen**.  
  
    > [!CAUTION]
    >  Sie können keine Beziehung aus einem Diagramm entfernen, ohne sie aus dem Modell entfernen.  
  
     Die Beziehung wird aus dem Modell gelöscht und aus jedem Diagramm, in dem sie angezeigt wird.  
  
##  <a name="presentation"></a> Vorbereiten eines Diagramms für die Präsentation  
 Mithilfe der folgenden Funktionen können Sie bestimmte Teile des Diagramms hervorheben, Erläuterungen hinzufügen oder ein Diagramm in unterschiedliche relevante Bereiche unterteilen.  
  
-   Sie können einen beliebigen Teil eines Diagramms in ein Word-, PowerPoint- oder anderes Dokument kopieren. Wählen Sie die Formen und Konnektoren, Sie möchten, mit der rechten Maustaste, und klicken Sie dann auf **Kopie**.  
  
-   Die Farbe der Formen und Konnectoren kann geändert werden. Wählen Sie eine oder mehrere Formen und ändern Sie die **Farbe** Eigenschaft. Wenn Sie das Fenster **Eigenschaften** nicht sehen, drücken Sie **F4**.  
  
-   Sie können auf einigen Arten von Diagrammen, Zeichnen von Linien, Rechtecke und Ellipsen aus dem **einfache Formen** Abschnitt der Toolbox. Diese Formen bilden keinen Teil des UML-Modells.  
  
-   Um einen Bereich zu bezeichnen, können Sie einen Kommentar aus der Toolbox ziehen und legen Sie dann die **Transparent** Eigenschaft **"true"**. Genau wie einfache Formen sind Kommentare kein Bestandteil des UML-Modells und werden nicht im UML-Modell-Explorer angezeigt.  
  
-   Um Hinweise und Erläuterungen zu Modellelementen hinzuzufügen, können Sie Kommentare erstellen und diese dann mit den Elementen verknüpfen.  
  
-   Um eine Spalte oder Zeilenformen im Diagramm sauber auszurichten, können Sie den Befehl „Formen ausrichten“ installieren. Dies ist als UML-beispielerweiterung verfügbar: [UML: Befehl zum Ausrichten von Formen](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)  
  
### <a name="to-export-a-diagram-as-an-image"></a>Exportieren eines Diagramms als Bild  
 Weitere Informationen finden Sie unter [Exportieren von Diagrammen als Bild](../modeling/export-diagrams-as-images.md).  
  
##  <a name="extensions"></a> Erweitern Sie die UML-Designern  
 Sie können neue Funktionalität zu den UML-Tools hinzufügen und die Diagramm-Notation an Ihre eigenen Anforderungen anpassen. Weitere Informationen finden Sie unter [Erweitern von UML-Modellen und Diagrammen](../modeling/extend-uml-models-and-diagrams.md).  
  
 Es sind mehrere Beispielerweiterungen verfügbar. Sie können sie entweder einfach installieren und verwenden oder Sie können ihren Quellcode als Grundlage für eigene Erweiterungen verwenden. Die Beispiele enthalten:  
  
|||  
|-|-|  
|[Ausrichten von Formen](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)|Menübefehl, der Ihnen hilft, ein Diagramm zu bereinigen.|  
|[Link zu Dokumenten](http://code.msdn.microsoft.com/Link-UML-elements-to-0adbf5a8)|Verknüpfen Sie ein UML-Element mit Word-Überschriften, PowerPoint-Folien, Dateien eines beliebigen Typs, UML-Diagrammen oder anderen UML-Elementen. Die Verknüpfung kann einfach durch Ziehen erstellt werden. Später können Sie auf das Element doppelklicken, um das verknüpfte Element anzuzeigen. Beispielsweise können Sie die Anwendungsfälle zu Word-Spezifikationen oder ausführlichen Aktivitätsdiagrammen und Aktionen mit Storyboard-Folien verknüpfen.|  
|[Schnelle Eingabe](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)|Erstellen Sie mithilfe von Texteingabe schnell ein Modell. Nützlich zum Erfassen von Ideen in Besprechungen.|  
|[Farbe nach Stereotyp](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Farben-Klassen nach Stereotyp. Sie können den Code für Ihre eigenen Stereotype leicht erweitern.|  
|[Domänenmodellierung](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4)|Praktische Standardwerte für Geschäftsmodelle. Zuordnungen werden standardmäßig ohne Pfeile angezeigt, und Vorgänge werden nicht in Klassen angezeigt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von UML-Modellierungsprojekten und-Diagrammen](../modeling/create-uml-modeling-projects-and-diagrams.md)   
 [Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)   
 [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)



