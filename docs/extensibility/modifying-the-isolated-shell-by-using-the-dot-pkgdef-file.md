---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file
title: "Ändern von Isolated Shell mithilfe der. PKGDEF-Datei | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a0e654e603abe0e4f1546e5b06c2b3644af2067e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>Ändern von Isolated Shell mithilfe der. PKGDEF-Datei
Die PKGDEF-Datei unterstützt Einstellungen, die Sie verwenden können, um eine isolierte Shell-Anwendung anzupassen. Er gibt Werte an, die erstellt werden, wenn eine Anwendung auf einem Computer installiert ist und verwiesen wird, werden von der Visual Studio-Shell beim Starten der Anwendung. Die Einstellungen werden in der Datei, die basierend auf den entsprechenden Registrierungsschlüssel organisiert.  
  
> [!WARNING]
>  Beachten Sie, dass die PKGDEF-Dateien, die nicht in der vsixmanifest-Datei des VSPackage deklariert werden beim Start von Visual Studio nicht gescannt werden.  
  
 Die PKGDEF-Datei enthält Abschnitte, die jeweils anhand eines Schlüssels, entweder identifiziert werden `[$RootKey$]` oder `[$RootKey$\` *Unterschlüssel*`]`, wobei $RootKey$ den Stammschlüssel für die Anwendung.  
  
 Jeder Abschnitt enthält Name/Wert-Paare, die das folgende Format aufweisen: `"` *ValueName*`"=`*Wert*.  
  
 Werte sind entweder eine Zeichenfolge, die in Anführungszeichen eingeschlossen ist, oder eine 32-Bit-Ganzzahl, die als einen DWORD-Wert dargestellt wird. Werte haben die folgenden Einschränkungen:  
  
-   Alle Dword-Werte werden im Hexadezimalformat, z. B. `dword:00000001`.  
  
     Für boolesche Werte 1 "true", und 0 darstellt "false".  
  
-   Alle GUID-Zeichenfolgen sind im Registrierungsformat, z. B. `"{00000000-0000-0000-0000-000000000000}"`.  
  
-   Alle lokalisierbaren Ressourcen-IDs haben das Format "@*ResourceID*" oder "#*ResourceID*", wobei *ResourceID* ist der Ressourcenbezeichner im UI-Anwendungspaket beispielsweise `"@102"`. Das Anwendungspaket für die Benutzeroberfläche wird das Paket, das der Einstellung "AppLocalizationPackage" verwiesen wird.  
  
 Ein auf ein Objekt angewendeter  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 Sie können die PKGDEF-Datei Kommentare hinzufügen. Ein einzeiliger Kommentar hat zwei Schrägstriche, wie die ersten beiden Zeichen.  
  
 Eine Liste der Ersatzzeichenfolgen, finden Sie unter [Ersetzung in Zeichenfolgen verwendet. PKGDEF und. Pkgundef Dateien](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
 In den folgenden Abschnitten wird beschrieben, bestimmte Registrierungswerte, die das Verhalten von Visual Studio-Shell im isolierten Modus beeinflussen. Sie können auch zusätzliche Registrierungswerte für die Anwendung in dieser Datei definieren.  
  
> [!NOTE]
>  Wenn eine Einstellung nicht in der PKGDEF-Datei angegeben wird, ist kein entsprechender Eintrag in der Registrierung vorgenommen.  
  
## <a name="settings"></a>Einstellungen  
 Die folgende Tabelle beschreibt die Werte, die unter [$RootKey$] definiert.  
  
|name|Typ|Wert|  
|----------|----------|-----------|  
|AddinsAllowed|dword|True, wenn-add-ins geladen werden kann. andernfalls "false".<br /><br /> Der Standardwert ist true.|  
|AllowsDroppedFilesOnMainWindow|dword|True, wenn das Hauptfenster abgelegte Dateien annehmen kann. andernfalls "false". Dateien, die gelöscht werden, die im Hauptfenster geöffnet sind, mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> Methode. Dies entspricht dem Öffnen eines Dokuments mithilfe der **öffnen** Befehl die **Datei** Menü in der Anwendung.<br /><br /> Der Standardwert ist true.|  
|AppIcon|Zeichenfolge|Der vollständige Pfad des Programmsymbols. Dieses Symbol wird in der Titelleiste links vom Namen Anwendung angezeigt.<br /><br /> Der Standardwert ist "$RootFolder$\\*SolutionName*ICO", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|AppLocalizationPackage|Zeichenfolge|Die GUID des VSPackage, die die UI-Satellitenassembly für die Anwendung enthält. Diese VSPackage enthält eine kompilierte Version der VSCT-Datei und andere lokalisierte Zeichenfolgen enthalten kann. Das Feature für Gruppen und Menübefehl Gruppen können aktiviert oder deaktiviert das Ändern der Einstellungen in der UI-Projekt VSCT-Datei.<br /><br /> Der Standardwert ist "{*VsUiPackageGuid*}", wobei *VsUiPackageGuid* ist die GUID, die an der UI-Anwendungspaket zugewiesen.|  
|Anwendungsname|Zeichenfolge|Der Name der Anwendung. Der Name wird in der Titelleiste des Anwendungsfensters angezeigt.<br /><br /> Der Standardwert ist der Name der Projektmappendatei Anwendung.|  
|CommandLineLogo|Zeichenfolge|Den Bannertext, wenn die Anwendung in einem Konsolenfenster ausgeführt wird. Diese Einstellung betrifft nur Anwendungen, die Befehlszeilen-Vorgänge zu unterstützen.<br /><br /> Der Standardwert ist "*CompanyName**SolutionName* Version 1.0.", wobei *CompanyName* ist der Name des Unternehmens bereitgestellt, wenn Windows installiert wurde, und *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|DefaultDebugEngine|Zeichenfolge|Die GUID des Standardwerts für das Debuggen Modul für die Anwendung zu nutzen.<br /><br /> Hinweis: Eine leere GUID (Nullen) gibt an, dass die Anwendung eine Standard-Debugging-Modul nicht angegeben werden. Dies ermöglicht dem Debugger wählen Sie das Debugmodul verwenden.<br /><br /> Der Standardwert ist "{00000000-0000-0000-0000-000000000000}".|  
|DefaultHomePage|Zeichenfolge|Die Standard-URL der Startseite für die interne Webbrowserfenster angezeigt.<br /><br /> Wenn die **Startseite** Option in der Anwendung verfügbar ist, und klicken Sie dann diese Einstellung wirkt sich auch auf den Standardstatus der Option. Weitere Informationen finden Sie unter [Webbrowser, Umgebung, Optionen (Dialogfeld)](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Der Standardwert ist die URL des Unternehmens bereitgestellt, wenn Windows installiert wurde.|  
|DefaultProjectsLocation|Zeichenfolge|Der vollständige Pfad des Standardordners Projekte. Ein auf ein Objekt angewendeter<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> Wenn die **Speicherort der Visual Studio-Projekte** Option in der Anwendung verfügbar ist, und klicken Sie dann diese Einstellung wirkt sich auch auf den Standardstatus der Option. Weitere Informationen finden Sie unter [NIB: Allgemein, Projekte und Projektmappen, Dialogfeld Optionen](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> Der Standardwert ist "$MyDocuments$\\*SolutionName*", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|DefaultSearchPage|Zeichenfolge|Die standardmäßige URL der Suchseite für die interne Webbrowserfenster angezeigt.<br /><br /> Wenn die **Suchseite** Option in der Anwendung verfügbar ist, und klicken Sie dann diese Einstellung wirkt sich auch auf den Standardstatus der Option. Weitere Informationen finden Sie unter [Webbrowser, Umgebung, Optionen (Dialogfeld)](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Der Standardwert ist "http://search.live.com".|  
|DefaultUserFilesFolderRoot|Zeichenfolge|Der Name des Ordners "Benutzer" relativ zum aktuellen Benutzer Ordner Eigene Dokumente des.<br /><br /> Der Standardwert ist der Name der Projektmappendatei Anwendung.|  
|DisableOutputWindow|dword|Gibt an, ob der isolierte Shell die Fenster "Ausgabe" behandeln soll, als deaktiviert.<br /><br /> Wenn dieser Wert festgelegt ist, auf "true", Visual Studio zeigt keine Solution Manager Buildausgabe in den **Ausgabe** Fenster und blendet das **anzeigen Ausgabefenster bei Buildbeginn** Kontrollkästchen in der  **Projekte und Projektmappen** Kategorie in den **Optionen** (Dialogfeld).<br /><br /> Der Standardwert ist false.|  
|HideMiscellaneousFilesByDefault|dword|"True" Ausblenden der **sonstige Dateien** standardmäßig im Ordner **Projektmappen-Explorer**, andernfalls "false".<br /><br /> Wenn die **verschiedene Dateien im Projektmappen-Explorer anzeigen** Option in der Anwendung verfügbar ist, und klicken Sie dann diese Einstellung wirkt sich auch auf den Standardstatus der Option. Weitere Informationen finden Sie unter [Dokumente, Umgebung, Optionen (Dialogfeld)](../ide/reference/documents-environment-options-dialog-box.md).<br /><br /> Der Standardwert ist false.|  
|HideSolutionConcept|dword|True, um alle Projekte als eigenständige Projekte erstellen, und die Lösung und der Lösung bezogenen Befehle für eigenständige Projekte standardmäßig ausgeblendet. andernfalls "false".<br /><br /> Wenn die **Projektmappe immer anzeigen** Option in der Anwendung verfügbar ist, und klicken Sie dann diese Einstellung wirkt sich auch auf den Standardstatus der Option. Weitere Informationen finden Sie unter [NIB: Allgemein, Projekte und Projektmappen, Dialogfeld Optionen](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> Der Standardwert ist false.|  
|NewProjDlgInstalledTemplatesHdr|Zeichenfolge|Der Name für den Visual Studio installiert sein Vorlagen-Header in der **Vorlagen** in Liste der **neues Projekt** (Dialogfeld). Dies ist eine Zeichenfolge oder eine lokalisierbare Ressourcen-ID, die im UI-Anwendungspaket geladen wird.<br /><br /> Der Standardwert ist "*SolutionName* installierte Vorlagen", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|NewProjDlgSlnTreeNodeTitle|Zeichenfolge|Der Name für die **Visual Studio-Projektmappen** Knoten in der **-Projekttypen** -Struktur in der **neues Projekt** (Dialogfeld). Dies ist eine Zeichenfolge oder eine lokalisierbare Ressourcen-ID, die im UI-Anwendungspaket geladen wird.<br /><br /> Der Standardwert ist "*SolutionName* installierte Vorlagen", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|SolutionFileCreatorIdentifier|Zeichenfolge|Der Anwendungsbezeichner, der die zweite Zeile in die Projektmappendateien angezeigt wird, die von der Anwendung generiert werden. Diese Zeile gibt an, die Anwendung, die die Datei erstellt wird. Gemäß der Konvention enthält dieser Wert den Namen der Anwendung und die Versionsnummer der Anwendung. Ein auf ein Objekt angewendeter<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> Das Programm VSLauncher.exe, d., das h. als Standardprogramm für eine Visual Studio-Projektmappendatei öffnen, wird diese zweite Zeile ermitteln die Version von Visual Studio, öffnen Sie die Projektmappendatei verwendet. Die Anwendung, müsste eine eigene Startprogramm, seine zugeordneten Projektmappendateien zu behandeln. Das Startprogramm konnte auch diese zweite Zeile in der Projektmappendatei verwenden, um zu bestimmen, welche Version der Anwendung, die Projektmappe zu öffnen.<br /><br /> Hinweis: Die Anwendung von Visual Studio-VSLauncher.exe nicht .sln-Dateien behandelt, die von einer isolierten shellanwendung erstellt wurden.<br /><br /> Der Standardwert ist "*SolutionName* Projektmappendatei Formatversion 10,00", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|SolutionFileExt|Zeichenfolge|Der Projektmappe Erweiterung für die Anwendung. Es wird empfohlen, dass Sie eine eindeutigen Dateinamen-Erweiterung (not.sln) auswählen.<br /><br /> Der Standardwert ist "*SolutionName*_sln", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|SplashScreenBitmap|Zeichenfolge|Der vollständige Pfad der Bitmapdatei für den Begrüßungsbildschirm für die Anwendung.<br /><br /> Der Standardwert ist "$RootFolder$\Splash.bmp".|  
|ThisVersionDTECLSID|Zeichenfolge|Der Klassenbezeichner (CLSID) des Automatisierungsobjekts, für die Anwendung.<br /><br /> Die Anwendung das Automatisierungsobjekt ist das Objekt der obersten Ebene für die Anwendung in das Automatisierungsmodell für Visual Studio-Shell und implementiert die <xref:EnvDTE._DTE?displayProperty=fullName> Schnittstelle.<br /><br /> Wenn das Automatisierungsobjekt Anwendung unter dem Registrierungsschlüssel HKEY_CLASSES_ROOT\CLSID ordnungsgemäß registriert ist, können Sie die [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) Funktion, eine Instanz der Anwendung direkt zu erstellen.<br /><br /> Die Visual Studio-Shell verwendet diese CLSID, um das Anwendungsobjekt für die Automatisierung in der Running Object Table (ROT) registrieren, indem Sie mit dem ACTIVEOBJECT_WEAK-Flag. Auf diese Weise können Sie verwenden die [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)Funktion, um einen Zeiger auf eine ausgeführte Instanz der Anwendung abzurufen. Darüber hinaus, wenn Sie eine ProgID für die Automatisierung Anwendungsobjekt definieren, klicken Sie dann die Visual Studio-Shell registriert auch jede Instanz der Anwendung in der ROT mithilfe der Element-Moniker des Formulars *progID*:*ProcessID* , wobei *progID* ist die ProgID des Anwendungsobjekts Automatisierung und *ProcessID* ist der Prozess-ID für diese Instanz der Anwendung. Angenommen, Sie erstellen einen Moniker ist wie folgt:<br /><br /> `CreateItemMoniker(L"!",`  *InstanceString*`, &instanceMoniker)`<br /><br /> wobei `instanceString` ist die *progID*:*ProcessID* Zeichenfolge. Verwenden Sie `instanceMoniker` mit ROT GetObject-Funktion zum Abrufen einer Instanz.<br /><br /> Wenn die Einstellung ThisVersionDTECLSID weggelassen wird, wird die Anwendung nicht über das Component Object Model (COM) ausgesetzt. In diesem Fall kann keine Instanz der Anwendung erstellt werden, durch Aufrufen der [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) -Funktion und kann nicht in der ROT registriert werden.<br /><br /> Jede Version eines VSPackage benötigen unterschiedliche CLSID.<br /><br /> Der Standardwert ist die GUID, die Visual Studio für das Automatisierungsobjekt, mit der Anwendung generiert wurde.|  
|ThisVersionSolutionCLSID|Zeichenfolge|Die CLSID des Objekts Lösung für die Anwendung.<br /><br /> Das Automatisierungsobjekt Lösung enthält Informationen über die aktuelle geöffnete Projektmappe in einer Instanz von der Anwendung und implementiert die <xref:EnvDTE._Solution?displayProperty=fullName> Schnittstelle.<br /><br /> Wenn das Automatisierungsobjekt Lösung unter dem Registrierungsschlüssel HKEY_CLASSES_ROOT\CLSID ordnungsgemäß registriert ist, können Sie die [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) Funktion, ein Objekt der Lösung für die Anwendung direkt zu erstellen.<br /><br /> Die Visual Studio-Shell verwendet diese CLSID, um das Automatisierungsobjekt Lösung in der ROT zu registrieren, indem Sie mit dem ACTIVEOBJECT_WEAK-Flag.<br /><br /> Wenn diese Einstellung weggelassen wird, dann die Projektmappe-Klasse nicht das Component Object Model (COM registriert ist) und eine Projektmappe nicht werden durch Aufrufen erstellt konnte der [CComPtrBase:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) -Funktion und kann nicht registriert werden der ROT.<br /><br /> Der Standardwert ist eine GUID, die Visual Studio für das Objekt "Lösung" der Anwendung generiert wurde.|  
|UserFilesSubFolderName|Zeichenfolge|Der Name des Unterordners unter dem Benutzer eigene Ordner "Dokumente" in der die Anwendung Benutzerdateien und Unterordner erstellt.<br /><br /> Der Standardwert ist der Name der Projektmappendatei Anwendung.|  
|UserOptsFileExt|Zeichenfolge|Die Erweiterung für die Projektmappendateien Benutzer Optionen für die Anwendung.<br /><br /> Der Standardwert ist der Name der Projektmappendatei Anwendung.|  
  
## <a name="binding-path-settings"></a>Binden die Pfadeinstellungen  
 Die [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] Schlüssel enthält die Liste der Verzeichnisse, die die Befehlsshell nach Assemblys sucht. Diese Verzeichnisse werden die Liste der Verzeichnisse hinzugefügt, die Prüfpunkte die Shell nach privaten Assemblys für die Anwendung.  
  
 Standardmäßig werden die PKGDEF-Datei ohne Bindungspfad Einträge hinzugefügt. Allerdings werden die folgenden Unterverzeichnisse des Visual Studio-Installationsverzeichnis der Anwendung Bindungspfad Liste in der Registrierung automatisch hinzugefügt.  
  
-   Common7\IDE\  
  
-   Common7\ide\\\PrivateAssemblies  
  
-   Common7\ide\\\PublicAssemblies  
  
 Um den Bindungspfad ein Verzeichnis hinzuzufügen, fügen Sie einen Eintrag im Format "*DirectoryName*"="", wobei *DirectoryName* ist ein absoluter Pfad. Ein auf ein Objekt angewendeter  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>Profileinstellungen  
 Die folgende Tabelle beschreibt die Werte, die für jedes zugeordnete Paket unter [$RootKey$ \Profile] definiert sind.  
  
|name|Typ|Wert|  
|----------|----------|-----------|  
|AutoSaveFile|Zeichenfolge|Das Verzeichnis, in dem die Anwendung Automatisches Speichern Dateien speichert.<br /><br /> Der Standardwert ist "$RootFolder$\Profiles\CurrentSettings.vssettings".|  
  
## <a name="package-satellite-dll-settings"></a>Paketeinstellungen Satelliten-DLL  
 Die folgende Tabelle beschreibt die Werte, die unter definiert sind [$RootKey$ \Packages\\{*VsPackageGuid*} \SatelliteDll] für den Satelliten-DLL der einzelnen zugeordneten Pakete, auf dem *VsPackageGuid* ist die GUID des Pakets zugeordnet.  
  
|name|Typ|Wert|  
|----------|----------|-----------|  
|DLL-Name|Zeichenfolge|Der Dateiname der DLL.<br /><br /> Der Standardwert ist "*SolutionName*ui.dll", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|Pfad|Zeichenfolge|Das Verzeichnis, das die Satelliten-DLL enthält.<br /><br /> Der Standardwert ist "$PackageFolder$".|  
  
## <a name="package-menu-item-settings"></a>Paketeinstellungen Menü-Element  
 Der Registrierungsschlüssel [$RootKey$ \Menus] definiert UI Ressourcendateien für die Anwendung.  
  
 Menüelementwerte haben das Format "{*VsUiPackageGuid*}"=" *ResourceId*, *VersionNumber*", wobei *VsUiPackageGuid* ist die GUID des das Anwendungspaket UI *ResourceId* ist der Ressourcenbezeichner der Ressource CTMENU, die die UI-Elemente enthält und *VersionNumber* ist eine virtuelle Versionsnummer für die CTMENU die Ressource. Weitere Informationen finden Sie unter [Interop-Assembly-Befehlshandler registrieren](../extensibility/internals/registering-interop-assembly-command-handlers.md).  
  
 Standardmäßig wird ein Menüeintrag für das Element in der PKGDEF-Datei für das Anwendungspaket für die Benutzeroberfläche erstellt.  
  
 Fügen Sie für jedes Paket, Menüelemente bereitstellt und, die als Teil der Anwendung verteilt wird ein Menüeintrag-Element für das Paket ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der isolierten Shells](../extensibility/customizing-the-isolated-shell.md)   
 [. Pkgundef-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)