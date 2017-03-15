---
title: "MSBuild Task Reference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, tasks"
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# MSBuild Task Reference
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aufgaben stellen den Code bereit, der während des Buildprozesses ausgeführt wird.  Die Aufgaben in der folgenden Liste sind in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] enthalten.  Wenn [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] installiert ist, sind zusätzliche Aufgaben zum Erstellen von [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-Projekten verfügbar.  Weitere Informationen finden Sie unter [Visual C\+\+ Tasks](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).  
  
 Zusätzlich zu den Parametern, die in den Themen in diesem Abschnitt aufgeführt werden, kann jede Aufgabe auch über die folgenden Parameter verfügen:  
  
|Parameter|Description|  
|---------------|-----------------|  
|`Condition`|Optionaler `String`\-Parameter.<br /><br /> Ein `Boolean`\-Ausdruck, mit dem vom [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Modul ermittelt wird, ob diese Aufgabe ausgeführt wird.  Weitere Informationen zu den Bedingungen, die von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] unterstützt werden, finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Optionaler \- Parameter.  Kann einen der folgenden Werte enthalten:<br /><br /> -   **WarnAndContinue** oder **true**.  Wenn eine Aufgabe fehlschlägt, werden folgende Aufgaben im [Ziel](../msbuild/target-element-msbuild.md)\-Element und im Build fort, um auszuführen, und alle Fehler von der Aufgabe werden als Warnungen behandelt.<br />-   **ErrorAndContinue**.  Wenn eine Aufgabe fehlschlägt, werden folgende Aufgaben im `Target`\-Element und im Build fort, um auszuführen, und alle Fehler von der Aufgabe werden als Fehler behandelt.<br />-   **ErrorAndStop** oder **false** \(Standard\).  Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im `Target`\-Element und im Build nicht ausgeführt, und das gesamte `Target`\-Element und der Build wird angenommen fehlgeschlagen sein.<br /><br /> .NET Framework\-Versionen vor 4,5 unterstützten nur die `true` und `false`\-Werte.<br /><br /> Weitere Informationen finden Sie unter [How to: Ignore Errors in Tasks](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## In diesem Abschnitt  
 [Task Base Class](../msbuild/task-base-class.md)  
 Fügt den Aufgaben, die sich von der <xref:Microsoft.Build.Utilities.Task>\-Klasse ableiten, mehrere Parameter hinzu.  
  
 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)  
 Fügt den Aufgaben, die sich von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse ableiten, mehrere Parameter hinzu.  
  
 [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)  
 Fügt den Aufgaben, die sich von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>\-Klasse ableiten, mehrere Parameter hinzu.  
  
 [AL \(Assembly Linker\) Task](../msbuild/al-assembly-linker-task.md)  
 Erstellt eine Assembly mit einem Manifest aus einer oder mehreren Dateien, bei denen es sich um Module oder Ressourcendateien handelt.  
  
 [AspNetCompiler Task](../msbuild/aspnetcompiler-task.md)  
 Umschließt aspnet\_compiler.exe, ein Dienstprogramm, mit dem ASP.NET\-Anwendungen vorkompiliert werden.  
  
 [AssignCulture Task](../msbuild/assignculture-task.md)  
 Weist Elementen Kulturbezeichner zu.  
  
 [AssignProjectConfiguration Task](../msbuild/assignprojectconfiguration-task.md)  
 Akzeptiert eine Liste von Konfigurationszeichenfolgen und weist sie angegebenen Projekten zu.  
  
 [AssignTargetPath Task](../msbuild/assigntargetpath-task.md)  
 Akzeptiert eine Liste von Dateien und fügt `<TargetPath>`\-Attribute hinzu, sofern sie noch nicht angegeben wurden.  
  
 [CallTarget Task](../msbuild/calltarget-task.md)  
 Ruft ein Ziel in der Projektdatei auf.  
  
 [CombinePath Task](../msbuild/combinepath-task.md)  
 Kombiniert die angegebenen Pfade in einem einzelnen Pfad.  
  
 [ConvertToAbsolutePath Task](../msbuild/converttoabsolutepath-task.md)  
 Konvertiert einen relativen Pfad oder einen Verweis in einen absoluten Pfad.  
  
 [Copy Task](../msbuild/copy-task.md)  
 Kopiert Dateien an einen neuen Speicherort.  
  
 [CreateCSharpManifestResourceName Task](../msbuild/createcsharpmanifestresourcename-task.md)  
 Erstellt einen Manifestnamen im [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Format auf der Grundlage eines bestimmten RESX\-Dateinamens oder einer anderen Ressource.  
  
 [CreateItem Task](../msbuild/createitem-task.md)  
 Füllt Elementauflistungen aus den Eingabeelementen auf, sodass Elemente aus einer Liste in eine andere kopiert werden können.  
  
 [CreateProperty Task](../msbuild/createproperty-task.md)  
 Füllt Eigenschaften aus den Eingabewerten auf. Auf diese Weise können Werte von einer Eigenschaft oder Zeichenfolge in eine andere kopiert werden.  
  
 [CreateVisualBasicManifestResourceName Task](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 Erstellt einen Manifestnamen im [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Format auf der Grundlage eines bestimmten RESX\-Dateinamens oder einer anderen Ressource.  
  
 [Csc Task](../msbuild/csc-task.md)  
 Ruft den Visual C\#\-Compiler auf, um ausführbare Dateien, Dynamic Link Librarys oder Codemodule zu erzeugen.  
  
 [Delete Task](../msbuild/delete-task.md)  
 Löscht die angegebenen Dateien.  
  
 [Error Task](../msbuild/error-task.md)  
 Hält einen Build an und protokolliert einen Fehler anhand einer ausgewerteten Bedingungsanweisung.  
  
 [Exec Task](../msbuild/exec-task.md)  
 Führt das angegebene Programm oder den angegebenen Befehl mit den angegebenen Argumenten aus.  
  
 [FindAppConfigFile Task](../msbuild/findappconfigfile-task.md)  
 Sucht in den angegebenen Listen die Datei app.config, sofern vorhanden.  
  
 [FindInList Task](../msbuild/findinlist-task.md)  
 Sucht ein Element in einer angegebenen Liste, das über eine entsprechende Elementspezifikation verfügt.  
  
 [FindUnderPath Task](../msbuild/findunderpath-task.md)  
 Ermittelt, welche Elemente in der angegebenen Elementauflistung im angegebenen Ordner und allen Unterordnern vorhanden sind.  
  
 [FormatUrl Task](../msbuild/formaturl-task.md)  
 Konvertiert eine URL in ein richtiges URL\-Format.  
  
 [FormatVersion Task](../msbuild/formatversion-task.md)  
 Fügt die Revisionsnummer an die Versionsnummer an.  
  
 [GenerateApplicationManifest Task](../msbuild/generateapplicationmanifest-task.md)  
 Generiert ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsmanifest oder ein systemeigenes Manifest.  
  
 [GenerateBootstrapper Task](../msbuild/generatebootstrapper-task.md)  
 Bietet eine Möglichkeit zur Automatisierung von Erkennung, Download und Installation einer Anwendung und der erforderlichen Komponenten.  
  
 [GenerateDeploymentManifest Task](../msbuild/generatedeploymentmanifest-task.md)  
 Generiert ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsmanifest.  
  
 [GenerateResource Task](../msbuild/generateresource-task.md)  
 Konvertiert TXT\-Dateien und RESX\-Dateien in binäre RESOURCES\-Dateien der Common Language Runtime.  
  
 [GenerateTrustInfo Task](../msbuild/generatetrustinfo-task.md)  
 Generiert die Vertrauenswürdigkeit der Anwendung aus dem Basismanifest sowie aus der `TargetZone`\-Eigenschaft und den `ExcludedPermissions`\-Parametern.  
  
 [GetAssemblyIdentity Task](../msbuild/getassemblyidentity-task.md)  
 Ruft die Assemblyidentitäten aus den angegebenen Dateien ab und gibt die Identitätsinformationen aus.  
  
 [GetFrameworkPath Task](../msbuild/getframeworkpath-task.md)  
 Ruft den Pfad zu den [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Assemblys ab.  
  
 [GetFrameworkSdkPath Task](../msbuild/getframeworksdkpath-task.md)  
 Ruft den Pfad zu [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] ab.  
  
 [GetReferenceAssemblyPaths Task](../msbuild/getreferenceassemblypaths-task.md)  
 Gibt die Verweisassemblypfade der verschiedenen Frameworks zurück.  
  
 [LC Task](../msbuild/lc-task.md)  
 Generiert eine LICENSE\-Datei aus einer LICX\-Datei.  
  
 [MakeDir Task](../msbuild/makedir-task.md)  
 Erstellt Verzeichnisse und ggf. übergeordnete Verzeichnisse.  
  
 [Message Task](../msbuild/message-task.md)  
 Protokolliert eine Meldung während eines Builds.  
  
 [Move Task](../msbuild/move-task.md)  
 Verschiebt Dateien an eine neue Position.  
  
 [MSBuild\-Aufgabe](../msbuild/msbuild-task.md)  
 Erstellt [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projekte aus einem anderen [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projekt.  
  
 [ReadLinesFromFile Task](../msbuild/readlinesfromfile-task.md)  
 Liest eine Liste von Elementen aus einer Textdatei.  
  
 [RegisterAssembly Task](../msbuild/registerassembly-task.md)  
 Liest die Metadaten in der angegebenen Assembly und fügt der Registrierung die notwendigen Einträge hinzu.  
  
 [RemoveDir Task](../msbuild/removedir-task.md)  
 Entfernt die angegebenen Verzeichnisse und alle enthaltenen Dateien und Unterverzeichnisse.  
  
 [RemoveDuplicates Task](../msbuild/removeduplicates-task.md)  
 Entfernt doppelte Elemente aus der angegebenen Elementauflistung.  
  
 [RequiresFramework35SP1Assembly Task](../msbuild/requiresframework35sp1assembly-task.md)  
 Bestimmt, ob die Anwendung .NET Framework 3.5 SP1 erfordert.  
  
 ResGen\-Aufgabe  
 Veraltet.  Verwenden Sie die [GenerateResource Task](../msbuild/generateresource-task.md)\-Aufgabe, um TXT\-Dateien und RESX\-Dateien in binäre RESOURCES\-Dateien der Common Language Runtime und zurück in TXT\-Dateien bzw. RESX\-Dateien zu konvertieren.  
  
 [ResolveAssemblyReference Task](../msbuild/resolveassemblyreference-task.md)  
 Bestimmt alle Assemblys, die von den angegebenen Assemblys abhängen.  
  
 [ResolveComReference Task](../msbuild/resolvecomreference-task.md)  
 Erstellt eine Liste mit mindestens einem Typbibliotheknamen oder mindestens einer TLB\-Datei und löst die Typbibliotheken in Speicherorten auf dem Datenträger auf.  
  
 [ResolveKeySource Task](../msbuild/resolvekeysource-task.md)  
 Ermittelt die Quelle für Schlüssel für einen starken Namen.  
  
 [ResolveManifestFiles Task](../msbuild/resolvemanifestfiles-task.md)  
 Löst die folgenden Elemente im Buildprozess in Dateien für die Manifestgenerierung auf: erstellte Elemente, Abhängigkeiten, Satelliten, Inhalte, Debugsymbole und Dokumentation.  
  
 [ResolveNativeReference Task](../msbuild/resolvenativereference-task.md)  
 Löst systemeigene Verweise auf.  
  
 [ResolveNonMSBuildProjectOutput Task](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 Bestimmt die Ausgabedateien für Projektverweise, die keine MSBuild\-Projektverweise sind.  
  
 [SGen Task](../msbuild/sgen-task.md)  
 Erstellt eine XML\-Serialisierungsassembly für Typen in der angegebenen Assembly.  
  
 [SignFile Task](../msbuild/signfile-task.md)  
 Signiert die angegebene Datei mit dem angegebenen Zertifikat.  
  
 [Touch Task](../msbuild/touch-task.md)  
 Legt die Zugriffs\- und die Änderungszeiten für Dateien fest.  
  
 [UnregisterAssembly Task](../msbuild/unregisterassembly-task.md)  
 Hebt die Registrierung der angegebenen Assemblys für COM\-Interop\-Zwecke auf.  
  
 [UpdateManifest Task](../msbuild/updatemanifest-task.md)  
 Aktualisiert ausgewählte Eigenschaften in einem Manifest und führt eine erneute Signierung aus.  
  
 [Vbc Task](../msbuild/vbc-task.md)  
 Ruft den Visual Basic\-Compiler auf, um ausführbare Dateien, Dynamic Link Librarys oder Codemodule zu erzeugen.  
  
 [Warning Task](../msbuild/warning-task.md)  
 Protokolliert eine Warnung während eines Buildvorgangs auf der Grundlage einer ausgewerteten Bedingungsanweisung.  
  
 [WriteCodeFragment Task](../msbuild/writecodefragment-task.md)  
 Generiert eine temporäre Codedatei mit dem angegebenen generierten Codefragment.  Löscht die Datei nicht.  
  
 [WriteLinesToFile Task](../msbuild/writelinestofile-task.md)  
 Schreibt die angegebenen Elemente in die angegebene Textdatei.  
  
 [XmlPeek Task](../msbuild/xmlpeek-task.md)  
 Gibt Werte wie von einer XPath\-Abfrage angegeben aus einer XML\-Datei zurück.  
  
 [XmlPoke Task](../msbuild/xmlpoke-task.md)  
 Legt Werte wie von einer XPath\-Abfrage angegeben in einer XML\-Datei fest.  
  
 [XslTransformation Task](../msbuild/xsltransformation-task.md)  
 Transformiert eine XML\-Eingabe mithilfe einer *Extensible Stylesheet Language Transformation* \(XSLT\) oder kompilierten XSLT und gibt das Ergebnis in einem Ausgabegerät oder einer Datei aus.  
  
## Siehe auch  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Writing](../msbuild/task-writing.md)   
 [Tasks](../msbuild/msbuild-tasks.md)