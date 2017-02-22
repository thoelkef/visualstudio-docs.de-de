---
title: "Design-Time Code Generation by using T4 Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, guidelines for code generation"
  - "text templates, data source model"
  - "TextTemplatingFileGenerator custom tool"
  - "Transform All Templates"
  - "text templates, getting started"
  - "Text Template project item"
  - "text templates, generating code for your application"
ms.assetid: 2774b83d-1adb-4c66-a607-746e019b80c0
caps.latest.revision: 38
caps.handback.revision: 38
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Design-Time Code Generation by using T4 Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

T4\-Entwurfszeittextvorlagen ermöglichen es Ihnen, Programmcode und andere Dateien im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt zu generieren.  In der Regel werden die Vorlagen so geschrieben, dass der Code, der gemäß den Daten aus einem *Modell* generiert wird, variiert wird.  Ein Modell ist eine Datei oder Datenbank, die wichtige Informationen zu den Anforderungen der Anwendung enthält.  
  
 In einem Modell kann z. B. ein Workflow entweder als Tabelle oder Diagramm definiert sein.  Anhand des Modells können Sie die Software generieren, die den Workflow ausführt.  Wenn sich die Anforderungen der Benutzer ändern, kann der neue Workflow problemlos mit den Benutzern besprochen werden.  Die erneute Generierung des Codes anhand des Workflows ist zuverlässiger als die manuelle Aktualisierung des Codes.  
  
> [!NOTE]
>  Ein *Modell* ist eine Datenquelle, die einen bestimmten Teil einer Anwendung beschreibt.  Ein Modell kann ein beliebiges Format in einem beliebigen Datei\- oder Datenbanktyp aufweisen.  Es muss kein bestimmtes Format besitzen, wie z. B. ein UML\-Modell oder ein domänenspezifisches Sprachmodell.  Typische Modelle werden als Tabellen oder XML\-Dateien dargestellt.  
  
 Sie sind wahrscheinlich bereits mit der Codegenerierung vertraut.  Wenn Sie Ressourcen in einer **.resx**\-Datei in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projektmappe definieren, wird automatisch ein Satz von Klassen und Methoden generiert.  Durch die Ressourcendatei können die Ressourcen einfacher und zuverlässiger bearbeitet werden als dies beim Bearbeiten der Klassen und Methoden möglich wäre.  Mithilfe von Textvorlagen können Sie Code auf die gleiche Weise aus einer selbst entworfenen Quelle generieren.  
  
 Eine Textvorlage enthält eine Mischung des Texts, den Sie generieren möchten, sowie Programmcode, der Variablenteile des Texts generiert.  Der Programmcode ermöglicht die Wiederholung oder das bedingte Auslassen von Teilen des generierten Texts.  Der generierte Text selbst kann Programmcode sein, der einen Teil der Anwendung bildet.  
  
## Erstellen einer T4\-Textvorlage für die Entwurfszeit  
  
#### So erstellen Sie eine T4\-Vorlage für die Entwurfszeit in Visual Studio  
  
1.  Erstellen Sie ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt, oder öffnen Sie ein vorhandenes Projekt.  
  
     Wählen Sie z. B. im Menü **Datei**, **Neu**, **Projekt** aus.  
  
2.  Fügen Sie dem Projekt eine Textvorlagendatei hinzu, und geben Sie diesem einen Namen mit der Erweiterung .tt.  
  
     Hierzu wählen Sie im **Projektmappen\-Explorer** im Kontextmenü des Projekts die Option **Hinzufügen**, **Neues Element** aus.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** im mittleren Bereich **Textvorlage** aus.  
  
     Die Eigenschaft **Benutzerdefiniertes Tool** der Datei ist auf **TextTemplatingFileGenerator** festgelegt.  
  
