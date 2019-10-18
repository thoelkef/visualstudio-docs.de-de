---
title: Exemplarische Vorgehensweise zum Analysieren von verwaltetem Code auf Code Fehler | Microsoft-Dokumentation
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 79855f6915bbb0ed15bfd09f99fab0403290f09e
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448716"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Exemplarische Vorgehensweise: Verwenden der statischen Code Analyse zum Ermitteln von Code Fehlern

In dieser exemplarischen Vorgehensweise analysieren Sie ein verwaltetes Projekt mit Code Fehlern, indem Sie die Legacy Code Analyse verwenden.

In diesem Artikel wird beschrieben, wie Sie die Legacy Analyse verwenden, um Ihre .NET-Assemblys mit verwaltetem Code auf Übereinstimmung mit den .net-Entwurfs Richtlinien zu analysieren.

## <a name="create-a-class-library"></a>Erstellen einer Klassenbibliothek

1. Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt aus der Vorlage **Klassenbibliothek (.NET Framework)** .

1. Nennen Sie das Projekt " **CodeAnalysisManagedDemo**".

1. Nachdem das Projekt erstellt wurde, öffnen Sie die Datei *Class1.cs* .

1. Ersetzen Sie den vorhandenen Text in Class1.cs durch den folgenden Code:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Speichern Sie die Datei Class1.cs.

## <a name="analyze-the-project-for-code-defects"></a>Analysieren des Projekts auf Code Fehler

1. Wählen Sie das Projekt "CodeAnalysisManagedDemo" in **Projektmappen-Explorer**aus.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

   Die Eigenschaften Seite "CodeAnalysisManagedDemo" wird angezeigt.

3. Wählen Sie die Registerkarte **Code Analyse** aus.

::: moniker range="vs-2017"

4. Stellen Sie sicher, dass **Code Analyse für Build aktivieren** ausgewählt ist.

5. Wählen Sie in der Dropdown Liste **diesen Regelsatz ausführen** die Option **Microsoft alle Regeln**aus.

::: moniker-end

::: moniker range=">=vs-2019"

4. Stellen Sie sicher, dass im Abschnitt **binäre Analysen** die Option **auf Build ausführen** ausgewählt ist.

5. Wählen Sie in der Dropdown Liste **aktive Regeln** die Option **Microsoft alle Regeln**aus.

::: moniker-end

6. Klicken Sie im Menü **Datei** auf **ausgewählte Elemente speichern**, und schließen Sie dann die Eigenschaften Seiten.

7. Klicken Sie im Menü **Erstellen** auf **CodeAnalysisManagedDemo erstellen**.

    Die CodeAnalysisManagedDemo-projektbuildwarnungen werden im Fenster **Fehlerliste** und **Ausgabe** angezeigt.

## <a name="correct-the-code-analysis-issues"></a>Beheben der Code Analyse Probleme

1. Wählen Sie im Menü **Ansicht** die Option **Fehlerliste**aus.

    Je nachdem, welches Entwickler Profil Sie ausgewählt haben, müssen Sie möglicherweise im Menü **Ansicht** auf **andere Fenster** zeigen und dann **Fehlerliste**auswählen.

1. Klicken Sie im **Projektmappen-Explorer** auf **Alle Dateien anzeigen**.

1. Erweitern Sie den Knoten Eigenschaften, und öffnen Sie dann die Datei *AssemblyInfo.cs* .

1. Verwenden Sie die folgenden Tipps, um die Warnungen zu beheben:

   [CA1014: Assemblys mit CLSCompliantAttribute markieren](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Fügen Sie den Code `[assembly: CLSCompliant(true)]` am Ende der AssemblyInfo.cs-Datei hinzu.

   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Fügen Sie den Konstruktor `public demo (String s) : base(s) { }` der Klasse `demo` hinzu.

   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Fügen Sie den Konstruktor `public demo (String s, Exception e) : base(s, e) { }` der Klasse `demo` hinzu.

   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Fügen Sie den Konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` der Klassen-Demo hinzu. Sie müssen auch eine `using`-Anweisung für <xref:System.Runtime.Serialization?displayProperty=fullName> hinzufügen.

   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Fügen Sie den Konstruktor `public demo () : base() { }` der Klasse `demo` hinzu.

   [CA1709:](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)Bezeichner müssen ordnungsgemäß geschrieben werden: Ändern Sie die Schreibweise des Namespace `testCode` in `TestCode`.

   [CA1709:](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)Bezeichner müssen ordnungsgemäß geschrieben werden: Ändern Sie den Namen des Members in `Demo`.

   [CA1709:](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)Bezeichner müssen ordnungsgemäß geschrieben werden: Ändern Sie den Namen des Members in `Item`.

   [CA1710: Bezeichner sollten ein korrektes Suffix aufweisen](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Ändern Sie den Namen der Klasse und deren Konstruktoren in `DemoException`.

   [CA2237: Markieren von iserialisierbaren Typen mit SerializableAttribute](../code-quality/ca2237.md): Fügen Sie der Klasse `demo` das `[Serializable ()]` Attribut hinzu.

   [CA2210: Assemblys müssen gültige starke Namen aufweisen](../code-quality/ca2210.md): Signieren von "CodeAnalysisManagedDemo" mit einem Schlüssel mit starkem Namen:

   1. Wählen Sie im Menü **Projekt** die Option **CodeAnalysisManagedDemo-Eigenschaften**aus.

      Die Projekteigenschaften werden angezeigt.

   1. Wählen Sie die Registerkarte **Signierung** aus.

   1. Aktivieren Sie das Kontrollkästchen **Assembly signieren** .

   1. Wählen Sie in der Liste **Schlüsseldatei für Zeichen folgen Name auswählen** **\<new->** aus.

      Das Dialogfeld Schlüssel für einen **starken Namen erstellen** wird angezeigt.

   1. Geben Sie für **Schlüssel Dateiname den Namen** **TestKey**ein.

   1. Geben Sie ein Kennwort ein, und wählen Sie dann **OK**aus.

   1. Wählen Sie im Menü **Datei** die Option **ausgewählte Elemente speichern**aus, und schließen Sie dann die Eigenschaften Seiten.

   Nachdem Sie alle Änderungen vorgenommen haben, sollte die Class1.cs-Datei wie folgt aussehen:

   ```csharp
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

1. Erstellen Sie das Projekt neu.

## <a name="exclude-code-analysis-warnings"></a>Code Analyse Warnungen ausschließen

1. Führen Sie für jede der verbleibenden Warnungen die folgenden Schritte aus:

    1. Wählen Sie im **Fehlerliste**die Warnung aus.

    1. Klicken Sie im Kontextmenü (Kontextmenü) auf  > **in Unterdrückungs Datei**unter **drücken**.

1. Erstellen Sie das Projekt neu.

     Das Projekt wird ohne Warnungen oder Fehler erstellt.

## <a name="see-also"></a>Siehe auch

[Code Analyse für verwalteten Code](../code-quality/code-analysis-for-managed-code-overview.md)
