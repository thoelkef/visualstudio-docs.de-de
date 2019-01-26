---
title: Laufzeittextgenerierung mithilfe von T4-Textvorlagen
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 7f2cabab7db65b9289a928c95c3cbe73fa0d97d9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961740"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Laufzeittextgenerierung mithilfe von T4-Textvorlagen

Sie können Zeichenfolgen, die in Ihrer Anwendung zur Laufzeit mithilfe von Visual Studio-Laufzeit-Textvorlagen generieren. Der Computer, in dem die Anwendung ausgeführt wird, keine Visual Studio sein. Runtime-Vorlagen werden manchmal als "vorverarbeitete Textvorlagen" bezeichnet, weil zum Zeitpunkt der Kompilierung die Vorlage Code generiert, die zur Laufzeit ausgeführt wird.

Jede Vorlage ist eine Mischung des Texts, wie er in das generierte Zeichenfolge, und die Fragmente des Programmcodes angezeigt wird. Die Programmfragmente Geben Sie Werte für die Variablen Teile der Zeichenfolge ein, und auch steuern, bedingte und wiederholte Teile.

Beispielsweise könnte die folgende Vorlage in einer Anwendung verwendet werden, die einen HTML-Bericht erstellt.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

Beachten Sie, dass die Vorlage eine HTML-Seite ist in der die Variablenteile durch Programmcode ersetzt wurden. Sie können zunächst, dass den Entwurf einer solchen Seite schreiben einen statischen Prototyp der HTML-Seite. Sie können die in der Tabelle und anderen Variablen Teile klicken Sie dann mit Programmcode ersetzen, die den Inhalt, der variiert Variablenteile generiert, zur nächsten.

Mithilfe einer Vorlage in Ihrer Anwendung nutzt, ist es einfacher, das endgültige Format der Ausgabe angezeigt, als Sie beispielsweise eine lange Reihe von Write-Anweisungen in könnten. Vornehmen von Änderungen an der Form der Ausgabe ist einfacher und zuverlässiger.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Erstellen in jeder Anwendung eine Laufzeit-Textvorlage

### <a name="to-create-a-run-time-text-template"></a>Zum Erstellen einer Laufzeit-Textvorlage

1. Wählen Sie im Projektmappen-Explorer im Kontextmenü des Projekts **hinzufügen** > **neues Element**.

2. In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Runtimetextvorlage**. (Suchen Sie in Visual Basic unter **gemeinsame Elemente** > **allgemeine**.)

3. Geben Sie einen Namen für die Vorlagendatei an.

    > [!NOTE]
    > Der Name der Vorlagendatei wird als Klassenname im generierten Code verwendet werden. Aus diesem Grund sollten sie Leerzeichen oder Interpunktionszeichen keine.

4. Wählen Sie **Hinzufügen** aus.

    Eine neue Datei wird erstellt, mit der Erweiterung **TT**. Die **benutzerdefiniertes Tool** -Eigenschaftensatz auf **TextTemplatingFilePreprocessor**. Es enthält die folgenden Zeilen:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Konvertieren einer vorhandenen Datei in einer Laufzeitvorlage

Eine gute Möglichkeit zum Erstellen einer Vorlage wird eine vorhandene Beispiel für die Ausgabe zu konvertieren. Wenn Ihre Anwendung HTML-Dateien generiert werden, können Sie z. B. durch Erstellen einer einfachen HTML-Datei starten. Stellen Sie sicher, dass sie ordnungsgemäß funktioniert und dass seine Darstellung richtig ist. Anschließend fügen Sie es in Visual Studio-Projekt, und konvertieren Sie es in eine Vorlage.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Um eine vorhandene Textdatei in eine Laufzeitvorlage zu konvertieren.

1. Schließen Sie die Datei in Visual Studio-Projekt. Wählen Sie im Projektmappen-Explorer im Kontextmenü des Projekts **hinzufügen** > **vorhandenes Element**.

2. Legen Sie die Datei **benutzerdefinierte Tools** Eigenschaft **TextTemplatingFilePreprocessor**. Wählen Sie im Projektmappen-Explorer im Kontextmenü der Datei **Eigenschaften**.

    > [!NOTE]
    > Wenn die Eigenschaft bereits festgelegt ist, stellen Sie sicher, dass er ist **TextTemplatingFilePreprocessor** und nicht **TextTemplatingFileGenerator**. Dies kann auftreten, wenn Sie eine Datei einschließen, die die Erweiterung bereits **TT**.

3. Ändern Sie die Dateinamenerweiterung zu **TT**. Obwohl dieser Schritt optional ist, können Sie vermeiden Sie die Datei in einem falschen Editor öffnen.

