---
title: "Registrieren benutzerdefinierter Seiten f&#252;r Optionen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Registrierung, benutzerdefinierte Seiten für Optionen, Extras (Menü)"
  - "Seiten für Optionen, Extras (Menü) [Visual Studio SDK], registrieren"
ms.assetid: 0ac6377d-a679-4f7d-be80-451c829b56f2
caps.latest.revision: 28
caps.handback.revision: 28
manager: "douge"
---
# Registrieren benutzerdefinierter Seiten f&#252;r Optionen
Damit eine Seite **Extras\/Optionen** verfügbar ist und den Benutzern zur Unterstützung automatisierung, muss sie mit der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) ordnungsgemäß registriert werden.  
  
 **Extras\/Optionen** Seiten auf der Grundlage des verwalteten Paketframework registriert werden, indem eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> zu VSPackages übernimmt, die die Seite enthält.  Automatisierungsunterstützung wird angegeben, indem die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A>\-Eigenschaft auf `true` festlegt.  
  
## Seite Optionen im Menü Extrasen\-Registrierung  
 Die Integration einer benutzerdefinierten Seite **Extras\/Optionen** mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erfordert die Erstellung eines Registrierungseintrags an folgendem Speicherort: HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<Version\>*\\ ToolsOptionsPages, wo *\<Version\>* die Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist, z. B. 8.0.  
  
 Der Eintrag verfügt über einen Primärschlüssel der Kategorie \(`<PageCategory>`\) der Seite **Extras\/Optionen** sowie einen untergeordneten Unterschlüssel, der den Namen der Unterkategorie der Seite \(`<PageSubCategory>`\) enthält.  
  
 Beispielsweise verfügt die Seite **Extras\/Optionen**, die mit der Zeichenfolge, **TextEditor.Basic** identifiziert wird, ein Registrierungsschlüssel `<PageCategory>`\=textEditor mit einem Unterschlüssel von `<PageSubCategory>`\=Basic.  
  
 Die Struktur des Registrierungseintrags ist unten:  
  
 HKLM \\ Software \\ Microsoft \\ VisualStudio \\*\<Version\>*\\ \\ ToolsOptionsPages  
  
 `<PageCategory>` \= '\#12345'  
  
 Paket "\=" {}  
  
 ResourcePackage \= "{YYYYYY YYYY YYYY YYYY YYYYYYYYY}"  
  
 HKLM \\ Software \\ Microsoft \\ VisualStudio \\*\<Version\>*\\ ToolsOptionsPages \\`<PageCategory>`  
  
 `<PageSubCategory>>` \= '\#67890'  
  
 Seite \= "{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}"  
  
 Paket \= "{AAAAAA AAAA AAAA AAAA AAAAAAAAA}"  
  
 ResourcePackage \= "{BBBBBB BBBB BBBB BBBB BBBBBBBBB}"  
  
 NoShowAllView \= 0\/1  
  
 In der folgenden Tabelle sind die Werte unter HKLM \\ Software \\ Microsoft \\ VisualStudio \\*\<Version\>*\\ ToolsOptionsPages \\`<PageCategory>` auf.  
  
