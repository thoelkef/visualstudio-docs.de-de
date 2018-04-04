---
title: Beispielprojekt für das Erstellen eines Adapters für diagnostische Daten in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- samples. Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter, sample
ms.assetid: 548bdc5e-338f-4be7-a555-e6a2efb1df6b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 0b37512405442b327bb4b9688a39bfc4c99ea594
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="sample-project-for-creating-a-diagnostic-data-adapter"></a>Beispielprojekt für das Erstellen eines Adapters für diagnostische Daten

"MyDiagnosticDataAdapter" ist ein einfacher Adapter für diagnostische Daten, der eine Protokolldatei an die Testergebnisse anfügen kann, wenn Sie die Tests ausführen.

 Sie benötigen Administratorberechtigungen für jeden Computer, auf dem der Diagnosedatensammler oder der Konfigurations-Editor installiert ist.

## <a name="example-data-adapter"></a>Adapter für Beispieldaten

Dieses Beispiel veranschaulicht das Ausführen der folgenden Aufgaben:

-   Anwenden von Attributen, um eine Klasse für Microsoft Test Manager als Adapter für diagnostische Daten auffindbar zu machen

-   Anwenden von Attributen, um eine Benutzersteuerelementklasse für Microsoft Test Manager als Editor auffindbar zu machen, der zum Ändern der Konfiguration für einen Adapter für diagnostische Daten verwendet werden soll.

-   Zugreifen auf standardmäßige Konfigurationsdaten

-   Registrieren bestimmter Ereignisse der Sammlung diagnostischer Daten

-   Anfügen der Protokolldatei durch Senden an das <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>.

```csharp
// My Data Collector Class
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using System;

namespace MyCompany.MyDiagnosticDataAdapters
{
    // Provide a URI and friendly name for your diagnostic data adapter
    [DataCollectorTypeUri("datacollector://MyCompany/MyDataCollector/1.0")]
    [DataCollectorFriendlyName("Collect Log Files sample", false)]
    // Designate your chosen configuration editor
    [DataCollectorConfigurationEditor(
        "configurationeditor://MyCompany/MyDataConfigEditor/1.0")]
    public class MyDataCollector : DataCollector
    {
        private DataCollectionEvents dataEvents;
        private DataCollectionLogger dataLogger;
        private DataCollectionSink dataSink;
        private XmlElement configurationSettings;

        // Required method called by the testing framework
        public override void Initialize(
            XmlElement configurationElement,
            DataCollectionEvents events,
            DataCollectionSink sink,
            DataCollectionLogger logger,
            DataCollectionEnvironmentContext environmentContext)
        {
            dataEvents = events; // The test events
            dataLogger = logger; // The error and warning log
            dataSink = sink;     // Saves collected data
            // Configuration from the test settings
            configurationSettings = configurationElement;

            // Register common events for the data collector
            // Not all of the events are used in this class
            dataEvents.SessionStart +=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd +=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart +=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd +=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
            dataEvents.DataRequest +=
                new EventHandler<DataRequestEventArgs>(OnDataRequest);
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                dataEvents.SessionStart -=
                    new EventHandler<SessionStartEventArgs>(OnSessionStart);
                dataEvents.SessionEnd -=
                    new EventHandler<SessionEndEventArgs>(OnSessionEnd);
                dataEvents.TestCaseStart -=
                    new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
                dataEvents.TestCaseEnd -=
                    new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
                dataEvents.DataRequest -=
                    new EventHandler<DataRequestEventArgs>(OnDataRequest);
            }
        }

        #region Event Handlers
        public void OnSessionStart(object sender, SessionStartEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnSessionEnd(object sender, SessionEndEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseStart(object sender, TestCaseEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseEnd(object sender, TestCaseEndEventArgs e)
        {
            // Get any files to be collected that are
            // configured in your test settings
            List<string> files = getFilesToCollect();

            // For each of the files, send the file to the data sink
            // which will attach it to the test results or to a bug
            foreach (string file in files)
            {
                dataSink.SendFileAsync(e.Context, file, false);
            }
        }

        public void OnDataRequest(object sender, DataRequestEventArgs e)
        {
            // TODO: Provide implementation
            // Most likely this occurs because a bug is being filed
        }
        #endregion

        // A private method to collect the configured file names
        private List<string> getFilesToCollect()
        {
            // Seetup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    configurationSettings.OwnerDocument.NameTable);
            nsmgr.AddNamespace("ns",
                "http://MyCompany/schemas/MyDataCollector/1.0");

            // Find all of the "File" elements under our configuration
            XmlNodeList files =
                configurationSettings.SelectNodes(
                    "//ns:MyDataCollector/ns:File");

            // Build the list of files to collect from the
            // "FullPath" attributes of the "File" nodes.
            List<string> result = new List<string>();
            foreach (XmlNode fileNode in files)
            {
                XmlAttribute pathAttribute =
                    fileNode.Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result.Add(pathAttribute.Value);
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-editor"></a>Beispiel-Konfigurations-Editor

Dies ist ein beispielhafter Konfigurations-Editor für den Adapter für diagnostische Daten. Fügen Sie dem Projekt ein Benutzersteuerelement hinzu, und erstellen Sie ein sehr einfaches Formular mit einer Bezeichnung ("Name der Protokolldatei:") und einem Textfeld mit dem Namen "FileTextBox".

```csharp
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.Xml;
using System;

