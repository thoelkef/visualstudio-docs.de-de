---
title: Generieren von Codemetriken über die IDE oder über die Befehlszeile
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37f208421079f77cadaf85556e00a8f8548c6182
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188807"
---
# <a name="how-to-generate-code-metrics-data"></a>Gewusst wie: Generieren von Codemetrikdaten

Sie können Codemetrikdaten auf drei Arten generieren:

- Durch Installieren von [FxCop-Analyzern](#fxcop-analyzers-code-metrics-rules) und Aktivieren der vier Code metrikregeln (Wartbarkeit), die Sie enthält.

- Indem Sie den Menübefehl [ > **Code Metrik** **analysieren** ](#calculate-code-metrics-menu-command) in Visual Studio auswählen.

- In der [Befehlszeile](#command-line-code-metrics) für C# -und-Visual Basic Projekte.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Codemetrikregeln für FxCop-Analysen

Das [nuget-Paket "fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) " umfasst mehrere Code Metrik- [Analyse](roslyn-analyzers-overview.md) Regeln:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506-avoid-excessive-class-coupling.md)

Diese Regeln sind standardmäßig deaktiviert, aber Sie können Sie über [**Projektmappen-Explorer**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) oder in einer [Regel Satz](using-rule-sets-to-group-code-analysis-rules.md) Datei aktivieren. Wenn Sie z. b. Regel CA1502 als Warnung aktivieren möchten, enthält die RuleSet-Datei den folgenden Eintrag:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Konfiguration

Sie können die Schwellenwerte konfigurieren, bei denen die codemetrikregeln im Paket FxCop Analyzer ausgelöst werden.

1. Erstellen einer Textdatei Beispielsweise können Sie " *codemetricsconfig. txt*" benennen.

2. Fügen Sie die gewünschten Schwellenwerte der Textdatei im folgenden Format hinzu:

   ```txt
   CA1502: 10
   ```

   In diesem Beispiel ist die Regel [CA1502](ca1502.md) so konfiguriert, dass Sie ausgelöst wird, wenn die zyklomatische Komplexität einer Methode größer als 10 ist.

3. Markieren Sie im **Eigenschaften** Fenster von Visual Studio oder in der Projektdatei die Buildaktion der Konfigurationsdatei als [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Beispiel:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Menübefehl "Code Metrik berechnen"

Generieren Sie Codemetriken für ein oder alle geöffneten Projekte in der IDE mithilfe des Menüs **analysieren**  > **Code Metriken** .

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generieren von Codemetrikergebnissen für eine gesamte Projekt Mappe

Sie können Code Metrikergebnisse für eine gesamte Lösung auf eine der folgenden Arten generieren:

- Wählen Sie in der Menüleiste **analysieren** aus,  >   > **für die Lösung** **Code Metriken berechnen** .

- Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die Lösung, und wählen Sie dann **Codemetriken berechnen**aus.

- Wählen Sie im Fenster **Code Metrikergebnisse** die Schaltfläche **Code Metrik für Projekt Mappe berechnen aus** .

Die Ergebnisse werden generiert, und das Fenster **Code Metrikergebnisse** wird angezeigt. Um die Ergebnis Details anzuzeigen, erweitern Sie die Struktur in der Spalte **Hierarchie** .

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generieren von Codemetrikergebnissen für ein oder mehrere Projekte

1. Wählen Sie in **Projektmappen-Explorer**mindestens ein Projekt aus.

1. Wählen Sie in der Menüleiste **analysieren** aus,  >   > **Metrik Code Metrik** **für ausgewählte Projekte**berechnen.

Die Ergebnisse werden generiert, und das Fenster **Code Metrikergebnisse** wird angezeigt. Um die Ergebnis Details anzuzeigen, erweitern Sie die Struktur in der **Hierarchie**.

::: moniker range="vs-2017"

> [!NOTE]
> Der Befehl **Code Metriken berechnen** funktioniert nicht für .net Core-und .NET Standard-Projekte. Zum Berechnen von Codemetriken für ein .net Core-oder .NET Standard Projekt können Sie folgende Aktionen ausführen:
>
> - Berechnen Sie Codemetriken stattdessen über die [Befehlszeile](#command-line-code-metrics) .
>
> - Upgrade auf [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Befehlszeilencodemetriken

Sie können Codemetrikdaten über die Befehlszeile für C# und Visual Basic Projekte für .NET Framework-, .net Core-und .NET Standard-apps generieren. Zum Ausführen von Codemetriken über die Befehlszeile installieren Sie das [nuget-Paket Microsoft. Code Analysis. Metrics](#microsoftcodeanalysismetrics-nuget-package) , oder erstellen Sie die ausführbare Datei " [Metrics. exe](#metricsexe) " selbst.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Microsoft. Code Analysis. Metrics-nuget-Paket

Die einfachste Möglichkeit zum Generieren von Codemetrikdaten über die Befehlszeile besteht darin, das nuget-Paket [Microsoft. Code Analysis. Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) zu installieren. Nachdem Sie das Paket installiert haben, führen Sie `msbuild /t:Metrics` aus dem Verzeichnis aus, das die Projektdatei enthält. Beispiel:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

Sie können den Namen der Ausgabedatei überschreiben, indem Sie `/p:MetricsOutputFile=<filename>` angeben. Sie können auch Code Metrikdaten im [Legacy Stil](#previous-versions) erhalten, indem Sie `/p:LEGACY_CODE_METRICS_MODE=true`angeben. Beispiel:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>Ausgabe von Codemetriken

Die generierte XML-Ausgabe hat folgendes Format:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="metricsexe"></a>Metrik. exe

Wenn Sie das nuget-Paket nicht installieren möchten, können Sie die ausführbare Datei " *Metrics. exe* " direkt generieren und verwenden. So generieren Sie die ausführbare Datei " *Metrics. exe* "

1. Klonen Sie das Repository [dotnet/Roslyn-Analyzers](https://github.com/dotnet/roslyn-analyzers) .
2. Öffnen Sie Developer-Eingabeaufforderung für Visual Studio als Administrator.
3. Führen Sie im Stamm **Verzeichnis des Roslyn-Analyzers-** Repository den folgenden Befehl aus: `Restore.cmd`
4. Wechseln Sie in das Verzeichnis *src\tools*.
5. Führen Sie den folgenden Befehl aus, um das Projekt " **Metrics. csproj** " zu erstellen:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Eine ausführbare Datei namens " *Metrics. exe* " wird im Verzeichnis " *artifakts\bin* " unter dem Repository-Stammverzeichnis generiert.

#### <a name="metricsexe-usage"></a>Verwendung von "Metrics. exe"

Stellen Sie zum Ausführen von " *Metrics. exe*" ein Projekt oder eine Projekt Mappe und eine XML-Ausgabedatei als Argumente bereit. Beispiel:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Legacy Modus

Sie können " *Metrics. exe* " im *Legacy Modus*erstellen. Die Legacy Modus-Version des Tools generiert Metrikwerte, die näher an den [von den älteren Versionen des Tools generierten](#previous-versions)Werten liegen. Außerdem generiert " *Metrics. exe* " im Legacy Modus Codemetriken für denselben Satz von Methoden Typen, für die vorherige Versionen des Tools Codemetriken generiert haben. Beispielsweise werden keine Codemetrikdaten für die Feld-und Eigenschafteninitialisierer generiert. Der Legacy Modus ist aus Gründen der Abwärtskompatibilität nützlich, oder Sie verfügen über Code-Check-in-Gates, die auf codemetriknummern basieren Der Befehl zum Erstellen von " *Metrics. exe* " im Legacy Modus lautet:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Weitere Informationen finden Sie unter [Aktivieren der Erstellung von Codemetriken im Legacy Modus](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Frühere Versionen

Visual Studio 2015 enthielt ein Befehlszeilen-codemetriktool, das auch " *Metrics. exe*" genannt wurde. Diese vorherige Version des Tools hat eine binäre Analyse, d. h. eine assemblybasierte Analyse, durchgeführt. Das neue Tool *Metrics. exe* analysiert stattdessen Quellcode. Da das neue Tool " *Metrics. exe* " auf einem Quell Code basiert, unterscheiden sich die Metriken der befehlszeilencodemetriken von denen, die von der Visual Studio-IDE und früheren Versionen von " *Metrics. exe*" generiert werden

Das neue befehlszeilencodemetrik-Tool berechnet Metriken, auch wenn Quell Code Fehler vorhanden sind, solange die Projekt Mappe und das Projekt geladen werden können.

#### <a name="metric-value-differences"></a>Unterschiede bei Metriken

Die `LinesOfCode` Metrik ist im neuen befehlszeilencodemetriktool präziser und zuverlässiger. Es ist unabhängig von CodeGen-unterschieden und ändert sich nicht, wenn sich das Toolset oder die Laufzeit ändert. Das neue Tool zählt tatsächliche Codezeilen, einschließlich leerer Zeilen und Kommentare.

Bei anderen Metriken, z. b. `CyclomaticComplexity` und `MaintainabilityIndex`, werden dieselben Formeln wie in früheren Versionen von " *Metrics. exe*" verwendet, aber das neue Tool zählt die Anzahl der `IOperations` (logische Quell Anweisungen) anstelle von Intermediate Language (IL)-Anweisungen. Die Zahlen unterscheiden sich geringfügig von den Werten, die von der Visual Studio-IDE und früheren Versionen von " *Metrics. exe*" generiert werden.

## <a name="see-also"></a>Siehe auch

- [Verwenden des Fensters "Code Metrikergebnisse"](../code-quality/working-with-code-metrics-data.md)
- [Codemetrikwerte](../code-quality/code-metrics-values.md)
