---
title: 'Vorgehensweise: Installieren eines Quellcodeverwaltungs-Plug-in | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b1e7e60819b9ac10308be26a1f3ea3243cc71c34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990502"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Vorgehensweise: Installieren eines Quellcodeverwaltungs-Plug-in
Erstellen eines Quellcodeverwaltungs-Plug-in umfasst drei Schritte:  

1. Erstellen Sie eine DLL-Datei mit den Funktionen, die in-API-Plug-in von Datenquelle Referenzabschnitt in dieser Dokumentation definiert.  

2. Die Source-Control-Plug-in-API-Funktionen zu implementieren. Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Aufrufe, Dialogfeldern und Schnittstellen verfügbar machen vom plug-in.  

3. Registrieren Sie die DLL, indem Sie die entsprechenden Registrierungseinträge vornehmen.  

## <a name="integration-with-visual-studio"></a>Integration in Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt die Quellcodeverwaltungs-Plug-ins, die die Source-Plug-in-API entsprechen.  

### <a name="register-the-source-control-plug-in"></a>Registrieren Sie das Quellcodeverwaltungs-Plug-in  
 Bevor eine ausgeführte integrierte Entwicklungsumgebung (IDE) in das Quellcodeverwaltungssystem aufrufen kann, muss er zunächst die Quelle finden steuern Sie die Plug-in-DLL, die die API exportiert.  

#### <a name="to-register-the-source-control-plug-in-dll"></a>Zum Registrieren der Quelle zu steuern, Plug-in-DLL  

1. Fügen Sie zwei Einträge unter den **HKEY_LOCAL_MACHINE** -Schlüssel in der **SOFTWARE** Unterschlüssel, die Ihr Unternehmen Namen Unterschlüssel gibt an, gefolgt von Ihrem Product Name-Unterschlüssel. Das Muster ist **HKEY_LOCAL_MACHINE\SOFTWARE\\\<Unternehmensname >\\\<Produktname >\\\<Eintrag >**  =  *Wert*. Die beiden Einträge werden immer aufgerufen **SCCServerName** und **SCCServerPath**. Jede ist eine reguläre Zeichenfolge.  

    Z. B. wenn den Namen Ihres Unternehmens Microsoft ist, und Ihre Quellcodeverwaltungsprogramm SourceSafe benannt ist, klicken Sie dann diesen Registrierungspfad wäre **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. In diesem Unterschlüssel, die den ersten Eintrag, **SCCServerName**, ist eine Benutzer lesbare Zeichenfolge, benennen Ihr Produkt. Der zweite Eintrag, **SCCServerPath**, ist der vollständige Pfad zur Quelldatei steuern, Plug-in-DLL, die die IDE eine Verbindung herstellen soll. Im folgenden finden Sie Beispieleinträge für die Registrierung:  

   |Beispiel-Registrierungseintrag|Beispielwert|  
   |---------------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|  

   > [!NOTE]
   >  SCCServerPath ist der vollständige Pfad zu der SourceSafe-Plug-in. Die quellcodeverwaltung-Plug-in verwendet unterschiedliche Unternehmens- und -Namen, aber die gleichen Registrierungspfade Eintrag.  

