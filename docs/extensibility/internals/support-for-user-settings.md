---
title: Unterstützung für Benutzereinstellungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f7fbb6c8e6a6310b736ade599ad7854bc4255c0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070739"
---
# <a name="support-for-user-settings"></a>Unterstützung für Benutzereinstellungen
Eine VSPackage kann ein oder mehrere Einstellungskategorien, sind Gruppen von Zustandsvariablen, die beibehalten werden, wenn ein Benutzer wählt definieren die **Import-/Exporteinstellungen** Befehl die **Tools** Menü. Zum Aktivieren der dieser Persistenz, die Sie verwenden der Einstellungen-APIs in der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

 Ein Registrierungseintrag, der als eines benutzerdefinierten Einstellungspunkts und einer GUID bezeichnet wird definiert, eine VSPackage Einstellungskategorie. Eine VSPackage kann mehrere Einstellungskategorien unterstützen, die jeweils durch einen benutzerdefinierten Einstellungspunkt definiert.

- Implementierungen von Einstellungen, die auf Interopassemblys basieren (mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> Schnittstelle) sollten Sie die benutzerdefinierten Einstellungspunkts durch Bearbeiten der Registrierungs oder mithilfe eines Skripts Registrierungsstelle (RGS-Datei) erstellen. Weitere Informationen finden Sie unter [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Code, der das Managed Package Framework (MPF) verwendet, sollten benutzerdefinierten Einstellungspunkten erstellen, durch Anfügen einer <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> für das VSPackage für jeden benutzerdefinierten Einstellungspunkts.

     Wenn ein einzelne VSPackage mehrere benutzerdefinierten Einstellungspunkten unterstützt, jeder benutzerdefinierten Einstellungspunkts durch eine separate Klasse implementiert wird und jedes, indem eine eindeutige Instanz registriert wird der <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Klasse. Daher können die Einstellungen für einen implementierende Klasse mehr als eine Einstellungskategorie unterstützen.

## <a name="custom-settings-point-registry-entry-details"></a>Benutzerdefinierte Einstellungen Punkt Eintrag Registrierungsdetails
 Benutzerdefinierten Einstellungspunkten werden in einem Registrierungseintrag an folgendem Speicherort erstellt: HKLM\Software\Microsoft\VisualStudio\\*\<Version >* \UserSettings\\`<CSPName>`, wobei `<CSPName>` ist der Name des benutzerdefinierten Einstellungspunkts das VSPackage unterstützt und  *\<Version >* ist die Version des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], z. B. 8.0.

> [!NOTE]
>  Der Stammpfad des HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* kann überschrieben werden, mit einer alternativen Stamm, wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) ist Initialisiert. Weitere Informationen finden Sie unter [Befehlszeilenoptionen](../../extensibility/command-line-switches-visual-studio-sdk.md).

 Die Struktur des Registrierungseintrags ist nachstehend dargestellt:

 HKLM\Software\Microsoft\VisualStudio\\*\<Version>* \UserSettings\

 `<CSPName`>= s '#12345'

 Paket = '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'

 Kategorie = "{YYYYYY JJJJ JJJJ JJJJ YYYYYYYYY}"

 ResourcePackage = "{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}"

 AlternateParent = "CategoryName"

| Name | Typ | Daten | Beschreibung |
|-----------------|--------| - | - |
| (Standard) | REG_SZ | Name des benutzerdefinierten Einstellungspunkts | Der Schlüsselname `<CSPName`>, der nicht lokalisierte Name des benutzerdefinierten Einstellungspunkts.<br /><br /> Für basierend auf MPF-Implementierungen der Schlüsselname abgerufen wird, aus der `categoryName` und `objectName` Argumente der <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Konstruktor in `categoryName_objectName`.<br /><br /> Der Schlüssel kann leer sein, oder die Verweis-ID, die lokalisierte Zeichenfolge in einer Satelliten-DLL enthalten. Dieser Wert wird abgerufen, von der `objectNameResourceID` Argument für die <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Konstruktor. |
| Package | REG_SZ | GUID | Die GUID des VSPackage, das die benutzerdefinierten Einstellungspunkts implementiert.<br /><br /> Implementierungen je nach MPF der <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Klasse, verwenden Sie den Konstruktor des `objectType` , enthält der VSPackages Argument <xref:System.Type> und Reflektion, um diesen Wert zu erhalten. |
| Kategorie | REG_SZ | GUID | GUID, die die Einstellungskategorie identifiziert werden.<br /><br /> Für Implementierungen, die basierend auf interop-Assemblys, kann dieser Wert kann nach dem Zufallsprinzip gewählten sein GUID, die die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE übergibt an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> Methoden. Alle Implementierungen dieser beiden Methoden sollten überprüfen, ob ihre GUID-Argumente.<br /><br /> Für Implementierungen basierend auf MPF-diese GUID wird abgerufen, indem die <xref:System.Type> von der Klasse implementiert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] einstellungsmechanismus. |
| ResourcePackage | REG_SZ | GUID | Dies ist optional.<br /><br /> Pfad zur Satelliten-DLL mit lokalisierte Zeichenfolgen auf, wenn das VSPackage implementierende, wird diese nicht bereitgestellt.<br /><br /> MPF verwendet Reflektion, um die richtige Ressource VSPackage, erhalten so die <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Klasse wird dieses Argument nicht festgelegt. |
| AlternateParent | REG_SZ | Der Name des Ordners, unter der Extras Optionen-Seite, enthält dieses benutzerdefinierten Einstellungspunkts. | Dies ist optional.<br /><br /> Sie müssen diesen Wert festlegen, nur, wenn eine einstellungenimplementierung unterstützt **Extras/Optionen** Seiten, verwenden den persistenzmechanismus in, der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] statt der Mechanismus in das Automatisierungsmodell zum Zustand zu speichern.<br /><br /> In diesen Fällen ist der Wert im Schlüssel AlternateParent ist die `topic` Teil der `topic.sub-topic` Zeichenfolge zur Identifizierung der entsprechenden **ToolsOptions** Seite. Z. B. für die **ToolsOptions** Seite `"TextEditor.Basic"` wäre der Wert des AlternateParent `"TextEditor"`.<br /><br /> Wenn <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> des benutzerdefinierten Einstellungspunkts, generiert es ist identisch mit den Namen der Kategorie. |
