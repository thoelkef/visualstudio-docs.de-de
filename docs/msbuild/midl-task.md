---
title: "MIDL-Aufgabe | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCMidlTool.ServerStubFile"
  - "VC.Project.VCMidlTool.ApplicationConfigurationMode"
  - "VC.Project.VCMidlTool.GenerateServerFiles"
  - "VC.Project.VCMidlTool.ClientStubFile"
  - "VC.Project.VCMidlTool.LocaleID"
  - "VC.Project.VCMidlTool.GenerateClientFiles"
  - "VC.Project.VCMidlTool.SuppressCompilerWarnings"
  - "VC.Project.VCMidlTool.TypeLibFormat"
  - "vc.task.midl"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild (Visual C++) MIDL-Aufgabe"
  - "MIDL-Aufgabe (MSBuild [Visual C++])"
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MIDL-Aufgabe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Umschließt das Compilertool von Microsoft Interface Definition Language (MIDL) midl.exe. Weitere Informationen finden Sie unter "MIDL Command-Line Reference" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
## <a name="parameters"></a>Parameter  
 Die folgende Tabelle beschreibt die Parameter der **MIDL** Aufgabe. Die meisten Aufgabenparameter und einige Sätze von Parametern entsprechen einer Befehlszeilenoption.  
  
-   **AdditionalIncludeDirectories**  
  
     Optionale **String []** Parameter.  
  
     Fügt ein Verzeichnis zur Liste der Verzeichnisse, die für importierte IDL-Dateien, eingeschlossene Headerdateien und Anwendungskonfigurationsdateien (ACF) durchsucht werden.  
  
     Weitere Informationen finden Sie unter der **/i** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **AdditionalOptions**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Eine Liste der Befehlszeilenoptionen. Z. B. **"***option1/option2 /option#*". Verwenden Sie diesen Parameter, um Befehlszeilenoptionen anzugeben, die nicht von einem beliebigen anderen MIDL-Aufgabenparameter dargestellt werden.  
  
     Weitere Informationen finden Sie unter "MIDL Command-Line Reference" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **ApplicationConfigurationMode**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, können einige ACF-Schlüsselwörter in der IDL-Datei verwendet.  
  
     Weitere Informationen finden Sie unter der **/app_config** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **ClientStubFile**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Namen der Client-Stub-Datei für eine RPC-Schnittstelle.  
  
     Weitere Informationen finden Sie unter der **/cstub** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website. Siehe auch die **ServerStubFile** -Parameter in dieser Tabelle.  
  
-   **CPreprocessOptions**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt Optionen an, an die C/C++-Präprozessor übergeben. Geben Sie eine durch Leerzeichen getrennte Liste der Präprozessor Optionen.  
  
     Weitere Informationen finden Sie unter der **/cpp_opt** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **DefaultCharType**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Standardtyp für Zeichen, den der C#-Compiler zum Kompilieren des generierten Codes verwenden.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**Signiert**|**/Char signiert**|  
    |**Ohne Vorzeichen**|**/Char ohne Vorzeichen**|  
    |**ASCII**|**/Char ascii7**|  
  
     Weitere Informationen finden Sie unter der **/char** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **DllDataFileName**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Dateinamen für die generierte *Dlldata* -Datei für eine Proxy-DLL.  
  
     Weitere Informationen finden Sie unter der **/dlldata** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **EnableErrorChecks**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Typ des Fehlers überprüfen, dass die generierten Stubs zur Laufzeit ausgeführt werden.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**Keine**|**/ Error none**|  
    |**EnableCustom**|**/ Error**|  
    |**Alle**|**alle/Error**|  
  
     Weitere Informationen finden Sie unter der **/Error** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **ErrorCheckAllocations**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, überprüfen Sie Out-of-Memory-Fehler.  
  
     Weitere Informationen finden Sie unter der **/Error Zuweisung** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **ErrorCheckBounds**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, wird die Größe konform veränderlicher und veränderlicher Arrays mit der Übertragungslängenangabe.  
  
     Weitere Informationen finden Sie unter der **/error Bounds_check** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **ErrorCheckEnumRange**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, überprüft, ob Enumerationswerte im zulässigen Bereich sind.  
  
     Weitere Informationen finden Sie unter der **/Error Enum** Option in der Befehlszeilenhilfe (**/?**) für midl.exe.  
  
