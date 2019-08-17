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
ms.openlocfilehash: 4a00fdb2a41a03554113f2ecb626185aab2c74d5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547997"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Exemplarische Vorgehensweise: Verwenden der statischen Code Analyse zum Ermitteln von Code Fehlern

In dieser exemplarischen Vorgehensweise analysieren Sie ein verwaltetes Projekt mit Code Fehlern, indem Sie die Legacy Code Analyse verwenden.

In diesem Artikel wird beschrieben, wie Sie die Legacy Analyse verwenden, um Ihre .NET-Assemblys mit verwaltetem Code auf Übereinstimmung mit den .net-Entwurfs Richtlinien zu analysieren.

## <a name="create-a-class-library"></a>Erstellen einer Klassenbibliothek

### <a name="to-create-a-class-library"></a>So erstellen Sie eine Klassenbibliothek

1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu** > **Projekt** aus.

1. Erweitern Sie im Dialogfeld **Neues Projekt** die Option **installiertes** > **visuelles C#** Element, und wählen Sie dann **Windows-Desktop**aus.

1. Wählen Sie die Vorlage **Klassenbibliothek (.NET Framework)** aus.

1. Geben Sie im Textfeld **Name den Namen** **CodeAnalysisManagedDemo** ein, und klicken Sie dann auf **OK**.

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

## <a name="analyze-the-project"></a>Analysieren des Projekts

### <a name="to-analyze-a-managed-project-for-code-defects"></a>So analysieren Sie ein verwaltetes Projekt auf Code Fehler

1. Wählen Sie das Projekt "CodeAnalysisManagedDemo" in **Projektmappen-Explorer**aus.

1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Die Eigenschaften Seite "CodeAnalysisManagedDemo" wird angezeigt.

1. Wählen Sie die Registerkarte **Code Analyse** aus.

1. Vergewissern Sie sich, dass die Option **Code Analyse für Build aktivieren** aktiviert ist.

1. Wählen Sie in der Dropdown Liste **diesen Regelsatz ausführen** die Option **Microsoft alle Regeln**aus.

1. Klicken Sie im Menü **Datei** auf **ausgewählte Elemente speichern**, und schließen Sie dann die Eigenschaften Seiten.

1. Klicken Sie im Menü **Erstellen** auf **CodeAnalysisManagedDemo erstellen**.

    Die CodeAnalysisManagedDemo-projektbuildwarnungen werden im Fenster **Fehlerliste** und **Ausgabe** angezeigt.

## <a name="correct-the-code-analysis-issues"></a>Beheben der Code Analyse Probleme

### <a name="to-correct-code-analysis-rule-violations"></a>So korrigieren Sie Verstöße gegen Code Analyse Regeln

1. Wählen Sie im Menü **Ansicht** die Option **Fehlerliste**aus.

    Je nachdem, welches Entwickler Profil Sie ausgewählt haben, müssen Sie möglicherweise im Menü **Ansicht** auf **andere Fenster** zeigen und dann **Fehlerliste**auswählen.

1. Klicken Sie im **Projektmappen-Explorer** auf **Alle Dateien anzeigen**.

1. Erweitern Sie den Knoten Eigenschaften, und öffnen Sie dann die Datei *AssemblyInfo.cs* .

