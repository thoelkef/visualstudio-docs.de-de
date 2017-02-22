---
title: "Run-Time Text Generation with T4 Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Preprocessed Text Template project item"
  - "TextTemplatingFilePreprocessor custom tool"
  - "text templates, TransformText() method"
  - "text templates, generating files at run time"
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 22
caps.handback.revision: 22
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Run-Time Text Generation with T4 Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Textzeichenfolgen in Ihrer Anwendung zur Laufzeit generieren, mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Runtime Textvorlagen.  Auf dem Computer, auf dem die Anwendung ausgeführt wird, muss [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht installiert sein.  Common Language Runtime\-Vorlagen werden manchmal "vorverarbeitet Textvorlagen" bezeichnet, da die Vorlage zum Zeitpunkt der Kompilierung Code generiert, der zur Laufzeit ausgeführt wird.  
  
 Jede Vorlage besteht aus einer Mischung des in der generierten Zeichenfolge angezeigten Texts und Fragmenten des Programmcodes.  Die Programmfragmente liefern Werte für die variablen Teile der Zeichenfolge und steuern zudem bedingte und wiederholte Teile.  
  
 Die folgende Vorlage kann z. B. in einer Anwendung verwendet werden, die einen HTML\-Bericht erstellt.  
  
```  
<#@ template language="C#" #>  
<html><body>  
<h1>Sales for Previous Month</h2>  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
This report is Company Confidential.  
</body></html>  
```  
  
 Die Vorlage ist eine HTML\-Seite, in der die variablen Teile durch Programmcode ersetzt wurden.  Sie können den Entwurf einer derartigen Seite beginnen, indem Sie einen statischen Prototyp der HTML\-Seite schreiben.  Sie können dann die Tabelle und andere Variablenteile durch Programmcode ersetzen, mit dem der Inhalt generiert wird, der sich je nach Situation ändert.  
  
 Die Verwendung einer Vorlage in der Anwendung erleichtert die Anzeige des endgültigen Formats der Ausgabe im Vergleich zu einer langen Reihe von Schreibanweisungen.  Änderungen am Format der Ausgabe können einfacher und zuverlässiger vorgenommen werden.  
  
## Erstellen einer Laufzeittextvorlage in einer beliebigen Anwendung  
  
#### So erstellen Sie eine Laufzeittextvorlage  
  
1.  Wählen Sie im Projektmappen\-Explorer im Kontextmenü des Projekts,  **Hinzufügen**,  **Neues Element**.  
  
2.  In der  **Neues Element hinzufügen** wählen Sie im Dialogfeld  **Runtime Textvorlage**.  \(Navigieren Sie in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] zu **Gemeinsame Elemente\\Allgemein**.\)  
  
3.  Geben Sie einen Namen für die Vorlagendatei ein.  
  
    > [!NOTE]
    >  Der Vorlagendateiname wird im generierten Code als Klassenname verwendet.  Er sollte daher keine Leerzeichen oder Interpunktionszeichen enthalten.  
  
4.  Wählen Sie  **Hinzufügen**.  
  
     Eine neue Datei mit der Erweiterung **.tt** wird erstellt.  Die Eigenschaft **Benutzerdefiniertes Tool** der Datei ist auf **TextTemplatingFilePreprocessor** festgelegt.  Es enthält die folgenden Zeilen:  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## Konvertieren einer vorhandenen Datei in eine Laufzeitvorlage  
 Eine effektive Methode zur Erstellung einer Vorlage ist das Konvertieren eines vorhandenen Beispiels der Ausgabe.  Wenn die Anwendung HTML\-Dateien generiert, können Sie z. B. mit dem Erstellen einer einfachen HTML\-Datei beginnen.  Stellen Sie sicher, dass die Datei ordnungsgemäß funktioniert und korrekt dargestellt wird.  Schließen Sie sie dann in das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt ein, und konvertieren Sie sie in eine Vorlage.  
  
#### So konvertieren Sie eine vorhandene Textdatei in eine Laufzeitvorlage  
  
1.  Schließen Sie die Datei in das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekt ein.  Wählen Sie im Projektmappen\-Explorer im Kontextmenü des Projekts,  **Hinzufügen**,  **Vorhandenes Element**.  
  
