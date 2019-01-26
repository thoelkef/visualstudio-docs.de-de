---
title: Implementieren von benutzerdefinierten Kategorien und Anzeigeelemente | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81deac9f46c03cac997f555f817bba5831409bca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54968699"
---
# <a name="implement-custom-categories-and-display-items"></a>Implementieren Sie benutzerdefinierte Kategorien und Einblenden von Elementen
Eine VSPackage kann Kontrolle über die Schriftarten und Farben des Texts zum Bereitstellen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) über den benutzerdefinierten Kategorien und Anzeigeelemente.

 Benutzerdefinierte Kategorien und Anzeigeelemente befinden sich auf die **Schriftarten und Farben** Eigenschaftenseite. Zum Öffnen der **Schriftarten und Farben** Eigenschaftenseite auf die **Tools** Menü klicken Sie auf **Optionen**. Erweitern Sie **Umgebung** , und klicken Sie dann auf **Schriftarten und Farben**.

 Wenn Sie diesen Mechanismus verwenden zu können, muss die VSPackages implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> -Schnittstelle und die zugehörigen Schnittstellen.

 Dieser Mechanismus kann im Prinzip so ändern Sie alle vorhandenen verwendet werden **Anzeigeelemente** und **Kategorien** , die diese enthalten sind. Allerdings es sollte nicht verwendet werden, so ändern Sie die **Text EditorCategory** oder den zugehörigen **Elemente anzeigen**. Weitere Informationen finden Sie unter [Übersicht über die Schriftart- und farbeinstellungen](../extensibility/font-and-color-overview.md).

 Zum Implementieren von benutzerdefinierten **Kategorien** oder **Anzeigeelemente**, ein VSPackage muss:

- Erstellen Sie oder identifizieren Sie die Kategorien in der Registrierung.

   Die IDE Implementierung der **Schriftarten und Farben** Eigenschaftenseite anhand dieser Informationen ordnungsgemäß für den Dienst, der eine angegebene Kategorie unterstützt Abfragen.

- Erstellen Sie oder identifizieren Sie Gruppen, die in der Registrierung (optional).

   Es kann hilfreich sein, eine Gruppe definieren, die die Gesamtmenge von zwei oder mehr Kategorien darstellt. Wenn eine Gruppe definiert ist, wird die IDE automatisch zusammengeführt Unterkategorien und verteilt die Elemente in der Gruppe anzeigen.

- Implementieren Sie die IDE-Unterstützung.

- Behandeln Sie Schriftart- und farbänderungen an.

  Weitere Informationen finden Sie unter [gespeicherte Schriftart-und farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md).

## <a name="to-create-or-identify-categories"></a>Zum Erstellen oder Identifizieren von Kategorien

- Erstellen Sie eine besondere Art von Kategorie-Registrierungseintrag unter *["HKLM\Software\Microsoft" \Visual Studio\\*\<Visual Studio-Version >*\FontAndColors\\ `<Category>`]*

   *\<Kategorie >* ist der nicht lokalisierte Name der Kategorie.

- Füllen Sie die Registrierung mit zwei Werten:

  |name|Typ|Daten|Beschreibung|
  |----------|----------|----------|-----------------|
  |Kategorie|REG_SZ|GUID|Eine GUID zum Identifizieren der Kategorie erstellt.|
  |Package|REG_SZ|GUID|Die GUID des VSPackage-Diensts, der die Kategorie unterstützt.|

  Der Dienst in der Registrierung angegebene muss eine Implementierung bereitstellen <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> für die entsprechende Kategorie.

## <a name="to-create-or-identify-groups"></a>Zum Erstellen oder Identifizieren von Gruppen

- Erstellen Sie eine besondere Art von Kategorie-Registrierungseintrag unter *["HKLM\Software\Microsoft" \Visual Studio\\*\<Visual Studio-Version >*\FontAndColors\\*  \<Gruppe >*]*

   *\<Gruppe >* der nicht lokalisierten Namen der Gruppe ist.

