---
title: Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8422b32398c99f33575bb03923e1025207e5956e
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476704"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen

Während der Entwurfszeit T4-Textvorlagen können Programmcode und andere Dateien in Ihrem Visual Studio-Projekt zu generieren. In der Regel schreiben Sie die Vorlagen, damit sie den Code variieren, die sie gemäß den Daten aus generieren eine *Modell*. Ein Modell ist eine Datei oder Datenbank, die wichtige Informationen zu den Anforderungen Ihrer Anwendung enthält.

In einem Modell kann z. B. ein Workflow entweder als Tabelle oder Diagramm definiert sein. Anhand des Modells können Sie die Software generieren, die den Workflow ausführt. Wenn die Anforderungen Ihrer Benutzer ändern, ist es einfach den neuen Workflow mit den Benutzern besprochen werden. Die erneute Generierung des Codes anhand des Workflows ist zuverlässiger als die manuelle Aktualisierung des Codes.

> [!NOTE]
> Ein *Modell* ist eine Datenquelle, die einen bestimmten Aspekt einer Anwendung beschreibt. Ein Modell kann ein beliebiges Format in einem beliebigen Datei- oder Datenbanktyp aufweisen. Es muss kein bestimmtes Format besitzen, wie z. B. ein UML-Modell oder ein domänenspezifisches Sprachmodell. Typische Modelle werden als Tabellen oder XML-Dateien dargestellt.

Sie sind wahrscheinlich bereits mit der Codegenerierung vertraut. Beim Definieren von Ressourcen in einem **resx** -Datei in Visual Studio-Projektmappe, ein Satz von Klassen und Methoden wird automatisch generiert. Durch die Ressourcendatei können die Ressourcen einfacher und zuverlässiger bearbeitet werden als dies beim Bearbeiten der Klassen und Methoden möglich wäre. Mithilfe von Textvorlagen können Sie Code auf die gleiche Weise aus einer selbst entworfenen Quelle generieren.

Eine Textvorlage enthält eine Mischung des Texts, den Sie generieren möchten, sowie Programmcode, der Variablenteile des Texts generiert. Der Programmcode können Sie wiederholen oder das bedingte Auslassen von Teilen des generierten Texts. Der generierte Text selbst kann Programmcode sein, der einen Teil der Anwendung bildet.

## <a name="create-a-design-time-t4-text-template"></a>Erstellen Sie eine Entwurfszeit-T4-Textvorlage

1. Erstellen Sie ein neues Visual Studio-Projekt, oder öffnen Sie eine vorhandene Ressourcengruppe.

2. Ihr Projekt eine Textvorlagendatei hinzu, und geben sie einen Namen mit der Erweiterung **TT**.

    Klicken Sie hierzu in **Projektmappen-Explorer**, wählen Sie im Kontextmenü des Projekts **hinzufügen** > **neues Element**. In der **neues Element hinzufügen** aktivieren Sie im Dialogfeld **Textvorlage** im mittleren Bereich.

    Beachten Sie, dass die **benutzerdefiniertes Tool** -Eigenschaft der Datei ist **TextTemplatingFileGenerator**.

