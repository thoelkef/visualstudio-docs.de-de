---
title: "Live Unit Testing – häufig gestellte Fragen | Microsoft-Dokumentation"
ms.date: 2017-10-03
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 2437a138e9e83d3b723971b53dac413ad0ea4151
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2018
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing – häufig gestellte Fragen

## <a name="live-unit-testing-is-improved-and-enhanced-regularly-how-can-i-find-information-about-the-latest-new-features-and-enhancements"></a>Live Unit Testing wird regelmäßig verbessert und erweitert. Wie finde ich Informationen zu den neuesten Features und Verbesserungen?

**Antwort:**

Weitere Informationen zu neuen Features und Verbesserungen für Live Unit Testing ab Visual Studio 2017 Version 15.3 finden Sie unter [What‘s New in Live Unit Testing (Neuerungen in Live Unit Testing)](live-unit-testing-whats-new.md).


## <a name="what-test-frameworks-does-live-unit-testing-support-and-what-are-the-minimum-supported-versions"></a>Welche Testframeworks werden von Live Unit Testing unterstützt und welche sind die unterstützten Mindestversionen?

**Antwort:**

Live Unit Testing kann mit den drei gängigen Frameworks für Komponententests verwendet werden, die in der folgenden Tabelle aufgeführt sind. Die unterstützte Mindestversion der Adapter und Frameworks ist ebenfalls in der Tabelle aufgeführt. Die Frameworks für Komponententests sind auf „NuGet.org“ verfügbar.

<table>
<tr>
   <th>Testframework</th>
   <th>Mindestversion des Visual Studio-Adapters</th>
   <th>Mindestversion des Frameworks</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio, Version 2.2.0-beta3-build1187</td>
   <td>xUnit 1.9.2</td>
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter, Version 3.5.1</td>
   <td>NUnit, Version 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Wenn Sie ältere auf MSTest-basierenden Testprojekte haben, die sich auf `Microsoft.VisualStudio.QualityTools.UnitTestFramework` beziehen, und Sie nicht auf die neueren MSTest-NuGet-Pakete umsteigen möchten, sollten Sie auf Visual Studio 2017 Version 15.4 upgraden.

In einigen Fällen müssen Sie explizit die NuGet-Pakete wiederherstellen, auf die die Projekte in der Projektmappe verweisen, damit Live Unit Testing funktioniert. Hierzu können Sie entweder die Projektmappe explizit erstellen (wählen Sie im obersten Visual Studio-Menü **Erstellen** und dann **Projektmappe neu erstellen** aus) oder Pakete in der Projektmappe wiederherstellen (klicken Sie mit der rechten Maustaste auf die Projektmappe, und wählen Sie **NuGet-Pakete wiederherstellen** aus), bevor Sie Living Unit Testing aktivieren.


## <a name="does-live-unit-testing-work-with-net-core"></a>Kann Live Unit Testing mit .NET Core verwendet werden?

**Antwort:**

Ja. Live Unit Testing funktioniert mit .NET Core und .NET Frameworks. Die Unterstützung für .NET Core wurde kürzlich in Visual Studio 2017 Version 15.3 hinzugefügt. Führen Sie ein Upgrade auf diese Version von Visual Studio aus, wenn Sie die Live Unit Testing-Unterstützung für .NET Core möchten.

## <a name="why-doesnt-live-unit-testing-work-when-i-turn-it-on"></a>Warum funktioniert Live Unit Testing nicht, wenn ich diese Funktion aktiviere?

**Antwort:**

Das **Ausgabefenster** (wenn das Live Unit Testing-Dropdownmenü ausgewählt ist) sollte Ihnen sagen, warum Live Unit Testing nicht funktioniert. Live Unit Testing funktioniert möglicherweise aus einem der folgenden Gründe nicht:

- Wenn die NuGet-Pakete, auf die von Projekten in der Projektmappe verwiesen wird, nicht wiederhergestellt wurden, funktioniert Live Unit Testing nicht. Eine explizite Erstellung der Projektmappe oder das Wiederherstellen von NuGet-Paketen in der Projektmappe vor dem Aktivieren von Live Unit Testing sollte dieses Problem beheben.

