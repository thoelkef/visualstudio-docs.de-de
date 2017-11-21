---
title: 'Vorgehensweise: Installieren Sie ein Quellcodeverwaltungs-Plug-in | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab02b65e4a40f15da857038a45d9bcc2b88b1b83
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-install-a-source-control-plug-in"></a>Vorgehensweise: Installieren Sie ein Quellcodeverwaltungs-Plug-in
Erstellen ein Quellcodeverwaltungs-Plug-in umfasst drei Schritte:  
  
1.  Erstellen Sie eine DLL-Datei mit den Funktionen, die in der Source Control-Plug-in-API-Referenz dieser Dokumentation im Abschnitt definiert.  
  
2.  Implementieren Sie die Datenquellen-Steuerelement-Plug-in-API-Funktionen. Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Aufrufe, Dialogfeldern und Schnittstellen verfügbar machen aus dem plug-in.  
  
3.  Registrieren Sie die DLL, indem Sie die entsprechenden Registrierungseinträge.  
  
## <a name="integration-with-visual-studio"></a>Integration in Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unterstützt die Datenquellen-Steuerelement-Plug-ins, die die Quelle Steuerelement-Plug-in-API entsprechen.  
  
### <a name="registering-the-source-control-plug-in"></a>Registrieren das Quellsteuerelement-Plug-in  
 Bevor ausgeführten integrierte Entwicklungsumgebung (IDE) in das Quellcodeverwaltungssystem aufrufen kann, müssen sie zuerst suchen Sie die Ursache steuern Sie die Plug-in-DLL, die die API exportiert.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Zum Registrieren der Quelle zu steuern, Plug-in-DLL  
  
1.  Fügen Sie zwei Einträge unter dem Schlüssel HKEY_LOCAL_MACHINE im Unterschlüssel SOFTWARE, die Ihr Unternehmen Namen Unterschlüssel gefolgt von der Product Name Unterschlüssel angibt. Das Muster ist HKEY_LOCAL_MACHINE\SOFTWARE\\*[Company Name]*\\*[Produktname]*\\*[Entry]* = Wert. Die beiden Einträge werden immer SCCServerName und SCCServerPath aufgerufen. Jede ist eine reguläre Zeichenfolge.  
  
     Z. B. den Namen Ihres Unternehmens ist Microsoft und Ihre Quellcodeverwaltungsprogramm SourceSafe lautet dann diesen Registrierungspfad HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe wäre. In dieser Unterschlüssel ist der erste Eintrag, SCCServerName, String Benutzer lesbaren Namen Ihres Produkts. Der zweite Eintrag, SCCServerPath, ist der vollständige Pfad zur Quelle steuern Plug-in-DLL, die die IDE eine Verbindung herstellen soll. Nachfolgend erhalten Registrierung Beispieleinträge:  
  
    |Beispiel-Registrierungseintrag|Beispielwert|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  Die SCCServerPath ist der vollständige Pfad zu der SourceSafe-Plug-in. Als Quellcodeverwaltungs-Plug-in wird andere Unternehmen und Produkt Namen jedoch die gleichen Registrierungspfade-Eintrag zu verwenden.  
  