2. Die folgenden optionalen Registrierungseinträge können verwendet werden, um das Verhalten Ihres Quellcodeverwaltungs-Plug-in ändern. Diese Einträge wechseln Sie in den gleichen Unterschlüssel als **SccServerName** und **SccServerPath**.  

   - Die **HideInVisualStudioregistry** Eintrag kann verwendet werden, wenn die Quelle nicht Steuerelement-Plug-in angezeigt werden sollen die **Plug-in-Auswahl** Liste [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Dieser Eintrag wirkt sich auch auf automatische Umschaltung auf das Quellcodeverwaltungs-Plug-in. Eine Verwendungsmöglichkeit für diesen Eintrag ist, wenn Sie angeben, dass ein Quellcode-Verwaltungspaket, das Ihre quellcodeverwaltung-Plug-in ersetzt, aber für den Benutzer zu migrieren, verwenden Sie das Quellcodeverwaltungs-Plug-in das Quellcodeverwaltungspaket erleichtern sollen. Wenn der Quellcode-Verwaltungspaket installiert ist, wird dieses Registrierungseintrags, die das plug-in wird ausgeblendet.  

      **HideInVisualStudio** ist ein DWORD-Wert und nastaven NA hodnotu *1* der-Plug-in ausblenden oder *0* des Plug-Ins angezeigt. Wenn der Registrierungseintrag nicht angezeigt wird, wird das Standardverhalten Plug-Ins erläutert.  

   - Die **DisableSccManager** Registrierungseintrag kann verwendet werden, deaktivieren oder Ausblenden der **starten \<Quellcode-Verwaltungsserver >** Menüoption, die normalerweise angezeigt der **Datei**  >  **Quellcodeverwaltung** Untermenü. Wählen in diesem Menü option Aufrufe der [SccRunScc](../../extensibility/sccrunscc-function.md) Funktion. Die quellcodeverwaltung-Plug-Ins unterstützen möglicherweise kein externes Programm und aus diesem Grund sollten Sie zu deaktivieren oder sogar Ausblenden der **starten** Option des Menüs.  

      **DisableSccManager** ist ein DWORD-Wert und nastaven NA hodnotu *0* aktivieren die **starten \<Quellcode-Verwaltungsserver >** Menüoption, legen Sie auf *1* auf Deaktivieren Sie die Menüoption "", und legen auf *2* So blenden Sie die Menüoption "" aus. Wenn dieses Registrierungseintrags nicht angezeigt wird, wird das Standardverhalten die Menüoption erläutert.  

   | Beispiel-Registrierungseintrag | Beispielwert |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |


3. Fügen Sie die Unterschlüssel **SourceCodeControlProvider**unter der **HKEY_LOCAL_MACHINE** -Schlüssel in der **SOFTWARE** Unterschlüssel.  

    Unter diesem Unterschlüssel, die den Registrierungseintrag **ProviderRegKey** festgelegt ist, um eine Zeichenfolge, die Unterschlüssel darstellt, die Sie in der Registrierung in Schritt 1 platziert. Das Muster ist **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *SOFTWARE\\< Firmenname\>\\< Produktname \>*.  

    Im folgenden finden die Beispielinhalte für diesen Unterschlüssel.  

   |Registrierungseintrag|Beispielwert|  
   |--------------------|------------------|  
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  Die quellcodeverwaltung-Plug-in verwenden die gleichen Unterschlüssel und Eintragsnamen, aber der Wert unterscheiden.  

4. Erstellen Sie einen Unterschlüssel mit dem Namen **InstalledSCCProviders** unter der **SourceCodeControlProvider** Unterschlüssel, und legen Sie einen Eintrag unter diesem Unterschlüssel.  

    Der Name dieses Eintrags ist, den Benutzer lesbaren Namen des Anbieters (entspricht der Wert für den Eintrag SCCServerName angegeben), und der Wert ist, von denen wiederum den Unterschlüssel, die in Schritt 1 erstellt haben. Das Muster ist **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<display name>** = *SOFTWARE\\< Firmenname\> \\< Produktname\>*.  

    Zum Beispiel:  

   |Beispiel-Registrierungseintrag|Beispielwert|  
   |---------------------------|------------------|  
   |Visual SourceSafe HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft|SOFTWARE\Microsoft\SourceSafe|  

   > [!NOTE]
   >  Es können mehrere Quellcodeverwaltungs-Plug-ins auf diese Weise registriert sein. Dies ist wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] findet alle Source Control-Plug-in-API-basierte-Plug-ins installiert.  

## <a name="how-an-ide-locates-the-dll"></a>Suchen eine IDE wie der DLL  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE verfügt über zwei Methoden zur Suche nach der Quelle Plug-in-DLL zu steuern:  

- Finden Sie das Standard-Quellcodeverwaltungs-Plug-in, und verbinden Sie diesen im Hintergrund.  

