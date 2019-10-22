---
title: 'Exemplarische Vorgehensweise: Analysieren von verwaltetem Code auf Code Fehler | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9478394162051fc08c33047cf1ac24275aff75e2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609332"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Exemplarische Vorgehensweise: Analysieren von verwaltetem Code auf Codefehler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise analysieren Sie mit dem Code Analysetool ein verwaltetes Projekt mit Code Fehlern.

 Diese exemplarische Vorgehensweise führt Sie durch den Prozess der Verwendung der Code Analyse zum Analysieren Ihrer .NET-verwalteten Codeassemblys, um die Konformität mit den Microsoft .NET Framework-Entwurfs Richtlinien zu erfüllen.

 In dieser exemplarischen Vorgehensweise haben Sie Folgendes:

- Analysieren und korrigieren Sie Code Fehler Warnungen.

## <a name="prerequisites"></a>Erforderliche Voraussetzungen

- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]

## <a name="create-a-class-library"></a>Erstellen einer Klassenbibliothek

#### <a name="to-create-a-class-library"></a>So erstellen Sie eine Klassenbibliothek

1. Klicken Sie im Menü **Datei** von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] auf **neu** , und klicken Sie dann auf **Projekt**.

2. Klicken Sie im Dialogfeld **Neues Projekt** unter **Projekttypen**auf **Visualisierung C#** .

3. Wählen Sie unter **Vorlagen**die Option **Klassenbibliothek**aus.

4. Geben Sie im Textfeld **Name den Namen** **CodeAnalysisManagedDemo** ein, und klicken Sie dann auf **OK**.

5. Nachdem das Projekt erstellt wurde, öffnen Sie die Datei Class1.cs.

6. Ersetzen Sie den vorhandenen Text in Class1.cs durch den folgenden Code:

     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`

7. Speichern Sie die Datei Class1.cs.

## <a name="analyze-the-project"></a>Analysieren des Projekts

#### <a name="to-analyze-a-managed-project-for-code-defects"></a>So analysieren Sie ein verwaltetes Projekt auf Code Fehler

1. Wählen Sie das Projekt "CodeAnalysisManagedDemo" in **Projektmappen-Explorer**aus.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Die Eigenschaften Seite "CodeAnalysisManagedDemo" wird angezeigt.

3. Klicken Sie auf **Code Analyse**.

4. Stellen Sie sicher, dass die Option **Code Analyse für Build aktivieren (definiert CODE_ANALYSIS-Konstante**) aktiviert ist.

5. Wählen Sie in der Dropdown Liste **diesen Regelsatz ausführen** die Option **Microsoft alle Regeln**aus.

6. Klicken Sie im Menü **Datei** auf **ausgewählte Elemente speichern**, und schließen Sie dann die Eigenschaften Seiten von ManagedDemo.

7. Klicken Sie im Menü **Erstellen** auf **ManagedDemo erstellen**.

     Die CodeAnalysisManagedDemo-projektbuildwarnungen werden in den Fenstern " **Code Analyse** " und " **Ausgabe** " gemeldet.

     Wenn das **Code Analyse** Fenster nicht angezeigt wird, wählen Sie im Menü **analysieren** die Option **Fenster** aus, und **Wählen Sie dann Code Analyse**aus.

## <a name="correct-the-code-analysis-issues"></a>Beheben der Code Analyse Probleme

#### <a name="to-correct-code-analysis-rule-violations"></a>So korrigieren Sie Verstöße gegen Code Analyse Regeln

1. Klicken Sie im Menü **Ansicht** auf **Fehlerliste**.

     Je nachdem, welches Entwickler Profil Sie ausgewählt haben, müssen Sie möglicherweise im Menü **Ansicht** auf **andere Fenster** zeigen und dann auf **Fehlerliste**klicken.

2. Klicken Sie in **Projektmappen-Explorer**auf **alle Dateien anzeigen**.

3. Erweitern Sie als nächstes den Knoten Eigenschaften, und öffnen Sie dann die Datei AssemblyInfo.cs.

4. Verwenden Sie Folgendes, um Warnungen zu korrigieren:

- [CA1014: Markieren Sie Assemblys mit CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: "Demo" sollte mit dem CLSCompliantAttribute gekennzeichnet werden, und der Wert sollte "true" lauten.

  - Fügen Sie der Datei AssemblyInfo.cs den Code `using``System;` hinzu.

       Fügen Sie als nächstes den Code `[assembly: CLSCompliant(true)]` am Ende der AssemblyInfo.cs-Datei hinzu.

       Erstellen Sie das Projekt neu.

- [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Fügen Sie dieser Klasse den folgenden Konstruktor hinzu: öffentliche Demo (Zeichenfolge)

  - Fügen Sie der-Klasse `demo` den Konstruktor-`public demo (String s) : base(s) { }` hinzu.

- [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Fügen Sie dieser Klasse den folgenden Konstruktor hinzu: öffentliche Demo (Zeichenfolge, Ausnahme)

  - Fügen Sie der-Klasse `demo` den Konstruktor-`public demo (String s, Exception e) : base(s, e) { }` hinzu.

- [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Fügen Sie dieser Klasse den folgenden Konstruktor hinzu: geschützte Demo (SerializationInfo, StreamingContext)

  - Fügen Sie den Code `using System.Runtime.Serialization;` am Anfang der Class1.cs-Datei hinzu.

       Fügen Sie als nächstes den Konstruktor hinzu `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

       Erstellen Sie das Projekt neu.