3. Öffnen Sie die Datei. Sie enthält bereits die folgenden Anweisungen:

   ```
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   ```

    Wenn Sie die Vorlage einem [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Projekt hinzugefügt haben, ist das Sprachattribut auf `VB` festgelegt.

4. Fügen Sie am Ende der Datei Text hinzu. Zum Beispiel:

   ```
   Hello, world!
   ```

5. Speichern Sie die Datei.

    Sie sehen möglicherweise eine **Sicherheitswarnung** Meldungsfeld mit der Frage zu bestätigen, dass die Vorlage ausgeführt werden soll. Klicken Sie auf **OK**.

6. In **Projektmappen-Explorer**, erweitern Sie den Vorlagendateiknoten und sehen Sie eine Datei mit der Erweiterung **.txt**. Die Datei enthält den Text, der von der Vorlage generiert wird.

   > [!NOTE]
   > Ist Ihr Projekt eine Visual Basic-Projekt ist, klicken Sie auf **alle Dateien anzeigen** um die Ausgabedatei anzuzeigen.

### <a name="regenerate-the-code"></a>Erneutes Generieren des Codes

In den folgenden Fällen wird eine Vorlage ausgeführt, wobei die untergeordnete Datei generiert wird:

- Bearbeiten Sie die Vorlage aus, und klicken Sie dann den Fokus auf ein anderes Visual Studio-Fenster.

- Sie speichern die Vorlage.

- Klicken Sie auf **alle Vorlagen transformieren** in die **erstellen** Menü. Dadurch werden alle Vorlagen in Visual Studio-Projektmappe transformieren.

- In **Projektmappen-Explorer**, im Kontextmenü der Datei, wählen Sie **benutzerdefiniertes Tool ausführen**. Verwenden Sie diese Methode, um eine ausgewählte Untergruppe von Vorlagen zu transformieren.

Sie können auch ein Visual Studio-Projekt festlegen, damit die Vorlagen ausgeführt werden, wenn sich die Datendateien, die sie lesen geändert haben. Weitere Informationen finden Sie unter [automatisches erneutes Generieren des Codes](#Regenerating).

## <a name="generate-variable-text"></a>Generieren von Variablentext

Textvorlagen ermöglichen es Ihnen, den Inhalt der generierten Datei mithilfe von Programmcode zu verändern.

1. Ändern des Inhalts der `.tt`-Datei:

   ```csharp
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   <#int top = 10;

   for (int i = 0; i<=top; i++)
   { #>
      The square of <#= i #> is <#= i*i #>
   <# } #>
   ```

   ```vb
   <#@ template hostspecific="false" language="VB" #>
   <#@ output extension=".txt" #>
   <#Dim top As Integer = 10

   For i As Integer = 0 To top
   #>
       The square of <#= i #> is <#= i*i #>
   <#
   Next
   #>
   ```

2. Speichern Sie die TT-Datei, und überprüfen Sie die generierte TXT-Datei erneut. Sie enthält die Quadratzahlen der Zahlen 0 bis 10.

   Beachten Sie, dass Anweisungen in `<#...#>` eingeschlossen sind und einzelne Ausdrücke in `<#=...#>`. Weitere Informationen finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).

   Wenn Sie den generierenden Code in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] schreiben, sollte die `template`-Direktive `language="VB"` enthalten. `"C#"` Der Standardwert ist.

## <a name="debugging-a-design-time-t4-text-template"></a>Debuggen einer T4-Textvorlage für die Entwurfszeit

So debuggen Sie eine Textvorlage

- Fügen Sie `debug="true"` in die `template`-Anweisung ein. Zum Beispiel:

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- Legen Sie in der Vorlage Haltepunkte auf dieselbe Weise fest wie für normalen Code.

- Wählen Sie **T4-Vorlage Debuggen** aus dem Kontextmenü der Textvorlagendatei im Projektmappen-Explorer.

   Die Vorlage ausgeführt wird und an den Haltepunkten hält. Sie können Variablen prüfen und den Code ganz normal durchlaufen.

> [!TIP]
> Mit `debug="true"` wird die Zuordnung des generierten Codes zur Textvorlage genauer, indem mehr Direktiven zur Zeilennummerierungsdirektive in den generierten Code eingefügt werden. Wenn Sie diese auslassen, wird die Ausführung möglicherweise durch die Haltepunkte im falschen Zustand angehalten.
>
> Sie können jedoch die Klausel in der template-Anweisung lassen, auch wenn Sie nicht debuggen. Dies verursacht nur einen sehr geringen Leistungsverlust.

## <a name="generating-code-or-resources-for-your-solution"></a>Generieren von Code oder Ressourcen für die Projektmappe

