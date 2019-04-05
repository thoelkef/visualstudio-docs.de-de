---
title: 'CA3003: Code nach Datei Pfad-Injection-Anfälligkeiten überprüfen'
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
ms.openlocfilehash: c20d3efb9ea84a7e8bb22288303313ef44b2b795
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018526"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003: Code nach Datei Pfad-Injection-Anfälligkeiten überprüfen

|||
|-|-|
|TypeName|ReviewCodeForFilePathInjectionVulnerabilities|
|CheckId|CA3003|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Potenziell nicht vertrauenswürdige Eingabe der HTTP-Anforderung erreicht den Pfad von Dateien.

## <a name="rule-description"></a>Regelbeschreibung

Bei der Arbeit mit nicht vertrauenswürdigen Eingaben aus webanforderungen Achten Sie darauf, dass Sie benutzergesteuerte Eingabe verwenden, wenn Sie Pfade zu Dateien angeben. Ein Angreifer kann eine beliebige Datei, lesen möglicherweise Offenlegung von sensiblen Daten führt. Oder ein Angreifer möglicherweise zum Schreiben in eine beliebige Datei, was zu nicht autorisierten Änderung von sensiblen Daten oder die Sicherheit des Servers beeinträchtigen. Ist ein gängiges Verfahren der Angreifer [Path Traversal](https://www.owasp.org/index.php/Path_Traversal) auf Dateien außerhalb des vorgesehenen Verzeichnisses zugreifen.

Mit dieser Regel versucht beim Suchen der Eingabespalte aus HTTP-Anforderungen, die einen Pfad in einem Dateivorgang zu erreichen.

> [!NOTE]
> Mit dieser Regel kann nicht zum Nachverfolgen von Daten in Assemblys führen. Wenn eine Assembly die Eingabe der HTTP-Anforderung liest und leitet diese dann an eine andere Assembly, die in eine Datei schreibt, wird nicht mit dieser Regel beispielsweise eine Warnung generiert.

> [!NOTE]
> Es gibt ein konfigurierbares Limit wie deep mit dieser Regel Datenfluss Methodenaufrufe analysieren wird. Finden Sie unter [Analysekonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) zum Konfigurieren des Grenzwerts in `.editorconfig` Dateien.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Wenn möglich, Dateipfade, die auf Grundlage der Benutzereingabe in einer explizit bekannte Sicherungsliste zu beschränken.  Lassen Sie z. B. wenn die Anwendung, die nur den Zugriff auf "red.txt", "green.txt" oder "blue.txt" benötigt wird, nur diese Werte zu.
- Überprüfen Sie bei nicht vertrauenswürdigen Dateinamen, und überprüfen Sie, dass der Name gültig ist.
- Verwenden Sie vollständigen Pfadnamen aus, wenn die Pfade angeben.
- Vermeiden Sie potenziell gefährliche Konstrukte wie Path-Umgebungsvariablen.
- Nur akzeptieren Sie lange Dateinamen zu und überprüfen Sie langen Namen zu, wenn Benutzer den Kurznamen übermittelt.
- Endbenutzer-Eingabe für gültige Zeichen zu beschränken.
- Ablehnen von Namen, in denen MAX_PATH-Länge überschritten wird.
- Behandeln Sie Dateinamen buchstäblich, ohne Sie zu interpretieren.
- Bestimmt, ob Sie den Dateinamen einer Datei oder ein Gerät darstellt.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Nachdem Sie Eingabe überprüft haben, wie im vorherigen Abschnitt beschrieben, ist es angemessen, diese Warnung unterdrücken.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userInput = Request.Params["UserInput"];
        // Assume the following directory structure:
        //   wwwroot\currentWebDirectory\user1.txt
        //   wwwroot\currentWebDirectory\user2.txt
        //   wwwroot\secret\allsecrets.txt
        // There is nothing wrong if the user inputs:
        //   user1.txt
        // However, if the user input is: 
        //   ..\secret\allsecrets.txt
        // Then an attacker can now see all the secrets.

        // Avoid this:
        using (File.Open(userInput, FileMode.Open))
        {
            // Read a file with the name supplied by user
            // Input through request's query string and display 
            // The content to the webpage. 
        }
    }
}
```

```vb
Imports System
Imports System.IO

Partial Public Class WebForm 
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim userInput As String = Me.Request.Params("UserInput")
        ' Assume the following directory structure:
        '   wwwroot\currentWebDirectory\user1.txt
        '   wwwroot\currentWebDirectory\user2.txt
        '   wwwroot\secret\allsecrets.txt
        ' There is nothing wrong if the user inputs:
        '   user1.txt
        ' However, if the user input is: 
        '   ..\secret\allsecrets.txt
        ' Then an attacker can now see all the secrets.

        ' Avoid this:
        Using File.Open(userInput, FileMode.Open)
            ' Read a file with the name supplied by user
            ' Input through request's query string and display 
            ' The content to the webpage. 
        End Using
    End Sub
End Class
```
