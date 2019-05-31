---
title: 'Exemplarische Vorgehensweise: Analysieren von verwaltetem Code auf Codefehler | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26d8412318efd2292fd0f5a0f0ef52fe36c7d06c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116289"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Exemplarische Vorgehensweise: Analysieren von verwaltetem Code im Hinblick auf Codefehler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise analysieren Sie ein verwaltetes Projekt Codefehler, mit dem Code Analysetool.  
  
 Diese exemplarische Vorgehensweise führt Sie durch den Prozess mit der Codeanalyse analysiert Ihre .NET-verwaltete Codeassemblys auf Übereinstimmung mit den Microsoft .NET Framework-Entwurfsrichtlinien ausführlich.  
  
 In dieser exemplarischen Vorgehensweise Sie:  
  
- Analysieren Sie und beheben Sie Fehler für Code (Warnungen).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
## <a name="create-a-class-library"></a>Erstellen einer Klassenbibliothek  
  
#### <a name="to-create-a-class-library"></a>So erstellen Sie eine Klassenbibliothek  
  
1. Auf der **Datei** Menü [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], klicken Sie auf **neu** , und klicken Sie dann auf **Projekt**.  
  
2. In der **neues Projekt** Dialogfeld **Projekttypen**, klicken Sie auf **Visual C#-** .  
  
3. Klicken Sie unter **Vorlagen**Option **Klassenbibliothek**.  
  
4. In der **Namen** Textfeld **CodeAnalysisManagedDemo** , und klicken Sie dann auf **OK**.  
  
5. Nachdem das Projekt erstellt wurde, öffnen Sie die Datei "Class1.cs".  
  
6. Ersetzen Sie den vorhandenen Text in "Class1.cs" durch den folgenden Code ein:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7. Speichern Sie die Datei "Class1.cs".  
  
## <a name="analyze-the-project"></a>Analysieren des Projekts  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Um ein verwaltetes Projekt Codefehler zu analysieren.  
  
1. Wählen Sie das Projekt CodeAnalysisManagedDemo in **Projektmappen-Explorer**.  
  
2. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
     Die Eigenschaftenseite CodeAnalysisManagedDemo wird angezeigt.  
  
3. Klicken Sie auf **CodeAnalysis**.  
  
4. Stellen Sie sicher, dass **Codeanalyse für Build aktivieren (definiert eine CODE_ANALYSIS-Konstante**) aktiviert ist.  
  
5. Von der **diesen Regelsatz ausführen** Dropdown-Liste **alle Microsoft-Regeln**.  
  
6. Auf der **Datei** Menü klicken Sie auf **ausgewählte Elemente speichern**, und schließen Sie dann die Eigenschaftenseiten für ManagedDemo.  
  
7. Auf der **erstellen** Menü klicken Sie auf **ManagedDemo erstellen**.  
  
     Die CodeAnalysisManagedDemo Project Buildwarnungen werden gemeldet, der **Codeanalyse** und **Ausgabe** Windows.  
  
     Wenn die **Codeanalyse** Fenster nicht angezeigt wird, auf die **analysieren** im Menü wählen **Windows** und dann **wählen Sie die Codeanalyse**.  
  
## <a name="correct-the-code-analysis-issues"></a>Korrigieren Sie bei der Codeanalyse  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Um Code Analysis-Regelverstöße zu beheben.  
  
1. Auf der **Ansicht** Menü klicken Sie auf **Fehlerliste**.  
  
     Abhängig von der Developer-Profil, das Sie ausgewählt haben, müssen Sie möglicherweise ein auf zeigen **andere Windows** auf die **Ansicht** , und klicken Sie dann auf **Fehlerliste**.  
  
2. In **Projektmappen-Explorer**, klicken Sie auf **alle Dateien anzeigen**.  
  
3. Anschließend erweitern Sie den Knoten "Eigenschaften", und öffnen Sie die Datei "AssemblyInfo.cs".  
  
4. Verwenden Sie Folgendes, um Warnungen zu beheben:  
  