Abhängig vom Modell können verschiedene Programmdateien generiert werden. Ein Modell ist eine Eingabequelle wie eine Datenbank, eine Konfigurationsdatei, ein UML- oder DSL-Modell oder eine andere Quelle. Sie werden in der Regel mehrere Programmdateien aus dem gleichen Modell generieren. Sie erstellen zu diesem Zweck eine Vorlagendatei für jede generierte Programmdatei und lassen das gleiche Modell von allen Vorlagen lesen.

### <a name="to-generate-program-code-or-resources"></a>So generieren Sie Programmcode oder Ressourcen

1. Ändern Sie die output-Direktive, um eine Datei des entsprechenden Typs zu generieren, z. B. .cs, .vb, .resx oder .xml.

2. Fügen Sie Code ein, durch den der benötigte Projektmappencode generiert wird. Fügen Sie z. B. folgenden Code ein, wenn Sie drei Deklarationen für Felder für ganze Zahlen in einer Klasse generieren möchten:

    ```csharp

    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    <# var properties = new string [] {"P1", "P2", "P3"}; #>
    // This is generated code:
    class MyGeneratedClass {
    <# // This code runs in the text template:
      foreach (string propertyName in properties)  { #>
      // Generated code:
      private int <#= propertyName #> = 0;
    <# } #>
    }
    ```

    ```vb
    <#@ template debug="false" hostspecific="false" language="VB" #>
    <#@ output extension=".cs" #>
    <# Dim properties = {"P1", "P2", "P3"} #>
    class MyGeneratedClass {
    <#
       For Each propertyName As String In properties
    #>
      private int <#= propertyName #> = 0;
    <#
       Next
    #>
    }

    ```

3. Speichern Sie die Datei, und überprüfen Sie die generierte Datei, die nun den folgenden Code enthält:

    ```csharp
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Generieren von Code und generierter Text

Wenn Sie Programmcode generieren, ist es wichtig, den Generierungscode, der in der Vorlage ausgeführt wird, nicht mit dem resultierenden generierten Code zu verwechseln, der Teil der Projektmappe wird. Die beiden Sprachen müssen nicht identisch sein.

Das vorherige Beispiel enthält zwei Versionen. In einer Version liegt der generierende Code in C# vor. In der anderen Version liegt der generierende Code in Visual Basic vor. Der in beiden Versionen generierte Text ist jedoch identisch, und er befindet sich in einer C#-Klasse.

Ebenso können Sie eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Vorlage verwenden, um Code in einer beliebigen Sprache zu generieren. Der generierte Text muss nicht in einer bestimmten Sprache vorliegen, und es muss sich nicht um Programmcode handeln.

### <a name="structuring-text-templates"></a>Strukturieren von Textvorlagen

Es wird empfohlen, den Vorlagencode in zwei Teile aufzuteilen:

- Ein Konfigurations- oder Datensammlungsteil, der Werte in Variablen festlegt, jedoch keine Textblöcke enthält. Im vorherigen Beispiel ist dieser Teil die Initialisierung von `properties`.

   Dies wird manchmal als Modellabschnitt bezeichnet, da ein speicherinternes Modell erstellt und normalerweise eine Modelldatei gelesen wird.

- Der Textgenerierungsteil (im vorliegenden Beispiel `foreach(...){...}`), in dem die Werte der Variablen verwendet werden.

   Dies ist keine notwendige Trennung, doch auf diese Weise wird das Lesen der Vorlage wegen der geringeren Komplexität des Teils, der Text enthält, vereinfacht.

## <a name="reading-files-or-other-sources"></a>Lesen von Dateien oder anderen Quellen

Im Vorlagencode können Assemblys wie System.XML verwendet werden, um auf eine Modelldatei oder eine Datenbank zuzugreifen. Um Zugriff auf diese Assemblys zu erhalten, müssen Sie wie hier dargestellt Anweisungen einfügen:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

Die `assembly` -Direktive macht die angegebene Assembly in die gleiche Weise wie der Abschnitt "Referenzen" der Visual Studio-Projekt für den Vorlagencode verfügbar. Sie müssen keinen Verweis auf "System.dll" einschließen, da automatisch darauf verwiesen wird. Die `import`-Anweisung ermöglicht wie die `using`-Anweisung in einer normalen Programmdatei die Verwendung von Typen ohne ihre vollqualifizierten Namen.

Beispielsweise nach dem Importieren von **System.IO**, könnten Sie schreiben:

```csharp

