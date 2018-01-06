---
title: 'Exemplarische Vorgehensweise: Verbinden von einem Host auf einen generierten Direktivenprozessor | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: "47"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 26903dad4c1218d0d9ba389322351eb629f6f31a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>Exemplarische Vorgehensweise: Verbinden eines Hosts mit einem generierten Direktivenprozessor
Sie können einen eigenen Host schreiben, der Textvorlagen verarbeitet. Ein einfacher benutzerdefinierter Host wird veranschaulicht, [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md). Erweitern Sie die diesem Host zum Hinzufügen von Funktionen, z. B. das Generieren von mehreren Ausgabedateien.  
  
 In dieser exemplarischen Vorgehensweise erweitern Sie Ihre benutzerdefinierten Host, damit sie Textvorlagen unterstützt, die Direktivenprozessoren aufrufen. Wenn Sie eine domänenspezifische Sprache definieren, generiert er eine *Direktivenprozessor* für das Domänenmodell. Die Direktivenprozessor erleichtert es Benutzern Vorlagen schreiben, die Zugriff auf das Modell, mindert die Notwendigkeit, schreiben die Assembly und Importieren von Richtlinien in den Vorlagen.  
  
> [!WARNING]
>  Diese exemplarische Vorgehensweise basiert auf [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md). Durchführen Sie in dieser exemplarischen Vorgehensweise zunächst.  
  
 Diese exemplarische Vorgehensweise umfasst die folgenden Aufgaben:  
  
-   Mithilfe von [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] einen Direktivenprozessor generieren, die auf ein Domänenmodell basiert.  
  
-   Herstellen einer Verbindung eines benutzerdefinierten Textvorlagenhosts zum generierten Direktivenprozessor.  
  
