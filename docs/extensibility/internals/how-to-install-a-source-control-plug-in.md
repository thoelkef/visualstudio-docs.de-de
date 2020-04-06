---
title: 'Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-Ins | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c0ac87aec3d6ac2532909772238e020e33bf78f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707994"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-Ins
Das Erstellen eines Quellcodeverwaltungs-Plug-Ins umfasst drei Schritte:

1. Erstellen Sie eine DLL mit den im Abschnitt Source Control Plug-In-API-Referenz dieser Dokumentation definierten Funktionen.

2. Implementieren Sie die mit der Quellcodeverwaltung definierten Funktionen für die Quellsteuerungs-Plug-in-API. Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Sie dies aufrufen, stellen Sie Schnittstellen und Dialogfelder über das Plug-In zur Verfügung.

3. Registrieren Sie die DLL, indem Sie entsprechende Registrierungseinträge vornehmen.

## <a name="integration-with-visual-studio"></a>Integration in Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]unterstützt Quellcodeverwaltungs-Plug-Ins, die der Quellcodeverwaltungs-Plug-In-API entsprechen.

### <a name="register-the-source-control-plug-in"></a>Registrieren des Quellcodeverwaltungs-Plug-Ins
 Bevor eine ausgeführte integrierte Entwicklungsumgebung (IDE) das Quellcodeverwaltungssystem aufrufen kann, muss zunächst die Quellcodeverwaltungs-Plug-In-DLL gefunden werden, die die API exportiert.

#### <a name="to-register-the-source-control-plug-in-dll"></a>So registrieren Sie die Quellcodeverwaltungs-Plug-In-DLL

1. Fügen Sie zwei Einträge unter dem **HKEY_LOCAL_MACHINE** Schlüssel im **UNTERschlüssel SOFTWARE** hinzu, der Ihren Unterschlüssel für den Firmennamen gefolgt von Ihrem Produktnamen-Unterschlüssel angibt. Das Muster lautet **\\\<HKEY_LOCAL_MACHINE-SOFTWARE-Firmenname>\\ \<Produktname>\\ \<Eintrag>**  =  *Wert*. Die beiden Einträge heißen immer **SCCServerName** und **SCCServerPath**. Jede ist eine reguläre Zeichenfolge.

    Wenn Ihr Firmenname z. B. Microsoft lautet und Ihr Quellcodeverwaltungsprodukt den Namen SourceSafe trägt, lautet dieser Registrierungspfad **HKEY_LOCAL_MACHINE.-SOFTWARE-Microsoft-SourceSafe**. In diesem Unterschlüssel ist der erste **Eintrag, SCCServerName**, eine vom Benutzer lesbare Zeichenfolge, die Ihr Produkt benennt. Der zweite Eintrag, **SCCServerPath**, ist der vollständige Pfad zur Quellcodeverwaltungs-Plug-In-DLL, mit der die IDE eine Verbindung herstellen soll. Im Folgenden finden Sie Beispielregistrierungseinträge:

   |Beispielregistrierungseintrag|Beispielwert|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-SourceSafe-SCCServername|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-SourceSafe-SCCServerPath|*c:-vss-win32-ssscc.dll*|

   > [!NOTE]
   > SCCServerPath ist der vollständige Pfad zum SourceSafe-Plug-In. Ihr Quellcodeverwaltungs-Plug-In verwendet unterschiedliche Firmen- und Produktnamen, aber dieselben Registrierungseintragspfade.