|Name|type|Daten|Beschreibung|  
|----------|----------|-----------|------------------|  
|\(Standard\)|REG\_SZ|Der kanonische Kategoriename der benutzerdefinierten **Extras\/Optionen** Seite|Der Schlüsselname, `<PageCategory>`, ist die kanonische nicht lokalisierte Kategoriename der Seite **Extras\/Optionen**. **Note:**  Wenn die Automatisierung unterstützt wird, sind die kanonischen nicht lokalisierten Namen der Kategorie und Unterkategorie abgerufen <xref:EnvDTE.Properties>\-Auflistung einer Seite **Extras\/Optionen**.  Weitere Informationen finden Sie unter [Verwenden von Optionsseiten](../misc/using-options-pages.md). <br /><br /> Für Implementierungen auf das verwaltete Paketframework, wird `<PageCategory`\> vom `categoryName`\-Argument an den Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> abzurufen.<br /><br /> Der Schlüssel kann leer sein, oder sie kann die Bezugs\-ID auf die lokalisierten Zeichenfolgen in der Satelliten\-DLL enthalten eine Implementierung.<br /><br /> Für Implementierungen auf das verwaltete Paketframework, wird dieser Wert vom `categoryResourceID`\-Argument an den Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> abzurufen.|  
|Package|REG\_SZ|GUID|Die GUID VSPackages, das die benutzerdefinierte Seite **Extras\/Optionen** implementiert.<br /><br /> Implementierungen auf das verwaltete Paketframework mithilfe der Reflektion abzurufen, verwenden Sie <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> diesen Wert.|  
|ResourcePackage|REG\_SZ|GUID|Optional.<br /><br /> Ein Satelliten\-DLLs, die lokalisierte Zeichenfolgen enthält, wenn implementierende VSPackage sie nicht bereitstellt.<br /><br /> Das verwaltete Paketframework verwendet Reflektion, um das richtige Ressourcen Paket, sodass dieses Argument nicht <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> legt diesen fest.|  
  
 In der folgenden Tabelle sind die Werte unter HKLM \\ Software \\ Microsoft \\ VisualStudio \\*\<Version\>*\\ ToolsOptionsPages \\`<PageCategory>`\\`<PageSubCategory>` auf.  
  
|Name|type|Daten|Beschreibung|  
|----------|----------|-----------|------------------|  
|\(Standard\)|REG\_SZ|Der kanonische Name der Unterkategorie der benutzerdefinierten **Extras\/Optionen** Seite|Der Schlüsselname, `<PageSubCategory`\>, ist die kanonische nicht lokalisierte Name der **Extras\/Optionen** Seiten unterkategorie. **Note:**  Wenn die Automatisierung unterstützt wird, sind die kanonischen nicht lokalisierten Namen der Kategorie und Unterkategorie abgerufen <xref:EnvDTE.Properties>\-Auflistung einer Seite **Extras\/Optionen**.  Weitere Informationen finden Sie unter [Verwenden von Optionsseiten](../misc/using-options-pages.md). <br /><br /> Für Implementierungen auf das verwaltete Paketframework, wird `<PageSubegory`\> vom `pageName`\-Argument an den Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> abzurufen.<br /><br /> Der Schlüssel kann leer sein, oder sie kann die Bezugs\-ID auf die lokalisierten Zeichenfolgen in einer Satelliten\-DLL einer Implementierung enthalten.<br /><br /> Für Implementierungen auf das verwaltete Paketframework, wird dieser Wert vom `pageNameResourceID`\-Argument an den Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> abzurufen.|  
|Seite|REG\_SZ|GUID|Die GUID des Objekts, das die benutzerdefinierte Seite **Extras\/Optionen** implementiert.<br /><br /> Implementierungen auf das verwaltete Paketframework mit <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> verwenden das `pageType`\-Argument des Konstruktors, der <xref:System.Type> VSPackages und Reflektion, um diesen Wert zu erhalten.|  
|Package|REG\_SZ|GUID|Implementierungen auf das verwaltete Paketframework mithilfe der Reflektion abzurufen, verwenden Sie <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> diesen Wert.|  
|ResourcePackage|REG\_SZ|GUID|Optional.<br /><br /> Ein Satelliten\-DLLs, die lokalisierte Zeichenfolgen enthält, wenn implementierende VSPackage sie nicht bereitstellt.<br /><br /> Das verwaltete Paketframework verwendet Reflektion, um die richtige Ressourcen\-DLL, sodass dieses Argument nicht <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> legt diesen fest.|  
|NoShowAllView|REG\_DWORD|0 oder 1|Optional.<br /><br /> Gibt an, ob eine angegebene Seite **Extras\/Optionen** in der komplexen \(Standard\) Ansicht von **Extras\/Optionen** Seiten angezeigt werden soll.  Unterstützt die Programmierumgebung, z. B. Visual Basic, die spezielle **Extras\/Optionen** Seiten verfügen, um allgemeine Einstellungen zu aggregieren, um Benutzer mit spezialisierten vereinfachten Ansichten von Optionen zu bieten.<br /><br /> Wenn der REG\_DWORD\-Eintrag ungleich 0 \(null\) ist, wird die Seite **Extras\/Optionen** nicht in einer komplexen Ansicht.<br /><br /> Weitere Informationen finden Sie unter [Dialogfeld "Optionen"](../ide/reference/options-dialog-box-visual-studio.md).<br /><br /> Implementierungen auf das verwaltete Paketframework können diesen Wert festlegen, indem sie die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.NoShowAllView%2A>\-Eigenschaft auf `true` im <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>\-Konstruktor festlegen.|  
  
 VSPackage oder ein Objekt auf Grundlage einer einzelnen Interop\-Assembly implementieren möglicherweise mehrere Seite **Extras\/Optionen**.  Jede Implementierung erfordert einen neuen Eintrag unter HKLM \\ Software \\ Microsoft \\ VisualStudio \\*\<Version\>*\\ ToolsOptionsPages.  
  
 Da das verwaltete Paketframework das Objekt instanziiert, das eine Seite **Extras\/Optionen** bereitstellt, sollte jede Seite über eine eigene Implementierung Objekt verfügen, das von einer <xref:Microsoft.VisualStudio.Shell.Package> Implementierung von VSPackages unabhängig ist.  
  
