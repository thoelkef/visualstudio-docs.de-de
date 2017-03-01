---
title: Lesen von Modellen und Diagrammen in anderen Visual Studio-Editionen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 20
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 9ffc4c39dee2da1d6daa051f478eac18d9670151
ms.lasthandoff: 02/22/2017

---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Lesen von Modellen und Diagrammen in anderen Versionen von Visual Studio
Wenn Sie ein Model in einer Version von Visual Studio öffnen, die keine Modellerstellung unterstützt, wird das Modell im schreibgeschützten Modus geöffnet. In diesem Modus können Sie das Layout der Diagramme ändern, aber nicht das Modell.  
  
 Welche Versionen von Visual Studio die Modellerstellung unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>Erhalten von Zugriff auf ein Modell und Diagramme  
 Um ein Abhängigkeitsdiagramm zu lesen, müssen Sie zunächst Visual Studio verwenden, um das Modellierungsprojekt zu öffnen und öffnen Sie dann das Diagramm im.  
  
 Aus diesem Grund Wenn Sie ein Abhängigkeitsdiagramm lesen möchten müssen auch Zugriff auf das Modellierungsprojekt Sie in denen es erstellt wurde. Dafür können Sie entweder aus [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] auf das Projekt zugreifen oder eine Kopie der Projektdateien abrufen.  
  
> [!NOTE]
>  Dies gilt nicht für Codezuordnungen und .NET-Klassendiagramme, die aus Code generiert wurden. Diese Diagramme können unabhängig von einem Modellierungsprojekt angezeigt werden.  
  
 Um ein Abhängigkeitsdiagramm zu lesen, lautet der minimale Satz von Dateien, die Sie benötigen:  
  
-   Die beiden Diagrammdateien für das Diagramm, das Sie lesen z. B., möchten **MyDiagram.classdiagram and MyDiagram.classdiagram.layout**.  
  
    > [!NOTE]
    >  Bei Abhängigkeitsdiagramme, sollten Sie auch die Datei mit dem Namen haben *MyDiagram***. layerdiagram.suppressions**.  
  
-   Die Modellierungsprojektdatei (**MyModel.modelproj**)  
  
-   Die Stammmodelldatei (**ModelDefinition\MyModel. UML**)  
  
-   Die Paketdateien für jedes Paket, das im Diagramm verwiesen wird (**ModelDefinition\MyPackage. UML**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>Änderungen, die Sie im schreibgeschützten Modus vornehmen können  
 Wenn Sie ein Modell und seine Diagramme in einer Version von Visual Studio öffnen, die keine Modellerstellung unterstützt, können Sie das Modell nicht ändern. Das heißt, dass Sie nicht die Elemente und Beziehungen ändern können, die in den Diagrammen oder im Modell-Explorer angezeigt werden. Sie können jedoch einige Änderungen am Layout der Diagramme vornehmen:  
  
-   Anordnen von Formen und Konnektoren im Diagramm.  
  
-   Erweitern und Reduzieren von Formen.  
  
 Sie können diese Änderungen speichern. Wenn Sie die Änderungen für andere Benutzer sichtbar machen möchten, müssen Sie mindestens Senden der aktualisierten **.layout** Dateien.  
  
##  <a name="a-namerelatedtopicsa-related-topics"></a><a name="RelatedTopics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)|Ein Ebenendiagramm stellt die Struktur einer vorhandenen oder vorgeschlagenen Architektur dar. Wenn Code geschrieben wird, kann er automatisch anhand eines Ebenendiagramms überprüft werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)
