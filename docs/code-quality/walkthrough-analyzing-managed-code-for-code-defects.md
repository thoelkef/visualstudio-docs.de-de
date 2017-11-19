---
title: 'Exemplarische Vorgehensweise: Analysieren von verwaltetem Code Codefehler | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3dd0c93476e646895362b98c2f62b569d87ffe35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Exemplarische Vorgehensweise: Analysieren von verwaltetem Code auf Codefehler
In dieser exemplarischen Vorgehensweise analysieren Sie ein verwaltetes Projekt Codefehler mit Codeanalysetools.  
  
 Diese exemplarische Vorgehensweise führt Sie durch die Verwendung von Codeanalyse Analysieren Ihrer verwalteten Codeassemblys zur Erhaltung der Konformität mit den Microsoft .NET Framework-Entwurfsrichtlinien schrittweise.  
  
 In dieser exemplarischen Vorgehensweise Sie:  
  
-   Analysieren Sie und beheben Sie Fehler in Code (Warnungen).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>Erstellen einer Klassenbibliothek  
  
#### <a name="to-create-a-class-library"></a>So erstellen Sie eine Klassenbibliothek  
  
1.  Auf der **Datei** Menü [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], klicken Sie auf **neu** , und klicken Sie dann auf **Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld unter **Projekttypen**, klicken Sie auf **Visual C#-**.  
  
3.  Klicken Sie unter **Vorlagen**Option **-Klassenbibliothek**.  
  
4.  In der **Namen** Textfeld **CodeAnalysisManagedDemo** , und klicken Sie dann auf **OK**.  
  
5.  Nachdem das Projekt erstellt wurde, öffnen Sie die Datei "Class1.cs".  
  
6.  Ersetzen Sie den vorhandenen Text in "Class1.cs" durch den folgenden Code ein:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Speichern Sie die Datei "Class1.cs".  
  
## <a name="analyze-the-project"></a>Analysieren Sie das Projekt  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Um ein verwaltetes Projekt Codefehler zu analysieren.  
  
1.  Wählen Sie das Projekt CodeAnalysisManagedDemo **Projektmappen-Explorer**.  
  
2.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
     Die Eigenschaftenseite CodeAnalysisManagedDemo wird angezeigt.  
  
3.  Klicken Sie auf **eine Code_analysis**.  
  
4.  Stellen Sie sicher, dass **Codeanalyse für Build aktivieren (definiert eine CODE_ANALYSIS-Konstante**) aktiviert ist.  
  
5.  Aus der **diesen Regelsatz ausführen** Dropdown-Liste **Microsoft alle Regeln**.  
  
6.  Auf der **Datei** Menü klicken Sie auf **ausgewählte Elemente speichern**, und schließen Sie dann die Eigenschaftenseiten für ManagedDemo.  
  
7.  Auf der **erstellen** Menü klicken Sie auf **ManagedDemo erstellen**.  
  
     Die CodeAnalysisManagedDemo Projekt Buildwarnungen werden gemeldet, der **Codeanalyse** und **Ausgabe** Windows.  
  
     Wenn die **Codeanalyse** Fenster nicht angezeigt wird, auf die **analysieren** Menü wählen **Windows** und dann **wählen Sie die Codeanalyse**.  
  
## <a name="correct-the-code-analysis-issues"></a>Beheben Sie die Codeanalysefehler  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>So beheben Sie codeanalyseverstöße Regel  
  
1.  Auf der **Ansicht** Menü klicken Sie auf **Fehlerliste**.  
  
     Abhängig von der Developer-Profil, das Sie ausgewählt haben, müssen Sie möglicherweise auf zeigen **Weitere Fenster** auf die **Ansicht** Menü, und klicken Sie dann auf **Fehlerliste**.  
  
2.  In **Projektmappen-Explorer**, klicken Sie auf **alle Dateien anzeigen**.  
  
3.  Als Nächstes, erweitern Sie den Knoten für die Eigenschaften, und öffnen Sie die Datei "AssemblyInfo.cs".  
  
4.  Verwenden Sie Folgendes, um Warnungen zu beheben:  
  
