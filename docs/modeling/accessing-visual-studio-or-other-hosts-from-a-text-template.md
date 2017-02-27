---
title: "Accessing Visual Studio or other Hosts from a Text Template | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 5
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 5
---
# Accessing Visual Studio or other Hosts from a Text Template
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In einer Textvorlage können Sie Methoden und Eigenschaften verwenden, die vom Host verfügbar gemacht werden, der die Vorlage ausführt, z. B. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Dies gilt für reguläre Textvorlagen, jedoch nicht für vorverarbeitete Textvorlagen.  
  
## Erhalten von Zugriff auf den Host  
 Legen Sie `hostspecific="true"` in der `template`\-Direktive fest.  Damit können Sie `this.Host` verwenden, das den Typ <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> hat.  Dieser Typ verfügt über Member, die Sie verwenden können, z. B., um Dateinamen aufzulösen und Fehler zu protokollieren.  
  
### Auflösen von Dateinamen  
 Um den vollständigen Pfad einer Datei relativ zur Textvorlage zu suchen, verwenden Sie this.Host.ResolvePath\(\).  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.IO" #>  
<#  
 // Find a path within the same project as the text template:  
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));  
#>  
Content of myFile is:  
<#= myFile #>  
  
```  
  
### Anzeigen von Fehlermeldungen  
 In diesem Beispiel werden Meldungen protokolliert, wenn die Vorlage transformiert wird.  Wenn der Host [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist, werden sie dem Fehlerfenster hinzugefügt.  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.CodeDom.Compiler" #>  
<#  
  string message = "test message";  
  this.Host.LogErrors(new CompilerErrorCollection()   
    { new CompilerError(  
       this.Host.TemplateFile, // Identify the source of the error.  
       0, 0, "0",   // Line, column, error ID.  
       message) }); // Message displayed in error window.  
#>  
  
```  
  
## Verwenden der Visual Studio\-API  
 Wenn Sie eine Textvorlage in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführen, können Sie mit `this.Host` auf Dienste zugreifen, die von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und allen geladenen Paketen oder Erweiterungen bereitgestellt werden.  
  
 Legen Sie hostspecific\="true" fest, und wandeln Sie `this.Host` in <xref:System.IServiceProvider> um.  
  
 In diesem Beispiel wird die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-API, <xref:EnvDTE.DTE>, als Dienst abgerufen:  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="EnvDTE" #>  
<#   
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;    
#>  
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>  
  
```  
  
## Verwenden HostSpecific mit Template\-Vererbung  
 Geben Sie `hostspecific="trueFromBase"` Wenn Sie auch verwenden, die `inherits` \-Attribut, und wenn Sie von einer Vorlage erben, der angibt, `hostspecific="true"`.  Dies vermeidet eine Compilerwarnung dahingehend, dass die Eigenschaft `Host` wurde zweimal deklariert.