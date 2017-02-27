---
title: "Walkthrough: Creating an Inline Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, tutorial"
  - "MSBuild, tasks"
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Walkthrough: Creating an Inline Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild\-Aufgaben werden in der Regel durch Kompilieren einer Klasse erstellt, die die <xref:Microsoft.Build.Framework.ITask>\-Schnittstelle implementiert.  Seit .NET Framework Version 4 können Sie Aufgaben inline in der Projektdatei erstellen.  Zum Hosten der Aufgabe müssen Sie keine separate Assembly erstellen.  Weitere Informationen finden Sie unter [Inline Tasks](../msbuild/msbuild-inline-tasks.md).  
  
 In dieser exemplarischen Vorgehensweise wird das Erstellen und Ausführen dieser Inlineaufgaben erläutert:  
  
-   Eine Aufgabe, der keine Eingabe\- oder Ausgabeparameter zugewiesen sind.  
  
-   Eine Aufgabe, der ein einzelner Eingabeparameter, aber kein Ausgabeparameter zugewiesen ist.  
  
-   Eine Aufgabe, der zwei Eingabeparameter und ein Ausgabeparameter, der eine MSBuild\-Eigenschaft zurückgibt, zugewiesen sind.  
  
-   Eine Aufgabe, der zwei Eingabeparameter und ein Ausgabeparameter, der ein MSBuild\-Element zurückgibt, zugewiesen sind.  
  
 Zum Erstellen und Ausführen der Aufgaben verwenden Sie Visual Studio und das Fenster **Visual Studio\-Eingabeaufforderung** wie folgt:  
  
-   Erstellen Sie in Visual Studio eine MSBuild\-Projektdatei.  
  
-   Ändern Sie die Projektdatei in Visual Studio, um die Inlineaufgabe zu erstellen.  
  
-   Erstellen Sie im **Eingabeaufforderungsfenster** das Projekt, und untersuchen Sie die Ergebnisse.  
  
## Erstellen und Ändern eines MSBuild\-Projekts  
 Das Visual Studio\-Projektsystem beruht auf MSBuild.  Daher können Sie in Visual Studio eine Buildprojektdatei erstellen.  In diesem Abschnitt erstellen Sie eine Visual C\#\-Projektdatei.  \(Stattdessen können Sie auch eine Visual Basic\-Projektdatei erstellen.  Im Kontext dieses Lernprogramms ist der Unterschied zwischen den zwei Projektdateien marginal.\)  
  
#### So erstellen und ändern Sie eine Projektdatei  
  
1.  Klicken Sie in Visual Studio im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** den Projekttyp Visual C\# und dann die Vorlage **Windows Forms\-Anwendung** aus.  Geben Sie im Feld **Name** die Zeichenfolge `InlineTasks` ein.  Geben Sie einen **Speicherort** für die Projektmappe ein, z. B. `D:\`.  Stellen Sie sicher, dass **Projektmappenverzeichnis erstellen** aktiviert , **Zur Quellcodeverwaltung hinzufügen** deaktiviert und **Projektmappenname** auf `InlineTasks` festgelegt ist.  
  
     Klicken Sie auf **OK**, um die neue Projektdatei zu erstellen.  
  
3.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Projektknoten InlineTasks, und klicken Sie anschließend auf **Projekt entladen**.  
  
4.  Klicken Sie erneut mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **InlineTasks.csproj bearbeiten**.  
  
     Die Projektdatei wird im Code\-Editor angezeigt.  
  
## Hinzufügen einer einfachen Hello\-Aufgabe  
 Fügen Sie der Projektdatei nun eine einfache Aufgabe hinzu, mit der die Nachricht "Hello, world\!" anzeigt wird. Fügen Sie auch ein standardmäßiges TestBuild\-Ziel hinzu, um die Aufgabe aufzurufen.  
  
#### So fügen Sie eine einfache Hello\-Aufgabe hinzu  
  
1.  Ändern Sie im `Project`\-Stammknoten das `DefaultTargets`\-Attribut in `TestBuild`. Der resultierende `Project`\-Knoten sollte dem folgenden Beispiel ähneln:  
  
     `<Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">`  
  
2.  Fügen Sie der Projektdatei vor dem `</Project>`\-Tag die folgende Inlineaufgabe und das folgende Ziel hinzu.  
  
    ```  
    <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
      <ParameterGroup />  
      <Task>  
        <Code Type="Fragment" Language="cs">  
          Log.LogMessage("Hello, world!", MessageImportance.High);  
        </Code>  
      </Task>  
    </UsingTask>  
    <Target Name="TestBuild">  
      <Hello />  
    </Target>  
    ```  
  
3.  Speichern Sie die Projektdatei.  
  
 In diesem Code wird die Inlineaufgabe Hello ohne Parameter, Verweise oder `Using`\-Anweisungen erstellt.  Die Hello\-Aufgabe enthält nur eine einzelne Codezeile, die auf dem Standardprotokollierungsgerät, in der Regel dem Konsolenfenster, eine Hello\-Nachricht anzeigt.  
  