- Finden Sie alle registrierten Datenquellen Steuerelement-Plug-ins aus dem der Benutzer wird eine ausgewählt.  

  Um die DLL in die erste Methode zu suchen, sucht die IDE unter der **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** Unterschlüssel für den Eintrag **ProviderRegKey**. Der Wert dieses Eintrags verweist auf eine andere Unterschlüssel. Die IDE sucht dann nach einem Eintrag mit dem Namen **SccServerPath** in diesem zweiten Unterschlüssel unter **HKEY_LOCAL_MACHINE**. Der Wert dieses Eintrags zeigt die IDE auf die DLL an.  

> [!NOTE]
>  Die IDE DLLs von relativen Pfaden wird nicht geladen werden (z. B. *.\NewProvider.DLL*). Ein vollständiger Pfad zur DLL muss angegeben werden (z. B. *c:\Providers\NewProvider.DLL*). Dies erhöht die Sicherheit der IDE, indem verhindert das Laden von nicht autorisierten oder Identitätswechsel-Plug-in-DLLs.  

 Um die DLL in die zweite Methode zu suchen, sucht die IDE unter der **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** Unterschlüssel für alle Einträge. Jeder Eintrag hat einen Namen und einen Wert an. Die IDE zeigt eine Liste dieser Namen für den Benutzer. Wenn der Benutzer einen Namen auswählt, sucht die IDE den Wert für den ausgewählten Namen, der auf einen Unterschlüssel zeigt. Sucht die IDE nach einem Eintrag mit dem Namen **SccServerPath** in unter diesem Unterschlüssel **HKEY_LOCAL_MACHINE**. Der Wert, der den Eintrag zeigt die IDE auf die richtigen DLL.  

 Ein Quellcodeverwaltungs-Plug-in muss beide Methoden zum Suchen der DLL zu unterstützen und daher legt, **ProviderRegKey**, alle vorherigen Einstellungen überschrieben. Wichtiger ist, es muss sich selbst hinzufügt zur Liste der **InstalledSccProviders** müssen der Benutzer eine Auswahl von der quellcodeverwaltung-Plug-in verwenden kann.  

> [!NOTE]
>  Da die **HKEY_LOCAL_MACHINE** Schlüssel verwendet wird, nur eine quellcodeverwaltung-Plug-in registriert werden kann, als das standardmäßige Quellcodeverwaltungs-Plug-in auf einem bestimmten Computer (allerdings [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ermöglicht es Benutzern, um zu bestimmen, welche Datenquellen-Steuerelement-Plug-in Sie möchten für eine bestimmte Lösung tatsächlich verwendet). Während des Installationsvorgangs überprüfen Sie, wenn ein Quellcodeverwaltungs-Plug-in bereits festgelegt ist; Wenn dies der Fall ist, bitten Sie den Benutzer angibt, ob das neue Quellcodeverwaltungs-Plug-In installiert wird, als Standard festgelegt werden soll oder nicht. Bei der Deinstallation, entfernen Sie nicht anderen Registrierungsunterschlüssel, die für alle Quellcodeverwaltungs-Plug-ins in gelten **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider**; nur Ihre bestimmten SCC-Unterschlüssel zu entfernen.  

## <a name="how-the-ide-detects-version-1213-support"></a>Wie erkennt die IDE die Unterstützung für Version 1.2/1.3  
 Wie wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erkennen, ob eine-Plug-in unterstützt Source Control-Plug-in-API-Version 1.2 und 1.3-Funktion? Um erweiterte Funktionen zu deklarieren, muss das Quellcodeverwaltungs-Plug-in die entsprechende Funktion implementieren:  

 Zuerst [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] überprüft den Wert zurückgegeben, indem die [SccGetVersion](../../extensibility/sccgetversion-function.md). Es muss größer als oder gleich 1.2 sein.  

 Als Nächstes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bestimmt, ob der bestimmte neue Funktion, anhand unterstützt wird der `lpSccCaps` Arguments auf der [SccInitialize](../../extensibility/sccinitialize-function.md).  

 Wenn beide Bedingungen erfüllt sind, können die neuen Funktionen, die in den Versionen 1.2 und 1.3 unterstützt aufgerufen werden.  

## <a name="see-also"></a>Siehe auch  
 [Erste Schritte mit Quellcodeverwaltungs-Plug-ins](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)