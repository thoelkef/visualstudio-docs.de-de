---
title: Zugriff auf gespeicherte Schriftart- und Farbeinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bab850a6943268581035336a923232377e6489f2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843677"
---
# <a name="accessing-stored-font-and-color-settings"></a>Zugriff auf gespeicherte Schriftart- und Farbeinstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE) speichert die geänderte Einstellungen für Schriftarten und Farben in der Registrierung. Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle, um diese Einstellungen zuzugreifen.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Zum Initiieren der Statuspersistenz von Schriftarten und Farben  
 Schriftart und Farbinformationen befindet sich im am folgenden Registrierungsspeicherort nach Kategorie: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio-Version >* \FontAndColors\\  *\<CategoryGUID >*], wobei  *\<CategoryGUID >* ist die Kategorie-GUID.  
  
 Aus diesem Grund um Persistenz zu initiieren, muss eine VSPackage:  
  
-   Abrufen einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle durch den Aufruf `QueryService` für den globalen Dienstanbieter.  
  
     `QueryService` muss aufgerufen werden, mithilfe einer Dienst-ID-Argument `SID_SVsFontAndColorStorage` und ID Schnittstellenargument `IID_IVsFontAndColorStorage`.  
  
-   Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> Methode zum Öffnen einer Kategorie unter Verwendung der Kategorie-GUID und eine moduskennzeichnung als Argumente beibehalten werden sollen.  
  
     Der Modus, gemäß der `fFlags` Argument wird aus Werten erstellt die <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> Enumeration. In diesem Modus steuert:  
  
    -   Die Einstellungen, die über zugegriffen werden können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle.  
  
    -   Alle Einstellungen oder nur diejenigen, die Benutzer zu ändern, und sind abrufbar, bis, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle.  
  
    -   Die Art und Weise der Weitergabe von Änderungen an den benutzereinstellungen.  
  
    -   Das Format der RGB-Werte, die verwendet werden.  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Verwenden von Schriftarten und Farben Statuspersistenz  
 Beibehalten von Schriftarten und Farben umfasst:  
  
- Synchronisieren die IDE-Einstellungen, mit Einstellungen, die in der Registrierung gespeichert.  
  
- Weiter Informationen zur Änderung der Registrierung.  
  
- Festlegen und Abrufen von Einstellungen, die in der Registrierung gespeichert.  
  
  Synchronisieren die speichereinstellung mit dem IDE-Einstellungen ist größtenteils transparent. Die zugrunde liegenden IDE schreibt automatisch die aktualisierte Einstellungen für **Anzeigeelemente** um die Registrierungseinträge der Kategorien.  
  
  Wenn eine bestimmte Kategorie von mehreren VSPackages gemeinsam nutzen, eine VSPackage sollte erforderlich sein, dass die Ereignisse generiert werden, wenn Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle werden verwendet, um gespeicherte registrierungseinstellungen ändern.  
  
  Standardmäßig ist das Generieren nicht aktiviert. Zum Generieren von Ereignissen zu aktivieren, muss eine Kategorie mit geöffnet sein <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Dies bewirkt, dass die IDE aufrufen, die entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> Methode, die eine VSPackage implementiert.  
  
> [!NOTE]
>  Änderungen über die **Schriftart- und Farbeinstellungen** Eigenschaftenseite Generieren von Ereignissen, die unabhängig von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Können Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Schnittstelle, um zu bestimmen, ob ein Update der zwischengespeicherten Einstellungen von Schriftart und Farbe erforderlich ist, vor dem Aufrufen der Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Klasse.  
  
### <a name="storing-and-retrieving-information"></a>Speichern und Abrufen von Informationen  
 Rufen Sie zum Abrufen oder konfigurieren die Informationen, die ein Benutzer für ein benanntes Display-Element in einem geöffneten Kategorie ändern können, VSPackages die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> Methoden.  
  
 Informationen zu Schriftart Attribute für eine bestimmte Kategorie, mithilfe abgerufen werden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> Methoden.  
  
> [!NOTE]
>  Die `fFlags` Argument, das an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> Methode, wenn diese Kategorie geöffnet wurde, definiert das Verhalten der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> Methoden. Diese Methoden nur Informationen ausgegeben werden Aboutdisplay Itemsthat standardmäßig wurden geändert. Allerdings wird eine Kategorie mit geöffnet die <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> zu kennzeichnen, beide aktualisiert und können unverändert Anzeigeelemente zugegriffen werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.  
  
 Nur in der Standardeinstellung geändert **Anzeigeelemente** Informationen werden in der Registrierung gespeichert. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle kann nicht verwendet werden, um alle Einstellungen für Schriftarten und Farben abgerufen werden.  
  
> [!NOTE]
>  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> Methoden zurückgeben REGDB_E_KEYMISSING, (0x80040152L), wenn Sie diese verwenden, zum Abrufen von Informationen zu unverändert **Anzeigeelemente**.  
  
 Die Einstellungen aller **Anzeigeelemente** in einer bestimmten **Kategorie** erhalten Sie, indem Sie mithilfe der Methoden der der `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementieren benutzerdefinierter Kategorien und Anzeigeelemente](../extensibility/implementing-custom-categories-and-display-items.md)

