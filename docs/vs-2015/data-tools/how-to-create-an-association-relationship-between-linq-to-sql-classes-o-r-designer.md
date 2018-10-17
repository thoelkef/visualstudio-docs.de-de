---
title: 'Gewusst wie: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O / R-Designer) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5c739fcf11cec7eb841b99e58b01ada32cfdfd49
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209364"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Gewusst wie: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zuordnungen zwischen Entitätsklassen in [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] ähneln Beziehungen zwischen Tabellen einer Datenbank. Sie können Zuordnungen zwischen Entitätsklassen mithilfe von erstellen, die **Zuordnungs-Editor** Dialogfeld.  
  
 Sie müssen eine übergeordnete und untergeordnete Klasse auswählen, bei der Verwendung der **Zuordnungs-Editor** Dialogfeld zum Erstellen einer Zuordnung. Die übergeordnete Klasse ist die Entitätsklasse, die den Primärschlüssel enthält. Die untergeordnete Klasse ist die Entitätsklasse, die den Fremdschlüssel enthält. Wenn z. B. Entitätsklassen erstellt würden, die den Northwind-Tabellen Customers und Orders zugeordnet sind, wäre die Customer-Klasse die übergeordnete und die Order-Klasse die untergeordnete Klasse.  
  
> [!NOTE]
>  Beim Ziehen von Tabellen aus **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), Zuordnungen werden automatisch basierend auf den vorhandenen erstellt Fremdschlüssel-Beziehungen in der Datenbank.  
  
 Nachdem Sie eine Zuordnung erstellen, wenn Sie die Zuordnung im O/R-Designer auswählen, es gibt einige konfigurierbaren Eigenschaften in der **Eigenschaften** Fenster. (Die Zuordnung wird durch die Linie zwischen den verknüpften Klassen dargestellt.) In der folgenden Tabelle werden Beschreibungen der Eigenschaften einer Zuordnung aufgeführt.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**Kardinalität**|Bestimmt, ob es sich um eine 1:n- oder eine 1:1-Zuordnung handelt.|  
|**Untergeordnete Eigenschaft**|Gibt an, ob für die übergeordnete Klasse eine Eigenschaft erstellt werden soll, die eine Auflistung der untergeordneten Datensätze auf der Fremdschlüsselseite der Zuordnung ist oder auf diese Datensätze verweist. Z. B. in der Zuordnung zwischen Customer und Order Wenn die **untergeordnete Eigenschaft** nastaven NA hodnotu **"true"**, eine Eigenschaft mit dem Namen Orders wird auf der übergeordneten Klasse erstellt.|  
|**Parent-Eigenschaft**|Die Eigenschaft der untergeordneten Klasse, die auf die zugeordnete übergeordnete Klasse verweist. In der Zuordnung zwischen Customer und Order wird z. B. eine Eigenschaft mit dem Namen Customer, die auf den einer Bestellung zugeordneten Kunden verweist, für die Order-Klasse erzeugt.|  
|**Beteiligte Eigenschaften**|Zeigt die Zuordnungseigenschaften an und stellt eine **mit den Auslassungspunkten** Schaltfläche (…), die erneut öffnet der **Zuordnungs-Editor** Dialogfeld.|  
|**eindeutige**|Gibt an, ob die Fremdschlüssel-Zielspalten eine Unique-Einschränkung aufweisen.|  
  
### <a name="to-create-an-association-between-entity-classes"></a>So erstellen Sie eine Zuordnung zwischen Entitätsklassen  
  
1.  Mit der rechten Maustaste in der Entitätsklasse, die die übergeordnete Klasse in der Zuordnung darstellt, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Zuordnung**.  
  
2.  Überprüfen Sie, ob die richtigen **übergeordnete Klasse** ausgewählt ist, der **Zuordnungs-Editor** Dialogfeld.  
  
3.  Wählen Sie die **untergeordnete Klasse** im Kombinationsfeld.  
  
4.  Wählen Sie die **Zuordnungseigenschaften** , die die Klassen verbinden. In der Regel wird hier die in der Datenbank definierte Fremdschlüsselbeziehung zugeordnet. In der Zuordnung Customers und Orders beispielsweise die **Zuordnungseigenschaften** die CustomerIDs jeder Klasse sind.  
  
5.  Klicken Sie auf **OK** zum Erstellen der Zuordnung.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Vorgehensweise: Darstellen von Primärschlüsseln](http://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)

