---
title: Bereitstellung – Featuretour
description: Erfahren Sie mehr über die Möglichkeiten zum Bereitstellen von apps aus Visual Studio.
ms.custom: mvc
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91dc83a1599058e1357c3ac7869f4284a1fc7fc5
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279114"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Schnellstart: Ein erster Blick auf die Bereitstellung in Visual Studio

Durch die Bereitstellung einer Anwendung, den Dienst oder die Komponente, verteilen Sie diese für die Installation auf anderen Computern, Geräten oder Servern oder in der Cloud. Wählen Sie die entsprechende Methode für den Typ der Bereitstellung in Visual Studio aus, den Sie benötigen. (Viele app-Typen unterstützen andere Bereitstellungstools wie z. B. die Bereitstellung über die Befehlszeile oder NuGet, die hier nicht beschrieben sind.)

Schnellstarts und Tutorials für die schrittweise bereitstellungsanleitung angezeigt. Einen Überblick über die Optionen für die Bereitstellung, finden Sie unter [welche Veröffentlichungsoptionen für mich geeignet sind?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Bereitstellen in lokalen Ordner

Bereitstellung auf einem lokalen Ordner wird normalerweise verwendet, für das Testen oder um einer Bereitstellung zu beginnen, in der ein anderes Tool für die endgültige Bereitstellung verwendet wird.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, und. **NET Core**: Verwenden Sie das Tool "Veröffentlichen", um in einen lokalen Ordner bereitzustellen. Die genaue verfügbaren Optionen hängen von Ihren app-Typ ab. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Projekts, und wählen Sie **veröffentlichen**. (Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben, klicken Sie dann auf **neues Profil erstellen**.) Wählen Sie als Nächstes **Ordner**. Weitere Informationen finden Sie unter [in einen lokalen Ordner bereitstellen](quickstart-deploy-to-local-folder.md).

    ![Wählen Sie veröffentlichen](../deployment/media/quickstart-publish.png)

- **Visual C++-Laufzeitbibliotheken**: Sie können die Visual C++-Laufzeit, die mit der lokalen Bereitstellung oder statische Verknüpfung bereitstellen. Weitere Informationen finden Sie unter [Bereitstellen von systemeigenen Desktopanwendungen (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

## <a name="publish-to-azure"></a>Veröffentlichen in Azure

- **ASP.NET**, **ASP.NET Core**, **Python**, und **Node.js**: Sie können das Tool "Veröffentlichen" verwenden, zum schnellen Bereitstellen von apps in Azure App Service oder einen virtuellen Azure- Computer. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**. (Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben, klicken Sie dann auf **neues Profil erstellen**.) Klicken Sie im Dialogfeld "Veröffentlichen" Wählen Sie entweder **App Service** oder **Azure Virtual Machines**, und befolgen Sie dann die Konfigurationsschritte.

    ![Wählen Sie Azure App Service](../deployment/media/quickstart-publish-azure.png "Azure App Service auswählen")

    In Visual Studio 2017 Version 15.7 und höher, können Sie ASP.NET Core-apps bereitstellen **App Service für Linux**.

    Für Python-apps finden Sie auch unter [Python - Veröffentlichung in Azure App Service](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

    Eine kurze Einführung finden Sie unter [in Azure veröffentlichen](quickstart-deploy-to-azure.md) und [in Linux veröffentlichen](quickstart-deploy-to-linux.md). Siehe auch [Veröffentlichen einer ASP.NET Core-app in Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Bereitstellung mit Git, finden Sie unter [kontinuierliche Bereitstellung von ASP.NET Core in Azure mit Git](/aspnet/core/publishing/azure-continuous-deployment).

    Weitere Informationen zum Importieren eines Veröffentlichungsprofils aus Azure App Service in Visual Studio finden Sie unter [veröffentlichungseinstellungen importieren und Bereitstellen in Azure](../deployment/tutorial-import-publish-settings-azure.md).

    > [!NOTE]
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, können Sie [melden Sie sich hier](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Im Web veröffentlichen oder auf einer Netzwerkfreigabe bereitstellen

- **ASP.NET**, **ASP.NET Core**, **Node.js**, und **Python**: Sie können das Tool "Veröffentlichen" verwenden, um auf einer Website über FTP oder Web Deploy bereitstellen. Weitere Informationen finden Sie unter [bereitstellen auf einer Website](quickstart-deploy-to-a-web-site.md).

    Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Veröffentlichen**. (Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben, klicken Sie dann auf **neues Profil erstellen**.) Wählen Sie die Option, Sie möchten, und führen Sie die Konfigurationsschritte aus, in das Tool "Veröffentlichen".

    ![Wählen Sie IIS, FTP usw. an.](../deployment/media/quickstart-publish-iis-ftp.png)

    Informationen zum Importieren eines Veröffentlichungsprofils in Visual Studio finden Sie unter [Importieren von veröffentlichungseinstellungen und Bereitstellen von IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Sie können auch ASP.NET-Anwendungen und-Dienste auf vielfältige andere Weise bereitstellen. Weitere Informationen finden Sie unter [Bereitstellen von ASP.NET Webanwendungen und-Dienste](http://www.asp.net/aspnet/overview/deployment).

- **Visual C++-Laufzeitbibliotheken**: Sie können die zentrale Bereitstellung mithilfe von Visual C++-Laufzeit bereitstellen. Weitere Informationen finden Sie unter [Bereitstellen von systemeigenen Desktopanwendungen (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

- **Windows-Desktop** können Sie eine Windows-Desktopanwendung auf einem Webserver oder eine Dateifreigabe im Netzwerk mithilfe von ClickOnce-Bereitstellung veröffentlichen. Benutzer können die Anwendung mit einem einzelnen Mausklick installieren. Weitere Informationen finden Sie unter [bereitstellen eine desktop-app mit ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) und [Bereitstellen einer nativen app mit ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

## <a name="publish-to-microsoft-store"></a>Veröffentlichen in Microsoft Store

In Visual Studio können Sie für die Bereitstellung in Microsoft Store-app-Pakete erstellen.

- **UWP**: Sie können Ihre app Packen und stellen Sie sie mithilfe der Menüelemente. Weitere Informationen finden Sie unter [Packen eine UWP-app mit Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Erstellen eines App-Pakets](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows-Desktop**: Sie können auf der Microsoft Store über Desktop-Brücke ab Visual Studio 2017 Version 15.4 bereitstellen. Zu diesem Zweck erstellen Sie zunächst ein Projekt zum Verpacken von Windows-Anwendungen. Weitere Informationen finden Sie unter [Packen einer desktop-app für Microsoft Store (Desktop-Brücke)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Desktop-Brücke](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Bereitstellen Sie auf einem Gerät (UWP)

Wenn Sie eine UWP-app zu Testzwecken auf einem Gerät bereitstellen, finden Sie unter [Ausführen von UWP-apps auf einem Remotecomputer in Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-client"></a>Erstellen Sie ein Installationspaket (Windows-Client)

Wenn Sie mehr über eine komplexe Installation einer desktop-Anwendung als benötigen [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) bereitstellen können, können Sie ein Installationspaket, eines Setup-Projekts oder eines benutzerdefinierten Bootstrappers erstellen.

- Eine MSI-basierte WiX-Installationsprogramms kann erstellt werden, mithilfe der [WiX Toolset Visual Studio 2017-Erweiterung](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera Software kann mit Visual Studio 2017 (Community-Edition nicht unterstützt) verwendet werden. Beachten Sie, dass InstallShield Limited Edition nicht mehr in Visual Studio enthalten ist und wird in Visual Studio 2017 nicht unterstützt. Wenden Sie [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) zur künftigen Verfügbarkeit.

- Wenn Sie ein Setup-Projekt (Vdproj) erstellen möchten, installieren Sie die [Visual Studio 2017-Installer Projects Extension](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Sie können die erforderliche Komponenten für desktopanwendungen installieren, konfigurieren Sie ein generisches Installationsprogramm, das als Bootstrapper bezeichnet wird. Weitere Informationen finden Sie unter [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Bereitstellen, um die testumgebung

Sie können anspruchsvollere Entwicklung und Tests, die durch die Bereitstellung Ihrer Anwendungen in virtuellen Umgebungen aktivieren. Weitere Informationen finden Sie unter [Test in einer laborumgebung](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="devops-deployment"></a>DevOps-Bereitstellung

Azure-Pipelines können Sie in einer teamumgebung um continuous Deployment Ihrer App zu aktivieren. Weitere Informationen finden Sie unter [Azure Pipelines](/azure/devops/pipelines/index) und [in Azure bereitstellen](/azure/devops/deploy-azure/index).

## <a name="deployment-for-other-app-types"></a>Bereitstellung für andere app-Typen

| App-Typ | Bereitstellungsszenario | Link |
| --- | --- | --- |
| **Office-app** | Sie können ein Add-In für Office in Visual Studio veröffentlichen. | [Bereitstellen Sie und veröffentlichen Sie Ihre Office-add-Ins](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF oder OData-Dienst**  | Andere Anwendungen können WCF RIA-Diensten, die Sie auf einem Webserver bereitstellen. | [Entwickeln und Bereitstellen von WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch wird in Visual Studio 2017 nicht mehr unterstützt, aber Sie können weiterhin in Visual Studio 2015 und früher bereitgestellt werden. | [Bereitstellen von LightSwitch-Anwendungen](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie einen kurzen Blick auf die Bereitstellungsoptionen für unterschiedliche Anwendungen.

> [!div class="nextstepaction"]
> [Welche Veröffentlichungsoptionen sind für mich geeignet?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
