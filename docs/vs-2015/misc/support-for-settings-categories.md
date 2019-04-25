---
title: Unterstützung für Einstellungskategorien | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- settings, supporting with Visual Studio SDK
- Visual Studio SDK, supporting settings
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
manager: jillfra
ms.openlocfilehash: 833783267c70c0a201e4b84bc5031bce517dc0a2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054481"
---
# <a name="support-for-settings-categories"></a>Unterstützung für Einstellungskategorien
Eine Einstellungskategorie besteht aus einer Gruppe von Optionen, die die integrierte Entwicklungsumgebung (Integrated Development Environment; IDE) anpassen. Beispielsweise können Einstellungen das Layout der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Fenster und die Inhalte von Menüs steuern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um den **Assistent zum Importieren und Exportieren von Einstellungen**zu starten. Der Assistent bietet drei Optionen zur Auswahl: Exportieren, Importieren oder Zurücksetzen der Einstellungen. Durch die Auswahl von beispielsweise „Exportieren“ wird die Seite **Einstellungen für den Export auswählen** des Assistenten aufgerufen.  
  
 In der Strukturansicht im Navigationsbereich auf dieser Seite sind die Kategorien aufgeführt. Eine Kategorie ist eine Gruppe von verwandten Einstellungen, die als „benutzerdefinierter Einstellungspunkt“ angezeigt werden, d.h. als ein Kontrollkästchen. Verwenden Sie diese Kontrollkästchen, um die Kategorien auszuwählen, die in einer VSETTINGS-Datei dauerhaft gespeichert werden. Der Assistent ermöglicht das Benennen der VSETTINGS-Datei und das Angeben ihres Pfads.  
  
> [!NOTE]
>  Die Einstellungen werden gespeichert oder als eine Kategorie wiederhergestellt, und individuelle Einstellungsnamen werden nicht im Assistenten angezeigt.  
  
 Das Managed Package Framework (MPF) unterstützt die Erstellung von Einstellungskategorien mit einem Minimum an zusätzlichem Code.  
  
- Sie erstellen ein VSPackage, um einen Container für die Kategorie bereitzustellen, indem Sie eine Unterklasse der <xref:Microsoft.VisualStudio.Shell.Package>-Klasse erstellen.  
  
- Sie erstellen die Kategorie selbst, indem Sie sie von der <xref:Microsoft.VisualStudio.Shell.DialogPage>-Klasse ableiten.  
  
- Sie verbinden die beiden mit dem <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="support-for-settings-categories"></a>Unterstützung für Einstellungskategorien  
 Die <xref:Microsoft.VisualStudio.Shell.Package>-Klasse bietet Unterstützung für das Erstellen von Kategorien. Die<xref:Microsoft.VisualStudio.Shell.DialogPage>-Klasse implementiert eine Kategorie. Die Standardimplementierung von <xref:Microsoft.VisualStudio.Shell.DialogPage> bietet Benutzern Ihre öffentlichen Eigenschaften als Kategorie an. Weitere Informationen finden Sie unter [Creating a Settings Category](../extensibility/creating-a-settings-category.md).  
  
 Die <xref:Microsoft.VisualStudio.Shell.DialogPage>-Klasse implementiert <xref:Microsoft.VisualStudio.Shell.IProfileManager>, der Persistenz jeweils für die Optionsseiten und Benutzereinstellungen bietet. Die Methoden <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> und <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> schreiben Einstellungen dauerhaft in eine VSETTINGS-Datei, die von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] als jeweils <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> bereitgestellt wurde. Die <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A>-Methode setzt Einstellungen auf ihre Standardwerte zurück.  
  
 Die Klasse <xref:Microsoft.VisualStudio.Shell.DialogPage> stellt eine Implementierung der <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A>-Methode bereit, die die Name-Wert-Paare aus dem XML-Feed liest und Reflektion zum Ermitteln von öffentlichen Eigenschaften in der abgeleiteten <xref:Microsoft.VisualStudio.Shell.DialogPage>-Klasse verwendet. Eigenschaften, die Namen besitzen, die mit den Name-Wert-Paaren übereinstimmen, erhalten die entsprechenden Werte.  
  
 Die standardmäßige Implementierung von <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> verwendet Reflektion, um öffentliche Eigenschaften in der von <xref:Microsoft.VisualStudio.Shell.DialogPage> abgeleiteten Klasse zu ermitteln und schreibt die Eigenschaftennamen und -Werte an den XML-Feed als Name-Wert-Paare.  
  
### <a name="settings-category-registry-path"></a>Registrierungspfad der Einstellungskategorie  
 Der Registrierungspfad der Einstellungskategorie wird durch die Kombination von <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, dem Wort, UserSettings, der Einstellungskategorie und dem Namen des benutzerdefinierten Einstellungspunkts festgelegt. Die Namen der Einstellungskategorie und des benutzerdefinierten Einstellungspunkts werden verknüpft und durch einen Unterstrich getrennt, um den kanonischen, nicht lokalisierten Namen zu bilden, der in der Registrierung erscheint. Wenn die Einstellungskategorie z.B. „My Category“ ist, der benutzerdefinierte Einstellungspunkt „My Settings“ ist, und ApplicationRegistryRoot ist „HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp“, dann verfügt die Einstellungskategorie über den Registrierungsschlüssel „HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\My Category_My Settings“.  
  
> [!NOTE]
>  Der kanonische Name wird nicht in einer Benutzeroberfläche angezeigt. Er wird verwendet, um einen lesbaren Namen der Einstellungskategorie zuzuordnen, so wie ein programmatischer Bezeichner (ProgID).  
  
### <a name="settings-category-attribute"></a>Das Attribut der Einstellungskategorie  
 Die <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> bestimmt die Zuordnung von Kategorien zu benutzerdefinierten einstellungspunkten im der **-Import- und Exportassistenten Einstellungen** durch Zuordnen einer Kategorie mit dem VSPackage, das es bereitstellt. Betrachten Sie das folgende Codefragment:  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 Ressourcen-ID 106 wird „My Category“ zugeordnet, 107 wird „My Settings“ zugeordnet, und 108 wird „Various Options“ zugeordnet. Damit wird deklariert, dass `MyPackage` die Kategorie „My Category_My Settings“ bereitstellt. Die Kategorie wird von der `OptionsPageGeneral`-Klasse bereitgestellt, die <xref:Microsoft.VisualStudio.Shell.IProfileManager> implementieren muss. Die Einstellungen in dieser Kategorie sind die öffentlichen Eigenschaften der `OptionsPageGeneral` -Klasse.  
  
 Der Einstellungspunkt im **Assistent zum Importieren und Exportieren von Einstellungen**verfügt über den Namen „My Settings“. Wenn der Einstellungspunkt ausgewählt ist, wird die Beschreibung **Various Options**(Verschiedene Optionen) angezeigt. Der Name und die Beschreibung des Einstellungspunkts stammen aus den lokalisierten Zeichenfolgenressourcen.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Optionsseite](../extensibility/creating-an-options-page.md)   
 [VSSDK-Beispiele](../misc/vssdk-samples.md)   
 [VSPackage-Status](../misc/vspackage-state.md)   
 [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)