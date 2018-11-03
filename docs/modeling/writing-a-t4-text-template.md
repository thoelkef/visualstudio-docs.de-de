---
title: Schreiben einer T4-Textvorlage
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0d697f1fed2a7b17862ff4c6f72488674859f754
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967297"
---
# <a name="writing-a-t4-text-template"></a>Schreiben einer T4-Textvorlage
Eine Textvorlage enthält den Text, der aus ihr generiert wird. Beispielsweise enthält eine Vorlage, die eine Webseite erstellt "\<html > …" und alle anderen Standardteile einer HTML-Seite. In der Vorlage eingefügt werden *Kontrollblöcke*, die Fragmente des Programmcodes sind. Kontrollblöcke stellen veränderliche Werte bereit und ermöglichen es, Bedingungen für Teile des Texts zu definieren und Teile des Texts zu wiederholen.

 Diese Struktur vereinfacht das Entwickeln einer Vorlage, da Sie mit einem Prototyp der generierten Datei beginnen und nach und nach Kontrollblöcke zum Verändern des Ergebnisses einfügen können.

 Textvorlagen bestehen aus den folgenden Teilen:

-   **Direktiven** -Elemente, die steuern, wie die Vorlage verarbeitet wird.

-   **Textblöcke** : Inhalt, der direkt in die Ausgabe kopiert wird.

-   **Kontrollblöcke** -Programmcode, der Variablenwerte in den Text eingefügt und bedingte oder wiederholte Teile des Texts gesteuert.

Wenn in die Beispielen in diesem Thema testen möchten, kopieren Sie sie in einer Vorlagendatei unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Nach dem Bearbeiten der Datei der Vorlage an, sie speichern und untersuchen Sie die Ausgabe **.txt** Datei.

## <a name="directives"></a>Anweisungen
 Textvorlagendirektiven stellen allgemeine Anweisungen zum Generieren des Transformationscodes und der Ausgabedatei für das Textvorlagenmodul bereit.

 Die folgende Anweisung gibt z. B. an, dass die Ausgabedatei die Erweiterung .txt haben soll:

