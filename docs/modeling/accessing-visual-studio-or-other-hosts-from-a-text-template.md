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
ms.openlocfilehash: 26845b3878a89ea52a3f77f9a0a8d23363877edd
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870680"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Zugreifen auf Visual Studio oder andere Hosts über eine Textvorlage

In einer Textvorlage können Sie Methoden und Eigenschaften, die vom Host bereitgestellt werden, die die Vorlage ausgeführt wird. Visual Studio ist ein Beispiel für einen Host an.

> [!NOTE]
> Sie können als Host für Methoden und Eigenschaften verwenden, in reguläre Textvorlagen, aber nicht in *vorverarbeitete* Textvorlagen.

## <a name="obtain-access-to-the-host"></a>Erhalten Sie Zugriff auf den host

Legen Sie den Host für den Zugriff auf `hostspecific="true"` in die `template` Richtlinie. Nun können Sie mit `this.Host`dem Typ [itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))verwenden. Der [itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) -Typ enthält Member, die Sie zum Auflösen von Dateinamen und Protokoll Fehlern verwenden können, z. b.

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