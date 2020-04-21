---
title: Generieren von Codemetriken aus der IDE oder Befehlszeile
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abae26ed8a5e5db74f7b0d04db66d9d99930d5c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649323"
---
# <a name="how-to-generate-code-metrics-data"></a>Gewusst wie: Generieren von Codemetrikdaten

Sie können Codemetrikdaten auf drei Arten generieren:

- Durch die Installation von [FxCop-Analysatoren](#fxcop-analyzers-code-metrics-rules) und aktivieren Sie die vier darin enthaltenen Codemetrikregeln (Wartbarkeit).

- Wenn Sie [ **Analyze** > ](#calculate-code-metrics-menu-command) den Menübefehl Codemetriken berechnen in Visual Studio auswählen.

- Aus der [Befehlszeile](#command-line-code-metrics) für C- und Visual Basic-Projekte.

## <a name="fxcop-analyzers-code-metrics-rules"></a>FxCop-Analysatoren-Codemetrikregeln

Das [FxCopAnalyzers NuGet-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) enthält mehrere Code-Metriken-Analyzer-Regeln: [analyzer](roslyn-analyzers-overview.md)

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

Diese Regeln sind standardmäßig deaktiviert, Sie können sie jedoch im [**Projektmappen-Explorer**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) oder in einer [Regelsatzdatei](using-rule-sets-to-group-code-analysis-rules.md) aktivieren. Um beispielsweise die Regel CA1502 als Warnung zu aktivieren, enthält Ihre .ruleset-Datei den folgenden Eintrag:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Konfiguration

Sie können die Schwellenwerte konfigurieren, bei denen die Codemetrikregeln im FxCop-Analyzer-Paket ausgelöst werden.

1. Erstellen einer Textdatei Als Beispiel können Sie *codeMetricsConfig.txt*nennen.

2. Fügen Sie der Textdatei die gewünschten Schwellenwerte im folgenden Format hinzu:

   ```txt
   CA1502: 10
   ```

   In diesem Beispiel wird Regel [CA1502](ca1502.md) so konfiguriert, dass sie ausgelöst wird, wenn die zyklomatische Komplexität einer Methode größer als 10 ist.

3. Markieren Sie im **Eigenschaftenfenster** von Visual Studio oder in der Projektdatei die Buildaktion der Konfigurationsdatei als [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Beispiel:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Menübefehl Codemetriken berechnen

Generieren Sie Codemetriken für eines oder alle geöffneten Projekte in der IDE mithilfe des**Menüs Codemetriken** **analysieren.** > 

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generieren von Codemetrikergebnissen für eine gesamte Lösung

Sie können Codemetrikergebnisse für eine gesamte Lösung auf eine der folgenden Arten generieren:

- Wählen Sie in der Menüleiste **die** > Option**Codemetriken** > **für Lösung**berechnen aus .

- Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf die Projektmappe, und wählen Sie dann **Codemetriken berechnen**aus.

- Wählen Sie im Fenster **Codemetrikergebnisse** die Schaltfläche **Codemetriken für Lösung berechnen** aus.

Die Ergebnisse werden generiert, und das Fenster **Codemetrikergebnisse** wird angezeigt. Um die Ergebnisdetails anzuzeigen, erweitern Sie die Struktur in der Spalte **Hierarchie.**

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generieren von Codemetrikergebnissen für ein oder mehrere Projekte

1. Wählen Sie im **Projektmappen-Explorer**ein oder mehrere Projekte aus.

1. **Wählen** > Sie in der Menüleiste**Codemetriken** > **für ausgewählte Projekte**berechnen aus.

Die Ergebnisse werden generiert, und das Fenster **Codemetrikergebnisse** wird angezeigt. Um die Ergebnisdetails anzuzeigen, erweitern Sie die Struktur in der **Hierarchie**.

::: moniker range="vs-2017"

> [!NOTE]
> Der Befehl **Codemetriken berechnen** funktioniert nicht für .NET Core- und .NET Standard-Projekte. Um Codemetriken für ein .NET Core- oder .NET Standard-Projekt zu berechnen, können Sie:
>
> - Codemetriken stattdessen aus der [Befehlszeile](#command-line-code-metrics) berechnen
>
> - Upgrade auf [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Codemetriken für Befehlszeilenzeilen

Sie können Codemetrikdaten aus der Befehlszeile für C- und Visual Basic-Projekte für .NET Framework-, .NET Core- und .NET Standard-Apps generieren. Um Codemetriken über die Befehlszeile auszuführen, installieren Sie das [NuGet-Paket Microsoft.CodeAnalysis.Metrics,](#microsoftcodeanalysismetrics-nuget-package) oder erstellen Sie die ausführbare Datei [Metrics.exe](#metricsexe) selbst.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Microsoft.CodeAnalysis.Metrics NuGet-Paket

Die einfachste Möglichkeit, Codemetrikdaten aus der Befehlszeile zu generieren, besteht darin, das NuGet-Paket [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) zu installieren. Nachdem Sie das Paket installiert `msbuild /t:Metrics` haben, führen Sie aus dem Verzeichnis aus, das die Projektdatei enthält. Beispiel:

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

Sie können den Namen der Ausgabedatei überschreiben, indem Sie angeben. `/p:MetricsOutputFile=<filename>` Sie können auch Codemetrikdaten [im Legacy-Stil](#previous-versions) abrufen, indem Sie `/p:LEGACY_CODE_METRICS_MODE=true`angeben. Beispiel:

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

### <a name="code-metrics-output"></a>Codemetrikausgabe

Die generierte XML-Ausgabe hat das folgende Format:

::: moniker range=">=vs-2019"
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
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
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
::: moniker-end
::: moniker range="vs-2017"
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
::: moniker-end

### <a name="metricsexe"></a>Metrics.exe

Wenn Sie das NuGet-Paket nicht installieren möchten, können Sie die ausführbare Datei *Metrics.exe* direkt generieren und verwenden. So generieren Sie die ausführbare Datei *Metrics.exe:*

1. Klonen Sie das Repository der [Dotnet/Roslyn-Analyzer.](https://github.com/dotnet/roslyn-analyzers)
2. Öffnen Sie die Eingabeaufforderung für Entwickler für Visual Studio als Administrator.
3. Führen Sie von der Wurzel des **Repos roslyn-analyzers** den folgenden Befehl aus:`Restore.cmd`
4. Ändern Sie das Verzeichnis in *src-Tools*.
5. Führen Sie den folgenden Befehl aus, um das Projekt **Metrics.csproj** zu erstellen:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Eine ausführbare Datei mit dem Namen *Metrics.exe* wird im Verzeichnis *artifacts-bin* unter dem Repository-Stamm generiert.

#### <a name="metricsexe-usage"></a>Metrik.exe Verwendung

Um *Metrics.exe*auszuführen, geben Sie ein Projekt oder eine Projektmappe und eine Ausgabe-XML-Datei als Argumente an. Beispiel:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Legacy-Modus

Sie können *Metrics.exe* im *Legacy-Modus*erstellen. Die Legacymodusversion des Tools generiert Metrikwerte, die näher an den [älteren Versionen des Tools liegen, die generiert wurden.](#previous-versions) Darüber hinaus generiert *Metrics.exe* im Legacymodus Codemetriken für denselben Satz von Methodentypen, für die frühere Versionen des Tools Codemetriken generiert haben. Beispielsweise werden keine Codemetrikdaten für Feld- und Eigenschaftsinitialisierer generiert. Der Legacymodus ist für die Abwärtskompatibilität nützlich, oder wenn Sie Code-Check-In-Gates basierend auf Codemetriknummern haben. Der Befehl zum Erstellen von *Metrics.exe* im Legacy-Modus lautet:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Weitere Informationen finden Sie unter [Aktivieren der Generierung von Codemetriken im Legacymodus](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Vorgängerversionen

::: moniker range=">=vs-2019"
Visual Studio 2015 enthielt ein Befehlszeilencode-Metriken-Tool, das auch *als Metrics.exe*bezeichnet wurde. Diese vorherige Version des Tools hat eine binäre Analyse durchgeführt, d. h. eine assemblybasierte Analyse. Die neuere Version des Tools *Metrics.exe* analysiert stattdessen den Quellcode. Da das Tool *"Neuere Metrics.exe"* quellcodebasiert ist, können sich die Ergebnisse von Befehlszeilencodemetriken von denen unterscheiden, die von der Visual Studio-IDE und früheren Versionen von *Metrics.exe*generiert wurden. Ab Visual Studio 2019 analysiert die Visual Studio-IDE Quellcode wie das Befehlszeilentool, und die Ergebnisse sollten identisch sein.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015 enthielt ein Befehlszeilencode-Metriken-Tool, das auch *als Metrics.exe*bezeichnet wurde. Diese vorherige Version des Tools hat eine binäre Analyse durchgeführt, d. h. eine assemblybasierte Analyse. Das neue Tool *Metrics.exe* analysiert stattdessen den Quellcode. Da das neue Tool *Metrics.exe* quellcodebasiert ist, unterscheiden sich die Ergebnisse von Befehlszeilencodemetriken von denen, die von der Visual Studio-IDE und früheren Versionen von *Metrics.exe*generiert wurden.
::: moniker-end

Das neue Befehlszeilencode-Metriken-Tool berechnet Metriken auch bei Vorhandensein von Quellcodefehlern, solange die Projektmappe und das Projekt geladen werden können.

#### <a name="metric-value-differences"></a>Metrische Wertunterschiede

::: moniker range=">=vs-2019"
Ab Visual Studio 2019 Version 16.4 und Microsoft.CodeAnalysis.Metics `SourceLines` (2.9.5), und `ExecutableLines` ersetzen Sie die vorherige `LinesOfCode` Metrik. Beschreibungen der neuen Metriken finden Sie unter [Codemetrikwerte](../code-quality/code-metrics-values.md). Die `LinesOfCode` Metrik ist im Legacymodus verfügbar.
::: moniker-end
::: moniker range="vs-2017"
Die `LinesOfCode` Metrik ist im neuen Befehlszeilencode-Metrikwerkzeug genauer und zuverlässiger. Es ist unabhängig von Codegen-Unterschieden und ändert sich nicht, wenn sich das Toolset oder die Laufzeit ändert. Das neue Werkzeug zählt tatsächliche Codezeilen, einschließlich leerer Zeilen und Kommentare.
::: moniker-end

Andere Metriken, `CyclomaticComplexity` z. B. und `MaintainabilityIndex` verwenden dieselben Formeln wie frühere Versionen von *Metrics.exe*, aber das neue Tool zählt die Anzahl der (logischen Quellanweisungen) anstelle von `IOperations` IL-Anweisungen (Intermediate Language). Die Zahlen unterscheiden sich geringfügig von denen, die von der Visual Studio-IDE und früheren Versionen von *Metrics.exe*generiert wurden.

## <a name="see-also"></a>Siehe auch

- [Verwenden des Fensters Codemetrikergebnisse](../code-quality/working-with-code-metrics-data.md)
- [Codemetrikwerte](../code-quality/code-metrics-values.md)