-   Testen des benutzerdefinierten Hosts mit der generierten Direktivenprozessor.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zur Definition einer DSL müssen folgende Komponenten installiert sein:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.Microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Visual Studio Visualization and Modeling SDK||  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
 Darüber hinaus benötigen Sie im erstellten benutzerdefinierten Textvorlagentransformation [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Domänenspezifische Sprachtools verwenden generiert einen Direktivenprozessor  
 In dieser exemplarischen Vorgehensweise verwenden Sie den einer domänenspezifischen Sprache-Designer-Assistenten, eine domänenspezifische Sprache für die Projektmappe DSLMinimalTest erstellen.  
  
#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>Domänenspezifische Sprachtools verwenden, um einen Direktivenprozessor generieren, der auf ein Domänenmodell basiert  
  
1.  Erstellen Sie eine domänenspezifische Sprache-Lösung, die über die folgenden Eigenschaften verfügt:  
  
    -   Name: DSLMinimalTest  
  
    -   Projektmappenvorlage: minimale Sprache  
  
    -   Dateierweiterung: Min.  
  
    -   Firmenname: Fabrikam  
  
     Weitere Informationen zum Erstellen einer Lösung einer domänenspezifischen Sprache finden Sie unter [Vorgehensweise: Erstellen einer domänenspezifischen Sprache Lösung](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
2.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
    > [!IMPORTANT]
    >  Dieser Schritt generiert des Direktivenprozessors komplizierter, und fügt den Schlüssel für die sie in der Registrierung hinzu.  
  
3.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
     Eine zweite Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird geöffnet.  
  
4.  In der experimentellen Build in **Projektmappen-Explorer**, doppelklicken Sie auf die Datei **sample.min**.  
  
     Die Datei wird im Designer geöffnet. Beachten Sie, dass das Modell zwei Elemente, ExampleElement1 und ExampleElement2 und einen Link zwischen ihnen verfügt.  
  
5.  Schließen Sie die zweite Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
6.  Speichern Sie die Projektmappe, und schließen Sie dann den einer domänenspezifischen Sprache-Designer.  
  
## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Herstellen einer Verbindung eines benutzerdefinierten Textvorlagenhosts, einen Direktivenprozessor  
 Nach dem Generieren des Direktivenprozessors komplizierter, verbinden Sie den Direktivenprozessor und den benutzerdefinierten Textvorlagenhosts, die Sie erstellt haben [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>Die Verbindung zum generierten Direktivenprozessor ein benutzerdefinierten Textvorlagenhosts  
  
1.  Öffnen Sie die Projektmappe "CustomHost".  
  
2.  Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen** .  
  
     Die **Verweis hinzufügen** Dialogfeld wird geöffnet, mit der **.NET** Registerkarte angezeigt.  
  
3.  Fügen Sie die folgenden Verweise hinzu:  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0  
  
4.  Fügen Sie am oberen Rand der Datei "Program.cs" oder "Module1.vb" die folgende Codezeile hinzu:  
  
    ```csharp  
    using Microsoft.Win32;  
    ```  
  
    ```vb  
    Imports Microsoft.Win32  
    ```  
  
5.  Suchen Sie den Code für die Eigenschaft `StandardAssemblyReferences`, und Ersetzen Sie ihn durch den folgenden Code:  
  
    > [!NOTE]
    >  In diesem Schritt fügen Sie Verweise auf die Assemblys, die von der generierten Direktivenprozessor erforderlich sind, die dem Host unterstützt.  
  
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
  
6.  Suchen Sie den Code für die Funktion `ResolveDirectiveProcessor`, und Ersetzen Sie ihn durch den folgenden Code:  
  
    > [!IMPORTANT]
    >  Dieser Code enthält hartcodierte Verweise auf den Namen des generierten Direktivenprozessors auf dem Sie eine Verbindung herstellen möchten. Sie problemlos womöglich dies allgemeineren, in diesem Fall sucht nach allen Direktivenprozessoren aufgeführt, die in der Registrierung und versucht, eine Übereinstimmung zu finden. In diesem Fall würde der Host alle generierten Direktivenprozessor arbeiten.  
  
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
  
7.  Auf der **Datei** Menü klicken Sie auf **alle speichern**.  
  
8.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
## <a name="testing-the-custom-host-with-the-directive-processor"></a>Testen des benutzerdefinierten Hosts mit der Direktivenprozessor  
 Zum Testen der benutzerdefinierten Textvorlagenhosts müssen Sie zuerst eine Textvorlage schreiben, die den generierten Direktivenprozessor aufruft. Klicken Sie dann den benutzerdefinierten Host ausführen, den Namen der Textvorlage an diesen weitergegeben und stellen Sie sicher, dass die Anweisung ordnungsgemäß verarbeitet wird.  
  
#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>So erstellen Sie eine Textvorlage zum Testen des benutzerdefinierten Hosts  
  
1.  Erstellen Sie eine Textdatei, und nennen Sie es `TestTemplateWithDP.tt`. Sie können einem beliebigen Texteditor wie Editor zum Erstellen der Datei verwenden.  
  
2.  Fügen Sie folgenden Text in der Textdatei ein:  
  
    > [!NOTE]
    >  Die Programmiersprache der Textvorlage muss nicht mit den benutzerdefinierten Host übereinstimmen.  
  
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
  
3.  Ersetzen Sie im Code, \<IHR Pfad > durch den Pfad der Datei Sample.min aus der Design-spezifische Sprache, die Sie im ersten Verfahren erstellt haben.  
  
4.  Speichern und schließen Sie die Datei.  
  
#### <a name="to-test-the-custom-host"></a>So testen Sie den benutzerdefinierten Host  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Geben Sie den Pfad der ausführbaren Datei für den benutzerdefinierten Host ein, drücken Sie aber noch nicht die EINGABETASTE.  
  
     Beispiel:  
  
     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`  
  
    > [!NOTE]
    >  Anstatt die Adresse einzugeben, können Sie zu der Datei CustomHost.exe Navigieren in **Windows Explorer**, und klicken Sie dann die Datei in das Eingabeaufforderungsfenster ziehen.  
  
3.  Geben Sie ein Leerzeichen ein.  
  
4.  Geben Sie den Pfad der Textvorlagendatei ein, und drücken Sie dann die EINGABETASTE.  
  
     Beispiel:  
  
     `<YOUR PATH>TestTemplateWithDP.txt`  
  
    > [!NOTE]
    >  Anstatt die Adresse einzugeben, können Sie zu der Datei TestTemplateWithDP.txt Navigieren in **Windows Explorer**, und klicken Sie dann die Datei in das Eingabeaufforderungsfenster ziehen.  
  
     Die benutzerdefinierte hostanwendung wird ausgeführt und startet den Textvorlagen-Transformationsprozess ab.  
  
5.  In **Windows Explorer**, navigieren Sie zu dem Ordner, die Datei TestTemplateWithDP.txt enthält.  
  
     Der Ordner enthält auch die Datei TestTemplateWithDP1.txt.  
  
6.  Öffnen Sie diese Datei, um die Ergebnisse der Textvorlagentransformation anzuzeigen.  
  
     Die Ergebnisse der die generierte Textausgabe wird angezeigt und sollte wie folgt aussehen:  
  
    ```  
    Text Template Host Test  
  
    Box: ExampleElement1  
    Linked to: ExampleElement2  
  
    Box: ExampleElement2  
    Linked from: ExampleElement1  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Textvorlagenhosts](../modeling/walkthrough-creating-a-custom-text-template-host.md)
