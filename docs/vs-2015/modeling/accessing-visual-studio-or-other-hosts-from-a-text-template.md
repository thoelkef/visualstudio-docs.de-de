---
title: Zugreifen auf Visual Studio 2015 oder andere Hosts über eine Text Vorlage | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 053e8b09fd2b52683238f1ffe008e5e7d38b3962
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872007"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Zugreifen auf Visual Studio oder andere Hosts von einer Textvorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einer Textvorlage können Sie Methoden und Eigenschaften verwenden, die vom Host verfügbar gemacht werden, der die Vorlage ausführt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], z. b.

 Dies gilt für reguläre Textvorlagen, nicht für vorverarbeitete Textvorlagen.

## <a name="obtaining-access-to-the-host"></a>Zugriff auf den Host erhalten

In `hostspecific="true"` der`template` -Direktive festgelegt. Auf diese Weise können `this.Host`Sie mit dem Typ [itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))verwenden. Dieser Typ enthält Member, die Sie verwenden können, um z. b. Dateinamen aufzulösen und Fehler zu protokollieren.

### <a name="resolving-file-names"></a>Auflösen von Dateinamen
 Um den vollständigen Pfad einer Datei relativ zur Textvorlage zu finden, verwenden Sie diese. Host. resolvepath ().

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
 In diesem Beispiel protokolliert Meldungen auf, wenn Sie die Vorlage transformieren. Wenn der Host ist [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], werden diese dem Fehler Fenster hinzugefügt.

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

## <a name="using-the-visual-studio-api"></a>Verwenden der Visual Studio-API
 Wenn Sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]eine Textvorlage ausführen, können Sie verwenden `this.Host` , um auf die von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bereitgestellten Dienste und alle Pakete oder Erweiterungen zuzugreifen, die geladen werden.

 Legen Sie Hostspecific = "true", und wandeln Sie `this.Host` zu <xref:System.IServiceProvider>.

 In diesem Beispiel wird [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] die API <xref:EnvDTE.DTE>,, als Dienst abgerufen:

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

## <a name="using-hostspecific-with-template-inheritance"></a>Verwenden von hostspecific mit Vorlagen Vererbung
 Geben Sie `hostspecific="trueFromBase"` , wenn Sie auch verwenden, die `inherits` -Attribut, und wenn Sie eine Vorlage erben, der angibt, `hostspecific="true"`. Dadurch wird eine Compilerwarnung vermieden, die besagt, `Host` dass die Eigenschaft zweimal deklariert wurde.
