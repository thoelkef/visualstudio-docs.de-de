---
title: Testen Ihres Codes mit dem Live Unit Testing in Visual Studio 2017 | Microsoft-Dokumentation | Microsoft-Dokumentation
ms.date: 08/31/2017
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 2f2c8ba68419b23d2e74b82e23640c68a6f534aa
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2018
---
# <a name="get-started-with-live-unit-testing-in-visual-studio"></a>Erste Schritte mit Live Unit Testing in Visual Studio

Wenn Sie Live Unit Testing in einer Visual Studio-Projektmappe aktivieren, werden beim Live Unit Testing Ihre Testabdeckung und der Status Ihrer Tests dargestellt. Zudem werden bei jeder Änderung Ihres Codes dynamisch Tests ausgeführt. Live Unit Testing ermöglicht eine sofortige Benachrichtigung, wenn Ihr Code durch Änderungen außer Kraft gesetzt wurde, und gibt Bereiche an, für die weitere Tests erforderlich sind. 

Live Unit Testing kann zum Testen von Projektmappen für .NET Framework oder .NET Core verwendet werden. In diesem Tutorial erlernen Sie die Verwendung von Live Unit Testing, indem Sie eine einfache Klassenbibliothek für .NET Standard erstellen. Des Weiteren erstellen Sie zu Testzwecken ein MSTest-Projekt für .NET Core.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
Die vollständige C#-Projektmappe kann aus dem Repository [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) auf GitHub heruntergeladen werden.
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
Die vollständige Visual Basic-Projektmappe kann aus dem Repository [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/visual-basic/UtilityLibraries/) auf GitHub heruntergeladen werden.

---

## <a name="prerequisites"></a>Erforderliche Komponenten

Für dieses Tutorial ist die Installation von Visual Studio 2017 Enterprise Edition Version 15.3 mit der .NET Core 2.0-Arbeitsauslastung erforderlich.

## <a name="create-the-solution-and-the-class-library-project"></a>Projektmappe und Klassenbibliotheksprojekt erstellen

Erstellen Sie zunächst eine Visual Studio-Projektmappe mit dem Namen `UtilityLibraries`, die ein einfaches .NET-Standard-Klassenbibliotheksprojekt, `StringLibrary`, enthält. Sie können `StringLibrary` in C# oder Visual Basic schreiben. 

Die Projektmappe ist nur ein Container für mindestens ein Projekt. Öffnen Sie Visual Studio 2017 und führen Sie zum Erstellen der Projektmappe die folgenden Schritte aus:

1. Wählen Sie aus dem Hauptebenenmenü von Visual Studio die Option **Datei**, **Neu**, **Projekt** aus.

1. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Andere Projekttypen**, und wählen Sie **Visual Studio-Projektmappen** aus. Wählen Sie im rechten Bereich die Vorlage **Leere Projektmappe** aus, und geben Sie `UtilityLibraries` in das Textfeld **Name** ein. Siehe hierzu die folgende Abbildung:

   ![Das Dialogfeld **Neues Projekt**](./media/lut-start/new-solution.png)

1. Klicken Sie auf **OK**, um die Projektmappe zu erstellen.
 
Nach der Erstellung der Projektmappe erstellen Sie eine Klassenbibliothek mit dem Namen `StringLibrary`, die einige Erweiterungsmethoden für das Arbeiten mit Zeichenfolgen enthält.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe `UtilityLibraries`, und wählen Sie **Hinzufügen** > **Neues Projekt** aus.

1. Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** auf den C#-Knoten, und wählen Sie anschließend **.NET Standard** aus. 

   > [!NOTE]
   > Da das Ziel unserer Bibliothek die .NET Standard-Implementierung und keine bestimmte .NET-Implementierung ist, kann sie über eine beliebige .NET-Implementierung aufgerufen werden, die diese .NET Standard-Version unterstützt. Weitere Informationen finden Sie unter [.NET Standard](/dotnet/standard/net-standard).

