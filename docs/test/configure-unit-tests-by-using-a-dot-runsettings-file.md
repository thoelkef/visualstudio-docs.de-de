---
title: Konfigurieren von Komponententests mit einer RUNSETTINGS-Datei
ms.date: 10/03/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bd6d2f394edf1a1d2c96404a8af3714fbe9550d6
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880350"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Konfigurieren von Komponententests mithilfe einer *RUNSETTINGS*-Datei

Komponententests in Visual Studio können mithilfe einer *RUNSETTINGS*-Datei konfiguriert werden. Beispielsweise können Sie die .NET-Version, in der die Tests ausgeführt werden, das Verzeichnis für die Testergebnisse sowie die während eines Testlaufs erfassten Daten ändern.

Testlaufeinstellungsdateien sind optional. Wenn keine spezielle Konfiguration erforderlich sein soll, benötigen Sie keine *RUNSETTINGS*-Datei. *RUNSETTINGS*-Dateien werden häufig verwendet, um die [Code Coverage-Analyse](../test/customizing-code-coverage-analysis.md) anzupassen.

## <a name="specify-a-run-settings-file"></a>Angeben einer Testlaufeinstellungsdatei

Laufzeiteinstellungsdateien können verwendet werden, um Tests zu konfigurieren, die über die [Befehlszeile](vstest-console-options.md), in der IDE oder in einem [Buildworkflow ](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) mit Azure Test Plans oder Team Foundation Server (TFS) ausgeführt werden.

### <a name="ide"></a>IDE

::: moniker range="vs-2017"

Um eine Testlaufeinstellungsdatei in der IDE anzugeben, wählen Sie **Test** > **Testeinstellungen** > **Datei für Testeinstellungen auswählen** und anschließend die *.runsettings*-Datei aus.

![Menü „Datei für Testeinstellungen auswählen“ in Visual Studio 2017](media/select-test-settings-file.png)

Die Datei wird im Menü „Testeinstellungen“ angezeigt, und Sie können sie auswählen oder abwählen. Wenn die Testlaufeinstellungsdatei ausgewählt ist, wird sie bei jeder Auswahl von **Code Coverage analysieren** angewendet.

::: moniker-end

::: moniker range=">=vs-2019"

#### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019, Version 16.3 und früher

Wählen Sie **Test** > **Einstellungsdatei auswählen** aus, um eine Testlaufeinstellungsdatei anzugeben. Navigieren Sie zur *.runsettings*-Datei, und wählen Sie diese aus.

![Menü „Datei für Testeinstellungen auswählen“ in Visual Studio 2019](media/vs-2019/select-settings-file.png)

Die Datei wird im Menü „Test“ angezeigt, und Sie können sie auswählen oder abwählen. Wenn die Testlaufeinstellungsdatei ausgewählt ist, wird sie bei jeder Auswahl von **Code Coverage analysieren** angewendet.

#### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019, Version 16.4 und höher

Es gibt drei Möglichkeiten, in Visual Studio 2019, Version 16.4 und höher, eine Datei mit Laufzeiteinstellungen anzugeben:

- Fügen Sie entweder über die Projektdatei oder eine Directory.Build.props-Datei eine Buildeigenschaft zu einem Projekt hinzu. Die Datei mit Laufzeiteinstellungen für ein Projekt wird durch die Eigenschaft **RunSettingsFilePath** angegeben.

    - Laufzeiteinstellungen auf Projektebene werden zurzeit in C#-, VB-, C++- und F#-Projekten unterstützt.
    - Eine für ein Projekt angegebene Datei setzt alle anderen in der Projektmappe angegebenen Laufzeiteinstellungen außer Kraft.
    - Mithilfe [dieser MSBuild-Eigenschaften](https://docs.microsoft.com/visualstudio/msbuild/msbuild-reserved-and-well-known-properties?view=vs-2019) können Sie den Pfad zur RUNSETTINGS-Datei angeben. 

    Beispiel für die Angabe einer *RUNSETTINGS*-Datei für ein Projekt:
    
    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
      </PropertyGroup>
      ...
    </Project>
    ```

- Fügen Sie im Stammverzeichnis Ihrer Projektmappe eine Datei mit Laufzeiteinstellungen namens „RUNSETTINGS“ ein.

  Wenn die automatische Erkennung der Datei mit Laufzeiteinstellungen aktiviert ist, werden die Einstellungen in dieser Datei auf alle ausgeführten Tests angewendet. Die können die automatische Erkennung der RUNSETTINGS-Datei an zwei Stellen aktivieren:
  
    - **Tools** > **Optionen** > **Test** > **RUNSETTINGS-Dateien automatisch erkennen**

      ![Option zum automatischen Erkennen einer RUNSETTINGS-Datei in Visual Studio 2019](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
    - **Test** > **Laufzeiteinstellungen konfigurieren** > **RUNSETTINGS-Dateien automatisch erkennen**
    
      ![Menü für das automatisch Erkennen einer RUNSETTINGS-Datei in Visual Studio 2019](media/vs-2019/auto-detect-runsettings-menu.png)

- Wählen Sie in der IDE **Test** > **Laufzeiteinstellungen konfigurieren** > **Lösungsweite RUNSETTINGS-Datei auswählen** und anschließend die *RUNSETTINGS*-Datei aus.

   ![Menü „Lösungsweite RUNSETTINGS-Datei auswählen“ in Visual Studio 2019](media/vs-2019/select-solution-settings-file.png)
      
   - Diese Datei setzt die RUNSETTINGS-Datei im Stammverzeichnis der Projektmappe außer Kraft, sofern diese vorhanden ist, und wird auf alle ausgeführten Tests angewendet.  
   - Diese Dateiauswahl wird nur lokal beibehalten. 

::: moniker-end

### <a name="command-line"></a>Befehlszeile

Verwenden Sie zum Ausführen von Tests über die Befehlszeile *vstest.console.exe*, und geben Sie die Einstellungsdatei mithilfe des Parameters **/Settings** an.

1. Starten der Visual Studio Developer-Eingabeaufforderung:

   ::: moniker range="vs-2017"

   Wählen Sie im Windows **Startmenü** **Visual Studio 2017** > **Developer Command Prompt for VS 2017** (Eingabeaufforderung für Entwickler für VS 2017) aus.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   Wählen Sie im Windows **Startmenü** **Visual Studio 2019** > **Developer Command Prompt for VS 2019** (Eingabeaufforderung für Entwickler für VS 2019) aus.

   ::: moniker-end

2. Geben Sie einen Befehl wie diesen ein:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   oder

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Weitere Informationen finden Sie unter [Befehlszeilenoptionen von „VSTest.Console.exe“](vstest-console-options.md).

## <a name="customize-tests"></a>Anpassen von Tests

Gehen Sie wie folgt vor, um Ihre Tests mit einer *RUNSETTINGS*-Datei anzupassen:

1. Fügen Sie Ihrer Visual Studio-Projektmappe eine XML-Datei hinzu, und speichern Sie sie als *test.runsettings*.

   > [!TIP]
   > Der Dateiname spielt keine Rolle, sofern Sie die Erweiterung *.runsettings* verwenden.

2. Ersetzen Sie die Dateiinhalte durch das XML aus dem folgenden Beispiel ,und passen Sie es nach Bedarf an.

::: moniker range="vs-2017"

3. Klicken Sie im Menü **Test** auf **Testeinstellungen** > **Datei für Testeinstellungen auswählen**. Navigieren Sie zu der erstellten *RUNSETTINGS*-Datei, und wählen Sie **OK** aus.

::: moniker-end

::: moniker range=">=vs-2019"

3. Wählen Sie **Test** > **Einstellungsdatei auswählen** aus, um die Testlaufeinstellungsdatei auszuwählen. Navigieren Sie zu der erstellten *RUNSETTINGS*-Datei, und wählen Sie **OK** aus.

::: moniker-end

   > [!TIP]
   > Sie können mehrere *RUNSETTINGS*-Dateien in Ihrer Projektmappe erstellen und je nach Bedarf eine davon als aktive Testeinstellungsdatei auswählen.

## <a name="example-runsettings-file"></a>Beispiel für eine *RUNSETTINGS*-Datei

Der folgende XML-Code ist ein Beispiel für den Inhalt einer typischen *RUNSETTINGS*-Datei. Alle Elemente der Datei sind optional, da sie einen Standardwert enthalten.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the Test menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
          <!-- Set "sendRecordedMediaForPassedTestCase" to "false" to add video attachments to failed tests only -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true"  xmlns="">           
            <ScreenCaptureVideo bitRate="512" frameRate="2" quality="20" />
          </MediaRecorder>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="elements-of-a-runsettings-file"></a>Elemente einer *RUNSETTINGS*-Datei

In den folgenden Abschnitten werden die Elemente einer *RUNSETTINGS*-Datei beschrieben.

### <a name="run-configuration"></a>Laufzeitkonfiguration

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

Das **RunConfiguration**-Element kann folgende Elemente enthalten:

|Knoten|Standard|Werte|
|-|-|-|
|**ResultsDirectory**||Das Verzeichnis, in dem die Testergebnisse gespeichert werden.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` für .NET Core-Quellen, `FrameworkUap10` für UWP-basierte Quellen, `Framework45` für.NET Framework 4.5 und höher, `Framework40` für.NET Framework 4.0 und `Framework35` für.NET Framework 3.5.<br /><br />Durch diese Einstellung wird die Version des Komponententestframeworks angegeben, die zum Ermitteln und Ausführen der Tests verwendet wird. Diese kann sich von der Version der .NET-Plattform unterscheiden, die Sie in den Buildeigenschaften des Komponententestprojekts angeben.<br /><br />Wenn Sie das Element `TargetFrameworkVersion` in der Datei *.runsettings* weglassen, bestimmt die Plattform die Frameworkversion automatisch basierend auf den erstellten Binärdateien.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|False|false, true|
|**TestAdaptersPaths**||Ein oder mehrere Pfade zu dem Verzeichnis, in dem die Testadapter gespeichert sind.|
|**MaxCpuCount**|1|Durch diese Einstellung wird der Umfang der parallelen Ausführung gesteuert, wenn Komponententests ausgeführt werden, bei denen die auf dem Computer verfügbaren Kerne verwendet werden. Die Testausführungs-Engine startet für jeden verfügbaren Kern einen eigenständigen Prozess und übergibt an jeden Kern einen Container mit auszuführenden Tests. Ein Container kann eine Assembly, eine DLL oder ein relevantes Artefakt sein. Der Testcontainer ist die Planungseinheit. In jedem Container werden die Tests entsprechend dem Testframework ausgeführt. Gibt es viele Container, werden Prozesse, sobald das Ausführen ihrer Tests in einem Container abgeschlossen ist, an den nächsten verfügbaren Container übergeben.<br /><br />MaxCpuCount kann Folgendes sein:<br /><br />n, wobei 1 < = n < = Anzahl von Kernen: bis zu n Prozesse werden gestartet.<br /><br />n, wobei n = beliebiger anderer Wert: die Anzahl von gestarteten Prozessen kann maximal der Anzahl der verfügbaren Kerne entsprechen. Legen Sie beispielsweise n = 0 fest, damit die Plattform automatisch die optimale Anzahl der zu startenden Prozesse anhand der Umgebung ermittelt.|
|**TestSessionTimeout**||Ermöglicht Benutzern, eine Testsitzung zu beenden, wenn sie ein angegebenes Timeout überschreitet. Die Einstellung eines Timeouts stellt sicher, dass die Ressourcen gut ausgenutzt werden und Testsitzungen auf einen bestimmten Zeitraum beschränkt bleiben. Diese Einstellung ist in **Visual Studio 2017 Version 15.5** und höher verfügbar.|
|**DotnetHostPath**||Legen Sie einen benutzerdefinierten Pfad zum Dotnet-Host fest, der zum Ausführen des Testhosts verwendet wird. Dies ist hilfreich, wenn Sie Ihren eigenen Dotnet-Host erstellen, z. B. beim Erstellen des Repositorys „dotnet/runtime“. Wenn Sie diese Option festlegen, wird die Suche nach der Datei „testhost.exe“ übersprungen, und stattdessen wird die Datei „testhost.dll“ verwendet. 

### <a name="diagnostic-data-adapters-data-collectors"></a>Adapter für diagnostische Daten (Datensammler)

Das **DataCollectors**-Element gibt die Einstellungen von Adaptern für diagnostische Daten an. Adapter für diagnostische Daten sammeln zusätzliche Informationen zur Umgebung und der getesteten Anwendung. Jeder Adapter verfügt über Standardeinstellungen. Wenn Sie diese nicht verwenden möchten, können Sie andere Einstellungen festlegen.

#### <a name="code-coverage-adapter"></a>Codeabdeckungsadapter

```xml
<CodeCoverage>
    <ModulePaths>
        <Exclude>
            <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
    </ModulePaths>

    <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
    <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
    <CollectFromChildProcesses>True</CollectFromChildProcesses>
    <CollectAspDotNet>False</CollectAspDotNet>
</CodeCoverage>
```

Der Datensammler der Codeabdeckung erstellt ein Protokoll der Teile des Anwendungscodes, die im Test ausgeführt wurden. Weitere Informationen zum Anpassen der Einstellungen für die Code Coverage finden Sie unter [Anpassen der Code Coverage-Analyse](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Videodatensammler

Der Videodatensammler erfasst einen Bildschirm bei der Ausführung von Tests. Diese Aufzeichnung kann zur Problembehandlung von Benutzeroberflächentests verwendet werden. Der Videodatensammler ist in **Visual Studio 2017 Version 15.5** und höher verfügbar.

Um andere Typen von Adaptern für diagnostische Daten anzupassen, verwenden Sie eine [Testeinstellungsdatei](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Testlaufparameter bieten eine Möglichkeit zum Definieren von Variablen und Werten, die für die Tests zur Laufzeit verfügbar sind. Auf diese Parameter kann mithilfe der <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType>-Eigenschaft zugegriffen werden:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Fügen Sie Ihrer Testklasse ein privates <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext>-Feld und eine öffentliche <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext>-Eigenschaft hinzu, um Testlaufparameter zu verwenden.

### <a name="mstest-run-settings"></a>MSTest-Testlaufeinstellungen

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

Diese Einstellungen betreffen den Testadapter, der Testmethoden ausführt, die über das <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> -Attribut verfügen.

|Konfiguration|Standard|Werte|
|-|-|-|
|**ForcedLegacyMode**|False|In Visual Studio 2012 wurde der MSTest-Adapter für eine schnellere Geschwindigkeit und bessere Skalierbarkeit optimiert. Einige Verhalten, z. B. die Reihenfolge der Testausführung, sind möglicherweise nicht mehr so präzise wie in den vorherigen Versionen von Visual Studio. Legen Sie diesen Wert auf **TRUE** fest, um den älteren Testadapter zu verwenden.<br /><br />Beispielsweise können Sie diese Einstellung verwenden, wenn Sie eine *app.config*-Datei für einen Komponententest angegeben haben.<br /><br />Eventuell sollten Sie in Betracht ziehen, die Tests so umzugestalten, dass Sie den späteren Adapter verwenden können.|
|**IgnoreTestImpact**|False|Das Testauswirkungsfeature priorisiert Tests, auf die sich aktuelle Änderungen auswirken, wenn sie in MSTest oder über Microsoft Test Manager ausgeführt werden (ab Visual Studio 2017 veraltet). Diese Einstellung deaktiviert die Funktion. Weitere Informationen finden Sie unter [Welche Tests sollten ab einem vorherigen Build ausgeführt werden?](https://msdn.microsoft.com/library/dd286589)|
|**SettingsFile**||Sie können eine Testeinstellungsdatei, die mit dem MS-Testadapter verwendet werden soll, hier angeben. Sie können auch eine Testeinstellungsdatei [ im Menü „Einstellungen“](#ide) angeben.<br /><br />Wenn Sie diesen Wert angeben, müssen Sie außerdem **ForcedlegacyMode** auf **true**festlegen.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|False|Nachdem ein Testlauf abgeschlossen ist, wird MSTest beendet. Jeder Prozess, der als Teil des Tests gestartet wird, wird dann ebenfalls abgebrochen. Wenn der Test-Executor aktiv bleiben soll, legen Sie den Wert auf **TRUE** fest. Beispielsweise können Sie mit dieser Einstellung erreichen, dass der Browser zwischen Tests der programmierten UI aktiv bleibt.|
|**DeploymentEnabled**|true|Wenn Sie den Wert auf **FALSE** festlegen, werden in der Testmethode angegebene Bereitstellungselemente nicht in das Bereitstellungsverzeichnis kopiert.|
|**CaptureTraceOutput**|true|Mithilfe von <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType> können Sie über Ihre Testmethode in die Debugablaufverfolgung schreiben.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Legen Sie diesen Wert auf **FALSE** fest, um das Bereitstellungsverzeichnis nach einem Testlauf beizubehalten.|
|**MapInconclusiveToFailed**|False|Wenn ein Test mit einem nicht eindeutigen Status abgeschlossen wird, wird er im **Test-Explorer** dem Status „Übersprungen“ zugeordnet. Wenn nicht eindeutige Tests als fehlerhaft angezeigt werden sollen, verwenden Sie den Wert **TRUE**.|
|**InProcMode**|False|Wenn die Tests im selben Prozess wie der MSTest-Adapter ausgeführt werden sollen, legen Sie diesen Wert auf **true** fest. Diese Einstellung führt zu einer geringen Leistungssteigerung. Wenn ein Test allerdings mit einer Ausnahme beendet wird, werden die restlichen Tests nicht ausgeführt.|
|**AssemblyResolution**|False|Sie können Pfade zu weiteren Assemblys angeben, wenn Komponententests gefunden und ausgeführt werden. Verwenden Sie diese Pfade beispielsweise für Abhängigkeitsassemblys, die sich nicht im selben Verzeichnis wie die Testassembly befinden. Um einen Pfad anzugeben, verwenden Sie ein **Directory Path**-Element. Pfade können Umgebungsvariablen enthalten.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Siehe auch

- [Konfigurieren eines Testlaufs](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Anpassen der Code Coverage-Analyse](../test/customizing-code-coverage-analysis.md)
- [Visual Studio-Testaufgabe (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)