- [CA1014: Assemblys mit CLSCompliantAttribute markieren](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: "Demo" markiert werden mit CLSCompliantAttribute, und der Wert sollte "true" sein.  
  
  - Fügen Sie den Code `using``System;` in die Datei "AssemblyInfo.cs".  
  
       Als Nächstes fügen Sie den Code `[assembly: CLSCompliant(true)]` an das Ende der Datei "AssemblyInfo.cs".  
  
       Erstellen Sie das Projekt neu.  
  
- [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie den folgenden Konstruktor dieser Klasse: public demo(String)  
  
  - Fügen Sie den Konstruktor `public demo (String s) : base(s) { }` auf die Klasse `demo`.  
  
- [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie den folgenden Konstruktor dieser Klasse: öffentliche Demo ("String", "Exception")  
  
  - Fügen Sie den Konstruktor `public demo (String s, Exception e) : base(s, e) { }` auf die Klasse `demo`.  
  
- [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie den folgenden Konstruktor dieser Klasse: Demo (SerializationInfo-Objekt, StreamingContext) geschützt  
  
  - Fügen Sie den Code `using System.Runtime.Serialization;` an den Anfang der Datei "Class1.cs".  
  
       Als Nächstes fügen Sie den Konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
       Erstellen Sie das Projekt neu.  
  
- [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie den folgenden Konstruktor dieser Klasse: öffentliche Demo()"ein, um  
  
  - Fügen Sie den Konstruktor `public demo () : base() { }` auf die Klasse `demo` **.**  
  
       Erstellen Sie das Projekt neu.  
  
- [CA1709: Bezeichner sollten werden Groß-/Kleinschreibung korrekt](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Groß-/Kleinschreibung des Namespacenamens 'TestCode' in 'TestCode'.  
  
  - Ändern Sie die Schreibweise des Namespace `testCode` zu `TestCode`.  
  
- [CA1709: Bezeichner sollten werden Groß-/Kleinschreibung korrekt](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Groß-/Kleinschreibung des Typnamens "Demo", "Demo".  
  
  - Ändern Sie den Namen des abzurufenden Members `Demo`.  
  
- [CA1709: Bezeichner sollten werden Groß-/Kleinschreibung korrekt](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Schreibweise des Namens 'Item' in 'Item'.  
  
  - Ändern Sie den Namen des abzurufenden Members `Item`.  
  
- [CA1710: Bezeichner sollten ein richtiges Suffix aufweisen](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Benennen Sie "Testcode.Demo dass lautet" Ende "Ausnahme".  
  
  - Ändern Sie den Namen der Klasse und die zugehörigen Konstruktoren in `DemoException`.  
  
- [CA2210: Assemblys müssen gültige starke Namen aufweisen](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Melden Sie 'ManagedDemo' mit einem Schlüssel mit starkem Namen an.  
  
  - Auf der **Projekt** Menü klicken Sie auf **ManagedDemo Eigenschaften**.  
  
       Die Projekteigenschaften angezeigt.  
  
       Klicken Sie auf **signieren**.  
  
       Wählen Sie die **Assembly signieren** Kontrollkästchen.  
  
       In der **wählen Sie eine Schlüsseldatei mit starkem Namen** Liste  **\<neu... >** .  
  
       Die **Schlüssel für einen starken Namen erstellen** Dialogfeld wird angezeigt.  
  
       In der **Schlüsseldateiname**, TestKey geben.  
  
       Geben Sie ein Kennwort ein, und klicken Sie dann auf **OK**.  
  
       Auf der **Datei** Menü klicken Sie auf **ausgewählte Elemente speichern**, und klicken Sie dann die Eigenschaftenseiten zu schließen.  
  
       Erstellen Sie das Projekt neu.  
  
- [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Fügen Sie einem [Serializable]-Attribut, um "demo" Geben Sie, wie dieser Typ ISerializable implementiert.  
  
  - Hinzufügen der `[Serializable ()]` -Attribut der Klasse `demo`.  
  
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
  
#### <a name="to-exclude-code-defect-warnings"></a>Auszuschließende Mängel Code (Warnungen)  
  
1. Führen Sie für jede der verbleibenden Warnungen folgende Schritte aus:  
  
   1. Wählen Sie im Codeanalysefenster angezeigt die Warnung ein.  
  
   2. Wählen Sie **Aktionen**, wählen Sie dann **Meldung unterdrücken**, und wählen Sie dann **In Projektunterdrückungsdatei**.  
  
      Weitere Informationen finden Sie unter [Vorgehensweise: Unterdrücken von Warnungen über das Menüelement](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2. Erstellen Sie das Projekt neu.  
  
    Das Projekt erstellt, ohne alle Warnungen oder Fehler.
