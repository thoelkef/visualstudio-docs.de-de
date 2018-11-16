---
title: 'Vorgehensweise: Installieren eines Quellcodeverwaltungs-Plug-in | Microsoft-Dokumentation'
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
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f151653387c95e77d775bfc9f37cbdfb9f824e7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741636"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Vorgehensweise: Installieren eines Quellcodeverwaltungs-Plug-in
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Erstellen eines Quellcodeverwaltungs-Plug-in umfasst drei Schritte:  
  
1.  Erstellen Sie eine DLL-Datei mit den Funktionen, die in-API-Plug-in von Datenquelle Referenzabschnitt in dieser Dokumentation definiert.  
  
2.  Die Source-Control-Plug-in-API-Funktionen zu implementieren. Wenn [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Aufrufe, Dialogfeldern und Schnittstellen verfügbar machen vom plug-in.  
  
3.  Registrieren Sie die DLL, indem Sie die entsprechenden Registrierungseinträge vornehmen.  
  
## <a name="integration-with-visual-studio"></a>Integration in Visual Studio  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] unterstützt die Quellcodeverwaltungs-Plug-ins, die die Source-Plug-in-API entsprechen.  
  
### <a name="registering-the-source-control-plug-in"></a>Registrieren das Quellcodeverwaltungs-Plug-in  
 Bevor eine ausgeführte integrierte Entwicklungsumgebung (IDE) in das Quellcodeverwaltungssystem aufrufen kann, muss er zunächst die Quelle finden steuern Sie die Plug-in-DLL, die die API exportiert.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Zum Registrieren der Quelle zu steuern, Plug-in-DLL  
  
1.  Fügen Sie zwei Einträge unter dem Schlüssel HKEY_LOCAL_MACHINE, in der SOFTWARE-Unterschlüssel, die Ihr Unternehmen Namen Unterschlüssel gefolgt von Ihrem Product Name-Unterschlüssel angibt. Das Muster ist HKEY_LOCAL_MACHINE\SOFTWARE\\ *[Company Name]*\\ *[Produktname]*\\ *[Entry]* = Wert. Die beiden Einträge werden immer SCCServerName und SCCServerPath aufgerufen. Jede ist eine reguläre Zeichenfolge.  
  
     Z. B. den Namen Ihres Unternehmens ist Microsoft und Ihre Quellcodeverwaltungsprogramm SourceSafe handelt, heißt dieser Registrierungspfad HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe wäre. In diesem Unterschlüssel ist der erste Eintrag, SCCServerName, einen Benutzer lesbare Zeichenfolge, benennen Ihr Produkt. Der zweite Eintrag, SCCServerPath, ist der vollständige Pfad zur Quelldatei steuern, Plug-in-DLL, die die IDE eine Verbindung herstellen soll. Im folgenden finden Sie Beispieleinträge für die Registrierung:  
  
    |Beispiel-Registrierungseintrag|Beispielwert|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  Die SCCServerPath ist der vollständige Pfad zu der SourceSafe-Plug-in. Die quellcodeverwaltung-Plug-in verwendet unterschiedliche Unternehmens- und -Namen, aber die gleichen Registrierungspfade Eintrag.  
  
2.  Die folgenden optionalen Registrierungseinträge können verwendet werden, um das Verhalten Ihres Quellcodeverwaltungs-Plug-in ändern. Diese Einträge werden in den gleichen Unterschlüssel als SccServerName und SccServerPath wechseln.  
  
    -   Der Eintrag HideInVisualStudioregistry kann verwendet werden, wenn Sie nicht Ihre Quelle Steuerelement-Plug-in in der Liste der Plug-in-Auswahl der angezeigt werden soll [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Dieser Eintrag wirkt sich auch auf automatische Umschaltung auf das Quellcodeverwaltungs-Plug-in. Eine Verwendungsmöglichkeit für diesen Eintrag ist, wenn Sie angeben, dass ein Quellcode-Verwaltungspaket, das Ihre quellcodeverwaltung-Plug-in ersetzt, aber für den Benutzer zu migrieren, verwenden Sie das Quellcodeverwaltungs-Plug-in das Quellcodeverwaltungspaket erleichtern sollen. Wenn der Quellcode-Verwaltungspaket installiert ist, wird dieses Registrierungseintrags, die das plug-in wird ausgeblendet.  
  
         HideInVisualStudio ist ein DWORD-Wert und auf 1 fest, um das plug-in auszublenden, oder 0, um das plug-in zeigen festgelegt ist. Wenn der Registrierungseintrag nicht angezeigt wird, wird das Standardverhalten Plug-Ins erläutert.  
  
    -   Der Registrierungseintrag DisableSccManager kann verwendet werden, deaktivieren oder Ausblenden der **starten \<Quellcode-Verwaltungsserver >** Menüoption, die normalerweise angezeigt der **Datei**  ->   **Datenquellen-Steuerelement** Untermenü. Wählen in diesem Menü option Aufrufe der [SccRunScc](../../extensibility/sccrunscc-function.md) Funktion. Die quellcodeverwaltung-Plug-Ins unterstützen möglicherweise kein externes Programm und aus diesem Grund sollten Sie zu deaktivieren oder sogar Ausblenden der **starten** Option des Menüs.  
  
         DisableSccManager ist ein DWORD-Wert auf 0 festgelegt ist, aktivieren die **starten \<Quellcodeverwaltungsserver >** Menüoption, die auf 1 festgelegt, um die Menüoption zu deaktivieren und Ausblenden die Menüoption auf 2 festgelegt. Wenn dieses Registrierungseintrags nicht angezeigt wird, wird das Standardverhalten die Menüoption erläutert.  
  
    |Beispiel-Registrierungseintrag|Beispielwert|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  Fügen Sie den Unterschlüssel, SourceCodeControlProvider, unter dem Schlüssel "HKEY_LOCAL_MACHINE" in der SOFTWARE-Unterschlüssel hinzu.  
  
     Unter diesem Unterschlüssel wird der Registrierungseintrag ProviderRegKey in eine Zeichenfolge festgelegt, die den Unterschlüssel darstellt, den Sie in der Registrierung in Schritt 1 platziert. Das Muster ist HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = SOFTWARE\\ *[Company Name]*\\ *[Produktname]*.  
  
     Im folgenden finden die Beispielinhalte für diesen Unterschlüssel.  
  
    |Registrierungseintrag|Beispielwert|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Die quellcodeverwaltung-Plug-in verwenden die gleichen Unterschlüssel und Eintragsnamen, aber der Wert unterscheiden.  
  
4.  Erstellen Sie einen Unterschlüssel mit dem Namen InstalledSCCProviders unter dem Unterschlüssel SourceCodeControlProvider, und legen Sie einen Eintrag unter diesem Unterschlüssel.  
  
     Der Name dieses Eintrags ist, den Benutzer lesbaren Namen des Anbieters (entspricht der Wert für den Eintrag SCCServerName angegeben), und der Wert ist, von denen wiederum den Unterschlüssel, die in Schritt 1 erstellt haben. Das Muster ist HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\ *[Anzeigename]* = SOFTWARE\\ *[Company Name]* \\ *[Produktname]*.  
  
     Zum Beispiel:  
  
    |Beispiel-Registrierungseintrag|Beispielwert|  
    |---------------------------|------------------|  
    |Visual SourceSafe HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Es können mehrere Quellcodeverwaltungs-Plug-ins auf diese Weise registriert sein. Dies ist wie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] findet alle Source Control-Plug-in-API-basierte-Plug-ins installiert.  
  
## <a name="how-an-ide-locates-the-dll"></a>Suchen eine IDE wie der DLL  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE verfügt über zwei Methoden zur Suche nach der Quelle Plug-in-DLL zu steuern:  
  
- Finden Sie das Standard-Quellcodeverwaltungs-Plug-in, und verbinden Sie diesen im Hintergrund.  
  
- Finden Sie alle registrierten Datenquellen Steuerelement-Plug-ins aus dem der Benutzer wird eine ausgewählt.  
  
  Um die DLL in die erste Methode zu suchen, sucht die IDE, unter dem Unterschlüssel HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider für den Eintrag ProviderRegKey. Der Wert dieses Eintrags verweist auf eine andere Unterschlüssel. Die IDE sucht nach einem Eintrag mit dem Namen SccServerPath in dieser zweiten "unter" HKEY_LOCAL_MACHINE. Der Wert dieses Eintrags zeigt die IDE auf die DLL an.  
  
> [!NOTE]
>  Die IDE wird DLLs aus relative Pfade (z. B..\NewProvider.DLL) nicht geladen werden. Ein vollständiger Pfad zur DLL muss angegeben werden (z. B. c:\Providers\NewProvider.DLL). Dies erhöht die Sicherheit der IDE, indem verhindert das Laden von nicht autorisierten oder Identitätswechsel-Plug-in-DLLs.  
  
 Um die DLL in die zweite Methode zu suchen, sucht die IDE unter dem Unterschlüssel HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders für alle Einträge<em>.</em> Jeder Eintrag hat einen Namen und einen Wert an. Zeigt die IDE eine Liste mit diesen Namen für den Benutzer<em>.</em> Wenn der Benutzer einen Namen auswählt, sucht die IDE den Wert für den ausgewählten Namen, der auf einen Unterschlüssel zeigt. Die IDE sucht nach einem Eintrag mit dem Namen SccServerPath in diesem "unter" HKEY_LOCAL_MACHINE. Der Wert, der den Eintrag zeigt die IDE auf die richtigen DLL.  
  
 Ein Quellcodeverwaltungs-Plug-in muss beide Methoden zum Suchen der DLL zu unterstützen, und legen Sie daher ProviderRegKey, alle vorherigen Einstellungen überschrieben. Wichtiger ist, muss es hinzufügen selbst in die Liste der InstalledSccProviders müssen der Benutzer eine Auswahl von der quellcodeverwaltung-Plug-in verwenden kann.  
  
> [!NOTE]
>  Da es sich bei der Schlüssel HKEY_LOCAL_MACHINE verwendet wird, kann nur eine quellcodeverwaltung-Plug-in als das standardmäßige Quellcodeverwaltungs-Plug-in auf einem bestimmten Computer registriert werden (allerdings [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ermöglicht es Benutzern, um zu bestimmen, welche Datenquellen-Steuerelement-Plug-In für die tatsächlich verwendet werden soll ein bestimmten Lösung). Während des Installationsvorgangs überprüfen Sie, wenn ein Quellcodeverwaltungs-Plug-in bereits festgelegt ist; Wenn dies der Fall ist, bitten Sie den Benutzer angibt, ob das neue Quellcodeverwaltungs-Plug-In installiert wird, als Standard festgelegt werden soll oder nicht. Bei der Deinstallation entfernen Sie andere Registrierungsunterschlüssel, die für alle Quellcodeverwaltungs-Plug-ins in HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider gelten nicht; Entfernen Sie nur Ihre bestimmten SCC-Unterschlüssel.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>Wie erkennt die IDE 1.2/1.3-Versionsunterstützung  
 Wie wird [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] erkennen, ob eine-Plug-in unterstützt Source Control-Plug-in-API-Version 1.2 und 1.3-Funktion? Um erweiterte Funktionen zu deklarieren, muss das Quellcodeverwaltungs-Plug-in die entsprechende Funktion implementieren.  
  
 Zuerst [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] überprüft den Wert zurückgegeben, indem die [SccGetVersion](../../extensibility/sccgetversion-function.md). Es muss größer als oder gleich 1.2 sein.  
  
 Als Nächstes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bestimmt, ob der bestimmte neue Funktion, anhand unterstützt wird der `lpSccCaps` Arguments auf der [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Wenn beide Bedingungen erfüllt sind, können die neuen Funktionen, die in den Versionen 1.2 und 1.3 unterstützt aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

