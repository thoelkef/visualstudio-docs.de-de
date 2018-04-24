---
title: Erstellen eines benutzerdefinierten Daten-Editors für einen Adapter für diagnostische Daten in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, creating custom editor
ms.assetid: 24970227-d1ea-4f6d-9839-e911478848ba
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 58c0a4e764edd27e2059175e170a9e542c285a89
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter"></a>Gewusst wie: Erstellen eines benutzerdefinierten Editors für Daten im Adapter für diagnostische Daten

Beim Erstellen eines Adapters für diagnostische Daten können Sie es dem Endbenutzer ermöglichen, bestimmte Daten zu konfigurieren, wenn der benutzerdefinierte Adapter für diagnostische Daten für die Testeinstellungen ausgewählt wird. Sie können z. B. die Konfigurationsdaten auswählen, die die zu extrahierenden Registrierungsschlüssel angeben, und festlegen, welche Ebene der Netzwerklast simuliert werden soll oder in welchem Verzeichnis nach temporären Dateien oder Arbeitsdateien gesucht werden soll.

Sie müssen eine Konfigurationsdatei verwenden, um die Anfangswerte für den Adapter für diagnostische Daten einzurichten. Sie können einen benutzerdefinierten Editor bereitstellen, um dem Benutzer das Ändern der Konfigurationsdaten zu ermöglichen.

Um einen eigenen Editor zu erstellen, müssen Sie ein Benutzersteuerelement erstellen, das <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> implementiert.

Der Adapter für diagnostische Daten kann die Editorklasse zum Bearbeiten von Diagnosedaten-Konfigurationseinstellungen mithilfe eines <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>-Objekts angeben.

