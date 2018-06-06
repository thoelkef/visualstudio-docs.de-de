---
title: Exemplarische Vorgehensweise Analysieren von verwaltetem Code auf Codefehler | Microsoft Docs
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a353d7a61f9bc1dbb83d37ad419c3d2fbdf656ba
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746558"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Exemplarische Vorgehensweise: Analysieren von verwalteter Code für Code Fehlern

In dieser exemplarischen Vorgehensweise müssen Sie ein verwaltetes Projekt Codefehler analysieren, mit dem Code Analysis-Tool.

Diese exemplarische Vorgehensweise führt Sie durch die Verwendung von Codeanalyse Ihrer verwalteten Codeassemblys zur Erhaltung der Konformität mit den Microsoft .NET Framework-Entwurfsrichtlinien analysieren.

## <a name="create-a-class-library"></a>Erstellen einer Klassenbibliothek

### <a name="to-create-a-class-library"></a>So erstellen Sie eine Klassenbibliothek

1. Wählen Sie im Menü **Datei** die Befehlsfolge **Neu** > **Projekt...** aus.

1. In der **neues Projekt** Dialogfeld erweitern Sie **installiert** > **Visual C#-**, und wählen Sie dann **Windows Desktop**.

1. Wählen Sie die **-Klassenbibliothek ((.NET Framework)** Vorlage.

1. In der **Namen** Textfeld **CodeAnalysisManagedDemo** , und klicken Sie dann auf **OK**.

1. Nachdem das Projekt erstellt wurde, öffnen Sie die *"Class1.cs"* Datei.

1. Ersetzen Sie den vorhandenen Text in "Class1.cs" durch den folgenden Code ein:

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

1. Speichern Sie die Datei "Class1.cs".

## <a name="analyze-the-project"></a>Analysieren Sie das Projekt

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Um ein verwaltetes Projekt Codefehler zu analysieren.

1. Wählen Sie das Projekt CodeAnalysisManagedDemo **Projektmappen-Explorer**.

1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Die Eigenschaftenseite CodeAnalysisManagedDemo wird angezeigt.

1. Wählen Sie die **Codeanalyse** Registerkarte.

1. Stellen Sie sicher, dass **Codeanalyse für Build aktivieren** aktiviert ist.

1. Aus der **diesen Regelsatz ausführen** Dropdown-Liste **Microsoft alle Regeln**.

1. Auf der **Datei** Menü klicken Sie auf **ausgewählte Elemente speichern**, und klicken Sie dann die Eigenschaftenseiten zu schließen.

1. Auf der **erstellen** Menü klicken Sie auf **erstellen CodeAnalysisManagedDemo**.

    Die CodeAnalysisManagedDemo Projekt Buildwarnungen werden angezeigt, der **Fehlerliste** und **Ausgabe** Windows.

## <a name="correct-the-code-analysis-issues"></a>Beheben Sie die Codeanalysefehler

### <a name="to-correct-code-analysis-rule-violations"></a>So beheben Sie codeanalyseverstöße Regel

1. Auf der **Ansicht** Menü wählen **Fehlerliste**.

    Abhängig von der Developer-Profil, das Sie ausgewählt haben, müssen Sie möglicherweise ein zeigen Sie auf **Weitere Fenster** auf die **Ansicht** Menü, und wählen Sie dann **Fehlerliste**.

1. In **Projektmappen-Explorer**, wählen Sie **alle Dateien anzeigen**.

1. Erweitern Sie den Knoten für die Eigenschaften, und öffnen Sie die *AssemblyInfo.cs* Datei.

1. Verwenden Sie die folgenden Tipps, um die Warnungen zu beheben:

   [CA1014: Assemblys mit CLSCompliantAttribute markieren](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: "Demo" sollte mit CLSCompliantAttribute markiert sein, und der Wert sollte "true" sein.

   1. Fügen Sie den Code `using System;` der Datei AssemblyInfo.cs.

   1. Als Nächstes fügen Sie den Code `[assembly: CLSCompliant(true)]` bis zum Ende der Datei AssemblyInfo.cs.

   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie diese Klasse den folgenden Konstruktor hinzu: public demo(String)

   1. Fügen Sie den Konstruktor `public demo (String s) : base(s) { }` der Klasse `demo`.

   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie diese Klasse den folgenden Konstruktor hinzu: public Demo ("String", "Ausnahme")

   1. Fügen Sie den Konstruktor `public demo (String s, Exception e) : base(s, e) { }` der Klasse `demo`.

   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie diese Klasse den folgenden Konstruktor hinzu: protected Demo (SerializationInfo, StreamingContext)

   1. Fügen Sie den Code `using System.Runtime.Serialization;` am Anfang der Datei "Class1.cs".

   1. Als Nächstes fügen Sie den Konstruktor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Standardausnahmekonstruktoren implementieren](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Fügen Sie diese Klasse den folgenden Konstruktor hinzu: public demo()

   1. Fügen Sie den Konstruktor `public demo () : base() { }` der Klasse `demo` **.**

   [CA1709: Bezeichner sollten werden Groß-/Kleinschreibung beachtet ordnungsgemäß](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Groß-/Kleinschreibung des Namespacenamens 'TestCode' in 'TestCode'.

   1. Ändern Sie die Groß-/Kleinschreibung des Namespaces `testCode` auf `TestCode`.

   [CA1709: Bezeichner sollten werden Groß-/Kleinschreibung beachtet ordnungsgemäß](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Groß-/Kleinschreibung des Typnamens "Demo" auf "Demo".

   1. Ändern Sie den Namen des Members, um `Demo`.

   [CA1709: Bezeichner sollten werden Groß-/Kleinschreibung beachtet ordnungsgemäß](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Korrigieren Sie die Groß-/Kleinschreibung des Namens "Item", "Element".

   1. Ändern Sie den Namen des Members, um `Item`.

   [CA1710: Bezeichner sollten richtiges Suffix aufweisen](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Rename 'Testcode.Demo dass lautet"Ende"Ausnahme".

   1. Ändern Sie den Namen der Klasse und ihre Konstruktoren `DemoException`.

   [CA2210: Assemblys müssen gültige starke Namen aufweisen](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): "CodeAnalysisManagedDemo" mit einem starken Namensschlüssel signieren.

   1. Auf der **Projekt** Menü wählen **CodeAnalysisManagedDemo Eigenschaften**.

      Die Projekteigenschaften werden angezeigt.

   1. Wählen Sie die Registerkarte **Signierung** aus.

   1. Wählen Sie die **zum Signieren der Assembly** Kontrollkästchen.

   1. In der **wählen Sie eine Schlüsseldatei mit starkem Namen** Liste  **\<neu... >**.

      Die **Schlüssel für einen starken Namen erstellen** Dialogfeld wird angezeigt.

   1. In der **Schlüsseldateiname**, TestKey geben.

   1. Geben Sie ein Kennwort ein, und wählen Sie dann **OK**.

   1. Auf der **Datei** Menü wählen **ausgewählte Elemente speichern**, und schließen Sie dann auf die Eigenschaftenseiten.

   [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Fügen Sie einem [Serializable] "demo" geben, wie dieser Typ ISerializable implementiert.

   1. Hinzufügen der `[Serializable ()]` -Attribut der Klasse `demo`.

   Nachdem Sie die Änderungen abgeschlossen haben, sollte die Datei "Class1.cs" wie folgt aussehen:

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

## <a name="exclude-code-analysis-warnings"></a>Ausschließen von codeanalysewarnungen

### <a name="to-exclude-code-defect-warnings"></a>Auszuschließende defekt Code (Warnungen)

1. Führen Sie für jede der verbleibenden Warnungen folgende Schritte aus:

    1. Wählen Sie die Warnung in der **Fehlerliste**.

    1. Wählen Sie im Menü mit der rechten Maustaste oder Kontext **unterdrücken** > **In Unterdrückungsdatei**.

1. Erstellen Sie das Projekt neu.

     Das Projekt erstellt, ohne alle Warnungen oder Fehler.

## <a name="see-also"></a>Siehe auch

[Codeanalyse für verwalteten code](../code-quality/code-analysis-for-managed-code-overview.md)