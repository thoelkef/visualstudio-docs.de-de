---
title: Erstellen eines benutzerdefinierten HTTP-Text-Editors für den Webleistungstest-Editor in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c3f5e60f8cde791f571c5a6663356ad7d2ca80f9
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750694"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>How to: Create a Custom HTTP Body Editor for the Web Performance Test Editor

Sie können einen benutzerdefinierten Inhalts-Editor erstellen, der es Ihnen ermöglicht, den Zeichenfolgentextinhalt oder den binären Textinhalt einer Webdienstanforderung zu bearbeiten (z.B. SOAP, REST, asmx, wcf, RIA und andere Webdienstanforderungstypen).

 Sie können diese Arten von Editoren implementieren:

-   **Zeichenfolgeninhalts-Editor:** Wird mit der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>-Schnittstelle implementiert.

-   **Binärer Inhalts-Editor:** Wird mit der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>-Schnittstelle implementiert.

Diese Schnittstellen sind im <xref:Microsoft.VisualStudio.TestTools.WebTesting>-Namespace enthalten.

## <a name="create-a-windows-control-library-project"></a>Erstellen eines Windows-Steuerelementbibliothek-Projekts

### <a name="create-a-user-control-by-using-a-windows-control-library-project"></a>Erstellen eines Benutzersteuerelements mithilfe eines Windows-Steuerelementbibliothek-Projekts

1.  Klicken Sie in Visual Studio im Menü **Datei** auf **Neu** und dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2.  Wählen Sie unter **Installierte Vorlagen** je nach Programmieranforderungen entweder **Visual Basic** oder **Visual C#** aus, und wählen Sie dann **Windows** aus.

    > [!NOTE]
    > In diesem Beispiel wird Visual C# verwendet.

3.  Wählen Sie in der Liste der Vorlagen den Eintrag **Windows Forms-Steuerelementbibliothek** aus.

4.  Geben Sie im Textfeld „Name“ einen Namen ein (z.B. `MessageEditors`), und klicken Sie auf **OK**.

    > [!NOTE]
    > In diesem Beispiel wird "MessageEditors" verwendet.

     Das Projekt wird der neuen Projektmappe hinzugefügt, und im Designer wird ein <xref:System.Windows.Forms.UserControl>-Objekt mit dem Namen "UserControl1.cs" präsentiert.

5.  Ziehen Sie von der **Toolbox** unter der Kategorie **Allgemeine Steuerelemente** ein <xref:System.Windows.Forms.RichTextBox>-Element auf die Oberfläche von „UserControl1“.

6.  Wählen Sie das Aktionstagsymbol (![Smarttag-Glyphe](../test/media/vs_winformsmttagglyph.gif)) in der oberen rechten Ecke des <xref:System.Windows.Forms.RichTextBox>-Steuerelements aus, und klicken Sie dann auf **In übergeordnetem Container andocken**.

7.  Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Windows Forms-Bibliotheksprojekt und dann auf **Eigenschaften**.

8.  Wählen Sie unter „Eigenschaften“ die Registerkarte **Anwendung** aus.

9. Wählen Sie in der Dropdownliste **Zielframework** den Eintrag **.NET Framework 4** aus.

10. Das Dialogfeld "Änderung des Zielframeworks" wird angezeigt.

11. Klicken Sie auf **Ja**.

12. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **Verweise** und dann auf **Verweis hinzufügen**.

13. Das Dialogfeld **Verweis hinzufügen** wird angezeigt.

14. Klicken Sie auf die Registerkarte **.NET**, scrollen Sie nach unten, und wählen Sie **Microsoft.VisualStudio.QualityTools.WebTestFramework** aus. Klicken Sie dann auf **OK**.

15. Wenn der Ansicht-Designer nicht mehr geöffnet ist, klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **UserControl1.cs** und dann auf **Ansicht-Designer**.

16. Klicken Sie auf der Designoberfläche mit der rechten Maustaste, und wählen Sie **Code anzeigen** aus.

17. (Optional) Ändern Sie den Namen der Klasse und des Konstruktors von "UserControl1" in einen aussagekräftigen Namen, z. B. "MessageEditorControl":

    > [!NOTE]
    > Im Beispiel wird "MessageEditorControl" verwendet.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

