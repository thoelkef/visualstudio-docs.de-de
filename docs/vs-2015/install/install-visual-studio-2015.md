---
title: Installieren von Visual Studio 2015 | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a31bc328c20aada21b05edeef61886d57e914165
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298044"
---
# <a name="install-visual-studio-2015"></a>Installieren von Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Seite enthält detaillierte Informationen zum Installieren von **Visual Studio 2015**, der integrierten Sammlung von Produktivitätstools für Entwickler. Wir haben auch Links eingefügt, sodass Sie schnell auf Informationen zu [Funktionen](https://www.visualstudio.com/news/vs2015-vs.aspx), [Editionen](https://go.microsoft.com/fwlink/?LinkID=242142), [Systemanforderungen](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [Downloads](https://go.microsoft.com/fwlink/?LinkId=517106)usw. zugreifen können.

## <a name="quick-links"></a>Quicklinks

Bevor wir auf die Details eingehen, finden Sie hier die am häufigsten aufgerufenen Links.

|||
|------------------|----------------|
|![Herunterladen von Visual Studio](../install/media/downloads.png "Downloads") |**Downloads**: To install Visual Studio 2015, you can download a product executable file from the  [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) page (subscription required), or use the installation media from the boxed product. [Learn more about how to download current or previous versions of Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Learn more about features](../install/media/features.png "Features") |**Features**: To learn  more about the features in Visual Studio 2015, see the release notes for [RTM](https://www.visualstudio.com/news/vs2015-vs), [Update 1](https://www.visualstudio.com/news/vs2015-update1-vs), [Update 2](https://www.visualstudio.com/news/vs2015-update2-vs), and [Update 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|
|![Find out what's in each SKU](../install/media/sku.png "SKUs") |**SKUs:** Informationen zu den in den einzelnen Editionen von Visual Studio 2015 verfügbaren Funktionen finden Sie unter [Compare Visual Studio Offerings (Visual Studio-Editionen im Vergleich)](https://go.microsoft.com/fwlink/?LinkID=242142).|
|![View system requirements](../install/media/system-requirements.png "Systemanforderungen") |**System Requirements**: To view the system requirements for each edition of Visual Studio 2015, see the [Visual Studio 2015 Compatibility](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) page.|
|![Locate your Product Key](../install/media/product-keys.png "Product Keys") |**Product Keys**: To locate your product key, see the [How to: Locate the Visual Studio Product Key](../install/how-to-locate-the-visual-studio-product-key.md) topic.|
|![Find out about licensing](../install/media/licensing.png "Lizenzierung") |**Licensing**: To find out about licensing options for both individuals or enterprise customers, see  the [Visual Studio and MSDN Licensing](https://www.microsoft.com/download/details.aspx?id=13350) white paper.|

## <a name="custom"></a> Default vs. Custom Setup
 Bei der Installation von Visual Studio 2015 können Sie Komponenten, die Sie täglich verwenden, ein- und ausschließen. Dies bedeutet, dass eine Standardinstallation oft kleiner und schneller erfolgt als eine benutzerdefinierte Installation. Dies bedeutet zudem, dass in früheren Versionen viele standardmäßig installierte Komponenten nun als benutzerdefinierte Komponenten erachtet werden, die Sie explizit in dieser Version auswählen müssen.

 ![Visual Studio 2015 Setup Dialog](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Zu benutzerdefinierten Komponenten zählen Visual C++, Visual F#, SQL Server-Datentools, plattformübergreifende mobile Tools und SDKs sowie SDKs und Erweiterungen von Drittanbietern. Sie können jede der benutzerdefinierten Komponenten zu einem späteren Zeitpunkt installieren, wenn Sie sie während des ersten Setups nicht auswählen.

> [!NOTE]
> Bei einer benutzerdefinierten Installation werden die in einer Standardinstallation enthaltenen Komponenten automatisch mit aufgenommen.

 Die vollständige Liste der benutzerdefinierten Komponenten lautet wie folgt:

|Feature Sets|Komponenten|
|------------------|----------------|
|**Updates**|Visual Studio 2015 Update 3|
|**Programmiersprachen**|Visual C++<br />Visual F#<br />Python-Tools für Visual Studio|
|**Windows- und Webentwicklung**|ClickOnce-Tools für die Veröffentlichung<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server-Datentools<br /> Microsoft Web Developer Tools<br />PowerShell Tools for Visual Studio (3rd Party)<br />Silverlight Development Kit<br />Universal Windows App-Entwicklungstools<br />Windows 10-Tools und -SDKs<br />Windows 8.1- und Windows Phone 8.0/8.1-Tools<br />Windows 8.1-Tools und -SDKs|
|**Plattformübergreifende mobile Entwicklung**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Mobile Visual C++-Entwicklung für iOS / Android<br />Clang mit Microsoft CodeGen|
|**Common Tools and Software Development Kits**|Android Native Development Kit (3rd Party)<br /> Android SDK [3rd Party]<br />Android SDK Setup APIs (3rd Party)<br />Apache Ant (3rd Party)<br /> Java SE Development Kit (3rd Party)<br /> Joyent Node.js (3rd Party)|
|**Häufig verwendete Tools**|Git for Windows (3rd Party)<br />GitHub Extension for Visual Studio (3rd Party)<br /> Visual Studio-Erweiterbarkeitstools|

## <a name="installing"></a> Installieren von Visual Studio
 You can install Visual Studio by using installation media (DVDs), by using your Visual Studio subscription service from the [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) website, by downloading  a web installer from the [Visual Studio Downloads](https://go.microsoft.com/fwlink/?LinkId=517106) website, or by creating an offline installation layout (see the [Create an Offline Installation of Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) page for more details).

> [!IMPORTANT]
> Sie benötigen Administratoranmeldeinformationen, um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]zu installieren. Sie benötigen sie allerdings nicht, um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nach der Installation zu verwenden.

 Ihr lokales Administratorkonto benötigt die folgenden Berechtigungen, damit Sie alles in Visual Studio installieren können.

|Angezeigter Name des lokalen Richtlinienobjekts|Benutzerrechte|
|--------------------------------------|----------------|
|Sichern von Dateien und Verzeichnissen|SeBackupPrivilege|
|Debuggen von Programmen|SeDebugPrivilege|
|Verwalten von Überwachungs- und Sicherheitsprotokollen|SeSecurityPrivilege|

 Weitere Informationen zu den Anforderungen an das lokale Administratorkonto finden Sie im Knowledge Base-Artikel [SQL Server-Installation schlägt fehl, wenn das Setupkonto nicht über bestimmte Benutzerrechte verfügt](https://support.microsoft.com/kb/2000257).

### <a name="BKMK_Media"></a> Using installation media
 Führen Sie zum Installieren von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]die Installationsdatei für die gewünschte Edition im Stammverzeichnis des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Installationsmediums aus:

|Edition|Installationsdatei|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio-Community|vs_community.exe|

### <a name="BKMK_Website"></a> Downloading from the product website
 Visit the [Visual Studio Downloads](https://go.microsoft.com/fwlink/?LinkId=517106) page, and select the edition of Visual Studio that you want.

### <a name="downloading-from-your-subscription-service"></a>Downloading from your subscription service
 Visit  the [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) page, and select the edition of Visual Studio that you want.

### <a name="BKMK_Offline"></a> Creating an offline installation layout
 If you do not have the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installation media, or you do not have a Visual Studio subscription,  or you do not want to install [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] by using the web installer, you can perform a "disconnected" installation by creating what is known as an offline installation layout. For more information, see the [Create an Offline Installation of Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) page.

## <a name="enterprise"></a> Deploying Visual Studio in an Enterprise
 For information about how to deploy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] over a network, see the [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md).

### <a name="BKMK_Virtualized"></a> Installing Visual Studio in a virtualized environment
 **Videoprobleme mit Hyper-V**

 Das Ausführen von Windows Server 2008 R2 mit aktiviertem Hyper-V und beschleunigter Grafikkarte führt möglicherweise zu Systemverlangsamungen.

 Weitere Informationen finden Sie auf der folgenden Seite der Microsoft-Website: [Die Videoleistung eines Computers mit Windows Server 2008 oder Windows Server 2008 R2 ist bei aktivierter Hyper-V-Rolle und installierter beschleunigter Grafikkarte möglicherweise verringert](https://go.microsoft.com/fwlink/?LinkID=231084).

 **Emulieren von Geräten mit Hyper-V**

 Bei der Installation von Visual Studio 2015 auf echter Hardware ohne Virtualisierung können Sie Features auswählen, die eine Emulation von Windows- und Android-Geräten mithilfe von Hyper-V ermöglichen. Bei der Installation in Hyper-V können Sie keine Windows- oder Android-Geräte emulieren. Der Grund hierfür ist, dass die Emulatoren selbst virtuelle Computer sind, und Sie können derzeit keine virtuellen Computer auf anderen virtuellen Computern hosten. Als Problemumgehung verwenden Sie echte Windows- oder Android-Geräte, auf denen Sie Ihre Anwendung direkt bereitstellen und debuggen können .

## <a name="optionalComponents"></a> Installing optional components
 If you want to install components that you might not have selected during your original installation, use the following procedure.

#### <a name="to-install-optional-components"></a>To install optional components

1. Wählen Sie in der **Systemsteuerung**auf der Seite **Programme und Funktionen** die Produktversion aus, zu der Sie mindestens eine Komponente hinzufügen möchten, und wählen Sie anschließend **Deinstallieren/Ändern**aus.

2. Wählen Sie im Setup-Assistenten **Ändern**aus, und wählen Sie anschließend die Komponenten aus, die Sie installieren möchten.

3. Wählen Sie **Weiter**aus, und befolgen Sie anschließend die übrigen Anweisungen.

## <a name="helpContent"></a> Installieren von Offline-Hilfeinhalt
 Nach der Installation von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]können Sie zusätzliche Hilfeinhalte herunterladen, damit diese offline zur Verfügung stehen.

#### <a name="to-install-or-uninstall-help-content"></a>So installieren oder deinstallieren Sie Hilfeinhalt

1. Klicken Sie in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Menüleiste auf **Hilfe**, **Hilfeinhalte hinzufügen und entfernen**.

2. Wählen Sie in der Registerkarte **Inhalt verwalten** in **Microsoft Help Viewer**die Installationsquelle für den Hilfeinhalt aus.

3. Wenn Sie nach einem bestimmten Hilfethema suchen, geben Sie den Namen oder ein Schlüsselwort in das Textfeld **Suchen** ein und drücken dann die **EINGABETASTE**.

4. Klicken Sie neben dem Namen des Hilfethemas, das Sie installieren möchten, auf **Hinzufügen** oder **Entfernen** .

5. Click the **Update** button.

   For more information about how to install or deploy offline Help, see the [Help Viewer Administrator Guide](../ide/help-viewer-administrator-guide.md).

## <a name="serviceReleases"></a> Suchen nach Service Releases und Produktupdates
 Da nicht alle Erweiterungen kompatibel sind, führt Visual Studio kein automatisches Upgrade für Erweiterungen durch, wenn Sie ein Upgrade von früheren Versionen durchführen. You must reinstall the extensions from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/) or from the software publisher.

#### <a name="to-automatically-check-for-service-releases"></a>So suchen Sie automatisch nach Service Releases

1. Wählen Sie in der Menüleiste **Extras**, **Optionen**.

2. Erweitern Sie **Umgebung** im Dialogfeld **Optionen**und klicken Sie dann auf **Erweiterungen und Updates**. Stellen Sie sicher, dass das Kontrollkästchen **Automatisch nach Updates suchen** markiert ist, und klicken Sie auf **OK**.

## <a name="registering-visual-studio"></a>Registrieren von Visual Studio

1. Wählen Sie in der Menüleiste **Hilfe**dann **Info**aus.

     Im Dialogfeld **Info** wird die Produkt-ID (PID) angezeigt. Sie benötigen die PID und die Anmeldeinformationen für das Windows-Konto (z. B. eine E-Mail-Adresse und das zugehörige Kennwort von Hotmail oder Outlook.com), um das Produkt registrieren zu können.

2. Wählen Sie in der Menüleiste **Hilfe**dann **Produkt registrieren**.

## <a name="repair"></a> Reparieren von Visual Studio

#### <a name="to-repair-visual-studio"></a>So reparieren Sie Visual Studio

1. Wählen Sie in der **Systemsteuerung**auf der Seite **Programme und Funktionen** die Produktversion aus, die Sie reparieren möchten, und wählen Sie anschließend **Ändern**aus.

2. Wählen Sie im Setup-Assistenten **Reparieren**aus, wählen Sie **Weiter**aus, und befolgen Sie anschließend die übrigen Anweisungen.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>To repair Visual Studio in silent or passive modes (that is, to repair from source)

1. Öffnen Sie die Windows-Eingabeaufforderung auf dem Computer, auf dem Visual Studio installiert ist.

2. Geben Sie folgende Parameter ein:

     *DVDRoot* \\<Installation File\> \</quiet&#124;/passive> [/norestart]/Repair

## <a name="troubleshooting"></a> Troubleshooting an installation
 In den folgenden Ressourcen finden Sie Hilfe für Setup- und Installationsprobleme:

- [Einrichtung und Installation in Visual Studio](https://go.microsoft.com/fwlink/?LinkID=151190) – Forum. Lesen Sie Fragen und Antworten von anderen Personen in der Visual Studio-Community. Wenn Sie die gesuchte Antwort nicht finden, stellen Sie eigene Fragen.

- [Microsoft Support für Visual Studio](https://go.microsoft.com/fwlink/?LinkID=251019) -Website. Lesen Sie Artikel der Knowledge Base (KB), und erfahren Sie, wie Sie sich an den Microsoft Support wenden, um Informationen zu Problemen bei der Installation von Visual Studio zu erhalten.

## <a name="relatedTopics"></a> Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Erstellen einer Offlineinstallation von Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Describes how to install Visual Studio when you are not connected to the Internet.
|[Parallele Installation mehrerer Visual Studio-Versionen](../install/install-visual-studio-versions-side-by-side.md)|Stellt Informationen zum Installieren mehrerer Versionen von Visual Studio auf demselben Computer bereit.|
|[Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Lists the command-line parameters that you can use when you install Visual Studio from a command prompt.|
|[Deinstallieren von Visual Studio](../install/uninstall-visual-studio.md)|Describes how to uninstall Visual Studio.|
|[Administratorhandbuch für Visual Studio](../install/visual-studio-administrator-guide.md)|Stellt Informationen zu Bereitstellungsoptionen für Visual Studio bereit.|
|[Visual Studio Bildbibliothek](../designers/the-visual-studio-image-library.md)|Stellt Informationen zum Installieren von Grafiken bereit, die in Visual Studio-Anwendungen verwendet werden können.|
|[Erste Schritte mit der Entwicklung in Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Includes information and links that can help you use Visual Studio more effectively.|

## <a name="see-also"></a>Siehe auch

- [Anmelden bei Visual Studio](../ide/signing-in-to-visual-studio.md)