3.  Öffnen Sie die Datei.  Sie enthält bereits die folgenden Direktiven:  
  
    ```  
    <#@ template hostspecific="false" language="C#" #>  
    <#@ output extension=".txt" #>  
    ```  
  
     Wenn Sie die Vorlage einem [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Projekt hinzugefügt haben, ist das Sprachattribut auf `VB` festgelegt.  
  
4.  Fügen Sie am Ende der Datei Text hinzu.  Beispiel:  
  
    ```  
    Hello, world!  
    ```  
  
5.  Speichern Sie die Datei.  
  
     Möglicherweise wird eine **Sicherheitswarnung** angezeigt, in der Sie aufgefordert werden, die Ausführung der Vorlage zu bestätigen.  Klicken Sie auf **OK**.  
  
6.  Erweitern Sie im **Projektmappen\-Explorer** den Knoten der Vorlagendatei. Der Knoten enthält eine Datei mit der Erweiterung .txt.  Die Datei enthält den Text, der von der Vorlage generiert wird.  
  
    > [!NOTE]
    >  Wenn es sich um ein Visual Basic\-Projekt handelt, müssen Sie auf **Alle Dateien anzeigen** klicken, um die Ausgabedatei anzuzeigen.  
  
### Erneutes Generieren des Codes  
 In den folgenden Fällen wird eine Vorlage ausgeführt, wobei die untergeordnete Datei generiert wird:  
  
-   Sie bearbeiten die Vorlage und verschieben dann den Fokus auf ein anderes [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Fenster.  
  
-   Sie speichern die Vorlage.  
  
-   Klicken Sie im Menü **Build** auf **Alle Vorlagen transformieren**.  Dadurch werden alle Vorlagen in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projektmappe transformiert.  
  
-   Wählen Sie im **Projektmappen\-Explorer** im Kontextmenü jeder Datei die Option **Benutzerdefiniertes Tool ausführen** aus.  Verwenden Sie diese Methode, um eine ausgewählte Untergruppe von Vorlagen zu transformieren.  
  
 Sie können ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt auch so einrichten, dass die Vorlagen ausgeführt werden, wenn sich die von den Vorlagen gelesenen Datendateien ändern.  Weitere Informationen finden Sie unter [Automatisches erneutes Generieren des Codes](#Regenerating).  
  
## Generieren von Variablentext  
 Textvorlagen ermöglichen es Ihnen, den Inhalt der generierten Datei mithilfe von Programmcode zu verändern.  
  
#### So generieren Sie Text mithilfe von Programmcode  
  
1.  Ändern des Inhalts der `.tt`\-Datei:  
  
    ```c#  
    <#@ template hostspecific="false" language="C#" #>  
    <#@ output extension=".txt" #>  
    <#int top = 10;  
  
    for (int i = 0; i<=top; i++)   
    { #>  
       The square of <#= i #> is <#= i*i #>  
    <# } #>  
    ```  
  
    ```vb#  
    <#@ template hostspecific="false" language="VB" #>  
    <#@ output extension=".txt" #>  
    <#Dim top As Integer = 10  
  
    For i As Integer = 0 To top  
    #>  
        The square of <#= i #> is <#= i*i #>  
    <#  
    Next  
    #>  
  
    ```  
  
2.  Speichern Sie die TT\-Datei, und überprüfen Sie die generierte TXT\-Datei erneut.  Sie enthält die Quadratzahlen der Zahlen 0 bis 10.  
  
 Beachten Sie, dass Anweisungen in `<#...#>` eingeschlossen sind und einzelne Ausdrücke in `<#=...#>`.  Weitere Informationen finden Sie unter [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
 Wenn Sie den generierenden Code in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] schreiben, sollte die `template`\-Direktive `language="VB"` enthalten.  Standardmäßig ist `"C#"` festgelegt.  
  
## Debuggen einer T4\-Textvorlage für die Entwurfszeit  
 So debuggen Sie eine Textvorlage  
  
-   Fügen Sie `debug="true"` in die `template`\-Direktive ein.  Zum Beispiel:  
  
     `<#@ template debug="true" hostspecific="false" language="C#" #>`  
  
-   Legen Sie in der Vorlage Haltepunkte auf dieselbe Weise fest wie für normalen Code.  
  
-   Wählen Sie im Kontextmenü des Textvorlagendatei im Projektmappen\-Explorer **T4\-Vorlage debuggen** aus.  
  
 Die Vorlage wird ausgeführt und an den Haltepunkten angehalten.  Sie können Variablen prüfen und den Code ganz normal durchlaufen.  
  
> [!TIP]
>  Mit `debug="true"` wird die Zuordnung des generierten Codes zur Textvorlage genauer, indem mehr Direktiven zur Zeilennummerierungsdirektive in den generierten Code eingefügt werden.  Wenn Sie diese auslassen, wird die Ausführung möglicherweise durch die Haltepunkte im falschen Zustand angehalten.  
>   
>  Sie können jedoch die Klausel in der template\-Direktive lassen, auch wenn Sie nicht debuggen.  Dies verursacht nur einen sehr geringen Leistungsverlust.  
  
## Generieren von Code oder Ressourcen für die Projektmappe  
 Abhängig vom Modell können verschiedene Programmdateien generiert werden.  Ein Modell ist eine Eingabequelle wie eine Datenbank, eine Konfigurationsdatei, ein UML\- oder DSL\-Modell oder eine andere Quelle.  Normalerweise generieren Sie mehrere Programmdateien aus dem gleichen Modell.  Sie erstellen zu diesem Zweck eine Vorlagendatei für jede generierte Programmdatei und lassen das gleiche Modell von allen Vorlagen lesen.  
  
#### So generieren Sie Programmcode oder Ressourcen  
  
1.  Ändern Sie die output\-Direktive, um eine Datei des entsprechenden Typs zu generieren, z. B. .cs, .vb, .resx oder .xml.  
  
2.  Fügen Sie Code ein, durch den der benötigte Projektmappencode generiert wird.  Fügen Sie z. B. folgenden Code ein, wenn Sie drei Deklarationen für Felder für ganze Zahlen in einer Klasse generieren möchten:  
  
    ```c#  
  
                      <#@ template debug="false" hostspecific="false" language="C#" #>  
    <#@ output extension=".cs" #>  
    <# var properties = new string [] {"P1", "P2", "P3"}; #>  
    // This is generated code:  
    class MyGeneratedClass {  
    <# // This code runs in the text template:  
      foreach (string propertyName in properties)   { #>  
      // Generated code:  
      private int <#= propertyName #> = 0;  
    <# } #>  
    }  
    ```  
  
    ```vb#  
    <#@ template debug="false" hostspecific="false" language="VB" #>  
    <#@ output extension=".cs" #>  
    <# Dim properties = {"P1", "P2", "P3"} #>  
    class MyGeneratedClass {  
    <#   
       For Each propertyName As String In properties  
    #>  
      private int <#= propertyName #> = 0;  
    <#  
       Next  
    #>  
    }  
  
    ```  
  
3.  Speichern Sie die Datei, und überprüfen Sie die generierte Datei, die nun den folgenden Code enthält:  
  
    ```  
    class MyGeneratedClass {  
      private int P1 = 0;   
      private int P2 = 0;  
      private int P3 = 0;  
    }  
    ```  
  
### Generieren von Code und generierter Text  
 Wenn Sie Programmcode generieren, ist es wichtig, den Generierungscode, der in der Vorlage ausgeführt wird, nicht mit dem resultierenden generierten Code zu verwechseln, der Teil der Projektmappe wird.  Die beiden Sprachen müssen nicht identisch sein.  
  
 Das vorherige Beispiel enthält zwei Versionen.  In einer Version liegt der generierende Code in C\# vor.  In der anderen Version liegt der generierende Code in Visual Basic vor.  Der in beiden Versionen generierte Text ist jedoch identisch, und er befindet sich in einer C\#\-Klasse.  
  
 Ebenso können Sie eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Vorlage verwenden, um Code in einer beliebigen Sprache zu generieren.  Der generierte Text muss nicht in einer bestimmten Sprache vorliegen, und es muss sich nicht um Programmcode handeln.  
  
### Strukturieren von Textvorlagen  
 Es wird empfohlen, den Vorlagencode in zwei Teile aufzuteilen:  
  
-   Ein Konfigurations\- oder Datensammlungsteil, der Werte in Variablen festlegt, jedoch keine Textblöcke enthält.  Im vorherigen Beispiel ist dieser Teil die Initialisierung von `properties`.  
  
     Dies wird manchmal als Modellabschnitt bezeichnet, da ein speicherinternes Modell erstellt und normalerweise eine Modelldatei gelesen wird.  
  
-   Der Textgenerierungsteil \(im vorliegenden Beispiel `foreach(...){...}`\), in dem die Werte der Variablen verwendet werden.  
  
 Dies ist keine notwendige Trennung, doch auf diese Weise wird das Lesen der Vorlage wegen der geringeren Komplexität des Teils, der Text enthält, vereinfacht.  
  
## Lesen von Dateien oder anderen Quellen  
 Im Vorlagencode können Assemblys wie System.XML verwendet werden, um auf eine Modelldatei oder eine Datenbank zuzugreifen.  Um Zugriff auf diese Assemblys zu erhalten, müssen Sie wie hier dargestellt Direktiven einfügen:  
  
```  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
<#@ import namespace="System.IO" #>  
```  
  
 Die `assembly`\-Direktive macht die angegebene Assembly auf die gleiche Weise für den Vorlagencode verfügbar wie der Abschnitt "Verweise" eines [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekts.  Sie müssen keinen Verweis auf "System.dll" einschließen, da automatisch darauf verwiesen wird.  Die `import`\-Direktive ermöglicht wie die `using`\-Direktive in einer normalen Programmdatei die Verwendung von Typen ohne ihre vollqualifizierten Namen.  
  
 Nach dem Import von **System.IO** können Sie z. B. Folgendes schreiben:  
  
```c#  
  
          <# var properties = File.ReadLines("C:\\propertyList.txt");#>  
...  
<# foreach (string propertyName in properties) { #>  
...  
```  
  
```vb#  
<# For Each propertyName As String In   
             File.ReadLines("C:\\propertyList.txt")  
#>  
  
```  
  
### Öffnen einer Datei mit einem relativen Pfadnamen  
 Verwenden Sie `this.Host.ResolvePath()`, um eine Datei aus einem Ort zu laden, der relativ zur Textvorlage ist.  Zur Verwendung von this.Host muss `hostspecific="true"` in `template` festgelegt werden:  
  
```  
<#@ template debug="false" hostspecific="true" language="C#" #>  
  
```  
  
 Anschließend können Sie z. B. Folgendes schreiben:  
  
```c#  
<# string fileName = this.Host.ResolvePath("filename.txt");  
  string [] properties = File.ReadLines(filename);  
#>  
...  
<#  foreach (string propertyName in properties { #>  
...  
  
```  
  
```vb#  
<# Dim fileName = Me.Host.ResolvePath("propertyList.txt")  
   Dim properties = File.ReadLines(filename)  
#>  
...  
<#   For Each propertyName As String In properties  
...  
#>  
  
```  
  
 Sie können auch `this.Host.TemplateFile` verwenden, was den Namen der aktuellen Vorlagendatei darstellt.  
  
 Der Typ von `this.Host` \(in VB `Me.Host`\) ist `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`.  
  
### Abrufen von Daten von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 Um in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bereitgestellte Dienste zu verwenden, legen Sie das `hostSpecific`\-Attribut fest, und laden Sie die `EnvDTE`\-Assembly.  Sie können dann IServiceProvider.GetCOMService\(\) verwenden, um auf DTE und andere Dienste zuzugreifen.  Beispiel:  
  
```scr  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
> [!TIP]
>  Eine Textvorlage wird in ihrer eigene App\-Domäne ausgeführt, und der Zugriff auf Dienste erfolgt durch Marshalling.  Unter diesen Umständen ist GetCOMService\(\) zuverlässiger als GetService\(\).  
  
##  <a name="Regenerating"></a> Automatisches erneutes Generieren des Codes  
 In der Regel werden mehrere Dateien in einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projektmappe mit einem Eingabemodell generiert.  Jede Datei wird aus einer eigenen Vorlage generiert, die Vorlagen verweisen jedoch alle auf das gleiche Modell.  
  
 Wenn sich das Quellmodell ändert, müssen Sie alle Vorlagen in der Projektmappe erneut ausführen.  Um dies manuell auszuführen, wählen Sie im Menü **BuildAlle Vorlagen transformieren** aus.  
  
 Wenn Sie das Visualisierungs\- und Modellierungs\-SDK für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installiert haben, können alle Vorlagen bei jeder Buildausführung automatisch transformiert werden.  Bearbeiten Sie dazu die Projektdatei \(.csproj oder .vbproj\) in einem Text\-Editor, und fügen Sie in der Nähe des Endes der Datei nach allen anderen `<import>`\-Anweisungen die folgenden Zeilen hinzu:  
  
```  
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v11.0\TextTemplating\Microsoft.TextTemplating.targets" />  
<PropertyGroup>  
   <TransformOnBuild>true</TransformOnBuild>  
   <!-- Other properties can be inserted here -->  
</PropertyGroup>  
```  
  
 Weitere Informationen finden Sie unter [Code Generation in a Build Process](../modeling/code-generation-in-a-build-process.md).  
  
## Fehlerberichte  
 Zum Anzeigen von Fehler\- und Warnmeldungen im Fehlerfenster von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] stehen Ihnen die folgenden Methoden zur Verfügung:  
  
```  
Error("An error message");  
Warning("A warning message");  
```  
  
##  <a name="Converting"></a> Konvertieren einer vorhandenen Datei in eine Vorlage  
 Eine hilfreiche Eigenschaft von Vorlagen ist, dass sie den generierten Dateien sehr ähneln und zudem einigen eingefügten Programmcode enthalten.  Dadurch ergibt sich eine einfache Methode zum Erstellen einer Vorlage.  Erstellen Sie zuerst eine normale Datei als Prototyp, z. B. eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Datei, und fügen Sie dann nach und nach Generierungscode ein, durch den die resultierende Datei verändert wird.  
  
#### So konvertieren Sie eine vorhandene Datei in eine Entwurfszeitvorlage  
  
1.  Fügen Sie dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt eine Datei des Typs hinzu, den Sie generieren möchten, z. B. eine `.cs`\-, `.vb`\- oder `.resx`\-Datei.  
  
2.  Testen Sie die neue Datei, um sicherzustellen, dass sie ordnungsgemäß funktioniert.  
  
3.  Ändern Sie in Projektmappen\-Explorer die Dateinamenerweiterung in **.tt**.  
  
4.  Überprüfen Sie die folgenden Eigenschaften der **.tt**\-Eigenschaft:  
  
    |||  
    |-|-|  
    |**Benutzerdefiniertes Tool \=**|**TextTemplatingFileGenerator**|  
    |**Buildvorgang \=**|**Keine**|  
  
5.  Fügen Sie am Anfang der Datei die folgenden Zeilen ein:  
  
    ```  
    <#@ template debug="false" hostspecific="false" language="C#" #>  
    <#@ output extension=".cs" #>  
    ```  
  
     Wenn Sie den Generierungscode der Vorlage in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] schreiben möchten, legen Sie das `language`\-Attribut anstelle von `"VB"` auf `"C#"` fest.  
  
     Legen Sie das `extension`\-Attribut auf die Dateinamenerweiterung für den zu generierenden Dateityp fest, z. B. `.cs`, `.resx` oder `.xml`.  
  
6.  Speichern Sie die Datei.  
  
     Eine untergeordnete Datei mit der angegebenen Erweiterung wird erstellt.  Die Eigenschaften entsprechen dem Dateityp.  Die Eigenschaft **Buildvorgang** einer CS\-Datei wäre z. B. **Kompilieren**.  
  
     Vergewissern Sie sich, dass die generierte Datei den gleichen Inhalt enthält wie die ursprüngliche Datei.  
  
7.  Identifizieren Sie einen Teil der Datei, den Sie ändern möchten.  Beispielsweise einen Teil, der nur unter bestimmten Bedingungen angezeigt oder wiederholt wird oder in dem sich bestimmte Werte ändern.  Fügen Sie Generierungscode ein.  Speichern Sie die Datei, und überprüfen Sie, ob die untergeordnete Datei ordnungsgemäß generiert wurde.  Wiederholen Sie diesen Schritt.  
  
## Richtlinien für die Codegenerierung  
 Siehe [Guidelines for Writing T4 Text Templates](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
## Nächste Schritte  
  
|Nächster Schritt|Thema|  
|----------------------|-----------|  
|Schreiben und debuggen Sie eine erweiterte Textvorlage mit Code, in dem zusätzliche Funktionen, eingeschlossene Dateien und externe Daten verwendet werden.|[Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)|  
|Generieren Sie zur Laufzeit Dokumente aus Vorlagen.|[Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md)|  
|Führen Sie die Textgenerierung außerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aus.|[Generating Files with the TextTransform Utility](../modeling/generating-files-with-the-texttransform-utility.md)|  
|Transformieren Sie die Daten in das Format einer domänenspezifischen Sprache.|[Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Schreiben Sie Direktivenprozessoren, um eigene Datenquellen zu transformieren.|[Customizing T4 Text Transformation](../modeling/customizing-t4-text-transformation.md)|  
  
## Siehe auch  
 [Guidelines for Writing T4 Text Templates](../modeling/guidelines-for-writing-t4-text-templates.md)