1. Wählen Sie im rechten Bereich die Vorlage **Klassenbibliothek (.NET Standard)** aus, und geben Sie `StringLibrary` in das Textfeld **Name** ein. Siehe hierzu die folgende Abbildung:

   ![Dialogfeld **Neues Projekt hinzufügen**](./media/lut-start/add-project-cs.png)

1. Klicken Sie auf **OK**, um das Projekt zu erstellen.

1. Ersetzen Sie sämtlichen vorhandenen Code im Codefenster durch den folgenden Code:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   `StringLibrary` verfügt über drei statische Methoden:

      - `StartsWithUpper` gibt `true` zurück, wenn eine Zeichenfolge mit einem Großbuchstaben beginnt; andernfalls wird `false` zurückgegeben.
      
      - `StartsWithLower` gibt `true` zurück, wenn eine Zeichenfolge mit einem Kleinbuchstaben beginnt; andernfalls wird `false` zurückgegeben.
     
      - `HasEmbeddedSpaces` gibt `true` zurück, wenn eine Zeichenfolge mit einem Leerzeichen beginnt; andernfalls wird `false` zurückgegeben.
    
1.  Wählen Sie aus dem Hauptebenenmenü von Visual Studio die Option **Erstellen**, **Projektmappe erstellen** aus. Visual Studio müsste Ihre Bibliothek erfolgreich erstellen.
 
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe `UtilityLibraries`, und wählen Sie **Hinzufügen** > **Neues Projekt** aus.

1. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** den Visual Basic-Knoten und anschließend **.NET Standard** aus. 

   > [!NOTE]
   > Da das Ziel unserer Bibliothek die .NET Standard-Implementierung und keine bestimmte .NET-Implementierung ist, kann sie über eine beliebige .NET-Implementierung aufgerufen werden, die diese .NET Standard-Version unterstützt. Weitere Informationen finden Sie unter [.NET Standard](/dotnet/standard/net-standard).

1. Wählen Sie im rechten Bereich die Vorlage **Klassenbibliothek (.NET Standard)** aus, und geben Sie `StringLibrary` in das Textfeld **Name** ein. Siehe hierzu die folgende Abbildung:

   ![Dialogfeld **Neues Projekt hinzufügen**](./media/lut-start/add-project-vb.png)

1. Klicken Sie auf **OK**, um das Projekt zu erstellen.

1. Ersetzen Sie sämtlichen vorhandenen Code im Codefenster durch den folgenden Code:

   [!code-vb[StringLibrary source code](samples/visual-basic/utilitylibraries/stringlibrary/class1.vb)]

   `StringLibrary` verfügt über drei statische Methoden:

      - `StartsWithUpper` gibt `true` zurück, wenn eine Zeichenfolge mit einem Großbuchstaben beginnt; andernfalls wird `false` zurückgegeben.
      
      - `StartsWithLower` gibt `true` zurück, wenn eine Zeichenfolge mit einem Kleinbuchstaben beginnt; andernfalls wird `false` zurückgegeben.
     
      - `HasEmbeddedSpaces` gibt `true` zurück, wenn eine Zeichenfolge mit einem Leerzeichen beginnt; andernfalls wird `false` zurückgegeben.
    
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das StringLibrary-Projekt, und wählen Sie anschließend **Eigenschaften** aus. Löschen Sie auf der Registerkarte **Anwendung** den Text im Textfeld **Stammnamespace**. Sie hierzu die folgende Abbildung. Der Stammnamespace wird von der [Namespace-Anweisung](/dotnet/visual-basic/language-reference/statements/namespace-statement) im Quellcode definiert.

   ![Das Dialogfeld „Projekteigenschaften für ein Visual Basic-Projekt“](./media/lut-start/vb-properties.png)
 
1.  Wählen Sie aus dem Hauptebenenmenü von Visual Studio die Option **Erstellen**, **Projektmappe erstellen** aus. Visual Studio müsste Ihre Bibliothek erfolgreich erstellen.

---

## <a name="create-the-test-project"></a>Erstellen des Testprojekts

