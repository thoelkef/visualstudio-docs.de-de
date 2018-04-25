---
title: Hilfsprogrammmethoden für Textvorlagen
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9367c5c8e65c58a79b0d8e864c5a9a201fbe3954
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="text-template-utility-methods"></a>Hilfsprogrammmethoden für Textvorlagen

Es gibt mehrere Methoden, die immer Ihnen beim Schreiben von Code in einer Textvorlage Visual Studio stehen. Diese Methoden werden in definiert <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

> [!TIP]
> Sie können auch andere Methoden und Dienste, die von der hostumgebung in eine reguläre (nicht vorverarbeiteten Vorlage) bereitgestellt. Z. B. Sie Dateipfade zu beheben, Fehler protokollieren und Abrufen von Diensten, die von Visual Studio und alle bereitgestellten Pakete geladen. Weitere Informationen finden Sie unter [Zugriff auf Visual Studio in einer Textvorlage](http://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

## <a name="write-methods"></a>Write-Methoden

Sie können die `Write()` und `WriteLine()` Methoden, um Text in einem standardmäßigen Codeblock, anstatt von einem Ausdrucksblock-Code angefügt werden soll. Die folgenden zwei Codeblöcke sind funktional äquivalent.

### <a name="code-block-with-an-expression-block"></a>Code-Block mit einem Ausdrucksblock

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Codeblock mit WriteLine()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Sie können es verwenden diese Hilfsmethoden statt einem Ausdrucksblock in einem langen Codeblock mit geschachtelten Steuerungsstrukturen hilfreich sein.

Die `Write()` und `WriteLine()` Methoden verfügen über zwei Überladungen, die eine, die einen einzelnen Zeichenfolgenparameter und eine, die akzeptiert akzeptiert eine kombinierte Formatzeichenfolge plus ein Array von Objekten, die in der Zeichenfolge enthalten (z. B. die `Console.WriteLine()` Methode). Die folgenden beiden Verwendungen von `WriteLine()` sind funktional äquivalent:

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>Einzugsmethoden

Einzugsmethoden können zur Formatierung der Ausgabe von der Textvorlage. Die <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> -Klasse verfügt über eine `CurrentIndent` Zeichenfolgeneigenschaft, die den aktuellen Einzug in der Textvorlage anzeigt und eine `indentLengths` Feld, das eine Liste mit den Einzüge, die hinzugefügt wurden. Sie können einen Einzug mit Hinzufügen der `PushIndent()` Methode und subtrahieren ein Einzugs mit der `PopIndent()` Methode. Wenn Sie alle Einzüge entfernen möchten, verwenden Sie die `ClearIndent()` Methode. Der folgende Codeblock zeigt die Verwendung der folgenden Methoden:

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

In diesem Codeblock erzeugt die folgende Ausgabe:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Fehler- und Warning-Methoden

Sie können Fehler und Warnung Utility-Methoden zum Hinzufügen von Nachrichten, die Visual Studio-Fehlerliste verwenden. Im folgende Code wird z. B. eine Fehlermeldung an die Fehlerliste hinzufügen.

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>Zugriff auf den Host und Dienstanbieter

Die Eigenschaft `this.Host` bieten Zugriff auf Eigenschaften verfügbar gemacht werden, durch den Host, der die Vorlage ausgeführt wird. Mit `this.Host`, müssen Sie festlegen `hostspecific` Attribut in der `<@template#>` Richtlinie:

`<#@template ... hostspecific="true" #>`

Der Typ des `this.Host` hängt vom Typ des Hosts, die in der Vorlage ausgeführt wird. In einer Vorlage, die in Visual Studio ausgeführt wird, können Sie umwandeln `this.Host` auf `IServiceProvider` für den Zugriff auf Dienste wie der IDE. Zum Beispiel:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Verwenden einen anderen Satz von Hilfsmethoden

Im Rahmen des Prozesses Generation Text Vorlagendatei in eine Klasse, die stets benannt wird transformiert `GeneratedTextTransformation`und erbt von <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Wenn Sie ein anderes verwenden möchten können Satz von Methoden stattdessen, Sie eine eigene Klasse schreiben und in der Template-Direktive angeben. Die Klasse muss von erben <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

```
<#@ template inherits="MyUtilityClass" #>
```

Verwenden der `assembly` Richtlinie auf die Assembly verweisen, in dem die kompilierte Klasse gefunden werden kann.