-   [CA1014: Assemblys mit CLSCompliantAttribute markieren](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: "Demo" sollte mit CLSCompliantAttribute markiert sein, und der Wert sollte "true" sein.  
  
    -   Fügen Sie den Code `using``System;` der Datei AssemblyInfo.cs.  
  
         Als Nächstes fügen Sie den Code `[assembly: CLSCompliant(true)]` bis zum Ende der Datei AssemblyInfo.cs.  
  
         Erstellen Sie das Projekt neu.  
  
-   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie diese Klasse den folgenden Konstruktor hinzu: public demo(String)  
  
    -   Fügen Sie den Konstruktor `public demo (String s) : base(s) { }` der Klasse `demo`.  
  
-   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie diese Klasse den folgenden Konstruktor hinzu: public Demo ("String", "Ausnahme")  
  
    -   Fügen Sie den Konstruktor `public demo (String s, Exception e) : base(s, e) { }` der Klasse `demo`.  
  
-   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie diese Klasse den folgenden Konstruktor hinzu: protected Demo (SerializationInfo, StreamingContext)  
  
    -   Fügen Sie den Code `using System.Runtime.Serialization;` am Anfang der Datei "Class1.cs".  
  
         Als Nächstes fügen Sie den Konstruktor`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         Erstellen Sie das Projekt neu.  
  
-   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie diese Klasse den folgenden Konstruktor hinzu: public demo()  
  
    -   Fügen Sie den Konstruktor `public demo () : base() { }` der Klasse `demo` **.**  
  
         Erstellen Sie das Projekt neu.  
  
-   [CA1709: Bezeichner sollten werden Groß-/Kleinschreibung beachtet ordnungsgemäß](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Groß-/Kleinschreibung des Namespacenamens 'TestCode' in 'TestCode'.  
  
    -   Ändern Sie die Groß-/Kleinschreibung des Namespaces `testCode` auf `TestCode`.  
  
-   [CA1709: Bezeichner sollten werden Groß-/Kleinschreibung beachtet ordnungsgemäß](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Groß-/Kleinschreibung des Typnamens "Demo" auf "Demo".  
  
    -   Ändern Sie den Namen des Members, um `Demo`.  
  
-   [CA1709: Bezeichner sollten werden Groß-/Kleinschreibung beachtet ordnungsgemäß](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Groß-/Kleinschreibung des Namens "Item", "Element".  
  
    -   Ändern Sie den Namen des Members, um `Item`.  
  
-   [CA1710: Bezeichner sollten richtiges Suffix aufweisen](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Rename 'Testcode.Demo dass lautet"Ende"Ausnahme".  
  
    -   Ändern Sie den Namen der Klasse und ihre Konstruktoren `DemoException`.  
  
-   [CA2210: Assemblys müssen gültige starke Namen aufweisen](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): 'ManagedDemo' mit einem starken Namensschlüssel signieren.  
  
    -   Auf der **Projekt** Menü klicken Sie auf **ManagedDemo Eigenschaften**.  
  
         Die Projekteigenschaften werden angezeigt.  
  
         Klicken Sie auf **signieren**.  
  
         Wählen Sie die **zum Signieren der Assembly** Kontrollkästchen.  
  
         In der **wählen Sie eine Schlüsseldatei mit starkem Namen** Liste  **\<neu... >**.  
  
         Die **Schlüssel für einen starken Namen erstellen** Dialogfeld wird angezeigt.  
  
         In der **Schlüsseldateiname**, TestKey geben.  
  
         Geben Sie ein Kennwort ein, und klicken Sie dann auf **OK**.  
  
         Auf der **Datei** Menü klicken Sie auf **ausgewählte Elemente speichern**, und klicken Sie dann die Eigenschaftenseiten zu schließen.  
  
         Erstellen Sie das Projekt neu.  
  
-   [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Fügen Sie einem [Serializable] "demo" geben, wie dieser Typ ISerializable implementiert.  
  
    -   Hinzufügen der `[Serializable ()]` -Attribut der Klasse `demo`.  
  
         Erstellen Sie das Projekt neu.  
  
 Nachdem Sie die Änderungen abgeschlossen haben, sollte die Datei "Class1.cs" wie folgt aussehen:  
  
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
  
#### <a name="to-exclude-code-defect-warnings"></a>Auszuschließende defekt Code (Warnungen)  
  
1.  Führen Sie für jede der verbleibenden Warnungen folgende Schritte aus:  
  
    1.  Wählen Sie im Codeanalysefenster angezeigt die Warnung ein.  
  
    2.  Wählen Sie **Aktionen**, wählen Sie dann **Meldung unterdrücken**, und wählen Sie dann **im Projektunterdrückungsdatei**.  
  
     Weitere Informationen finden Sie unter [wie: Unterdrücken von Warnungen über das Menüelement](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  Erstellen Sie das Projekt neu.  
  
     Das Projekt erstellt, ohne alle Warnungen oder Fehler.