Im nächsten Schritt wird das Komponententestprojekt zum Testen der `StringLibrary`-Bibliothek erstellt. Führen Sie die folgenden Schritte aus, um die Komponententests zu erstellen:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe `UtilityLibraries`, und wählen Sie **Hinzufügen** > **Neues Projekt** aus.

1. Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** auf den C#-Knoten, und wählen Sie anschließend **.NET Core** aus. 

   > [!NOTE]
   > Sie müssen die Komponententests nicht in derselben Sprache wie die Klassenbibliothek schreiben.

1. Wählen Sie im rechten Bereich die Vorlage **Komponententestprojekt (.NET Core)** aus, und geben Sie `StringLibraryTests` in das Textfeld **Name** ein. Siehe hierzu die folgende Abbildung:

   ![Das Dialogfeld **Neues Projekt hinzufügen** für das Komponententestprojekt](./media/lut-start/add-unit-test-cs.png)

1. Klicken Sie auf **OK**, um das Projekt zu erstellen.

   > [!NOTE]
   > In dieser Einführung wird das Live Unit Testing mit dem MSTest-Testframework verwendet. Sie können auch die xUnit- und NUnit-Testframeworks verwenden. 

1. Das Komponententestprojekt kann nicht automatisch auf die Klassenbibliothek zugreifen, die getestet wird. Sie erteilen der Testbibliothek Zugriff, indem Sie eine Referenz auf das Klassenbibliotheksprojekt hinzufügen. Klicken Sie hierzu mit der rechten Maustaste auf das Projekt `StringLibraryTests`, und wählen Sie **Hinzufügen** > **Referenz** aus. Stellen Sie sicher, dass im Dialogfeld **Verweis-Manager** die Registerkarte **Projektmappe** ausgewählt ist, und wählen Sie das Projekt `StringLibrary` aus. Siehe hierzu die folgende Abbildung. 

   ![Das Dialogfeld **Verweis-Manager**](./media/lut-start/add-reference.png)
 
1. Ersetzen Sie den in der Vorlage angegebenen Codebaustein für den Komponententest durch den folgenden Code:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

1. Speichern Sie Ihr Projekt, indem Sie auf das Symbol **Speichern** in der Symbolleiste klicken. 

1. Da der Komponententestcode einige ASCII-fremde Zeichen enthält, zeigt Visual Studio das folgende Dialogfeld mit der Warnung an, dass einige Zeichen verloren gehen, wenn die Datei im ASCII-Standardformat gespeichert wird. Klicken Sie auf die Schaltfläche **Mit anderer Codierung speichern**. 
 
   ![Wählen Sie eine Dateicodierung aus](media/lut-start/ascii-encoding.png) 

1. Wählen Sie in der Dropdownliste **Codierung** des Dialogfelds **Erweiterte Speicheroptionen** den Eintrag **Unicode (UTF-8 ohne Signatur) – Codepage 65001** aus, wie in der folgenden Abbildung dargestellt:

   ![Auswählen der UTF-8-Codierung](media/lut-start/utf8-encoding.png) 

1. Kompilieren Sie das Komponententestprojekt im Hauptebenenmenü von Visual Studio über **Erstellen** > **Projektmappe neu erstellen**.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe `UtilityLibraries`, und wählen Sie **Hinzufügen** > **Neues Projekt** aus.

1. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** den Visual Basic-Knoten und anschließend **.NET Core** aus. 

   > [!NOTE]
   > Sie müssen die Komponententests nicht in derselben Sprache wie die Klassenbibliothek schreiben.

1. Wählen Sie im rechten Bereich die Vorlage **Komponententestprojekt (.NET Core)** aus, und geben Sie `StringLibraryTests` in das Textfeld **Name** ein. Siehe hierzu die folgende Abbildung:

   ![Das Dialogfeld **Neues Projekt hinzufügen** für den Komponententest](./media/lut-start/add-unit-test-vb.png)

1. Klicken Sie auf **OK**, um das Projekt zu erstellen.

   > [!NOTE]
   > In dieser Einführung wird das Live Unit Testing mit dem MSTest-Testframework verwendet. Sie können auch die xUnit- und NUnit-Testframeworks verwenden. 

