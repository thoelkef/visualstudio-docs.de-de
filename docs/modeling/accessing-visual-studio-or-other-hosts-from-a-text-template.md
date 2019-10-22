---
title: Zugreifen auf Visual Studio oder andere Hosts von einer Textvorlage
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752b9d9e69eee26f267927f03c4b83c68740100b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652363"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Zugreifen auf Visual Studio oder andere Hosts über eine Textvorlage

In einer Textvorlage können Sie Methoden und Eigenschaften verwenden, die vom Host verfügbar gemacht werden, von dem die Vorlage ausgeführt wird. Visual Studio ist ein Beispiel für einen Host.

> [!NOTE]
> Sie können Host Methoden und-Eigenschaften in regulären Textvorlagen verwenden, aber nicht in *vorverarbeiteten* Textvorlagen.

## <a name="obtain-access-to-the-host"></a>Zugriff auf den Host erhalten

Um auf den Host zuzugreifen, legen Sie `hostspecific="true"` in der `template`-Direktive fest. Nun können Sie `this.Host` mit dem Typ [itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))verwenden. Der [itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) -Typ enthält Member, die Sie zum Auflösen von Dateinamen und Protokoll Fehlern verwenden können, z. b.

### <a name="resolve-file-names"></a>Auflösen von Dateinamen

Verwenden Sie `this.Host.ResolvePath()`, um den vollständigen Pfad einer Datei relativ zur Textvorlage zu finden.

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

In diesem Beispiel werden Nachrichten protokolliert, wenn Sie die Vorlage transformieren. Wenn es sich bei dem Host um Visual Studio handelt, werden die Fehler der **Fehlerliste**hinzugefügt.

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

## <a name="use-the-visual-studio-api"></a>Verwenden der Visual Studio-API

Wenn Sie eine Textvorlage in Visual Studio ausführen, können Sie `this.Host` verwenden, um auf die von Visual Studio bereitgestellten Dienste und alle Pakete oder Erweiterungen zuzugreifen, die geladen werden.

Legen Sie hostspecific = "true" fest, und wandeln Sie `this.Host` in <xref:System.IServiceProvider>.

In diesem Beispiel wird die Visual Studio-API (<xref:EnvDTE.DTE>) als Dienst abgerufen:

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

## <a name="use-hostspecific-with-template-inheritance"></a>Verwenden von hostspecific mit Vorlagen Vererbung

Geben Sie `hostspecific="trueFromBase"` an, wenn Sie auch das `inherits`-Attribut verwenden, und wenn Sie von einer Vorlage erben, die `hostspecific="true"` angibt. Wenn Sie dies nicht tun, erhalten Sie möglicherweise eine Compilerwarnung, dass die Eigenschaft `Host` zweimal deklariert wurde.