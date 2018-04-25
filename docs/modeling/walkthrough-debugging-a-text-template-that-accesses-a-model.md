---
title: 'Exemplarische Vorgehensweise: Debuggen einer Textvorlage, die auf ein Modell zugreift'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: afa61e3d6158e5651fdc88969270a3bcf3af63c5
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Exemplarische Vorgehensweise: Debuggen einer Textvorlage, die auf ein Modell zugreift
Beim Ändern oder Hinzufügen von Textvorlagen in einer Projektmappe domänenspezifische Sprache, möglicherweise Fehler angezeigt werden, wenn das Modul die Vorlage auf den Quellcode oder transformiert bei der Kompilierung des generierten Codes. Die folgende exemplarische Vorgehensweise veranschaulicht einige der Dinge, die Sie ausführen können, um das Debuggen einer Textvorlage.

> [!NOTE]
>  Weitere Informationen zu Vorlagen im Allgemeinen finden Sie unter [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md). Weitere Informationen zum Debuggen von Textvorlagen finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer Textvorlage](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).

## <a name="creating-a-domain-specific-language-solution"></a>Erstellen einer Projektmappe einer domänenspezifischen Sprache
 In diesem Verfahren erstellen Sie eine domänenspezifische Sprache-Lösung, die über die folgenden Eigenschaften verfügt:

-   Name: DebuggingTestLanguage

-   Projektmappenvorlage: minimale Sprache

-   Dateierweiterung: .ddd

-   Firmenname: Fabrikam

 Weitere Informationen zum Erstellen einer Lösung einer domänenspezifischen Sprache finden Sie unter [Vorgehensweise: Erstellen einer domänenspezifischen Sprache Lösung](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Erstellen einer Textvorlage
 Fügen Sie eine Textvorlage zur Projektmappe hinzu.

#### <a name="to-create-a-text-template"></a>So erstellen eine Textvorlage

1.  Erstellen Sie die Projektmappe, und anschließend im Debugger auszuführen. (Auf der **erstellen** im Menü klicken Sie auf **Projektmappe neu erstellen**, und klicken Sie dann auf die **Debuggen** im Menü klicken Sie auf **Debuggen**.) Eine neue Instanz von Visual Studio öffnet das Debugging-Projekt.

2.  Fügen Sie eine Textdatei mit dem Namen `DebugTest.tt` zum Projekt debuggen.

3.  Stellen Sie sicher, dass die **benutzerdefiniertes Tool** von DebugTest.tt ist-Eigenschaftensatz auf `TextTemplatingFileGenerator`.

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Debuggen von Direktiven, die ein Modell aus einer Textvorlage zugreifen
 Bevor Sie ein Modell über die Anweisungen und Ausdrücke in einer Textvorlage zugreifen können, müssen Sie zuerst einen generierten Direktivenprozessor aufrufen. Aufrufen der generierten Direktivenprozessors stellt die Klassen in Ihrem Modell zur Verfügung der Textvorlagencode als Eigenschaften. Weitere Informationen finden Sie unter [Zugriff auf Modelle über Textvorlagen](../modeling/accessing-models-from-text-templates.md).

 In den folgenden Verfahren Debuggen Sie einen falschen Namen für die Richtlinie und eine falsche Eigenschaftsnamen.

#### <a name="to-debug-an-incorrect-directive-name"></a>So debuggen Sie einen falschen Namen für die Richtlinie

1.  Ersetzen Sie den Code in "DebugTest.tt" durch den folgenden Code ein:

    > [!NOTE]
    >  Der Code enthält einen Fehler. Sie werden die Fehler eingeführt, um es zu debuggen.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2.  In **Projektmappen-Explorer**mit der rechten Maustaste auf "DebugTest.tt", und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**.

     Die **Fehlerliste** Fenster wird dieser Fehler angezeigt:

     **Der Prozessor, der mit dem Namen "DebuggingTestLanguageDirectiveProcessor" unterstützt nicht die Direktive mit dem Namen "ModelRoot". Die Transformation wird nicht ausgeführt werden.**

     In diesem Fall enthält der Richtlinie Aufruf einen falschen Namen für die Richtlinie an. Sie haben angegeben `modelRoot` wie den Direktivennamen, den richtigen Namen für die Richtlinie ist jedoch `DebuggingTestLanguage`.

3.  Doppelklicken Sie auf den Fehler in der **Fehlerliste** Fenster springen zu Code.

4.  Um den Code zu beheben, ändern Sie den Direktivennamen, `DebuggingTestLanguage`.

     Die Änderung wird hervorgehoben.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5.  In **Projektmappen-Explorer**mit der rechten Maustaste auf "DebugTest.tt", und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**.

     Nachdem das System Textvorlage transformiert und die entsprechenden Ausgabedatei generiert. Sie werden feststellen, dass alle Fehler in der **Fehlerliste** Fenster.

#### <a name="to-debug-an-incorrect-property-name"></a>So debuggen Sie einen falschen Eigenschaftsnamen

1.  Ersetzen Sie den Code in "DebugTest.tt" durch den folgenden Code ein:

    > [!NOTE]
    >  Der Code enthält einen Fehler. Sie werden die Fehler eingeführt, um es zu debuggen.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2.  In der **Projektmappen-Explorer**mit der rechten Maustaste auf "DebugTest.tt", und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**.

     Die **Fehlerliste** Fenster wird geöffnet und zeigt einen der folgenden Fehler:

     (C#)

     **Kompilieren von Transformation: Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation "enthält keine Definition für 'ExampleModel'**

     (Visual Basic)

     **Kompilieren von Transformation: "ExampleModel" ist kein Mitglied von "Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation ".**

     In diesem Fall enthält der Textvorlagencode einen falschen Eigenschaftsnamen. Sie haben angegeben `ExampleModel` wie den Namen der Eigenschaft, jedoch die entsprechende Eigenschaft Name ist `LibraryModel`. Finden Sie in der richtigen Eigenschaftsname der Parameter enthält, wie im folgenden Code gezeigt:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3.  Doppelklicken Sie auf den Fehler in das Fenster "Fehlerliste" auf den Code zu springen.

4.  Um den Code zu beheben, ändern Sie den Namen der Eigenschaft, um `LibraryModel` im Textvorlagencode.

     Die Änderungen werden hervorgehoben.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.LibraryModel #>
    <#
    foreach (ExampleElement element in this.LibraryModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.LibraryModel #>
    <#
    For Each element as ExampleElement in Me.LibraryModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

5.  In **Projektmappen-Explorer**mit der rechten Maustaste auf "DebugTest.tt", und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**.

     Nachdem das System Textvorlage transformiert und die entsprechenden Ausgabedatei generiert. Sie werden feststellen, dass alle Fehler in der **Fehlerliste** Fenster.