1. Das Komponententestprojekt kann nicht automatisch auf die Klassenbibliothek zugreifen, die getestet wird. Sie erteilen der Testbibliothek Zugriff, indem Sie eine Referenz auf das Klassenbibliotheksprojekt hinzufügen. Klicken Sie hierzu mit der rechten Maustaste auf das Projekt `StringLibraryTests`, und wählen Sie **Hinzufügen** > **Referenz** aus. Stellen Sie sicher, dass im Dialogfeld **Verweis-Manager** die Registerkarte **Projektmappe** ausgewählt ist, und wählen Sie das Projekt `StringLibrary` aus. Siehe hierzu die folgende Abbildung. 

   ![Das Dialogfeld **Verweis-Manager**](./media/lut-start/add-reference.png)
 
1. Ersetzen Sie den in der Vorlage angegebenen Codebaustein für den Komponententest durch den folgenden Code:

   [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest1.vb)]

1. Speichern Sie Ihr Projekt, indem Sie auf das Symbol **Speichern** in der Symbolleiste klicken. 

1. Da der Komponententestcode einige ASCII-fremde Zeichen enthält, zeigt Visual Studio das folgende Dialogfeld mit der Warnung an, dass einige Zeichen verloren gehen, wenn die Datei im ASCII-Standardformat gespeichert wird. Klicken Sie auf die Schaltfläche **Mit anderer Codierung speichern**. 
 
   ![Wählen Sie eine Dateicodierung aus](media/lut-start/ascii-encoding.png) 

1. Wählen Sie in der Dropdownliste **Codierung** des Dialogfelds **Erweiterte Speicheroptionen** den Eintrag **Unicode (UTF-8 ohne Signatur) – Codepage 65001** aus, wie in der folgenden Abbildung dargestellt:

   ![Auswählen der UTF-8-Codierung](media/lut-start/utf8-encoding.png)

1. Kompilieren Sie das Komponententestprojekt im Hauptebenenmenü von Visual Studio über **Erstellen** > **Projektmappe neu erstellen**.

---

Sie haben eine Klassenbibliothek und einige Komponententests dafür erstellt. Sie haben nun die Vorbereitungen abgeschlossen, die für die Verwendung von Live Unit Testing erforderlich sind.

## <a name="enable-live-unit-testing"></a>Aktivieren von Live Unit Testing

Bisher haben Sie die Tests für die `StringLibrary`-Klassenbibliothek zwar geschrieben, jedoch nicht ausgeführt. Live Unit Testing macht dies automatisch, nachdem es aktiviert wurde. Führen Sie hierzu die folgenden Schritte aus:

1. Wählen Sie das Codefenster mit dem Code für `StringLibrary` aus (optional). Dies ist entweder „class1.cs“ für ein C#-Projekt oder „class1.vb“ für ein Visual Basic-Projekt. (In diesem Schritt können Sie nach der Aktivierung von Live Unit Testing das Ergebnis Ihrer Tests und die Reichweite Ihrer Code Coverage prüfen.)

1. Wählen Sie im Hauptebenenmenü von Visual Studio **Test** > **Live Unit Testing** > **Starten** aus.
 
1. Visual Studio startet Live Unit Testing, das automatisch alle Ihre Tests ausführt. 
 
Nach Abschluss der Testausführung zeigt der **Test-Explorer** die Gesamtergebnisse und das Ergebnis der einzelnen Tests an. Darüber hinaus werden die Code Coverage der Tests und das Ergebnis Ihrer Tests im Codefenster grafisch dargestellt. Wie in der folgenden Abbildung zu sehen ist, wurden alle drei Tests erfolgreich ausgeführt. Zudem ist zu sehen, dass die Tests alle Codepfade in der Methode `StartsWithUpper` abgedeckt haben, und dass diese Tests alle erfolgreich ausgeführt wurden (durch das grüne Häkchen „✓“ gekennzeichnet). Schließlich ist zu sehen, dass keine der anderen Methoden in `StringLibrary` über eine Code Coverage verfügt (dies wird durch eine blaue Linie „➖“ gekennzeichnet). 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Das Fenster „Test-Explorer“ und das Codefenster nach dem Starten von Live Unit Testing](media/lut-start/lut-results-cs.png) 

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
![Das Fenster „Test-Explorer“ und das Codefenster nach dem Starten von Live Unit Testing](media/lut-start/lut-results-vb.png) 