2.  Legen Sie die Eigenschaft **Benutzerdefiniertes Tool** der Datei auf **TextTemplatingFilePreprocessor** fest.  Wählen Sie im Projektmappen\-Explorer im Kontextmenü der Datei,  **Eigenschaften**.  
  
    > [!NOTE]
    >  Wenn die Eigenschaft bereits festgelegt ist, vergewissern Sie sich, dass ihr Wert **TextTemplatingFilePreprocessor** lautet, und nicht **TextTemplatingFileGenerator**.  Wenn Sie eine Datei einschließen, die bereits die Erweiterung **.tt** besitzt, kann es vorkommen, dass dieser Wert festgelegt ist.  
  
3.  Ändern Sie die Dateinamenerweiterung in **.tt**.  Obwohl dieser Schritt optional ist, wird dadurch vermieden, dass die Datei in einem falschen Editor geöffnet wird.  
  
4.  Entfernen Sie alle Leerzeichen oder Interpunktionszeichen aus dem Hauptteil des Dateinamens.  Die korrekte Form von "My Web Page.tt" wäre z. B. "MyWebPage.tt".  Der Dateiname wird im generierten Code als Klassenname verwendet.  
  
5.  Fügen Sie am Anfang der Datei die folgende Zeile ein:  Wenn Sie in einem Visual Basic\-Projekt arbeiten, ersetzen Sie "C\#" durch "VB".  
  
     `<#@ template language="C#" #>`  
  
## Der Inhalt der Laufzeitvorlage  
  
### Vorlagendirektive  
 Belassen Sie die erste Zeile der Vorlage in dem Zustand, in dem sie sich bei der Erstellung der Datei befand:  
  
 `<#@ template language="C#" #>`  
  
 Der Sprachparameter hängt von der Sprache des Projekts ab.  
  
### Einfacher Inhalt  
 Bearbeiten Sie die **.tt**\-Datei, sodass Sie den von der Anwendung zu generierenden Text enthält.  Beispiele:  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### Eingebetteter Programmcode  
 Sie können Programmcode zwischen `<#` und `#>` einfügen.  Beispiele:  
  
