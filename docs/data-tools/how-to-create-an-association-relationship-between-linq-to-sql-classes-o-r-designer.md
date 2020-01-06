---
title: Beziehungen zwischen LINQ to SQL Klassen (O/R-Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fb81cf17de86a11d2373f6a545b3efc78e65ada9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586470"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Gewusst wie: Erstellen einer Zuordnung zwischen LINQ to SQL Klassen (O/R-Designer)
Zuordnungen zwischen Entitätsklassen in [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ähneln Beziehungen zwischen Tabellen einer Datenbank. Sie können Zuordnungen zwischen Entitätsklassen mithilfe des Dialogfelds **Zuordnungs-Editor** erstellen.

Sie müssen eine übergeordnete und eine untergeordnete Klasse auswählen, wenn Sie das Dialogfeld **Zuordnungs-Editor** verwenden, um eine Zuordnung zu erstellen. Die übergeordnete Klasse ist die Entitätsklasse, die den Primärschlüssel enthält. Die untergeordnete Klasse ist die Entitätsklasse, die den Fremdschlüssel enthält. Wenn beispielsweise Entitäts Klassen erstellt wurden, die den Tabellen `Northwind Customers` und `Orders` zugeordnet sind, ist die `Customer` Klasse die übergeordnete Klasse, und die `Order` Klasse wäre die untergeordnete Klasse.

> [!NOTE]
> Wenn Sie Tabellen aus **Server-Explorer** oder **Datenbank-Explorer** auf den **objektrelationaler Designer** (**O/R-Designer**) ziehen, werden Zuordnungen automatisch basierend auf den vorhandenen Fremdschlüssel Beziehungen in der Datenbank erstellt.

## <a name="association-properties"></a>Zuordnungseigenschaften
Nach dem Erstellen der Zuordnung kann die Zuordnung im **O/R-Designer** ausgewählt werden, um einige ihrer Eigenschaften im Fenster **Eigenschaften** zu konfigurieren. (Die Zuordnung ist die Linie zwischen den verknüpften Klassen.) In der folgenden Tabelle finden Sie Beschreibungen der Eigenschaften einer Zuordnung.

|Die Eigenschaften-|Beschreibung|
|--------------|-----------------|
|**Kardinalität**|Bestimmt, ob es sich um eine 1:n- oder eine 1:1-Zuordnung handelt.|
|**Untergeordnete Eigenschaft**|Gibt an, ob für die übergeordnete Klasse eine Eigenschaft erstellt werden soll, die eine Auflistung der untergeordneten Datensätze auf der Fremdschlüsselseite der Zuordnung ist oder auf diese Datensätze verweist. Wenn die untergeordnete **Eigenschaft** beispielsweise in der Zuordnung zwischen `Customer` und `Order`auf **true**festgelegt ist, wird für die übergeordnete Klasse eine Eigenschaft mit dem Namen `Orders` erstellt.|
|**Übergeordnete Eigenschaft**|Die Eigenschaft der untergeordneten Klasse, die auf die zugeordnete übergeordnete Klasse verweist. Beispielsweise wird in der Zuordnung zwischen `Customer` und `Order`eine Eigenschaft mit dem Namen `Customer`, die auf den zugeordneten Kunden für einen Auftrag verweist, in der `Order`-Klasse erstellt.|
|**Beteiligte Eigenschaften**|Zeigt die Zuordnungseigenschaften an und stellt eine Schaltfläche mit **Auslassungszeichen** (...) bereit, mit der das Dialogfeld **Zuordnungs-Editor** erneut geöffnet werden kann.|
|**Eindeutig**|Gibt an, ob die Fremdschlüssel-Zielspalten eine Unique-Einschränkung aufweisen.|

## <a name="to-create-an-association-between-entity-classes"></a>So erstellen Sie eine Zuordnung zwischen Entitätsklassen

1. Klicken Sie mit der rechten Maustaste auf die Entitätsklasse, die die übergeordnete Klasse in der Zuordnung darstellt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Zuordnung**.

2. Überprüfen Sie, ob die richtige Einstellung für **Übergeordnete Klasse** im Dialogfeld **Zuordnungs-Editor** ausgewählt ist.

3. Wählen Sie die Einstellung für **Untergeordnete Klasse** im Kombinationsfeld aus.

4. Wählen Sie die **Zuordnungseigenschaften** aus, die die Klassen verbinden. In der Regel wird hier die in der Datenbank definierte Fremdschlüsselbeziehung zugeordnet. Beispielsweise sind die Zuordnungs **Eigenschaften** in der `Customers`-und `Orders` Zuordnung die `CustomerID` für jede Klasse.

5. Klicken Sie auf **OK**, um die Zuordnung zu erstellen.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL Klassen](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext methods (O/R Designer) (DataContext-Methoden (O/R-Designer))](../data-tools/datacontext-methods-o-r-designer.md)
- [Vorgehensweise: Darstellen von Primärschlüsseln](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
