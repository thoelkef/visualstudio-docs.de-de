---
title: 'Vorgehensweise: Erstellen Sie eine Beziehung zwischen LINQ to SQL-Klassen, die mit dem O/R-Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ab66f41a6510eb8cf2376cb7bb4d6fa21e7b1159
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001329"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Vorgehensweise: Erstellen Sie eine Zuordnung zwischen LINQ to SQL-Klassen (O/R Designer)
Zuordnungen zwischen Entitätsklassen in [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ähneln Beziehungen zwischen Tabellen einer Datenbank. Sie können Zuordnungen zwischen Entitätsklassen mithilfe des Dialogfelds **Zuordnungs-Editor** erstellen.

Sie müssen eine übergeordnete und eine untergeordnete Klasse auswählen, wenn Sie das Dialogfeld **Zuordnungs-Editor** verwenden, um eine Zuordnung zu erstellen. Die übergeordnete Klasse ist die Entitätsklasse, die den Primärschlüssel enthält. Die untergeordnete Klasse ist die Entitätsklasse, die den Fremdschlüssel enthält. Angenommen, Entitätsklassen, die zugeordnet erstellt wurden die `Northwind Customers` und `Orders` Tabellen, die `Customer` Klasse wäre die übergeordnete Klasse und die `Order` Klasse wäre der untergeordneten Klasse.

> [!NOTE]
>  Beim Ziehen von Tabellen aus **Server-Explorer** oder **Datenbank-Explorer** auf die **Object Relational Designer** (**O/R Designer**), Zuordnungen werden automatisch basierend auf den vorhandenen Fremdschlüssel-Beziehungen in der Datenbank erstellt.

## <a name="association-properties"></a>Zuordnungseigenschaften
Nach dem Erstellen der Zuordnung kann die Zuordnung im **O/R-Designer** ausgewählt werden, um einige ihrer Eigenschaften im Fenster **Eigenschaften** zu konfigurieren. (Die Zuordnung wird durch die Linie zwischen den verknüpften Klassen dargestellt.) In der folgenden Tabelle werden Beschreibungen der Eigenschaften einer Zuordnung aufgeführt.

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|**Kardinalität**|Bestimmt, ob es sich um eine 1:n- oder eine 1:1-Zuordnung handelt.|
|**Untergeordnete Eigenschaft**|Gibt an, ob für die übergeordnete Klasse eine Eigenschaft erstellt werden soll, die eine Auflistung der untergeordneten Datensätze auf der Fremdschlüsselseite der Zuordnung ist oder auf diese Datensätze verweist. Z. B. in der Zuordnung zwischen `Customer` und `Order`, wenn die **untergeordnete Eigenschaft** nastaven NA hodnotu **"true"**, eine Eigenschaft namens `Orders` auf der übergeordneten Klasse erstellt wird.|
|**Übergeordnete Eigenschaft**|Die Eigenschaft der untergeordneten Klasse, die auf die zugeordnete übergeordnete Klasse verweist. Z. B. in der Zuordnung zwischen `Customer` und `Order`, eine Eigenschaft namens `Customer` , die auf den zugeordneten Kunden verweist auf ein Auftrag erstellt wird die `Order` Klasse.|
|**Beteiligte Eigenschaften**|Zeigt die Zuordnungseigenschaften an und stellt eine Schaltfläche mit **Auslassungszeichen** (...) bereit, mit der das Dialogfeld **Zuordnungs-Editor** erneut geöffnet werden kann.|
|**Eindeutig**|Gibt an, ob die Fremdschlüssel-Zielspalten eine Unique-Einschränkung aufweisen.|

## <a name="to-create-an-association-between-entity-classes"></a>So erstellen Sie eine Zuordnung zwischen Entitätsklassen

1.  Klicken Sie mit der rechten Maustaste auf die Entitätsklasse, die die übergeordnete Klasse in der Zuordnung darstellt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Zuordnung**.

2.  Überprüfen Sie, ob die richtige Einstellung für **Übergeordnete Klasse** im Dialogfeld **Zuordnungs-Editor** ausgewählt ist.

3.  Wählen Sie die Einstellung für **Untergeordnete Klasse** im Kombinationsfeld aus.

4.  Wählen Sie die **Zuordnungseigenschaften** aus, die die Klassen verbinden. In der Regel wird hier die in der Datenbank definierte Fremdschlüsselbeziehung zugeordnet. Z. B. in der `Customers` und `Orders` Zuordnung der **Zuordnungseigenschaften** sind die `CustomerID` für jede Klasse.

5.  Klicken Sie auf **OK**, um die Zuordnung zu erstellen.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext methods (O/R Designer) (DataContext-Methoden (O/R-Designer))](../data-tools/datacontext-methods-o-r-designer.md)
- [Vorgehensweise: Darstellen von Primärschlüsseln](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)