---  

Ausführlichere Informationen zu Testabdeckung und Testergebnissen erhalten Sie, indem Sie im Codefenster ein bestimmtes Code Coverage-Symbol auswählen. Gehen Sie wie folgt vor, um diese Details zu prüfen:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Klicken Sie in der Zeile, in der `if (String.IsNullOrWhiteSpace(s))` bei der Methode `StartsWithUpper` steht, auf das grüne Häkchen. Wie in der folgenden Abbildung zu sehen ist, gibt Live Unit Testing an, dass drei Tests diese Codezeile abdecken und dass alle Tests erfolgreich ausgeführt wurden.

   ![Code Coverage für die Bedingungsanweisung „if“](media/lut-start/code-coverage-cs1.png) 

1. Klicken Sie in der Zeile, in der `return Char.IsUpper(s[0])` bei der Methode `StartsWithUpper` steht, auf das grüne Häkchen. Wie in der folgenden Abbildung zu sehen ist, gibt Live Unit Testing an, dass nur zwei Tests diese Codezeile abdecken und dass alle Tests erfolgreich ausgeführt wurden.

   ![Code Coverage für die return-Anweisung](media/lut-start/code-coverage-cs2.png)

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Klicken Sie in der Zeile, in der `If (String.IsNullOrWhiteSpace(s)) Then` bei der Methode `StartsWithUpper` steht, auf das grüne Häkchen. Wie in der folgenden Abbildung zu sehen ist, gibt Live Unit Testing an, dass drei Tests diese Codezeile abdecken und dass alle Tests erfolgreich ausgeführt wurden.

   ![Code Coverage für die Bedingungsanweisung „if“](media/lut-start/code-coverage-vb1.png) 

1. Klicken Sie in der Zeile, in der `Return Char.IsUpper(s(0))` bei der Methode `StartsWithUpper` steht, auf das grüne Häkchen. Wie in der folgenden Abbildung zu sehen ist, gibt Live Unit Testing an, dass nur zwei Tests diese Codezeile abdecken und dass alle Tests erfolgreich ausgeführt wurden.

   ![Code Coverage für die return-Anweisung](media/lut-start/code-coverage-vb2.png)

---

Das größte, von Live Unit Testing ermittelte Problem ist die unvollständige Code Coverage. Dieses Problem wird im nächsten Abschnitt behandelt. 

## <a name="expand-test-coverage"></a>Erweitern der Testabdeckung

In diesem Abschnitt erweitern Sie die Komponententests um die Methode `StartsWithLower`. Während Sie dies tun, testet Live Unit Testing Ihren Code weiterhin dynamisch.

Gehen Sie wie folgt vor, um die Code Coverage um die Methode `StartsWithLower` zu erweitern:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Fügen Sie die folgenden Methoden `TestStartsWithLower` und `TestDoesNotStartWithLower` zur Testquellcodedatei Ihres Projekts hinzu:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Ändern Sie die Methode `DirectCallWithNullOrEmpty`, indem Sie den folgenden Code direkt nach dem Aufruf zur Methode [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) hinzufügen.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Wenn Sie Ihren Quellcode ändern, führt Live Unit Testing automatisch neue und geänderte Tests aus. Wie in der folgenden Abbildung des **Test-Explorers** zu sehen ist, wurden alle Tests, einschließlich der beiden von Ihnen hinzugefügten Tests und dem geänderten Test, erfolgreich ausgeführt.

   ![Der Test-Explorer nach der Erweiterung der Testabdeckung.](media/lut-start/test-dynamic.png) 

