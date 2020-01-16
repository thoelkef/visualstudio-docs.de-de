---
title: 'Vorgehensweise: Erweitern von durch den O/R-Designer erstellten Code'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 588eb0f61dbc16fb1625752417ac5257bf48320f
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113681"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Vorgehensweise: Erweitern von durch den O/R-Designer erstellten Code
Vom **O/R-Designer** generierter Code wird erneut generiert, wenn Änderungen an den Entitäts Klassen und anderen Objekten auf der Designer Oberfläche vorgenommen werden. Aufgrund dieser erneuten Codegenerierung wird in der Regel jeglicher Code, der zum generierten Code hinzugefügt wurde, überschrieben, sobald vom Designer neuer Code generiert wird. Der **O/R-Designer** bietet die Möglichkeit, partielle Klassendateien zu generieren, in denen Sie Code hinzufügen können, der nicht überschrieben wird. Ein Beispiel für das Hinzufügen Ihres eigenen Codes zu dem vom **O/R-Designer** generierten Code ist das Hinzufügen der Datenvalidierung zu LINQ to SQL (Entitäts Klassen). Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Validierungen zu Entitäts Klassen](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Hinzufügen von Code zu einer Entitäts Klasse

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>So erstellen Sie eine partielle Klasse und fügen Code zu einer Entitätsklasse hinzu

1. Öffnen oder erstellen Sie eine neue LINQ to SQL Klassen-Datei ( **. dbml** -Datei) im **O/R-Designer**. (Doppelklicken Sie auf die **DBML** -Datei in **Projektmappen-Explorer** oder **Datenbank-Explorer**.)

2. Klicken Sie im **O/R-Designer** mit der rechten Maustaste auf die Klasse, der Sie Validierungen hinzufügen möchten, und klicken Sie dann auf **Code anzeigen**.

     Der Code-Editor wird mit einer partiellen Klasse für die ausgewählte Entitätsklasse geöffnet.

3. Fügen Sie Ihren Code zur Deklaration der partiellen Klasse für die Entitätsklasse hinzu.

## <a name="add-code-to-a-datacontext"></a>Hinzufügen von Code zu einem DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>So erstellen Sie eine partielle Klasse und fügen Code zu einem DataContext hinzu

1. Öffnen oder erstellen Sie eine neue LINQ to SQL Klassen-Datei ( **. dbml** -Datei) im **O/R-Designer**. (Doppelklicken Sie auf die **DBML** -Datei in **Projektmappen-Explorer** oder **Datenbank-Explorer**.)

2. Klicken Sie im **O/R-Designer**mit der rechten Maustaste auf einen leeren Bereich im Designer, und klicken Sie dann auf **Code anzeigen**.

     Der Code-Editor wird mit einer partiellen Klasse für den DataContext geöffnet.

3. Fügen Sie Ihren Code zur Deklaration der partiellen Klasse für den DataContext hinzu.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Walkthrough: Creating LINQ to SQL classes (O-R Designer) (Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O/R-Designer))](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
