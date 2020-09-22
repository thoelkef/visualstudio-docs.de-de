---
title: Implementieren von benutzerdefinierten Kategorien und Anzeigen von Elementen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 474d5c66507b56bea609568b6acfe9f5eff75e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840965"
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementieren von benutzerdefinierten Kategorien und Anzeigeelementen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein VSPackage kann die Schriftarten und Farben seines Texts in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) über benutzerdefinierte Kategorien und Anzeigeelemente bereitstellen.  
  
 Benutzerdefinierte Kategorien und Anzeigeelemente befinden sich auf der Eigenschaften Seite **Schriftarten und Farben** . Um die Eigenschaften Seite **Schriftarten und Farben** zu öffnen, klicken Sie **im Menü Extras** auf **Optionen**. Erweitern Sie **Umgebung** , und klicken Sie dann auf **Schriftarten und Farben**.  
  
 Bei Verwendung dieses Mechanismus müssen VSPackages die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> -Schnittstelle und die zugehörigen Schnittstellen implementieren.  
  
 Im Prinzip kann dieser Mechanismus verwendet werden, um alle vorhandenen **Anzeigeelemente** und die **Kategorien** zu ändern, in denen Sie enthalten sind. Es sollte jedoch nicht verwendet werden, um den **Text Editor Category** oder seine **Anzeigeelemente**zu ändern. Weitere Informationen finden Sie unter [Übersicht über Schriftart und Farben](../extensibility/font-and-color-overview.md).  
  
 Ein VSPackage muss Folgendes durchführen, um benutzerdefinierte **Kategorien** oder **Elemente anzuzeigen**:  
  
- Erstellen oder identifizieren Sie Kategorien in der Registrierung.  
  
   Diese Informationen werden von der IDE-Implementierung der **Schriftarten und Farben** -Eigenschaften Seite verwendet, um den Dienst, der eine bestimmte Kategorie unterstützt, ordnungsgemäß abzufragen.  
  
- Erstellen oder identifizieren Sie Gruppen (optional) in der Registrierung.  
  
   Es kann sinnvoll sein, eine Gruppe zu definieren, die die Union von zwei oder mehr Kategorien darstellt. Wenn eine Gruppe definiert ist, führt die IDE automatisch Unterkategorien zusammen und verteilt Anzeigeelemente in der Gruppe.  
  
- Implementieren Sie IDE-Unterstützung.  
  
