---
title: Lesen von Modellen und Diagrammen in anderen Editionen von Visual Studio | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6a7c944eb3d5378ad0fc1542b90ad182f7eb976
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671280"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Lesen von Modellen und Diagrammen in anderen Versionen von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie ein Model in einer Version von Visual Studio öffnen, die keine Modellerstellung unterstützt, wird das Modell im schreibgeschützten Modus geöffnet. In diesem Modus können Sie das Layout der Diagramme ändern, aber nicht das Modell.

 Welche Versionen von Visual Studio die Modell Erstellung unterstützen, erfahren Sie unter [Versions Unterstützung für Architektur-und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Erhalten von Zugriff auf ein Modell und Diagramme
 Um ein UML-Diagramm oder ein Ebenendiagramm zu lesen, müssen Sie zunächst mithilfe von Visual Studio das Modellierungsprojekt öffnen und dann das Diagramm in diesem öffnen.

 Wenn Sie ein UML-Diagramm oder ein Ebenendiagramm lesen möchten, benötigen Sie daher auch Zugriff auf das Modellierungsprojekt, in dem es erstellt wurde. Dafür können Sie entweder aus [!INCLUDE[esprscc](../includes/esprscc-md.md)] auf das Projekt zugreifen oder eine Kopie der Projektdateien abrufen.

> [!NOTE]
> Dies gilt nicht für Codezuordnungen und .NET-Klassendiagramme, die aus Code generiert wurden. Diese Diagramme können unabhängig von einem Modellierungsprojekt angezeigt werden.

 Um ein UML-Diagramm oder ein Ebenendiagramm zu lesen, benötigen Sie mindestens die folgenden Dateien:

- Die beiden Diagramm Dateien für das Diagramm, das Sie lesen möchten, z. b. " **mydiagram. classdiagram" und "mydiagram. classdiagram. Layout**".

    > [!NOTE]
    > Für ebenendiagramme sollten Sie auch über die Datei mit dem Namen " _mydiagram_**. layerdiagram. supausdrücke**" verfügen.

- Die Modellierungsprojekt Datei (**MyModel. modelproj**)

- Die Stamm Modelldatei (**ModelDefinition\MyModel.UML**)

- Die Paketdateien für ein beliebiges Paket, auf das im Diagramm verwiesen wird (**ModelDefinition\MyPackage.UML**).

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Änderungen, die Sie im schreibgeschützten Modus vornehmen können
 Wenn Sie ein Modell und seine Diagramme in einer Version von Visual Studio öffnen, die keine Modellerstellung unterstützt, können Sie das Modell nicht ändern. Das heißt, dass Sie nicht die Elemente und Beziehungen ändern können, die in den Diagrammen oder im Modell-Explorer angezeigt werden. Sie können jedoch einige Änderungen am Layout der Diagramme vornehmen:

- Anordnen von Formen und Konnektoren im Diagramm.

- Erweitern und Reduzieren von Formen.

  Sie können diese Änderungen speichern. Wenn Sie die Änderungen für andere Benutzer sichtbar machen möchten, müssen Sie mindestens die aktualisierten **Layoutdateien** senden.

## <a name="related-topics"></a><a name="RelatedTopics"></a> Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md)|Ein Ebenendiagramm stellt die Struktur einer vorhandenen oder vorgeschlagenen Architektur dar. Wenn Code geschrieben wird, kann er automatisch anhand eines Ebenendiagramms überprüft werden.|
|[UML-Aktivitätsdiagramme: Referenz](../modeling/uml-activity-diagrams-reference.md)|Ein Aktivitätsdiagramm stellt einen Arbeitsfluss in einem Geschäftsprozess oder in Software dar.|
|[UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)|Ein Klassendiagramm stellt Typen und Beziehungen dar, die in vielen Kontexten verwendet werden, z. B. Code, Datenbankschemas, Kommunikationsprotokolle oder das Glossar der Begriffe, die zum Beschreiben einer Geschäftsdomäne verwendet werden.|
|[UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)|Ein Komponentendiagramm stellt trennbare Teile in einem Softwareentwurf und ihre Schnittstellen dar.|
|[UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)|Ein Sequenzdiagramm zeigt Interaktionen zwischen Elementen in einem Softwareentwurf.|
|[UML-Anwendungsfalldiagramme: Referenz](../modeling/uml-use-case-diagrams-reference.md)|Ein Anwendungsfalldiagramm zeigt die Benutzer eines Systems und die Aktivitäten, die sie ausführen können, um bestimmte Ziele zu erreichen.|

## <a name="see-also"></a>Weitere Informationen
 [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)
