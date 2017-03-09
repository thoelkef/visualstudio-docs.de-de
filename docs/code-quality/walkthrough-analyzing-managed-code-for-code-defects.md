---
title: "Exemplarische Vorgehensweise: Analysieren von verwaltetem Code auf Codefehler | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Codeanalyse, exemplarische Vorgehensweisen"
  - "Verwalteter Code, Analysieren"
  - "Codeanalysetool, exemplarische Vorgehensweisen"
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 45
caps.handback.revision: 45
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Exemplarische Vorgehensweise: Analysieren von verwaltetem Code auf Codefehler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise analysieren Sie ein verwaltetes Projekt, um Codefehler mithilfe des Codeanalysetools.  
  
 Diese exemplarische Vorgehensweise führt Sie durch die Verwendung von Codeanalyse Ihrer verwalteten Codeassemblys auf Übereinstimmung mit den Microsoft .NET Framework-Entwurfsrichtlinien analysieren schrittweise.  
  
 In dieser exemplarischen Vorgehensweise Sie:  
  
-   Analysieren Sie und beheben Sie Fehler Code (Warnungen).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>Erstellen einer Klassenbibliothek  
  
#### <a name="to-create-a-class-library"></a>So erstellen Sie eine Klassenbibliothek  
  
1.  Auf der **Datei** Menü [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], klicken Sie auf **Neu** und klicken Sie dann auf **Projekt**.  
  
2.  In der **Neues Projekt** Dialogfeld **Projekttypen**, klicken Sie auf **Visual C#-**.  
  
3.  Unter **Vorlagen**, Option **Klassenbibliothek**.  
  
4.  In den **Namen** Textfeld **CodeAnalysisManagedDemo** und klicken Sie dann auf **OK**.  
  
5.  Nachdem das Projekt erstellt wurde, öffnen Sie die Datei "Class1.cs" aus.  
  
6.  Ersetzen Sie den vorhandenen Text in Class1.cs durch den folgenden Code:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Speichern Sie die Datei Class1.cs.  
  
## <a name="analyze-the-project"></a>Analysieren des Projekts  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Um ein verwaltetes Projekt, um Codefehler zu analysieren.  
  
1.  Wählen Sie das Projekt CodeAnalysisManagedDemo **Projektmappen-Explorer**.  
  
2.  Auf der **Projekt** Menü klicken Sie auf **Eigenschaften**.  
  
     Die Eigenschaftenseite für CodeAnalysisManagedDemo wird angezeigt.  
  
3.  Klicken Sie auf **CodeAnalysis**.  
  
4.  Stellen Sie sicher, dass  **Codeanalyse für Build aktivieren (definiert eine CODE_ANALYSIS-Konstante**) aktiviert ist.  
  
5.  Aus der **diesen Regelsatz ausführen** Dropdown-Liste **alle Microsoft-Regeln**.  
  
6.  Auf der **Datei** Menü klicken Sie auf **Ausgewählte Elemente speichern**, und schließen Sie dann die Eigenschaftenseiten für ManagedDemo.  
  
7.  Auf der **Erstellen** Menü klicken Sie auf **ManagedDemo erstellen**.  
  
     Die Buildwarnungen zum Projekt CodeAnalysisManagedDemo werden gemeldet, der **Codeanalyse** und **Ausgabe** Windows.  
  
     Wenn die **Codeanalyse** Fenster nicht angezeigt wird, auf die **Analysieren** Menü wählen **Windows** und dann **Wählen Sie die Codeanalyse**.  
  
## <a name="correct-the-code-analysis-issues"></a>Korrigieren Sie die Codeanalysefehler  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>So beheben Sie Code Analysis-Regelverstößen  
  
1.  Auf der **Ansicht** Menü klicken Sie auf **Fehlerliste**.  
  
     Abhängig von der Developer-Profil, das Sie ausgewählt haben, müssen Sie möglicherweise auf zeigen **Weitere Fenster** auf die **Ansicht** Menü, und klicken Sie dann auf **Fehlerliste**.  
  
2.  In **Projektmappen-Explorer**, klicken Sie auf **Alle Dateien anzeigen**.  
  
3.  Anschließend erweitern Sie den Knoten Eigenschaften, und öffnen Sie die Datei "AssemblyInfo.cs".  
  
4.  Verwenden Sie Folgendes, um Warnungen zu beheben:  
  
