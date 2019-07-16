---
title: Anpassen der Code Coverage-Analyse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f6337c35-acae-4c5f-b5d9-ac5ff687ef18
caps.latest.revision: 18
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 15093cc6af6e61384c393b1c3e435df3840a2811
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686438"
---
# <a name="customizing-code-coverage-analysis"></a>Anpassen der Code Coverage-Analyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Standardmäßig analysiert das Code Coverage-Tool von Visual Studio alle Projektmappenassemblys („.exe“ oder „.dl“l), die während der Komponententests geladen werden. Es wird empfohlen, diese Standardeinstellung beizubehalten, da sie meist gut funktioniert. Weitere Informationen finden Sie unter [Using Code Coverage to Determine How Much Code is being Tested (Wie Sie feststellen können, wie viel Code untersucht wird)](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Bevor Sie das Code Coverage-Verhalten anpassen, berücksichtigen Sie einige Alternativen:  
  
- *Ich möchte den Testcode aus den Code Coverage-Ergebnissen ausschließen und nur den Anwendungscode einbinden.*  
  
   Fügen Sie Ihrer Testklasse `ExcludeFromCodeCoverage Attribute` hinzu.  
  
- *Ich möchte die Assemblys einschließen, die nicht Teil meiner Projektmappe sind.*  
  
   Rufen Sie die PDB-Dateien für diese Assemblys ab, und kopieren Sie sie in den gleichen Ordner wie die Assemblydateien (DLL-Dateien).  
  
  Um das Code Coverage-Verhalten anzupassen, kopieren Sie das [Beispiel am Ende dieses Themas](#sample), und fügen Sie es der Projektmappe mit der Dateierweiterung „.runsettings“ hinzu. Bearbeiten Sie das Beispiel Ihren eigenen Anforderungen entsprechend, und klicken Sie dann im Menü **Test** auf **Testeinstellungen** und auf **Datei für Testeinstellungen auswählen**. Im verbleibenden Teil dieses Themas werden diese Schritte ausführlicher beschrieben.  
  
## <a name="the-runsettings-file"></a>RUNSETTINGS-Datei  
 Erweiterte Codeabdeckungseinstellungen werden in einer RUNSETTINGS-Datei angegeben. Dies ist die Konfigurationsdatei, die von den Tools für Unittests verwendet wird. Es wird empfohlen, das [Beispiel am Ende dieses Themas](#sample) zu kopieren und es an Ihre eigenen Anforderungen anzupassen.  
  
- *Was ist mit der TESTSETTINGS-Datei geschehen, die in Visual Studio 2010 verwendet wurde?*  
  
   In Visual Studio 2010 wird die TESTSETTINGS-Datei nur auf Komponententests angewendet, die auf dem MSTest-Framework basieren. In Visual Studio 2012 können die Testtools nicht nur auf MSTest, sondern auch auf andere Frameworks wie NUnit und xUnit.net angewendet werden. Die TESTSETTINGS-Datei funktioniert nicht mit diesen Frameworks. Die RUNSETTINGS-Datei wurde entwickelt, um die Testtools so anzupassen, dass sie in allen Testframeworks funktionieren.  
  
  Zur Anpassung der Code Coverage müssen Sie Ihrer Projektmappe eine RUNSETTINGS-Datei hinzufügen:  
  
1. Fügen Sie eine XML-Datei als Projektmappenelement mit der Erweiterung `.runsettings` hinzu:  
  
    Wählen Sie im Projektmappen-Explorer im Kontextmenü der Projektmappe die Option **Hinzufügen**, **Neues Element** und **XML-Datei** aus. Speichern der Datei mit einer Namensendung wie z.B. `CodeCoverage.runsettings`  
  
2. Fügen Sie den Inhalt hinzu, der im Beispiel am Ende dieses Themas enthalten ist, und passen Sie diesen dann, wie in den folgenden Abschnitten beschrieben, an Ihre Anforderungen an.  
  
3. Klicken Sie im Menü **Test** auf **Testeinstellungen**, **Datei für Testeinstellungen auswählen**, und wählen Sie dann die Datei aus.  
  
4. Wenn Sie jetzt **Code Coverage analysieren** ausführen, steuert die `.runsettings`-Datei das Verhalten. Vergessen Sie nicht, dass Sie die Code Coverage erneut ausführen müssen: Die vorherigen Abdeckungsergebnisse und Codefarben werden nicht automatisch ausgeblendet, wenn Sie Tests ausführen oder den Code aktualisieren.  
  
5. Um die benutzerdefinierten Einstellungen ein- und auszuschalten, deaktivieren oder aktivieren Sie die Datei im Menü **Test**, **Testeinstellungen**.  
  
   ![Testeinstellungsmenü mit benutzerdefinierter Einstellungsdatei](../test/media/codecoverage-settingsfile.png "CodeCoverage-settingsFile")  
  
   Andere Aspekte von Komponententests können in derselben RUNSETTINGS-Datei konfiguriert werden. Weitere Informationen finden Sie unter [Komponententests des Codes](../test/unit-test-your-code.md).  
  
### <a name="specifying-symbol-search-paths"></a>Festlegen von Symbolsuchpfaden  
 Die Codeabdeckung erfordert Symbole (PDB-Dateien), damit Assemblys zur Verfügung stehen. Für über die Projektmappe erstellte Assemblys werden Symboldateien im Allgemeinen neben den Binärdateien bereitgestellt, und die Codeabdeckung funktioniert automatisch. In einigen Fällen sollten Sie jedoch Assemblys, auf die verwiesen wird, in die Codeabdeckungsanalyse einschließen. In solchen Fällen befinden sich die PDB-Dateien nicht neben den Binärdateien. Sie können jedoch den Symbolsuchpfad in der RUNSETTINGS-Datei angeben.  
  
```xml  
<SymbolSearchPaths>                
      <Path>\\mybuildshare\builds\ProjectX</Path>  
      <!--More paths if required-->  
</SymbolSearchPaths>  
  
```  
  
> [!WARNING]
> Die Symbolauflösung kann zeitaufwendig sein, insbesondere wenn sie einen Remotedateispeicherort mit zahlreichen Assemblys verwendet. Daher sollten Sie erwägen, die Remote-PDB-Dateien an denselben lokalen Speicherort wie die Binärdateien (DLL- und EXE-Dateien) zu kopieren.  
  
### <a name="excluding-and-including"></a>Ausschließen und Einschließen  
 Sie können angegebene Assemblys von der Codeabdeckungsanalyse ausschließen. Zum Beispiel:  
  
```minterastlib  
<ModulePaths>  
  <Exclude>  
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>  
   <!-- Add more ModulePath nodes here. -->  
  </Exclude>  
</ModulePaths>  
```  
  
 Alternativ können Sie angeben, welche Assemblys enthalten sein sollen. Dieser Ansatz hat den Nachteil, dass Sie beim Hinzufügen von weiteren Assemblys zur Projektmappe daran denken müssen, diese der Liste hinzuzufügen:  
  
```minterastlib  
<ModulePaths>  
  <Include>  
   <ModulePath>Fabrikam.Math.dll</ModulePath>  
   <!-- Add more ModulePath nodes here. -->  
  </Include>  
</ModulePaths>  
```  
  
 Wenn `<Include>` leer ist, enthält die Verarbeitung der Code Coverage alle Assemblys (DLL- und EXE-Dateien), die geladen wurden und für die **PDB**-Dateien gefunden werden können, ausgenommen der Elemente, die mit einer Klausel in der `<Exclude>`-Liste übereinstimmen.  
  
 `Include` wird vor `Exclude` verarbeitet.  
  
### <a name="regular-expressions"></a>Reguläre Ausdrücke  
 In den Knoten "include" und "exclude" werden reguläre Ausdrücke verwendet. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Reguläre Ausdrücke sind nicht identisch mit Platzhaltern. Insbesondere:  
  
1. **\.\\** * entspricht einer Zeichenfolge beliebiger Zeichen  
  
2. **\\.** entspricht einem Punkt „.“  
  
3. **\\(   \\)** entspricht Klammern „(  )“  
  
4. **\\\\** entspricht dem Dateipfadtrennzeichen „\\“  
  
5. **^** entspricht dem Anfang der Zeichenfolge  
  
6. **$** entspricht dem Ende der Zeichenfolge  
  
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
> Wenn ein Fehler in einem regulären Ausdruck auftritt, z. B. eine Klammer ohne Escapezeichen und Übereinstimmung, wird die Codeabdeckungsanalyse nicht ausgeführt.  
  
### <a name="other-ways-to-include-or-exclude-elements"></a>Andere Möglichkeiten zum Einschließen oder Ausschließen von Elementen  
 Ein Codebeispiel finden Sie [am Ende dieses Themas](#sample).  
  
- `ModulePath` – Assemblys, die durch den Assemblydateipfad angegeben werden.  
  
- `CompanyName` – gleicht Assemblys nach dem Unternehmensattribut ab.  
  
- `PublicKeyToken` - gleicht signierte Assemblys nach dem öffentlichen Schlüsseltoken ab. Verwenden Sie beispielsweise `<PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>`, um alle Visual Studio-Komponenten und -Erweiterungen abzugleichen.  
  
- `Source` – gleicht Elemente nach dem Pfadnamen der Quelldatei ab, in der sie definiert sind.  
  
- `Attribute` – gleicht Elemente ab, an die ein bestimmtes Attribut angefügt ist. Geben Sie den vollständigen Namen des Attributs, einschließlich "Attribut", am Ende des Namens an.  
  
- `Function` – gleicht Prozeduren, Funktionen oder Methoden nach dem vollqualifizierten Namen ab.  
  
  **Abgleichen eines Funktionsnamens**  
  
  Der reguläre Ausdruck muss mit dem vollqualifizierten Namen der Funktion, einschließlich Namespace, Klasse, Methodenname und Parameterliste, übereinstimmen. Ein auf ein Objekt angewendeter  
  
- C# oder Visual Basic: `Fabrikam.Math.LocalMath.SquareRoot(double)`  
  
- C++: `Fabrikam::Math::LocalMath::SquareRoot(double)`  
  
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
  
## <a name="how-to-specify-runsettings-files-while-running-tests"></a>So geben Sie RUNSETTINGS-Dateien beim Ausführen von Tests an  
  
### <a name="to-customize-runsettings-in-visual-studio-tests"></a>So passen Sie die RUNSETTINGS-Datei in Visual Studio-Tests an  
 Klicken Sie auf **Test**, **Testeinstellungen**, **Datei für Testeinstellungen auswählen**, und wählen Sie die RUNSETTINGS-Datei aus. Die Datei erscheint im Menü "Testeinstellungen", und Sie können sie auswählen oder abbrechen. Wenn die RUNSETTINGS-Datei ausgewählt ist, wird sie bei jeder Ausführung von **Code Coverage analysieren** angewendet.  
  
### <a name="to-customize-run-settings-in-a-command-line-test"></a>So passen Sie Laufzeiteinstellungen in einem Befehlszeilentest an  
 Um Tests über die Befehlszeile auszuführen, verwenden Sie "vstest.console.exe". Die Einstellungsdatei ist ein Parameter dieses Hilfsprogramms. Weitere Informationen finden Sie unter [Verwenden von VSTest.console über die Befehlszeile](https://msdn.microsoft.com/library/852812d8-b3bb-407e-bc43-04d511fcb27a).  
  
1. Starten der Visual Studio Developer-Eingabeaufforderung:  
  
     Klicken Sie im Windows-Menü **Start** auf **Alle Programme**, **Microsoft Visual Studio**, **Visual Studio-Tools** und **Developer-Eingabeaufforderung**.  
  
2. Führen Sie Folgendes aus:  
  
     `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings`  
  
### <a name="to-customize-run-settings-in-a-build-definition"></a>So passen Sie Testlaufeinstellungen in einer Builddefinition an  
 Sie können die Code Coverage-Daten von einem Teambuild abrufen.  
  
 ![Festlegen von Testlaufeinstellungen in einer Builddefinition](../test/media/codecoverage-buildrunsettings.png "CodeCoverage-buildRunsettings")  
  
1. Vergewissern Sie sich, dass die RUNSETTINGS-Datei eingecheckt ist.  
  
2. Öffnen Sie im Team Explorer **Builds**, und fügen Sie dann eine Builddefinition hinzu oder bearbeiten Sie diese.  
  
3. Erweitern Sie auf der Seite **Prozess** die Elemente **Automatisierte Tests**, **Testquelle** und **Testlaufeinstellungen**. Wählen Sie die **RUNSETTINGS**-Datei aus.  
  
   - <em>Es wird jedoch die **Testassembly</em>* anstelle der **Testquelle** angezeigt. Beim Versuch, das Feld **Laufzeiteinstellungen** festzulegen, kann ich nur TESTSETTINGS-Dateien auswählen.*  
  
      Wählen Sie unter **Automatisierte Tests** die Option **Testassembly** aus, und klicken Sie am Ende der Zeile auf **[...]** . Setzen Sie im Dialogfeld **Testlauf hinzufügen/bearbeiten** den **Test Runner** auf **Visual Studio Test Runner**.  
  
   Die Ergebnisse sind im zusammenfassenden Abschnitt des Buildberichts sichtbar.  
  
## <a name="sample"></a> Beispiel für eine RUNSETTINGS-Datei:  
 Kopieren Sie diesen Code, und passen Sie ihn Ihren Anforderungen entsprechend an. Dies ist die standardmäßige RUNSETTINGS-Datei.  
  
 (Informationen zu anderen Verwendungsmöglichkeiten der RUNSETTINGS-Datei, finden Sie unter [Konfigurieren von Komponententests mithilfe einer .runsettings-Datei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).)  
  
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
Each element in the list is a regular expression (ECMAScript syntax). See https://msdn.microsoft.com/library/2k3te2cs.aspx.  
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
                <!—Don't forget "Attribute" at the end of the name -->  
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
 [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)   
 [Komponententest für Code](../test/unit-test-your-code.md)