-   **ErrorCheckRefPointers**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, überprüfen Sie, die keine null-Verweis-Zeiger auf Client-Stub übergeben werden.  
  
     Weitere Informationen finden Sie unter der **/Error Ref** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **ErrorCheckStubData**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, generiert einen Stub, der Marshalling rückgängig machende Ausnahmen auf der Serverseite abfängt und an den Client weitergegeben.  
  
     Weitere Informationen finden Sie unter der **/error Stub_data** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **GenerateClientFiles**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt an, ob der Compiler clientseitige C-Quelldateien für eine RPC-Schnittstelle generiert.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**Keine**|**/ Client keine**|  
    |**Stub**|**/ Client-stub**|  
  
     Weitere Informationen finden Sie unter der **/Client** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **GenerateServerFiles**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt an, ob der Compiler serverseitige C-Quelldateien für eine RPC-Schnittstelle generiert.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**Keine**|**/ Server keine**|  
    |**Stub**|**/ Server-stub**|  
  
     Weitere Informationen finden Sie unter der **/Server** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **GenerateStublessProxies**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, vollständig interpretierte Stubs zusammen mit Proxys ohne Stubs für Schnittstellen generiert.  
  
     Weitere Informationen finden Sie unter der **/Oicf** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **GenerateTypeLibrary**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, eine Typbibliotheksdatei (.tlb) wird nicht generiert.  
  
     Weitere Informationen finden Sie unter der **Erstellen/notlb** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **HeaderFileName**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Namen der generierten Headerdatei.  
  
     Weitere Informationen finden Sie unter der **/h** oder **/Header** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **IgnoreStandardIncludePath**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, die MIDL-Aufgabe durchsucht nur die mit angegebenen Verzeichnisse der **AdditionalIncludeDirectories** wechseln, und das aktuelle Verzeichnis und die von der INCLUDE-Umgebungsvariablen angegebenen Verzeichnisse werden ignoriert.  
  
     Weitere Informationen finden Sie unter der **/no_def_idir** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **InterfaceIdentifierFileName**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Namen der *Bezeichner Schnittstellendatei* für eine COM-Schnittstelle. Dies überschreibt den Standardnamen durch Hinzufügen von "_i.c" auf den Namen der IDL-Datei abgerufen.  
  
     Weitere Informationen finden Sie unter der **/iid** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **Gebietsschema-ID**  
  
     Optionale **Int** Parameter.  
  
     Gibt die *Gebietsschemabezeichner* ermöglicht die Verwendung internationaler Zeichen in Eingabedateien, Dateinamen und Verzeichnispfaden. Geben Sie einen dezimalen Gebietsschemabezeichner.  
  
     Weitere Informationen finden Sie unter der **/LCID** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website. Siehe auch "Locale IDs Assigned by Microsoft" in der MSDN LIBRARY.  
  
-   **MkTypLibCompatible**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, erfordert das Format der Eingabedatei mit mktyplib.exe, Version 2.03 kompatibel sein.  
  
     Weitere Informationen finden Sie unter der **/mktyplib203** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website. Siehe auch "ODL File Syntax" auf der MSDN-Website.  
  
-   **OutputDirectory**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt das Standardverzeichnis, in dem die MIDL-Aufgabe Ausgabedateien speichern.  
  
     Weitere Informationen finden Sie unter der **/out** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **PreprocessorDefinitions**  
  
     Optionale **String []** Parameter.  
  
     Gibt ein oder mehrere *definiert*; d. h. einen Namen und einen optionalen Wert an den C-Präprozessor wie übergeben werden bei einer `#define` Richtlinie. Das Format jeder definieren ist, *Name [= Value]*.  
  
     Weitere Informationen finden Sie unter der **/d** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website. Siehe auch die **UndefinePreprocessorDefinitions** -Parameter in dieser Tabelle.  
  
-   **ProxyFileName**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Namen der Schnittstellenproxydatei für eine COM-Schnittstelle.  
  
     Weitere Informationen finden Sie unter der **/Proxy** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **RedirectOutputAndErrors**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Leitet die Ausgabe z. B. Fehlermeldungen und Warnungen, aus dem Standardausgabestream in der angegebenen Datei.  
  
     Weitere Informationen finden Sie unter der **/o** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **ServerStubFile**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Namen der Server-Stub-Datei für eine RPC-Schnittstelle.  
  
     Weitere Informationen finden Sie unter der **/sstub** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website. Siehe auch die **ClientStubFile** -Parameter in dieser Tabelle.  
  
-   **Datenquelle**  
  
     Erforderlicher `ITaskItem[]`-Parameter.  
  
     Gibt eine durch Leerzeichen getrennte Liste der Quelldateien an.  
  
