---
title: 'Vorgehensweise: Wechseln zwischen Member- und Zuordnungsnotation (Klassen-Designer) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef4216cb18ee46ded66c482749b39715f7f0e252
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-between-member-notation-and-association-notation-class-designer"></a>Gewusst wie: Wechseln zwischen Member- und Zuordnungsnotation (Klassen-Designer)
Im Klassendesigner können Sie ändern, wie das Klassendiagramm eine Zuordnungsbeziehung zwischen zwei Typen von der Member- zur Zuordnungsnotation und andersherum darstellt. Member, die als Zuordnungslinien dargestellt werden, bieten oft eine nützliche Visualisierung der Beziehung von Typen.  
  
> [!NOTE]
>  Zuordnungsbeziehungen können als Membereigenschaft oder -feld dargestellt werden. Um die Membernotation in die Zuordnungsnotation zu ändern, muss ein Typ über den Member eines anderen verfügen. Um die Zuordnungsnotation in die Membernotation zu ändern, müssen die zwei Typen über eine Zuordnungslinie verbunden sein. Weitere Informationen finden Sie unter [How to: Create Associations Between Types (Class Designer) (Vorgehensweise: Erstellen von Zuordnungen zwischen Typen (Klassen-Designer))](how-to-create-associations-between-types.md). Wenn Ihr Projekt über mehrere Klassendiagramme verfügt, betreffen Änderungen, die Sie an der Anzeige der Zuordnungsbeziehung für das Diagramm vornehmen, nur das Diagramm. Um die Darstellung, wie ein anderes Diagramm die Zuordnungsbeziehungen darstellt, zu ändern, öffnen und zeigen Sie das Diagramm an, und befolgen Sie diese Schritte.  
  
### <a name="to-change-member-notation-to-association-notation"></a>Ändern der Membernotation in die Zuordnungsnotation  
  
1.  Öffnen Sie vom Projektknoten im Projektmappen-Explorer aus die Klassendiagrammdatei (CD-Datei).  
  
2.  Führen Sie einen Rechtsklick in der Typform auf dem Klassendiagramm auf die Membereigenschaft oder das -feld aus, die bzw. das die Zuweisung darstellt. Wählen Sie anschließend **Als Zuordnung anzeigen** aus.  
  
    > [!TIP]
    >  Wenn keine Eigenschaften oder Felder in der Typform sichtbar sind, sind die Depots in der Form womöglich reduziert. Um die Typform zu erweitern, führen Sie einen Doppelklick auf den Depotnamen oder einen Rechtsklick in die Typform aus, und wählen Sie **Erweitern** aus.  
  
    Der Member verschwindet aus dem Depot in der Typform, und eine Zuordnungslinie erscheint, um die beiden Typen zu verbinden. Die Zuordnungslinie wird mit dem Namen der Eigenschaft bzw. des Felds bezeichnet.  
  
### <a name="to-change-association-notation-to-member-notation"></a>So ändern Sie die Zuweisungsnotation in die Membernotation  
  
-   Klicken Sie im Klassendiagramm mit der rechten Maustaste auf die Zuordnungslinie, und wählen Sie **Als Eigenschaft anzeigen** oder ggf. **Als Feld anzeigen** aus.  
  
     Die Zuordnungslinie verschwindet, und die Eigenschaft wird im geeigneten Depot in ihrer Typform auf dem Diagramm angezeigt.  
  
## <a name="see-also"></a>Siehe auch
[Vorgehensweise: Erstellen einer Vererbungsbeziehung zwischen Typen](how-to-create-inheritance-between-types.md)  
[Vorgehensweise: Anzeigen der Vererbung zwischen Typen](how-to-view-inheritance-between-types.md)   
[Anzeigen von Typen und Beziehungen](viewing-types-and-relationships.md)   
[Vorgehensweise: Darstellen einer Auflistungszuordnung](how-to-visualize-a-collection-association.md)