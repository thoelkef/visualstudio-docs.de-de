---
title: "Ändern die isolierte Shell mithilfe der. PKGDEF-Datei | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 41e91983aaf236682b4ce723143f4053b5189547
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>Ändern die isolierte Shell mithilfe der. PKGDEF-Datei
Die PKGDEF-Datei unterstützt die Einstellungen, die Sie verwenden können, um eine isolierte Shell-Anwendung anzupassen. Es gibt Werte an, die erstellt werden, wenn eine Anwendung auf einem Computer installiert wird und verwiesen wird, werden von der Visual Studio-Shell beim Start der Anwendung. Die Einstellungen werden in der Datei, die basierend auf den entsprechenden Registrierungsschlüssel organisiert.  
  
> [!WARNING]
>  Beachten Sie, dass die PKGDEF-Dateien, die nicht in der Datei vsixmanifest VSPackages deklariert werden beim Start von Visual Studio nicht gescannt werden.  
  
 Die PKGDEF-Datei enthält Abschnitte, die jeweils entweder durch ein Schlüsselsymbol gekennzeichnet sind `[$RootKey$]` oder `[$RootKey$\` *Unterschlüssel*`]`, wobei $RootKey$ den Stammschlüssel für die Anwendung.  
  
 Jeder Abschnitt enthält Name-Wert-Paare, die das folgende Format aufweisen: `"` *ValueName*`"=`*Wert*.  
  
 Werte sind entweder eine Zeichenfolge, die in Anführungszeichen eingeschlossen ist, oder eine 32-Bit-Ganzzahl, die als einen DWORD-Wert dargestellt wird. Werte haben die folgenden Einschränkungen:  
  
-   Alle DWORD-Werte werden im Hexadezimalformat z. B. `dword:00000001`.  
  
     Boolesche Werte 1 steht für True und 0 für False steht.  
  
-   Alle GUID-Zeichenfolgen sind im Registrierungsformat, z. B. `"{00000000-0000-0000-0000-000000000000}"`.  
  
-   Alle lokalisierbaren Ressourcen-IDs haben das Format "@*ResourceID*" oder "#*ResourceID*", wobei *ResourceID* ist der Ressourcenbezeichner in das Anwendungspaket für die Benutzeroberfläche, z. B. `"@102"`. Das Anwendungspaket für die Benutzeroberfläche ist das Paket, das in der Einstellung der AppLocalizationPackage verwiesen wird.  
  
 Beispiel:  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 Sie können der PKGDEF-Datei Kommentare hinzufügen. Ein einzeiliger Kommentar hat zwei Schrägstriche, wie die ersten beiden Zeichen.  
  
 Eine Liste der Ersatzzeichenfolgen, finden Sie unter [Ersetzung in Zeichenfolgen verwendet. PKGDEF und. Pkgundef Dateien](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
 In den folgenden Abschnitten wird beschrieben, bestimmte Registrierungswerte, die das Verhalten von Visual Studio-Shell im isolierten Modus beeinflussen. Sie können auch zusätzliche Registrierungswerte für die Anwendung in dieser Datei definieren.  
  
> [!NOTE]
>  Wenn eine Einstellung nicht in der PKGDEF-Datei angegeben wird, wird keine entsprechender Eintrag in der Registrierung vorgenommen.  
  
## <a name="settings"></a>Einstellungen  
 Die folgende Tabelle beschreibt die Werte, die unter [$RootKey$] definiert.  
  
|Name|Typ|Wert|  
|----------|----------|-----------|  
|AddinsAllowed|dword|True, wenn Add-Ins geladen werden können. andernfalls "false".<br /><br /> Der Standardwert ist true.|  
|AllowsDroppedFilesOnMainWindow|dword|True, wenn das Hauptfenster abgelegte Dateien akzeptieren kann. andernfalls "false". Dateien im Hauptfenster werden geöffnet, mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>-Methode.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> Dies entspricht dem Öffnen eines Dokuments mithilfe der **öffnen** Befehl die **Datei** Menü in der Anwendung.<br /><br /> Der Standardwert ist true.|  
|AppIcon|string|Der vollständige Pfad des Programmsymbols. Dieses Symbol wird in der Titelleiste links neben den Namen der Anwendung.<br /><br /> Der Standardwert ist "$RootFolder$\\*SolutionName*ICO", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|AppLocalizationPackage|string|Die GUID des VSPackage, das die Benutzeroberfläche Satellitenassembly für die Anwendung enthält. Diese VSPackage ist eine kompilierte Version der .vsct-Datei und andere lokalisierte Zeichenfolgen enthalten. Funktionsgruppen und Menügruppen-Befehl können aktiviert oder deaktiviert das Ändern der Einstellungen in der Benutzeroberfläche VSCT-Datei.<br /><br /> Der Standardwert ist "{*VsUiPackageGuid*}", wobei *VsUiPackageGuid* ist die GUID für das Anwendungspaket für die Benutzeroberfläche.|  
|Anwendungsname|string|Der Name der Anwendung. Der Name wird in der Titelleiste des Anwendungsfensters angezeigt.<br /><br /> Der Standardwert ist der Name der Projektmappendatei Anwendung.|  
|CommandLineLogo|string|Den Bannertext, wenn die Anwendung in einem Konsolenfenster ausgeführt wird. Diese Einstellung gilt nur für Programme, die Befehlszeilen-Vorgänge zu unterstützen.<br /><br /> Der Standardwert ist "*CompanyName**SolutionName* Version 1.0.", wobei *CompanyName* ist der Name des Unternehmens bereitgestellt, wenn Windows installiert wurde, und *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|DefaultDebugEngine|string|Die GUID der standardmäßigen debug-Modul für die Anwendung verwenden.<br /><br /> Hinweis: Eine leere GUID (Nullen) gibt an, dass die Anwendung nicht über ein Standard-Debugmodul angibt. Dies ermöglicht dem Debugger das Debugmodul auswählen.<br /><br /> Der Standardwert ist "{00000000-0000-0000-0000-000000000000}".|  
|DefaultHomePage|string|Die Standard-URL der Startseite für die internen Web-Browser-Fenster.<br /><br /> Wenn die **Startseite** Option in der Anwendung verfügbar ist, wird diese Einstellung wirkt sich auch auf den Standardzustand der Option. Weitere Informationen finden Sie unter [Webbrowser, Umgebung, Optionen (Dialogfeld)](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Der Standardwert ist die URL des Unternehmens bei der Installation von Windows bereitgestellt.|  
|DefaultProjectsLocation|string|Der vollständige Pfad des Standardordners Projekte. Beispiel:<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> Wenn die **Speicherort der Visual Studio-Projekte** Option in der Anwendung verfügbar ist, wird diese Einstellung wirkt sich auch auf den Standardzustand der Option. Weitere Informationen finden Sie unter [NIB: Allgemein, Projekte und Projektmappen, Dialogfeld Optionen](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> Der Standardwert ist "$MyDocuments$\\*SolutionName*", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|DefaultSearchPage|string|Die URL der Standardsuchseite für interne Webbrowser-Fenster.<br /><br /> Wenn die **Suchseite** Option in der Anwendung verfügbar ist, wird diese Einstellung wirkt sich auch auf den Standardzustand der Option. Weitere Informationen finden Sie unter [Webbrowser, Umgebung, Optionen (Dialogfeld)](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Der Standardwert ist "http://search.live.com".|  
|DefaultUserFilesFolderRoot|string|Der Name des Ordners Benutzer relativ zum aktuellen Benutzer Ordner Eigene Dokumente des.<br /><br /> Der Standardwert ist der Name der Projektmappendatei Anwendung.|  
|DisableOutputWindow|dword|Gibt an, ob die isolierte Shell im Ausgabefenster behandeln soll, als deaktiviert.<br /><br /> Wenn dieser Wert festgelegt ist zeigt "true", Visual Studio die Lösung Manager Buildausgabe in nicht die **Ausgabe** Fenster und blendet die **anzeigen Ausgabefenster bei Buildbeginn** Kontrollkästchen in der **Projekte und Projektmappen** in die Kategorie der **Optionen** im Dialogfeld.<br /><br /> Der Standardwert ist false.|  
|HideMiscellaneousFilesByDefault|dword|True, wenn Ausblenden der **verschiedene Dateien** standardmäßig im Ordner **Projektmappen-Explorer**, andernfalls false.<br /><br /> Wenn die **verschiedene Dateien im Projektmappen-Explorer anzeigen** Option in der Anwendung verfügbar ist, wird diese Einstellung wirkt sich auch auf den Standardzustand der Option. Weitere Informationen finden Sie unter [Dokumente, Umgebung, Optionen (Dialogfeld)](../ide/reference/documents-environment-options-dialog-box.md).<br /><br /> Der Standardwert ist false.|  
|HideSolutionConcept|dword|True, um alle Projekte als eigenständige Projekte erstellt und der Lösung und der Lösung bezogenen Befehle für eigenständige Projekte standardmäßig ausgeblendet. andernfalls "false".<br /><br /> Wenn die **Projektmappe immer anzeigen** Option in der Anwendung verfügbar ist, wird diese Einstellung wirkt sich auch auf den Standardzustand der Option. Weitere Informationen finden Sie unter [NIB: Allgemein, Projekte und Projektmappen, Dialogfeld Optionen](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> Der Standardwert ist false.|  
|NewProjDlgInstalledTemplatesHdr|string|Der Name für den Visual Studio installiert sein Vorlagen-Header in der **Vorlagen** Liste der **neues Projekt** Dialogfeld. Dies ist eine Zeichenfolge oder eine lokalisierbare Ressourcen-ID, die aus dem UI-Anwendungspaket geladen wird.<br /><br /> Der Standardwert ist "*SolutionName* installierte Vorlagen", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|NewProjDlgSlnTreeNodeTitle|string|Der Name für die **Visual Studio-Projektmappen** Knoten in der **Projekttypen** in Struktur der **neues Projekt** Dialogfeld. Dies ist eine Zeichenfolge oder eine lokalisierbare Ressourcen-ID, die aus dem UI-Anwendungspaket geladen wird.<br /><br /> Der Standardwert ist "*SolutionName* installierte Vorlagen", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|SolutionFileCreatorIdentifier|string|Der Anwendungsbezeichner, die in der zweiten Zeile die Projektmappendateien angezeigt wird, die von der Anwendung generiert werden. Diese Zeile gibt an, die Anwendung, die die Datei erstellt wird. Gemäß der Konvention enthält dieser Wert den Namen der Anwendung und die Versionsnummer der Anwendung. Beispiel:<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> Das Programm VSLauncher.exe, das das Standardprogramm zum Öffnen einer Visual Studio-Projektmappendatei ist, wird diese zweite Zeile ermitteln die Version von Visual Studio, öffnen Sie die Projektmappendatei verwendet. Die Anwendung benötigt eine eigene Startprogramm, seine zugeordneten Projektmappendateien zu behandeln. Das Startprogramm kann auch diese zweite Zeile in der Projektmappendatei verwenden, um in die Version der Anwendung, öffnen die Projektmappe zu bestimmen.<br /><br /> Hinweis: Die Anwendung von Visual Studio-VSLauncher.exe nicht .sln-Dateien behandelt, die durch eine isolierte Shell-Anwendung erstellt wurden.<br /><br /> Der Standardwert ist "*SolutionName* Projektmappendatei Formatversion 10,00", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|SolutionFileExt|string|Die Projektmappen-Dateiname-Erweiterung für die Anwendung. Es wird empfohlen, dass Sie eine eindeutigen Dateinamen-Erweiterung (not.sln) auswählen.<br /><br /> Der Standardwert ist "*SolutionName*_sln", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|SplashScreenBitmap|string|Der vollständige Pfad der Bitmapdatei für den Begrüßungsbildschirm für die Anwendung.<br /><br /> Der Standardwert ist "$RootFolder$\Splash.bmp".|  
|ThisVersionDTECLSID|string|Der Klassenbezeichner (CLSID) für das Automatisierungsobjekt für die Anwendung.<br /><br /> Das Automatisierungsobjekt Anwendung ist das Objekt der obersten Ebene für die Anwendung in das Automatisierungsmodell für Visual Studio-Shell und implementiert die <xref:EnvDTE._DTE?displayProperty=fullName>Schnittstelle.</xref:EnvDTE._DTE?displayProperty=fullName><br /><br /> Wenn das Automatisierungsobjekt Anwendung unter dem Registrierungsschlüssel HKEY_CLASSES_ROOT\CLSID ordnungsgemäß registriert ist, können Sie die [CComPtrBase:: CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) Funktion, um eine Instanz der Anwendung direkt erstellen.<br /><br /> Die Visual Studio-Shell verwendet diese CLSID, um das Anwendungsobjekt für die Automatisierung in der Running Object Table (ROT) registrieren, indem Sie mit dem Flag ACTIVEOBJECT_WEAK. Auf diese Weise können Sie unter Verwendung der [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)-Funktion, einen Zeiger auf eine ausgeführte Instanz der Anwendung abrufen. Darüber hinaus, wenn Sie eine ProgID für das Automatisierungsobjekt Anwendung definieren, dann Visual Studio Shell registriert auch jede Instanz der Anwendung in der ROT mithilfe der Element-Moniker des Formulars *progID*:*ProcessID*, wobei *progID* ist die ProgID des Anwendungsobjekts Automatisierung und *ProcessID* ist der Prozess-ID für diese Instanz der Anwendung. Wenn beispielsweise einen Moniker ist wie folgt zu erstellen:<br /><br /> `CreateItemMoniker(L"!",`  *InstanceString*`, &instanceMoniker)`<br /><br /> wobei `instanceString` ist die *progID*:*ProcessID* Zeichenfolge. Verwenden Sie konnte `instanceMoniker` mit ROT GetObject-Funktion zum Abrufen einer Instanz.<br /><br /> Die Einstellung ThisVersionDTECLSID fehlt, wird die Anwendung nicht über das Component Object Model (COM) bereitgestellt. In diesem Fall kann keine Instanz der Anwendung erstellt werden, durch Aufrufen der [CComPtrBase:: CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) -Funktion und kann nicht in der ROT registriert werden.<br /><br /> Jede Version von einem VSPackage müssen verschiedene CLSID.<br /><br /> Der Standardwert ist die GUID, die Visual Studio für das Automatisierungsobjekt der Anwendung generiert.|  
|ThisVersionSolutionCLSID|string|Die CLSID des Solution-Objekts für die Anwendung.<br /><br /> Die Lösung Automation-Objekt enthält Informationen über die aktuelle geöffnete Projektmappe in einer Instanz der Anwendung, und implementiert die <xref:EnvDTE._Solution?displayProperty=fullName>Schnittstelle.</xref:EnvDTE._Solution?displayProperty=fullName><br /><br /> Wenn das Automatisierungsobjekt Lösung unter dem Registrierungsschlüssel HKEY_CLASSES_ROOT\CLSID ordnungsgemäß registriert ist, können Sie die [CComPtrBase:: CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) Funktion, ein Solution-Objekt für die Anwendung direkt zu erstellen.<br /><br /> Die Visual Studio-Shell verwendet diese CLSID Solution Automation-Objekts in der ROT registrieren, mit dem ACTIVEOBJECT_WEAK-Flag.<br /><br /> Wenn diese Einstellung weggelassen wird, und klicken Sie dann die Projektmappen-Klasse das Component Object Model (COM) nicht registriert ist und ein Solution-Objekt nicht werden, durch Aufrufen erstellt kann der [CComPtrBase:: CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) -Funktion und kann nicht in der ROT registriert werden.<br /><br /> Der Standardwert ist eine GUID, die Visual Studio für das Solution-Objekt der Anwendung generiert.|  
|UserFilesSubFolderName|string|Der Name des Unterordners unter Eigene Dateien-Ordner des Benutzers in dem die Anwendung Benutzerdateien und Unterordner erstellt.<br /><br /> Der Standardwert ist der Name der Projektmappendatei Anwendung.|  
|UserOptsFileExt|string|Die Erweiterung für die Projektmappendateien Benutzer Optionen für die Anwendung.<br /><br /> Der Standardwert ist der Name der Projektmappendatei Anwendung.|  
  
## <a name="binding-path-settings"></a>Pfad Bindungseinstellungen  
 Die [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}]-Schlüssel enthält die Liste der Verzeichnisse, die die Shell nach Assemblys sucht. Diese Verzeichnisse werden die Liste der Verzeichnisse hinzugefügt, die prüft die Shell für private Assemblys für die Anwendung.  
  
 Standardmäßig werden die PKGDEF-Datei keine Bindungspfad Einträge hinzugefügt. Allerdings werden die folgenden Unterverzeichnisse von der Visual Studio-Installationsverzeichnis der Anwendung Bindungspfad Liste in der Registrierung automatisch hinzugefügt.  
  
-   Common7\IDE\  
  
-   Common7\ide\\\PrivateAssemblies  
  
-   Common7\ide\\\PublicAssemblies  
  
 Um den Bindungspfad ein Verzeichnis hinzuzufügen, fügen Sie einen Eintrag im Format "*DirectoryName*"="", wobei *DirectoryName* ist ein absoluter Pfad. Beispiel:  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>Profileinstellungen  
 Die folgende Tabelle beschreibt die Werte, die für jedes zugeordnete Paket unter [$RootKey$ \Profile] definiert sind.  
  
|Name|Typ|Wert|  
|----------|----------|-----------|  
|AutoSaveFile|string|Das Verzeichnis, in dem die Anwendung Automatisches Speichern Dateien speichert.<br /><br /> Der Standardwert ist "$RootFolder$\Profiles\CurrentSettings.vssettings".|  
  
## <a name="package-satellite-dll-settings"></a>Satelliten-DLL für das Paket  
 Die folgende Tabelle beschreibt die Werte, die unter definiert sind [$RootKey$ \Packages\\{*VsPackageGuid*} \SatelliteDll] für die Satellite-DLL für jedes Paket zugeordnet, in dem *VsPackageGuid* ist die GUID des Pakets zugeordnet.  
  
|Name|Typ|Wert|  
|----------|----------|-----------|  
|DLL-Name|string|Der Dateiname der DLL.<br /><br /> Der Standardwert ist "*SolutionName*ui.dll", wobei *SolutionName* ist der Name der Projektmappendatei Anwendung.|  
|Pfad|string|Das Verzeichnis, das die Satelliten-DLL enthält.<br /><br /> Der Standardwert ist "$PackageFolder$".|  
  
## <a name="package-menu-item-settings"></a>Für das Paket im Menü Element  
 Der Registrierungsschlüssel [$RootKey$ \Menus] definiert die Benutzeroberflächen-Ressourcendateien für die Anwendung.  
  
 Menüelementwerte haben das Format "{*VsUiPackageGuid*}"=" *ResourceId*, *VersionNumber*", wobei *VsUiPackageGuid* ist die GUID des Anwendungspakets UI *ResourceId* ist der Ressourcenbezeichner der Ressource CTMENU, die die UI-Elemente enthält und *VersionNumber* ist eine virtuelle Versionsnummer für die CTMENU-Ressource. Weitere Informationen finden Sie unter [-Interop-Assembly-Befehlshandler registrieren](../extensibility/internals/registering-interop-assembly-command-handlers.md).  
  
 Standardmäßig wird ein Menüeintrag für das Element in der PKGDEF-Datei für das UI-Anwendungspaket erstellt.  
  
 Fügen Sie für jedes Paket mit Menüelementen, die als Teil der Anwendung verteilt wird einen Menüeintrag-Element für das Paket.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der isolierte Shells](../extensibility/customizing-the-isolated-shell.md)   
 [. Pkgundef-Dateien](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)
