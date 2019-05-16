---
title: Verwalten von Modellen und Diagrammen unter Versionskontrolle | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55142e000a22b6e45543c6fc14594a12c93f4f92
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680290"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>Verwalten von Modellen und Diagrammen unter Versionskontrolle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwalten Sie unterschiedliche Versionen von Modellierungsprojekten und -diagrammen, einschließlich Code Maps (DGML-Dateien), mithilfe von [Team Foundation-Versionskontrolle oder Git](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314)– entweder mit lokalem Team Foundation Server oder in der Cloud mit Visual Studio Team Services.  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!IMPORTANT]
> Besondere Sorgfalt ist erforderlich, wenn mehrere Benutzer am gleichen Modellierungsprojekt arbeiten. Erfahren Sie, wie Sie [Modelle in mittelgroßen oder großen Projekten organisieren](../modeling/structure-your-modeling-solution.md)können.  
  
## <a name="ModelingProjects"></a> Dateien in einem Modellierungsprojekt  
 Mehrere Benutzer können gleichzeitig an einem Modellierungsprojekt arbeiten, solange sie an unterschiedlichen Dateien arbeiten.  
  
 Um Konflikte zwischen von verschiedenen Benutzern vorgenommenen Änderungen zu vermeiden oder zu beheben, ist es wichtig zu verstehen, wie das Modell in Dateien gespeichert wird.  
  
- Jedes Paket wird in einer separaten **.uml** -Datei gespeichert, die jeweils im **ModelDefinition** -Projektordner abgelegt wird. Das Modell verfügt auch über eine **.uml** -Datei. Wenn eine dieser Dateien gelöscht oder beschädigt wird, geht das entsprechende Paket oder Modell verloren.  
  
- Jedes Diagramm wird in zwei Dateien gespeichert. Beispiel für ein Klassendiagramm:  
  
    - **DiagramName.classdiagram** – Wenn diese Datei gelöscht wird oder beschädigt ist, geht das Diagramm verloren. Die im Diagramm angezeigten Klassen und Zuordnungen bleiben jedoch im Modell erhalten und werden im UML-Modell-Explorer angezeigt.  
  
    - **DiagramName.classdiagram.layout** – Wenn diese Datei gelöscht wird, werden die Formen weiterhin im Diagramm angezeigt, aber ihre Größen und Positionen gehen verloren. Jede Layoutdatei ist einer Diagrammdatei untergeordnet. Um diese anzuzeigen, klicken Sie im Projektmappen-Explorer neben der Diagrammdatei auf [+].  
  
> [!NOTE]
> Es ist wichtig, die Konsistenz zwischen den Dateien beizubehalten. Wenn Sie z. B. die Quellcodeverwaltung verwenden, um Änderungen in einer UML-Datei zurückzusetzen, sollten Sie die entsprechenden Änderungen in den *DIAGRAM- und LAYOUT-Dateien gleichzeitig zurücksetzen. Elemente im dargestellt ein. \*Diagrammdatei verloren, wenn sie nicht auch in einem UML-Datei dargestellt werden.  
  
## <a name="Shared"></a> Arbeiten an freigegebenen Modellierungsprojekten  
 So minimieren Sie Konflikte bei der gleichzeitigen Arbeit an verschiedenen Teilen eines Projekts:  
  
- Unterteilen Sie das Modellierungsprojekt in Pakete, die jeweils andere Arbeitsbereiche darstellen. Verschieben Sie das gesamte Modell in Pakete, anstatt es im Stammmodell zu belassen. Weitere Informationen finden Sie unter [Definieren von Paketen und Namespaces](../modeling/define-packages-and-namespaces.md).  
  
- Verschiedene Benutzer sollten nicht gleichzeitig am gleichen Paket oder Diagramm arbeiten.  
  
