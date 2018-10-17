---
title: Hilfsprogrammmethoden für Textvorlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4a9c5a0b4b6c85a301c5d3a0e12ad3687f54aeb0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186302"
---
# <a name="text-template-utility-methods"></a>Hilfsprogrammmethoden für Textvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es gibt mehrere Methoden, die immer verfügbar, Sie beim Schreiben von Code sind einem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Textvorlage. Diese Methoden werden in definiert <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  Sie können auch andere Methoden und Diensten, die von der hostumgebung in einem regulären (nicht vorverarbeiteten Textvorlage) bereitgestellt. Z. B. Sie Dateipfade zu beheben, Fehler protokollieren und Abrufen von bereitgestellten Dienste können [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und alle geladenen Pakete.  Weitere Informationen finden Sie unter [den Zugriff auf Visual Studio von einer Textvorlage](http://msdn.microsoft.com/en-us/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## <a name="write-methods"></a>Write-Methoden  
 Sie können die `Write()` und `WriteLine()` Methoden zum Anfügen von Text in einem standard-Codeblock, anstatt einen Codeblock Ausdruck. Die folgenden beiden Codeblöcke sind funktional äquivalent.  
  
##### <a name="code-block-with-an-expression-block"></a>Der Codeblock mit einem Ausdrucksblock  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>Mithilfe von WriteLine()"Codeblock  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 Möglicherweise finden Sie es hilfreich, um eine der folgenden Hilfsprogrammmethoden statt einem Ausdrucksblock in einem langen Codeblock mit geschachtelten Steuerungsstrukturen.  
  
 Die `Write()` und `WriteLine()` Methoden verfügen über zwei Überladungen, die eine, die einen einzelnen Zeichenfolgenparameter und eine, die akzeptiert übernimmt, eine kombinierte Formatzeichenfolge sowie ein Array von Objekten, die in der Zeichenfolge enthalten (z. B. die `Console.WriteLine()` Methode). Die folgenden beiden Verwendungen von `WriteLine()` sind funktional äquivalent:  
  
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
 Sie können den Einzugsmethoden verwenden, zum Formatieren der Ausgabe von der Textvorlage. Die <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> -Klasse verfügt über eine `CurrentIndent` Zeichenfolgeneigenschaft, die den aktuellen Einzug in der Textvorlage anzeigt und ein `indentLengths` Feld, das eine Liste der die Einzüge, die hinzugefügt wurden. Sie können einen Einzug mit Hinzufügen der `PushIndent()` Methode und subtrahieren ein Einzugs mit der `PopIndent()` Methode. Wenn Sie alle Einzüge entfernen möchten, verwenden Sie die `ClearIndent()` Methode. Der folgende Codeblock zeigt die Verwendung der folgenden Methoden:  
  
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
  
## <a name="error-and-warning-methods"></a>Fehler und Warning-Methoden  
 Können Sie Fehler und Warnungen-Hilfsmethoden zum Hinzufügen von Nachrichten an die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Fehlerliste. Beispielsweise wird der folgende Code eine Fehlermeldung der Fehlerliste hinzugefügt werden.  
  
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
 Die Eigenschaft `this.Host` bieten Zugriff auf Eigenschaften verfügbar gemacht werden, durch den Host, der die Vorlage ausgeführt wird. Verwendung von `this.Host`, müssen Sie festlegen, `hostspecific` -Attribut in der `<@template#>` Richtlinie:  
  
 `<#@template ... hostspecific="true" #>`  
  
 Der Typ des `this.Host` hängt vom Typ des Hosts, die in der die Vorlage ausgeführt wird. In einer Vorlage, die ausgeführt wird, in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Sie können eine Typumwandlung `this.Host` zu `IServiceProvider` für den Zugriff auf Dienste wie der IDE. Zum Beispiel:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>Verwenden einen anderen Satz von Hilfsmethoden  
 Als Teil des Generierungsprozesses der Text, in eine Klasse, die immer den Namen die Vorlagendatei transformiert `GeneratedTextTransformation`und erbt von <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Sollten Sie einen anderen können Satz von Methoden stattdessen Sie eine eigene Klasse schreiben und es in der Template-Direktive angeben. Die Klasse muss von erben <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Verwenden der `assembly` Richtlinie auf die Assembly verweisen, in denen die kompilierte Klasse gefunden werden kann.



