---
title: Writing a T4 Text Template | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
ms.assetid: 94328da7-953b-4e92-9587-648543d1f732
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcd5a4996db4a5e374baabe4f52d5fd1dbac2e5e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301118"
---
# <a name="writing-a-t4-text-template"></a>Schreiben einer T4-Textvorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Textvorlage enthält den Text, der aus ihr generiert wird. For example, a template that creates a web page will contain "\<html>…" and all the other standard parts of an HTML page. Inserted into the template are *control blocks*, which are fragments of program code. Kontrollblöcke stellen veränderliche Werte bereit und ermöglichen es, Bedingungen für Teile des Texts zu definieren und Teile des Texts zu wiederholen.

 Diese Struktur vereinfacht das Entwickeln einer Vorlage, da Sie mit einem Prototyp der generierten Datei beginnen und nach und nach Kontrollblöcke zum Verändern des Ergebnisses einfügen können.

 Textvorlagen bestehen aus den folgenden Teilen:

- **Directives** - elements that control how the template is processed.

- **Text blocks** - content that is copied directly to the output.

- **Control blocks** - program code that inserts variable values into the text, and controls conditional or repeated parts of the text.

  To try the examples in this topic, copy them into a template file as described in [Design-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md). After editing the template file, save it, and then inspect the output **.txt** file.

## <a name="directives"></a>Anweisungen
 Textvorlagenanweisungen stellen allgemeine Anweisungen zum Generieren des Transformationscodes und der Ausgabedatei für die Textvorlagen-Engine bereit.

 Die folgende Anweisung gibt z. B. an, dass die Ausgabedatei die Erweiterung .txt haben soll:

