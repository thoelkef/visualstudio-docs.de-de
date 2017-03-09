---
title: "CA2100: SQL-Abfragen auf Sicherheitsrisiken &#252;berpr&#252;fen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Review SQL queries for security vulnerabilities"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
  - "CA2100"
helpviewer_keywords: 
  - "CA2100"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2100: SQL-Abfragen auf Sicherheitsrisiken &#252;berpr&#252;fen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode legt die <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName>\-Eigenschaft mithilfe einer Zeichenfolge fest, die aus einem Zeichenfolgenargument für die Methode erstellt wird.  
  
## Regelbeschreibung  
 Diese Regel setzt voraus, dass das Zeichenfolgenargument Benutzereingaben enthält.  Eine aus Benutzereingaben erstellte SQL\-Befehlszeichenfolge ist anfällig für SQL\-Injection\-Angriffe.  Bei einem SQL\-Injection\-Angriff stellt ein böswilliger Benutzer Eingaben bereit, die das Design der Abfrage so ändern, dass die zugrunde liegende Datenbank beschädigt wird oder der Benutzer unbefugten Zugriff auf die zugrunde liegende Datenbank erhält.  Zu den typischen Techniken zählen das Einfügen eines einfachen Anführungszeichens oder eines Apostrophs, das als Trennzeichen für ein SQL\-Zeichenfolgenliteral interpretiert wird, das Einfügen von zwei Bindestrichen, die einen SQL\-Kommentar kennzeichnen, sowie das Einfügen eines Semikolons, wodurch angezeigt wird, dass ein neuer Befehl folgt.  Falls die Benutzereingaben Teil der Abfrage sein müssen, sollten Sie eine der im Folgenden nach ihrer Effektivität aufgelisteten Methoden anwenden, um das Risiko eines Angriffs zu verringern.  
  
-   Verwenden Sie eine gespeicherte Prozedur.  
  
-   Verwenden Sie eine parametrisierte Befehlszeichenfolge.  
  
-   Überprüfen Sie die Benutzereingaben vor dem Erstellen der Befehlszeichenfolge sowohl auf Typ als auch auf Inhalt.  
  
 Die folgenden [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Typen implementieren die <xref:System.Data.IDbCommand.CommandText%2A>\-Eigenschaft oder bieten Konstruktoren, die die Eigenschaften mithilfe eines Zeichenfolgenarguments festlegen.  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> und <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> und <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> und <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>  
  
-   [System.Data.SqlServerCe.SqlCeCommand](assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&autoUpgrade=True) und [System.Data.SqlServerCe.SqlCeDataAdapter](assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&autoUpgrade=True).  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> und <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>  
  
 Beachten Sie, dass diese Regel verletzt wird, wenn die ToString\-Methode eines Typs explizit oder implizit zum Erstellen der Abfragezeichenfolge verwendet wird.  Im Folgenden finden Sie ein Beispiel.  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 Die Regel wird verletzt, da ein böswilliger Benutzer die ToString\(\)\-Methode überschreiben kann.  
  
 Die Regel wird auch verletzt, wenn ToString implizit verwendet wird.  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu korrigieren, verwenden Sie eine parametrisierte Abfrage.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Befehlstext keine Benutzereingaben enthält.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Methode, `UnsafeQuery`, gezeigt, die gegen die Regel verstößt. Außerdem wird eine Methode, `SaferQuery` gezeigt, die die Regel mithilfe einer parametrisierten Befehlszeichenfolge einhält.  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-cs[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## Siehe auch  
 [Übersicht über die Sicherheit](../Topic/Security%20Overview2.md)