```
<#@ output extension=".txt" #>
```

 Weitere Informationen zu Direktiven finden Sie unter [T4-Textvorlagenanweisungen](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>Textblöcke
 Durch einen Textblock wird Text direkt in die Ausgabedatei eingefügt. Für Textblöcke wird keine spezielle Formatierung verwendet. Die folgende Textvorlage erzeugt z. B. eine Textdatei, die das Wort "Hello" enthält:

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Kontrollblöcke
 Kontrollblöcke sind Abschnitte des Programmcodes, die zum Transformieren der Vorlagen verwendet werden. Die Standardsprache ist C#, zur Verwendung von [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] können Sie jedoch die folgende Direktive am Anfang der Datei schreiben:

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

 Anstatt explizite `Write()`-Anweisungen zu verwenden, können Sie Text und Code verschachteln. Das folgende Beispiel gibt "Hello!" vier Mal:

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
>  Wenn Sie einen Textblock innerhalb einer verbundanweisung, z. B. einer Schleife oder Bedingung einbetten, verwenden Sie immer geschweifte Klammern {...} den Textblock enthalten.

### <a name="expression-control-blocks"></a>Ausdruckskontrollblöcke
 Durch einen Ausdruckskontrollblock wird ein Ausdruck ausgewertet und in eine Zeichenfolge konvertiert. Diese Zeichenfolge wird in die Ausgabedatei eingefügt.

 Ausdruckskontrollblöcke sind durch die Symbole `<#= ... #>` begrenzt.

 Beim folgenden Kontrollblock enthält die Ausgabedatei z. B. "5":

```
<#= 2 + 3 #>
```

 Beachten Sie, dass das öffnende Symbol aus drei Zeichen besteht "<#=".

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
 Ein Klassenfunktionskontrollblock definiert Eigenschaften, Methoden oder anderen Code, die nicht in der Haupttransformation enthalten sein sollten. Klassenfunktionsblöcke werden häufig für Hilfsfunktionen verwendet.  Normalerweise werden Klassenfunktionsblöcke in separaten Dateien gespeichert, damit sie stehen [enthalten](#Include) von mehr als eine Textvorlage.

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

 Weitere Informationen zu Kontrollblöcken finden Sie unter [Kontrollblöcke für Textvorlagen](../modeling/text-template-control-blocks.md).

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

 Verwenden Sie absolute Pfadnamen oder standardmäßige Makronamen im Pfadnamen. Zum Beispiel:

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 Die Assembly-Anweisung hat keine Auswirkung, in einem [vorverarbeiteten Textvorlage](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Weitere Informationen finden Sie unter [T4-Assemblydirektive](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>Namespaces
 Die import-Direktive entspricht der `using`-Klausel in C# bzw. der `imports`-Klausel in Visual Basic. Sie ermöglicht es Ihnen, ohne einen vollqualifizierten Namen auf Typen im Code zu verweisen:

```
<#@ import namespace="System.Xml" #>
```

 Sie können beliebig viele `assembly`- und `import`-Direktiven verwenden. Diese Direktiven müssen vor Text- und Kontrollblöcken eingefügt werden.

 Weitere Informationen finden Sie unter [T4-Import-Direktive](../modeling/t4-import-directive.md).

### <a name="Include"></a> Einschließlich Code und text
 Die `include`-Anweisung fügt Text aus einer anderen Vorlagendatei ein. Die folgende Direktive fügt z. B. den Inhalt von `test.txt` ein.

```
<#@ include file="c:\test.txt" #>
```

 Der eingeschlossene Inhalt wird fast so verarbeitet, als wäre er Teil der jeweiligen Textvorlage. Sie können jedoch auch dann eine Datei einschließen, die einen Klassenfunktionsblock `<#+...#>` enthält, wenn nach der include-Anweisung normale Text- und Standardkontrollblöcke eingefügt werden.

 Weitere Informationen finden Sie unter [T4-Include-Direktive](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>Hilfsmethoden
 Mehrere Methoden wie z. B. `Write()` stehen Ihnen in einem Kontrollblock immer zur Verfügung. Dazu zählen Methoden zum Einziehen der Ausgabe und Melden von Fehlern.

 Sie können auch einen eigenen Satz von Hilfsmethoden schreiben.

 Weitere Informationen finden Sie unter [Hilfsprogrammmethoden für Textvorlagen](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>Transformieren von Daten und Modellen
 Einer der sinnvollsten Verwendungszwecke von Textvorlagen ist das Generieren von Material basierend auf dem Inhalt einer Quelle, z. B. einem Modell, einer Datenbank oder einer Datendatei. Die Vorlage extrahiert Daten und formatiert sie neu. Durch eine Auflistung von Vorlagen kann eine solche Quelle in mehrere Dateien transformiert werden.

 Zum Lesen der Quelldatei sind mehrere Ansätze verfügbar.

 **Lesen einer Datei in der Textvorlage**. Dies ist einfachste Methode, um Daten in die Vorlage abzurufen:

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Lädt eine Datei als navigierbares Modell**. Eine effektivere Methode besteht darin, die Daten als ein Modell zu lesen, durch das der Textvorlagencode navigieren kann. Sie können z. B. eine XML-Datei laden und mit XPath-Ausdrücken darin navigieren. Außerdem können Sie [xsd.exe](http://go.microsoft.com/fwlink/?LinkId=178765) um einen Satz von Klassen zu erstellen, mit denen die XML-Daten gelesen werden können.

 **Bearbeiten Sie die Modelldatei in einem Diagramm oder Formular.** [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] bietet Tools, mit denen Sie ein Modell als Diagramm oder Windows Form bearbeiten. Dadurch kann das Modell einfacher mit Benutzern der generierten Anwendung besprochen werden. Die [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] erstellen auch einen Satz stark typisierter Klassen, die die Struktur des Modells wiedergeben. Weitere Informationen finden Sie unter [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="relative-file-paths-in-design-time-templates"></a>Relative Dateipfade in den Entwurfszeitvorlagen
 In einem [während der Entwurfszeit Textvorlage](../modeling/design-time-code-generation-by-using-t4-text-templates.md), wenn Sie eine Datei an einem Speicherort relativ zur Textvorlage ist, verwenden verweisen möchten `this.Host.ResolvePath()`. Sie müssen auch `hostspecific="true"` in der `template`-Anweisung festlegen:

```
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

Sie können auch andere Dienste empfangen, die vom Host bereitgestellt werden. Weitere Informationen finden Sie unter [den Zugriff auf Visual Studio oder andere Hosts aus einer Vorlage](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Entwurfszeittextvorlagen werden in einer separaten AppDomain ausgeführt

 Sollten Sie bedenken, die eine [während der Entwurfszeit Textvorlage](../modeling/design-time-code-generation-by-using-t4-text-templates.md) ausgeführt wird, in einer AppDomain, die von der hauptanwendung getrennt ist. In den meisten Fällen ist dies nicht wichtig, doch in bestimmten komplexen Fällen können sich Einschränkungen ergeben. Wenn Sie z. B. Daten in oder aus der Vorlage von einem separaten Dienst übergeben möchten, muss der Dienst eine serialisierbare API bereitstellen.

 (Dies gilt nicht für eine [Laufzeit-Textvorlage](../modeling/run-time-text-generation-with-t4-text-templates.md), der Code, der zusammen mit dem restlichen Code kompiliert wird bereitgestellt.)

## <a name="editing-templates"></a>Bearbeiten von Vorlagen
 Spezialisierte Textvorlagen-Editoren können aus dem Onlinekatalog des Erweiterungs-Managers heruntergeladen werden. Auf der **Tools** Menü klicken Sie auf **Erweiterungs-Manager**. Klicken Sie auf **Onlinekatalog**, und klicken Sie dann mithilfe der Suchfunktion.

## <a name="related-topics"></a>Verwandte Themen

|Aufgabe|Thema|
|-|-|
|Schreiben einer Textvorlage.|[Richtlinien für das Verfassen von T4-Textvorlagen](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Generieren Sie Text mithilfe von Programmcode.|[Text-Vorlagen: Struktur](../modeling/writing-a-t4-text-template.md)|
|Generieren von Dateien in Visual Studio-Projektmappe.|[Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Führen Sie die textgenerierung außerhalb von Visual Studio.|[Generieren von Dateien mit dem Hilfsprogramm "TextTransform"](../modeling/generating-files-with-the-texttransform-utility.md)|
|Transformieren Sie die Daten in das Format einer domänenspezifischen Sprache.|[Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)|
|Schreiben Sie Anweisungsprozessoren, um eigene Datenquellen zu transformieren.|[Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)|
