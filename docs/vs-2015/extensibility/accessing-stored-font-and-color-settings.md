---
title: Zugreifen auf gespeicherte Schriftart-und Farbeinstellungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821833"
---
# <a name="accessing-stored-font-and-color-settings"></a>Zugriff auf gespeicherte Schriftart- und Farbeinstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) speichert geänderte Einstellungen für Schriftarten und Farben in der Registrierung. Sie können die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle verwenden, um auf diese Einstellungen zuzugreifen.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>So initiieren Sie die Zustands Persistenz von Schriftarten und Farben  
 Schriftart-und Farbinformationen werden nach Kategorie im folgenden Registrierungs Speicherort gespeichert: [hkcu\software\microsoft \Visual Studio \\ *\<Visual Studio version>* \fontandcolors \\ *\<CategoryGUID>* ], wobei *\<CategoryGUID>* die Kategorie-GUID ist.  
  
 Um die Persistenz zu initiieren, muss ein VSPackage daher Folgendes ausführen:  
  
- Rufen Sie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle ab, indem Sie für `QueryService` den globalen Dienstanbieter aufrufen.  
  
     `QueryService` muss mithilfe eines Dienst-ID-Arguments von `SID_SVsFontAndColorStorage` und eines Schnittstellen-ID-Arguments von aufgerufen werden `IID_IVsFontAndColorStorage` .  
  
- Verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> -Methode, um eine Kategorie zu öffnen, die beibehalten werden soll, indem Sie die GUID der Kategorie und ein modusflag als Argumente verwenden.  
  
  Der Modus, der durch das-Argument angegeben wird `fFlags` , wird aus Werten in der- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> Enumeration erstellt. Dieser Modus steuert Folgendes:  

  - Die Einstellungen, auf die über die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle zugegriffen werden kann.  

  - Entweder alle Einstellungen oder nur diejenigen, die Benutzer ändern und die über die-Schnittstelle abgerufen werden können <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  

  - Die Art der Weitergabe der Änderungen an Benutzereinstellungen.  

  - Das Format der verwendeten Farbwerte.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>So verwenden Sie die Zustands Persistenz von Schriftarten und Farben  
 Die Beibehaltung von Schriftarten und Farben umfasst Folgendes:  
  
- Synchronisieren der IDE-Einstellungen mit Einstellungen, die in der Registrierung gespeichert sind.  
  
- Informationen zur Registrierungs Änderung werden weitergegeben.  
  
- Festlegen und Abrufen von Einstellungen, die in der Registrierung gespeichert sind.  
  
  Die Synchronisierung der Speichereinstellung mit den IDE-Einstellungen ist größtenteils transparent. Die zugrunde liegende IDE schreibt automatisch aktualisierte Einstellungen für **Anzeigeelemente** in die Registrierungseinträge von Kategorien.  
  
  Wenn mehrere VSPackages eine bestimmte Kategorie gemeinsam nutzen, muss ein VSPackage erfordern, dass Ereignisse generiert werden, wenn die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle zum Ändern gespeicherter Registrierungs Einstellungen verwendet werden.  
  
  Die Ereignis Generierung ist standardmäßig nicht aktiviert. Um die Ereignis Generierung zu aktivieren, muss eine Kategorie mithilfe von geöffnet werden <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> . Dies bewirkt, dass die IDE die entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> Methode aufruft, die von einem VSPackage implementiert wird.  
  
> [!NOTE]
> Änderungen auf der Eigenschaften Seite **Schriftart und Farbe** generieren Ereignisse, die unabhängig von sind <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> -Schnittstelle verwenden, um zu bestimmen, ob ein Update der zwischengespeicherten Schriftart-und Farbeinstellungen erforderlich ist, bevor Sie die Methoden der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Klasse aufrufen.  
  
### <a name="storing-and-retrieving-information"></a>Speichern und Abrufen von Informationen  
 Um Informationen zu erhalten oder zu konfigurieren, die ein Benutzer für ein benanntes Anzeigeelement in einer geöffneten Kategorie ändern kann, rufen VSPackages die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> -Methode und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> Methode auf.  
  
 Informationen zu Schriftart Attributen für eine bestimmte Kategorie werden mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> -Methode und der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> Methode abgerufen.  
  
> [!NOTE]
> Das `fFlags` Argument, das an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> -Methode beim Öffnen dieser Kategorie übermittelt wird, definiert das Verhalten der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> -Methode und der-Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> . Standardmäßig geben diese Methoden nur Informationen zurück, die sich geändert haben. Wenn eine Kategorie jedoch mit dem-Flag geöffnet wird <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> , kann auf sowohl aktualisierte als auch unveränderte Anzeigeelemente von <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> und zugegriffen werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> .  
  
 Standardmäßig werden nur geänderte **Anzeige** Element Informationen in der Registrierung gespeichert. Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle kann nicht zum Abrufen aller Einstellungen für Schriftarten und Farben verwendet werden.  
  
> [!NOTE]
> Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> -Methode und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> Methode geben REGDB_E_KEYMISSING zurück (0x80040152l), wenn Sie Sie zum Abrufen von Informationen über unveränderte **Anzeigeelemente**verwenden.  
  
 Die Einstellungen aller **Anzeigeelemente** in einer bestimmten **Kategorie** können mithilfe der Methoden der-Schnittstelle abgerufen werden `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` .  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementieren benutzerdefinierter Kategorien und Anzeigeelemente](../extensibility/implementing-custom-categories-and-display-items.md)