4. Entfernen Sie alle Leerzeichen oder Satzzeichen, aus dem Hauptteil des Dateinamens. Z. B. "Meine Web Page.tt" wird nicht korrekt, aber "MyWebPage.tt" korrekt ist. Der Dateiname wird als Klassenname im generierten Code verwendet werden.

5. Fügen Sie die folgende Zeile am Anfang der Datei. Wenn Sie in Visual Basic-Projekt arbeiten, ersetzen Sie "C#", mit "VB".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Der Inhalt der Vorlage zur Laufzeit

### <a name="template-directive"></a>Template-Direktive

Behalten Sie die erste Zeile der Vorlage, wie Sie die Datei erstellt wurde:

`<#@ template language="C#" #>`

Der Language-Parameter hängen von der Sprache des Projekts ab.

### <a name="plain-content"></a>Einfacher Inhalt

Bearbeiten der **TT** Datei, die Text enthalten, der Sie Ihre Anwendung generieren soll. Zum Beispiel:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Eingebettete Programmcode

Sie können Programmcode zwischen einfügen `<#` und `#>`. Zum Beispiel:

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

Beachten Sie, dass Anweisungen, zwischen eingefügt werden `<# ... #>` und Ausdrücke werden eingefügt, zwischen `<#= ... #>`. Weitere Informationen finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Verwenden der Vorlage

### <a name="the-code-built-from-the-template"></a>Der Code erstellt aus der Vorlage

Beim Speichern der **TT** -Datei, einem Tochterunternehmen **cs** oder **vb** -Datei generiert wird. Um diese Datei finden Sie unter **Projektmappen-Explorer**, erweitern Sie die **TT** Dateiknoten. In Visual Basic-Projekt, und wählen Sie zuerst **alle Dateien anzeigen** in die **Projektmappen-Explorer** Symbolleiste.

Beachten Sie, dass die untergeordnete Datei enthält eine partielle Klasse, die eine Methode namens enthält `TransformText()`. Sie können diese Methode von Ihrer Anwendung aufrufen.

### <a name="generating-text-at-run-time"></a>Generieren von Text zur Laufzeit

In Ihrem Anwendungscode verwenden können Sie den Inhalt der Vorlage über einen Aufruf wie folgt generieren:

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

Um in einem bestimmten Namespace die generierte Klasse zu platzieren, legen Sie die **Custom Tool Namespace** Eigenschaft von der Textvorlagendatei.

### <a name="debugging-runtime-text-templates"></a>Debuggen von Laufzeit-Textvorlagen

Debuggen Sie und Testen Sie die Laufzeit-Textvorlagen in die gleiche Weise wie normale Code.

Sie können einen Haltepunkt in einer Textvorlage festlegen. Wenn Sie die Anwendung im Debugmodus in Visual Studio starten, können Sie den Code schrittweise durchgehen und Watch-Ausdrücke auswerten, auf die übliche Weise.

### <a name="passing-parameters-in-the-constructor"></a>Übergeben von Parametern im Konstruktor

In der Regel muss eine Vorlage einige Daten aus anderen Teilen der Anwendung importieren. Um dies zu vereinfachen, ist der Code, der von der Vorlage erstellt eine partielle Klasse. Sie können einen anderen Teil der gleichen Klasse in einer anderen Datei in Ihrem Projekt erstellen. Diese Datei kann einen Konstruktor mit Parametern, Eigenschaften und Funktionen, die den Code, der in der Vorlage eingebettet ist, und die übrigen Teile der Anwendung zugegriffen werden können, enthalten.

Beispielsweise könnten Sie eine separate Datei erstellen **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

In Ihre Vorlagendatei **MyWebPage.tt**, könnten Sie schreiben:

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

Diese Vorlage in der Anwendung verwenden zu können:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Parameter des Konstruktors in Visual Basic

In Visual Basic die separate Datei **MyWebPageCode.vb** enthält:

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

Die Vorlagendatei kann Folgendes enthalten:

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

Die Vorlage kann durch Übergeben des Parameters im Konstruktor aufgerufen:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Übergeben von Daten in den Eigenschaften der Vorlage

Eine alternative Möglichkeit übergeben von Daten an die Vorlage wird der Vorlagenklasse in eine partielle Klassendefinition öffentliche Eigenschaften hinzugefügt. Die Anwendung kann die Eigenschaften festlegen, vor dem Aufrufen `TransformText()`.

