---
title: "Übersicht über die Bereitstellung - Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e05bf361515b45f3ebc7683fa0c83ec6116d9419
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="deployment-overview-in-visual-studio"></a>Übersicht über die Bereitstellung in Visual Studio

Wenn Sie eine Anwendung, einen Dienst oder eine Komponente bereitstellen, verteilen Sie diese für die Installation auf anderen Computern, Geräten, Servern oder in der Cloud. Wählen Sie die entsprechende Methode für den Typ der Bereitstellung in Visual Studio aus, den Sie benötigen. (Viele app-Typen unterstützen anderen Bereitstellungstools z. B. Bereitstellung über die Befehlszeile oder NuGet, die hier nicht beschrieben sind.)

Finden Sie in den Lernprogrammen für-Schritt-Anweisungen.

### <a name="deploy-to-local-folder"></a>Bereitstellen von lokalen Ordner

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, und **.NET Core**: Verwenden des Tools zum Veröffentlichen mit einer lokalen Bereitstellung Ordner. Die genaue verfügbaren Optionen hängen von Ihrer app-Typ ab. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste des Projekts, und wählen Sie **veröffentlichen**, und wählen Sie dann **Ordner**. Weitere Informationen finden Sie unter [Bereitstellen in einen lokalen Ordner](quickstart-deploy-to-local-folder.md).

    ![Wählen Sie veröffentlichen](../deployment/media/quickstart-publish.png)

