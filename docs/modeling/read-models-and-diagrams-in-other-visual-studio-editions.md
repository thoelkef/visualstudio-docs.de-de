---
title: Lesen von Modellen und Diagrammen in anderen Visual Studio-Editionen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0b25a69293e98ffb56c3536683837d1320fea319
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Lesen von Modellen und Diagrammen in anderen Versionen von Visual Studio
Wenn Sie ein Model in einer Version von Visual Studio öffnen, die keine Modellerstellung unterstützt, wird das Modell im schreibgeschützten Modus geöffnet. In diesem Modus können Sie das Layout der Diagramme ändern, aber nicht das Modell.  
  
 Welche Versionen von Visual Studio Modellerstellung unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>Erhalten von Zugriff auf ein Modell und Diagramme  
 Um eine Abhängigkeit Diagramm lesen zu können, müssen Sie zuerst Visual Studio verwenden, um das Modellierungsprojekt zu öffnen und öffnen Sie das Diagramm im.  
  
 Aus diesem Grund, wenn Sie eine Abhängigkeit Diagramm lesen möchten benötigen Sie auch den Zugriff auf das Modellierungsprojekt in denen er erstellt wurde. Dafür können Sie entweder aus [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] auf das Projekt zugreifen oder eine Kopie der Projektdateien abrufen.  
  
> [!NOTE]
>  Dies gilt nicht für Codezuordnungen und .NET-Klassendiagramme, die aus Code generiert wurden. Diese Diagramme können unabhängig von einem Modellierungsprojekt angezeigt werden.  
  
 Um eine Abhängigkeit Diagramm lesen möchten, weist der minimale Satz von Dateien, die Sie benötigen Folgendes:  
  
-   Die beiden Diagrammdateien für das Diagramm, das Sie lesen z. B., möchten **MyDiagram.classdiagram und MyDiagram.classdiagram.layout**.  
  
    > [!NOTE]
    >  Abhängigkeit Diagramme, Sie sollten außerdem haben die Datei mit dem Namen * MeinDiagramm ***. layerdiagram.suppressions**.  
  
-   Die Modellierungsprojektdatei (**MyModel.modelproj**)  
  
-   Der Stamm-Modelldatei (**ModelDefinition\MyModel. UML**)  
  
-   Die Paketdateien für jedes Paket verwiesen wird, im Diagramm (**ModelDefinition\MyPackage. UML**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>Änderungen, die Sie im schreibgeschützten Modus vornehmen können  
 Wenn Sie ein Modell und seine Diagramme in einer Version von Visual Studio öffnen, die keine Modellerstellung unterstützt, können Sie das Modell nicht ändern. Das heißt, dass Sie nicht die Elemente und Beziehungen ändern können, die in den Diagrammen oder im Modell-Explorer angezeigt werden. Sie können jedoch einige Änderungen am Layout der Diagramme vornehmen:  
  
-   Anordnen von Formen und Konnektoren im Diagramm.  
  
-   Erweitern und Reduzieren von Formen.  
  
 Sie können diese Änderungen speichern. Wenn Sie Ihre Änderungen für andere Benutzer sichtbar machen möchten, müssen Sie mindestens Senden der aktualisierten **.layout** Dateien.  
  
##  <a name="RelatedTopics"></a> Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)|Ein Ebenendiagramm stellt die Struktur einer vorhandenen oder vorgeschlagenen Architektur dar. Wenn Code geschrieben wird, kann er automatisch anhand eines Ebenendiagramms überprüft werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)