```

<#@ output extension=".txt" #>
```

 For more information about directives, see [T4 Text Template Directives](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>Textblöcke
 Durch einen Textblock wird Text direkt in die Ausgabedatei eingefügt. Für Textblöcke wird keine spezielle Formatierung verwendet. Die folgende Textvorlage erzeugt z. B. eine Textdatei, die das Wort "Hello" enthält:

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Kontrollblöcke
 Kontrollblöcke sind Abschnitte des Programmcodes, die zum Transformieren der Vorlagen verwendet werden. Die Standardsprache ist C#, zur Verwendung von [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] können Sie jedoch die folgende Direktive am Anfang der Datei schreiben:

```
<#@ template language="VB" #>
```

 Die Sprache, in der Sie den Code in den Kontrollblöcken schreiben, steht in keinem Zusammenhang mit der Sprache des generierten Texts.

### <a name="standard-control-blocks"></a>Standardkontrollblöcke
 Ein Standardkontrollblock ist ein Abschnitt des Programmcodes, durch den ein Teil der Ausgabedatei generiert wird.

 Sie können in einer Vorlagendatei eine beliebige Anzahl von Textblöcken und Standardkontrollblöcken kombinieren. Es ist jedoch nicht möglich, einen Kontrollblock in einen anderen Kontrollblock einzufügen. Jeder Standardkontrollblock ist durch die Symbole `<# ... #>` begrenzt.

 Beim folgenden Kontrollblock und Textblock wird z. B. die Zeile "0, 1, 2, 3, 4 Hello!" in die Ausgabedatei eingefügt:

```

      <#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 Anstatt explizite `Write()`-Anweisungen zu verwenden, können Sie Text und Code verschachteln. The following example prints "Hello!" four times:

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 Sie können überall dort einen Textblock einfügen, wo eine `Write();`-Anweisung im Code zulässig wäre.

> [!NOTE]
> When you embed a text block within a compound statement such as a loop or conditional, always use braces {...} to contain the text block.

### <a name="expression-control-blocks"></a>Ausdruckskontrollblöcke
 Durch einen Ausdruckskontrollblock wird ein Ausdruck ausgewertet und in eine Zeichenfolge konvertiert. Diese Zeichenfolge wird in die Ausgabedatei eingefügt.

 Ausdruckskontrollblöcke sind durch die Symbole `<#= ... #>` begrenzt.

 Beim folgenden Kontrollblock enthält die Ausgabedatei z. B. "5":

```
<#= 2 + 3 #>
```

 Notice that the opening symbol has three characters "<#=".

 Der Ausdruck kann beliebige gültige Variablen enthalten. Durch den folgenden Block werden z. B. Zeilen mit Zahlen ausgegeben:

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>Klassenfunktionskontrollblöcke
 Ein Klassenfunktionskontrollblock definiert Eigenschaften, Methoden oder anderen Code, die nicht in der Haupttransformation enthalten sein sollten. Klassenfunktionsblöcke werden häufig für Hilfsfunktionen verwendet.  Typically, class feature blocks are placed in separate files so that they can be [included](#Include) by more than one text template.

 Klassenfunktionskontrollblöcke sind durch die Symbole `<#+ ... #>` begrenzt.

 In der folgenden Vorlagendatei wird z. B. eine Methode deklariert und verwendet:

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 Klassenfunktionen müssen am Ende der Datei eingefügt werden, in der sie geschrieben werden. `<#@include#>` kann jedoch auch dann für eine Datei, die eine Klassenfunktion enthält, verwendet werden, wenn nach der `include`-Direktive Standardblöcke und Text eingefügt werden.

 For more information about control blocks, see [Text Template Control Blocks](../modeling/text-template-control-blocks.md).

### <a name="class-feature-blocks-can-contain-text-blocks"></a>Klassenfunktionsblöcke können Textblöcke enthalten
 Sie können eine Methode schreiben, durch die Text generiert wird. Beispiel:

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 Es ist sinnvoll, Methoden zum Generieren von Text in einer separaten Datei zu speichern, die in mehrere Vorlagen eingeschlossen werden kann.

## <a name="using-external-definitions"></a>Verwenden von externen Definitionen

### <a name="assemblies"></a>Assemblys
 In den Codeblöcken der Vorlage können Typen verwendet werden, die in den am häufigsten verwendeten .NET-Assemblys definiert sind, z. B. System.dll. Außerdem können Sie auf andere .NET-Assemblys oder eigene Assemblys verweisen. Sie können einen Pfadnamen oder den starken Namen einer Assembly angeben:

```
<#@ assembly name="System.Xml" #>
```

 Verwenden Sie absolute Pfadnamen oder standardmäßige Makronamen im Pfadnamen. Beispiel:

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 For a list of macros, see [Common Macros for Build Commands and Properties](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).

 The assembly directive has no effect in a [preprocessed text template](../modeling/run-time-text-generation-with-t4-text-templates.md).

 For more information, see [T4 Assembly Directive](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>Namespaces
 Die import-Anweisung entspricht der `using`-Klausel in C# bzw. der `imports`-Klausel in Visual Basic. Sie ermöglicht es Ihnen, ohne einen vollqualifizierten Namen auf Typen im Code zu verweisen:

```
<#@ import namespace="System.Xml" #>
```

 Sie können beliebig viele `assembly`- und `import`-Direktiven verwenden. Diese Direktiven müssen vor Text- und Kontrollblöcken eingefügt werden.

 For more information, see [T4 Import Directive](../modeling/t4-import-directive.md).

### <a name="Include"></a> Including code and text
 Die `include`-Anweisung fügt Text aus einer anderen Vorlagendatei ein. Die folgende Direktive fügt z. B. den Inhalt von `test.txt` ein.

 `<#@ include file="c:\test.txt" #>`

 Der eingeschlossene Inhalt wird fast so verarbeitet, als wäre er Teil der jeweiligen Textvorlage. Sie können jedoch auch dann eine Datei einschließen, die einen Klassenfunktionsblock `<#+...#>` enthält, wenn nach der include-Direktive normale Text- und Standardkontrollblöcke eingefügt werden.

 For more information, see [T4 Include Directive](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>Hilfsmethoden
 Mehrere Methoden wie z. B. `Write()` stehen Ihnen in einem Kontrollblock immer zur Verfügung. Dazu zählen Methoden zum Einziehen der Ausgabe und Melden von Fehlern.

 Sie können auch einen eigenen Satz von Hilfsmethoden schreiben.

 For more information, see [Text Template Utility Methods](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>Transformieren von Daten und Modellen
 Einer der sinnvollsten Verwendungszwecke von Textvorlagen ist das Generieren von Material basierend auf dem Inhalt einer Quelle, z. B. einem Modell, einer Datenbank oder einer Datendatei. Die Vorlage extrahiert Daten und formatiert sie neu. Durch eine Auflistung von Vorlagen kann eine solche Quelle in mehrere Dateien transformiert werden.

 Zum Lesen der Quelldatei sind mehrere Ansätze verfügbar.

 **Read a file in the text template**. Dies ist einfachste Methode, um Daten in die Vorlage abzurufen:

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Load a file as a navigable model**. Eine effektivere Methode besteht darin, die Daten als ein Modell zu lesen, durch das der Textvorlagencode navigieren kann. Sie können z. B. eine XML-Datei laden und mit XPath-Ausdrücken darin navigieren. You could also use [xsd.exe](https://go.microsoft.com/fwlink/?LinkId=178765) to create a set of classes with which you can read the XML data.

 **Edit the model file in a diagram or form.** [!INCLUDE[dsl](../includes/dsl-md.md)] provides tools that let you edit a model as a diagram or Windows form. Dadurch kann das Modell einfacher mit Benutzern der generierten Anwendung besprochen werden. Die [!INCLUDE[dsl](../includes/dsl-md.md)] erstellen auch einen Satz stark typisierter Klassen, die die Struktur des Modells wiedergeben. For more information, see [Generating Code from a Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

 **Use a UML model**. Sie können Code aus einem UML-Modell generieren. Dies hat den Vorteil, dass das Modell als Diagramm in einer gewohnten Darstellungsweise bearbeitet werden kann. Zudem müssen Sie das Diagramm nicht entwerfen. For more information, see [Generate files from a UML model](../modeling/generate-files-from-a-uml-model.md).

### <a name="relative-file-paths-in-design-time-templates"></a>Relative Dateipfade in den Entwurfszeitvorlagen
 In a [design-time text template](../modeling/design-time-code-generation-by-using-t4-text-templates.md), if you want to reference a file in a location relative to the text template, use `this.Host.ResolvePath()`. Sie müssen auch `hostspecific="true"` in der `template`-Anweisung festlegen:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>

```

 Sie können auch andere Dienste empfangen, die vom Host bereitgestellt werden. For more information, see [Accessing Visual Studio or other Hosts from a Template](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Entwurfszeittextvorlagen werden in einer separaten AppDomain ausgeführt
 You should be aware that a [design-time text template](../modeling/design-time-code-generation-by-using-t4-text-templates.md) runs in an AppDomain that is separate from the main application. In den meisten Fällen ist dies nicht wichtig, doch in bestimmten komplexen Fällen können sich Einschränkungen ergeben. Wenn Sie z. B. Daten in oder aus der Vorlage von einem separaten Dienst übergeben möchten, muss der Dienst eine serialisierbare API bereitstellen.

 (This isn’t true of a [run-time text template](../modeling/run-time-text-generation-with-t4-text-templates.md), which provides code that is compiled along with the rest of your code.)

## <a name="editing-templates"></a>Bearbeiten von Vorlagen
 Spezialisierte Textvorlagen-Editoren können aus dem Onlinekatalog des Erweiterungs-Managers heruntergeladen werden. On the **Tools** menu, click **Extension Manager**. Click **Online Gallery**, and then use the search tool.

## <a name="related-topics"></a>Verwandte Themen

|Aufgabe|Topic|
|----------|-----------|
|Schreiben einer Textvorlage.|[Richtlinien für das Verfassen von T4-Textvorlagen](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Generieren Sie Text mithilfe von Programmcode.|[Text Template Structure](../modeling/writing-a-t4-text-template.md)|
|Generieren Sie Dateien in einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe.|[Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Führen Sie die Textgenerierung außerhalb von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aus.|[Generieren von Dateien mit dem Hilfsprogramm "TextTransform"](../modeling/generating-files-with-the-texttransform-utility.md)|
|Transformieren Sie die Daten in das Format einer domänenspezifischen Sprache.|[Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)|
|Schreiben Sie Direktivenprozessoren, um eigene Datenquellen zu transformieren.|[Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)|
