---
title: Implementieren benutzerdefinierte Kategorien und Anzeigeelemente | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f03dbae8b320161705c50da06d605cfc335074cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementieren benutzerdefinierte Kategorien und Anzeigeelemente
Eine VSPackage bieten Kontrolle über die Schriftarten und Farben der Text der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) durch benutzerdefinierte Kategorien und Anzeigeelemente.  
  
 Benutzerdefinierte Kategorien und Anzeigeelementen befinden sich auf die **Schriftarten und Farben** Eigenschaftenseite. So öffnen die **Schriftarten und Farben** Eigenschaftenseite auf die **Tools** Menü klicken Sie auf **Optionen**. Erweitern Sie **Umgebung** , und klicken Sie dann auf **Schriftarten und Farben**.  
  
 VSPackages müssen implementieren, wenn Sie diesen Mechanismus verwenden, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> Schnittstelle und die zugehörigen Schnittstellen.  
  
 Im Prinzip dieser Mechanismus verwendet werden kann, so ändern Sie alle vorhandenen **Einblenden von Elementen** und die **Kategorien** , die sie enthalten. Sollte jedoch nicht so ändern Sie verwendet werden die **Text EditorCategory** oder den zugehörigen **Einblenden von Elementen**. Weitere Informationen finden Sie unter [Schriftart und Farbe (Übersicht)](../extensibility/font-and-color-overview.md).  
  
 Zum Implementieren von benutzerdefinierten **Kategorien** oder **Einblenden von Elementen**, ein VSPackage muss:  
  
-   Erstellen Sie oder identifizieren Sie der Kategorien in der Registrierung.  
  
     Die IDE-Implementierung von der **Schriftarten und Farben** Eigenschaftenseite anhand dieser Informationen ordnungsgemäß für die Unterstützung einer bestimmten Kategorie Dienst abzufragen.  
  
-   Erstellen Sie oder identifizieren Sie Gruppen, die in der Registrierung (optional).  
  
     Möglicherweise empfiehlt es sich zum Definieren einer Gruppe, die die Vereinigung der zwei oder mehrere Kategorien darstellt. Wenn eine Gruppe definiert ist, wird die IDE automatisch Unterkategorien zusammengeführt und verteilt die Elemente innerhalb der Gruppe anzeigen.  
  
-   Implementieren Sie IDE-Unterstützung.  
  