2.  Die folgenden optionalen Registrierungseinträge können verwendet werden, um das Verhalten Ihres Quellcodeverwaltungs-Plug-in ändern. Diese Einträge im gleichen Unterschlüssel als SccServerName und SccServerPath wechseln.  
  
    -   Der Eintrag HideInVisualStudioregistry kann verwendet werden, wenn Sie nicht Ihre Quelle Steuerelement-Plug-in in der Plug-in-Auswahl Liste angezeigt werden sollen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Dieser Eintrag hat außerdem Auswirkungen auf den automatischen Wechsel zu den Datenquellen-Steuerelement-Plug-in. Eine Verwendungsmöglichkeit für diesen Eintrag ist, wenn Sie angeben, dass ein Datenquellen-Steuerelement-Paket, das als Quellcodeverwaltungs-Plug-in ersetzt, aber für den Benutzer zum Migrieren von der Verwendung der quellcodeverwaltung-Plug-in das Quellcodeverwaltungspaket vereinfachen möchten. Wenn das Quellcodeverwaltungspaket installiert ist, wird dieses Registrierungseintrags, das plug-in verborgen.  
  
         HideInVisualStudio einen DWORD-Wert ist und auf 1 fest, um das plug-in auszublenden, oder 0, um das plug-in anzeigen festgelegt ist. Wenn der Registrierungseintrag nicht angezeigt wird, ist das Standardverhalten des Plug-Ins angezeigt.  
  
    -   Der Registrierungseintrag DisableSccManager dienen zum Deaktivieren oder Ausblenden der **starten \<Quellcodeverwaltungsserver >** Menüoption, die normalerweise unter angezeigt wird der **Datei**  ->   **Quellcodeverwaltung** Untermenü. Auswählen von diesem Menü option Aufrufe der [SccRunScc](../../extensibility/sccrunscc-function.md) Funktion. Als Quellcodeverwaltungs-Plug-in kann ein externes Programm nicht unterstützt und daher möglicherweise möchten deaktivieren oder sogar Ausblenden der **starten** Option des Menüs.  
  
         DisableSccManager ist ein DWORD-Wert auf 0 festgelegt ist, Aktivieren der **starten \<Quellcodeverwaltungsserver >** Menüoption, deaktivieren Sie die Option auf 1 festgelegt und auf 2 festgelegt wird, um die Menüoption auszublenden. Wenn dieses Registrierungseintrags nicht angezeigt wird, ist das Standardverhalten der Menüoption angezeigt.  
  
    |Beispiel-Registrierungseintrag|Beispielwert|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  Fügen Sie den Unterschlüssel SourceCodeControlProvider, unter dem Schlüssel HKEY_LOCAL_MACHINE im Unterschlüssel SOFTWARE hinzu.  
  
     Dieser Unterschlüssel wird der Registrierungseintrag ProviderRegKey in eine Zeichenfolge festgelegt, die den Unterschlüssel darstellt, den Sie in der Registrierung in Schritt 1 platziert. Das Muster ist HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = SOFTWARE\\*[Company Name]*\\*[Produktname]*.  
  
     Im folgenden finden Beispielinhalte für die dieser Unterschlüssel.  
  
    |Registrierungseintrag|Beispielwert|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Als Quellcodeverwaltungs-Plug-in verwenden die gleichen Unterschlüssel und Eintragsnamen, aber der Wert unterscheiden.  
  
4.  Erstellen Sie einen Unterschlüssel mit dem Namen InstalledSCCProviders SourceCodeControlProvider Unterschlüssel, und legen Sie einen Eintrag unter diesem Unterschlüssel.  
  
     Der Name dieses Eintrags ist, den Benutzer lesbaren Namen des Anbieters (identisch mit den Wert für den Eintrag SCCServerName angegeben), und der Wert ist, von denen wiederum den Unterschlüssel, die in Schritt 1 erstellt haben. Das Muster ist HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\*[Anzeigename]* = SOFTWARE\\*[Company Name]* \\ *[Produktname]*.  
  
     Zum Beispiel:  
  
    |Beispiel-Registrierungseintrag|Beispielwert|  
    |---------------------------|------------------|  
    |Visual SourceSafe HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Es können mehrere Datenquellen-Steuerelement-Plug-ins auf diese Weise registriert sein. Dies ist wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] findet alle Source Control-Plug-in-API-basierte-Plug-ins installiert.  
  
## <a name="how-an-ide-locates-the-dll"></a>Wie die DLL findet eine IDE  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE verfügt über zwei Methoden zum Ermitteln der Ursache Plug-in-DLL zu steuern:  
  
-   Suchen Sie die Standard-Datenquellen-Steuerelement-Plug-in und Verbindung erfolgt im Hintergrund.  
  