<# var properties = File.ReadLines("C:\\propertyList.txt");#>
...
<# foreach (string propertyName in properties) { #>
...
```

```vb
<# For Each propertyName As String In
             File.ReadLines("C:\\propertyList.txt")
#>
```

### <a name="opening-a-file-with-a-relative-pathname"></a>Öffnen einer Datei mit einem relativen Pfadnamen

Verwenden Sie `this.Host.ResolvePath()`, um eine Datei aus einem Ort zu laden, der relativ zur Textvorlage ist. Zur Verwendung von this.Host muss `hostspecific="true"` in `template` festgelegt werden:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
```

Anschließend können Sie z. B. Folgendes schreiben:

```csharp
<# string fileName = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...
```

```vb
<# Dim fileName = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>
```

Sie können auch `this.Host.TemplateFile` verwenden, was den Namen der aktuellen Vorlagendatei darstellt.

Der Typ von `this.Host` (in VB `Me.Host`) ist `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`.

### <a name="getting-data-from-visual-studio"></a>Abrufen von Daten aus Visual Studio

Um Dienste, die in Visual Studio verwenden, legen die `hostSpecific` -Attribut, und laden die `EnvDTE` Assembly. Import `Microsoft.VisualStudio.TextTemplating`, enthält die `GetCOMService()` -Erweiterungsmethode.  Sie können dann IServiceProvider.GetCOMService() verwenden, um auf DTE und andere Dienste zuzugreifen. Zum Beispiel:

