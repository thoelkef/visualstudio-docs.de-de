---
title: "Hilfsprogrammmethoden für Textvorlagen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: "50"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 534a7317b4bca2abe559c028d025a52997a9f508
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="text-template-utility-methods"></a>Hilfsprogrammmethoden für Textvorlagen
Es gibt mehrere Methoden, die immer Ihnen beim Schreiben von Code stehen einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Textvorlage. Diese Methoden werden in definiert <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  Sie können auch andere Methoden und Dienste, die von der hostumgebung in eine reguläre (nicht vorverarbeiteten Vorlage) bereitgestellt. Z. B. Sie Dateipfade zu beheben, Fehler werden protokolliert und Abrufen von Diensten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und alle Pakete geladen.  Weitere Informationen finden Sie unter [Zugriff auf Visual Studio in einer Textvorlage](http://msdn.microsoft.com/en-us/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## <a name="write-methods"></a>Write-Methoden  
 Sie können die `Write()` und `WriteLine()` Methoden, um Text in einem standardmäßigen Codeblock, anstatt von einem Ausdrucksblock-Code angefügt werden soll. Die folgenden zwei Codeblöcke sind funktional äquivalent.  
  
##### <a name="code-block-with-an-expression-block"></a>Code-Block mit einem Ausdrucksblock  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>Codeblock mit WriteLine()  
  
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
 Können Sie Fehler und Warnungen Utility-Methoden zum Hinzufügen von Nachrichten an die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Fehlerliste. Im folgende Code wird z. B. eine Fehlermeldung an die Fehlerliste hinzufügen.  
  
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
  
 Der Typ des `this.Host` hängt vom Typ des Hosts, die in der Vorlage ausgeführt wird. In einer Vorlage, die ausgeführt wird, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], können Sie eine Umwandlung `this.Host` auf `IServiceProvider` für den Zugriff auf Dienste wie der IDE. Zum Beispiel:  
  
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