- [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: Fügen Sie dieser Klasse den folgenden Konstruktor hinzu: öffentliche Demo ()

  - Fügen Sie der-Klasse `demo` den Konstruktor-`public demo () : base() { }` hinzu **.**

       Erstellen Sie das Projekt neu.

- [CA1709: Bezeichner müssen ordnungsgemäß geschrieben werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: korrigieren Sie die Schreibweise des Namespace namens "Testcode", indem Sie ihn in "Testcode" ändern.

  - Ändern Sie die Schreibweise des Namespace `testCode` in `TestCode`.

- [CA1709: Bezeichner müssen ordnungsgemäß geschrieben werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: korrigieren Sie die Schreibweise des Typnamens "Demo", indem Sie Sie in "Demo" ändern.

  - Ändern Sie den Namen des Members in `Demo`.

- [CA1709: Bezeichner müssen ordnungsgemäß geschrieben werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. Naming: korrigieren Sie die Schreibweise des Element namens "Item", indem Sie ihn in "Item" ändern.

  - Ändern Sie den Namen des Members in `Item`.

- [CA1710: Bezeichner sollten ein korrektes Suffix aufweisen](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. Naming: benennen Sie "Testcode. Demo" um, damit Sie auf "Exception" enden.

  - Ändern Sie den Namen der Klasse und deren Konstruktoren in `DemoException`.

- [CA2210: Assemblys müssen gültige starke Namen aufweisen](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Signieren Sie "ManagedDemo" mit einem Schlüssel mit starkem Namen.

  - Klicken Sie im Menü **Projekt** auf **ManagedDemo-Eigenschaften**.

       Die Projekteigenschaften werden angezeigt.

       Klicken Sie auf **Signatur**.

       Aktivieren Sie das Kontrollkästchen **Assembly signieren** .

       Wählen Sie in der Liste **Schlüsseldatei für Zeichen folgen Name** auswählen **\<New... >** .

       Das Dialogfeld Schlüssel für einen **starken Namen erstellen** wird angezeigt.

       Geben Sie im **Schlüssel Dateinamen den Namen**TestKey ein.

       Geben Sie ein Kennwort ein, und klicken Sie auf **OK**

       Klicken Sie im Menü **Datei** auf **ausgewählte Elemente speichern**, und schließen Sie dann die Eigenschaften Seiten.

       Erstellen Sie das Projekt neu.

- [CA2237: Markieren Sie iserialisierbare Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: Fügen Sie ein [serialisierbares]-Attribut zum Typ ' Demo ' hinzu, da dieser Typ iserialisierbar implementiert.

  - Fügen Sie der Klasse `demo` das `[Serializable ()]`-Attribut hinzu.

       Erstellen Sie das Projekt neu.

  Nachdem Sie die Änderungen vorgenommen haben, sollte die Class1.cs-Datei wie folgt aussehen:

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

## <a name="exclude-code-analysis-warnings"></a>Code Analyse Warnungen ausschließen

#### <a name="to-exclude-code-defect-warnings"></a>So schließen Sie Code Fehler Warnungen aus

1. Führen Sie für jede der verbleibenden Warnungen die folgenden Schritte aus:

   1. Wählen Sie im Fenster "Code Analyse" die Warnung aus.

   2. Wählen Sie **Aktionen**und dann **Meldung unterdrücken**, und wählen Sie dann **in Projekt Unterdrückungs Datei aus**.

      Weitere Informationen finden Sie unter Gewusst [wie: Unterdrücken von Warnungen mithilfe des Menü Elements](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md) .

2. Erstellen Sie das Projekt neu.

    Das Projekt wird ohne Warnungen oder Fehler erstellt.
