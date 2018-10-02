---
title: Zugreifen auf Visual Studio oder andere Hosts von einer Textvorlage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5bcd1811db000b39f7c9897f1329434af9fe5258
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514408"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Zugreifen auf Visual Studio oder andere Hosts von einer Textvorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [den Zugriff auf Visual Studio oder andere Hosts von einer Textvorlage](https://docs.microsoft.com/visualstudio/modeling/accessing-visual-studio-or-other-hosts-from-a-text-template).  
  
Sie können in einer Textvorlage verwenden, Methoden und Eigenschaften verfügbar gemacht werden, von dem Host, der die Vorlage, wie z. B. führt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Dies gilt für Textvorlagen reguläre, nicht vorverarbeitete Textvorlagen.  
  
## <a name="obtaining-access-to-the-host"></a>Erhalten Zugriff auf den host  
 Legen Sie `hostspecific="true"` in die `template` Richtlinie. So können Sie verwenden `this.Host`, weist den Typ der <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Dieser Typ verfügt über Elemente, mit denen Sie, z. B. zum Auflösen von Dateinamen und den Fehler zu protokollieren.  
  
### <a name="resolving-file-names"></a>Auflösen von Dateinamen  
 Verwenden Sie diese Schritte aus, um den vollständigen Pfad einer Datei relativ zur Textvorlage zu suchen. Host.ResolvePath().  
  
```csharp  
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
  
### <a name="displaying-error-messages"></a>Anzeigen von Fehlermeldungen  
 In diesem Beispiel protokolliert Meldungen auf, wenn Sie die Vorlage transformieren. Wenn der Host ist [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], werden sie das Fehlerfenster hinzugefügt.  
  
```csharp  
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
  
## <a name="using-the-visual-studio-api"></a>Mithilfe der Visual Studio-API  
 Wenn Sie eine Textvorlage in ausführen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], können Sie `this.Host` zum Zugreifen auf Dienste, die von bereitgestellte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und Pakete und -Erweiterungen, die geladen werden.  
  
 Legen Sie Hostspecific = "true", und wandeln Sie `this.Host` zu <xref:System.IServiceProvider>.  
  
 In diesem Beispiel wird die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -API, <xref:EnvDTE.DTE>, als Dienst:  
  
```csharp  
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
  
## <a name="using-hostspecific-with-template-inheritance"></a>Verwenden HostSpecific mit vorlagenvererbung  
 Geben Sie `hostspecific="trueFromBase"` , wenn Sie auch verwenden, die `inherits` -Attribut, und wenn Sie eine Vorlage erben, der angibt, `hostspecific="true"`. Dies vermeidet eine compilerwarnung für den Effekt, der die Eigenschaft `Host` zweimal deklariert wurde.



