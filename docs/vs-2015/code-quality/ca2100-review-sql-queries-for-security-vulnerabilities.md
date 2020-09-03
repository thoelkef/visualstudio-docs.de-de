---
title: 'CA2100: Überprüfen von SQL-Abfragen auf Sicherheitsrisiken | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 797c071cdc74c36afeece304bfa4c708d7bf7147
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521211"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: SQL-Abfragen auf Sicherheitsrisiken überprüfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode legt die- <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> Eigenschaft mithilfe einer Zeichenfolge fest, die aus einem Zeichen folgen Argument für die-Methode erstellt wird.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel setzt voraus, dass das Zeichenfolgenargument Benutzereingaben enthält. Eine aus Benutzereingaben erstellte SQL-Befehlszeichenfolge ist anfällig für SQL-Injection-Angriffe. Bei einem SQL-Injection-Angriff liefert ein böswilliger Benutzereingaben, die den Entwurf einer Abfrage verändern, wenn versucht wird, den Zugriff auf die zugrunde liegende Datenbank zu beschädigen oder nicht autorisierten Zugriff zu erhalten. Typische Techniken sind die Einschleusung eines einfachen Anführungs Zeichens oder Apostroph, bei dem es sich um das SQL-literalzeichentrennzeichen handelt. zwei Bindestriche, die einen SQL-Kommentar bedeuten. und ein Semikolon, das angibt, dass ein neuer Befehl folgt. Wenn Benutzereingaben Teil der Abfrage sein müssen, verwenden Sie eine der folgenden (in der Reihenfolge der Effektivität aufgeführten), um das Risiko von Angriffen zu verringern.

- Gespeicherte Prozedur verwenden.

- Verwenden Sie eine parametrisierte Befehls Zeichenfolge.

- Überprüfen Sie die Benutzereingaben für Typ und Inhalt, bevor Sie die Befehls Zeichenfolge erstellen.

  Die folgenden [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Typen implementieren die- <xref:System.Data.IDbCommand.CommandText%2A> Eigenschaft oder stellen Konstruktoren bereit, mit denen die-Eigenschaft mithilfe eines Zeichen folgen Arguments festgelegt wird.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> und <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> und <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> und <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System. Data. SqlServerCe. SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) und [System. Data. SqlServerCe. SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> und <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  Beachten Sie, dass diese Regel verletzt wird, wenn die Methode "destring" eines Typs explizit oder implizit verwendet wird, um die Abfrage Zeichenfolge zu erstellen. Im Folgenden finden Sie ein Beispiel.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Die Regel wird verletzt, weil ein böswilliger Benutzer die Methode "destring ()" überschreiben kann.

 Die Regel wird auch verletzt, wenn die Zeichenfolge implizit verwendet wird.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie eine parametrisierte Abfrage.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Befehls Text keine Benutzereingaben enthält.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, `UnsafeQuery` , die gegen die Regel verstößt, und eine Methode, `SaferQuery` , die die Regel mithilfe einer parametrisierten Befehls Zeichenfolge erfüllt.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>Weitere Informationen
 [Sicherheitsübersicht](https://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)