-   Behandeln Sie Schriftart- und farbänderungen an.  
  
 Informationen finden Sie unter [Zugriff auf gespeicherte Schriftart und Farbe Einstellungen](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Zum Erstellen oder Identifizieren von Kategorien  
  
-   Erstellen Sie eine besondere Art von Kategorie-Registrierungseintrags unter [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio-Version >*\FontAndColors\\`<Category>`]  
  
     *\<Kategorie >* der nicht lokalisierte Name der Kategorie.  
  
-   Füllen Sie die Registrierung mit zwei Werten:  
  
    |Name|Typ|Daten|Beschreibung|  
    |----------|----------|----------|-----------------|  
    |Kategorie|REG_SZ|GUID|Eine GUID erstellt, um die Kategorie zu identifizieren.|  
    |Package|REG_SZ|GUID|Die GUID des VSPackage-Diensts, der die Kategorie unterstützt.|  
  
 Der Dienst in der Registrierung angegebene muss eine Implementierung bereitstellen <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> für die entsprechende Kategorie.  
  
## <a name="to-create-or-identify-groups"></a>Zum Erstellen oder identifizieren Gruppen  
  
-   Erstellen Sie eine besondere Art von Kategorie-Registrierungseintrags unter [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio-Version >*\FontAndColors\\  *\<Gruppe >*]  
  
     *\<Gruppe >* der nicht lokalisierte Name der Gruppe.  
  
-   Füllen Sie die Registrierung mit zwei Werten:  
  
    |Name|Typ|Daten|Beschreibung|  
    |----------|----------|----------|-----------------|  
    |Kategorie|REG_SZ|GUID|Eine GUID, die zur Identifizierung der Gruppe erstellt wird.|  
    |Package|REG_SZ|GUID|Die GUID des Diensts, der die Kategorie unterstützt.|  
  
 Der Dienst in der Registrierung angegebene muss eine Implementierung bereitstellen `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` für die entsprechende Gruppe.  
  
## <a name="to-implement-ide-support"></a>IDE-Unterstützung implementieren  
  
-   Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, womit entweder ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Schnittstelle oder eine `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` Schnittstelle, um die IDE für die einzelnen **Kategorie** oder die Gruppe der angegebenen GUID.  
  
-   Für jede **Kategorie** unterstützt, die eine VSPackage implementiert eine separate Instanz von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Schnittstelle.  
  
-   Die Methoden implementiert, über <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> müssen die IDE mit bereitstellen:  
  
    -   Listen von **Einblenden von Elementen** in die **Kategorie.**  
  
    -   Lokalisierbare Namen für **Einblenden von Elementen**.  
  
    -   Anzeigen von Informationen für jedes Element der **Kategorie**.  
  
    > [!NOTE]
    >  Jede **Kategorie** muss mindestens ein enthalten **Anzeigeelements**.  
  
-   Die IDE verwendet die `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` Schnittstelle, um eine Union von verschiedene Kategorien definieren.  
  
     Die Implementierung stellt die IDE mit:  
  
    -   Eine Liste mit den **Kategorien** , die eine bestimmte Gruppe bilden.  
  
    -   Zugriff auf Instanzen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> unterstützen jede **Kategorie** innerhalb der Gruppe.  
  
    -   Lokalisierbare Gruppennamen.  
  
-   Die IDE werden aktualisiert:  
  
     Die IDE speichert Informationen zu **Schriftart und Farbe** Einstellungen. Aus diesem Grund nach jeder Änderung der IDE **Schriftart und Farbe** Konfiguration, es wird empfohlen, um sicherzustellen, dass der Cache auf dem neuesten Stand ist.  
  
 Aktualisieren des Caches erfolgt über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> -Schnittstelle und ausgeführten global oder nur auf ausgewählten Elemente werden können.  
  
## <a name="to-handle-font-and-color-changes"></a>Behandeln von Schriftart und Farbe ändert.  
 Um die farbliche Kennzeichnung von Text ordnungsgemäß zu unterstützen, die eine VSPackage anzeigt, muss antwortet der unterstützen des VSPackages farbliche Kennzeichnung-Dienst auf die Benutzerinitiierte Änderungen, die über die **Schriftarten und Farben** Seite "Eigenschaften". Eine VSPackage geschieht dies durch:  
  
-   Behandlung von Ereignissen IDE generiert durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> Schnittstelle.  
  
     Die IDE Ruft die entsprechende Methode, die folgenden Änderungen durch den Benutzer von der **Schriftarten und Farben** Seite. Beispielsweise ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> Methode, wenn eine neue Schriftart ausgewählt ist.  
  
     - oder -   
  
-   Abrufen der IDE nach Änderungen an.  
  
     Dies kann erfolgen über die vom System implementierte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle. Obwohl in erster Linie für die Unterstützung von Persistenz, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> Methode kann verwendet werden, um die Schriftart und Farbe zu erhalten **Einblenden von Elementen**. Weitere Informationen finden Sie unter [Zugriff auf gespeicherte Schriftart und Farbe Einstellungen](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    >  Um sicherzustellen, dass die Ergebnisse durch Abruf richtig sind, möglicherweise empfiehlt es sich um verwenden die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Schnittstelle, um zu bestimmen, ob ein Cache leeren und Update benötigt werden, vor dem Aufrufen der Abrufmethoden, der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Abrufen von Informationen zur Schriftart und Farbe für die farbliche Kennzeichnung von Text](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Zugriff auf gespeicherte Schriftart- und Farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Vorgehensweise: Zugriff auf die integrierten Schriftarten und Farbschemas](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Schriftart und Farbe (Übersicht)](../extensibility/font-and-color-overview.md)