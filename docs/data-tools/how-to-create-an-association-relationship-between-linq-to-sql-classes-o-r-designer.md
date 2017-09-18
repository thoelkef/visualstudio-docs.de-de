---
title: "Vorgehensweise: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O/R-Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vorgehensweise: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O/R-Designer)
Zuordnungen zwischen Entitätsklassen in [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ähneln Beziehungen zwischen Tabellen einer Datenbank.Sie können Zuordnungen zwischen Entitätsklassen mithilfe des Dialogfelds **Zuordnungs\-Editor** erstellen.  
  
 Sie müssen eine übergeordnete und eine untergeordnete Klasse auswählen, wenn Sie das Dialogfeld **Zuordnungs\-Editor** verwenden, um eine Zuordnung zu erstellen.Die übergeordnete Klasse ist die Entitätsklasse, die den Primärschlüssel enthält. Die untergeordnete Klasse ist die Entitätsklasse, die den Fremdschlüssel enthält.Wenn z. B. Entitätsklassen erstellt würden, die den Northwind\-Tabellen Customers und Orders zugeordnet sind, wäre die Customer\-Klasse die übergeordnete und die Order\-Klasse die untergeordnete Klasse.  
  
> [!NOTE]
>  Wenn Sie Tabellen aus **Server\-Explorer**\/**Datenbank\-Explorer** in den [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) ziehen, werden automatisch Zuordnungen auf der Grundlage der existierenden Fremdschlüsselbeziehungen in der Datenbank erstellt.  
  
 Nach dem Erstellen der Zuordnung kann die Zuordnung im O\/R\-Designer ausgewählt werden, um einige ihrer Eigenschaften im Fenster **Eigenschaften** zu konfigurieren.\(Die Zuordnung wird durch die Linie zwischen den verknüpften Klassen dargestellt.\) In der folgenden Tabelle werden Beschreibungen der Eigenschaften einer Zuordnung aufgeführt.  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|****Kardinalität****|Bestimmt, ob es sich um eine 1:n\- oder eine 1:1\-Zuordnung handelt.|  
|****Untergeordnete Eigenschaft****|Gibt an, ob für die übergeordnete Klasse eine Eigenschaft erstellt werden soll, die eine Auflistung der untergeordneten Datensätze auf der Fremdschlüsselseite der Zuordnung ist oder auf diese Datensätze verweist.Wenn z. B. in der Zuordnung zwischen Customer und Order die **Untergeordnete Eigenschaft** auf **True** festgelegt ist, wird für die übergeordnete Klasse die Eigenschaft Orders erzeugt.|  
|****Übergeordnete Eigenschaft****|Die Eigenschaft der untergeordneten Klasse, die auf die zugeordnete übergeordnete Klasse verweist.In der Zuordnung zwischen Customer und Order wird z. B. eine Eigenschaft mit dem Namen Customer, die auf den einer Bestellung zugeordneten Kunden verweist, für die Order\-Klasse erzeugt.|  
|****Einbezogene Eigenschaften****|Zeigt die Zuordnungseigenschaften an und stellt eine Schaltfläche mit **Auslassungszeichen** \(...\) bereit, mit der das Dialogfeld **Zuordnungs\-Editor** erneut geöffnet werden kann.|  
|**Unique**|Gibt an, ob die Fremdschlüssel\-Zielspalten eine Unique\-Einschränkung aufweisen.|  
  
### So erstellen Sie eine Zuordnung zwischen Entitätsklassen  
  
1.  Klicken Sie mit der rechten Maustaste auf die Entitätsklasse, die die übergeordnete Klasse in der Zuordnung darstellt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Zuordnung**.  
  
2.  Überprüfen Sie, ob die richtige **Übergeordnete Klasse** im Dialogfeld **Zuordnungs\-Editor** ausgewählt ist.  
  
3.  Wählen Sie die **Untergeordnete Klasse** im Kombinationsfeld aus.  
  
4.  Wählen Sie die **Zuordnungseigenschaften** aus, die die Klassen verbinden.In der Regel wird hier die in der Datenbank definierte Fremdschlüsselbeziehung zugeordnet.In der Zuordnung von Customers und Orders beispielsweise sind die **Zuordnungseigenschaften** die CustomerIDs jeder Klasse.  
  
5.  Klicken Sie auf **OK**, um die Zuordnung zu erstellen.  
  
## Siehe auch  
 [Übersicht über den O\/R\-Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Vorgehensweise: Darstellen primärer Schlüssel](../Topic/How%20to:%20Represent%20Primary%20Keys.md)