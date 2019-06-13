---
title: 'Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts'
ms.date: 06/10/2019
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6f58581a601da59e7ff66a3bae5ddcb7432bf8e3
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836105"
---
# <a name="walkthrough-create-a-code-snippet"></a>Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts

Ein Codeausschnitt kann in wenigen Schritten erstellt werden. Sie müssen nur eine XML-Datei erstellen, die entsprechenden Elemente eintragen und den Code hinzufügen. Sie können optional, Ersatzparameter verwenden und Projektverweise. Importieren Sie den Codeausschnitt zu Visual Studio-Installation mithilfe der **Import** Schaltfläche der **Codeausschnitt-Manager** (**Tools** > **Code Codeausschnitt-Manager**).

## <a name="snippet-template"></a>Ausschnittvorlage

Das folgende XML ist die einfache Ausschnittvorlage:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title></Title>
        </Header>
        <Snippet>
            <Code Language="">
                <![CDATA[]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="create-a-code-snippet"></a>Erstellen eines Codeausschnitts

1. Erstellen Sie eine neue XML-Datei in Visual Studio, und fügen Sie die oben gezeigten Vorlage hinzu.

2. Geben Sie den Titel des Ausschnitts in der **Titel** Element. Verwenden Sie den Titel **Quadratwurzel**.

3. Tragen Sie die Sprache des Ausschnitts in das **Sprachen**-Attribut des **Code**-Elements ein. Für C#, verwenden Sie **CSharp**, und verwenden Sie für Visual Basic **VB**.

   > [!TIP]
   > Um alle verfügbaren Werte anzuzeigen, navigieren die [Code-Element für den Abschnitt "Benutzerattribute"](code-snippets-schema-reference.md#attributes) auf die [Code Schemareferenz für Codeausschnitte](code-snippets-schema-reference.md) Seite.

4. Fügen Sie den Codeausschnitt-Code in die **CDATA** Abschnitt innerhalb der **Code** Element.

   Für C#:

   ```xml
   <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt(16);]]>
   </Code>
   ```

   Oder für Visual Basic:

   ```xml
   <Code Language="VB">
       <![CDATA[Dim root = Math.Sqrt(16)]]>
   </Code>
   ```

5. Speichern Sie den Ausschnitt als *SquareRoot.snippet* (Sie können ihn speichern überall).

## <a name="import-a-code-snippet"></a>Importieren eines Codeausschnitts

1. Sie können einen Ausschnitt in Visual Studio-Installation importieren, mit der **Codeausschnitt-Manager**. Öffnen Sie es durch Auswahl **Tools** > **Codeausschnitt-Manager**.

2. Klicken Sie auf die Schaltfläche **Importieren**.

3. Wechseln Sie zum Speicherort des Codeausschnitts aus der vorherigen Prozedur, klicken Sie zuerst darauf und anschließend auf **Öffnen**.

4. Das Dialogfeld **Codeausschnitt importieren** öffnet sich, und Sie werden aufgefordert, aus den Optionen im rechten Bereich auszuwählen, wo der Ausschnitt hinzugefügt werden soll. Die Option **Meine Codeausschnitte** sollte dabei zur Auswahl stehen. Wählen Sie diese Option aus, klicken Sie auf **Fertig stellen** und anschließend auf **OK**.

5. Der Codeausschnitt wird auf einen der folgenden Speicherorte, abhängig von der Codesprache kopiert:

   ::: moniker range="vs-2017"

   *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual C#\My Code Snippets*
    *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\Visual Basic\My Code Snippets*

   ::: moniker-end

6. Testen Sie den Ausschnitt, indem Sie öffnen ein C# oder Visual Basic-Projekt. Während eine Codedatei im Editor geöffnet, **Codeausschnitte** > **Ausschnitt einfügen** klicken Sie dann im Kontextmenü **Meine Codeausschnitte**. Daraufhin sollte einen Ausschnitt mit dem Namen **Quadratwurzel**. Doppelklicken Sie darauf.

   Der Code eines Ausschnitts wird in der Codedatei eingefügt.

## <a name="description-and-shortcut-fields"></a>Felder "Beschreibung" und "Kontextmenü

::: moniker range="vs-2017"

1. Beschreibungsfelder liefern Informationen über den Codeabschnitt, wenn sie im Codeausschnitt-Manager angezeigt werden. Die Verknüpfung ist ein Tag, das Benutzer zum Einfügen Ihres Codeausschnitts eingeben können. Bearbeiten Sie den Ausschnitt, der Sie hinzugefügt haben, indem Sie die Datei öffnen *%USERPROFILE%\Documents\Visual Studio 2017\Code Snippets\\[Visual C# oder Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Beschreibungsfelder liefern Informationen über den Codeabschnitt, wenn sie im Codeausschnitt-Manager angezeigt werden. Die Verknüpfung ist ein Tag, das Benutzer zum Einfügen Ihres Codeausschnitts eingeben können. Bearbeiten Sie den Ausschnitt, der Sie hinzugefügt haben, indem Sie die Datei öffnen *%USERPROFILE%\Documents\Visual Studio 2019\Code Snippets\\[Visual C# oder Visual Basic] \My Code Snippet\SquareRoot.snippet*.

::: moniker-end

   > [!TIP]
   > Da Sie die Datei im Verzeichnis bearbeiten, in dem Sie Visual Studio platziert, müssen Sie es in Visual Studio importieren.

2. Fügen Sie dem **Header**-Element **Autor**- und **Beschreibungs**-Elemente hinzu, und füllen Sie diese aus.

3. Das **Header**-Element sollte in etwa wie folgt aussehen:

   ```xml
   <Header>
       <Title>Square Root</Title>
       <Author>Myself</Author>
       <Description>Calculates the square root of 16.</Description>
   </Header>
   ```

4. Öffnen Sie den **Codeausschnitt-Manager**, und wählen Sie Ihren Codeausschnitt aus. Im rechten Bereich, beachten Sie, dass die **Beschreibung** und **Autor** jetzt aufgefüllt werden.

   ![Beschreibung für den Codeausschnitt im Codeausschnitt-Manager](media/code-snippet-description-author.png)

5. Um eine Verknüpfung zu hinzuzufügen, fügen einen **Verknüpfung** Element innerhalb der **Header** Element:

   ```xml
   <Header>
      <Title>Square Root</Title>
      <Author>Myself</Author>
      <Description>Calculates the square root of 16.</Description>
      <Shortcut>sqrt</Shortcut>
    </Header>
   ```

6. Speichern Sie die Ausschnittdatei erneut.

7. Um die Verknüpfung zu testen, öffnen Sie das Projekt, das Sie zuvor verwendet haben, geben Sie **"SQRT"** im Editor, und drücken Sie **Registerkarte** (einmal für Visual Basic wird zweimal für C#).

   Der Codeausschnitt wird eingefügt.

## <a name="replacement-parameters"></a>Ersatzparameter

Sie sollten die Teile eines Codeausschnitts, die vom Benutzer ersetzt werden. Beispielsweise empfiehlt den Benutzer einen Variablennamen durch einen in ihrem aktuellen Projekt ersetzen. Sie können zwei Typen von Ersetzungen bereitstellen: Literale und Objekte. Verwenden der [Literalelement](code-snippets-schema-reference.md#literal-element) Ersatz zu identifizieren, für die ein Codeabschnitt, der vollständig in den Ausschnitt jedoch wahrscheinlich enthalten ist angepasst werden, nachdem es in den Code (z. B. ein Zeichenfolgenausdruck oder ein numerischer Wert) eingefügt wurde. Verwenden der [Objektelement](code-snippets-schema-reference.md#object-element) ein Element zu identifizieren, die vom Codeausschnitt ist erforderlich, aber wahrscheinlich außerhalb des Codeausschnitts selbst (z. B. eine Objektinstanz oder eines Steuerelements) definiert werden.

1. Um den Benutzer auf einfache Weise ersetzen. die Zahl, um die Quadratwurzel berechnet zu aktivieren, Ändern der **Codeausschnitt** Element der *SquareRoot.snippet* -Datei wie folgt:

   ```xml
   <Snippet>
     <Code Language="CSharp">
       <![CDATA[double root = Math.Sqrt($Number$);]]>
     </Code>
     <Declarations>
       <Literal>
         <ID>Number</ID>
         <ToolTip>Choose the number you want the square root of.</ToolTip>
         <Default>16</Default>
       </Literal>
     </Declarations>
   </Snippet>
   ```

   Beachten Sie, dass die Literale Ersetzung eine ID angegeben ist (`Number`). ID aus dem Code-Ausschnitt verwiesen wird durch, umgibt ihn mit `$` Zeichen:

   ```xml
   <![CDATA[double root = Math.Sqrt($Number$);]]>
   ```

2. Speichern Sie die Snippet-Datei.

3. Öffnen Sie ein Projekt, und fügen Sie den Codeausschnitt.

   Der Codeausschnitt eingefügt wird, und das Literal bearbeitet wird für den Austausch hervorgehoben. Zeigen Sie auf den Ersatzparameter, um die QuickInfo für den Wert anzuzeigen.

   ![Ausschnitt ersetzen Parameter QuickInfo in Visual Studio Code](media/snippet-replacement-parameter-tooltip.png)

   > [!TIP]
   > Wenn mehr als einen replacable Parameter in einem Codeausschnitt vorhanden ist, können Sie drücken **Registerkarte** Navigieren von einem zum anderen die Werte ändern.

## <a name="import-a-namespace"></a>Importiert einen namespace

Können Sie einen Codeausschnitt zum Hinzufügen einer `using` Richtlinie (C#) oder `Imports` -Anweisung (Visual Basic) durch Einschließen der [Imports-Element](code-snippets-schema-reference.md#imports-element). Bei .NET Framework-Projekten können Sie auch einen Verweis auf das Projekt hinzufügen, mit der [References-Element](code-snippets-schema-reference.md#references-element).

Das folgende XML zeigt einen Codeausschnitt, der die Methode verwendet `File.Exists` im System.IO-Namespace und, folglich definiert die **Importe** Element, um dem System.IO-Namespace zu importieren.

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>File Exists</Title>
      <Shortcut>exists</Shortcut>
    </Header>
    <Snippet>
      <Code Language="CSharp">
        <![CDATA[var exists = File.Exists("C:\\Temp\\Notes.txt");]]>
      </Code>
      <Imports>
        <Import>
          <Namespace>System.IO</Namespace>
        </Import>
      </Imports>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Siehe auch

- [Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md)