18. Fügen Sie die folgenden Eigenschaften hinzu, um das Abrufen und Festlegen des Texts in "RichTextBox1" zu aktivieren. Die <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>-Schnittstelle verwendet EditString, und <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> verwendet EditByteArray:

   ```csharp
   public String EditString
   {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
   }

   public byte[] EditByteArray
   {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
   }
   ```

## <a name="add-a-class-for-to-the-windows-control-library-project"></a>Hinzufügen einer Klasse zum Windows-Steuerelementbibliothek-Projekt

Fügen Sie dem Projekt eine Klasse hinzu. Diese wird verwendet, um die <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>-Schnittstelle und die <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>-Schnittstelle zu implementieren.

**Übersicht über den Code in dieser Prozedur**

Das <xref:System.Windows.Forms.UserControl> "MessageEditorControl", das in der vorherigen Prozedur erstellt wurde, wird als "messageEditorControl" instanziiert:

```csharp
private MessageEditorControl messageEditorControl
```

 Die messageEditorControl-Instanz wird innerhalb des Plug-In-Dialogfelds gehostet, das von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*>-Methode erstellt wird. Darüber hinaus wird das <xref:System.Windows.Forms.RichTextBox> von "messageEditorControl" mit dem Inhalt von <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> aufgefüllt. Das Plug-In kann jedoch nur erstellt werden, wenn <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> `true` zurückgibt. Bei diesem Editor gibt <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> `true` zurück, wenn der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> im <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> "xml" enthält.

 Wenn die Bearbeitung des Zeichenfolgentexts abgeschlossen ist und der Benutzer im Plug-In-Dialogfeld auf **OK** klickt, wird <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> aufgerufen, um den bearbeiteten Text als Zeichenfolge abzurufen und den **Zeichenfolgentext** in der Anforderung im Webleistungstest-Editor zu aktualisieren.

### <a name="to-create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface-code"></a>So erstellen Sie eine Klasse und implementieren Sie den IStringHttpBodyEditorPlugin-Schnittstellencode

1.  Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf das Windows Forms-Steuerelementbibliothek-Projekt, und wählen Sie dann **Neues Element hinzufügen** aus.

2.  Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

3.  Wählen Sie **Klasse** aus.

4.  Geben Sie im Textfeld **Name** einen aussagekräftigen Namen für die Klasse ein (z.B. `MessageEditorPlugins`).

5.  Wählen Sie **Hinzufügen** aus.

     "Class1" wird dem Projekt hinzugefügt und im Code-Editor präsentiert.

6.  Fügen Sie im Code-Editor folgende using-Anweisung hinzu:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

7.  Schreiben oder kopieren Sie den folgenden Code, um die XmlMessageEditor-Klasse von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>-Schnittstelle zu instanziieren und die erforderlichen Methoden zu implementieren:

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Hinzufügen eines IBinaryHttpBodyEditorPlugin zur Klasse

Implementieren Sie die <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>-Schnittstelle.

**Übersicht über den Code in dieser Prozedur**

Die Codeimplementierung für die <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>-Schnittstelle ähnelt der für <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> (siehe vorherige Prozedur). Die binäre Version behandelt die Binärdaten jedoch nicht mit einer Zeichenfolge, sondern mithilfe eines Bytearrays.

Das in der ersten Prozedur erstellte <xref:System.Windows.Forms.UserControl> "MessageEditorControl" wird als "messageEditorControl" instanziiert:

```csharp
private MessageEditorControl messageEditorControl
```

Die messageEditorControl-Instanz wird innerhalb des Plug-In-Dialogfelds gehostet, das von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*>-Methode erstellt wird. Darüber hinaus wird das <xref:System.Windows.Forms.RichTextBox> von "messageEditorControl" mit dem Inhalt von <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> aufgefüllt. Das Plug-In kann jedoch nur erstellt werden, wenn <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> `true` zurückgibt. Bei diesem Editor gibt <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*>`true` zurück, wenn der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> im <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> "msbin1" enthält.

