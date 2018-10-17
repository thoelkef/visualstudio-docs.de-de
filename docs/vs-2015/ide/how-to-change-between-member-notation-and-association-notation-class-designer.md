---
title: 'Vorgehensweise: Wechseln zwischen Member- und Zuordnungsnotation (Klassen-Designer) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1ed7ee328e65f0e76426a21db8f2481e590b0546
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173603"
---
# <a name="how-to-change-between-member-notation-and-association-notation-class-designer"></a>Gewusst wie: Wechseln zwischen Member- und Zuordnungsnotation (Klassen-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Klassendesigner können Sie ändern, wie das Klassendiagramm eine Zuordnungsbeziehung zwischen zwei Typen von der Member- zur Zuordnungsnotation und andersherum darstellt. Member, die als Zuordnungslinien dargestellt werden, bieten oft eine nützliche Visualisierung der Beziehung von Typen.  
  
> [!NOTE]
>  Zuordnungsbeziehungen können als Membereigenschaft oder -feld dargestellt werden. Um die Membernotation in die Zuordnungsnotation zu ändern, muss ein Typ über den Member eines anderen verfügen. Um die Zuordnungsnotation in die Membernotation zu ändern, müssen die zwei Typen über eine Zuordnungslinie verbunden sein. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Zuordnungen zwischen Typen (Klassen-Designer)](../ide/how-to-create-associations-between-types-class-designer.md) Wenn Ihr Projekt über mehrere Klassendiagramme verfügt, betreffen Änderungen, die Sie an der Anzeige der Zuordnungsbeziehung für das Diagramm vornehmen, nur das Diagramm. Um die Darstellung, wie ein anderes Diagramm die Zuordnungsbeziehungen darstellt, zu ändern, öffnen und zeigen Sie das Diagramm an, und befolgen Sie diese Schritte.  
  
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
 [Vorgehensweise: Erstellen der Vererbung zwischen Typen (Klassen-Designer)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Vorgehensweise: Anzeigen der Vererbung zwischen Typen (Klassen-Designer)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Anzeigen von Typen und Beziehungen (Klassen-Designer)](../ide/viewing-types-and-relationships-class-designer.md)   
 [Gewusst wie: Darstellen einer Auflistungszuordnung (Klassen-Designer)](../ide/how-to-visualize-a-collection-association-class-designer.md)



