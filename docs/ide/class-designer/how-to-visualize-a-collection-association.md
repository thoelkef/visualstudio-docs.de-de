---
title: 'Vorgehensweise: Visualisieren einer Collectionzuordnung (Klassen-Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e074eee5972bcf952108a36f52c0915057c470a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631321"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Vorgehensweise: Visualisieren einer Collectionzuordnung im Klassen-Designer

Eigenschaften und Felder, die Auflistungen eines anderen Typs darstellen, können als Auflistungszuordnung im Klassendiagramm angezeigt werden. Anders als bei einer regulären Zuordnung, bei der ein Feld oder eine Eigenschaft als eine Zeile dargestellt wird, welche die Eigentümerklasse mit dem Feldtyp verknüpft, wird eine Auflistungszuordnung als eine Zeile dargestellt, welche die Eigentümerklasse mit dem gesammelten Typ verknüpft.

## <a name="to-create-a-collection-association"></a>So erstellen Sie eine Auflistungszuordnung

1. Erstellen Sie verschlüsselt eine Eigenschaft oder ein Feld, deren bzw. dessen Typ selbst eine stark typisierte Auflistung ist.

2. Erweitern Sie im Klassendiagramm die Klasse so, dass Felder und Eigenschaften angezeigt werden.

3. Klicken Sie in der Klasse mit der rechten Maustaste auf das Feld oder die Eigenschaft, und wählen Sie **Als Auflistungszuordnung anzeigen** aus.

Die Eigenschaft oder das Feld wird als Zuordnungslinie dargestellt, die mit dem gesammelten Typ verknüpft ist.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: How to: Create associations between types (Vorgehensweise: Erstellen von Zuordnungen zwischen Typen)](how-to-create-associations-between-types.md)
- [Entwerfen von Klassen und Typen](designing-and-viewing-classes-and-types.md)