- Bearbeiten von Schriftart-und Farbänderungen.  
  
  Weitere Informationen finden Sie unter [zugreifen auf gespeicherte Schriftart-und Farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>So erstellen oder identifizieren Sie Kategorien  
  
- Erstellen Sie einen besonderen Typ von kategorieregistrierungs Eintrag unter [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \fontandcolors \\ `<Category>` ].  
  
   *\<Category>* der nicht lokalisierte Name der Kategorie.  
  
- Füllen Sie die Registrierung mit zwei Werten auf:  
  
  |Name|Typ|Daten|BESCHREIBUNG|  
  |----------|----------|----------|-----------------|  
  |Category|REG_SZ|GUID|Eine GUID, die zur Identifizierung der Kategorie erstellt wird.|  
  |Paket|REG_SZ|GUID|Die GUID des VSPackage-Dienstanbieter, der die Kategorie unterstützt.|  
  
  Der in der Registrierung angegebene Dienst muss eine Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> für die entsprechende Kategorie bereitstellen.  
  
## <a name="to-create-or-identify-groups"></a>So erstellen oder identifizieren Sie Gruppen  
  
- Erstellen Sie einen besonderen Typ von kategorieregistrierungs Eintrag unter [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \fontandcolors \\ *\<group>* ].  
  
   *\<group>* der nicht lokalisierte Name der Gruppe.  
  
- Füllen Sie die Registrierung mit zwei Werten auf:  
  
  |Name|Typ|Daten|BESCHREIBUNG|  
  |----------|----------|----------|-----------------|  
  |Category|REG_SZ|GUID|Eine GUID, die zum Identifizieren der Gruppe erstellt wurde.|  
  |Paket|REG_SZ|GUID|Die GUID des Dienstanbieter, der die Kategorie unterstützt.|  
  
  Der in der Registrierung angegebene Dienst muss `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` für die zugehörige Gruppe eine Implementierung von bereitstellen.  
  
## <a name="to-implement-ide-support"></a>So implementieren Sie IDE-Unterstützung  
  
- Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A> Sie, das entweder eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Schnittstelle oder eine `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` Schnittstelle zur IDE für jede bereitgestellte **Kategorie** oder Gruppen-GUID zurückgibt.  
  
- Für jede unterstützte **Kategorie** implementiert ein VSPackage eine separate Instanz der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Schnittstelle.  
  
- Die durch implementierten Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> müssen der IDE Folgendes bereitstellen:  
  
  - Listen der **Anzeigeelemente** in der **Kategorie.**  
  
  - Lokalisierbare Namen für **Anzeigeelemente**.  
  
  - Anzeigen von Informationen für jedes Mitglied der **Kategorie**.  
  
  > [!NOTE]
  > Jede **Kategorie** muss mindestens ein **Anzeigeelement**enthalten.  
  
- Die IDE verwendet die- `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` Schnittstelle, um eine Union mehrerer Kategorien zu definieren.  
  
   Die-Implementierung stellt die IDE mit bereit:  
  
  - Eine Liste der **Kategorien** , aus denen eine bestimmte Gruppe besteht.  
  
  - Zugriff auf Instanzen von, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> die jede **Kategorie** innerhalb der Gruppe unterstützen.  
  
  - Lokalisierbare Gruppennamen.  
  
- Aktualisieren der IDE:  
  
   Die IDE speichert Informationen zu **Schriftart-und Farb** Einstellungen zwischen. Daher ist es ratsam, nach jeder Änderung der **Schriftart-und Farb** Konfiguration der IDE sicherzustellen, dass der Cache auf dem neuesten Stand ist.  
  
  Das Aktualisieren des Caches erfolgt über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> -Schnittstelle und kann global oder nur für ausgewählte Elemente ausgeführt werden.  
  
## <a name="to-handle-font-and-color-changes"></a>So behandeln Sie Schriftart-und Farbänderungen  
 Um die farbliche Farbgebung von Text, den ein VSPackage anzeigt, ordnungsgemäß zu unterstützen, muss der für das VSPackage unterstützende Farb Erfassungs Dienst auf die vom Benutzer initiierten Änderungen reagieren, die über die Eigenschaften Seite **Schriftarten und Farben** vorgenommen wurden. Ein VSPackage führt dies wie folgt aus:  
  
- Behandeln von IDE-generierten Ereignissen durch Implementieren der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> Schnittstelle.  
  
     Die IDE Ruft die entsprechende Methode auf, die auf die Benutzer Änderungen der Seite **Schriftarten und Farben** folgt. Beispielsweise wird die-Methode aufgerufen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> Wenn eine neue Schriftart ausgewählt wird.  
  
     - oder -  
  
- Abrufen der IDE auf Änderungen.  
  
     Dies kann über die vom System implementierte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle erfolgen. Obwohl die-Methode in erster Linie für die Unterstützung der Persistenz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> verwendet wird, kann die **Display items**-Methode zum Abrufen von Schriftart-und Farbinformationen für Weitere Informationen finden Sie unter [zugreifen auf gespeicherte Schriftart-und Farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    > Um sicherzustellen, dass die vom Abruf abzurufenden Ergebnisse richtig sind, kann es hilfreich sein, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> -Schnittstelle zu verwenden, um zu bestimmen, ob vor dem Aufrufen der Abruf Methoden der Schnittstelle eine Cache Leerung und ein Update erforderlich sind <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Informationen zu Schriftart und Farbe für die farbliche Kennzeichnung von Text](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Zugreifen auf gespeicherte Schriftart-und Farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Gewusst wie: Zugreifen auf die integrierten Schriftarten und das Farbschema](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Übersicht: Schriftart und Farben](../extensibility/font-and-color-overview.md)
