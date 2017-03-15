---
title: 'Exemplarische Vorgehensweise: Debuggen einer Textvorlage, die auf ein Modell zugreift | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 7bbe2b592dc315bc0885e1f1ca4c890e4e66255d
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Exemplarische Vorgehensweise: Debuggen einer Textvorlage, die auf ein Modell zugreift
Beim Ändern oder Hinzufügen von Textvorlagen in einer domänenspezifischen Sprache-Lösung, möglicherweise Fehler ausgegeben, wenn es sich bei das Modul transformiert die Vorlage auf den Quellcode oder beim Kompilieren des generierten Codes. Die folgende exemplarische Vorgehensweise veranschaulicht einige der Dinge, die Sie ausführen können, um das Debuggen einer Textvorlage.  
  
> [!NOTE]
>  Weitere Informationen zu Vorlagen im Allgemeinen finden Sie unter [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md). Weitere Informationen zum Debuggen von Textvorlagen finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer Textvorlage](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).  
  
## <a name="creating-a-domain-specific-language-solution"></a>Erstellen einer domänenspezifischen Sprache-Lösung  
 In diesem Verfahren erstellen Sie eine domänenspezifische Sprache-Lösung, die folgende Merkmale aufweist:  
  
-   Name: DebuggingTestLanguage  
  
-   Projektmappenvorlage: minimale Sprache  
  
-   Dateierweiterung: .ddd  
  
-   Firmenname: Fabrikam  
  
 Weitere Informationen zum Erstellen einer domänenspezifischen Sprache-Lösung finden Sie unter [Gewusst wie: Erstellen einer domänenspezifischen Sprachlösung](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="creating-a-text-template"></a>Erstellen einer Textvorlage  
 Fügen Sie der Projektmappe eine Textvorlage.  
  
#### <a name="to-create-a-text-template"></a>Erstellen Sie eine Textvorlage  
  
1.  Erstellen Sie die Projektmappe, und starten Sie ihn im Debugger ausführen. (Auf der **erstellen** Menü klicken Sie auf **Projektmappe neu erstellen**, und klicken Sie dann auf die **Debuggen** Menü klicken Sie auf **Debuggen starten**.) Eine neue Instanz von Visual Studio öffnet das Projekt debuggen.  
  
2.  Fügen Sie eine Textdatei namens `DebugTest.tt` für das Projekt debuggen.  
  
3.  Stellen Sie sicher, dass die **benutzerdefiniertes Tool** von "DebugTest.tt"-Eigenschaft auf festgelegt ist `TextTemplatingFileGenerator`.  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Debuggen von Direktiven, die Zugriff auf ein Modell in einer Textvorlage  
 Bevor Sie ein Modell in die Anweisungen und Ausdrücke in einer Textvorlage zugreifen können, müssen Sie zunächst einen generierten Direktivenprozessor aufrufen. Aufrufen der generierten Direktivenprozessors stellt die Klassen im Modell zur Verfügung der Textvorlagencode als Eigenschaften. Weitere Informationen finden Sie unter [Zugriff auf Modelle aus Textvorlagen](../modeling/accessing-models-from-text-templates.md).  
  
 In den folgenden Verfahren Debuggen Sie einen falschen Namen für die Richtlinie und eine falsche Eigenschaftennamen.  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>So debuggen Sie einen falschen Namen für die Richtlinie  
  
1.  Ersetzen Sie den Code in "DebugTest.tt" durch den folgenden Code:  
  
    > [!NOTE]
    >  Der Code enthält einen Fehler. Sie werden den Fehler eingeführt, um es zu debuggen.  
  
    ```c#  
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
  
    ```vb#  
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
  
     Die **Fehlerliste** Fenster diese Fehlermeldung angezeigt:  
  
     **Der Prozessor mit dem Namen 'DebuggingTestLanguageDirectiveProcessor' unterstützt nicht die Direktive namens "ModelRoot". Die Transformation wird nicht ausgeführt werden.**  
  
     In diesem Fall enthält der Richtlinie Aufruf einen falschen Namen für die Richtlinie. Sie haben angegeben `modelRoot` wie den Direktivennamen, den richtigen Namen für die Richtlinie ist jedoch `DebuggingTestLanguage`.  
  
3.  Doppelklicken Sie auf den Fehler in der **Fehlerliste** Fenster, um den Code zu wechseln.  
  
4.  Um den Code zu korrigieren, ändern Sie den Direktivennamen, `DebuggingTestLanguage`.  
  
     Die Änderung wird hervorgehoben.  
  
    ```c#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  In **Projektmappen-Explorer**mit der rechten Maustaste auf "DebugTest.tt", und klicken Sie dann auf **benutzerdefiniertes Tool ausführen**.  
  
     Jetzt wird das System transformiert die Textvorlage und generiert die entsprechende Ausgabedatei. Sehen Sie keine Fehler in der **Fehlerliste** Fenster.  
  
#### <a name="to-debug-an-incorrect-property-name"></a>So debuggen Sie ein falsches Eigenschaftenname  
  
1.  Ersetzen Sie den Code in "DebugTest.tt" durch den folgenden Code:  
  
    > [!NOTE]
    >  Der Code enthält einen Fehler. Sie werden den Fehler eingeführt, um es zu debuggen.  
  
    ```c#  
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
  
    ```vb#  
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
  
     **Kompilieren von Transformation: Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation' enthält keine Definition für 'ExampleModel'**  
  
     (Visual Basic)  
  
     **Kompilieren von Transformation: 'ExampleModel' ist kein Mitglied von ' Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation'.**  
  
     In diesem Fall enthält der Textvorlagencode einen falscher Name für Eigenschaft. Sie haben angegeben `ExampleModel` als Namen der Eigenschaft, aber die korrekte Eigenschaft Name ist `LibraryModel`. Finden Sie den richtigen Eigenschaftennamen in die Parameter enthält, wie im folgenden Code gezeigt:  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  Doppelklicken Sie auf den Fehler im Fenster "Fehlerliste", um den Code zu wechseln.  
  
4.  Um den Code zu korrigieren, ändern Sie den Namen der Eigenschaft, um `LibraryModel` im Textvorlagencode.  
  
     Die Änderungen werden hervorgehoben.  
  
    ```c#  
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
  
    ```vb#  
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
  
     Jetzt wird das System transformiert die Textvorlage und generiert die entsprechende Ausgabedatei. Sehen Sie keine Fehler in der **Fehlerliste** Fenster.