Darüber hinaus geben Sie die zu verwendenden Standardkonfigurationsdaten an.  Ein Beispiel für eine Standardkonfiguration finden Sie unter [Beispielprojekt für das Erstellen eines Adapters für diagnostische Daten](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

Führen Sie die folgenden Schritte aus, um einen benutzerdefinierten Editor für das Aktualisieren von Daten der Testeinstellungen zu erstellen, wenn ein benutzerdefinierter Adapter für diagnostische Daten verwendet wird.

> [!NOTE]
> Sie müssen zum Erstellen eines benutzerdefinierten Editors zunächst den Adapter für diagnostische Daten erstellen, in dem <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> für die Klasse übernommen wurde. Sie können die optionale <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute.HelpUri*>-Eigenschaft in diesem Attribut verwenden, um die Quelle der Hilfeinhalte für den Editor anzugeben. Weitere Informationen zum Erstellen eines Adapters für diagnostische Daten finden Sie unter [Vorgehensweise: Erstellen eines Adapters für diagnostische Daten](../test/how-to-create-a-diagnostic-data-adapter.md).

Ein vollständiges Beispielprojekt für Adapter für diagnostische Daten, einschließlich eines benutzerdefinierten Konfigurations-Editors, finden Sie unter [Beispielprojekt für das Erstellen eines Adapters für diagnostische Daten](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

## <a name="to-create-a-custom-editor-for-your-diagnostic-data-adapter"></a>So erstellen Sie einen benutzerdefinierten Editor für den Adapter für diagnostische Daten

1.  Erstellen Sie im Projekt ein Benutzersteuerelement für Ihren Adapter für diagnostische Daten:

    1.  Klicken Sie mit der rechten Maustaste auf das Codeprojekt, das die Klasse des Adapters für diagnostische Daten enthält, zeigen Sie auf **Hinzufügen** und dann auf **Benutzersteuerelement**.

    2.  Fügen Sie für dieses Beispiel eine Bezeichnung zum Formular mit dem folgenden Text hinzu: **Datendateiname:** und ein Textfeld mit dem Namen **FileTextBox**, in dem der Benutzer die notwendigen Daten eingeben kann.

    > [!NOTE]
    > Nur Windows Forms-Steuerelemente werden derzeit unterstützt.

2.  Fügen Sie dem Deklarationsabschnitt diese Zeilen hinzu:

    ```csharp
    using System.Xml;
    using Microsoft.VisualStudio.TestTools.Common;
    using Microsoft.VisualStudio.TestTools.Execution;
    ```

3.  Machen Sie dieses Benutzersteuerelement zu einem benutzerdefinierten Editor.

    1.  Klicken Sie mit der rechten Maustaste auf das Benutzersteuerelement in dem Codeprojekt, und zeigen Sie auf **Code anzeigen**.

    2.  Legen Sie fest, dass die Klasse die Editorschnittstelle <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> wie folgt implementiert:

    ```csharp
    public partial class MyDataConfigEditor :
         UserControl, IDataCollectorConfigurationEditor
    ```

    1.  Klicken Sie im Code mit der rechten Maustaste auf <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>, und wählen Sie den Befehl **Schnittstelle implementieren** aus. Die Methoden, die Sie für diese Schnittstelle implementieren müssen, werden der Klasse hinzugefügt.

    2.  Fügen Sie das <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>-Objekt dem Benutzersteuerelement für den Editor hinzu, damit es als Adapter für diagnostische Daten identifiziert werden kann, und ersetzen Sie **Unternehmen**, **Produkt** und **Version** durch die entsprechenden Informationen für den Adapter für diagnostische Daten:

        ```csharp
        [DataCollectorConfigurationEditorTypeUri(
            "configurationeditor://MyCompany/MyConfigEditor/1.0")]
        ```

4.  Fügen Sie folgendermaßen zwei private Variablen hinzu:

    ```csharp
    private DataCollectorSettings collectorSettings;
    private IServiceProvider ServiceProvider { get; set; }
    ```

5.  Fügen Sie Code hinzu, um den Editor für den Adapter für diagnostische Daten zu initialisieren. Sie können den Feldern im Benutzersteuerelement Standardwerte anhand der Daten in der Einstellungsvariable hinzufügen. Dies sind die Daten, die im `<DefaultConfiguration>`-Element in der XML-Konfigurationsdatei für den Adapter enthalten sind.

    ```csharp
    public void Initialize(
        IServiceProvider svcProvider,
        DataCollectorSettings settings)
    {
        ServiceProvider = svcProvider;
        collectorSettings = settings;

        // Display the default file name as listed in the settings file.
        this.SuspendLayout();
        this.FileTextBox.Text = getText(collectorSettings.Configuration);
        this.ResumeLayout();
    }
    ```

6.  Fügen Sie Code hinzu, um die Daten aus den Steuerelementen im Editor wieder im XML-Format zu speichern, das die Diagnosedatenadapter-API benötigt. Gehen Sie dazu wie folgt vor:

    ```csharp
    public DataCollectorSettings SaveData()
    {
        collectorSettings.Configuration.InnerXml =
            String.Format(
    @"<MyCollectorName
        xmlns=""http://MyCompany/schemas/MyDiagnosticDataCollector/1.0"">
      <File FullPath=""{0}"" />
    </MyCollectorName>",
        FileTextBox.Text);
        return collectorSettings;
    }
    ```

7.  Wenn es von Bedeutung ist, fügen Sie Code hinzu, mit dem überprüft wird, ob die Daten in der `VerifyData`-Methode korrekt sind. Sie können auch einfach festlegen, dass die Methode `true` zurückgeben muss.

    ```csharp
    public bool VerifyData()
    {
        // Not currently verifying data
        return true;
    }
    ```

8.  Sie können Code hinzufügen, um die Daten auf die Anfangseinstellungen zurückzusetzen, die in der XML-Konfigurationsdatei in der `ResetToAgentDefaults()`-Methode enthalten sind, für die das private `getText()`-Objekt verwendet wird (optional).

    ```csharp
    // Reset to default value from XML configuration
    // using a custom getText() method
    public void ResetToAgentDefaults()
    {
        this.FileTextBox.Text = getText(collectorSettings.DefaultConfiguration);
    }

    // Local method to read the configuration settings
    private string getText(XmlElement element)
    {
        // Setup namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                element.OwnerDocument.NameTable);

        // Find all the "File" elements under our configuration
        XmlNodeList files = element.SelectNodes("//ns:MyCollectorName/ns:File", nsmgr);

        string result = String.Empty;
        if (files.Count > 0)
        {
            XmlAttribute pathAttribute = files[0].Attributes["FullPath"];
            if (pathAttribute != null &&
                !String.IsNullOrEmpty(pathAttribute.Value))
            {
                result = pathAttribute.Value;
            }
        }

        return result;
    }
    ```

9. Erstellen Sie Ihre Lösung. Kopieren Sie die Assembly für den Adapter für diagnostische Daten und die XML-Konfigurationsdatei (`<diagnostic data adapter name>.dll.config`) an den folgenden Speicherort, auf der Basis Ihres Installationsverzeichnisses: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

    > [!NOTE]
    > Obwohl sich der Konfigurations-Editor in einem Projekt und einer Assembly befinden kann, die sich beide vom Adapter für diagnostische Daten unterscheiden, können sie sich auch in der gleichen Assembly befinden.

10. Um beim Testen den Adapter für diagnostische Daten zu verwenden, müssen Sie eine Auswahl in der Liste der vorhandenen Testeinstellungen treffen oder in Microsoft Test Manager oder Visual Studio neue Einstellungen erstellen und anschließend den Adapter für diagnostische Daten auswählen.

     Der Adapter wird auf der Registerkarte **Daten und Diagnose** der Testeinstellungen mit dem Anzeigenamen angezeigt, den Sie der Klasse zugewiesen haben.

11. Um den Adapter für diagnostische Daten für die Testeinstellungen zu konfigurieren, klicken Sie neben dem Adapternamen auf **Konfigurieren**.

     Der benutzerdefinierte Editor wird jetzt angezeigt.

12. Bearbeiten Sie die Felder im benutzerdefinierten Editor nach Bedarf, und klicken Sie dann auf **Speichern**.

13. Wenn Sie Tests in Microsoft Test Manager ausführen, können Sie diese Testeinstellungen dem Testplan zuweisen, bevor Sie die Tests ausführen, oder verwenden Sie den Befehl **Ausführen mit Optionen**, um Testeinstellungen zuzuweisen und zu überschreiben. Weitere Informationen zu Testeinstellungen finden Sie unter [Collect Diagnostic Information Using Test Settings (Erfassen von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md).

14. Bevor Sie den neuen Konfigurations-Editor mit einem Adapter für diagnostische Daten verwenden können, müssen Sie das <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>-Objekt für jede Adapterklasse für diagnostische Daten übernehmen, für die Sie den Editor verwenden möchten, und sie auf dem Clientcomputer neu kompilieren und installieren. Weitere Informationen zum Installieren von Adaptern für diagnostische Daten und Konfigurations-Editoren finden Sie unter [Vorgehensweise: Installieren eines benutzerdefinierten Adapters für diagnostische Daten](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

15. Führen Sie die Tests unter Verwendung der Testeinstellungen aus, wenn der Adapter für diagnostische Daten ausgewählt ist.

     Die von Ihnen im Editor angegebene Datendatei ist an die Testergebnisse angefügt.

 Weitere Informationen zum Konfigurieren der Testeinstellungen zum Verwenden einer Umgebung beim Ausführen von Tests finden Sie unter [Collect diagnostic data while testing (VSTS) (Sammeln von Diagnosedaten beim Testen (VSTS))](/vsts/manual-test/collect-diagnostic-data) oder unter [Collect diagnostic data in manual tests (VSTS) (Sammeln von Diagnosedaten in manuellen Tests (VSTS))](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- [Erstellen eines Adapters für diagnostische Daten zum Sammeln von benutzerdefinierten Daten oder Beeinflussen eines Testsystems](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Collect Diagnostic Information Using Test Settings (Sammeln von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md)
- [Beispielprojekt für das Erstellen eines Adapters für diagnostische Daten](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)