```c#  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb#  
<table>  
<#  
    For i As Integer = 1 To 10  
#>  
    <tr><td>Test name <#= i #> </td>  
      <td>Test value <#= i*i #> </td></tr>  
<#  
    Next  
#>  
</table>  
  
```  
  
 Anweisungen werden zwischen `<# ... #>` eingefügt, Ausdrücke zwischen `<#= ... #>`.  Weitere Informationen finden Sie unter [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
## Verwenden der Vorlage  
  
### Aus der Vorlage erstellter Code  
 Jedes Mal, wenn Sie die **.tt**\-Datei speichern, wird eine untergeordnete **.cs**\- oder **.vb**\-Datei generiert.  Erweitern Sie im Projektmappen\-Explorer den **.tt**\-Dateiknoten, um diese Datei anzuzeigen.  In einem Visual Basic\-Projekt können Sie den Knoten erweitern, nachdem Sie auf der Symbolleiste des Projektmappen\-Explorers auf **Alle Dateien anzeigen** geklickt haben.  
  
 Diese untergeordnete Datei enthält eine partielle Klasse mit einer Methode namens `TransformText()`.  Diese Methode kann in der Anwendung aufgerufen werden.  
  
### Generieren von Text zur Laufzeit  
 Der Inhalt der Vorlage kann mit einem Aufruf wie dem folgenden im Anwendungscode generiert werden:  
  
```c#  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb#  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 Um die generierte Klasse in einem bestimmten Namespace zu platzieren, legen Sie die Eigenschaft **Namespace des benutzerdefinierten Tools** der Textvorlagendatei fest.  
  
### Debuggen der Common Language Runtime\-Textvorlagen  
 Debuggen und Runtime Textvorlagen auf gleiche Weise wie normale Code testen.  
  
 Sie können einen Haltepunkt in einer Textvorlage festlegen.  Wenn Sie die Anwendung im Debugmodus aus Visual Studio starten, können Sie Schritt für Schritt durch den Code und Watch\-Ausdrücke auf die übliche Weise.  
  
### Übergeben von Parametern im Konstruktor  
 Normalerweise muss eine Vorlage einige Daten aus anderen Teilen der Anwendung importieren.  Dieser Vorgang wird dadurch vereinfacht, dass es sich bei dem von der Vorlage erstellten Code um eine partielle Klasse handelt.  Sie können in einer anderen Datei im Projekt einen weiteren Teil der gleichen Klasse erstellen.  Diese Datei kann einen Konstruktor mit Parametern, Eigenschaften und Funktionen enthalten, auf die sowohl der eingebettete Code in der Vorlage als auch die anderen Teile der Anwendung zugreifen können.  
  
 Sie könnten z. B. eine separate Datei **MyWebPageCode.cs** erstellen:  
  
```c#  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 In der Vorlagendatei **MyWebPage.tt** könnten Sie Folgendes schreiben:  
  
```c#  
<h2>Sales figures</h2>  
<table>  
<# foreach (MyDataItem item in m_data.Items)   
   // m_data is declared in MyWebPageCode.cs  
   { #>  
      <tr><td> <#= item.Name #> </td>  
          <td> <#= item.Value #> </td></tr>  
<# } // end of foreach  
#>  
</table>  
```  
  
 So verwenden Sie diese Vorlage in der Anwendung  
  
```c#  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### Konstruktorparameter in Visual Basic  
 In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] enthält die separate Datei **MyWebPageCode.vb** Folgendes:  
  
```vb#  
Namespace My.Templates  
  Partial Public Class MyWebPage  
    Private m_data As MyData  
    Public Sub New(ByVal data As MyData)  
      m_data = data  
    End Sub  
  End Class  
End Namespace  
```  
  
 Die Vorlagendatei kann Folgendes enthalten:  
  
```vb#  
<#@ template language="VB" #>  
<html><body>  
<h1>Sales for January</h2>  
<table>  
<#  
    For Each item In m_data.Items  
#>  
    <tr><td>Test name <#= item.Name #> </td>  
      <td>Test value <#= item.Value #> </td></tr>  
<#  
    Next  
#>  
</table>  
This report is Company Confidential.  
</body></html>  
  
```  
  
 Die Vorlage würde aufgerufen werden, indem der Parameter im Konstruktor übergeben wird:  
  
```vb#  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### Übergeben von Daten in Vorlageneigenschaften  
 Eine alternative Methode, Daten an die Vorlage zu übergeben, ist das Hinzufügen von öffentlichen Eigenschaften zur Vorlagenklasse in einer partiellen Klassendefinition.  Die Anwendung kann die Eigenschaften vor dem Aufruf von `TransformText()` festlegen.  
  
 Sie können der Vorlagenklasse in einer partiellen Definition auch Felder hinzufügen.  Dies würde es Ihnen ermöglichen, Daten zwischen aufeinander folgenden Ausführungen der Vorlage zu übergeben.  
  
### Verwenden von partiellen Klassen für Code  
 Zahlreiche Entwickler ziehen es vor, in Vorlagen keinen umfangreichen Codetext zu schreiben.  Definieren Sie stattdessen Methoden in einer partiellen Klasse, die über den gleichen Namen wie die Vorlagendatei verfügt.  Rufen Sie diese Methoden von der Vorlage auf.  Dadurch zeigt die Vorlage deutlicher, wie die Zielausgabezeichenfolge aussieht.  Diskussionen über die Darstellung des Ergebnisses können von der Logik der Erstellung der Daten getrennt werden, die angezeigt werden.  
  
### Assemblys und Verweise  
 Wenn der Vorlagencode auf eine .NET\-Assembly oder eine andere Assembly wie **System.Xml.dll** verweisen soll, fügen Sie die Assembly wie gewohnt den **Verweisen** des Projekts hinzu.  
  
 Wenn Sie einen Namespace wie bei Verwendung einer `using`\-Anweisung importieren möchten, können Sie die `import`\-Direktive verwenden:  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 Diese Direktiven müssen direkt nach der `<#@template`\-Direktive am Anfang der Datei eingefügt werden.  
  
### Freigegebener Inhalt  
 Wenn bestimmter Text für mehrere Vorlagen freigegeben werden soll, können Sie diesen Text in einer separaten Datei speichern und in die gewünschten Dateien einschließen:  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 Der eingeschlossene Inhalt kann eine beliebige Mischung aus Programmcode und Nur\-Text sowie andere include\-Direktiven und sonstige Direktiven enthalten.  
  
 Die include\-Direktive kann überall im Text einer Vorlagendatei oder einer eingeschlossenen Textdatei verwendet werden.  
  
### Vererbung zwischen Laufzeittextvorlagen  
 Sie können Inhalt zwischen Laufzeitvorlagen freigeben, indem Sie eine Basisklassenvorlage schreiben, die abstrakt sein kann.  Verwendung der `inherits` Parameter von der `<@#template#>` Richtlinie auf einen anderen Common Language Runtime\-Vorlage\-Klasse zu verweisen.  
  
#### Vererbungsmuster: Fragmente in Basismethoden  
 Beachten Sie im Muster, das im folgenden Beispiel verwendet wird, die folgenden Punkte:  
  
-   Die Basisklasse `SharedFragments` definiert Methoden innerhalb der Klassenfunktionsblöcke `<#+ ... #>`.  
  
-   Die Basisklasse enthält keinen freien Text.  Stattdessen sind alle Textblöcke in den Klassenfunktionsmethoden vorhanden.  
  
-   Die abgeleitete Klasse ruft die in `SharedFragments` definierten Methoden auf.  
  
-   Die Anwendung ruft die `TextTransform()`\-Methode der abgeleiteten Klasse auf, transformiert jedoch nicht die Basisklasse `SharedFragments`.  
  
-   Die Basisklassen und abgeleiteten Klassen sind Textvorlagen Runtime: d. h. die  **Benutzerdefiniertes Tool** festgelegt sind  **TextTemplatingFilePreprocessor**.  
  
 **SharedFragments.tt:**  
  
```c#  
<#@ template language="C#" #>  
<#+  
protected void SharedText(int n)  
{  
#>  
   Shared Text <#= n #>  
<#+  
}  
// Insert more methods here if required.  
#>  
  
```  
  
 **MyTextTemplate1.tt:**  
  
```c#  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs:**  
  
```c#  
...   
MyTextTemplate1 t1  = new MyTextTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **Die resultierende Ausgabe:**  
  
```  
begin 1  
    Shared Text 2  
end 1  
```  
  
#### Vererbungsmuster: Text in Basistext  
 In dieser alternativen Methode zur Verwendung der Vorlagenvererbung wird der Großteil des Texts in der Basisvorlage definiert.  Die abgeleiteten Vorlagen enthalten Daten und Textfragmente, die mit dem Basisinhalt kompatibel sind.  
  
 **AbstractBaseTemplate1.tt:**  
  
```c#  
<#@ template language="C#" #>  
  
Here is the description for this derived template:  
  <#= this.Description #>  
  
Here is the fragment specific to this derived template:  
<#   
  this.PushIndent("  ");  
  SpecificFragment(42);   
  this.PopIndent();  
#>  
End of common template.  
<#+   
  // State set by derived class before calling TextTransform:  
  protected string Description = "";  
  // 'abstract' method to be defined in derived classes:  
  protected virtual void SpecificFragment(int n) { }  
#>  
  
```  
  
 **DerivedTemplate1.tt:**  
  
```c#  
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>  
<#   
  // Set the base template properties:  
  base.Description = "Description for this derived class";   
  
  // Run the base template:  
  base.TransformText();  
  
#>  
End material for DerivedTemplate1.  
  
<#+  
// Provide a fragment specific to this derived template:  
  
protected override void SpecificFragment(int n)  
{  
#>  
   Specific to DerivedTemplate1 : <#= n #>  
<#+  
}  
#>  
  
```  
  
 **Anwendungscode:**  
  
```c#  
...   
DerivedTemplate1 t1 = new DerivedTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **Ergebnis:**  
  
```  
Here is the description for this derived template:  
  Description for this derived class  
  
Here is the fragment specific to this derived template:  
     Specific to DerivedTemplate1 : 42  
End of common template.  
End material for DerivedTemplate1.  
```  
  
## Verwandte Themen  
 Entwurfszeitvorlagen: Informationen zum Generieren von Code für die Anwendung mithilfe einer Vorlage finden Sie unter [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Common Language Runtime\-Vorlagen können in jeder Anwendung verwendet werden, wo sind die Vorlagen und deren Inhalt zur Kompilierzeit bestimmt.  Informationen zum Schreiben einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Erweiterung, die zur Laufzeit veränderten Text aus Vorlagen generiert, finden Sie unter [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## Siehe auch  
 [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)   
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)   
 [Verständnis T4: Vorverarbeitet Textvorlagen von Oleg Sych](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)