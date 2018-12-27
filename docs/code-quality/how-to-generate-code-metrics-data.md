---
title: Generieren von codemetriken aus der IDE oder über die Befehlszeile
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83ec85855e17f8798f55b01f043d47d7140278e7
ms.sourcegitcommit: c7b16358a5d6f7ea1dd2f70a6ac2a8266efa9c15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53425772"
---
# <a name="how-to-generate-code-metrics-data"></a>Vorgehensweise: Generieren von Codemetrikdaten

Sie können die Codemetrikergebnisse für eine oder mehrere Projekte oder eine gesamte Projektmappe generieren. Codemetrik ist verfügbar, in das interaktive Entwicklungsumgebung (IDE) von Visual Studio und für C# und Visual Basic-Projekten in der Befehlszeile.

Darüber hinaus können Sie installieren ein [NuGet-Paket](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01) , enthält vier Codemetrik [Analyzer](roslyn-analyzers-overview.md) Regeln: CA1501, CA1502, CA1505 und CA1506. Diese Regeln sind standardmäßig deaktiviert, aber Sie können sie aus **Projektmappen-Explorer** oder in einem [Regelsatz](using-rule-sets-to-group-code-analysis-rules.md) Datei.

## <a name="visual-studio-ide-code-metrics"></a>Codemetrik für Visual Studio-IDE

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Codemetrikergebnisse für eine gesamte Projektmappe generieren

Sie können Codemetrikergebnisse für eine gesamte Projektmappe in einem der folgenden Arten generieren:

- Wählen Sie in der Menüleiste **analysieren** > **Berechnen der Codemetrik** > **für Projektmappe**.

- In **Projektmappen-Explorer**mit der rechten Maustaste auf die Projektmappe, und wählen Sie dann **Berechnen der Codemetrik**.

- In der **Codemetrikergebnisse** Fenster, wählen Sie die **Berechnen der Codemetrik für Projektmappe** Schaltfläche.

Die Ergebnisse werden generiert und die **Codemetrikergebnisse** Fenster wird angezeigt. Um die Ergebnisdetails anzuzeigen, erweitern Sie die Struktur in der **Hierarchie** Spalte.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generieren Sie Codemetrikergebnisse für ein oder mehrere Projekte

1. In **Projektmappen-Explorer**, wählen Sie ein oder mehrere Projekte.

1. Wählen Sie in der Menüleiste **analysieren** > **Berechnen der Codemetrik** > **für ausgewählte Projekte**.

Die Ergebnisse werden generiert und die **Codemetrikergebnisse** Fenster wird angezeigt. Um die Ergebnisdetails anzuzeigen, erweitern Sie die Struktur in der **Hierarchie**.

## <a name="command-line-code-metrics"></a>Befehlszeile Codemetrik

Generieren von Codemetrikdaten werden über die Befehlszeile für C# und Visual Basic-Projekten für .NET Framework, .NET Core und .NET Standard-apps. Die Code Metriken Befehlszeilentools wird aufgerufen, *Metrics.exe*.