### Ausführen der Hello\-Aufgabe  
 Führen Sie MSBuild im **Eingabeaufforderungsfenster** aus, um die Hello\-Aufgabe zu erstellen und das TestBuild\-Ziel für deren Aufruf zu verarbeiten.  
  
##### So führen Sie die Hello\-Aufgabe aus  
  
1.  Klicken Sie auf **Start** und auf **Alle Programme**, suchen Sie den Ordner **Visual Studio Tools**, und klicken Sie auf **Visual Studio\-Eingabeaufforderung**.  
  
2.  Suchen Sie im **Eingabeaufforderungsfenster** den Ordner mit der Projektdatei, in diesem Fall, D:\\InlineTasks\\InlineTasks\\.  
  
3.  Geben Sie **msbuild** ohne Befehlsschalter ein, und drücken Sie dann die EINGABETASTE.  Standardmäßig wird so die Datei InlineTasks.csproj erstellt und das Standardziel TestBuild verarbeitet, das die Hello\-Aufgabe aufruft.  
  
4.  Überprüfen Sie die Ausgabe im **Eingabeaufforderungsfenster**.  Die folgende Zeile sollte angezeigt werden:  
  
     `Hello, world!`  
  
    > [!NOTE]
    >  Wenn die Hello\-Nachricht nicht angezeigt wird, speichern Sie die Projektdatei erneut, und führen Sie dann die Hello\-Aufgabe aus.  
  
 Durch Wechsel zwischen Code\-Editor und dem **Eingabeaufforderungsfenster** können Sie die Projektdatei ändern und die Ergebnisse schnell anzeigen.  
  
## Definieren der Echo\-Aufgabe  
 Erstellen Sie eine Inlineaufgabe, die einen Zeichenfolgenparameter akzeptiert und die Zeichenfolge auf dem Standardprotokollierungsgerät anzeigt.  
  
#### So definieren Sie die Echo\-Aufgabe  
  
1.  Ersetzen Sie im Code\-Editor die Hello\-Aufgabe und das Ziel TestBuild durch den folgenden Code.  
  
    ```  
    <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
      <ParameterGroup>  
        <Text Required="true" />  
      </ParameterGroup>  
      <Task>  
        <Code Type="Fragment" Language="cs">  
          Log.LogMessage(Text, MessageImportance.High);  
        </Code>  
      </Task>  
    </UsingTask>  
    <Target Name="TestBuild">  
      <Echo Text="Greetings!" />  
    </Target>  
    ```  
  
2.  Geben Sie im **Eingabeaufforderungsfenster** die Zeichenfolge **msbuild** ohne Befehlsschalter ein, und drücken Sie dann EINGABETASTE.  Standardmäßig wird damit das Standardziel TestBuild verarbeitet, das die Echo\-Aufgabe aufruft.  
  
3.  Überprüfen Sie die Ausgabe im **Eingabeaufforderungsfenster**.  Die folgende Zeile sollte angezeigt werden:  
  
     `Greetings!`  
  
 In diesem Code wird die Inlineaufgabe Echo mit nur einem erforderlichen Eingabeparameter, Text, definiert.  Standardmäßig sind Parameter vom Typ System.String.  Der Wert des Text\-Parameters wird festgelegt, wenn das Ziel TestBuild die Echo\-Aufgabe aufruft.  
  
## Definieren der Adder\-Aufgabe  
 Erstellen Sie eine Inlineaufgabe, mit der zwei ganzzahlige Parameter hinzufügt werden und deren Summe als MSBuild\-Eigenschaft ausgegeben wird.  
  
#### So definieren Sie die Adder\-Aufgabe  
  
1.  Ersetzen Sie im Code\-Editor die Echo\-Aufgabe und das Ziel TestBuild durch den folgenden Code.  
  
    ```  
    <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
      <ParameterGroup>  
        <A ParameterType="System.Int32" Required="true" />  
        <B ParameterType="System.Int32" Required="true" />  
        <C ParameterType="System.Int32" Output="true" />  
      </ParameterGroup>  
      <Task>  
        <Code Type="Fragment" Language="cs">  
          C = A + B;  
        </Code>  
      </Task>  
    </UsingTask>    
    <Target Name="TestBuild">  
      <Adder A="4" B="5">  
        <Output PropertyName="Sum" TaskParameter="C" />  
      </Adder>  
      <Message Text="The sum is $(Sum)" Importance="High" />  
    </Target>  
    ```  
  
2.  Geben Sie im **Eingabeaufforderungsfenster** die Zeichenfolge **msbuild** ohne Befehlsschalter ein, und drücken Sie dann EINGABETASTE.  Standardmäßig wird damit das Standardziel TestBuild verarbeitet, das die Echo\-Aufgabe aufruft.  
  
