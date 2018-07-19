---
title: 'Vorgehensweise: Erstellen Sie eine Beziehung zwischen LINQ to SQL-Klassen, die mit dem O/R-Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d247603e14f431e44aa7c1589ba2ecd7463fac02
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089528"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Gewusst wie: Erstellen einer Assoziation zwischen LINQ to SQL-Klassen (O/R Designer)
Zuordnungen zwischen Entitätsklassen in [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ähneln Beziehungen zwischen Tabellen einer Datenbank. Sie können Zuordnungen zwischen Entitätsklassen mithilfe von erstellen, die **Zuordnungs-Editor** Dialogfeld.

Sie müssen eine übergeordnete und untergeordnete Klasse auswählen, bei der Verwendung der **Zuordnungs-Editor** Dialogfeld zum Erstellen einer Zuordnung. Die übergeordnete Klasse ist die Entitätsklasse, die den Primärschlüssel enthält. Die untergeordnete Klasse ist die Entitätsklasse, die den Fremdschlüssel enthält. Angenommen, Entitätsklassen, die zugeordnet erstellt wurden die `Northwind Customers` und `Orders` Tabellen, die `Customer` Klasse wäre die übergeordnete Klasse und die `Order` Klasse wäre der untergeordneten Klasse.

> [!NOTE]
>  Beim Ziehen von Tabellen aus **Server-Explorer** oder **Datenbank-Explorer** auf die **Object Relational Designer** (**O/R Designer**), Zuordnungen werden automatisch basierend auf den vorhandenen Fremdschlüssel-Beziehungen in der Datenbank erstellt.

## <a name="association-properties"></a>Eigenschaften der computerzuordnung
Nach der Erstellung einer Zuordnung, wenn Sie die Zuordnung im Auswählen der **O/R-Designer**, es gibt einige konfigurierbaren Eigenschaften in der **Eigenschaften** Fenster. (Die Zuordnung wird durch die Linie zwischen den verknüpften Klassen dargestellt.) In der folgenden Tabelle werden Beschreibungen der Eigenschaften einer Zuordnung aufgeführt.

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|**Kardinalität**|Bestimmt, ob es sich um eine 1:n- oder eine 1:1-Zuordnung handelt.|
|**Untergeordnete Eigenschaft**|Gibt an, ob für die übergeordnete Klasse eine Eigenschaft erstellt werden soll, die eine Auflistung der untergeordneten Datensätze auf der Fremdschlüsselseite der Zuordnung ist oder auf diese Datensätze verweist. Z. B. in der Zuordnung zwischen `Customer` und `Order`, wenn die **untergeordnete Eigenschaft** nastaven NA hodnotu **"true"**, eine Eigenschaft namens `Orders` auf der übergeordneten Klasse erstellt wird.|
|**Parent-Eigenschaft**|Die Eigenschaft der untergeordneten Klasse, die auf die zugeordnete übergeordnete Klasse verweist. Z. B. in der Zuordnung zwischen `Customer` und `Order`, eine Eigenschaft namens `Customer` , die auf den zugeordneten Kunden verweist auf ein Auftrag erstellt wird die `Order` Klasse.|
|**Beteiligte Eigenschaften**|Zeigt die Zuordnungseigenschaften an und stellt eine **mit den Auslassungspunkten** Schaltfläche (…), die erneut öffnet der **Zuordnungs-Editor** Dialogfeld.|
|**eindeutige**|Gibt an, ob die Fremdschlüssel-Zielspalten eine Unique-Einschränkung aufweisen.|

## <a name="to-create-an-association-between-entity-classes"></a>So erstellen Sie eine Zuordnung zwischen Entitätsklassen

1.  Mit der rechten Maustaste in der Entitätsklasse, die die übergeordnete Klasse in der Zuordnung darstellt, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Zuordnung**.

2.  Überprüfen Sie, ob die richtigen **übergeordnete Klasse** ausgewählt ist, der **Zuordnungs-Editor** Dialogfeld.

3.  Wählen Sie die **untergeordnete Klasse** im Kombinationsfeld.

4.  Wählen Sie die **Zuordnungseigenschaften** , die die Klassen verbinden. In der Regel wird hier die in der Datenbank definierte Fremdschlüsselbeziehung zugeordnet. Z. B. in der `Customers` und `Orders` Zuordnung der **Zuordnungseigenschaften** sind die `CustomerID` für jede Klasse.

5.  Klicken Sie auf **OK** zum Erstellen der Zuordnung.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Gewusst wie: Darstellen von Primärschlüsseln](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)