- **Visual C++-Laufzeitbibliotheken**: Sie können die lokale Bereitstellung oder statische Verknüpfung mit Visual C++-Laufzeit bereitstellen. Weitere Informationen finden Sie unter [Bereitstellen von systemeigenen Desktopanwendungen (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

### <a name="publish-to-web-or-deploy-to-network-share"></a>Im Web veröffentlichen oder auf einer Netzwerkfreigabe bereitstellen

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, und **.NET Core**: Sie können mithilfe des Tools zum Veröffentlichen zum Bereitstellen einer die Website über FTP oder Web Deploy. Weitere Informationen finden Sie unter [bereitstellen, um eine Website](quickstart-deploy-to-a-web-site.md).

    Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**. Wählen Sie das Tool "Veröffentlichen" die Option, Sie möchten, und führen Sie die Konfigurationsschritte aus.

    ![Wählen Sie IIS, FTP usw. ein.](../deployment/media/quickstart-publish-iis-ftp.png)

    Sie können auch ASP.NET-Anwendungen und-Dienste in verschiedene andere Weise bereitstellen. Weitere Informationen finden Sie unter [Bereitstellen von ASP.NET-Webanwendungen und-Dienste](http://www.asp.net/aspnet/overview/deployment).

- **Visual C++-Laufzeitbibliotheken**: Sie können die zentrale Bereitstellung mithilfe von Visual C++-Laufzeit bereitstellen. Weitere Informationen finden Sie unter [Bereitstellen von systemeigenen Desktopanwendungen (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

- **Windows-Desktop** können Sie eine Windows-Desktopanwendung auf einem Webserver oder eine Dateifreigabe im Netzwerk mithilfe von ClickOnce-Bereitstellung veröffentlichen. Benutzer können die Anwendung mit einem einzelnen Mausklick installieren. Weitere Informationen finden Sie unter [eine desktop-app mit ClickOnce bereitstellen](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) und [eine systemeigene app mit ClickOnce bereitstellen](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

### <a name="publish-to-azure"></a>Veröffentlichen in Azure

- **ASP.NET, ASP.NET Core, Python, Node.js und .NET Core** Webanwendungen: Sie können mithilfe des Tools zum Veröffentlichen schnell apps nach Azure App Service oder auf einem virtuellen Azure-Computer bereitstellen. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**. Klicken Sie im Dialogfeld "Veröffentlichen" Wählen Sie entweder **Microsoft Azure App Service** oder **Microsoft Azure Virtual Machines**, und befolgen Sie dann die Konfigurationsschritte.

    ![Wählen Sie die Azure App Service](../deployment/media/quickstart-publish-azure.png "-Azure App Service auswählen")

    Um auf einem virtuellen Azure-Computer zu veröffentlichen, führen Sie einen Bildlauf nach rechts, und wählen Sie **Microsoft Azure Virtual Machines**.

    Eine kurze Einführung finden Sie unter [Publish to Azure](quickstart-deploy-to-azure.md). Siehe auch [eine ASP.NET Core-app in Azure veröffentlichen](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Bereitstellung mit Git, finden Sie unter [fortlaufende Bereitstellung von ASP.NET Core in Azure mit Git](/aspnet/core/publishing/azure-continuous-deployment).

    > [!NOTE]
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, können Sie [registrieren Sie sich hier](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

- Andere **Azure Services**: finden Sie unter den jeweiligen [Azure-Dienst](/azure/#pivot=products) Dokumentation für die verschiedenen Bereitstellungsoptionen, die von Visual Studio unterstützt werden kann.

### <a name="publish-to-microsoft-store"></a>Microsoft-Datenspeicher veröffentlichen

In Visual Studio können Sie app-Pakete für die Bereitstellung in Microsoft Store erstellen.

- **Universelle Windows-Plattform**: können Sie Ihre app Packen und Bereitstellen mit Menüelementen. Weitere Informationen finden Sie unter [eine uwp-app mit Visual Studio-Paket](/windows/uwp/packaging/packaging-uwp-apps).

    ![Erstellen eines App-Pakets](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows-Desktop**: Sie können auf der Microsoft Store unter Verwendung der Bridge Desktop ab Visual Studio 2017 Version 15.4 bereitstellen. Zu diesem Zweck erstellen Sie zunächst ein Windows-Anwendungsprojekt verpacken. Weitere Informationen finden Sie unter [eine desktop-app-Paket für Microsoft Store (Desktop Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Desktop-bridge](../deployment/media/feature-tour-desktop-bridge.png)

### <a name="create-an-installer-package-windows-client"></a>Erstellen Sie ein Installationspaket (Windows-Client)

- Ein Installer MSI-basierte WiX kann erstellt werden, mithilfe der [WiX-Toolset 2017 Erweiterung für Visual Studio](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera Software kann mit Visual Studio 2017 (Community-Edition nicht unterstützt) verwendet werden. Beachten Sie, dass InstallShield Limited Edition nicht mehr in Visual Studio enthalten ist und wird in Visual Studio 2017 nicht unterstützt; Erkundigen Sie sich [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) über die Verfügbarkeit von zukünftigen.

- Wenn Sie ein Setup-Projekt (Vdproj) erstellen möchten, installieren Sie die [Visual Studio 2017 Installer Projects Extension](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Sie können die erforderliche Komponenten für desktopanwendungen installieren, konfigurieren Sie ein generisches Installationsprogramm, das als Bootstrapper bezeichnet wird. Weitere Informationen finden Sie unter [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md).

### <a name="deploy-to-test-lab"></a>Bereitstellen, um das Labor testen

Sie können anspruchsvollere Entwicklung und Tests durch Bereitstellen von Anwendungen in virtuellen Umgebungen aktivieren. Weitere Informationen finden Sie unter [Test in einer laborumgebung](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

### <a name="devops-deployment"></a>DevOps-Bereitstellung

Visual Studio Team Services (VSTS) können Sie in einer teamumgebung um fortlaufende Bereitstellung Ihrer App zu ermöglichen. Weitere Informationen finden Sie unter [Build und Release](/vsts/build-release/index) und [Bereitstellung in Azure](/vsts/deploy-azure/index).

### <a name="deployment-for-other-app-types"></a>Bereitstellung für andere app-Typen

| App-Typ | Bereitstellungsszenario | Link |
| --- | --- | --- |
| **Office-app** | Sie können ein Add-in für Office in Visual Studio veröffentlichen. | [Bereitstellen Sie und veröffentlichen Sie des Office-add-Ins](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF- oder OData-Dienst**  | Andere Anwendungen können WCF RIA-Dienste, die Sie auf einem Webserver bereitstellen. | [Entwickeln und Bereitstellen von WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch wird nicht mehr in Visual Studio 2017 unterstützt, aber Sie können weiterhin in Visual Studio 2015 und früher bereitgestellt werden. | [Bereitstellen von LightSwitch-Anwendungen](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

