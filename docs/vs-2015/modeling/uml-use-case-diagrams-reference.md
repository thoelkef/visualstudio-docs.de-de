---
title: 'UML-Anwendungsfalldiagramme: Verweisen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.toolbox
- vs.teamarch.usecasediagram.diagram
- vs.teamarch.UMLModelExplorer.usecasediagram
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: aa15772b-eb67-4366-b145-b559112817df
caps.latest.revision: 35
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9fbdf85b3177b88e1a7e97f3cbcd4f901961958d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256307"
---
# <a name="uml-use-case-diagrams-reference"></a>UML-Anwendungsfalldiagramme: Referenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio eine *Anwendungsfalldiagramm* zusammengefasst, die Ihre Anwendung oder das System verwendet und wie sie es verwenden können. Erstellen Sie ein UML-Anwendungsfalldiagramm, auf die **Architektur** Menü klicken Sie auf **neues UML- oder Ebenendiagramm**.  
  
 Ein Anwendungsfalldiagramm dient als zentraler Punkt für die Beschreibung von Benutzeranforderungen. Es beschreibt die Beziehungen zwischen Anforderungen, Benutzern und den Hauptkomponenten. Die Anforderungen werden nicht ausführlich beschrieben. Sie können in separaten Diagrammen oder in Dokumenten beschrieben werden, die mit den einzelnen Anwendungsfällen verknüpft werden können. Informationen, wie Anwendungsfalldiagramme Ihnen zu verstehen helfen können, diskutieren und kommunizieren der benutzeranforderungen, finden Sie unter [Modellieren von benutzeranforderungen](../modeling/model-user-requirements.md).  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  In diesem Thema werden die Elemente beschrieben, die in Anwendungsfalldiagrammen verfügbar sind. Weitere Informationen über das Zeichnen von Anwendungsfalldiagrammen finden Sie unter [UML-Anwendungsfalldiagrammen: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md). Weitere Informationen zum Erstellen und Zeichnen von Modellierungsdiagrammen finden Sie unter [Bearbeiten von UML-Modellen und Diagrammen](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-use-case-diagrams"></a>Lesen von Anwendungsfalldiagrammen  
 In den Tabellen in den folgenden Abschnitten werden die Elemente, die in einem Anwendungsfalldiagramm verfügbar sind, zusammen mit ihren Haupteigenschaften beschrieben. Eine vollständige Liste der Eigenschaften, finden Sie unter [Eigenschaften von Elementen in UML-Anwendungsfalldiagrammen](../modeling/properties-of-elements-on-uml-use-case-diagrams.md).  
  
### <a name="actors-use-cases-and-subsystems"></a>Akteure, Anwendungsfälle und Subsysteme  
 ![Elemente in einem Anwendungsfalldiagramm](../modeling/media/uml-ucovactor.png "UML_UCOvActor")  
  
|**Form "**|**Element**|**Beschreibung und Haupteigenschaften**|  
|---------------|-----------------|-----------------------------------------|  
|1|**Actor**|Stellt Benutzer, Organisationen oder externe Systeme dar, die mit der Anwendung oder dem System interagieren. Ein Akteur ist eine Art von Typ.<br /><br /> -   **Image Path** : der Dateipfad eines Bilds, das statt des Standardakteursymbols verwendet werden soll. Bei dem Symbol sollte es sich um eine Ressourcendatei im Visual Studio-Projekt handeln.|  
|2|**Anwendungsfall**|Stellt die Aktionen dar, die von einem oder mehreren Akteuren ausgeführt werden, um ein bestimmtes Ziel zu erreichen. Ein Anwendungsfall ist eine Art von Typ.<br /><br /> -   **Themen** -das Subsystem, in dem der Anwendungsfall angezeigt wird.|  
|3|**Zuordnung**|Gibt an, dass ein Akteur an einem Anwendungsfall gehörige.|  
|4|**Subsystem oder Komponente**|Das System oder die Anwendung, an dem bzw. der Sie arbeiten, oder ein Teil davon. Dies kann alles von einem großen Netzwerk bis hin zu einer einzelnen Klasse in einer Anwendung sein.<br /><br /> Die Anwendungsfälle, die ein System oder eine Komponente unterstützt, werden innerhalb des Rechtecks angezeigt. Es kann nützlich sein, einige Anwendungsfälle außerhalb des Rechtecks anzuzeigen, um den Umfang des Systems zu verdeutlichen.<br /><br /> Ein Subsystem in einem Anwendungsfalldiagramm weist im Grunde den gleichen Typ wie eine Komponente in einem Komponentendiagramm auf.<br /><br /> -   **Is Indirectly Instantiated** – Wenn "false", das ausführende System verfügt über eine oder mehrere Objekte wird, die direkt diesem Subsystem entsprechen. Bei „true“ ist das Subsystem ein Konstrukt im Entwurf, das im ausführenden System nur durch die Instanziierung seiner Bestandteile angezeigt wird.|  
  
### <a name="structuring-use-cases"></a>Strukturieren von Anwendungsfällen  
 ![Anwendungsfälle mit Include, erweitern und Generalisierung](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")  
  
|Form|**Element**|Beschreibung|  
|-----------|-----------------|-----------------|  
|5|**einschließen**|Ein einschließender Anwendungsfall ruft den eingeschlossenen Anwendungsfall auf. Das Einschließen wird verwendet, um darzustellen, wie ein Anwendungsfall in kleinere Schritte unterteilt ist. Der eingeschlossene Anwendungsfall befindet sich am Ende der Pfeilspitze.<br /><br /> Beachten Sie, dass im Diagramm nicht die Reihenfolge der Schritte angezeigt wird. Sie können ein Aktivitätsdiagramm, Sequenzdiagramm oder anderes Dokument verwenden, um diese Details zu beschreiben.|  
|6|**Erweitern**|Ein erweiternder Anwendungsfall fügt dem erweiterten Anwendungsfall Ziele und Schritte hinzu. Die Erweiterungen führen Vorgänge nur unter bestimmten Bedingungen aus. Der erweiterte Anwendungsfall befindet sich am Ende der Pfeilspitze.<br /><br /> Beachten Sie, dass das Diagramm nicht die genauen Umstände anzeigt, unter denen die Erweiterung angewendet wird: Sie können dies in einem Kommentar oder in einem anderen Dokument aufzeichnen.|  
|7|**Vererbung**|Verknüpft ein spezialisiertes und ein generalisiertes Element. Das generalisierte Element befindet sich am Ende Pfeilspitze.<br /><br /> Ein spezialisierter Anwendungsfall erbt die Ziele und Akteure seiner Generalisierung und kann ggf. entsprechende spezifischere Ziele und Schritte bereitstellen.<br /><br /> Ein spezialisierter Akteur erbt die Anwendungsfälle, Attribute und Zuordnungen seiner Generalisierung und kann weitere Elemente hinzufügen.|  
|8|**Abhängigkeit**|Gibt an, dass der Entwurf der Quelle vom Entwurf des Ziels abhängt.|  
|9|**Kommentar**|Wird verwendet, um dem Diagramm allgemeine Hinweise hinzuzufügen.|  
|10|**Artefakt**|Ein Artefakt stellt einen Link zu einem anderen Diagramm oder Dokument bereit. Sie können diesen erstellen, indem Sie eine Datei aus dem Projektmappen-Explorer ziehen. Es kann eine Verknüpfung mit einer Abhängigkeit zu einem anderen Element des Diagramms eingerichtet werden. Ein Artefakt wird normalerweise verwendet, um einen Anwendungsfall mit einem Sequenzdiagramm, einer OneNote-Seite, einem Word-Dokument oder einer PowerPoint-Präsentation zu verknüpfen, in der bzw. dem der Anwendungsfall ausführlich beschrieben wird. Das Dokument kann entweder ein Element in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe oder ein Dokument an einem freigegebenen Speicherort wie einer SharePoint-Website sein.<br /><br /> -   **Hyperlink**. Die URL oder der Pfad des Diagramms oder Dokuments.<br /><br /> Doppelklicken Sie auf ein Artefakt, um die damit verknüpfte Datei bzw. die verknüpfte Webseite zu öffnen.|  
|11 (nicht angezeigt)|**Pakete**|Anwendungsfälle, Akteure und Subsysteme können in Paketen enthalten sein. Paketformen werden nicht im Diagramm angezeigt, aber Sie können festlegen, die **LinkedPackage** Eigenschaft des Diagramms. Elemente, die Sie anschließend im Diagramm erstellen, werden innerhalb des Pakets platziert. Weitere Informationen finden Sie unter [Definieren von Paketen und Namespaces](../modeling/define-packages-and-namespaces.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [UML-Anwendungsfalldiagramme: Richtlinien](../modeling/uml-use-case-diagrams-guidelines.md)   
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)   
 [UML-Sequenzdiagramme: Referenz](../modeling/uml-sequence-diagrams-reference.md)   
 [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)   
 [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)   
 [UML-Komponentendiagramme: Referenz](../modeling/uml-component-diagrams-reference.md)



