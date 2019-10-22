---
title: 'Exemplarische Vorgehensweise: Debuggen einer Text Vorlage, die auf ein Modell zugreift Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7dc591451b314d5ebac10d30cc89d9498d70f96b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659267"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Exemplarische Vorgehensweise: Debuggen einer Textvorlage, die auf ein Modell zugreift
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Textvorlagen in einer domänenspezifischen Sprachlösung ändern oder hinzufügen, treten möglicherweise Fehler auf, wenn die Engine die Vorlage in den Quellcode umwandelt oder den generierten Code kompiliert. In der folgenden exemplarischen Vorgehensweise werden einige Dinge veranschaulicht, die Sie zum Debuggen einer Textvorlage ausführen können.

> [!NOTE]
> Weitere Informationen zu Textvorlagen im Allgemeinen finden Sie unter [Code Generierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md). Weitere Informationen zum Debuggen von Textvorlagen finden Sie unter Exemplarische Vorgehensweise [: Debuggen einer Textvorlage](https://msdn.microsoft.com/library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).

## <a name="creating-a-domain-specific-language-solution"></a>Erstellen einer domänenspezifischen Sprachlösung
 In diesem Verfahren erstellen Sie eine domänenspezifische Sprachlösung mit folgenden Merkmalen:

- Name: "tbuggingtestlanguage"

- Lösungs Vorlage: minimale Sprache

- Dateierweiterung:. ddd

- Firmenname: fabrikam

  Weitere Informationen zum Erstellen einer domänenspezifischen Sprachlösung finden Sie unter Gewusst [wie: Erstellen einer domänenspezifischen Sprachlösung](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Erstellen einer Textvorlage
 Fügen Sie der Projekt Mappe eine Textvorlage hinzu.

#### <a name="to-create-a-text-template"></a>So erstellen Sie eine Textvorlage

1. Erstellen Sie die Projekt Mappe, und starten Sie Sie im Debugger. (Klicken Sie im Menü **Erstellen** auf Projekt Mappe **neu erstellen**, und klicken Sie dann im Menü **Debuggen** auf **Debugging starten**.) Das debugprojekt wird durch eine neue Instanz von Visual Studio geöffnet.

2. Fügen Sie dem debugprojekt eine Textdatei mit dem Namen `DebugTest.tt` hinzu.

3. Stellen Sie sicher, dass die Eigenschaft **benutzerdefiniertes Tool** von DebugTest.tt auf `TextTemplatingFileGenerator` festgelegt ist.

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Debugdirektiven, die auf ein Modell aus einer Textvorlage zugreifen
 Bevor Sie aus den Anweisungen und Ausdrücken in einer Textvorlage auf ein Modell zugreifen können, müssen Sie zuerst einen generierten Direktivenprozessor aufrufen. Wenn Sie den generierten Direktivenprozessor aufrufen, werden die Klassen in Ihrem Modell dem Textvorlagen Code als Eigenschaften zur Verfügung gestellt. Weitere Informationen finden Sie unter [zugreifen auf Modelle aus Text Vorlagen](../modeling/accessing-models-from-text-templates.md).

 In den folgenden Prozeduren debuggen Sie einen falschen Direktivennamen und einen falschen Eigenschaftsnamen.

#### <a name="to-debug-an-incorrect-directive-name"></a>So debuggen Sie einen falschen Anweisungs Namen

1. Ersetzen Sie den Code in DebugTest.tt durch den folgenden Code:

    > [!NOTE]
    > Der Code enthält einen Fehler. Sie führen den Fehler ein, um ihn zu debuggen.

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

2. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf DebugTest.tt, und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**.

     Im Fenster **Fehlerliste** wird dieser Fehler angezeigt:

     **Der Prozessor mit dem Namen "debuggingtestlanguagedirectiveprocessor" unterstützt die Direktive mit dem Namen "modelroot" nicht. Die Transformation wird nicht ausgeführt.**

     In diesem Fall enthält der direktivenaufruame einen falschen Direktivennamen. Sie haben `modelRoot` als Direktivenname angegeben, aber der korrekte Direktivenname ist `DebuggingTestLanguage`.

3. Doppelklicken Sie auf den Fehler im Fenster **Fehlerliste** , um zum Code zu springen.

4. Um den Code zu korrigieren, ändern Sie den Direktivennamen in `DebuggingTestLanguage`.

     Die Änderung wird hervorgehoben.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf DebugTest.tt, und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**.

     Nun transformiert das System die Textvorlage und generiert die entsprechende Ausgabedatei. Im Fenster **Fehlerliste** werden keine Fehler angezeigt.

#### <a name="to-debug-an-incorrect-property-name"></a>So debuggen Sie einen falschen Eigenschaftsnamen

1. Ersetzen Sie den Code in DebugTest.tt durch den folgenden Code:

    > [!NOTE]
    > Der Code enthält einen Fehler. Sie führen den Fehler ein, um ihn zu debuggen.

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

2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf DebugTest.tt, und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**.

     Das Fenster **Fehlerliste** wird angezeigt, und es wird einer der folgenden Fehler angezeigt:

     (C#)

     **Die Transformation wird kompiliert: Microsoft. VisualStudio. TextTemplating \<GUID >. "Generatedtexttransform" enthält keine Definition für "examplemodel".**

     (Visual Basic)

     **Die Transformation "examplemodel" ist kein Member von "Microsoft. VisualStudio. TextTemplating \<GUID >. Generatedtexttransformation '.**

     In diesem Fall enthält der Textvorlagen Code einen falschen Eigenschaftsnamen. Sie haben `ExampleModel` als Eigenschaftsnamen angegeben, aber der richtige Eigenschaftsname ist `LibraryModel`. Den richtigen Eigenschaftsnamen finden Sie im bereitgestellten Parameter, wie im folgenden Code gezeigt:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Doppelklicken Sie auf den Fehler im Fenster Fehlerliste, um zum Code zu springen.

4. Um den Code zu korrigieren, ändern Sie den Eigenschaftsnamen in `LibraryModel` im Textvorlagen Code.

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

5. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf DebugTest.tt, und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**.

     Nun transformiert das System die Textvorlage und generiert die entsprechende Ausgabedatei. Im Fenster **Fehlerliste** werden keine Fehler angezeigt.
