---
title: "Unterst&#252;tzung f&#252;r Benutzereinstellungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Benutzerdefinierte Einstellungen Punkte"
  - "benutzereinstellungen [Visual Studio SDK] registrieren Persistenz-Unterstützung"
  - "Persistenz, Einstellungen registrieren"
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Unterst&#252;tzung f&#252;r Benutzereinstellungen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein VSPackage definieren möglicherweise eine oder mehrere Einstellungskategorien, Gruppen von Zustandsvariablen, die beibehalten werden, wenn ein Benutzer die **Import\/Export\-Einstellungen** Befehl die **Tools** Menü. Um diese Dauerhaftigkeit zu aktivieren, verwenden Sie die Einstellungen APIs in der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Ein Registrierungseintrag, der als einen benutzerdefinierten Einstellungen und eine GUID bezeichnet definiert ein VSPackage Einstellungskategorie. Ein VSPackage kann mehrere Einstellungskategorien unterstützt, die jeweils durch einen benutzerdefinierten Einstellungen Punkt definiert.  
  
-   Die Implementierung von Einstellungen, die anhand von Interop\-Assemblys \(mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> Schnittstelle\) sollten benutzerdefinierte Einstellungen Zeitpunkt durch Bearbeitung der Registrierung oder mithilfe eines Skripts Registrierungsstelle \(.rgs\-Datei\) erstellen. Weitere Informationen finden Sie unter [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
-   Code, der die Managed Package Framework \(MPF\) verwendet, sollten benutzerdefinierte Einstellungen Punkt erstellen, indem Sie Anfügen einer <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> die VSPackage für benutzerdefinierte Einstellungen verweisen.  
  
     Wenn ein einzelnes VSPackage mehrere benutzerdefinierte Einstellungen Punkte unterstützt und jeder benutzerdefinierten Einstellungen Punkts wird durch eine separate Klasse implementiert jede durch eine eindeutige Instanz registriert wird, die <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Klasse. Folglich können mehrere Einstellungskategorie einer Einstellungsdatei, die die implementierende Klasse unterstützt werden.  
  
## Benutzerdefinierte Einstellungen Point\-Eintrag Registrierungsdetails  
 Benutzerdefinierte Einstellungen Wiederherstellungspunkte werden in einem Registrierungseintrag an folgendem Speicherort erstellt: HKLM\\Software\\Microsoft\\VisualStudio\\*\< Version \>*\\UserSettings\\`<CSPName>`, wobei `<CSPName>` ist der Name des benutzerdefinierten Einstellungen an das VSPackage unterstützt und *\< Version \>* ist die Version des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], z. B. 8.0.  
  
> [!NOTE]
>  Der Stammpfad der HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< Version \>* kann überschrieben werden, durch eine alternative root, wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) wird initialisiert. Weitere Informationen finden Sie unter [Befehlszeilenoptionen](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Die Struktur des Registrierungseintrags ist unten dargestellt:  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\< Version \>*\\UserSettings\\  
  
 `<CSPName`\> \= s '\#12345'  
  
 Paket \= '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 Kategorie \= "{YYYYYY JJJJ JJJJ YYYY YYYYYYYYY}"  
  
 ResourcePackage \= "{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}"  
  
 AlternateParent \= "CategoryName"  
  
|Name|Typ|Daten|Beschreibung|  
|----------|---------|-----------|------------------|  
|\(Standard\)|REG\_SZ|Namen des benutzerdefinierten Einstellungen an|Der Schlüsselname `<CSPName`\>, der nicht lokalisierte Name des benutzerdefinierten Einstellungen an.<br /><br /> Für basierend auf MPF\-Implementierungen Namen für den Schlüssel abgerufen wird, durch die Kombination der `categoryName` und `objectName` Argumente der <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Konstruktor in `categoryName_objectName`.<br /><br /> Der Schlüssel kann leer sein, oder die Verweis\-ID, die lokalisierte Zeichenfolge in einer Satelliten\-DLL enthalten. Dieser Wert stammt aus der `objectNameResourceID` Argument für die <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Konstruktor.|  
|Package|REG\_SZ|GUID|Die GUID des VSPackage, das den benutzerdefinierten Einstellungen Punkt implementiert.<br /><br /> Zur Verwendung von MPF beruhen die <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Klasse, verwenden Sie den Konstruktor `objectType` Argument mit der VSPackage <xref:System.Type> und Reflektion, um diesen Wert zu erhalten.|  
|Kategorie|REG\_SZ|GUID|GUID, die der Kategorie "Einstellungen" bezeichnet.<br /><br /> Für Implementierungen, die anhand von Interop\-Assemblys, dieser Wert kann einen zufällig ausgewählten GUID, die die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE übergibt an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> Methoden. Jede Implementierung dieser beiden Methoden sollten ihre Argumente GUID überprüfen.<br /><br /> Für Implementierungen basierend auf MPF\-GUID wird abgerufen, indem die <xref:System.Type> von der Klasse implementiert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Settings\-Mechanismus.|  
|ResourcePackage|REG\_SZ|GUID|Optional.<br /><br /> Pfad zur Satelliten\-DLL mit lokalisierte Zeichenfolgen, wenn das implementierende VSPackage nicht angegeben wird.<br /><br /> MPF verwendet Reflektion, um die richtige Ressource VSPackage erhalten damit die <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Klasse wird dieses Argument nicht festgelegt.|  
|AlternateParent|REG\_SZ|Der Name des Ordners auf der Seite Optionen, die diese benutzerdefinierten Einstellungen Punkt enthält.|Optional.<br /><br /> Nur, wenn eine Settings\-Implementierung unterstützt, legen Sie diesen Wert muss **Optionen** Seiten, die Dauerhaftigkeit in der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] statt der Mechanismus zum Speichern des Zustands des Automatisierungsmodells.<br /><br /> In diesen Fällen wird der Wert im Schlüssel AlternateParent der `topic` Teil der `topic.sub-topic` Zeichenfolge zum Identifizieren des jeweiligen **ToolsOptionen** Seite. Z. B. für die **ToolsOptionen** Seite `"TextEditor.Basic"` wäre der Wert der AlternateParent `"TextEditor"`.<br /><br /> Wenn <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> generiert den benutzerdefinierten Einstellungen Punkt ist identisch mit den Namen der Kategorie.|