1. Wechseln Sie zu dem Fenster mit dem Quellcode für die Klasse `StringLibrary`. Live Unit Testing zeigt jetzt an, dass Ihre Code Coverage um die Methode `StartsWithLower` erweitert wurde.

    ![Code Coverage für die Methode StartsWithLower](media/lut-start/lut-extended-cs.png) 

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Fügen Sie die folgenden Methoden `TestStartsWithLower` und `TestDoesNotStartWithLower` zur Testquellcodedatei Ihres Projekts hinzu:

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#1)]

1. Ändern Sie die Methode `DirectCallWithNullOrEmpty`, indem Sie den folgenden Code direkt nach dem Aufruf zur Methode [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) hinzufügen.

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#2)]

1. Wenn Sie Ihren Quellcode ändern, führt Live Unit Testing automatisch neue und geänderte Tests aus. Wie in der folgenden Abbildung des **Test-Explorers** zu sehen ist, wurden alle Tests, einschließlich der beiden von Ihnen hinzugefügten Tests und dem geänderten Test, erfolgreich ausgeführt.

   ![Der Test-Explorer nach der Erweiterung der Testabdeckung.](media/lut-start/test-dynamic.png) 

1. Wechseln Sie zu dem Fenster mit dem Quellcode für die Klasse `StringLibrary`. Live Unit Testing zeigt jetzt an, dass Ihre Code Coverage um die Methode `StartsWithLower` erweitert wurde.

    ![Code Coverage für StartsWithLower](media/lut-start/lut-extended-vb.png)

---
 
In einigen Fällen sind erfolgreich ausgeführte Tests im **Test-Explorer** grau unterlegt. Dies deutet darauf hin, dass gerade ein Test ausgeführt wird oder dass der Test nicht erneut ausgeführt wurde, da keine Codeänderungen vorgenommen wurden, die seit seiner letzten Ausführung Auswirkungen auf den Test haben würden.

Bisher wurden alle Tests erfolgreich abgeschlossen. Im nächsten Abschnitt untersuchen wir, wie Sie Testfehler behandeln können.

## <a name="handling-a-test-failure"></a>Behandeln eines Testfehlers

In diesem Abschnitt lernen Sie, wie Sie mithilfe von Live Unit Testing Testfehler ermitteln, behandeln und beheben können. Hierzu müssen Sie die Testabdeckung um die Methode `HasEmbeddedSpaces` erweitern.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Fügen Sie die folgende Methode zu Ihrer Testdatei hinzu:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Während der Ausführung des Tests gibt Live Unit Testing an, dass die `TestHasEmbeddedSpaces`-Methode fehlgeschlagen ist, wie in der folgenden Abbildung dargestellt wird: ![Der Test-Explorer meldet einen fehlgeschlagenen Test.](media/lut-start/test-failure.png) 
 
1. Wählen Sie das Fenster aus, in dem der Bibliothekscode angezeigt wird. Beachten Sie, dass Live Unit Testing die Code Coverage um die `HasEmbeddedSpaces`-Methode erweitert hat. Der Testfehler wird zudem durch Hinzufügen eines roten „🞩“ in Zeilen, die von fehlerhaften Tests abgedeckt werden, angegeben. 

1. Zeigen Sie auf die Zeile mit der `HasEmbeddedSpaces`-Methodensignatur. Live Unit Testing zeigt eine QuickInfo an, die angibt, dass die Methode von einem Test abgedeckt wird. Siehe hierzu die folgende Abbildung:

   ![Live Unit Testing-Informationen zu einem fehlgeschlagenen Test.](media/lut-start/test-failure-info-cs.png) 

1. Wählen Sie den fehlerhaften Test **TestHasEmbeddedSpaces** aus. Beachten Sie, dass Live Unit Testing Ihnen mehrere Optionen bietet, wie z.B. das Ausführen aller Test, das Ausführen der ausgewählten Tests, das Debuggen aller Tests und das Debuggen ausgewählter Tests. Siehe hierzu die folgende Abbildung:

   ![Live Unit Testing-Optionen für einen fehlgeschlagenen Test.](media/lut-start/test-failure-options.png) 
    
1. Wählen Sie **Ausgewählten Test debuggen** aus, um den fehlgeschlagenen Test zu debuggen. 
 