namespace MyCompany.DiagnosticDataAdapters.ConfigurationEditors
{
    [DataCollectorConfigurationEditorTypeUri(
        "configurationeditor://MyCompany/MyConfigEditor/1.0")]
    public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
    {
        private DataCollectorSettings collectorSettings;

        // Create a private property for the service provider
        private IServiceProvider ServiceProvider { get; set; }

        // Constructor
        public MyConfigurationEditor()
        {
            InitializeComponent();
        }

        // Required method called by the testing framework
        public void Initialize(
            IServiceProvider svcProvider,
            DataCollectorSettings settings)
        {
            ServiceProvider = svcProvider;
            collectorSettings = settings;

            // Display the file name as listed in the settings file.
            // If the configuration has not been updated before, this
            // data will be provided by the default configuration
            // section from <nameofcollector>.dll.config:
            // <DefaultConfiguration>
            //   <MyCollectorName
            //       xmlns="http://MyCompany/schemas/ProductName/Version");
            //     <File FullPath="C:\temp\logfile1.txt" />
            //   </MyCollectorName>
            // </DefaultConfiguration>
            this.SuspendLayout();
            this.FileTextBox.Text = GetText(collectorSettings.Configuration);
            this.ResumeLayout();
        }

        // Can be used to verify data before saving it
        public bool VerifyData()
        {
            // Not currently verifying data
            return true;
        }

        // Reset to default value from XML configuration
        // using a custom method
        public void ResetToAgentDefaults()
        {
            this.FileTextBox.Text =
                getText(collectorSettings.DefaultConfiguration);
        }

        // Saves data changed in the editor to the test configuration
        // settings. Does not change the default value.
        public DataCollectorSettings SaveData()
        {
            collectorSettings.Configuration.InnerXml =
                String.Format(
                    @"<MyCollectorName
      xmlns=""http://MyCompany/schemas/MyDataCollector/1.0"">
  <File FullPath=""{0}"" />
</MyCollectorName>",
                    FileTextBox.Text);
            return collectorSettings;
        }

        // Reads the configuration settings
        private string getText(XmlElement element)
        {
            // Setup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    element.OwnerDocument.NameTable);

            // Find all the "File" elements under our configuration
            XmlNodeList files = element.SelectNodes("//ns:MyDataCollector/ns:File", nsmgr);

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
    }
}
```

## <a name="example-configuration-file"></a>Beispiel-Konfigurationsdatei

Im Folgenden sehen Sie eine Beispielkonfigurationsdatei für den Diagnosedatensammler-Konfigurations-Editor.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section
      name="DataCollectorConfiguration"
      type="Microsoft.VisualStudio.QualityTools.Execution.DataCollectorConfigurationSection,
        Microsoft.visualStudio.QualityTools.ExecutionCommon,
        Version=4.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f7f11d50a3a" />
  </configSections>
  <DataCollectorConfiguration
      xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/11">
    <DataCollector
        typeUri="datacollector://MyCompany/MyDataCollector/1.0">
      <DefaultConfiguration>
        <!-- Your default config settings-->
        <File FullPath="c:\temp\logfile1.txt" />
      </DefaultConfiguration>
    </DataCollector>
  </DataCollectorConfiguration>
</configuration>

```

## <a name="compiling-the-code"></a>Kompilieren des Codes

### <a name="to-create-the-code-project-for-this-diagnostic-adapter"></a>So erstellen Sie das Codeprojekt für diesen Diagnoseadapter

1.  Erstellen Sie ein neues Klassenbibliothekprojekt mit dem Namen "MyDataCollector".

2.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt und dann auf **Eigenschaften**. Um einen Ordner auszuwählen, der hinzugefügt werden soll, klicken Sie auf **Verweispfade** und dann auf die Auslassungspunkte (**…**).

