---
title: 'Vorgehensweise: Erweitern von mit dem O/R-Designer erstelltem Code'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 41704ad1f43dadee1efd16102281173215bad4e0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933783"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Vorgehensweise: Erweitern von mit dem O/R-Designer erstelltem Code
Vom generierten Code der **O/R Designer** erneut generiert wird, wenn Änderungen an die Entitätsklassen und andere Objekte auf der Designeroberfläche vorgenommen werden. Aufgrund dieser erneuten Codegenerierung wird in der Regel jeglicher Code, der zum generierten Code hinzugefügt wurde, überschrieben, sobald vom Designer neuer Code generiert wird. Die **O/R Designer** bietet die Möglichkeit, Dateien mit partiellen Klassen zu generieren, in dem Sie hinzufügen können, Sie Code, der nicht überschrieben werden. Ein Beispiel für das Hinzufügen eigenen Codes, die vom generierten Code der **O/R Designer** ist Hinzufügen der datenvalidierung zu LINQ to SQL (Entität)-Klassen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Validierungen zu Entitätsklassen](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Fügen Sie Code in eine Entitätsklasse hinzu.

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>So erstellen Sie eine partielle Klasse und fügen Code zu einer Entitätsklasse hinzu

1.  Öffnen oder erstellen Sie eine neue LINQ to SQL-Klassendatei (**dbml** Datei) in der **O/R Designer**. (Doppelklicken Sie auf die **dbml** Datei **Projektmappen-Explorer** oder **Datenbank-Explorer**.)

2.  Klicken Sie im **O/R-Designer** mit der rechten Maustaste auf die Klasse, der Sie Validierungen hinzufügen möchten, und klicken Sie dann auf **Code anzeigen**.

     Der Code-Editor wird mit einer partiellen Klasse für die ausgewählte Entitätsklasse geöffnet.

3.  Fügen Sie Ihren Code zur Deklaration der partiellen Klasse für die Entitätsklasse hinzu.

## <a name="add-code-to-a-datacontext"></a>Fügen Sie Code zu einem DataContext hinzu.

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>So erstellen Sie eine partielle Klasse und fügen Code zu einem DataContext hinzu

1.  Öffnen oder erstellen Sie eine neue LINQ to SQL-Klassendatei (**dbml** Datei) in der **O/R Designer**. (Doppelklicken Sie auf die **dbml** Datei **Projektmappen-Explorer** oder **Datenbank-Explorer**.)

2.  In der **O/R Designer**mit der rechten Maustaste auf einen leeren Bereich im Designer, und klicken Sie dann auf **Ansichtscode**.

     Der Code-Editor wird mit einer partiellen Klasse für den DataContext geöffnet.

3.  Fügen Sie Ihren Code zur Deklaration der partiellen Klasse für den DataContext hinzu.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)