- Füllen Sie die Registrierung mit zwei Werten:

  |name|Typ|Daten|Beschreibung|
  |----------|----------|----------|-----------------|
  |Kategorie|REG_SZ|GUID|Eine GUID, die zur Identifizierung der Gruppe erstellt wird.|
  |Package|REG_SZ|GUID|Die GUID des Diensts, der die Kategorie unterstützt.|

  Der Dienst in der Registrierung angegebene muss eine Implementierung bereitstellen <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> für die entsprechende Gruppe.

## <a name="to-implement-ide-support"></a>Zum Implementieren von IDE-Unterstützung

- Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, womit entweder ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Schnittstelle oder ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Schnittstelle, um die IDE für die einzelnen **Kategorie** oder eine Gruppe von angegebenen GUID.

- Für jede **Kategorie** unterstützt, die eine VSPackage implementiert eine separate Instanz von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Schnittstelle.

- Die Methoden implementiert, über <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> müssen die IDE mit bereitstellen:

  -   Listen von **Anzeigeelemente** in die **Kategorie.**

  -   Lokalisierbaren Namen für die **Anzeigeelemente**.

  -   Anzeigen von Informationen für jeden Member des **Kategorie**.

  > [!NOTE]
  >  Jede **Kategorie** muss mindestens einen enthalten **Anzeigeelement**.

- Die IDE verwendet das <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Schnittstelle, um eine Kombination aus verschiedenen Kategorien zu definieren.

   Die Implementierung bietet die IDE mit:

  -   Eine Liste mit den **Kategorien** , die eine bestimmte Gruppe enthalten.

  -   Zugriff auf Instanzen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> unterstützen jeweils **Kategorie** innerhalb der Gruppe.

  -   Lokalisierbare Gruppennamen.

- Aktualisieren die IDE:

   Die IDE speichert Informationen über **Schriftart- und Farbeinstellungen** Einstellungen. Aus diesem Grund nach jeder Änderung der IDE **Schriftart- und Farbeinstellungen** Konfiguration, es wird empfohlen, um sicherzustellen, dass der Cache auf dem neuesten Stand ist.

  Aktualisieren des Caches erfolgt über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Schnittstelle und kann ausgeführt global oder nur für ausgewählte Elemente.

## <a name="to-handle-font-and-color-changes"></a>Behandeln von Schriftart- und farbänderungen an
 Um die farbliche Kennzeichnung von Text ordnungsgemäß zu unterstützen, die eine VSPackage anzeigt, der Farbgebung-Dienst unterstützt das VSPackage muss auf Antworten, die vom Benutzer initiierte Änderungen, die über die **Schriftarten und Farben** Seite "Eigenschaften". Eine VSPackage erledigt dies durch:

-   Behandeln von Ereignissen IDE generiert wurde durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> Schnittstelle.

     Die IDE Ruft die entsprechende Methode, die folgenden Änderungen durch den Benutzer von der **Schriftarten und Farben** Seite. Beispielsweise ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> Methode, wenn eine neue Schriftart ausgewählt ist.

     - oder - 

-   Abrufen der IDE Änderungen an.

     Dies kann erfolgen über das System implementierter <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle. Zwar in erster Linie für die Unterstützung von Persistenz der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> Methode kann verwendet werden, zum Abrufen von Informationen von Schriftart- und farbeinstellungen für **Anzeigeelemente**. Weitere Informationen finden Sie unter [gespeicherte Schriftart-und farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md).

    > [!NOTE]
    >  Um sicherzustellen, dass die Ergebnisse der Abfrage korrekt sind, es kann hilfreich sein, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Schnittstelle, um zu bestimmen, ob eine Entleerung des Cache und die Updates erforderlich sind, vor dem Aufrufen der Abrufmethoden, der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- [Abrufen von Informationen von Schriftart- und farbanbieters für die farbliche Kennzeichnung von text](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Zugriff auf gespeicherte Schriftart- und farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md)
- [Vorgehensweise: Zugriff auf die integrierten Schriftarten und Farbschemas](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)
- [Übersicht über die Schriftart und Farbe](../extensibility/font-and-color-overview.md)