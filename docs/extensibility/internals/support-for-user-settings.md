---
title: "Unterstützung für Benutzereinstellungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 24bd28ad78f1cd3a21167215ed8348dc79edce6b
ms.contentlocale: de-de
ms.lasthandoff: 04/05/2017

---
# <a name="support-for-user-settings"></a>Unterstützung für Benutzereinstellungen
Eine VSPackage definieren möglicherweise eine oder mehrere Einstellungskategorien, d. h. Gruppen von Zustandsvariablen, die beibehalten werden, wenn ein Benutzer die **Import-und Exporteinstellungen** Befehl die **Tools** Menü. Um diese Persistenz aktivieren, verwenden Sie die Einstellungen APIs in der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Ein Registrierungseintrag, der als eines benutzerdefinierten Einstellungspunkts und einer GUID bezeichnet definiert ein VSPackage Einstellungskategorie. Ein VSPackage kann mehrere Einstellungskategorien unterstützen, die jeweils durch eine benutzerdefinierte Einstellungspunkte definiert.  
  
-   Implementierungen von Einstellungen, die auf Interopassemblys basieren (mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>Schnittstelle) sollten benutzerdefinierte Einstellungspunkte durch Bearbeiten der Registrierung oder mithilfe eines Skripts Registrierungsstelle (RGS-Datei) erstellen.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> Weitere Informationen finden Sie unter [Registrierungsskripte erstellen](/cpp/atl/creating-registrar-scripts).  
  
-   Code, der das Managed Package Framework (MPF) verwendet, sollten einen benutzerdefinierten Einstellungspunkt erstellen, durch Anfügen einer <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>dem VSPackage für jede benutzerdefinierte Einstellungspunkte.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
     Wenn eine einzelne VSPackage mehrere einen benutzerdefinierten Einstellungspunkt unterstützt, jede benutzerdefinierte Einstellungspunkte wird durch eine separate Klasse implementiert, und jede wird registriert, indem eine eindeutige Instanz der <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>Klasse.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Folglich können eine Klasse implementieren Einstellungen mehrere Einstellungskategorie unterstützen.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Benutzerdefinierte Einstellungen Punkt Eintrag Registrierungsdetails  
 Einen benutzerdefinierten Einstellungspunkt werden in einem Registrierungseintrag an folgendem Speicherort erstellt: HKLM\Software\Microsoft\VisualStudio\\*\<Version >*\UserSettings\\`<CSPName>`, wobei `<CSPName>` ist der Name des benutzerdefinierten Einstellungen auf der VSPackage-unterstützt und  *\<Version >* ist die Version des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], z. B. 8.0.  
  
> [!NOTE]
>  Der Stammpfad des HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* kann überschrieben werden, mit einer alternativen root, wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) initialisiert wird. Weitere Informationen finden Sie unter [Befehlszeilenoptionen](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Nachstehend ist die Struktur des Registrierungseintrags dargestellt:  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<Version >*\usersettings\coreui_mypackage  
  
 `<CSPName`> = s "#12345"  
  
 Paket = '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 Kategorie = "{YYYYYY JJJJ JJJJ YYYY YYYYYYYYY}"  
  
 ResourcePackage = "{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}"  
  
 AlternateParent = CategoryName  
  
|Name|Typ|Daten|Beschreibung|  
|----------|----------|----------|-----------------|  
|(Standard)|REG_SZ|Namen des benutzerdefinierten Einstellungen an|Der Schlüsselname `<CSPName`>, wird der nicht lokalisierte Name des benutzerdefinierten Einstellungen an.<br /><br /> Für Implementierungen, die basierend auf MPF, Name des Schlüssels durch Kombinieren von abgerufen wird die `categoryName` und `objectName` Argumente der <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>Konstruktor in `categoryName_objectName`.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute><br /><br /> Der Schlüssel kann leer sein, oder die Verweis-ID, die lokalisierte Zeichenfolge in einer Satelliten-DLL enthalten. Dieser Wert stammt aus dem `objectNameResourceID` Argument an die <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>Konstruktor.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|Package|REG_SZ|GUID|Die GUID des VSPackage, das die benutzerdefinierte Einstellungspunkte implementiert.<br /><br /> Implementierungen mithilfe von MPF anhand der <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>Klasse, verwenden Sie den Konstruktor `objectType` , enthält der VSPackages Argument <xref:System.Type>und Reflektion, um diesen Wert erhalten.</xref:System.Type> </xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|Kategorie|REG_SZ|GUID|Die GUID der Einstellungskategorie identifizieren.<br /><br /> Für Implementierungen, die basierend auf Interop-Assemblys, kann dieser Wert kann ein willkürlich gewählte sein GUID, die die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE übergibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>Methoden.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> Alle Implementierungen von diesen beiden Methoden sollten überprüfen, ob ihre GUID-Argumente.<br /><br /> Für basierend auf MPF-Implementierungen dieser GUID abgerufen wird, indem Sie die <xref:System.Type>der implementierende Klasse die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] einstellungsmechanismus.</xref:System.Type>|  
|ResourcePackage|REG_SZ|GUID|Optional.<br /><br /> Pfad zur Satelliten-DLL mit lokalisierte Zeichenfolgen an, wenn das implementierende VSPackage nicht angegeben wird.<br /><br /> MPF verwendet Reflektion, um die richtige VSPackage-Ressource erhalten so die <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>"Class" wird dieses Argument nicht festgelegt.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|AlternateParent|REG_SZ|Der Name des Ordners, unter der Seite "Extras – Optionen", enthält diese benutzerdefinierte Einstellungspunkte.|Dies ist optional.<br /><br /> Sie müssen diesen Wert festlegen, nur, wenn eine einstellungenimplementierung unterstützt **Extras – Optionen** Seiten, die in den Persistenz-Mechanismus verwenden der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] anstelle der Mechanismus in das Automatisierungsmodell zum Speichern des Status.<br /><br /> In diesen Fällen ist der Wert im Schlüssel AlternateParent der `topic` Teil der `topic.sub-topic` Zeichenfolge zur Identifizierung des jeweiligen **ToolsOptions** Seite. Z. B. für die **ToolsOptions** Seite `"TextEditor.Basic"` wäre der Wert der AlternateParent `"TextEditor"`.<br /><br /> Wenn <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>generiert die benutzerdefinierte Einstellungspunkte ist identisch mit dem Kategorienamen.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|