     Das Dialogfeld **Verweispfad auswählen** wird angezeigt.

3.  Wählen Sie den folgenden Pfad aus, auf der Basis Ihres Installationsverzeichnisses: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*. Klicken Sie auf **OK**.

4.  Klicken Sie auf **Ordner hinzufügen**, um den Ordner zum Verweispfad hinzuzufügen.

     Der Ordner wird in der Liste der Verweispfade angezeigt.

5.  Klicken Sie auf **Alle speichern**, um die Verweispfade zu speichern.

6.  Fügen Sie die Assembly **Microsoft.VisualStudio.QualityTools.ExecutionCommon** hinzu.

    1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und klicken Sie dann auf **Verweis hinzufügen**.

    2.  Klicken Sie auf **Durchsuchen**, und suchen Sie **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

         Diese Assembly befindet sich unter *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Klicken Sie auf **OK**.

7.  Fügen Sie die Assembly **Microsoft.VisualStudio.QualityTools.Common** hinzu.

    1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf Verweise, und klicken Sie anschließend auf **Verweis hinzufügen**.

    2.  Klicken Sie auf **Durchsuchen**, und suchen Sie **Microsoft.VisualStudio.QualityTools.Common.dll**.

         Diese Assembly befindet sich unter *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Klicken Sie auf **OK**.

8.  Kopieren Sie die oben in diesem Dokument aufgeführte Klasse für den Adapter für diagnostische Daten in die Klasse für die Klassenbibliothek. Speichern Sie diese Klasse.

9. Um dem Projekt ein Benutzersteuerelement hinzuzufügen, klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf das Projekt „MyDataCollector“, zeigen Sie auf **Hinzufügen**, und wählen Sie dann **Benutzersteuerelement** aus. Wählen Sie **Hinzufügen** aus.

10. Fügen Sie dem Benutzersteuerelement mithilfe der Toolbox eine Bezeichnung hinzu, und ändern Sie die Text-Eigenschaft in **Dateiname:**.

11. Fügen Sie dem Benutzersteuerelement mithilfe der Toolbox ein Textfeld hinzu, und ändern Sie den Namen in **textBoxFileName**.

12. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Benutzersteuerelement, und wählen Sie dann **Code anzeigen** aus. Ersetzen Sie diese Benutzersteuerelementklasse durch die oben im Dokument aufgeführte Benutzersteuerelementklasse. Speichern Sie diese Klasse.

    > [!NOTE]
    > Standardmäßig bekommt das Benutzersteuerelement die Bezeichnung UserControl1. Stellen Sie sicher, dass im Benutzersteuerelement-Klassencode der Name des Benutzersteuerelements verwendet wird.

13. Um die XML-Konfigurationsdatei zu erstellen, klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf die Projektmappe, zeigen Sie auf **Hinzufügen**, und wählen Sie dann **Neues Element** aus. Klicken Sie, um **Anwendungskonfigurationsdatei** auszuwählen, und klicken Sie dann auf **Hinzufügen**. Dadurch wird der Projektmappe eine Datei namens **App.config** hinzugefügt.

14. Kopieren Sie die XML-Daten aus dem obigen Beispiel in die XML-Datei. Speichern Sie die Datei.

15. Erstellen Sie die Projektmappe, und kopieren Sie dann die Datei `App.config` in das Verzeichnis *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

16. Erstellen Sie Testeinstellungen, die diesen benutzerdefinierten Adapter für diagnostische Daten verwenden. Konfigurieren Sie die Testeinstellungen, um eine bereits vorhandene Datei zu erfassen.

     Wenn Sie Tests in Microsoft Test Manager ausführen, können Sie diese Testeinstellungen dem Testplan zuweisen, bevor Sie die Tests ausführen, oder verwenden Sie den Befehl „Ausführen mit Optionen“, um Testeinstellungen zuzuweisen und zu überschreiben. Weitere Informationen zu Testeinstellungen finden Sie unter [Collect Diagnostic Information Using Test Settings (Erfassen von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md).

17. Führen Sie die Tests unter Verwendung der Testeinstellungen aus, und wählen Sie dabei Ihren Adapter für diagnostische Daten aus.

     Die angegebene Datendatei wird bei Ausführung des Tests an die Testergebnisse angefügt.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Erstellen eines Adapters für diagnostische Daten](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Gewusst wie: Erstellen eines benutzerdefinierten Editors für Daten im Adapter für diagnostische Daten](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Gewusst wie: Installieren eines benutzerdefinierten Adapters für diagnostische Daten](../test/how-to-install-a-custom-diagnostic-data-adapter.md)
- [Erstellen eines Adapters für diagnostische Daten zum Sammeln von benutzerdefinierten Daten oder Beeinflussen eines Testsystems](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)