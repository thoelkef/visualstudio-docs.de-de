---
title: 'Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, creating
- code snippets, shortcut
- code snippets, template
- code snippets, replacements
- code snippets, references
- code snippets, imports
ms.assetid: 0dcaae11-39cf-4463-9c90-2494321251c2
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac188bcf7975b8da1bbc71a90d3b6c34b095d424
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845580"
---
# <a name="walkthrough-creating-a-code-snippet"></a>Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Codeausschnitt kann in wenigen Schritten erstellt werden. Sie müssen nur eine XML-Datei erstellen, die entsprechenden Elemente eintragen und den Code hinzufügen. Dem Code können auch Verweise und Ersatzparameter hinzugefügt werden. Sie können den Codeausschnitt im Codeausschnitt-Manager über die Schaltfläche „Importieren“ (**Extras > Codeausschnitt-Manager**) zur Visual Studio-Installation hinzufügen.

> [!TIP]
> Informationen zur einfacheren Erstellung von Codeausschnitten, beispielsweise mithilfe des [Editors für Codeausschnitte](https://snippeteditor.codeplex.com/), finden Sie auf der CodePlex-Website für Communitytools.

## <a name="snippet-template"></a>Ausschnittvorlage
 Im Folgenden finden Sie eine einfache Ausschnittvorlage:

```
<?xml version="1.0" encoding="utf-8"?>
<CodeSnippets
    xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
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

### <a name="to-create-a-code-snippet"></a>So erstellen Sie einen Codeausschnitt

1. Erstellen Sie eine neue XML-Datei in Visual Studio, und fügen Sie die oben gezeigten Vorlage hinzu.

2. Tragen Sie den Titel des Ausschnitts, z. B. "Hello World VB", in das Titelelement ein.

3. Tragen Sie die Sprache des Ausschnitts in das Sprachenattribut des Codeelements ein. In diesem Beispiel wird "VB" verwendet.

4. Fügen Sie etwas Code im CDATA-Abschnitt innerhalb des Codeelements hinzu, zum Beispiel:

    ```
    <Code Language="VB">
        <![CDATA[Console.WriteLine("Hello, World!")]]>
    </Code>

    ```

5. Speichern Sie den Ausschnitt als "VBCodeSnippet.snippet".

### <a name="to-add-a-code-snippet-to-visual-studio"></a>So fügen Sie einen Codeausschnitt zu Visual Studio hinzu

1. Sie können der Visual Studio-Installation mithilfe des Codeausschnitt-Managers eigene Ausschnitte hinzufügen. Öffnen Sie den Codeausschnitt-Manager (**Extras > Codeausschnitt-Manager**).

2. Klicken Sie auf die Schaltfläche **Importieren**.

3. Wechseln Sie zum Speicherort des Codeausschnitts aus der vorherigen Prozedur, klicken Sie zuerst darauf und anschließend auf **Öffnen**.

4. Das Dialogfeld **Codeausschnitt importieren** öffnet sich, und Sie werden aufgefordert, aus den Optionen im rechten Bereich auszuwählen, wo der Ausschnitt hinzugefügt werden soll. Die Option **Meine Codeausschnitte** sollte dabei zur Auswahl stehen. Wählen Sie diese Option aus, klicken Sie auf **Fertig stellen** und anschließend auf **OK**.

5. Der Ausschnitt wird an den folgenden Speicherort kopiert:

     `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippets`

6. Testen Sie den Ausschnitt, indem Sie ein Visual Basic-Projekt und eine Codedatei öffnen. Klicken Sie in der Datei im Kontextmenü auf **Codeausschnitt einfügen** und dann auf **Meine Codeausschnitte**. Es sollte ein Ausschnitt mit dem Namen **My Visual Basic Code Snippet** („Mein Visual Basic-Codeausschnitt“) angezeigt werden. Doppelklicken Sie darauf.

7. Sie sollten `Console.WriteLine("Hello, World!")` sehen, das in den Code eingefügt wurde.

### <a name="adding-description-and-shortcut-fields"></a>Hinzufügen von Beschreibungs- und Verknüpfungsfeldern

1. Beschreibungsfelder liefern Informationen über den Codeabschnitt, wenn sie im Codeausschnitt-Manager angezeigt werden. Die Verknüpfung ist ein Tag, das Benutzer zum Einfügen Ihres Codeausschnitts eingeben können. Bearbeiten Sie den Ausschnitt, den Sie hinzugefügt haben, indem Sie die Datei öffnen `%USERPROFILE%\Documents\Visual Studio 2013\Code Snippets\Visual Basic\My Code Snippet\VBCodeSnippet.snippet` .

2. Fügen Sie dem Headerelement Autor- und Beschreibungselemente hinzu, und füllen Sie diese aus.

3. Das Headerelement würde in etwa wie folgt aussehen:

    ```
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
    </Header>

    ```

4. Öffnen Sie den Codeausschnitt-Manager, und wählen Sie den Codeausschnitt aus. Die Beschreibungs- und Autorenfelder im rechten Bereich sollten jetzt aufgefüllt sind.

5. Wenn Sie eine Verknüpfung hinzufügen möchten, fügen Sie ein Verknüpfungselement zusammen mit dem Autor- und Beschreibungselement hinzu:

    ```
    <Header>
        <Title>Hello World VB</Title>
        <Author>Myself</Author>
        <Description>Says Hello to the world.</Description>
        <Shortcut>hello</Shortcut>
    </Header>

    ```

6. Speichern Sie die Ausschnittdatei erneut.

7. Öffnen Sie zum Testen der Verknüpfung ein Visual Basic-Projekt und eine Codedatei. Geben Sie `hello` in die Datei ein, und drücken Sie Tab. Der Ausschnittcode sollte nun eingefügt sein.

### <a name="to-add-references-and-imports"></a>So fügen Sie Verweise und Importe hinzu

1. Mit Visual Basic-Ausschnitten können Sie mithilfe des Verweiselements einen Verweis auf ein Projekt und mithilfe des Import-Elements eine Import-Deklaration hinzufügen. (Code Ausschnitte in anderen Sprachen haben dieses Feature nicht.) Wenn Sie z. b `Console.WriteLine` . im Codebeispiel in ändern `MessageBox.Show` , müssen Sie möglicherweise dem Projekt die System.Windows.Forms.dll-Assembly hinzufügen.

2. Öffnen Sie den Ausschnitt.

3. Fügen Sie das Verweiselement unter dem Ausschnittelement hinzu:

    ```
    <References>
        <Reference>
            <Assembly>System.Windows.Forms.dll</Assembly>
        </Reference>
    </References>

    ```

4. Fügen Sie das Imports-Element unter dem Ausschnittelement hinzu:

    ```
    <Imports>
        <Import>
           <Namespace>System.Windows.Forms</Namespace>
        </Import>
    </Imports>

    ```

5. Ändern Sie den CDATA-Abschnitt wie folgt:

    ```
    <![CDATA[MessageBox.Show("Hello, World!")]]>
    ```

6. Speichern Sie den Ausschnitt.

7. Öffnen Sie ein Visual Basic-Projekt, und fügen Sie den Ausschnitt hinzu.

8. Oben in der Codedatei finden Sie eine Imports-Anweisung:

    ```
    Imports System.Windows.Forms

    ```

9. Sehen Sie sich die Eigenschaften des Projekts an. Die Registerkarte "Verweise" enthält einen Verweis auf System.Windows.Forms.dll.

### <a name="adding-replacements"></a>Hinzufügen von Ersetzungen

1. Möglicherweise möchten Sie, dass Teile der Codeausschnitte vom Benutzer ersetzt werden, zum Beispiel, wenn Sie eine Variable hinzufügen und der Benutzer diese durch eine Variable aus einem aktuellen Projekt ersetzen soll. Sie können zwei Typen von Ersetzungen bereitstellen: Literale und Objekte. Literale sind Zeichenfolgen eines bestimmten Typs (Zeichenfolgenliterale, Variablennamen oder Zeichenfolgendarstellungen numerischer Werte). Objekte sind Instanzen eines Typs, der keine Zeichenfolge ist. In dieser Prozedur deklarieren Sie eine literale Ersetzung und eine Objektersetzung, und Sie ändern den Code, um auf diese Ersetzungen zu verweisen.

2. Öffnen Sie den Ausschnitt.

3. In diesem Beispiel wird eine SQL-Verbindungszeichenfolge verwendet, daher müssen Sie die Import- und Verweiselemente ändern, um die entsprechenden Verweise hinzuzufügen:

    ```
    <References>
        <Reference>
            <Assembly>System.Data.dll</Assembly>
        </Reference>
        <Reference>
            <Assembly>System.Xml.dll</Assembly>
        </Reference>
    </References>
    <Imports>
        <Import>
            <Namespace>System.Data</Namespace>
        </Import>
        <Import>
            <Namespace>System.Data.SqlClient</Namespace>
        </Import>
    </Imports>

    ```

4. Um eine literale Ersetzung für die SQL-Verbindungszeichenfolge zu deklarieren, fügen Sie unter dem Ausschnittelement ein Deklarationselement hinzu. Fügen Sie darin ein literales Element mit Unterelementen für die ID, die QuickInfo und den Standardwert für die Ersetzung hinzu:

    ```
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
    </Declarations>

    ```

5. Um eine Objektersetzung für die SQL-Verbindung zu deklarieren, fügen Sie innerhalb des Deklarationselements ein Objektelement und Unterelemente für die ID, den Typ des Objekts, die QuickInfo und den Standardwert hinzu. Das resultierende Deklarationselement sollte wie folgt aussehen:

    ```
    <Declarations>
        <Literal>
            <ID>SqlConnString</ID>
            <ToolTip>Replace with a SQL connection string.</ToolTip>
            <Default>"SQL connection string"</Default>
        </Literal>
        <Object>
            <ID>SqlConnection</ID>
            <Type>System.Data.SqlClient.SqlConnection</Type>
            <ToolTip>Replace with a connection object in your application.</ToolTip>
            <Default>dcConnection</Default>
        </Object>
    </Declarations>
    ```

6. Verweisen Sie im Codeabschnitt mit umgebenden $-Zeichen auf die Ersetzungen, z.B. `$replacement$`:

    ```
    <Code Language="VB" Kind="method body">
        <![CDATA[Dim daCustomers As SqlDataAdapter
            Dim selectCommand As SqlCommand

            daCustomers = New SqlClient.SqlDataAdapter()
            selectCommand = new SqlClient.SqlCommand($SqlConnString$)
            daCustomers.SelectCommand = selectCommand
            daCustomers.SelectCommand.Connection = $SqlConnection$]]>
    </Code>
    ```

7. Speichern Sie den Ausschnitt.

8. Öffnen Sie ein Visual Basic-Projekt, und fügen Sie den Ausschnitt hinzu.

9. Der Code sollte wie folgt aussehen, wobei die Ersetzungen `SQL connection string` und `dcConnection` in hellem Orange hervorgehoben sind. Drücken Sie die TAB-TASTE, um von einem Ausschnitt zum anderen zu navigieren.

    ```
    Dim daCustomers As SqlDataAdapter
    Dim selectCommand As SqlCommand

    daCustomers = New SqlClient.SqlDataAdapter()
    selectCommand = New SqlClient.SqlCommand("SQL connection string")
    daCustomers.SelectCommand = selectCommand
    daCustomers.SelectCommand.Connection = dcConnection

    ```

## <a name="see-also"></a>Weitere Informationen
 [Schema Referenz für Code Ausschnitte](../ide/code-snippets-schema-reference.md)
