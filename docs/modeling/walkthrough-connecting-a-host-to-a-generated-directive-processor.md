---
title: 'Exemplarische Vorgehensweise: Verbinden eines Hosts mit einem generierten Direktivenprozessor'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 255c82b09e87180149756ce684f001652f4b962a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60058720"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>Exemplarische Vorgehensweise: Verbinden eines Hosts mit einem generierten Anweisungsprozessor

Sie können einen eigenen Host schreiben, der Textvorlagen verarbeitet. Ein einfacher benutzerdefinierter Host wird im veranschaulicht [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md). Sie können diesem Host zum Hinzufügen von Funktionen, z. B. das Generieren von mehreren Ausgabedateien erweitern.

In dieser exemplarischen Vorgehensweise erweitern Sie Ihren benutzerdefinierten Host, damit sie Textvorlagen unterstützt, die anweisungsprozessoren aufrufen. Wenn Sie eine domänenspezifische Sprache definieren, generiert er eine *anweisungsprozessor* für das Domänenmodell. Der anweisungsprozessor erleichtert es Benutzern Zugriff auf das Modell, mindert die Notwendigkeit, schreiben die Assembly und import-Direktiven in den Vorlagen Vorlagen schreiben.

> [!NOTE]
> Diese exemplarische Vorgehensweise baut auf [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md). Führen Sie zunächst diese exemplarischen Vorgehensweise.

Diese exemplarische Vorgehensweise umfasst die folgenden Aufgaben:

- Mithilfe von [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] einen anweisungsprozessor zu generieren, die ein Domänenmodell basiert.

- Herstellen einer Verbindung mit der generierten Direktivenprozessor ein benutzerdefinierten Textvorlagenhosts.

- Testen des benutzerdefinierten Hosts mit der generierten Direktivenprozessor an.

## <a name="prerequisites"></a>Vorraussetzungen

Zur Definition einer DSL müssen folgende Komponenten installiert sein:

| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580) |
| Visual Studio Visualization and Modeling SDK | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Darüber hinaus benötigen Sie im erstellten benutzerdefinierten Textvorlagentransformation [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Verwenden Sie Tools für domänenspezifische Sprachen, um einen Anweisungsprozessor zu generieren.

In dieser exemplarischen Vorgehensweise verwenden Sie den Domain-Specific Language-Designer-Assistenten, um eine domänenspezifische Sprache für die Lösung DSLMinimalTest zu erstellen.

1. Erstellen Sie eine domänenspezifische Sprache-Lösung, die die folgenden Merkmale aufweist:

   - Name: DSLMinimalTest

   - Lösungsvorlage: Minimal Language (Einfache Version der Sprache)

   - Dateierweiterung: Min.

   - Name des Unternehmens: Fabrikam

   Weitere Informationen zum Erstellen einer DSL-Projektmappe finden Sie unter [Vorgehensweise: Create a Domain-Specific Language Solution (Vorgehensweise: Erstellen einer Projektmappe für die domänenspezifische Sprache)](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

   > [!IMPORTANT]
   > Dieser Schritt generiert den anweisungsprozessor und den Schlüssel für sie in der Registrierung hinzugefügt.

3. Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.

    Eine zweite Instanz von Visual Studio wird geöffnet.

4. Klicken Sie im experimentellen Build in **Projektmappen-Explorer**, doppelklicken Sie auf die Datei **sample.min**.

    Die Datei wird im Designer geöffnet. Beachten Sie, dass das Modell zwei Elemente, ExampleElement1 und ExampleElement2 und einen Link zwischen ihnen.

5. Die zweite Instanz von Visual Studio zu schließen.

6. Speichern Sie die Projektmappe, und schließen Sie die domänenspezifischen Sprach-Designers.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Verbinden Sie mit einem Direktivenprozessor ein benutzerdefinierten Textvorlagenhosts

Nachdem Sie den anweisungsprozessor generiert haben, verbinden Sie den anweisungsprozessor und der benutzerdefinierten Textvorlagenhosts, die Sie in erstellt [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md).

1. Öffnen Sie die Projektmappe "CustomHost".

2. Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen** .

     Die **Verweis hinzufügen** Dialogfeld wird geöffnet, und die **.NET** angezeigt.

3. Fügen Sie die folgenden Verweise hinzu:

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. Fügen Sie am oberen Rand der Datei "Program.cs" oder "Module1.vb" die folgende Codezeile hinzu:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Suchen Sie den Code für die Eigenschaft `StandardAssemblyReferences`, und Ersetzen Sie ihn durch den folgenden Code:

    > [!NOTE]
    > In diesem Schritt fügen Sie Verweise auf die Assemblys, die von der generierten Direktivenprozessor erforderlich sind, die dem Host unterstützt werden.

    ```csharp
    //the host can provide standard assembly references
    //the engine will use these references when compiling and
    //executing the generated transformation class
    //--------------------------------------------------------------
    public IList<string> StandardAssemblyReferences
    {
        get
        {
            return new string[]
            {
                //if this host searches standard paths and the GAC
                //we can specify the assembly name like this:
                //"System"
                //since this host only resolves assemblies from the
                //fully qualified path and name of the assembly
                //this is a quick way to get the code to give us the
                //fully qualified path and name of the System assembly
                //---------------------------------------------------------
                typeof(System.Uri).Assembly.Location,
                            typeof(System.Uri).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location

            };
        }
    }
    ```

6. Suchen Sie den Code für die Funktion `ResolveDirectiveProcessor`, und Ersetzen Sie ihn durch den folgenden Code:

    > [!IMPORTANT]
    > Dieser Code enthält hartcodierte Verweise auf den Namen der generierten Direktivenprozessor, zu der Sie eine Verbindung herstellen möchten. Sie können problemlos wandle die Liste Weitere allgemeine, in diesem Fall für alle anweisungsprozessoren in der Registrierung aufgeführte und versucht, eine Übereinstimmung zu finden. In diesem Fall würde der Host mit jeder generierten Direktivenprozessor funktionieren.

    ```csharp
    //the engine calls this method based on the directives the user has
            //specified it in the text template
            //this method can be called 0, 1, or more times
            //---------------------------------------------------------------------
            public Type ResolveDirectiveProcessor(string processorName)
            {
                //check the processor name, and if it is the name of the processor the
                //host wants to support, return the type of the processor
                //---------------------------------------------------------------------
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)
                {
                    try
                    {
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))
                        {
                            if (specificKey != null)
                            {
                                List<string> names = new List<String>(specificKey.GetValueNames());
                                string classValue = specificKey.GetValue("Class") as string;
                                if (!string.IsNullOrEmpty(classValue))
                                {
                                    string loadValue = string.Empty;
                                    System.Reflection.Assembly processorAssembly = null;
                                    if (names.Contains("Assembly"))
                                    {
                                        loadValue = specificKey.GetValue("Assembly") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //the assembly must be installed in the GAC
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);
                                        }
                                    }
                                    else if (names.Contains("CodeBase"))
                                    {
                                        loadValue = specificKey.GetValue("CodeBase") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //loading local assembly
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);
                                        }
                                    }
                                    if (processorAssembly == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    Type processorType = processorAssembly.GetType(classValue);
                                    if (processorType == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    return processorType;
                                }
                            }
                        }
                    }
                    catch (Exception e)
                    {
                        //if the directive processor can not be found, throw an error
                        throw new Exception("Directive Processor not found");
                    }
                }

                //if the directive processor is not one this host wants to support
                throw new Exception("Directive Processor not supported");
            }
    ```

7. Klicken Sie im Menü **Datei** auf **Alle speichern**.

8. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

## <a name="test-the-custom-host-with-the-directive-processor"></a>Testen des benutzerdefinierten Hosts mit der Anweisungsprozessor

Zum Testen der benutzerdefinierten Textvorlagenhosts müssen Sie zuerst eine Textvorlage schreiben, die die generierte Direktivenprozessor aufruft. Klicken Sie dann Ausführen des benutzerdefinierten Hosts, den Namen der Textvorlage an die Klasse weitergeben, und stellen Sie sicher, dass die Richtlinie ordnungsgemäß verarbeitet wird.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Erstellen Sie eine Textvorlage zum Testen des benutzerdefinierten Hosts

1. Erstellen Sie eine Textdatei, und nennen Sie es `TestTemplateWithDP.tt`. Sie können einem beliebigen Texteditor wie Editor verwenden, zum Erstellen der Datei.

2. Fügen Sie folgenden Text in der Textdatei ein:

    > [!NOTE]
    > Die Programmiersprache der Textvorlage muss nicht mit der des benutzerdefinierten Hosts übereinstimmen.

    ```csharp
    Text Template Host Test

    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
    <# //this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>
    <# //uncomment this line to test that the host allows the engine to set the extension #>
    <# //@ output extension=".htm" #>

    <# //uncomment this line if you want to see the generated transformation class #>
    <# //System.Diagnostics.Debugger.Break(); #>
    <# //this code uses the results of the examplemodel directive #>
    <#
        foreach ( ExampleElement box in this.ExampleModel.Elements )
        {
            WriteLine("Box: {0}", box.Name);

            foreach (ExampleElement linkedTo in box.Targets)
            {
                WriteLine("Linked to: {0}", linkedTo.Name);
            }

            foreach (ExampleElement linkedFrom in box.Sources)
            {
                WriteLine("Linked from: {0}", linkedFrom.Name);
            }

            WriteLine("");
        }
    #>
    ```

    ```vb
    Text Template Host Test

    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>

    <# 'this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>

    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>
    <# '@ output extension=".htm" #>

    <# 'Uncomment this line if you want to see the generated transformation class. #>
    <# 'System.Diagnostics.Debugger.Break() #>

    <# 'this code uses the results of the examplemodel directive #>

    <#
       For Each box as ExampleElement In Me.ExampleModel.Elements

           WriteLine("Box: {0}", box.Name)

            For Each LinkedTo as ExampleElement In box.Targets
                WriteLine("Linked to: {0}", LinkedTo.Name)
            Next

            For Each LinkedFrom as ExampleElement In box.Sources
                WriteLine("Linked from: {0}", LinkedFrom.Name)
            Next

            WriteLine("")

       Next
    #>
    ```

3. Ersetzen Sie im Code, \<IHR Pfad > durch den Pfad der Datei Sample.min aus der Design-spezifischen Sprache, die Sie im ersten Verfahren erstellt haben.

4. Speichern und schließen Sie die Datei.

### <a name="test-the-custom-host"></a>Testen des benutzerdefinierten Hosts

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Geben Sie den Pfad der ausführbaren Datei für den benutzerdefinierten Host ein, drücken Sie aber noch nicht die EINGABETASTE.

     Beispiel:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Anstatt die Adresse einzugeben, können Sie auf die Datei CustomHost.exe durchsuchen in **Windows Explorer**, und klicken Sie dann die Datei in das Eingabeaufforderungsfenster ziehen.

3. Geben Sie ein Leerzeichen ein.

4. Geben Sie den Pfad der Textvorlagendatei ein, und drücken Sie dann die EINGABETASTE.

     Beispiel:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Anstatt die Adresse einzugeben, können Sie auf die Datei TestTemplateWithDP.txt durchsuchen in **Windows Explorer**, und klicken Sie dann die Datei in das Eingabeaufforderungsfenster ziehen.

     Die benutzerdefinierte hostanwendung wird ausgeführt und startet das Textvorlagen-Transformationsprozess ab.

5. In **Windows Explorer**, navigieren Sie zu dem Ordner, die Datei TestTemplateWithDP.txt enthält.

     Der Ordner enthält auch die Datei TestTemplateWithDP1.txt.

6. Öffnen Sie diese Datei, um die Ergebnisse der Textvorlagentransformation anzuzeigen.

     Die Ergebnisse der die generierte Textausgabe wird angezeigt und sollte wie folgt aussehen:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md)
