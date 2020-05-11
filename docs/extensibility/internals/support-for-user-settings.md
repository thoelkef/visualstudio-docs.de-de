---
title: Support für Benutzereinstellungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bb2450196de76917e9cffc2f5f5acc6c8ee7b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704789"
---
# <a name="support-for-user-settings"></a>Unterstützung für Benutzereinstellungen
Ein VSPackage kann eine oder mehrere Einstellungskategorien definieren, d. h. Gruppen von Zustandsvariablen, die beibehalten werden, wenn ein Benutzer im Menü **Extras** den Befehl **Import-/Exporteinstellungen** auswählt. Um diese Persistenz zu aktivieren, verwenden [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Sie die Einstellungs-APIs im .

 Ein Registrierungseintrag, der als benutzerdefinierter Einstellungspunkt und GUID bezeichnet wird, definiert die Einstellungskategorie eines VSPackage. Ein VSPackage kann mehrere Einstellungskategorien unterstützen, die jeweils durch einen benutzerdefinierten Einstellungspunkt definiert sind.

- Implementierungen von Einstellungen, die auf Interopassemblys (mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> Schnittstelle) basieren, sollten benutzerdefinierte Einstellungspunkte erstellen, indem Sie entweder die Registrierung bearbeiten oder ein Registrierungsskript (.rgs-Datei) verwenden. Weitere Informationen finden Sie unter [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Code, der das Managed Package Framework (MPF) verwendet, <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> sollte benutzerdefinierte Einstellungspunkte erstellen, indem für jeden benutzerdefinierten Einstellungspunkt ein an das VSPackage angefügt wird.

     Wenn ein einzelnes VSPackage mehrere benutzerdefinierte Einstellungspunkte unterstützt, wird jeder benutzerdefinierte Einstellungspunkt <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> von einer separaten Klasse implementiert, und jeder wird von einer eindeutigen Instanz der Klasse registriert. Folglich kann eine Einstellung, die Eine Klasse implementiert, mehr als eine Einstellungskategorie unterstützen.

## <a name="custom-settings-point-registry-entry-details"></a>Details zu benutzerdefinierten Einstellungen Punktregistrierungseinträge
 Benutzerdefinierte Einstellungspunkte werden in einem Registrierungseintrag am folgenden Speicherort erstellt: HKLM-Software-Microsoft-VisualStudio-Version\\*\<>*,UserSettings\\`<CSPName>`, wobei `<CSPName>` der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Name des benutzerdefinierten Einstellungspunkts ist, den das VSPackage unterstützt, und * \<Version>* die Version von ist, z. B. 8.0.

> [!NOTE]
> Der Stammpfad der HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-Version\\*\<>* kann mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] einem alternativen Stamm überschrieben werden, wenn die integrierte Entwicklungsumgebung (IDE) initialisiert wird. Weitere Informationen finden Sie unter [Befehlszeilenschalter](../../extensibility/command-line-switches-visual-studio-sdk.md).

 Die Struktur des Registrierungseintrags ist unten dargestellt:

 HKLM-Software-Microsoft-VisualStudio-Version\\*\<>*"UserSettings"

 `<CSPName`>= s '#12345'

 Paket = ''XXXXXX XXXX XXXX XXXX XXXXXXXXX''

 Kategorie = ''YYYYYY YYYY YYYY YYYY YYYY YYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYY

 ResourcePackage = ''ZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ''

 AlternateParent = CategoryName

| Name | type | Daten | BESCHREIBUNG |
|-----------------|--------| - | - |
| (Standardwert) | REG_SZ | Name des benutzerdefinierten Einstellungspunkts | Der Name des `<CSPName` Schlüssels,>, ist der nicht lokalisierte Name des benutzerdefinierten Einstellungspunkts.<br /><br /> Bei Implementierungen, die auf MPF basieren, wird `categoryName` der `objectName` Name <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> des Schlüssels durch Kombinieren der und Argumente des Konstruktors in `categoryName_objectName`ermittelt.<br /><br /> Der Schlüssel kann leer sein oder die Referenz-ID auf die lokalisierte Zeichenfolge in einer Satelliten-DLL enthalten. Dieser Wert wird `objectNameResourceID` aus dem <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Argument an den Konstruktor abgerufen. |
| Paket | REG_SZ | GUID | Die GUID des VSPackage, das den benutzerdefinierten Einstellungspunkt implementiert.<br /><br /> Implementierungen, die auf <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> MPF unter Verwendung der `objectType` Klasse basieren, verwenden <xref:System.Type> Sie das Argument des Konstruktors, das die VSPackages und die Reflektion enthält, um diesen Wert zu erhalten. |
| Category | REG_SZ | GUID | GUID, die die Einstellungskategorie identifiziert.<br /><br /> Bei Implementierungen, die auf Interopassemblys basieren, kann dieser Wert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] eine beliebig ausgewählte GUID sein, die die IDE an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> Methoden übergibt. Alle Implementierungen dieser beiden Methoden sollten ihre GUID-Argumente überprüfen.<br /><br /> Für Implementierungen, die auf MPF basieren, <xref:System.Type> wird diese [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] GUID von der Klasse abgerufen, die den Einstellungsmechanismus implementiert. |
| ResourcePackage | REG_SZ | GUID | Optional.<br /><br /> Pfad zur Satelliten-DLL, die lokalisierte Zeichenfolgen enthält, wenn das implementierende VSPackage sie nicht liefert.<br /><br /> MPF verwendet Reflektion, um die richtige <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Ressource VSPackage abzusondern, sodass die Klasse dieses Argument nicht setzt. |
| AlternateParent | REG_SZ | Name des Ordners unter der Seite Tools-Optionen, die diesen benutzerdefinierten Einstellungspunkt enthält. | Optional.<br /><br /> Sie müssen diesen Wert nur festlegen, wenn eine Einstellungsimplementierung **Tools-Optionsseiten** unterstützt, die den Persistenzmechanismus im [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] nicht den Mechanismus im Automatisierungsmodell zum Speichern des Status verwenden.<br /><br /> In diesen Fällen ist der Wert im `topic` AlternateParent-Schlüssel der Abschnitt der Zeichenfolge, der `topic.sub-topic` zum Identifizieren der bestimmten **ToolsOptions-Seite** verwendet wird. Für die Seite `"TextEditor.Basic"` **ToolsOptions** wäre der Wert `"TextEditor"`von AlternateParent beispielsweise .<br /><br /> Wenn <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> der benutzerdefinierte Einstellungspunkt generiert wird, entspricht er dem Kategorienamen. |
