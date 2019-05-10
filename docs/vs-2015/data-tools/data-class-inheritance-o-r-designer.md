---
title: Datenklassenvererbung (O / R-Designer) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 37cc40651056b634deb9e81fc7407472485cb72b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670159"
---
# <a name="data-class-inheritance-or-designer"></a>Datenklassenvererbung (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wie andere Objekte können [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Klassen die Vererbung verwenden und aus anderen Klassen abgeleitet werden. Im Code können Sie Vererbungsbeziehungen zwischen Objekten angeben, indem Sie deklarieren, dass eine Klasse von einer anderen erbt. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Der [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) unterstützt das häufig in relationalen Systemen implementierte Konzept der Vererbung einer einzelnen Tabelle.  
  
 Bei der Vererbung einer einzelnen Tabelle gibt es eine einzelne Datenbanktabelle, die Spalten sowohl für Basisklassen als auch für abgeleitete Klassen enthält. Bei relationalen Daten enthält eine Unterscheidungsspalte den Wert, der festlegt, zu welcher Klasse ein bestimmter Datensatz gehört. Betrachten Sie beispielsweise die Tabelle "Persons", die alle in einem Unternehmen beschäftigten Personen enthält. Einige Personen sind Mitarbeiter, andere Führungskräfte. Die Tabelle Persons enthält die Spalte Type, die für Führungskräfte den Wert 1 und für Mitarbeiter den Wert 2 enthält. Der Spalte Type dient als Unterscheidungsspalte. In diesem Szenario können Sie eine Unterklasse von Mitarbeitern erstellen und die Klasse nur mit Datensätzen füllen, die den Type-Wert 2 haben.  
  
 Wenn Sie die Vererbung in Entitätsklassen unter Verwendung von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] konfigurieren, ziehen Sie die einzelne Tabelle, die die Vererbungsdaten enthält, zweimal auf den Designer: einmal für jede Klasse in der Vererbungshierarchie. Nachdem Sie dem Designer die Tabellen hinzugefügt haben, verbinden Sie sie mit einem Vererbungselement aus der Toolbox des **objektrelationaler Designers** und legen dann die vier Vererbungseigenschaften im Fenster **Eigenschaften** fest.  
  
## <a name="inheritance-properties"></a>Vererbungseigenschaften  
 In der folgenden Tabelle sind die Vererbungseigenschaften mit den jeweiligen Beschreibungen aufgeführt:  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Unterscheidungseigenschaft|Die (der Spalte zugeordnete) Eigenschaft, durch die bestimmt wird, zu welcher Klasse der aktuelle Datensatz gehört.|  
|Basisklassen-Diskriminatorwert|Der Wert (in der durch die Unterscheidungseigenschaft angegebenen Spalte), durch den bestimmt wird, das ein Datensatz der Basisklasse angehört.|  
|Diskriminatorwert der abgeleiteten Klasse|Der Wert (in der als Unterscheidungseigenschaft bezeichneten Eigenschaft), durch den bestimmt wird, dass ein Datensatz der abgeleiteten Klasse angehört.|  
|Vererbungsstandard|Die Klasse, die aufgefüllt werden soll, wenn der Wert in der Eigenschaft als festgelegt die **Unterscheidungseigenschaft** stimmt nicht überein, entweder die **Basisklassen-Diskriminatorwert** oder **abgeleitete Klasse Diskriminatorwert**.|  
  
 Das Erstellen eines Objektmodells, das Vererbung verwendet und sich auf relationale Daten bezieht, kann etwas verwirrend sein. Dieses Thema enthält Informationen über die grundlegenden Begriffe und einzelnen Eigenschaften, die zum Konfigurieren der Vererbung erforderlich sind. Die folgenden Themen enthalten eine genauere Erklärung darüber, wie die Vererbung mit dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] konfiguriert wird.  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Beschreibt das Konfigurieren von Entitätsklassen, die Vererbung für eine einzelne Tabelle verwenden, mit dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|  
|[Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mit einer Vererbung für eine einzelne Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Bietet schrittweise Anweisungen zum Konfigurieren von Entitätsklassen, die Vererbung für eine einzelne Tabelle verwenden, mithilfe von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mithilfe der Vererbung einer einzelnen Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [Erste Schritte](http://msdn.microsoft.com/library/db8a557a-fef8-4f4f-bb91-8cff7250ee25)