Sie können Felder auch der Vorlagenklasse in eine partielle Definition hinzufügen. Dadurch können Sie Daten zwischen aufeinander folgenden Ausführungen der Vorlage zu übergeben.

### <a name="use-partial-classes-for-code"></a>Verwenden Sie partielle Klassen für code

Viele Entwickler ziehen es vor, um zu vermeiden, umfangreiche Codetexte in Vorlagen zu schreiben. Stattdessen können Sie Methoden in einer partiellen Klasse definieren, die den gleichen Namen wie die Datei der Vorlage hat. Rufen Sie diese Methoden aus der Vorlage ein. Auf diese Weise wird die Vorlage zeigt weitere deutlich die Zielausgabezeichenfolge ähneln. Diskussionen über die Darstellung des Ergebnisses können getrennt werden, von der Logik zum Erstellen der Daten, die angezeigt wird.

### <a name="assemblies-and-references"></a>Assemblys und Verweise

Ggf. Vorlagencode auf eine .NET oder andere Assembly verweisen, wie z. B. **System.Xml.dll**, Hinzufügen des Projekts **Verweise** auf die übliche Weise.

Sollten Sie einen Namespace zu importieren, auf die gleiche Weise wie eine `using` -Anweisung, hierzu können Sie mit der `import` Richtlinie:

```
<#@ import namespace="System.Xml" #>
```

Diese Direktiven müssen am Anfang der Datei eingefügt werden, sofort nach der `<#@template` Richtlinie.

### <a name="shared-content"></a>Freigegebene Inhalte

Wenn Sie Text, die mehrere Vorlagen gemeinsam verwendet wird verwenden, können Sie ihn in einer separaten Datei platzieren und fügen Sie es in jeder Datei, die in der sie angezeigt werden soll:

```
<#@include file="CommonHeader.txt" #>
```

Der eingeschlossene Inhalt kann einer beliebigen Kombination von Programmcode und nur-Text enthalten, und andere include-Direktiven und andere Anweisungen.

Der Include-Anweisung kann eine beliebige Stelle im Text einer Vorlagendatei oder einer eingeschlossenen Datei verwendet werden.

### <a name="inheritance-between-run-time-text-templates"></a>Vererbung zwischen Laufzeit-Textvorlagen

Sie können Freigeben von Inhalten zwischen Laufzeitvorlagen durch Schreiben einer Textvorlage Basisklasse, die kann abstrakt sein. Verwenden der `inherits` Parameter, der die `<@#template#>` Richtlinie auf eine andere Runtime-Vorlagenklasse.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Vererbungsmuster: Fragmente in Basismethoden

Beachten Sie, dass im Muster, die in das folgende Beispiel verwendet die folgenden Punkte:

- Die Basisklasse `SharedFragments` definiert die Methoden in Klassenfunktionsblöcken `<#+ ... #>`.

- Die Basisklasse enthält keinen freien Text. Stattdessen auftreten aller Textblöcke innerhalb der Methoden der Klasse-Funktion.

- Die abgeleitete Klasse wird aufgerufen, die in definierten Methoden `SharedFragments`.

- Ruft die Anwendung die `TextTransform()` -Methode der abgeleiteten Klasse, aber nicht die Basisklasse umgewandelt wird `SharedFragments`.

- Die Basisklassen und abgeleiteten Klassen sind die Laufzeit-Textvorlagen. d. h. die **benutzerdefiniertes Tool** -Eigenschaftensatz auf **TextTemplatingFilePreprocessor**.

**SharedFragments.tt:**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram.cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Die resultierende Ausgabe:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Vererbungsmuster: Text im Basis-Text

Bei dieser Alternativen Vorgehensweise zum Verwenden von vorlagenvererbung ist der größte Teil des Texts in dieser Vorlage definiert. Die abgeleiteten Vorlagen enthalten Daten und Textfragmente, in die grundlegenden Inhalte.

**AbstractBaseTemplate1.tt:**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt:**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**Code der Anwendung:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Ausgabe:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>Verwandte Themen

Während der Entwurfszeit-Vorlagen: Wenn Sie eine Vorlage, die zum Generieren von Code verwenden möchten, die Teil Ihrer Anwendung, finden Sie unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Laufzeit-Vorlagen können in jeder Anwendung verwendet werden, in denen die Vorlagen und deren Inhalt zur Kompilierzeit bestimmt. Aber wenn Sie Visual Studio-Erweiterung schreiben, die Text aus Vorlagen generiert wird, die zur Laufzeit ändern möchten, finden Sie unter [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Siehe auch

- [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md)
- [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)
- [T4-Toolbox](http://olegsych.com/T4Toolbox/)
