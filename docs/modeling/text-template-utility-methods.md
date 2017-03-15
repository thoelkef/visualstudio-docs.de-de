---
title: "Text Template Utility Methods | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, utility methods"
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 50
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 50
---
# Text Template Utility Methods
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mehrere Methoden stehen Ihnen beim Schreiben von Code in einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Textvorlage immer zur Verfügung.  Diese Methoden sind in <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> definiert.  
  
> [!TIP]
>  Sie können auch andere Methoden und Dienste, die von der Hostumgebung bereitgestellt werden, in einer regulären \(nicht vorverarbeiteten\) Textvorlage verwenden.  Sie können z. B. Dateipfade und Protokollfehler korrigieren und Dienste von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und allen geladenen Paketen bereitstellen lassen.  Weitere Informationen finden Sie unter [Accessing Visual Studio from a Text Template](http://msdn.microsoft.com/de-de/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## Write\-Methoden  
 Die `Write()`\- und `WriteLine()`\-Methoden können anstelle eines Ausdruckscodeblocks verwendet werden, um Text in einem Standardcodeblock anzufügen.  Die folgenden zwei Codeblöcke sind funktional äquivalent.  
  
##### Codeblock mit einem Ausdrucksblock  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### Codeblock mit WriteLine\(\)  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 In einem langen Codeblock mit geschachtelten Kontrollstrukturen kann es hilfreich, eine dieser Hilfsprogrammmethoden anstelle eines Ausdrucksblocks zu verwenden.  
  
 Die `Write()`\- und `WriteLine()`\-Methoden verfügen über zwei Überladungen: eine, die einen einzelnen Zeichenfolgenparameter akzeptiert, und eine, die eine zusammengesetzte Formatzeichenfolge sowie ein in die Zeichenfolge einzuschließendes Objektarray akzeptiert \(wie die `Console.WriteLine()`\-Methode\).  Die folgenden zwei Deklarationen von `WriteLine()` sind funktional äquivalent:  
  
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
  
## Einzugsmethoden  
 Sie können die Ausgabe der Textvorlage mithilfe von Einzugsmethoden formatieren.  Die <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>\-Klasse verfügt über eine `CurrentIndent`\-Zeichenfolgeneigenschaft, die den aktuellen Einzug in der Textvorlage anzeigt, und ein `indentLengths`\-Feld, das eine Liste der hinzugefügten Einzüge enthält.  Sie können einen Einzug mit der `PushIndent()` \-Methode hinzufügen und mit der `PopIndent()`\-Methode entfernen.  Wenn Sie alle Einzüge entfernen möchten, verwenden Sie die `ClearIndent()`\-Methode.  Im folgenden Codeblock wird die Verwendung dieser Methoden veranschaulicht:  
  
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
  
## Error\- und Warning\-Methoden  
 Sie können der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Fehlerliste mithilfe von Error\- und Warning\-Hilfsmethoden Meldungen hinzufügen.  Durch den folgenden Code wird der Fehlerliste z. B. eine Fehlermeldung hinzugefügt.  
  
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
  
## Zugrifft auf den Host und Dienstanbieter  
 Die `this.Host`\-Eigenschaft kann Zugriff auf Eigenschaften bieten, die von dem zum Ausführen der Vorlage verwendeten Host verfügbar gemacht werden.  Zur Verwendung von `this.Host` müssen Sie das `hostspecific`\-Attribut in der `<@template#>`\-Direktive festlegen:  
  
 `<#@template ...  hostspecific="true" #>`  
  
 Der Typ von `this.Host` hängt vom Typ des Hosts ab, von dem die Vorlage ausgeführt wird.  In einer Vorlage, die in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird, können Sie `this.Host` in `IServiceProvider` umwandeln, um Zugriff auf Dienste wie IDE zu erhalten.  Beispiele:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## Verwenden eines anderen Hilfsmethodensatzes  
 Im Rahmen des Textgenerierungsprozesses wird die Vorlagendatei in eine Klasse transformiert, die immer den Namen `GeneratedTextTransformation` erhält und von <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> erbt.  Wenn Sie stattdessen einen anderen Satz von Methoden verwenden möchten, können Sie eine eigene Klasse schreiben und in der Vorlagendirektive angeben.  Die Klasse muss von <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> erben.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Verwenden Sie die `assembly`\-Direktive, um auf die Assembly zu verweisen, in der sich die kompilierte Klasse befindet.