1. Verwenden Sie die folgenden Tipps, um die Warnungen zu beheben:

   [CA1014: Assemblys mit CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)markieren: Microsoft. Design: "Demo" sollte mit dem CLSCompliantAttribute gekennzeichnet werden, und der Wert sollte "true" lauten.

   1. Fügen Sie den `using System;` Code der AssemblyInfo.cs-Datei hinzu.

   1. Fügen Sie als nächstes den `[assembly: CLSCompliant(true)]` Code am Ende der AssemblyInfo.cs-Datei hinzu.

   [CA1032: Standardausnahmekonstruktoren](../code-quality/ca1032-implement-standard-exception-constructors.md)implementieren: Microsoft.Design: Fügen Sie dieser Klasse den folgenden Konstruktor hinzu: öffentliche Demo (Zeichenfolge)

   1. Fügen Sie der- `public demo (String s) : base(s) { }` Klasse `demo`den-Konstruktor hinzu.

   [CA1032: Standardausnahmekonstruktoren](../code-quality/ca1032-implement-standard-exception-constructors.md)implementieren: Microsoft.Design: Fügen Sie dieser Klasse den folgenden Konstruktor hinzu: öffentliche Demo (Zeichenfolge, Ausnahme)

   1. Fügen Sie der- `public demo (String s, Exception e) : base(s, e) { }` Klasse `demo`den-Konstruktor hinzu.

   [CA1032: Standardausnahmekonstruktoren](../code-quality/ca1032-implement-standard-exception-constructors.md)implementieren: Microsoft.Design: Fügen Sie dieser Klasse den folgenden Konstruktor hinzu: geschützte Demo (SerializationInfo, StreamingContext)

   1. Fügen Sie den `using System.Runtime.Serialization;` Code am Anfang der Class1.cs-Datei hinzu.

   1. Fügen Sie als nächstes den Konstruktor hinzu.`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Standardausnahmekonstruktoren](../code-quality/ca1032-implement-standard-exception-constructors.md)implementieren: Microsoft.Design: Fügen Sie dieser Klasse den folgenden Konstruktor hinzu: öffentliche Demo ()

   1. Fügen Sie der- `public demo () : base() { }` Klasse `demo`den-Konstruktor hinzu **.**

   [CA1709: Bezeichner sollten korrekt](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)geschrieben werden: Microsoft.Naming: Korrigieren Sie die Schreibweise des Namespace namens "Testcode", indem Sie ihn in "Testcode" ändern.

   1. Ändern Sie die Groß-/Kleinschreibung `TestCode`des-Namespace `testCode` in.

   [CA1709: Bezeichner sollten korrekt](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)geschrieben werden: Microsoft.Naming: Korrigieren Sie die Schreibweise des Typnamens "Demo", indem Sie Sie in "Demo" ändern.

   1. Ändern Sie den Namen des Members in `Demo`.

   [CA1709: Bezeichner sollten korrekt](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)geschrieben werden: Microsoft.Naming: Korrigieren Sie die Schreibweise des Element namens "Item", indem Sie ihn in "Item" ändern.

   1. Ändern Sie den Namen des Members in `Item`.

   [CA1710: Bezeichner sollten ein korrektes](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)Suffix aufweisen: Microsoft.Naming: Benennen Sie "Testcode. Demo" in "Exception" um.

   1. Ändern Sie den Namen der Klasse und deren Konstruktoren in `DemoException`.

   [CA2210: Assemblys müssen gültige starke](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)Namen haben: Signieren Sie "CodeAnalysisManagedDemo" mit einem Schlüssel mit starkem Namen.

   1. Wählen Sie im Menü **Projekt** die Option **CodeAnalysisManagedDemo-Eigenschaften**aus.

      Die Projekteigenschaften werden angezeigt.

   1. Wählen Sie die Registerkarte **Signierung** aus.

   1. Aktivieren Sie das Kontrollkästchen **Assembly signieren** .

   1. Wählen Sie  **\<in der Liste Schlüsseldatei für Zeichen folgen Namen auswählen die Option neu... aus. >** .

      Das Dialogfeld Schlüssel für einen **starken Namen erstellen** wird angezeigt.

   1. Geben Sie im **Schlüssel Dateinamen den Namen**TestKey ein.

   1. Geben Sie ein Kennwort ein, und wählen Sie dann **OK**

   1. Wählen Sie im Menü **Datei** die Option **ausgewählte Elemente speichern**aus, und schließen Sie dann die Eigenschaften Seiten.

   [CA2237: Markieren Sie iserialisierbare Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Fügen Sie ein [serialisierbares]-Attribut zum Typ ' Demo ' hinzu, da dieser Typ iserialisierbar implementiert.

   1. Fügen Sie `[Serializable ()]` der-Klasse `demo`das-Attribut hinzu.

   Nachdem Sie die Änderungen vorgenommen haben, sollte die Class1.cs-Datei wie folgt aussehen:

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

    1. Wählen Sie im Kontextmenü (Kontextmenü) die Option**in Unterdrückungs Datei**unter **drücken** > aus.

1. Erstellen Sie das Projekt neu.

     Das Projekt wird ohne Warnungen oder Fehler erstellt.

## <a name="see-also"></a>Siehe auch

[Code Analyse für verwalteten Code](../code-quality/code-analysis-for-managed-code-overview.md)