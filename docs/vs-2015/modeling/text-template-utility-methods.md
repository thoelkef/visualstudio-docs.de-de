---
title: Methoden für Text Vorlagen-Hilfsprogramm | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c38b15a3b819ce561c098c3b9810ee6884e526b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658525"
---
# <a name="text-template-utility-methods"></a>Hilfsprogrammmethoden für Textvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Code in eine Textvorlage schreiben, stehen Ihnen mehrere Methoden zur Verfügung [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Diese Methoden werden in definiert <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> Sie können auch andere Methoden und Dienste, die von der Host Umgebung bereitgestellt werden, in einer regulären (nicht vorverarbeiteten) Textvorlage verwenden. Beispielsweise können Sie Dateipfade auflösen, Fehler protokollieren und Dienste, die von bereitgestellt werden, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sowie alle geladenen Pakete erhalten.  Weitere Informationen finden Sie unter [zugreifen auf Visual Studio von einer Text Vorlage aus](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

## <a name="write-methods"></a>Write-Methoden
 Sie können die `Write()` -Methode und die-Methode verwenden, `WriteLine()` um Text in einem standardmäßigen Codeblock anzufügen, anstatt einen Expression-Codeblock zu verwenden. Die folgenden beiden Code Blöcke sind funktional äquivalent.

##### <a name="code-block-with-an-expression-block"></a>Codeblock mit einem Ausdrucks Block

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

##### <a name="code-block-using-writeline"></a>Codeblock mit "Write teline ()"

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

 Möglicherweise ist es hilfreich, eine dieser Hilfsmethoden anstelle eines Ausdrucks Blocks innerhalb eines langen Codeblocks mit geschachtelten Steuerungsstrukturen zu verwenden.

 Die `Write()` -Methode und die- `WriteLine()` Methode verfügen über zwei über Ladungen: eine, die einen einzelnen Zeichen folgen Parameter annimmt, und einen, der eine kombinierte Format Zeichenfolge und ein Array von-Objekten annimmt, die in die Zeichenfolge eingeschlossen werden sollen (wie `Console.WriteLine()` Die folgenden beiden Verwendungen von `WriteLine()` sind funktional äquivalent:

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

## <a name="indentation-methods"></a>Einzug Methoden
 Sie können Einzugs Methoden verwenden, um die Ausgabe der Textvorlage zu formatieren. Die <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> -Klasse verfügt über eine `CurrentIndent` Zeichen folgen Eigenschaft, die den aktuellen Einzug in der Textvorlage und ein `indentLengths` Feld anzeigt, das eine Liste der hinzugefügten Einzüge ist. Sie können mit der-Methode einen Einzug hinzufügen `PushIndent()` und einen Einzug mit der-Methode subtrahieren `PopIndent()` . Wenn Sie alle Einzüge entfernen möchten, verwenden Sie die- `ClearIndent()` Methode. Der folgende Codeblock zeigt die Verwendung dieser Methoden:

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

 Dieser Codeblock erzeugt die folgende Ausgabe:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Fehler-und Warnungs Methoden
 Sie können Fehler-und Warnungs Dienstprogramm-Methoden verwenden, um dem Fehlerliste Meldungen hinzuzufügen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Der folgende Code fügt z. b. eine Fehlermeldung zum Fehlerliste hinzu.

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

## <a name="access-to-host-and-service-provider"></a>Zugriff auf Host und Dienstanbieter
 Die-Eigenschaft `this.Host` kann Zugriff auf Eigenschaften bereitstellen, die vom Host verfügbar gemacht werden, der die Vorlage ausführt. Zum Verwenden von `this.Host` müssen Sie `hostspecific` das-Attribut in der- `<@template#>` Direktive festlegen:

 `<#@template ... hostspecific="true" #>`

 Der Typ von `this.Host` hängt vom Hosttyp ab, in dem die Vorlage ausgeführt wird. In einer Vorlage, die in ausgeführt wird, können Sie in umwandeln, um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] `this.Host` `IServiceProvider` Zugriff auf Dienste wie z. b. die IDE zu erhalten. Beispiel:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Verwenden eines anderen Satzes von Hilfsprogrammmethoden
 Im Rahmen des Text Generierungs Prozesses wird die Vorlagen Datei in eine Klasse transformiert, die immer den Namen hat `GeneratedTextTransformation` und von erbt <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Wenn Sie stattdessen einen anderen Satz von Methoden verwenden möchten, können Sie eine eigene Klasse schreiben und in der Template-Direktive angeben. Die Klasse muss von Erben <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

 Verwenden Sie die- `assembly` Direktive, um auf die Assembly zu verweisen, in der sich die kompilierte Klasse befindet