2. Die folgenden optionalen Registrierungseinträge können verwendet werden, um das Verhalten des Quellcodeverwaltungs-Plug-Ins zu ändern. Diese Einträge befinden sich in demselben Unterschlüssel wie **SccServerName** und **SccServerPath**.

   - Der **HideInVisualStudioregistry-Eintrag** kann verwendet werden, wenn das Quellcodeverwaltungs-Plug-In nicht in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]der Liste **Plug-In-Auswahl** von angezeigt werden soll. Dieser Eintrag wirkt sich auch auf das automatische Umschalten auf das Quellcodeverwaltungs-Plug-In aus. Eine mögliche Verwendung für diesen Eintrag ist, wenn Sie ein Quellcodeverwaltungspaket angeben, das das Quellcodeverwaltungs-Plug-In ersetzt, dem Benutzer jedoch die Migration von der Verwendung des Quellcodeverwaltungs-Plug-Ins zum Quellcodeverwaltungspaket erleichtern soll. Wenn das Quellcodeverwaltungspaket installiert ist, wird dieser Registrierungseintrag festgelegt, der das Plug-In ausblendet.

      **HideInVisualStudio** ist ein DWORD-Wert und ist auf *1* festgelegt, um das Plug-In auszublenden, oder *0,* um das Plug-In anzuzeigen. Wenn der Registrierungseintrag nicht angezeigt wird, wird das Plug-In standardmäßig angezeigt.

   - Der **Registrierungseintrag DisableSccManager** kann verwendet werden, um die Menüoption **"Quellsteuerungsserver \<starten" zu** deaktivieren oder auszublenden>, die normalerweise unter dem Untermenü **Dateiquellcode** > **Source Control** angezeigt wird. Wenn Sie diese Menüoption auswählen, wird die [SccRunScc-Funktion](../../extensibility/sccrunscc-function.md) aufgezäunt. Ihr Quellcodeverwaltungs-Plug-In unterstützt möglicherweise kein externes Programm, und daher können Sie die Option **"Startmenü"** deaktivieren oder sogar ausblenden.

      **DisableSccManager** ist ein DWORD-Wert und ist auf *0* gesetzt, um die Menüoption **Source Control Server starten \<>** Menüoption zu aktivieren, auf *1* zu setzen, um die Menüoption zu deaktivieren, und auf *2,* um die Menüoption auszublenden. Wenn dieser Registrierungseintrag nicht angezeigt wird, wird standardmäßig die Menüoption angezeigt.

   | Beispielregistrierungseintrag | Beispielwert |
   | - |--------------|
   | HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-SourceSafe-HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-SourceSafe-DisableSccManager | 1 |

3. Fügen Sie den Unterschlüssel **SourceCodeControlProvider**unter dem **HKEY_LOCAL_MACHINE** Schlüssel im **Software-Unterschlüssel** hinzu.

    Unter diesem Unterschlüssel wird der Registrierungseintrag **ProviderRegKey** auf eine Zeichenfolge festgelegt, die den Unterschlüssel darstellt, den Sie in Schritt 1 in der Registrierung platziert haben. Das Muster lautet **HKEY_LOCAL_MACHINE-SOFTWARE-SourceCodeControlProvider-ProviderRegKey-SOFTWARE** = *\\<Firmennamen\> \\<Produktname\>*.

    Im Folgenden finden Sie Beispielinhalte für diesen Unterschlüssel.

   |Registrierungseintrag|Beispielwert|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE-SOFTWARE-SourceCodeControlProvider-ProviderRegKey|SOFTWARE-Microsoft-SourceSafe|

   > [!NOTE]
   > Das Quellcodeverwaltungs-Plug-In verwendet denselben Unterschlüssel und dieselben Eintragsnamen, der Wert ist jedoch unterschiedlich.

