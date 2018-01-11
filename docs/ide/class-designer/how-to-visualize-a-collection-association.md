---
title: 'Vorgehensweise: Darstellen einer Auflistungszuordnung (Klassen-Designer) | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 234c70896b28f27815b7563b814fb6b4bd933ebd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-visualize-a-collection-association-class-designer"></a>Gewusst wie: Darstellen einer Auflistungszuordnung (Klassen-Designer)
Eigenschaften und Felder, die Auflistungen eines anderen Typs darstellen, können als Auflistungszuordnung im Klassendiagramm angezeigt werden. Anders als bei einer regulären Zuordnung, bei der ein Feld oder eine Eigenschaft als eine Zeile dargestellt wird, welche die Eigentümerklasse mit dem Feldtyp verknüpft, wird eine Auflistungszuordnung als eine Zeile dargestellt, welche die Eigentümerklasse mit dem gesammelten Typ verknüpft.  
  
### <a name="to-create-a-collection-association"></a>So erstellen Sie eine Auflistungszuordnung  
  
1.  Erstellen Sie verschlüsselt eine Eigenschaft oder ein Feld, deren bzw. dessen Typ selbst eine stark typisierte Auflistung ist.  
  
2.  Erweitern Sie im Klassendiagramm die Klasse so, dass Felder und Eigenschaften angezeigt werden.  
  
3.  Klicken Sie in der Klasse mit der rechten Maustaste auf das Feld oder die Eigenschaft, und wählen Sie **Als Auflistungszuordnung anzeigen** aus.  
  
     Die Eigenschaft oder das Feld wird als Zuordnungslinie dargestellt, die mit dem gesammelten Typ verknüpft ist.  
  
## <a name="see-also"></a>Siehe auch
[Vorgehensweise: Erstellen von Zuordnungen zwischen Typen](how-to-create-associations-between-types.md)   
[Entwerfen von Klassen und Typen](designing-classes-and-types.md)   
[Anzeigen von Typen und Beziehungen](viewing-types-and-relationships.md)