## Automatisierungsunterstützung  
 Wenn Automatisierungsunterstützung verwendet wird, um eine Seite **Extras\/Optionen** zu implementieren, muss sie als Automatisierungsmodell für registrieren.  Zur Verwaltung von Eigenschaften für die Automatisierung verwendet werden, und seine Dauerhaftigkeit mit den Mechanismen **Extras\/Optionen** Seitenzustand, muss sie zu speichern als `AutomationProperty` Anbieter registrieren.  
  
### Registrieren von VSPackages als Automatisierungs\-Anbieter \(nur für Optionsseiten im Menü Extras auf der Grundlage von Interop\-Assemblys\)  
 **Extras\/Optionen** Seiten auf der Grundlage einer Interop\-Assembly werden als Teil von VSPackages Implementierungsklassen implementiert.  
  
 In diesem Fall wenn eine Seite **Extras\/Optionen**, die Automatisierung zu unterstützen, muss die Automatisierung als VSPackage ASSEMBLY\-basiertes Interop Anbieter registriert werden.  
  
> [!NOTE]
>  Automatisierungsunterstützung in verwaltetem Paketframework wird von einem Objekt von der Implementierung VSPackages zulässig.  Wenn dieses Objekt die Automatisierung unterstützt, wird dies von der <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A>\-Eigenschaft des <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>\-Konstruktors registriert.  
  
 Der Eintrag für die Registrierung eines VSPackage als Automatisierungsmodell für hat die Form HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<Version\>*\\ Packages \\*\<PackageGUID\>*\\ Automatisierung, wo *\<Version\>* die Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(z. B. 8.0\) festgelegt ist, und die GUID ist *\<PackageGUID\>* VSPackages, das das Automatisierungsobjekt implementiert.  
  
