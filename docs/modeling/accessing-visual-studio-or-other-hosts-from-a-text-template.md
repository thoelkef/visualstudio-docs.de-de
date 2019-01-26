---
title: Zugreifen auf Visual Studio oder andere Hosts von einer Textvorlage
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: f92a7a900c017d9fca067d1e2e6edfd0f3eb3f5d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033543"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Zugreifen auf Visual Studio oder andere Hosts von einer Textvorlage

In einer Textvorlage können Sie Methoden und Eigenschaften, die vom Host bereitgestellt werden, die die Vorlage ausgeführt wird. Visual Studio ist ein Beispiel für einen Host an.

> [!NOTE]
> Sie können als Host für Methoden und Eigenschaften verwenden, in reguläre Textvorlagen, aber nicht in *vorverarbeitete* Textvorlagen.

## <a name="obtain-access-to-the-host"></a>Erhalten Sie Zugriff auf den host

Legen Sie den Host für den Zugriff auf `hostspecific="true"` in die `template` Richtlinie. Nun können Sie `this.Host`, weist den Typ der <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Die <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> Typ enthält Member, die Sie zum Beispiel verwenden können, zum Auflösen von Dateinamen, und melden Sie Fehler.

### <a name="resolve-file-names"></a>Auflösen von Dateinamen

Um den vollständigen Pfad einer Datei relativ zur Textvorlage zu ermitteln, verwenden Sie `this.Host.ResolvePath()`.

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

### <a name="display-error-messages"></a>Anzeigen von Fehlermeldungen

In diesem Beispiel protokolliert Meldungen auf, wenn Sie die Vorlage transformieren. Wenn der Host Visual Studio ist, die Fehler werden hinzugefügt, die **Fehlerliste**.

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

## <a name="use-the-visual-studio-api"></a>Verwenden Sie die Visual Studio-API

Wenn Sie eine Textvorlage in Visual Studio ausführen, können Sie `this.Host` zum Zugreifen auf Dienste, die von Visual Studio und alle Pakete oder Erweiterungen, die geladen werden bereitgestellt.

Legen Sie Hostspecific = "true", und wandeln Sie `this.Host` zu <xref:System.IServiceProvider>.

In diesem Beispiel wird die Visual Studio-API, <xref:EnvDTE.DTE>, als Dienst:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Verwenden Sie HostSpecific mit vorlagenvererbung

Geben Sie `hostspecific="trueFromBase"` , wenn Sie auch verwenden, die `inherits` -Attribut, und wenn Sie eine Vorlage erben, der angibt, `hostspecific="true"`. Wenn Sie dies nicht tun, erhalten Sie möglicherweise einer compilerwarnung, die die Eigenschaft `Host` zweimal deklariert wurde.