4. Erstellen Sie einen Unterschlüssel mit dem Namen **InstalledSCCProviders** unter dem **Subkey SourceCodeControlProvider,** und platzieren Sie dann einen Eintrag unter diesem Unterschlüssel.

    Der Name dieses Eintrags ist der vom Benutzer lesbare Name des Anbieters (derselbe wie der für den SCCServerName-Eintrag angegebene Wert), und der Wert ist erneut der Unterschlüssel, der in Schritt 1 erstellt wurde. Das Muster lautet **HKEY_LOCAL_MACHINE-SOFTWARE-SourceCodeControlProvider<InstalledSCCProviders\\<Anzeigename\>** = SOFTWARE*\\<Firmennamen\> \\<Produktnamen\>*.

    Beispiel:

   |Beispielregistrierungseintrag|Beispielwert|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE-SOFTWARE-SourceCodeControlProvider-InstalledSCCProviders-Microsoft Visual SourceSafe|SOFTWARE-Microsoft-SourceSafe|

   > [!NOTE]
   > Auf diese Weise können mehrere Quellcodeverwaltungs-Plug-Ins registriert werden. Auf diese [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Weise werden alle installierten Quellcodeverwaltungs-Plug-In-API-basierten Plug-Ins gefunden.

## <a name="how-an-ide-locates-the-dll"></a>So findet eine IDE die DLL
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE bietet zwei Möglichkeiten, die Quellcodeverwaltungs-Plug-In-DLL zu finden:

- Suchen Sie das Standard-Quellcodeverwaltungs-Plug-In, und stellen Sie eine automatische Verbindung her.

- Suchen Sie alle registrierten Quellcodeverwaltungs-Plug-Ins, aus denen der Benutzer eines auswählt.

  Um die DLL zunächst zu finden, sucht die IDE unter dem Unterschlüssel **HKEY_LOCAL_MACHINE-Software-SourceCodeControlProvider** für den Eintrag **ProviderRegKey**. Der Wert dieses Eintrags verweist auf einen anderen Unterschlüssel. Die IDE sucht dann in diesem zweiten Unterschlüssel unter **HKEY_LOCAL_MACHINE**nach einem Eintrag mit dem Namen **SccServerPath.** Der Wert dieses Eintrags verweist die IDE auf die DLL.

> [!NOTE]
> Die IDE lädt keine DLLs von relativen Pfaden (z. B. *.'NewProvider.DLL ').* Es muss ein vollständiger Pfad zur DLL angegeben werden (z. B. *c:-Providers-NewProvider.DLL*). Dies erhöht die Sicherheit der IDE, indem das Laden nicht autorisierter oder imitierter Plug-In-DLLs verhindert wird.

 Um die DLL auf die zweite Weise zu finden, sucht die IDE unter dem Unterschlüssel **HKEY_LOCAL_MACHINE-Software-SourceCodeControlProvider-InstalledSCCProviders** für alle Einträge. Jeder Eintrag hat einen Namen und einen Wert. Die IDE zeigt dem Benutzer eine Liste dieser Namen an. Wenn der Benutzer einen Namen auswählt, findet die IDE den Wert für den ausgewählten Namen, der auf einen Unterschlüssel verweist. Die IDE sucht in diesem Unterschlüssel unter **HKEY_LOCAL_MACHINE**nach einem Eintrag mit dem Namen **SccServerPath.** Der Wert dieses Eintrags verweist die IDE auf die richtige DLL.

 Ein Quellcodeverwaltungs-Plug-In muss beide Möglichkeiten zum Suchen der DLL unterstützen und setzt daher **ProviderRegKey**, um alle vorherigen Einstellungen zu überschreiben. Noch wichtiger ist, dass es sich selbst zur Liste der **InstalledSccProviders** hinzufügen muss, damit der Benutzer die Wahl haben kann, welches Quellcodeverwaltungs-Plug-In verwendet werden soll.

> [!NOTE]
> Da der **HKEY_LOCAL_MACHINE-Schlüssel** verwendet wird, kann nur ein Quellcodeverwaltungs-Plug-In als Standard-Quellcodeverwaltungs-Plug-In auf einem bestimmten Computer registriert werden (kann Benutzern jedoch bestimmen, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] welches Quellcodeverwaltungs-Plug-In sie tatsächlich für eine bestimmte Lösung verwenden möchten). Überprüfen Sie während des Installationsvorgangs, ob bereits ein Quellcodeverwaltungs-Plug-In festgelegt ist. Wenn dies der Fall ist, fragen Sie den Benutzer, ob das neue Quellcodeverwaltungs-Plug-In als Standard installiert werden soll. Entfernen Sie während der Deinstallation keine anderen Registrierungsunterschlüssel, die allen Quellcodeverwaltungs-Plug-Ins in **HKEY_LOCAL_MACHINE-SOFTWARE-SourceCodeControlProvider**gemeinsam sind. entfernen Sie nur Ihren bestimmten SCC-Unterschlüssel.

## <a name="how-the-ide-detects-version-1213-support"></a>Wie die IDE Version 1.2/1.3-Unterstützung erkennt
 Wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erkennt, ob ein Plug-In die Source Control Plug-In-API-Funktionalität 1.2 und 1.3 unterstützt? Um erweiterte Funktionen zu deklarieren, muss das Quellcodeverwaltungs-Plug-In die entsprechende Funktion implementieren:

 Überprüft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zunächst den Wert, der durch Aufrufen der [SccGetVersion](../../extensibility/sccgetversion-function.md)zurückgegeben wird. Sie muss größer oder gleich 1,2 sein.

 Als [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Nächstes wird bestimmt, ob die `lpSccCaps` bestimmte neue Funktion unterstützt wird, indem das Argument auf der [SccInitialize](../../extensibility/sccinitialize-function.md)untersucht wird.

 Wenn beide Bedingungen erfüllt sind, können die neuen Funktionen, die in den Versionen 1.2 und 1.3 unterstützt werden, aufgerufen werden.

## <a name="see-also"></a>Weitere Informationen
- [Erste Schritte mit Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