> [!NOTE]
>  Der Stammpfad von HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<Version\>* kann mit einem alternativen Stamm überschrieben werden, wenn die Visual Studio\-Shell initialisiert wird.  Weitere Informationen finden Sie unter [Befehlszeilenoptionen](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Die Struktur des Registrierungseintrags ist:  
  
 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<Version\>*\\ Packages \\*\<PackageGUID\>*\\ Automatisierung  
  
 `<AutomationObjectName>`  
  
|Name|type|Daten|Beschreibung|  
|----------|----------|-----------|------------------|  
|Automatisierung|REG\_SZ|Nicht definiert|Nicht definiert.<br /><br /> Das Vorhandensein dieser Schlüssel gibt an, dass ein VSPackage, das von *\<PackageGUID\>* verweist, Automatisierung unterstützt.<br /><br /> Das Feld kann verwendet werden, um Dokumentation zu speichern.<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> erstellt automatisch dieser Schlüssel für Anwendungen auf das verwaltete Paketframework.|  
|`<AutomationObjectName>`|REG\_SZ|Der kanonische Name des Automatisierungsobjekts bereitgestellten|Nur der Schlüsselname ist relevant.  Er wird in den Automatisierungsvorgängen verwendet.<br /><br /> Das Feld kann verwendet werden, um Dokumentation zu speichern.<br /><br /> Für Implementierungen auf das verwaltete Paketframework, wird der Name dieser Taste vom `name`\-Argument an den <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute>\-Konstruktor bestimmt.<br /><br /> Wenn der <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute>\-Konstruktor eine gültige Zeichenfolge, die in die <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute.Description%2A>\-Eigenschaft angegeben wird, wird dieser Wert hier eingefügt.|  
  
### Registriert eine Optionsseite im Menü Extras von Automatisierung unterstützt  
 Verwaltete müssen Paket\-Rahmen\- und Interops ASSEMBLY\-basierte Implementierungen von **Extras\/Optionen** registrieren, um Seiten über Zugriff auf eine Seite **Extras\/Optionen** zu ermöglichen.  Dies schließt die Dauerhaftigkeit Automatisierungseigenschaften Mechanismen und der Zugriff durch ein <xref:EnvDTE>.  Dies ist unabhängig vom Automatisierungsmodell selbst als VSPackages Registrierung dienstanbieter.  
  
 Wie bei der **Extras\/Optionen** Registrierung der Seiten, die oben erwähnt wird, hat der Eintrag ein `<PageCategory>` Kategorie \(mit dem Primärschlüssel\) der Seite **Extras\/Optionen** sowie einen untergeordneten Unterschlüssel, der den Namen der Unterkategorie der Seite \(`<PageSubcategory>`\) enthält.  
  
 Wenn Sie das verwaltete Paketframework verwenden, verwenden Sie <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>, um eine Klasse als Bereitstellen einer Seite **Extras\/Optionen** und die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A>\-Eigenschaft festzulegen zu `true` zu registrieren, um anzugeben, dass die Seite Automatisierung unterstützt.  
  
 Der Registrierungseintrag HKEY\_LOCAL\_MACHINE wird in " \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<Version\>*\\ AutomationProperties, wo *\<Version\>* die Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist, z. B. 8.0.  
  
> [!NOTE]
>  Der Stammpfad von HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<Version\>* kann mit einem alternativen Stamm überschrieben werden, wenn die Visual Studio\-Shell initialisiert wird, dann [Befehlszeilenoptionen](../extensibility/command-line-switches-visual-studio-sdk.md), finden Sie weitere Informationen.  
  
 Die Struktur des Registrierungseintrags ist unten:  
  
 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ AutomationProperties *\<Version\>\\*  
  
 `<PageCategory>` \= ‘\#456’  
  
 ResourcePackage \= "{}"  
  
 `<PageSubCategory>` \= ‘\#789’  
  
 Paket \= "{YYYYYY YYYY YYYY YYYY YYYYYYYYY}"  
  
 name \= "`<PageCategory>` .`<PageSubcategory>`"  
  
 ProfileSave" \= "1\/0  
  
 In der folgenden Tabelle sind die Werte unter HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<Version\>*\\ AutomationProperties \\`<PageCategory>` auf.  
  
|Name|type|Daten|Beschreibung|  
|----------|----------|-----------|------------------|  
|\(Standard\)|REG\_SZ|Der kanonische Kategoriename der benutzerdefinierten **Extras\/Optionen** Seite|Der Schlüsselname, `<PageCategory`\>, ist die kanonische nicht lokalisierte Name der Kategorie **Extras\/Optionen** Seiten. **Note:**  Wenn die Automatisierung unterstützt wird, sind die kanonischen nicht lokalisierten Namen der Kategorie und Unterkategorie abgerufen <xref:EnvDTE.Properties>\-Auflistung einer Seite **Extras\/Optionen**.  Weitere Informationen finden Sie unter [Verwenden von Optionsseiten](../misc/using-options-pages.md). <br /><br /> Der Schlüssel kann leer sein, oder sie kann die Bezugs\-ID auf die lokalisierten Zeichenfolgen in der Satelliten\-DLL enthalten eine Implementierung.<br /><br /> Für Implementierungen auf das verwaltete Paketframework, wird `<PageCategory`\> vom `categoryName`\-Argument an den Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> abzurufen.|  
|ResourcePackage|REG\_SZ|GUID|Optional.<br /><br /> Ein Satelliten\-DLLs, die lokalisierte Zeichenfolgen enthält, wenn implementierende VSPackage sie nicht bereitstellt.<br /><br /> Das verwaltete Paketframework verwendet Reflektion, um die richtige Ressource VSPackage, sodass dieses Argument nicht <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> legt diesen fest.|  
  
 In der folgenden Tabelle sind die Werte unter HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<Version\>*\\ AutomationProperties \\`<PageCategory>\<PageSubCategory>` auf.  
  
|Name|type|Daten|Beschreibung|  
|----------|----------|-----------|------------------|  
|\(Standard\)|REG\_SZ|Der Name der Unterkategorie der benutzerdefinierten **Extras\/Optionen** Seite|Der Schlüsselname, `<PageSubCategory`\>, ist die kanonische nicht lokalisierte Name der **Extras\/Optionen** Seiten unterkategorie. **Note:**  Wenn die Automatisierung unterstützt wird, sind die kanonischen nicht lokalisierten Namen der Kategorie und Unterkategorie abgerufen <xref:EnvDTE.Properties>\-Auflistung einer Seite **Extras\/Optionen**.  Weitere Informationen finden Sie unter [Verwenden von Optionsseiten](../misc/using-options-pages.md). <br /><br /> Der Schlüssel kann leer sein, oder sie kann die Bezugs\-ID auf die lokalisierten Zeichenfolgen in der Satelliten\-DLL enthalten eine Implementierung.<br /><br /> Für Implementierungen auf das verwaltete Paketframework, wird `<PageSubCategory>` vom `pageName`\-Argument an den Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> abzurufen.|  
|Package|REG\_SZ|GUID|Die GUID VSPackages, das die benutzerdefinierte Seite **Extras\/Optionen** implementiert.<br /><br /> Implementierungen auf das verwaltete Paketframework mithilfe der Reflektion abzurufen, verwenden Sie <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> diesen Wert.|  
|Name|REG\_SZ|Name der Auflistung der Eigenschaft **Extras\/Optionen** Seiten|Die `<PageCategory>.<PageSubCategory>` Zeichenfolge verwendet, um die Seite **Extras\/Optionen** zuzugreifen.  Weitere Informationen finden Sie unter [Verwenden von Optionsseiten](../misc/using-options-pages.md).<br /><br /> Für Implementierungen auf das verwaltete Paketframework, wird der Name von Argumenten, die an den Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> abrufen und hat die Form `categoryName.pageName`.|  
|ProfileSave|DWORD|1\/0|Optional.<br /><br /> Dieser Wert gibt an, ob die **Extras\/Optionen** Seiteneinstellungen durch den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Mechanismus zur Einstellungen gespeichert werden, wenn ein Benutzer auf den Befehl im Menü **ExtrasEinstellungen importieren und exportieren** klickt.<br /><br /> Wenn der Schlüssel vorhanden ist und der Wert 1 ist, dann fordert die Seite **Extras\/Optionen** Unterstützung von Einstellungen an.<br /><br /> Implementierungen auf das verwaltete Paketframework legen diesen Wert fest, wenn der <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>\-Konstruktor mit dem <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>\-Eigenschaft auf `true` angegeben wird.|  
  
## Siehe auch  
 [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)   
 [Verwenden von Optionsseiten](../misc/using-options-pages.md)   
 [Erstellen von Optionsseiten mithilfe von Interop\-Assemblys](../misc/creating-options-pages-by-using-interop-assemblies.md)   
 [Gewusst wie: Erstellen benutzerdefinierter Optionsseiten](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [Optionen\-Seiten](../misc/options-pages.md)   
 [Benutzeroberflächenautomatisierungs\-Unterstützung für Optionen \(Seiten\)](../extensibility/internals/automation-support-for-options-pages.md)