-   Suchen Sie alle registrierten Ursache Steuerelement-Plug-ins, von dem wählt des Benutzers eine.  
  
 Um die DLL in die erste Möglichkeit zu suchen, sucht die IDE unter dem Unterschlüssel HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider für den Eintrag ProviderRegKey. Der Wert dieses Eintrags verweist auf eine andere Unterschlüssel. Die IDE sucht für einen Eintrag mit dem Namen SccServerPath in diesem zweiten "unter" HKEY_LOCAL_MACHINE. Der Wert dieses Eintrags zeigt die IDE auf die DLL.  
  
> [!NOTE]
>  Die IDE wird DLLs aus relative Pfade (beispielsweise.\NewProvider.DLL) nicht geladen werden. Ein vollständiger Pfad zur DLL muss angegeben werden (z. B. c:\Providers\NewProvider.DLL). Dies erhöht die Sicherheit der IDE an, indem verhindert das Laden von nicht autorisierten oder Identitätswechsel-Plug-in DLLs.  
  
 Um die DLL in die zweite Möglichkeit zu suchen, sucht der IDE unter dem Unterschlüssel HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders für alle Einträge*.* Jeder Eintrag hat einen Namen und einen Wert an. Zeigt die IDE eine Liste dieser Namen für den Benutzer*.* Wenn der Benutzer einen Namen auswählt, sucht die IDE den Wert für den ausgewählten Namen, der auf einen Unterschlüssel verweist. Die IDE sucht für einen Eintrag mit dem Namen SccServerPath in dieses "unter" HKEY_LOCAL_MACHINE. Der Wert, der diesem Eintrag zeigt die IDE auf die richtigen DLL.  
  
 Ein Quellcodeverwaltungs-Plug-in muss beide Methoden zum Suchen der DLL zu unterstützen und daher ProviderRegKey, überschreiben alle vorherigen Einstellung festgelegt. Vor allem müssen ihn hinzufügen selbst zur Liste der InstalledSccProviders damit der Benutzer eine Auswahl von der quellcodeverwaltung-Plug-in verwenden kann.  
  
> [!NOTE]
>  Da der Schlüssel HKEY_LOCAL_MACHINE verwendet wird, kann nur ein Datenquellen-Steuerelement-Plug-in als Standardeinstellung Versionskontroll-Plug-in auf einem bestimmten Computer registriert werden (allerdings [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ermöglicht Benutzern das Quell-Plug-in festzulegen, welche tatsächlich gewünschten für eine bestimmte Projektmappe). Während des Installationsvorgangs überprüfen Sie, wenn ein Quellcodeverwaltungs-Plug-in noch festgelegt ist; Wenn dies der Fall ist, fordern Sie den Benutzer angibt, ob der neue Datenquellen-Steuerelement-Plug-In installiert wird, als Standard festgelegt werden soll oder nicht. Während der Deinstallation bauen Sie nicht andere Registrierungsunterschlüsseln, die für alle Datenquellen-Steuerelement-Plug-ins in HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider identisch sind; Entfernen Sie nur die bestimmten SCC-Unterschlüssel.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>Wie 1.2/1.3 Versionsunterstützung erkennt die IDE  
 Wie wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erkennen, ob eine-Plug-in unterstützt Source Control-Plug-in-API-Version 1.2 und 1.3-Funktionen? Um erweiterte Funktionen zu deklarieren, muss die Datenquellen-Steuerelement-Plug-in die entsprechende Funktion implementieren.  
  
 Erstens [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] überprüft den Wert zurückgegeben, indem die [SccGetVersion](../../extensibility/sccgetversion-function.md). Er muss größer als oder gleich 1.2.  
  
 Als Nächstes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bestimmt, ob der bestimmte neue Funktion, mithilfe unterstützt wird der `lpSccCaps` Arguments auf der [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Wenn beide Bedingungen erfüllt sind, können die neuen Funktionen in den Versionen 1.2 und 1.3 unterstützt aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)