3.  Überprüfen Sie die Ausgabe im **Eingabeaufforderungsfenster**.  Die folgende Zeile sollte angezeigt werden:  
  
     `The sum is 9`  
  
 In diesem Code wird die Inlineaufgabe "Adder" mit den beiden erforderlichen ganzzahligen Eingabeparametern A und B und dem ganzzahligen Ausgabeparameter C definiert.  Die Aufgabe "Adder" fügt die zwei Eingabeparameter hinzu und gibt die Summe im Ausgabeparameter zurück.  Die Summe wird als MSBuild\-Eigenschaft `Sum` ausgegeben.  Die Werte der Eingabeparameter werden festgelegt, wenn das Ziel TestBuild die Adder\-Aufgabe aufruft.  
  
## Definieren der RegX\-Aufgabe  
 Erstellen Sie eine Inlineaufgabe, die eine Elementgruppe und einen regulären Ausdruck akzeptiert sowie eine Liste aller Elemente mit Dateiinhalten zurückgibt, die mit dem Ausdruck übereinstimmen.  
  
#### So definieren Sie die RegX\-Aufgabe  
  
1.  Ersetzen Sie im Code\-Editor die Adder\-Aufgabe und das Ziel TestBuild durch den folgenden Code.  
  
    ```  
    <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
      <ParameterGroup>  
        <Expression Required="true" />  
        <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
        <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />  
      </ParameterGroup>  
      <Task>  
        <Using Namespace="System.Text.RegularExpressions"/>  
        <Code Type="Fragment" Language="cs">  
    <![CDATA[  
          if (Files.Length > 0)  
          {  
            Result = new TaskItem[Files.Length];  
            for (int i = 0; i < Files.Length; i++)  
            {  
              ITaskItem item = Files[i];  
              string path = item.GetMetadata("FullPath");  
              using(StreamReader rdr = File.OpenText(path))  
              {  
                if (Regex.Match(rdr.ReadToEnd(), Expression).Success)  
                {  
                  Result[i] = new TaskItem(item.ItemSpec);  
                }  
              }  
            }  
          }  
    ]]>  
        </Code>  
      </Task>  
    </UsingTask>    
    <Target Name="TestBuild">  
      <RegX Expression="public|protected" Files="@(Compile)">  
        <Output ItemName="MatchedFiles" TaskParameter="Result" />  
      </RegX>  
      <Message Text="Input files: @(Compile)" Importance="High" />  
      <Message Text="Matched files: @(MatchedFiles)" Importance="High" />  
    </Target>  
    ```  
  
2.  Geben Sie im **Eingabeaufforderungsfenster** die Zeichenfolge **msbuild** ohne Befehlsschalter ein, und drücken Sie dann EINGABETASTE.  Standardmäßig wird damit das Standardziel TestBuild verarbeitet, das die RegX\-Aufgabe aufruft.  
  
3.  Überprüfen Sie die Ausgabe im **Eingabeaufforderungsfenster**.  Die folgenden Zeilen sollten angezeigt werden:  
  
     `Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs`  
  
     `Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs`  
  
 In diesem Code wird die Inlineaufgabe RegX mit den folgenden drei Parametern definiert:  
  
-   `Expression` ist ein erforderlicher Eingabeparameter vom Typ Zeichenfolge mit einem Wert, der mit dem gesuchten regulären Ausdruck übereinstimmt.  In diesem Beispiel stimmt der Ausdruck mit den Wörtern "public" oder "protected" überein.  
  
-   `Files` ist ein erforderlicher Eingabeparameter vom Typ Elementliste, der eine Liste von Dateien als Wert besitzt, die nach der Übereinstimmung durchsucht werden soll.  In diesem Beispiel ist `Files` auf das `Compile`\-Element festgelegt, das die Projektquelldateien aufführt.  
  
-   `Result` ist ein Ausgabeparameter, der eine Liste von Dateien als Wert besitzt, deren Inhalt mit dem regulären Ausdruck übereinstimmt.  
  
 Der Wert der Eingabeparameter wird festgelegt, wenn das Ziel TestBuild die RegX\-Aufgabe aufruft.  Die RegX\-Aufgabe liest jede Datei und gibt die Liste der Dateien zurück, die mit dem regulären Ausdruck übereinstimmen.  Diese Liste wird als `Result`\-Ausgabeparameter zurückgegeben, der als `MatchedFiles`\-Element von MSBuild ausgegeben wird.  
  
### Behandeln reservierter Zeichen  
 Der MSBuild\-Parser verarbeitet Inlineaufgaben als XML.  Zeichen, deren Bedeutung XML in reserviert ist, z. B."\<" und"\>", werden erkannt und behandelt, als ob es sich um XML und nicht um .NET\-Quellcode handelte.  Wenn Sie die reservierten Zeichen in Codeausdrücken einfügen möchten, z. B. `Files.Length > 0`, schreiben Sie das `Code`\-Element wie folgt so, dass sich dessen Inhalt in einem CDATA\-Ausdruck befindet:  
  
 `<Code Type="Fragment" Language="cs">`  
  
 `<![CDATA[`  
  
 `// Your code goes here.`  
  
 `]]>`  
  
 `</Code>`  
  
## Siehe auch  
 [Inline Tasks](../msbuild/msbuild-inline-tasks.md)   
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Targets](../msbuild/msbuild-targets.md)