1. Visual Studio führt den Test im Debugmodus aus. In dem Test wird jede Zeichenfolge in einem Array einer Variable mit dem Namen `phrase` zugewiesen und an die `HasEmbeddedSpaces`-Methode übergeben. Die Ausführung des Programms wird angehalten, und wenn der Assert-Ausdruck erstmalig `false` lautet, wird der Debugger abgerufen. Das Ausnahme-Dialogfeld, das aus dem unerwarteten Wert im Aufruf der Methode [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) resultiert, wird in der folgenden Abbildung dargestellt.  

   ![Ausnahme-Dialogfeld in Live Unit Testing.](media/lut-start/exception-dialog-cs.png) 
 
   Darüber hinaus sind alle von Visual Studio bereitgestellten Debugtools verfügbar, um bei der Fehlerbehebung fehlgeschlagener Tests als Unterstützung zu dienen. Siehe hierzu die folgende Abbildung:
 
   ![Debugtools von Visual Studio.](media/lut-start/debugging-tools-cs.png) 

   Beachten Sie im Fenster **Auto**, dass der Wert der Variable `phrase` „Name\tDescription“ lautet und damit dem zweiten Element des Arrays entspricht. Von der Testmethode wird erwartet, dass die Methode `HasEmbeddedSpaces` bei der Übergabe dieser Zeichenfolge den Wert `true` zurückgibt; stattdessen wird der Wert `false` zurückgegeben. Offenbar erkennt die Methode das Tabstoppzeichen „\t“ nicht als eingebettetes Leerzeichen.

1. Wählen Sie **Debuggen** > **Fortfahren** aus, drücken Sie F5, oder klicken Sie in der Symbolleiste auf die Schaltfläche **Fortfahren**, um mit der Ausführung des Testprogramms fortzufahren. Der Test wird aufgrund eines Ausnahmefehlers beendet.

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Fügen Sie die folgende Methode zu Ihrer Testdatei hinzu:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/unittest2.vb#3)]

1. Während der Ausführung des Tests gibt Live Unit Testing an, dass die `TestHasEmbeddedSpaces`-Methode fehlgeschlagen ist, wie in der folgenden Abbildung dargestellt wird:
 
   ![Der Test-Explorer gibt einen fehlgeschlagenen Test an.](media/lut-start/test-failure.png) 
 
1. Wählen Sie das Fenster aus, in dem der Bibliothekscode angezeigt wird. Beachten Sie, dass Live Unit Testing die Code Coverage um die `HasEmbeddedSpaces`-Methode erweitert hat. Der Testfehler wird zudem durch Hinzufügen eines roten „🞩“ in Zeilen, die von fehlerhaften Tests abgedeckt werden, angegeben. 

1. Zeigen Sie auf die Zeile mit der `HasEmbeddedSpaces`-Methodensignatur. Live Unit Testing zeigt eine QuickInfo an, die angibt, dass die Methode von einem Test abgedeckt wird. Siehe hierzu die folgende Abbildung:

   ![Live Unit Testing-Informationen zu einem fehlgeschlagenen Test.](media/lut-start/test-failure-info-vb.png) 

1. Wählen Sie den fehlerhaften Test **TestHasEmbeddedSpaces** aus. Beachten Sie, dass Live Unit Testing Ihnen mehrere Optionen bietet, wie z.B. das Ausführen aller Test, das Ausführen der ausgewählten Tests, das Debuggen aller Tests und das Debuggen ausgewählter Tests. Siehe hierzu die folgende Abbildung:

   ![Live Unit Testing-Optionen für einen fehlgeschlagenen Test.](media/lut-start/test-failure-options.png) 
    
1. Wählen Sie **Ausgewählten Test debuggen** aus, um den fehlgeschlagenen Test zu debuggen. 
 
