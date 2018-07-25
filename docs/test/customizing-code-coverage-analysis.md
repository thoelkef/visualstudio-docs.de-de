---
title: Anpassen der Code Coverage-Analyse in Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7b48fc77dd88cf327050c0bf8ba893f8d4a626fa
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303002"
---
# <a name="customize-code-coverage-analysis"></a>Anpassen der Code Coverage-Analyse

Standardmäßig werden bei der Code Coverage-Analyse alle Projektmappenassemblys analysiert, die während der Komponententests geladen werden. Es wird empfohlen, dieses Standardverhalten beizubehalten, da es meist gut funktioniert. Weitere Informationen finden Sie unter [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Fügen Sie das Attribut <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> zu Ihrer Testklasse hinzu, um Testcode aus den Code Coverage-Ergebnissen auszuschließen und nur Anwendungscode einzuschließen.

Rufen Sie die *PDB*-Dateien für diese Assemblys ab, und kopieren Sie sie in den gleichen Ordner wie die *DLL*-Assemblydateien, um Assemblys einzuschließen, die nicht Teil Ihrer Projektmappe sind.

## <a name="run-settings-file"></a>Testlaufeinstellungsdatei

Die [Testlaufeinstellungsdatei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) ist die Konfigurationsdatei, die von den Tools für Komponententests verwendet wird. Erweiterte Code Coverage-Einstellungen werden in einer *RUNSETTINGS*-Datei angegeben.

Führen Sie die folgenden Schritte aus, um Code Coverage anzupassen:

1. Fügen Sie eine Testlaufeinstellungsdatei zu Ihrer Projektmappe hinzu. Wählen sie im **Projektmappen-Explorer** im Kontextmenü Ihrer Projektmappe die Option **Hinzufügen** > **Neues Element** und **XML-Datei** aus. Speichern Sie die Datei mit einem Namen wie z.B. *CodeCoverage.runsettings*.

1. Fügen Sie den Inhalt der Beispieldatei am Ende dieses Artikels hinzu, und passen Sie diesen anschließend wie in den folgenden Abschnitten beschrieben an Ihre Anforderungen an.

1. Wählen Sie im Menü **Test** die Option **Testeinstellungen** > **Datei für Testeinstellungen auswählen** aus, um die Testeinstellungsdatei auszuwählen. Informationen zur Angabe einer Testlaufeinstellungsdatei für die Ausführung von Tests über die Befehlszeile oder in einem Buildworkflow finden Sie unter [Konfigurieren von Komponententests mit einer *RUNSETTINGS*-Datei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file).

   Wenn Sie **Code Coverage analysieren** auswählen, werden die Konfigurationsinformationen aus der Testlaufeinstellungsdatei gelesen.

   > [!TIP]
   > Die vorherigen Code Coverage-Ergebnisse und Codefarben werden nicht automatisch ausgeblendet, wenn Sie Tests ausführen oder Ihren Code aktualisieren.

Um die benutzerdefinierten Einstellungen ein- und auszuschalten, deaktivieren oder aktivieren Sie die Datei im Menü **Test** > **Testeinstellungen**.

![Testeinstellungsmenü mit benutzerdefinierter Einstellungsdatei](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>Angeben von Symbolsuchpfaden

Für die Code Coverage sind Symboldateien (*PDB*-Dateien) für Assemblys erforderlich. Für über die Projektmappe erstellte Assemblys werden Symboldateien meistens neben den Binärdateien bereitgestellt, und die Code Coverage funktioniert automatisch. In einigen Fällen sollten Sie jedoch Assemblys, auf die verwiesen wird, in die Codeabdeckungsanalyse einschließen. In solchen Fällen befinden sich die *PDB*-Dateien möglicherweise nicht neben den Binärdateien. Sie können jedoch den Symbolsuchpfad in der *RUNSETTINGS*-Datei angeben.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Die Symbolauflösung kann zeitaufwendig sein, insbesondere wenn sie einen Remotedateispeicherort mit zahlreichen Assemblys verwendet. Daher sollten Sie in Erwägung ziehen, die *PDB*-Dateien in denselben lokalen Speicherort zu kopieren wie die Binärdateien (*DLL* und *EXE*).

### <a name="exclude-and-include"></a>„Include“ und „Exclude“

Sie können angegebene Assemblys von der Codeabdeckungsanalyse ausschließen. Zum Beispiel:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Alternativ können Sie angeben, welche Assemblys enthalten sein sollen. Dieser Ansatz hat den Nachteil, dass Sie beim Hinzufügen von weiteren Assemblys zur Projektmappe daran denken müssen, diese der Liste hinzuzufügen:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Wenn **Include** leer ist, enthält die Verarbeitung der Code Coverage alle Assemblys, die geladen wurden und für die *PDB*-Dateien gefunden werden können. Die Code Coverage enthält keine Elemente, die mit einer Klausel in einer **Exclude**-Liste übereinstimmen.

**Include** wird vor **Exclude** verarbeitet.

### <a name="regular-expressions"></a>Reguläre Ausdrücke

In den Knoten "include" und "exclude" werden reguläre Ausdrücke verwendet. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Reguläre Ausdrücke sind nicht mit Platzhaltern identisch. Insbesondere:

- **.\*** entspricht einer Zeichenfolge beliebiger Zeichen

- **\\.** entspricht einem Punkt „.“

- **\\(   \\)** entspricht Klammern „(  )“

- **\\\\** entspricht dem Dateipfadtrennzeichen „\\“

- **^** entspricht dem Anfang der Zeichenfolge

- **$** entspricht dem Ende der Zeichenfolge

Bei allen Entsprechungen wird die Groß-/Kleinschreibung nicht beachtet.

Zum Beispiel:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

> [!WARNING]
> Wenn ein Fehler in einem regulären Ausdruck auftritt, z.B. eine Klammer ohne Escapezeichen oder Übereinstimmung, wird die Code Coverage-Analyse nicht ausgeführt.

### <a name="other-ways-to-include-or-exclude-elements"></a>Andere Möglichkeiten zum Einschließen oder Ausschließen von Elementen

- **ModulePath**: gleicht vom Assemblydateipfad angegebene Assemblys ab.

- **CompanyName**: gleicht Assemblys nach dem **Company**-Attribut ab.

- **PublicKeyToken**: gleicht signierte Assemblys nach dem öffentlichen Schlüsseltoken ab.

- **Source**: gleicht Elemente nach dem Pfadnamen der Quelldatei ab, in der sie definiert sind.

- **Attribute**: gleicht Elemente ab, an die ein bestimmtes Attribut angefügt ist. Geben Sie den vollständigen Namen des Attributs ein, und schließen Sie „Attribut“ am Ende des Namens ein.

- **Function**: gleicht Prozeduren, Funktionen oder Methoden nach dem vollqualifizierten Namen ab. Für den Abgleich mit einem Funktionsnamen muss der reguläre Ausdruck mit dem vollqualifizierten Namen der Funktion, einschließlich Namespace, Klassenname, Methodenname und Parameterliste, übereinstimmen. Zum Beispiel:

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

   ```xml
   <Functions>
     <Include>
       <!-- Include methods in the Fabrikam namespace: -->
       <Function>^Fabrikam\..*</Function>
       <!-- Include all methods named EqualTo: -->
       <Function>.*\.EqualTo\(.*</Function>
     </Include>
     <Exclude>
       <!-- Exclude methods in a class or namespace named UnitTest: -->
       <Function>.*\.UnitTest\..*</Function>
     </Exclude>
   </Functions>
   ```

## <a name="sample-runsettings-file"></a>Beispiel für eine RUNSETTINGS-Datei

Kopieren Sie diesen Code, und passen Sie ihn Ihren Anforderungen entsprechend an.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See http://msdn.microsoft.com/library/2k3te2cs.aspx.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Siehe auch

- [Konfigurieren von Komponententests mithilfe einer Testlaufeinstellungsdatei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)