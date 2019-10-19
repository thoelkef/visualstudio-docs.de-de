---
title: 'Vorgehensweise: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL Klassen (O-R-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c2f6f6f65410336eacf72967c8360a56e8fa5ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610004"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Gewusst wie: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL Klassen (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zuordnungen zwischen Entitätsklassen in [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] ähneln Beziehungen zwischen Tabellen einer Datenbank. Sie können Zuordnungen zwischen Entitätsklassen mithilfe des Dialogfelds **Zuordnungs-Editor** erstellen.

 Sie müssen eine übergeordnete und eine untergeordnete Klasse auswählen, wenn Sie das Dialogfeld **Zuordnungs-Editor** verwenden, um eine Zuordnung zu erstellen. Die übergeordnete Klasse ist die Entitätsklasse, die den Primärschlüssel enthält. Die untergeordnete Klasse ist die Entitätsklasse, die den Fremdschlüssel enthält. Wenn z. B. Entitätsklassen erstellt würden, die den Northwind-Tabellen Customers und Orders zugeordnet sind, wäre die Customer-Klasse die übergeordnete und die Order-Klasse die untergeordnete Klasse.

> [!NOTE]
> Wenn Sie Tabellen aus **Server-Explorer** /**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) ziehen, werden Zuordnungen automatisch basierend auf den vorhandenen Fremdschlüssel Beziehungen in der Datenbank erstellt.

 Wenn Sie die Zuordnung im O/R-Designer ausgewählt haben, können Sie nach dem Erstellen einer Zuordnung einige konfigurierbare Eigenschaften im **Eigenschaften** Fenster auswählen. (Die Zuordnung ist die Linie zwischen den verknüpften Klassen.) In der folgenden Tabelle finden Sie Beschreibungen der Eigenschaften einer Zuordnung.

|property|Beschreibung|
|--------------|-----------------|
|**Kardinalität**|Bestimmt, ob es sich um eine 1:n- oder eine 1:1-Zuordnung handelt.|
|**Untergeordnete Eigenschaft**|Gibt an, ob für die übergeordnete Klasse eine Eigenschaft erstellt werden soll, die eine Auflistung der untergeordneten Datensätze auf der Fremdschlüsselseite der Zuordnung ist oder auf diese Datensätze verweist. Wenn die untergeordnete **Eigenschaft** beispielsweise in der Zuordnung zwischen Kunde und Bestellung auf **true**festgelegt ist, wird für die übergeordnete Klasse eine Eigenschaft mit dem Namen Orders erstellt.|
|**Übergeordnete Eigenschaft**|Die Eigenschaft der untergeordneten Klasse, die auf die zugeordnete übergeordnete Klasse verweist. In der Zuordnung zwischen Customer und Order wird z. B. eine Eigenschaft mit dem Namen Customer, die auf den einer Bestellung zugeordneten Kunden verweist, für die Order-Klasse erzeugt.|
|**Beteiligte Eigenschaften**|Zeigt die Zuordnungseigenschaften an und stellt eine Schaltfläche mit **Auslassungszeichen** (...) bereit, mit der das Dialogfeld **Zuordnungs-Editor** erneut geöffnet werden kann.|
|**Eindeutig**|Gibt an, ob die Fremdschlüssel-Zielspalten eine Unique-Einschränkung aufweisen.|

### <a name="to-create-an-association-between-entity-classes"></a>So erstellen Sie eine Zuordnung zwischen Entitätsklassen

1. Klicken Sie mit der rechten Maustaste auf die Entitätsklasse, die die übergeordnete Klasse in der Zuordnung darstellt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Zuordnung**.

2. Überprüfen Sie, ob die richtige Einstellung für **Übergeordnete Klasse** im Dialogfeld **Zuordnungs-Editor** ausgewählt ist.

3. Wählen Sie die Einstellung für **Untergeordnete Klasse** im Kombinationsfeld aus.

4. Wählen Sie die **Zuordnungseigenschaften** aus, die die Klassen verbinden. In der Regel wird hier die in der Datenbank definierte Fremdschlüsselbeziehung zugeordnet. Beispielsweise sind die Zuordnungs **Eigenschaften** in der Zuordnung "Customers" und "Orders" die CustomerID für jede Klasse.

5. Klicken Sie auf **OK**, um die Zuordnung zu erstellen.

## <a name="see-also"></a>Siehe auch
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen (o-r-Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [DataContext-Methoden (o/r-Designer)](../data-tools/datacontext-methods-o-r-designer.md) Gewusst [wie: darstellen von primär Schlüsseln](https://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)