Zum Abrufen der *Metrics.exe* ausführbare Datei an, Sie müssen [selbst generieren](#generate-the-executable). In naher Zukunft eine [veröffentlichte Version des *Metrics.exe* stehen](https://github.com/dotnet/roslyn-analyzers/issues/1756) Sie brauchen ihn selbst erstellen.

### <a name="generate-the-executable"></a>Die ausführbare Datei generieren

Um die ausführbare Datei zu generieren *Metrics.exe*, gehen Sie folgendermaßen vor:

1. Klonen der [Dotnet/Roslyn-Analyzers](https://github.com/dotnet/roslyn-analyzers) Repository.
2. Öffnen Sie Developer-Eingabeaufforderung für Visual Studio als Administrator an.
3. Ausgehend vom Stamm des der **Roslyn-Analyzers** Repository, führen Sie den folgenden Befehl: `Restore.cmd`
4. Wechseln Sie zum Verzeichnis *Src\Tools*.
5. Führen Sie den folgenden Befehl zum Erstellen der **Metrics.csproj** Projekt:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Eine ausführbare Datei namens *Metrics.exe* wird generiert, der *Artifacts\bin* Verzeichnis unter dem Stammverzeichnis des Repositorys.

   > [!TIP]
   > Erstellung *Metrics.exe* in [Legacymodus](#legacy-mode), führen Sie den folgenden Befehl:
   >
   > ```shell
   > msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
   > ```

### <a name="usage"></a>Verwendung

Auszuführende *Metrics.exe*, geben Sie ein Projekt oder Projektmappe und ein Ausgabe-XML-Datei als Argumente. Zum Beispiel:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

### <a name="output"></a>Output

Die generierte XML-Ausgabe hat das folgende Format:

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
                  <Method Name="void Program.Main(string[] args)" File="C:\Users\mavasani\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
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

### <a name="tool-differences"></a>Tool-Unterschiede

Frühere Versionen von Visual Studio, einschließlich Visual Studio 2015 enthalten ein Befehlszeilentool Metriken-Tool namens *Metrics.exe*. Diese frühere Version des Tools wurde eine binäre Analyse, d. h. eine Assembly-basierte Analyse. Das neue Tool analysiert Quellcode stattdessen an. Da die neue *Metrics.exe* basiert auf Source Code, die Ergebnisse unterscheiden, was von früheren Versionen von generierten *Metrics.exe* und innerhalb der Visual Studio 2017-IDE.

Die neue *Metrics.exe* Tool kann berechnen von Metriken auch bei der Quelle von Codefehlern, solange die Projektmappen- und Projektdateien geladen werden können.

#### <a name="metric-value-differences"></a>Metrikwert Unterschiede

Die `LinesOfCode` Metrik ist genauer und zuverlässiger, in der neuen *Metrics.exe*. Dabei handelt es sich unabhängig von Codegen Unterschiede nicht geändert werden, wenn das Toolset oder Laufzeit ändert. Die neue *Metrics.exe* zählt, tatsächliche Zeilen von Code, einschließlich Leerzeilen und Kommentare.

Andere Metriken wie z. B. `CyclomaticComplexity` und `MaintainabilityIndex` verwenden die gleichen Formeln wie in früheren Versionen von *Metrics.exe*, aber die neue *Metrics.exe* zählt die Anzahl der `IOperations` (logische Quelle Anweisungen) anstelle der Zwischensprache (IL)-Anweisungen. Die Zahlen unterscheiden sich geringfügig von früheren Versionen von *Metrics.exe* und von der Codemetrikergebnisse für Visual Studio 2017-IDE.

### <a name="legacy-mode"></a>Legacy-Modus

Sie können auch auswählen, um erstellen *Metrics.exe* in *Legacymodus*. Die legacy-Modus-Version des Tools generiert Metrikwerte, die näher an welche älteren Versionen des Tools generiert werden. Darüber hinaus im Legacymodus *Metrics.exe* Codemetrik generiert, der gleiche Satz von der Methode, vorherige Versionen von die Tool-erzeugte codemetriken für die Datentypen. Z. B. nicht es Codemetrikdaten für Feld "und"-Eigenschaft-Initialisierer generieren. Legacy-Modus eignet sich für Abwärtskompatibilität Kompatibilitäts- oder wenn Sie Code Einchecken Gates haben Codemetrik Zahlen basierend auf. Der Befehl zum Erstellen *Metrics.exe* im Legacymodus ist:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Weitere Informationen finden Sie unter [aktivieren, Generieren von Codemetrikdaten im Legacymodus](https://github.com/dotnet/roslyn-analyzers/pull/1841).

## <a name="see-also"></a>Siehe auch

- [Verwenden Sie das Fenster Codemetrikergebnisse](../code-quality/working-with-code-metrics-data.md)
- [Codemetrikwerte](../code-quality/code-metrics-values.md)