-   [CA1014: Assemblys mit CLSCompliantAttribute markieren](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 'Demo' sollte mit CLSCompliantAttribute markiert sein, und der Wert sollte true sein.  
  
    -   Fügen Sie den Code `using``System;` der Datei AssemblyInfo.cs.  
  
         Als Nächstes fügen Sie den Code `[assembly: CLSCompliant(true)]` an das Ende der Datei AssemblyInfo.cs.  
  
         Erstellen Sie das Projekt neu.  
  
-   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie dieser Klasse den folgenden Konstruktor: public demo(String)  
  
    -   Fügen Sie den Konstruktor `public demo (String s) : base(s) { }` der Klasse `demo`.  
  
-   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie dieser Klasse den folgenden Konstruktor: public Demo (String, Exception)  
  
    -   Fügen Sie den Konstruktor `public demo (String s, Exception e) : base(s, e) { }` der Klasse `demo`.  
  
-   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie dieser Klasse den folgenden Konstruktor: protected Demo (SerializationInfo, StreamingContext)  
  
    -   Fügen Sie den Code `using System.Runtime.Serialization;` am Anfang der Datei Class1.cs.  
  
         Als Nächstes fügen Sie den Konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         Erstellen Sie das Projekt neu.  
  
-   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie dieser Klasse den folgenden Konstruktor: public demo()  
  
    -   Fügen Sie den Konstruktor `public demo () : base() { }` der Klasse `demo`**.**  
  
         Erstellen Sie das Projekt neu.  
  
-   [CA1709: bei Bezeichnern sollte werden Groß-/Kleinschreibung korrekt](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Schreibweise des Namespacenamens 'TestCode' in 'TestCode'.  
  
    -   Ändern Sie die Schreibweise des Namespace `testCode` auf `TestCode`.  
  
-   [CA1709: bei Bezeichnern sollte werden Groß-/Kleinschreibung korrekt](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Groß-/Kleinschreibung des Typnamens 'Demo' in 'Demo'.  
  
    -   Ändern Sie den Namen des Members `Demo`.  
  
-   [CA1709: bei Bezeichnern sollte werden Groß-/Kleinschreibung korrekt](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Schreibweise des Membernamens 'Item' in 'Item'.  
  
    -   Ändern Sie den Namen des Members `Item`.  
  
-   [CA1710: Bezeichner sollten richtiges Suffix aufweisen](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Rename 'Testcode.Demo 'dass lautet "Ausnahme" endet.  
  
    -   Ändern Sie den Namen der Klasse und der zugehörigen Konstruktoren in `DemoException`.  
  
-   [CA2210: Assemblys müssen gültige starke Namen aufweisen](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): 'ManagedDemo' mit einem Schlüssel mit starkem Namen zu signieren.  
  
    -   Auf der **Projekt** Menü klicken Sie auf **Eigenschaften von ManagedDemo**.  
  
         Die Projekteigenschaften werden angezeigt.  
  
         Klicken Sie auf **signieren**.  
  
         Wählen Sie die **zum Signieren der Assembly** das Kontrollkästchen.  
  
         In der **Wählen Sie eine Schlüsseldatei mit starkem Namen** Liste **\< neu... >**.  
  
         Die **Schlüssel für einen starken Namen erstellen** das Dialogfeld wird angezeigt.  
  
         In der **Schlüsseldateiname**, TestKey geben.  
  
         Geben Sie ein Kennwort ein, und klicken Sie dann auf **OK**.  
  
         Auf der **Datei** Menü klicken Sie auf **Ausgewählte Elemente speichern**, und schließen Sie dann die Eigenschaftenseiten.  
  
         Erstellen Sie das Projekt neu.  
  
-   [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Fügen Sie [Serializable] 'demo' geben, da dieser Typ ISerializable implementiert.  
  
    -   Hinzufügen der `[Serializable ()]` -Attribut auf die Klasse `demo`.  
  
         Erstellen Sie das Projekt neu.  
  
 Nachdem Sie die Änderungen abgeschlossen haben, sollte die Datei Class1.cs wie folgt aussehen:  
  
```  
//CodeAnalysisManagedDemo  
//Class1.cs  
using System;  
using System.Runtime.Serialization;  
  
namespace TestCode  
{  
  
    [Serializable()]   
    public class DemoException : Exception  
    {  
        public DemoException () : base() { }  
        public DemoException(String s) : base(s) { }  
        public DemoException(String s, Exception e) : base(s, e) { }  
        protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }  
  
        public static void Initialize(int size) { }  
        protected static readonly int _item;  
        public static int Item { get { return _item; } }  
    }  
}  
```  
  
## <a name="exclude-code-analysis-warnings"></a>Ausschließen von Codeanalysewarnungen  
  
#### <a name="to-exclude-code-defect-warnings"></a>Ausschließen von Code (Warnungen) Fehler  
  
1.  Führen Sie für jede der verbleibenden Warnungen folgende Schritte aus:  
  
    1.  Wählen Sie im Fenster Codeanalyse der Warnung.  
  
    2.  Wählen Sie **Aktionen**, wählen Sie dann **Meldung unterdrücken**, und wählen Sie dann **im Projektunterdrückungsdatei**.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Unterdrücken von Warnungen über das Menüelement](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  Erstellen Sie das Projekt neu.  
  
     Das Projekt erstellt, ohne alle Warnungen oder Fehler.