```src
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

> [!TIP]
> Eine Textvorlage wird in ihrer eigene App-Domäne ausgeführt, und der Zugriff auf Dienste erfolgt durch Marshalling. Unter diesen Umständen ist GetCOMService() zuverlässiger als GetService().

## <a name="Regenerating"></a> Automatisches Erneutes Generieren des Codes

In der Regel werden mehrere Dateien in Visual Studio-Projektmappe mit einem Eingabemodell generiert. Jede Datei wird aus einer eigenen Vorlage generiert, die Vorlagen verweisen jedoch alle auf das gleiche Modell.

Wenn sich das Quellmodell ändert, müssen Sie alle Vorlagen in der Projektmappe erneut ausführen. Wählen Sie dazu manuell **alle Vorlagen transformieren** auf die **erstellen** Menü.

Wenn Sie das Visual Studio-Modellierungs-SDK installiert haben, haben Sie alle Vorlagen, die bei jeder Buildausführung automatisch transformiert. Bearbeiten Sie dazu die Projektdatei (.csproj oder .vbproj) in einem Text-Editor, und fügen Sie in der Nähe des Endes der Datei nach allen anderen `<import>`-Anweisungen die folgenden Zeilen hinzu:

> [!NOTE]
> Das Text-Vorlage Transformation SDK und das Visual Studio-Modellierungs-SDK werden automatisch installiert, wenn Sie bestimmte Funktionen von Visual Studio zu installieren. Weitere Informationen finden Sie unter [in diesem Blogbeitrag](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

Weitere Informationen finden Sie unter [Codegenerierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md).

## <a name="error-reporting"></a>Fehlerberichte

Um Fehler- und Warnmeldungen im Fehlerfenster von Visual Studio zu platzieren, können Sie diese Methoden verwenden:

```
Error("An error message");
Warning("A warning message");
```

## <a name="Converting"></a> Konvertieren einer vorhandenen Datei zu einer Vorlage

Eine hilfreiche Funktion von Vorlagen ist, dass sie den generierten Dateien sehr ähneln und zudem einigen eingefügten Programmcode enthalten. Dadurch ergibt sich eine einfache Methode zum Erstellen einer Vorlage. Erstellen Sie zunächst eine normale Datei als Prototyp, z. B. eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Datei, und klicken Sie dann Generierungscode, der die resultierende Datei verändert.

### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>So konvertieren Sie eine vorhandene Datei in eine Entwurfszeitvorlage

1. Fügen Sie zum Visual Studio-Projekt, eine Datei des Typs, die Sie generieren, wie z. B. möchten eine `.cs`, `.vb`, oder `.resx` Datei.

2. Testen Sie die neue Datei, um sicherzustellen, dass sie ordnungsgemäß funktioniert.

3. Ändern Sie im Projektmappen-Explorer die Dateierweiterung, **TT**.

4. Überprüfen Sie die folgenden Eigenschaften der **TT** Datei:

   | | |
   |-|-|
   | **Benutzerdefiniertes Tool =** | **TextTemplatingFileGenerator** |
   | **Buildvorgang =** | **Keine** |

5. Fügen Sie am Anfang der Datei die folgenden Zeilen ein:

   ```
   <#@ template debug="false" hostspecific="false" language="C#" #>
   <#@ output extension=".cs" #>
   ```

    Wenn Sie den Generierungscode der Vorlage in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] schreiben möchten, legen Sie das `language`-Attribut anstelle von `"VB"` auf `"C#"` fest.

    Legen Sie das `extension`-Attribut auf die Dateinamenerweiterung für den zu generierenden Dateityp fest, z. B. `.cs`, `.resx` oder `.xml`.

6. Speichern Sie die Datei.

    Eine untergeordnete Datei mit der angegebenen Erweiterung wird erstellt. Die Eigenschaften entsprechen dem Dateityp. Z. B. die **Buildvorgang** Eigenschaft einer CS-Datei wäre **Kompilieren**.

    Vergewissern Sie sich, dass die generierte Datei den gleichen Inhalt enthält wie die ursprüngliche Datei.

7. Identifizieren Sie einen Teil der Datei, den Sie ändern möchten. Beispielsweise einen Teil, der nur unter bestimmten Bedingungen angezeigt oder wiederholt wird oder in dem sich bestimmte Werte ändern. Fügen Sie Generierungscode ein. Speichern Sie die Datei, und überprüfen Sie, ob die untergeordnete Datei ordnungsgemäß generiert wurde. Wiederholen Sie diesen Schritt.

## <a name="guidelines-for-code-generation"></a>Richtlinien für die Codegenerierung

Informieren Sie sich [Richtlinien für das Verfassen von T4-Textvorlagen](../modeling/guidelines-for-writing-t4-text-templates.md).

## <a name="next-steps"></a>Nächste Schritte

|Nächster Schritt|Thema|
|-|-|
|Schreiben und debuggen Sie eine erweiterte Textvorlage mit Code, in dem zusätzliche Funktionen, eingeschlossene Dateien und externe Daten verwendet werden.|[Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)|
|Generieren Sie zur Laufzeit Dokumente aus Vorlagen.|[Laufzeittextgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Führen Sie die textgenerierung außerhalb von Visual Studio.|[Generieren von Dateien mit dem Hilfsprogramm "TextTransform"](../modeling/generating-files-with-the-texttransform-utility.md)|
|Transformieren Sie die Daten in das Format einer domänenspezifischen Sprache.|[Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)|
|Schreiben Sie Direktivenprozessoren, um eigene Datenquellen zu transformieren.|[Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>Siehe auch

- [Richtlinien für das Verfassen von T4-Textvorlagen](../modeling/guidelines-for-writing-t4-text-templates.md)
