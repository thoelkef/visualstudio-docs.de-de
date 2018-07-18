---
title: Zugriff auf gespeicherte Schriftart- und Farbeinstellungen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1280555a2b8a293fcdd0f86891a1d198ef3c99d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105792"
---
# <a name="accessing-stored-font-and-color-settings"></a>Zugriff auf gespeicherte Schriftart- und Farbeinstellungen
Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) Speichert geänderte Einstellungen für Schriftarten und Farben in der Registrierung. Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle, um diese Einstellungen zuzugreifen.

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>So initiieren Sie Statuspersistenz von Schriftarten und Farben
 Schriftart und Farbe Informationen werden nach Kategorie im folgenden Registrierungsschlüssel gespeichert: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio-Version >* \FontAndColors\\  *\<CategoryGUID >*], wobei  *\<CategoryGUID >* Kategorie-GUID ist.

 Aus diesem Grund, um Persistenz zu initiieren, muss eine VSPackage:

-   Abrufen einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle durch den Aufruf `QueryService` für den globalen Service-Anbieter.

     `QueryService` muss aufgerufen werden, mithilfe des Dienst-ID-Argument der `SID_SVsFontAndColorStorage` und ID Schnittstellenargument `IID_IVsFontAndColorStorage`.

-   Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> Methode, um eine Kategorie, die beibehalten werden, mithilfe der Kategorie-GUID und einem moduskennzeichnung als Argumente zu öffnen.

     Der vom angegebenen Modus der `fFlags` Argument wird erstellt, anhand der Werte in der <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> Enumeration. In diesem Modus steuert:

    -   Die Einstellungen, die über zugegriffen werden können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle.

    -   Alle Einstellungen oder nur die Einstellungen, die Benutzer ändern und die abrufbar, bis, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle.

    -   Die Art und Weise der Weitergabe der Änderungen an der benutzereinstellungen.

    -   Das Format der Farbwerte, die verwendet werden.

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Verwenden von Schriftarten und Farben Statuspersistenz
 Beibehalten von Schriftarten und Farben umfasst:

-   Synchronisieren die IDE-Einstellungen mit Einstellungen, die in der Registrierung gespeichert.

-   Weiter Informationen zum Ändern der Registrierung.

-   Das Festlegen und Abrufen von Einstellungen, die in der Registrierung gespeichert.

 Synchronisieren die Speicher-Einstellung mit dem IDE-Einstellungen ist weitestgehend transparent. Die zugrunde liegenden IDE schreibt automatisch die aktualisierte Einstellungen für **Anzeigeelementen** um die Registrierungseinträge der Kategorien.

 Mehrere VSPackages eine bestimmte Kategorie freigeben, sollten eine VSPackage erfordern, die Ereignisse generiert werden bei der Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle werden verwendet, um gespeicherte registrierungseinstellungen ändern.

 Standardmäßig ist die Generierung von Ereignissen nicht aktiviert. Um die Generierung von Ereignissen zu aktivieren, muss eine Kategorie mit geöffnet werden <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Öffnen eine Kategorie bewirkt, dass die IDE rufen Sie die entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> Methode, die eine VSPackage implementiert.

> [!NOTE]
>  Änderungen, die über die **Schriftart und Farbe** Eigenschaftenseite generieren Ereignisse unabhängig von <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Können Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Schnittstelle, um zu bestimmen, ob ein Update der zwischengespeicherten Einstellungen von Schriftart und Farbe erforderlich ist, vor dem Aufrufen der Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Klasse.

### <a name="storing-and-retrieving-information"></a>Speichern und Abrufen von Informationen
 Um zu erhalten, oder konfigurieren Sie die Informationen, die ein Benutzer für eine benannte Anzeigeelements in einer geöffneten Kategorie ändern können, VSPackages Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> Methoden.

 Informationen zur Schriftart Attribute für eine bestimmte Kategorie, mithilfe abgerufen wird der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> Methoden.

> [!NOTE]
>  Die `fFlags` Argument zu übergeben der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> Methode beim Öffnen der entsprechenden Kategorie definiert das Verhalten der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> Methoden. Standardmäßig werden Informationen über Anzeigeelemente, die geändert wurden nur in diesen Methoden zurück. Allerdings wird eine Kategorie mit geöffnet der <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> kennzeichnen, beide aktualisiert und unverändert Anzeigeelementen zugegriffen werden können, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.

 Nur in der Standardeinstellung geändert **Anzeigeelementen** Informationen in der Registrierung gespeichert ist. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle kann nicht verwendet werden, um alle Einstellungen für Schriftarten und Farben abgerufen werden.

> [!NOTE]
>  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> -Methoden zurückgeben REGDB_E_KEYMISSING (0x80040152L), wenn Sie sie zum Abrufen von Informationen verwenden zu unverändert **Anzeigeelementen**.

 Die Einstellungen aller **Anzeigeelementen** in einer bestimmten **Kategorie** erhalten Sie, indem Sie mit den Methoden der der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Schnittstelle.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [Implementieren benutzerdefinierte Kategorien und Anzeigeelemente](../extensibility/implementing-custom-categories-and-display-items.md)