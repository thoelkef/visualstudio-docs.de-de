---
title: MIDL-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), MIDL task
- MIDL task (MSBuild (Visual C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d0398217bb48786067f8392c5e372b0888d060f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782474"
---
# <a name="midl-task"></a>MIDL-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Umschließt das MIDL (Microsoft Interface Definition Language)-Compilertool („midl.exe“). Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **MIDL**-Aufgabe beschrieben. Die meisten Aufgabenparameter und einige Parametersätze entsprechen einer Befehlszeilenoption.  
  
-   **AdditionalIncludeDirectories**  
  
     Optionaler **String[]**-Parameter.  
  
     Fügt ein Verzeichnis zur Liste der Verzeichnisse hinzu, die auf importierte IDL-Dateien durchsucht werden, einschließlich Headerdateien und Anwendungskonfigurationsdateien (ACF).  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/I**.  
  
-   **AdditionalOptions**  
  
     Optionaler **String**-Parameter.  
  
     Eine Liste der Befehlszeilenoptionen. Zum Beispiel **„**_/option1 /option2 /option#_“. Verwenden Sie diesen Parameter, um Befehlszeilenoptionen anzugeben, die nicht durch einen anderen MIDL-Aufgabenparameter repräsentiert werden.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“.  
  
-   **ApplicationConfigurationMode**  
  
     Optionaler **Boolean**-Parameter.  
  
     Wenn `true`, dann können Sie einige ACF-Schlüsselwörter in der IDL-Datei benutzen.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/app_config**.  
  
-   **ClientStubFile**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Namen der Client-Stub-Datei für eine RPC-Schnittstelle an.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/cstub**. Siehe auch den Parameter **ServerStubFile** in dieser Tabelle.  
  
-   **CPreprocessOptions**  
  
     Optionaler **String**-Parameter.  
  
     Gibt Optionen für die Übergabe an den C++-Präprozessor an. Geben eine durch Leerzeichen getrennte Liste mit Präprozessoroptionen an.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/cpp_opt**.  
  
-   **DefaultCharType**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den standardmäßigen Zeichentyp an, den der C-Compiler verwendet, um den generierten Code zu kompilieren.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**Signed**|**/char signed**|  
    |**Unsigned**|**/char unsigned**|  
    |**Ascii**|**/char ascii7**|  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/char**.  
  
-   **DllDataFileName**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Dateinamen für die generierte *dlldata*-Datei für eine Proxy-DLL an.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/dlldata**.  
  
-   **EnableErrorChecks**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Fehlertyp an, und überprüft, dass die generierten Stubs in der Laufzeit ausgeführt werden.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**Keine**|**/error none**|  
    |**EnableCustom**|**/error**|  
    |**All**|**/error all**|  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/error**.  
  
-   **ErrorCheckAllocations**  
  
     Optionaler **Boolean**-Parameter.  
  
     Wenn `true`, stellen Sie sicher, das keine Fehler aufgrund von unzureichendem Arbeitsspeicher aufgetreten sind.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/error allocation**.  
  
-   **ErrorCheckBounds**  
  
     Optionaler **Boolean**-Parameter.  
  
     Wenn `true`, dann wird die Größe der konform-variierenden und variierenden Arrays mit der Übertragungslängenspezifikation abgeglichen.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/error bounds_check**.  
  
-   **ErrorCheckEnumRange**  
  
     Optionaler **Boolean**-Parameter.  
  
     Wenn `true`, wird überprüft, ob sich die Enumerationswerte im zulässigen Bereich befinden.  
  
     Weitere Informationen finden Sie auf der Seite „Befehlszeilenhilfe“ (**/?**) für midl.exe unter der Option **error-Enumeration**.  
  
-   **ErrorCheckRefPointers**  
  
     Optionaler **Boolean**-Parameter.  
  
     Wenn `true`, stellen Sie sicher, dass keine NULL-Verweiszeiger an die Client-Stubs übergeben werden.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/error ref**.  
  
-   **ErrorCheckStubData**  
  
     Optionaler **Boolean**-Parameter.  
  
     Wenn `true`, wird ein Stub generiert, das Unmarshalling-Ausnahmen auf Serverseite erkennt, und überträgt sie zurück an den Client.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/error stub_data**.  
  
-   **GenerateClientFiles**  
  
     Optionaler **String**-Parameter.  
  
     Legt fest, ob der Compiler clientseitige C-Quelldateien für eine RPC-Schnittstelle generiert.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**Keine**|**/client none**|  
    |**Stub**|**/client stub**|  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/client**.  
  
-   **GenerateServerFiles**  
  
     Optionaler **String**-Parameter.  
  
     Legt fest, ob der Compiler serverseitige C-Quelldateien für eine RPC-Schnittstelle generiert.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**Keine**|**/server none**|  
    |**Stub**|**/server stub**|  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/server**.  
  
-   **GenerateStublessProxies**  
  
     Optionaler **Boolean**-Parameter.  
  
     Wenn `true`, werden vollständig interpretierte Stubs mit Proxys ohne Stubs für Objektschnittstellen generiert.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/Oicf**.  
  
-   **GenerateTypeLibrary**  
  
     Optionaler **Boolean**-Parameter.  
  
     Wenn `true`, dann wird keine Typbibliotheksdatei (.tlb) generiert.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/notlb**.  
  
-   **HeaderFileName**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Namen der generierten Headerdatei an.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter den Optionen **/h** und **/header**.  
  
-   **IgnoreStandardIncludePath**  
  
     Optionaler **Boolean**-Parameter.  
  
     Wenn `true`, dann sucht die MIDL-Aufgabe nur in den angegebenen Verzeichnissen mithilfe des Schalters **AdditonalIncludeDirectories**, und ignoriert das aktuelle Verzeichnis und die durch die Umgebungsvariable „INCLUDE“ angegebenen Verzeichnisse.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/no_def_idir**.  
  
-   **InterfaceIdentifierFileName**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Namen für die *Schnittstellen-Bezeichnerdatei* für die COM-Schnittstelle an. Dies setzt den Standardnamen außer Kraft, der durch ein Anhängen von „_i.c“ an den IDL-Dateinamen entsteht.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/iid**.  
  
-   **LocaleID**  
  
     Optionaler **int**-Parameter.  
  
     Gibt den *Gebietsschemabezeichner* an, der den Gebrauch von internationalen Zeichen in der Eingabedatei, dem Dateinamen und den Verzeichnispfaden ermöglicht. Geben Sie einen dezimalen Gebietsschemabezeichner an.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/lcid**. Siehe auch „Microsoft-Zuweisungen der Gebietsschema-IDs“ auf MSDN.  
  
-   **MkTypLibCompatible**  
  
     Optionaler **boolescher**-Parameter.  
  
     Wenn `true`, dann muss das Format der Eingabedatei mit mktyplib.exe Version 2.03 kompatibel sein.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/mktyplib203**. Siehe auch „Syntax der ODL-Datei“ auf MSDN.  
  
-   **OutputDirectory**  
  
     Optionaler **String**-Parameter.  
  
     Gibt das Standardverzeichnis an, in dem die MIDL-Aufgabe Ausgabedateien schreibt.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/out**.  
  
-   **PreprocessorDefinitions**  
  
     Optionaler **String[]**-Parameter.  
  
     Gibt einen oder mehrere *defines* an; d.h., einen Namen oder einen optionalen Wert, der an einen C-Präprozessor wie von einer `#define`-Direktive weitergegeben werden soll. Jedes „define“ ist folgendermaßen aufgebaut: *name[=value]*.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/D**. Siehe auch die Parameter **UndefinePreprocessorDefinitions** in dieser Tabelle.  
  
-   **ProxyFileName**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Namen für die Schnittstellen-Proxydatei für die COM-Schnittstelle an.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/proxy**.  
  
-   **RedirectOutputAndErrors**  
  
     Optionaler **String**-Parameter.  
  
     Leitet Ausgaben, wie z.B. Fehlermeldungen und Warnungen, aus der Standardausgabe in die angegebenen Dateien weiter.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/o**.  
  
-   **ServerStubFile**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Namen der Server-Stub-Datei für eine RPC-Schnittstelle an.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/sstub**. Siehe auch den Parameter **ClientStubFile** in dieser Tabelle.  
  
-   **Source**  
  
     Erforderlicher `ITaskItem[]`-Parameter.  
  
     Gibt eine durch Leerzeichen getrennte Liste der Quelldateien an.  
  
-   **StructMemberAlignment**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Zuweisung (*Komprimierungsebene*) der Strukturen im Zielsystem an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**NotSet**|*\<none>*|  
    |**1**|**/Zp1**|  
    |**2**|**/Zp2**|  
    |**4**|**/Zp4**|  
    |**8**|**/Zp8**|  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/Zp**. Die Option **/Zp** ist äquivalent zu der Option **/pack** und der älteren Option **/align**.  
  
-   **SuppressCompilerWarnings**  
  
     Optionaler **Boolean**-Parameter.  
  
     Wenn `true`, dann werden Warnmeldungen aus der MIDL-Aufgabe unterdrückt.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/no_warn**.  
  
-   **SuppressStartupBanner**  
  
     Optionaler `Boolean` -Parameter.  
  
     Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/nologo**.  
  
-   **TargetEnvironment**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Umgebung an, in der die Anwendung ausgeführt wird.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**NotSet**|*\<none>*|  
    |**Win32**|**/env win32**|  
    |**Itanium**|**/env ia64**|  
    |**X64**|**/env x64**|  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/env**.  
  
-   **TrackerLogDirectory**  
  
     Optionaler `String` -Parameter.  
  
     Gibt das Zwischenverzeichnis an, in dem die Nachverfolgungsprotokolle für diese Aufgabe gespeichert sind.  
  
-   **TypeLibFormat**  
  
     Optionaler **String**-Parameter.  
  
     Gibt das Format der Typbibliotheksdatei an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**NewFormat**|**/newtlb**|  
    |**OldFormat**|**/oldtlb**|  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter den Optionen **/newtlb** und **/oldtlb**.  
  
-   **TypeLibraryName**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Namen der Typbibliotheksdatei an.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/tlb**.  
  
-   **UndefinePreprocessorDefinitions**  
  
     Optionaler **String[]**-Parameter.  
  
     Entfernt jede vorherige Definition eines Namens, indem er den Namen wie eine `#undefine`-Direktive an den C-Präprozessor weitergibt. Geben Sie eine oder mehrere vorher definierte Namen ein.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/U**. Siehe auch die Parameter **PreprocessorDefinitions** in dieser Tabelle.  
  
-   **ValidateAllParameters**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, dann werden zusätzliche Dateifehler-Überprüfungsinformationen generiert, die für Integritätsprüfungen in der Laufzeit verwendet werden. Wenn `false`, dann werden keine Dateifehler-Überprüfungsinformationen generiert.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter den Optionen **/robust** und **/no_robist**.  
  
-   **WarnAsError**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, werden alle Warnungen als Fehler behandelt.  
  
     Wenn der MIDL-Aufgabenparameter **WarningLevel** nicht angegeben ist, werden Warnungen auf Standardlevel und auf Level 1 wie Fehler behandelt.  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/WX**. Siehe auch den Parameter **WarningLevel** in dieser Tabelle.  
  
-   **WarningLevel**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Schweregrad (*Warnstufe*) von auszugebenden Warnungen an. Für den Wert 0 wird keine Warnung ausgegeben. Andernfalls wird eine Warnung ausgegeben, wenn ihre Warnstufe numerisch kleiner als oder gleich der angegebene Wert ist.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**0**|**/W0**|  
    |**1**|**/W1**|  
    |**2**|**/W2**|  
    |**3**|**/W3**|  
    |**4**|**/W4**|  
  
     Weitere Informationen finden Sie auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website unter „MIDL-Befehlszeilenreferenz“ unter der Option **/W**. Siehe auch den Parameter **WarningLevel** in dieser Tabelle.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