1. Visual Studio führt den Test im Debugmodus aus. In dem Test wird jede Zeichenfolge in einem Array einer Variable mit dem Namen `phrase` zugewiesen und an die `HasEmbeddedSpaces`-Methode übergeben. Die Ausführung des Programms wird angehalten, und wenn der Assert-Ausdruck erstmalig `false` lautet, wird der Debugger abgerufen. Das Ausnahme-Dialogfeld, das aus dem unerwarteten Wert im Aufruf der Methode [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) resultiert, wird in der folgenden Abbildung dargestellt.  

   ![Ausnahme-Dialogfeld in Live Unit Testing.](media/lut-start/exception-dialog-vb.png) 
 
   Darüber hinaus sind alle von Visual Studio bereitgestellten Debugtools verfügbar, um bei der Fehlerbehebung fehlgeschlagener Tests als Unterstützung zu dienen. Siehe hierzu die folgende Abbildung:
 
   ![Debugtools von Visual Studio.](media/lut-start/debugging-tools-vb.png) 

   Beachten Sie im Fenster **Auto**, dass der Wert der Variable `phrase` „Name“ + vbTab + „Description“ lautet und damit dem zweiten Element des Arrays entspricht. Von der Testmethode wird erwartet, dass die Methode `HasEmbeddedSpaces` bei der Übergabe dieser Zeichenfolge den Wert `true` zurückgibt; stattdessen wird der Wert `false` zurückgegeben. Offenbar erkennt die Methode das Tabstoppzeichen nicht als eingebettetes Leerzeichen.

1. Wählen Sie **Debuggen** > **Fortfahren** aus, drücken Sie F5, oder klicken Sie in der Symbolleiste auf die Schaltfläche **Fortfahren**, um mit der Ausführung des Testprogramms fortzufahren. Der Test wird aufgrund eines Ausnahmefehlers beendet.

--- 

Die gelieferten Informationen sind für eine vorläufige Untersuchung des Fehlers ausreichend. Sämtliche eingebettete Leerzeichen werden entweder durch `TestHasEmbeddedSpaces`, die Testroutine, das Ausgehen von falschen Voraussetzungen oder `HasEmbeddedSpaces` nicht ordnungsgemäß erkannt. Starten Sie mit der `StringLibrary.HasEmbeddedSpaces`-Methode, um das Problem zu diagnostizieren und zu beheben:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Sehen Sie sich den Vergleich in der `HasEmbeddedSpaces`-Methode an. Darin wird angenommen, dass U+0020 für ein eingebettetes Leerzeichen steht. Der Unicode-Standard enthält jedoch mehrere andere Leerzeichen. Dies deutet darauf hin, dass der Bibliothekscode nicht ordnungsgemäß auf ein Leerzeichen getestet wurde.
 
1. Ersetzen Sie den Übereinstimmungsvergleich durch einen Aufruf der <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>-Methode:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing führt die fehlerhafte Testmethode erneut aus und aktualisiert automatisch die Ergebnisse im Codefenster und im **Test-Explorer**. Siehe hierzu die folgende Abbildung:

    ![Der erfolgreich ausgeführte Test der HasEmbeddedSpaces-Methode.](media/lut-start/test-success-cs.png) 

# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Sehen Sie sich den Vergleich in der `HasEmbeddedSpaces`-Methode an. Darin wird angenommen, dass U+0020 für ein eingebettetes Leerzeichen steht. Der Unicode-Standard enthält jedoch mehrere andere Leerzeichen. Dies deutet darauf hin, dass der Bibliothekscode nicht ordnungsgemäß auf ein Leerzeichen getestet wurde.
 
1. Ersetzen Sie den Übereinstimmungsvergleich durch einen Aufruf der <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>-Methode:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/class2.vb#1)]

1. Live Unit Testing führt die fehlerhafte Testmethode erneut aus und aktualisiert automatisch die Ergebnisse im Codefenster und im **Test-Explorer**. Siehe hierzu die folgende Abbildung:

    ![Der erfolgreich ausgeführte Test der HasEmbeddedSpaces-Methode.](media/lut-start/test-success-vb.png) 

---

## <a name="see-also"></a>Siehe auch
[Live Unit Testing in Visual Studio](live-unit-testing.md)   
[Live Unit Testing – FAQ (Häufig gestellte Fragen)](live-unit-testing-faq.md)   