Wenn die Bearbeitung des Zeichenfolgentexts abgeschlossen ist und der Benutzer im Plug-In-Dialogfeld auf **OK** klickt, wird <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> aufgerufen, um den bearbeiteten Text als Zeichenfolge abzurufen und **BinaryHttpBody.Data** in der Anforderung im Webleistungstest-Editor zu aktualisieren.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>So fügen Sie ein IBinaryHttpBodyEditorPlugin zur Klasse hinzu

-   Schreiben oder kopieren Sie den folgenden Code unter der XmlMessageEditor-Klasse, die in der vorherigen Prozedur hinzugefügt wurde, um die Msbin1MessageEditor-Klasse von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>-Schnittstelle zu instanziieren und die erforderlichen Methoden zu implementieren:

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes.  This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Erstellen und Bereitstellen der Plug-Ins

### <a name="to-build-and-deploy-the-resulting-dll-for-the-istringhttpbodyeditorplugin-and-ibinaryhttpbodyeditorplugin"></a>So erstellen Sie das IStringHttpBodyEditorPlugin und IBinaryHttpBodyEditorPlugin und stellen Sie die resultierende DLL bereit

1.  Klicken Sie im Menü „Erstellen“ auf **\<Name des Windows Form-Steuerelementbibliothek-Projekts> erstellen**.

2.  Schließen Sie alle Instanzen von Visual Studio.

    > [!NOTE]
    > Dadurch wird sichergestellt, dass die *DLL-Datei* nicht gesperrt ist, bevor Sie versuchen, diese zu kopieren.

3.  Kopieren Sie die resultierende *DLL-Datei* (z.B. *MessageEditors.dll*) aus dem Ordner *bin\debug* des Projekts nach %ProgramFiles%\Microsoft Visual Studio\2017\\<edition>\Common7\IDE\PrivateAssemblies\WebTestPlugins.

4.  Öffnen Sie Visual Studio.

     Die *DLL-Datei* wird nun in Visual Studio registriert.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Überprüfen der Plug-Ins mithilfe eines Webleistungstests

### <a name="to-test-your-plug-ins"></a>So testen Sie die Plug-Ins

1.  Erstellen Sie ein Testprojekt.

2.  Erstellen Sie einen Webleistungstest, und geben Sie im Browser eine URL zu einem Webdienst ein, z.B. http://dev.virtualearth.net/webservices/v1/metadata/searchservice/dev.virtualearth.net.webservices.v1.search.wsdl.

3.  Wenn Sie die Aufzeichnung beenden, erweitern Sie im Webleistungstest-Editor die Anforderung für den Webdienst, und wählen Sie die Option **Zeichenfolgentext** oder **Binärer Text** aus.

4.  Wählen Sie im Fenster "Eigenschaften" die Option "Zeichenfolgentext" oder "Binärer Text" aus, und wählen Sie die Auslassungspunkte (…).

     Das Dialogfeld **HTTP-Textdaten bearbeiten** wird angezeigt.

5.  Sie können die Daten jetzt bearbeiten und "OK" wählen. Hierdurch wird die anwendbare GetNewValue-Methode aufgerufen, die den Inhalt im <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> aktualisiert.

## <a name="compile-the-code"></a>Kompilieren des Codes

Überprüfen Sie, ob das Zielframework für das Windows-Steuerelementbibliothek-Projekt „.NET Framework 4.5“ ist. Standardmäßig verwenden Windows-Steuerelementbibliothek-Projekte das .NET Framework 4.5-Clientframework als Ziel, sodass der Verweis „Microsoft.VisualStudio.QualityTools.WebTestFramework“ nicht eingeschlossen werden kann.

Weitere Informationen finden Sie unter [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Gewusst wie: Erstellen eines Anforderungsebenen-Plug-Ins](../test/how-to-create-a-request-level-plug-in.md)
- [Kodieren einer benutzerdefinierten Extraktionsregel für einen Webleistungstest](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodieren einer benutzerdefinierten Validierungsregel für einen Webleistungstest](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Gewusst wie: Erstellen eines Auslastungstest-Plug-Ins](../test/how-to-create-a-load-test-plug-in.md)
- [Generieren und Ausführen eines codierten Webleistungstests](../test/generate-and-run-a-coded-web-performance-test.md)
- [Gewusst wie: Erstellen eines Visual Studio Add-Ins für die Webleistungstest-Ergebnisansicht](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)