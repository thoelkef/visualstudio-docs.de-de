---
title: 'CA2100: SQL-Abfragen auf Sicherheitsrisiken überprüfen'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 888e80174f34b82c25bc98b8745ae8608322c70c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: SQL-Abfragen auf Sicherheitsrisiken überprüfen
|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode legt die <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> Eigenschaft mithilfe einer Zeichenfolge, die aus einem Zeichenfolgenargument für die Methode erstellt wird.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel setzt voraus, dass das Zeichenfolgenargument Benutzereingaben enthält. Eine aus Benutzereingaben erstellte SQL-Befehlszeichenfolge ist anfällig für SQL-Injection-Angriffe. In einer SQL-Injection-Angriff stellt ein böswilliger Benutzer Eingabe, die den Entwurf einer Abfrage in dem Versuch, die beschädigt oder nicht autorisierten Zugriff auf die zugrunde liegende Datenbank ändert. Typische Methoden umfassen Injection ein einfaches Anführungszeichen oder Apostroph, also der SQL-Zeichenfolgenliteral-Trennzeichen; zwei Bindestriche, bedeutet einen SQL-Kommentar; und ein Semikolon, der angibt, dass ein neuer Befehl folgt. Wenn Benutzereingaben, Teil der Abfrage, verwenden Sie eines der folgenden sein muss aufgeführt, in der Reihenfolge der Effektivität, um das Risiko von Angriffen zu verringern.

-   Verwenden Sie eine gespeicherte Prozedur.

-   Verwenden Sie eine parametrisierte Befehlszeichenfolge an.

-   Überprüfen Sie die Benutzereingaben für Datentyp und Inhalt vor dem Erstellen der Befehlszeichenfolge.

 Die folgenden [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Typen implementieren die <xref:System.Data.IDbCommand.CommandText%2A> Eigenschaft, oder geben Sie die Konstruktoren, die die Eigenschaft festgelegt wird, mit der ein Zeichenfolgenargument.

-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> und <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> und <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> und <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> und <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

 Beachten Sie, dass diese Regel verletzt wird, wenn die ToString-Methode eines Typs explizit oder implizit verwendet wird, die Abfragezeichenfolge zu erstellen. Nachfolgend finden Sie ein Beispiel:

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Die Regel wird verletzt, da ein böswilliger Benutzer die ToString()-Methode überschreiben kann.

 Die Regel wird auch verletzt, wenn ToString implizit verwendet wird.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie eine parametrisierte Abfrage ein.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn der Befehlstext keine Benutzereingaben enthält.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode `UnsafeQuery`, die die Regel und eine Methode verletzt `SaferQuery`, der Regel mithilfe einer parametrisierten Befehlszeichenfolge entspricht.

 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>Siehe auch
 [Übersicht über die Sicherheit](/dotnet/framework/data/adonet/security-overview)