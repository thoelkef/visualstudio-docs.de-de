---
title: 'CA3005: Review code for LDAP injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von LDAP-Befehlen)'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 38c28153fa513c4f4db5b3a7833d279674f66734
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541297"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005: Review code for LDAP injection vulnerabilities (Überprüfen von Code auf Sicherheitsrisiken durch Einschleusung von LDAP-Befehlen)

|||
|-|-|
|TypeName|ReviewCodeForLdapInjectionVulnerabilities|
|CheckId|CA3005|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige Eingabe der HTTP-Anforderung erreicht eine LDAP-Anweisung.

## <a name="rule-description"></a>Regelbeschreibung

Achten Sie darauf von Lightweight Directory Access Protocol (LDAP)-Injection-Angriffen, bei der Arbeit mit nicht vertrauenswürdigen Eingaben. Angreifer kann potenziell schädliche LDAP-Anweisungen für Informationsverzeichnisse ausführen. Anwendungen, die eine Benutzereingabe zu verwenden, zum Erstellen von dynamischer LDAP-Anweisungen für den Zugriff auf Verzeichnisdienste sind besonders anfällig.

Mit dieser Regel versucht, beim Suchen der Eingabespalte aus HTTP-Anforderungen, die eine LDAP-Anweisung erreicht.

> [!NOTE]
> Mit dieser Regel kann nicht zum Nachverfolgen von Daten in Assemblys führen. Wenn eine Assembly die Eingabe der HTTP-Anforderung liest und leitet diese dann an eine andere Assembly, die eine LDAP-Anweisung ausgeführt wird, wird nicht mit dieser Regel beispielsweise eine Warnung generiert.

> [!NOTE]
> Es gibt ein konfigurierbares Limit wie deep mit dieser Regel Datenfluss Methodenaufrufe analysieren wird. Finden Sie unter [Analysekonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) zum Konfigurieren des Grenzwerts in `.editorconfig` Dateien.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Erwägen Sie für den vom Benutzer gesteuerte Teil LDAP-Anweisungen eine der:
- Zulassen von nur einer sicheren Liste von nicht-Sonderzeichen.
- Verbieten Sie Sonderzeichen
- Versehen Sie Sonderzeichen mit Escapezeichen.

Finden Sie unter [OWASPs LDAP-Injection Spickzettel](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md) Weitere Anleitungen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Wenn Sie wissen, wurde die Eingabe überprüft oder mit Escapezeichen versehen, um sicherzugehen, kann ich diese Warnung unterdrücken.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;
using System.DirectoryServices;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userName = Request.Params["user"];
        string filter = "(uid=" + userName + ")";  // searching for the user entry 

        // In this example, if we send the * character in the user parameter which will
        // result in the filter variable in the code to be initialized with (uid=*). 
        // The resulting LDAP statement will make the server return any object that 
        // contains a uid attribute.
        DirectorySearcher searcher = new DirectorySearcher(filter);
        SearchResultCollection results = searcher.FindAll();

        // Iterate through each SearchResult in the SearchResultCollection.
        foreach (SearchResult searchResult in results)
        {
            // ...
        }
    }
}
```

```vb
Imports System
Imports System.DirectoryServices

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(send As Object, e As EventArgs)
        Dim userName As String = Me.Request.Params(""user"")
        Dim filter As String = ""(uid="" + userName + "")""    ' searching for the user entry

        ' In this example, if we send the * character in the user parameter which will
        ' result in the filter variable in the code to be initialized with (uid=*). 
        ' The resulting LDAP statement will make the server return any object that 
        ' contains a uid attribute.
        Dim searcher As DirectorySearcher = new DirectorySearcher(filter)
        Dim results As SearchResultCollection = searcher.FindAll()

        ' Iterate through each SearchResult in the SearchResultCollection.
        For Each searchResult As SearchResult in results
            ' ...
        Next searchResult
    End Sub
End Class
```
