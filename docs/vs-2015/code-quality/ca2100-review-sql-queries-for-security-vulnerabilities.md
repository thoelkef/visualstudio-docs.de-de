---
title: 'CA2100: Überprüfen SQL-Abfragen für Sicherheitsrisiken | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7d39d324942348050d05dfb5273a9b4075747b1c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206504"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: SQL-Abfragen auf Sicherheitsrisiken überprüfen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode legt die <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> Eigenschaft mithilfe einer Zeichenfolge, die aus einem Zeichenfolgenargument für die Methode erstellt wird.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel setzt voraus, dass das Zeichenfolgenargument Benutzereingaben enthält. Eine aus Benutzereingaben erstellte SQL-Befehlszeichenfolge ist anfällig für SQL-Injection-Angriffe. In einer SQL-Injection-Angriff stellt ein böswilliger Benutzer Eingaben, die den Entwurf einer Abfrage zu beschädigen oder damit unautorisierter Zugriff auf die zugrunde liegende Datenbank ändert. Typische Techniken sind die Einfügung von einem einzelnen Anführungszeichen oder Apostroph, die die SQL-Zeichenfolgenliteral-Trennzeichen ist: zwei Gedankenstriche, was bedeutet einen SQL-Kommentar; und ein Semikolon, was bedeutet, dass ein neuer Befehl folgt. Wenn der Benutzereingabe Teil der Abfrage, verwenden Sie eine der folgenden sein muss aufgeführt, in der Reihenfolge der Effektivität, um das Risiko von Angriffen zu verringern.

-   Verwenden Sie eine gespeicherte Prozedur.

-   Verwenden Sie eine parametrisierten Befehl-Zeichenfolge.

-   Überprüfen Sie die Benutzereingabe für Typ und Inhalt vor dem Erstellen der Befehlszeichenfolge.

 Die folgenden [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Typen implementieren die <xref:System.Data.IDbCommand.CommandText%2A> Eigenschaft oder Konstruktoren, die die Eigenschaft festgelegt wird, mit der ein Zeichenfolgenargument bereitstellen.

-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> und <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> und <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> und <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

-   [System.Data.SqlServerCe.SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) und [System.Data.SqlServerCe.SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> und <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

 Beachten Sie, dass diese Regel verletzt wird, wenn die ToString-Methode eines Typs explizit oder implizit verwendet wird, die die Abfragezeichenfolge zu erstellen. Nachfolgend finden Sie ein Beispiel:

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Die Regel wird verletzt, da ein böswilliger Benutzer die ToString()-Methode überschreiben kann.

 Die Regel wird auch verletzt werden, wenn ToString implizit verwendet wird.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie eine parametrisierte Abfrage ein.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn der Befehlstext keine Benutzereingaben.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, `UnsafeQuery`, die gegen die Regel und eine Methode, `SaferQuery`, der Regel mithilfe einer parametrisierten Befehlszeichenfolge entspricht.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>Siehe auch
 [Übersicht über die Sicherheit](http://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)