-   **StructMemberAlignment**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Ausrichtung (*packen Ebene*) der Strukturen im Zielsystem.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**NotSet**|*\< none>*|  
    |**1**|**/ Zp1**|  
    |**2**|**/ Zp2**|  
    |**4**|**/ Zp4 Leerräume**|  
    |**8**|**/ Zp8**|  
  
     Weitere Informationen finden Sie unter der **/Zp** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website. Die **/Zp** Option entspricht der **Pack** Option und das ältere **/ align** Option.  
  
-   **SuppressCompilerWarnings**  
  
     Optionale **booleschen** Parameter.  
  
     Wenn `true`, unterdrückt die Warnung Nachrichten von der MIDL-Aufgabe.  
  
     Weitere Informationen finden Sie unter der **/no_warn** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **SuppressStartupBanner**  
  
     Optionaler `Boolean` -Parameter.  
  
     Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.  
  
     Weitere Informationen finden Sie unter der **/nologo** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **TargetEnvironment**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt die Umgebung, in der die Anwendung ausgeführt wird.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**NotSet**|*\< none>*|  
    |**Win32**|**win32/env**|  
    |**Itanium**|**/ env ia64**|  
    |**X64**|**/ env x64**|  
  
     Weitere Informationen finden Sie unter der **/env** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **TrackerLogDirectory**  
  
     Optionaler `String` -Parameter.  
  
     Gibt das temporäre Verzeichnis, in dem Nachverfolgungsprotokolle für diese Aufgabe gespeichert werden.  
  
-   **TypeLibFormat**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt das Format der Typbibliotheksdatei an.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**NewFormat**|**/newtlb**|  
    |**OldFormat**|**/oldtlb**|  
  
     Weitere Informationen finden Sie unter der **/newtlb** und **/oldtlb** Optionen in "MIDL Command-Line Reference" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **TypeLibraryName**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Namen der Typbibliotheksdatei an.  
  
     Weitere Informationen finden Sie unter der **/tlb** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **UndefinePreprocessorDefinitions**  
  
     Optionale **String []** Parameter.  
  
     Entfernt jede vorherige Definition eines Namens durch Übergeben des Namens an dem C-Präprozessor wie bei einer `#undefine` Richtlinie. Geben Sie mindestens einen zuvor definierte Namen.  
  
     Weitere Informationen finden Sie unter der **/u** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website. Siehe auch die **PreprocessorDefinitions** -Parameter in dieser Tabelle.  
  
-   **ValidateAllParameters**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, zusätzliche Überprüfung Informationen generiert, die zum Ausführen der integritätsprüfungen zur Laufzeit verwendet wird. Wenn `false`, die Überprüfung von Fehlern Informationen werden nicht generiert.  
  
     Weitere Informationen finden Sie unter der **/ robust** und **/no_robust** Optionen in "MIDL Command-Line Reference" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website.  
  
-   **WarnAsError**  
  
     Optionaler `Boolean` -Parameter.  
  
     Wenn `true`, alle Warnungen als Fehler behandelt.  
  
     Wenn die **WarningLevel** MIDL-Aufgabenparamenter nicht angegeben ist, Warnungen auf der Standardebene, Ebene 1 als Fehler behandelt werden.  
  
     Weitere Informationen finden Sie unter der **/WX** Optionen in "MIDL Command-Line Reference" auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website. Siehe auch die **WarningLevel** -Parameter in dieser Tabelle.  
  
-   **WarningLevel**  
  
     Optionale **Zeichenfolge** Parameter.  
  
     Gibt den Schweregrad (*Warnstufe*) von Warnungen ausgegeben. Für einen Wert von 0 wird keine Warnung ausgegeben. Andernfalls wird eine Warnung ausgegeben, wenn die Warnstufe numerisch ist kleiner oder gleich dem angegebenen Wert.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer Befehlszeilenoption entspricht.  
  
    |Wert|Befehlszeilenoption|  
    |-----------|--------------------------|  
    |**0**|**/ W0**|  
    |**1**|**/ W1**|  
    |**2**|**/ W2**|  
    |**3**|**/ W3**|  
    |**4**|**/ W4**|  
  
     Weitere Informationen finden Sie unter der **/w** in "MIDL Command-Line Reference" auf die option der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) Website. Siehe auch die **WarnAsError** -Parameter in dieser Tabelle.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu Aufgaben](../msbuild/msbuild-task-reference.md)