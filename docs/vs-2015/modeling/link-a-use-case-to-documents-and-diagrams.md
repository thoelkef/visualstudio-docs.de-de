---
title: Verknüpfen eines Anwendungsfalls mit Dokumenten und Diagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c713759a8ea75eed3048469327f962668efa4f70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657637"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>Verknüpfen eines Anwendungsfalls mit Dokumenten und Diagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können einen Anwendungsfall in einem Anwendungsfalldiagramm mit einem anderen Diagramm oder Dokument verknüpfen. Beispielsweise können Sie den Anwendungsfall mit den folgenden Diagrammen und Dokumenten verknüpfen:

- Einem Sequenzdiagramm, das zeigt, wie die Ziele des Anwendungsfalls durch Interaktionen zwischen Benutzern und dem System oder seinen Hauptkomponenten realisiert werden.

- Einem Aktivitätsdiagramm, das die genauen Aktionen der Benutzer und des Systems oder seiner Hauptkomponenten bei der Ausführung des Anwendungsfalls zeigt.

- Einer OneNote-Seite oder einem OneNote-Absatz, auf der bzw. in dem der Anwendungsfall ausführlich beschrieben wird.

- Einem Word-Dokument oder einer PowerPoint-Präsentation, in dem bzw. der der Anwendungsfall detailliert beschrieben wird. Sie können solche Dokumente in der Projektmappe oder an einem Ort aufbewahren, der für das Team zugänglich ist, wie z. B. eine SharePoint-Website.

  Um einen Anwendungsfall mit einem Dokument zu verknüpfen, erstellen Sie im Anwendungsfalldiagramm ein Artefakt, und verbinden den Anwendungsfall mit dem Artefakt. In den Eigenschaften des Artefakts legen Sie den Dateipfad des anderen Diagramms oder Dokuments fest. Wenn Sie auf das Artefakt doppelklicken, wird das andere Diagramm oder Dokument geöffnet.

  Sie können mit den einzelnen Anwendungsfällen beliebig viele Artefakte verknüpfen. Sie können Artefakte auch mit anderen Arten von Elementen in einem Anwendungsfalldiagramm verknüpfen.

### <a name="to-open-a-document-associated-with-an-artifact"></a>So öffnen Sie ein mit einem Artefakt verknüpftes Dokument

- Doppelklicken Sie im Anwendungsfalldiagramm auf die Artefaktform.

     Das zugehörige Dokument wird geöffnet.

### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>So verknüpfen Sie einen Anwendungsfall mit einem Diagramm oder einer Datei in der gleichen Projektmappe

1. Zeichnen Sie ein Diagramm, um ein Szenario des Anwendungsfalls zu veranschaulichen, z. B. ein Sequenz- oder Aktivitätsdiagramm.

2. Wechseln Sie zurück zum Anwendungsfalldiagramm.

3. Ziehen Sie das Diagramm oder die Datei vom Projektmappen-Explorer auf einen leeren Teil des Anwendungsfalldiagramms.

4. Stellen Sie eine Verbindung zwischen dem Element und dem Anwendungsfall mithilfe einer **Abhängigkeit**her.

### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>So erstellen Sie einen Link zu einer Projektmappendatei (z. B. ein Word-Dokument oder eine PowerPoint-Präsentation)

1. Fügen Sie das Dokument der Projektmappe hinzu.

    1. Verschieben Sie das Word-Dokument in den gleichen Windows-Ordner wie die Projektmappe.

    2. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf die Lösung, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Vorhandenes Element**.

    3. Navigieren Sie zum Word-Dokument, und klicken Sie auf **Hinzufügen**.

         Das Word-Dokument wird im Projektmappen-Explorer in einem Projektmappenordner angezeigt.

2. Ziehen Sie das Word-Dokument aus dem Projektmappen-Explorer auf einen leeren Teil des Anwendungsfalldiagramms.

     Ein neues Artefakt wird angezeigt.

3. Stellen Sie eine Verbindung zwischen dem Element und dem Anwendungsfall mithilfe einer **Abhängigkeit**her.

### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>So erstellen Sie einen Link zu einem freigegebenen Dokument, einem OneNote-Element oder einer Webseite

1. Sie benötigen die URL des freigegebenen Elements. Dies kann z. b. ein Netzwerkdatei Pfad sein, der mit "\\ \\" beginnt, oder eine Webseite oder SharePoint-URL, beginnend mit "http://", oder ein Link zu einem OneNote-Abschnitt, einer Seite oder einem Absatz, beginnend mit "OneNote:".

2. Klicken Sie in der Toolbox auf **artefaktelement** , und klicken Sie dann in das Anwendungsfall Diagramm.

3. Wenn das neue Element ausgewählt ist, geben Sie die URL in die **Hyperlink** -Eigenschaft ein oder fügen Sie Sie ein.

    > [!NOTE]
    > Wenn Sie einen Dateipfad angeben möchten, empfiehlt es sich, eine Datei entweder in einem gemeinsamen Arbeitsbereich (beginnend mit "\\ \\") oder in einer Datei in der Visual Studio-Projekt Mappe auszuwählen. Dadurch wird sichergestellt, dass der Dateipfad auf dem Computer eines anderen Teammitglieds oder beim Verschieben der Projektmappe seine Gültigkeit behält. Wenn Sie der Projekt Mappe ein Dokument wie ein Word-Dokument hinzufügen möchten, klicken Sie mit der rechten Maustaste auf Projektmappen-Explorer, zeigen Sie auf **Hinzufügen** , und klicken Sie dann auf **Vorhandenes Element**.

## <a name="see-also"></a>Siehe auch
 [UML-Anwendungsfall Diagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md) zu UML- [Anwendungsfall Diagrammen: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md) [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md) [Erstellen von Modellen für Ihre APP](../modeling/create-models-for-your-app.md)
