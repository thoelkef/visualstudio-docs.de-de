---
title: 'Vorgehensweise: erstellen eine Beziehung zwischen LINQ to SQL-Klassen, die mit dem O/R-Designer'
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
ms.openlocfilehash: 1fee78966a04da53e3b61b85a3440ea8e459771d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Vorgehensweise: Erstellen einer Assoziation zwischen LINQ to SQL-Klassen (O/R-Designer)
Zuordnungen zwischen Entitätsklassen in [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ähneln Beziehungen zwischen Tabellen einer Datenbank. Sie können Zuordnungen zwischen Entitätsklassen mithilfe erstellen die **Zuordnungs-Editor** (Dialogfeld).

Sie müssen eine übergeordnete und untergeordnete Klasse auswählen, bei der Verwendung der **Zuordnungs-Editor** (Dialogfeld), um eine Zuordnung zu erstellen. Die übergeordnete Klasse ist die Entitätsklasse, die den Primärschlüssel enthält. Die untergeordnete Klasse ist die Entitätsklasse, die den Fremdschlüssel enthält. Wenn z. B. Entitätsklassen erstellt würden, die den Northwind-Tabellen Customers und Orders zugeordnet sind, wäre die Customer-Klasse die übergeordnete und die Order-Klasse die untergeordnete Klasse.

> [!NOTE]
>  Beim Ziehen von Tabellen aus **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), Zuordnungen werden automatisch basierend auf den vorhandenen erstellt Fremdschlüssel-Beziehungen in der Datenbank.

## <a name="association-properties"></a>Zuordnungseigenschaften
Nach dem Erstellen einer Zuordnung, wenn Sie die Zuordnung im O/R-Designer auswählen, sind einige konfigurierbaren Eigenschaften in der **Eigenschaften** Fenster. (Die Zuordnung wird durch die Linie zwischen den verknüpften Klassen dargestellt.) In der folgenden Tabelle werden Beschreibungen der Eigenschaften einer Zuordnung aufgeführt.

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|**Kardinalität**|Bestimmt, ob es sich um eine 1:n- oder eine 1:1-Zuordnung handelt.|
|**Untergeordnete Eigenschaft**|Gibt an, ob für die übergeordnete Klasse eine Eigenschaft erstellt werden soll, die eine Auflistung der untergeordneten Datensätze auf der Fremdschlüsselseite der Zuordnung ist oder auf diese Datensätze verweist. Z. B. in der Zuordnung zwischen Customer und Order Wenn die **untergeordnete Eigenschaft** auf festgelegt ist **"true"**, eine Eigenschaft mit dem Namen Orders für die übergeordnete Klasse erstellt wird.|
|**Parent-Eigenschaft**|Die Eigenschaft der untergeordneten Klasse, die auf die zugeordnete übergeordnete Klasse verweist. In der Zuordnung zwischen Customer und Order wird z. B. eine Eigenschaft mit dem Namen Customer, die auf den einer Bestellung zugeordneten Kunden verweist, für die Order-Klasse erzeugt.|
|**Beteiligte Eigenschaften**|Zeigt die Zuordnungseigenschaften an und stellt eine **mit den Auslassungspunkten** Schaltfläche (…), die erneut öffnet die **Zuordnungs-Editor** (Dialogfeld).|
|**Eindeutige**|Gibt an, ob die Fremdschlüssel-Zielspalten eine Unique-Einschränkung aufweisen.|

## <a name="to-create-an-association-between-entity-classes"></a>So erstellen Sie eine Zuordnung zwischen Entitätsklassen

1.  Mit der rechten Maustaste in die Entitätsklasse, die die übergeordnete Klasse in der Zuordnung darstellt, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Zuordnung**.

2.  Überprüfen Sie, ob die richtige **übergeordnete Klasse** ausgewählt ist, der **Zuordnungs-Editor** (Dialogfeld).

3.  Wählen Sie die **untergeordnete Klasse** im Kombinationsfeld.

4.  Wählen Sie die **Zuordnungseigenschaften** , die die Klassen verbinden. In der Regel wird hier die in der Datenbank definierte Fremdschlüsselbeziehung zugeordnet. Beispielsweise ist in der Zuordnung von Customers und Orders der **Zuordnungseigenschaften** sind die CustomerIDs jeder Klasse.

5.  Klicken Sie auf **OK** zum Erstellen der Zuordnung.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Vorgehensweise: Darstellen von Primärschlüsseln](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)