- Wenn Sie Profile verwenden, müssen sie sicherstellen, dass überall die gleichen Profile installiert sind. Finden Sie unter [Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
- So stellen Sie sicher, dass Sie nur das Paket ändern, an dem Sie arbeiten:  
  
    - Legen Sie die **LinkedPackage** -Eigenschaft einer UML-Klasse, einer UML-Komponente oder eines UML-Anwendungsfalldiagramms fest.  
  
    - Ziehen Sie im UML-Modell-Explorer eine Aktivität oder Interaktion in ein Paket, sobald Sie es erstellt haben. Dieses Element wird im UML-Modell-Explorer angezeigt, wenn Sie im Aktivitäts- oder Sequenzdiagramm den ersten Knoten erstellen.  
  
- Benennen Sie als Hilfe beim Nachverfolgen der Pakete die Paketdateien um, um die tatsächlichen Paketnamen widerzuspiegeln.  
  
- Führen Sie in [!INCLUDE[esprscc](../includes/esprscc-md.md)]die Vorgänge **Einchecken** und **Neuste Version abrufen** immer für das gesamte Modellierungsprojekt aus, niemals für einzelne Dateien.  
  
- Führen Sie direkt vor dem Einchecken in das Modellierungsprojekt immer einen **Get** -Vorgang aus.  
  
- Schließen Sie vor dem Ausführen eines **Get** -Vorgangs stets alle Diagramme.  
  
    > [!NOTE]
    > Wenn beim Ausführen eines **Get**-Vorgangs eine Datei geöffnet ist und der Vorgang zu lokalen Änderungen führt, werden Sie aufgefordert, die Datei neu zu laden. Klicken Sie in diesem Fall auf **Nein**, und laden Sie dann das vollständige Projekt neu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Modellierungsprojektknoten, klicken Sie auf **Projekt entladen**und dann auf **Projekt erneut laden**.  
  
### <a name="Exclusive"></a> Änderungen, die exklusiven Zugriff auf das Modell erfordern.  
 Bevor Sie die folgenden Arten von Änderungen vornehmen, müssen Sie sicherstellen, dass für das gesamte Projekt eine Auschecksperre gilt.  
  
- Umbenennen oder Löschen von Elementen, auf die von anderen Paketen verwiesen wird  
  
- Ändern der Eigenschaften von Beziehungen, die über Paketbegrenzungen hinweg gelten  
  
- Informationen zu Auschecksperren finden Sie unter [Auschecken und Bearbeiten von Dateien](https://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a).  
  
##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>So verschieben Sie eine Diagrammdatei in einen oder aus einem Projektordner  
  
1. Starten Sie die **Developer-Eingabeaufforderung für Visual Studio**.  
  
2. Verwenden Sie **tf rename** , um die Diagrammdatei und die zugehörige **.layout** -Datei zu verschieben:  
  
     `tf rename sourcePath targetPath`  
  
3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Datei, und klicken Sie dann auf **Aus Projekt ausschließen**.  
  
4. Fügen Sie die Datei dem Zielordner hinzu.  
  
     Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Zielordner oder das Projekt, zeigen Sie auf **Hinzufügen**, und klicken Sie anschließend auf **Vorhandenes Element**. Wählen Sie im Dialogfeld die Diagrammdatei aus, und klicken Sie dann auf **Hinzufügen**. Die Layoutdatei wird automatisch hinzugefügt.  
  
    > [!NOTE]
    > Sie können die Datei nicht in ein anderes Projekt verschieben.  
  
## <a name="Merging"></a> Zusammenführen von Änderungen in Modelldateien und Diagrammen  
 Nachdem mehrere Benutzer gleichzeitig an einem Modell gearbeitet haben, werden Sie von [!INCLUDE[esprscc](../includes/esprscc-md.md)] aufgefordert, die Änderungen in den Modelldateien zusammenzuführen. Durch das Arbeiten an separaten Projekten, wie in den vorherigen Abschnitten beschrieben, können die meisten Zusammenführungen vermieden werden. Normalerweise können die restlichen Konflikte auf sichere Weise automatisch zusammengeführt werden. Die folgenden Arten von Änderungen sollten keine Schwierigkeiten verursachen:  
  
- Typen von Lebenslinien. Wenn Sie einer Interaktion (Sequenzdiagramm) eine Lebenslinie hinzufügen, wird deren Typ im Stammmodell gespeichert, es sei denn, Sie haben die Lebenslinie aus einem vorhandenen Typ erstellt.  
  
- Neue Aktivitäten und Interaktionen werden anfänglich im Stammmodell gespeichert.  
  
- Hinzufügen von Elementen und Beziehungen  
  
- Umbenennen oder Löschen von Elementen, auf die nur innerhalb ihres eigenen Pakets verwiesen wird  
  
## <a name="see-also"></a>Siehe auch  
 [Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)   
 [Freigeben von Modellen und Exportieren von Diagrammen](../modeling/share-models-and-exporting-diagrams.md)