- Wenn Sie MSTest-basierte Tests in den Projekten verwenden, stellen Sie sicher, dass Sie den Verweis auf `Microsoft.VisualStudio.QualityTools.UnitTestFramework` entfernen und Verweise auf die neuesten MSTest-NuGet-Pakete `MSTest.TestAdapter` (Mindestversion 1.1.11 ist erforderlich) und `MSTest.TestFramework` (Mindestversion 1.1.11 ist erforderlich) hinzufügen. Weitere Informationen finden Sie im Abschnitt „Unterstützte Testframeworks“ im Thema [Verwenden von Live Unit Testing in Visual Studio 2017 Enterprise Edition](live-unit-testing.md#supported-test-frameworks).

- Mindestens ein Projekt in der Projektmappe muss einen NuGet-Verweis oder einen direkten Verweis auf das xUnit-, NUnit- oder MSTest-Testframework aufweisen. Dieses Projekt sollte auch auf ein entsprechendes NuGet-Paket mit Visual Studio-Testadaptern verweisen. Auf den Visual Studio-Testadapter kann auch über eine `.runsettings`-Datei verwiesen werden. Die `.runsettings`-Datei muss einen Eintrag wie den folgenden enthalten:

   ```xml
    <RunSettings>
       <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
       </RunConfiguration>
    </RunSettings>
   ``` 

## <a name="why-does-live-unit-testing-show-incorrect-coverage-after-you-upgrade-the-test-adapter-referenced-in-your-visual-studio-projects-to-the-supported-version"></a>Warum wird beim Live Unit Testing eine falsche Abdeckung angezeigt, nachdem Sie ein Upgrade auf den in Ihren Visual Studio-Projekten verwiesenen Testadapter auf die unterstützte Version durchgeführt haben?

**Antwort:**

- Wenn mehrere Projekte in der Projektmappe auf das NuGet-Testadapterpaket verweisen, muss jedes auf die unterstützte Version upgegradet werden.

- Stellen Sie sicher, dass die Datei „MSBuild .props“, die aus dem Testadapterpaket importiert wurde, ebenfalls ordnungsgemäß aktualisiert wird. Überprüfen Sie die NuGet-Paket Version bzw. den Pfad des Imports, der sich in der Regel am Anfang der Datei befindet, z.B.:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="can-i-customize-my-live-unit-testing-builds"></a>Kann ich meine Live Unit Testing-Builds anpassen?

**Antwort:**

Wenn Ihre Projektmappe benutzerdefinierte Schritte für einen Buildvorgang zur Instrumentierung erfordert (Live Unit Testing), die für den „normalen“ nicht instrumentierten Build nicht erforderlich sind, dann können Sie Code zum Projekt oder zu TARGETS-Dateien hinzufügen, der auf die Eigenschaft `BuildingForLiveUnitTesting` prüft und vorab oder anschließend benutzerdefinierte Buildschritte ausführt. Sie können basierend auf dieser Eigenschaft auch bestimmte Buildschritte entfernen (z.B. Veröffentlichen oder Generieren von Paketen) oder einem Live Unit Testing-Build Buildschritte hinzuzufügen (z.B. Kopieren der erforderlichen Komponenten). Dies ändert Ihren regulären Build nicht, sondern wirkt sich nur auf Live Unit Testing-Builds aus.

Möglicherweise gibt es z.B. ein Ziel, das NuGet-Pakete während eines regulären Buildvorgangs erzeugt. Sie möchten wahrscheinlich nicht, dass NuGet-Pakete nach jeder Änderung generiert werden. Also können Sie dieses Ziel im Live Unit Testing-Build deaktivieren, indem Sie z.B. Folgendes ausführen:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Fehlermeldungen mit &lt;OutputPath&gt; oder &lt;OutDir&gt;

**Wenn Live Unit Testing versucht, meine Projektmappe zu erstellen, warum wird dann folgende Fehlermeldung angezeigt: „`<OutputPath>` oder `<OutDir>` werden scheinbar ohne Bedingungen festgelegt, und Live Unit Testing führt keine Tests der Ausgabeassembly aus“?**

**Antwort:**

Dies kann passieren, wenn der Buildvorgang für Ihre Projektmappe `<OutputPath>` oder `<OutDir>` ohne Bedingungen überschreibt, sodass diese Elemente kein Unterverzeichnis von `<BaseOutputPath>` sind. In solchen Fällen funktioniert Live Unit Testing nicht, da von der Funktion diese Elemente auch überschrieben werden, um sicherzustellen, dass Buildartefakte in einem Ordner unter `<BaseOutputPath>` abgelegt werden. Wenn Sie den Speicherort überschreiben müssen, in dem Ihre Buildartefakte in einem regulären Build abgelegt werden, überschreiben Sie `<OutputPath>` bedingt basierend auf `<BaseOutputPath>`.

Beispiel: Ihr Build überschreibt `<OutputPath>`, wie unten dargestellt:

```xml 
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

Dann können Sie ihn durch Folgendes ersetzen:

```xml 
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```
 
Dadurch wird sichergestellt, dass sich `<OutputPath>` im Ordner `<BaseOutputPath>` befindet.

Überschreiben Sie `<OutDir>` nicht direkt im Buildvorgang. Überschreiben Sie stattdessen `<OutputPath>`, um Buildartefakte an einem bestimmten Speicherort abzulegen.
 
## <a name="setting-the-location-of-live-unit-testing-build-artifacts"></a>Festlegen des Speicherorts von Live Unit Testing-Buildartefakten

**Ich möchte die Artefakte eines Live Unit Testing-Builds an einem bestimmten Speicherort ablegen, statt den Standardspeicherort im Ordner `.vs` zu verwenden. Wie kann ich ihn ändern?**

**Antwort:**

Legen Sie die `LiveUnitTesting_BuildRoot`-Umgebungsvariable auf Benutzerebene auf den Pfad fest, in dem die Live Unit Testing-Buildartefakte abgelegt werden sollen. 

## <a name="how-is-running-tests-from-test-explorer-window-different-from-running-tests-in-live-unit-testing"></a>Wie unterscheidet sich das Ausführen von Tests im Test-Explorer-Fenster vom Ausführen von Tests in Live Unit Testing?

**Antwort:**

Es gibt mehrere Unterschiede:

- Beim Ausführen oder Debuggen von Tests im Test-Explorer-Fenster werden reguläre Binärdateien ausgeführt. Live Unit Testing führt dagegen instrumentierte Binärdateien aus. Wenn Sie instrumentierte Binärdateien debuggen möchten, wird durch das Hinzufügen eines [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch)-Methodenaufrufs in der Testmethode der Debugger bei jeder Ausführung der Methode gestartet (auch bei der Ausführung durch Live Unit Testing), und Sie können dann die instrumentierte Binärdatei anfügen und debuggen. Wir hoffen jedoch, dass die Instrumentierung der meisten Benutzerszenarien für Sie transparent ist und Sie instrumentierte Binärdateien nicht debuggen müssen.

- Live Unit Testing erstellt keine neue Anwendungsdomäne zum Ausführen von Tests. Tests, die im Test-Explorer-Fenster ausgeführt werden, erstellen dagegen eine neue Anwendungsdomäne.

- Live Unit Testing testet jede Testassembly sequenziell. Wenn Sie jedoch mehrere Tests im Test-Explorer-Fenster ausführen und die Schaltfläche **Tests parallel ausführen** ausgewählt haben, werden sie parallel ausgeführt.

- Für die Ermittlung und Ausführung von Tests in Live Unit Testing wird Version 2 von `TestPlatform` verwendet, während im Test-Explorer-Fenster Version 1 verwendet wird. In den meisten Fällen sollten Sie allerdings keinen Unterschied feststellen. 

- Test-Explorer führt derzeit Tests standardmäßig in einem Singlethread-Apartment (STA) aus, während Live Unit Testing Tests in einem Multithread-Apartment (MTA) ausgeführt. Um MSTest-Tests in STA in Live Unit Testing auszuführen, versehen Sie die Testmethode oder die enthaltende Klasse mit dem `<STATestMethod>`- oder dem `<STATestClass>`-Attribut, das im NuGet-Paket `MSTest.STAExtensions 1.0.3-beta` enthalten ist. Ergänzen Sie für NUnit die Testmethode mit dem `<RequiresThread(ApartmentState.STA)>`-Attribut, und für xUnit mit dem `<STAFact>`-Attribut.

## <a name="how-do-i-exclude-tests-from-participating-in-live-unit-testing"></a>Wie schließe ich Tests von Live Unit Testing aus?

**Antwort:**

Die benutzerspezifische Einstellung finden Sie im Abschnitt „Einschließen und Ausschließen von Testprojekten und Testmethoden“ im Thema [Verwenden von Live Unit Testing in Visual Studio 2017 Enterprise Edition](live-unit-testing.md#including-and-excluding-test-projects-and-test-methods). Dies ist äußerst nützlich, wenn Sie einen bestimmten Satz von Tests für eine bestimmte Bearbeitungssitzung ausführen möchten oder Ihre eigenen persönlichen Einstellungen beibehalten möchten.
 
Bei spezifischen Einstellungen von Projektmappen können Sie das <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName>-Attribut programmgesteuert anwenden, um Methoden, Eigenschaften, Klassen oder Strukturen von der Instrumentierung durch Live Unit Testing auszuschließen. Darüber hinaus können Sie auch die `<ExcludeFromCodeCoverage>`-Eigenschaft in der Projektdatei auf `true` festlegen, um zu verhindern, dass das gesamte Projekt instrumentiert wird. Live Unit Testing führt die Tests dennoch aus, die nicht instrumentiert wurden, aber deren Abdeckung wird nicht visuell dargestellt.

Sie können auch überprüfen, ob `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` in der aktuellen Anwendungsdomäne geladen wird und auf dieser Grundlage Tests deaktivieren. Beispielsweise können Sie mit xUnit Folgendes ausführen:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

## <a name="why-are-win32-pe-headers-different-in-instrumented-assemblies-built-by-live-unit-testing"></a>Warum sind Win32 PE-Header in von Live Unit Testing erstellten instrumentierten Assemblys anders?

**Antwort:**

Dieses Problem wurde behoben und besteht nicht mehr in Visual Studio 2017 Version 15.3. Führen Sie ein Upgrade auf diese Version von Visual Studio aus.

Für ältere Versionen von Visual Studio 2017 gibt es ein bekanntes Problem, das dazu führen kann, dass Live Unit Testing-Builds die folgenden Win32 PE-Headerdaten nicht einbetten:

- Dateiversion (angegeben durch @System.Reflection.AssemblyFileVersionAttribute im Code).

- Win32-Symbol (angegeben durch `/win32icon:` an der Befehlszeile).

- Win32-Manifest (angegeben durch `/win32manifest:` an der Befehlszeile).

Tests, die auf diesen Werten basieren, können fehlschlagen, wenn sie von Live Unit Testing ausgeführt werden.

## <a name="why-does-live-unit-testing-keep-building-my-solution-all-the-time-even-if-i-am-not-making-any-edits"></a>Warum erstellt Live Unit Testing meine Projektmappe immer wieder, auch wenn ich keine Änderungen vornehme?

**Antwort:**

Dies kann passieren, wenn der Buildvorgang der Projektmappe Quellcode generiert, der Teil der Projektmappe selbst ist, und in den Buildzieldateien keine entsprechenden Eingaben und Ausgaben angegeben sind. Zielen sollte eine Liste von Eingaben und Ausgaben bereitgestellt werden, damit MSBuild die entsprechenden aktuellen Überprüfungen vornehmen kann und bestimmen kann, ob ein neuer Build erforderlich ist.

Live Unit Testing startet einen Buildvorgang, wenn erkannt wird, dass Quelldateien geändert wurden. Da der Buildvorgang Ihrer Projektmappe Quelldateien generiert, gerät Live Unit Testing in eine unendliche Buildschleife. Wenn die Eingaben und Ausgaben des Ziels jedoch überprüft werden, wenn Live Unit Testing den zweiten Buildvorgang startet (nach der Ermittlung neu generierter Quelldateien aus dem vorherigen Build), wird die Schleife unterbrochen, da die Überprüfungen der Eingaben und Ausgaben darauf hinweisen, dass alles auf dem neuesten Stand ist.  

## <a name="how-does-live-unit-testing-work-with-the-lightweight-solution-load-feature"></a>Wie funktioniert Live Unit Testing mit der Funktion „Lightweight-Ladevorgang für Projektmappen“?

**Antwort:**

Live Unit Testing funktioniert derzeit nicht richtig mit dem Lightweight-Ladefeature für Projektmappen. Dies funktioniert erst, nachdem mindestens eines der Testprojekte geladen wurde. Andernfalls funktioniert es nicht, da Live Unit Testing von mindestens einem der Testprojekte abhängt, das auf einen Testadapter verweist (MSTest, xUnit oder NUnit), der geladen wird.

> [!NOTE]
> Der Lightweight-Ladevorgang für Projektmappen ist in Visual Studio 2017 Version 15.5 und höher nicht mehr enthalten. In Visual Studio Version 2017 Version 15.5 und höher laden große Projektmappen, die verwalteten Code enthalten, auch ohne den Lightweight-Ladevorgang für Projektmappen viel schneller als zuvor.

## <a name="why-does-live-unit-testing-does-not-capture-coverage-from-a-new-process-created-by-a-test"></a>Warum erfasst Live Unit Testing die Abdeckung eines neuen Vorgangs nicht, der von einem Test erstellt wurde?

**Antwort:**

Dies ist ein bekanntest Problem und sollte in einem späteren Update von Visual Studio 2017 korrigiert werden.

## <a name="why-does-nothing-happen-after-i-include-or-exclude-tests-from-the-live-test-set"></a>Warum geschieht nichts, nachdem ich Tests in den Satz von Livetests eingeschlossen bzw. davon ausgeschlossen habe?

**Antwort:**

Dieses Problem wurde behoben und besteht in Visual Studio 2017 Version 15.3 nicht mehr. Führen Sie ein Upgrade auf diese Version von Visual Studio aus.

Für ältere Versionen von Visual Studio 2017 ist dies ein bekanntes Problem. Um dieses Problem zu umgehen, müssen Sie in einer beliebigen Datei eine Änderung vornehmen, nachdem Sie Tests eingeschlossen oder ausgeschlossen haben. 

## <a name="live-unit-testing-and-editor-icons"></a>Live Unit Testing und Editor-Symbole

**Warum werden keine Symbole im Editor angezeigt, obwohl Live Unit Testing basierend auf den Meldungen im Ausgabefenster Tests auszuführen scheint?**

**Antwort:**

Dies geschieht, wenn die Assemblys, die von Live Unit Testing verarbeitet werden, nicht instrumentiert werden. Beispielsweise ist Live Unit Testing nicht kompatibel mit Projekten, die `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` festlegen. In diesem Fall muss der Buildvorgang aktualisiert werden, um diese Einstellung zu entfernen oder in `true` zu ändern, damit Live Unit Testing funktioniert. 

## <a name="how-do-i-collect-more-detailed-logs-to-file-bug-reports"></a>Wie kann ich ausführlichere Protokolle für Dateifehlerberichte sammeln?

**Antwort:**

Sie haben mehrere Möglichkeiten, um ausführlichere Protokolle zu sammeln:

- Wechseln Sie zu **Extras**, **Optionen** und dann **Live Unit Testing**, und ändern Sie die Protokollierungsoption in **Ausführlich**. Dadurch werden ausführlichere Protokolle im Ausgabefenster angezeigt.

- Legen Sie die `LiveUnitTesting_BuildLog`-Benutzerumgebungsvariable auf den Namen der Datei fest, die Sie verwenden möchten, um das MSBuild-Protokoll zu erfassen. Detaillierte MSBuild-Protokollmeldungen von Live Unit Testing-Builds können dann aus dieser Datei abgerufen werden.

- Legen Sie die Umgebungsvariable`LiveUnitTesting_TestPlatformLog` auf `1` fest, um das Protokoll der Testplattform zu erfassen. Detaillierte Testplattform-Protokollmeldungen zu Live Unit Testing-Ausführungen können dann aus `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` abgerufen werden.

- Erstellen Sie eine Umgebungsvariable auf Benutzerebene mit dem Namen `VS_UTE_DIAGNOSTICS`, legen Sie sie auf 1 (oder einen beliebigen Wert) fest, und starten Sie Visual Studio neu. Jetzt sollten Sie eine umfangreiche Protokollierung auf der Registerkarte **Ausgabe – Tests** in Visual Studio sehen.

## <a name="see-also"></a>Siehe auch

[Live-Komponententests](live-unit-testing.md)

