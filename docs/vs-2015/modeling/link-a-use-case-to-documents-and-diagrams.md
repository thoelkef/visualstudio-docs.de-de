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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 012ab6828364af155b52bc19d9a83564b2126a6b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088677"
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
  
4. Verbinden Sie das Artefakt mit die Verwendung von Groß-/Kleinschreibung mit einem **Abhängigkeit**.  
  
### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>So erstellen Sie einen Link zu einer Projektmappendatei (z. B. ein Word-Dokument oder eine PowerPoint-Präsentation)  
  
1. Fügen Sie das Dokument der Projektmappe hinzu.  
  
    1. Verschieben Sie das Word-Dokument in den gleichen Windows-Ordner wie die Projektmappe.  
  
    2. Im Projektmappen-Explorer mit der Maustaste der Projektmappe, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **vorhandenes Element**.  
  
    3. Navigieren Sie zum Word-Dokument, und klicken Sie auf **hinzufügen**.  
  
         Das Word-Dokument wird im Projektmappen-Explorer in einem Projektmappenordner angezeigt.  
  
2. Ziehen Sie das Word-Dokument aus dem Projektmappen-Explorer auf einen leeren Teil des Anwendungsfalldiagramms.  
  
     Ein neues Artefakt wird angezeigt.  
  
3. Verbinden Sie das Artefakt mit die Verwendung von Groß-/Kleinschreibung mit einem **Abhängigkeit**.  
  
### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>So erstellen Sie einen Link zu einem freigegebenen Dokument, einem OneNote-Element oder einer Webseite  
  
1. Sie benötigen die URL des freigegebenen Elements. Dies kann sein, z. B. eine beginnender Netzwerkdateipfad "\\\\", oder die Seite einer Webseite oder Sharepoint-URL "http://" beginnende oder ein Link zu einem OneNote-Abschnitt oder-Absatz "Onenote:".  
  
2. Klicken Sie in der Toolbox auf **Artefakt** , und klicken Sie dann in das Anwendungsfalldiagramm.  
  
3. Das neue Artefakt aus, und geben oder fügen Sie die URL in die **Hyperlink** Eigenschaft.  
  
    > [!NOTE]
    >  Wenn Sie einen Dateipfad angeben möchten, empfiehlt sich, eine Datei auszuwählen, entweder in einem gemeinsamen Arbeitsbereich (beginnend mit "\\\\"), oder eine Datei in Visual Studio-Projektmappe. Dadurch wird sichergestellt, dass der Dateipfad auf dem Computer eines anderen Teammitglieds oder beim Verschieben der Projektmappe seine Gültigkeit behält. Um ein Dokument wie z. B. ein Word-Dokument der Projektmappe hinzuzufügen, mit der rechten Maustaste in der Projektmappe im Projektmappen-Explorer, zeigen Sie auf **hinzufügen** , und klicken Sie dann auf **vorhandenes Element**.  
  
## <a name="see-also"></a>Siehe auch  
 [UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)   
 [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)   
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)   
 [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)
